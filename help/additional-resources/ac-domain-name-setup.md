---
title: Configuração do nome de domínio
description: Saiba como delegar um subdomínio ao Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4d52d197-d20e-450c-bfcf-e4541c474be4
source-git-commit: 82f7254a9027f79d2af59aece81f032105c192d5
workflow-type: tm+mt
source-wordcount: '2043'
ht-degree: 2%

---

# Configuração do nome de domínio

Este documento descreve os requisitos comerciais e técnicos para a configuração e delegação de nomes de domínio. Você precisará selecionar um subdomínio de envio de email e, opcionalmente, um subdomínio voltado para o exterior para hospedar componentes da Web (páginas de aterrissagem, página de opção de não participação) para a plataforma de Adobe que está usando.

>[!NOTE]
>
>Você também pode configurar novos subdomínios usando o Painel de controle do Campaign (disponível na versão beta). Saiba mais [nesta seção](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read).

## Subdomínios

Com o Adobe, o marketing digital pode realmente se tornar o mecanismo contextual que potencializa o programa de marketing de engajamento do cliente da sua marca.  O email continua sendo a base dos programas de marketing digital. No entanto, alcançar a caixa de entrada se tornou mais difícil do que nunca.

A criação de um subdomínio para campanhas de email permite que as marcas isolem vários tipos de tráfego (marketing versus corporativo, por exemplo) em pools de IP específicos e com domínios específicos, o que irá acelerar o [processo de aquecimento de IP](../../help/additional-resources/increase-reputation-with-ip-warming.md) e melhorar a capacidade de entrega em geral. Se você compartilhar um domínio e ele for bloqueado ou adicionado à lista de bloqueios, isso poderá afetar seu delivery de email corporativo. No entanto, problemas de reputação ou bloqueios em um domínio específico para suas comunicações de marketing por email afetarão apenas esse fluxo de email.  Usar seu domínio principal como remetente ou endereço &quot;De&quot; para vários fluxos de email também pode interromper a autenticação de email, fazendo com que suas mensagens sejam bloqueadas ou colocadas na pasta de spam.

### Delegação

A delegação de nome de domínio é um método que permite ao proprietário de um nome de domínio (tecnicamente: uma zona DNS) delegar uma subdivisão dele (tecnicamente: uma zona DNS sob ele, que pode ser chamada de subzona) para outra entidade. Basicamente, se um cliente estiver lidando com a zona &quot;example.com&quot;, ele poderá delegar a subzona &quot;marketing.example.com&quot; ao Adobe Campaign.

Isso significa que os servidores DNS da Adobe Campaign terão autoridade total somente nessa zona e não no domínio de nível superior. Os servidores DNS da Adobe Campaign fornecerão respostas autoritativas a consultas sobre nomes de domínio nessa zona, como &quot;t.marketing.example.com&quot; em si, mas não &quot;www.example.com&quot;.

Ao delegar um subdomínio para uso com o Adobe Campaign, os clientes podem confiar no Adobe para manter a infraestrutura de DNS necessária para atender aos requisitos de capacidade de entrega padrão do setor para seus domínios de envio de marketing por email, enquanto continuam a manter e controlar o DNS para seus domínios de email internos.  A delegação de subdomínio permite:

Clientes para manter a imagem da marca usando um alias DNS com seus nomes de domínio
Adobe para implementar de forma autônoma todas as práticas recomendadas técnicas para otimizar totalmente a capacidade de entrega durante o envio por email

## Opções de configuração de DNS

Para fornecer um serviço gerenciado baseado em nuvem, o Adobe incentiva os clientes a usar a delegação de subdomínio ao implantar o Adobe Campaign.  No entanto, o Adobe oferece aos clientes uma opção alternativa - configuração CNAME - para configurar o DNS.

| Opção | Descrição | Responsabilidades do Adobe | Responsabilidades do cliente |
|--- |------- |--- |--- |
| Delegação de subdomínio para o Adobe Campaign | O cliente delega um subdomínio (email.example.com) ao Adobe. Nesse cenário, o Adobe é capaz de fornecer o Campaign como um serviço gerenciado controlando e mantendo todos os aspectos do DNS necessários para fornecer, renderizar e rastrear campanhas de email. | Gerenciamento completo do subdomínio e de todos os registros DNS necessários para o Adobe Campaign. | Delegação adequada do subdomínio para o Adobe |
| Uso de CNAMEs | O cliente cria um subdomínio e usa CNAMEs para apontar para registros específicos de Adobe.  Usando essa configuração, a Adobe e o cliente compartilham a responsabilidade pela manutenção do DNS. | Gerenciamento de registros DNS necessários para o Adobe Campaign. | Criação e controle do subdomínio e criação/gerenciamento dos registros CNAME necessários para o Adobe Campaign. |

## Registros DNS necessários

| Tipo de registro | Finalidade | Exemplos de registro/conteúdo |
|--- |--- |--- |
| MX | Especificar servidores de email para mensagens de entrada | <i>email.exemplo.com</i></br><i>10 inbound.email.exemplo.com</i> |
| SPF (TXT) | Estrutura de Política do Remetente | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM (TXT) | Email identificado de DomainKeys | <i>cliente._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY AQUI&quot; |
| Registros de hosts (A) | Mirror pages, hospedagem de imagem e links de rastreamento, todos os domínios de envio | m.email.example.com EM UM 123.111.100.99</br>t.email.example.com EM UM 123.111.100.98</br>email.example.com EM UM 123.111.100.97 |
| DNS reverso (PTR) | Mapeia os endereços IP do cliente para um nome de host da marca do cliente | 18.101.100.192.in-addr.arpa ponteiro de nome de domínio r18.email.example.com |
| CNAME | Fornece um alias para outro nome de domínio | t1.email.example.com é um alias para t1.email.example.campaign.adobe.com |


O DMARC (Domain-based Message Authentication, Reporting, and Conformance) é recomendado para autenticar remetentes de email e garantir que os sistemas de email de destino confiem em mensagens enviadas do seu domínio.

Exemplo de registro TXT DMARC:

```
_dmarc.email.example.com

“v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com” 
```

Você pode implementar o DMARC manualmente ou entrar em contato com o Adobe para ajudá-lo a configurar o DMARC para sua marca.

## Requisitos de configuração

### Delegação de subdomínio

Isso requer que o cliente crie um subdomínio em seus servidores DNS e defina os servidores de nomes para que esse subdomínio seja mantido pelo Adobe.  Por exemplo, um cliente cujo nome de domínio principal é &quot;example.com&quot; e que deseja delegar o gerenciamento de &quot;marketing.example.com&quot; ao Adobe para seus deliveries de email terá que materializar essa delegação para adicionar os seguintes registros de tipo ao seu DNS:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

A delegação de um nome de domínio implica que esse domínio será dedicado ao delivery de email por meio da plataforma Adobe Campaign e, portanto, não poderá ser usado para outros meios (por exemplo, enviar email de outra infraestrutura de email).

Durante o processo de configuração, o Adobe garantirá que o domínio esteja anexado à infraestrutura de email de entrada do Adobe para gerenciar e processar os emails de reassociação que retornam a esses domínios (configuração de registro DNS do tipo MX).

### Uso de CNAMEs

Se o cliente optar por usar CNAMEs em vez de delegar um subdomínio ao Adobe, durante a fase de configuração, o Adobe fornecerá os registros a serem colocados nos servidores DNS do cliente e configurará os valores correspondentes nos servidores DNS da Adobe Campaign.

## Requisitos gerais para implantação

Ao implementar uma nova solução de marketing corporativo, há requisitos para componentes voltados para o exterior.  Isso inclui hospedar páginas de aterrissagem e formulários Web, configurar links e páginas da Web para serem rastreadas, exibir mirror pages e configurar uma página de opção.

Embora esses requisitos estejam sendo gerenciados por meio de componentes hospedados pelo Adobe e pelo cliente, eles incluem URLs que podem ser vistos pelos recipients dos emails.  Para evitar ter URLs que indicam a solução técnica subjacente ou o provedor de hospedagem, os subdomínios podem ser configurados para tornar isso transparente para os recipients dos emails.  Por exemplo, ao analisar um URL como, http://www.customer.com/, o domínio seria &quot;www.customer.com&quot;.  O subdomínio seria &quot;www&quot;.

### Requisitos de subdomínio

Determine os subdomínios a serem usados para URLs com marca (mirror pages e URLs de rastreamento) do aplicativo do Adobe Campaign.  Decida também qual será o &quot;Endereço de origem&quot;, o &quot;Nome de origem&quot; e o &quot;Endereço de resposta&quot; para cada subdomínio nos deliveries de email.

Complete a tabela abaixo, a primeira linha é apenas um exemplo.

| Subdomain | Do endereço | Nome do remetente | Endereço para resposta |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Cliente | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* A finalidade do campo &quot;Endereço de resposta&quot; é quando você deseja que o recipient responda a um endereço diferente do &quot;Endereço de origem&quot;.  Embora não seja um campo obrigatório, o Adobe recomenda que o &quot;Endereço de resposta&quot; seja válido e vinculado a uma caixa de correio monitorada.  Esta caixa de correio deve ser hospedada pelo cliente.  Pode ser uma caixa de entrada de suporte, por exemplo, customercare@customer.com, em que os emails são lidos e respondidos.
>* Se nenhum &quot;Endereço de resposta&quot; for escolhido pelo cliente, o endereço padrão será sempre `<tenant>-<type>-<env>@<subdomain>`.
>* Quando o &quot;Endereço de resposta&quot; é configurado dessa forma, as respostas são enviadas para uma caixa de correio não monitorada.
>* Ao enviar emails do Adobe Campaign, a caixa de correio &quot;Do endereço&quot; não é monitorada e os usuários de marketing não podem acessá-la. O Adobe Campaign também não oferece a capacidade de responder automaticamente ou encaminhar emails recebidos nessa caixa de correio.
>* O endereço do Remetente/De da campanha e o endereço do Erro não podem ser &quot;abuso&quot; ou &quot;postmaster&quot;.

## Delegar subdomínios

O(s) subdomínio(s) escolhido(s) para ser(em) usado(s) na plataforma Adobe Campaign deve(m) ser delegado(s) criando quatro registros de servidor de nomes (NS).  Isso permite que o subdomínio seja delegado corretamente ao Adobe.  Veja abaixo um exemplo de delegação de subdomínio e as respectivas instruções de DNS.  Substitua ‘emails.customer.com’ pelo subdomínio que você deseja delegar.  Observe que o subdomínio deve ser exclusivo e não pode estar sendo usado por outra pessoa (por exemplo, um ESP ou MSP existente).

| Subdomínio delegado | Instruções de DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com. </br> `<subdomain>` NS b.ns.campaign.adobe.com. </br> `<subdomain>` NS c.ns.campaign.adobe.com. </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

## Rastreamento, Mirror pages, Recursos

Assim que os subdomínios de envio de email forem delegados corretamente na Adobe Campaign, a equipe de TechOps do Adobe criará dois ou mais domínios de nível inferior para gerenciar páginas de rastreamento e mirror de maneira independente.

| Tipo | Domínio |
|--- |--- |
| Mirror pages | m.`<subdomain>` |
| Rastreamento | t.`<subdomain>` |
| Recursos | res.`<subdomain>` |

## Implantação na nuvem (opcional)

Isso só se aplica se o Adobe Campaign Classic estiver totalmente hospedado na nuvem pelo Adobe.  Essa é uma configuração opcional.

Quaisquer pesquisas, formulários web e páginas de aterrissagem a serem desenvolvidas são gerenciados por meio do Adobe Campaign totalmente hospedado na nuvem.  Se necessário, um subdomínio adicional pode ser delegado ao Adobe (por exemplo, web.customer.com) para uso em qualquer componente da Web na ferramenta.  Observe que o subdomínio deve ser exclusivo e não pode ser usado por outra pessoa (por exemplo, um ESP ou MSP existente).

| Subdomínio delegado | Instruções de DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>Por padrão, qualquer componente da Web na ferramenta usará o subdomínio inicial delegado para ser usado para email.

## Implantação de mensagens em nuvem (opcional)

Se a instância de marketing do Adobe Campaign Classic estiver hospedada no local do cliente, configurações técnicas adicionais precisarão ser feitas pelo cliente.

Quaisquer pesquisas, formulários web e páginas de aterrissagem a serem desenvolvidas são gerenciados por meio da instância de marketing do Adobe Campaign, onde existem os registros do recipient.

A configuração de DNS CNAME adicional é necessária para implantar componentes da Web externos hospedados pela instância de marketing do Adobe Campaign.  Isso permitirá que os componentes da Web (por exemplo, web.customer.com) sejam acessíveis publicamente à Internet e sejam marcados com o domínio do cliente.

Os firewalls também precisarão ser configurados para permitir o acesso à instância de marketing do Adobe Campaign que hospeda esses componentes da Web (na porta 80 ou 443).

**Recommendations de Práticas Recomendadas:**

O subdomínio para hospedar componentes da Web estará visível aos clientes, portanto, certifique-se de marcá-lo corretamente e seja simples de lembrar, pois ele pode precisar ser digitado manualmente, por exemplo: https://web.customer.com.
Se algum formulário precisar ser hospedado em páginas seguras (HTTPS), será necessária uma configuração técnica de adição, descrita abaixo.

| Subdomínio delegado | Instruções de DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Serviços renderizados

Após essas delegações, a infraestrutura criada pelo Adobe garante que os seguintes serviços sejam executados para cada domínio de envio delegado ou com alias CNAME:

* Criação de caixas de entrada postmaster@ e abuse@
* Configuração de loops de comentários para o domínio delegado
* Mediante solicitação, o Adobe também configurará um registro DMARC conforme especificado. Seu consultor de capacidade de entrega pode ajudar a projetar uma política DMARC de longo prazo e planejar seus domínios de envio.
Os parâmetros estabelecidos pelo Adobe são válidos somente a partir do momento em que a delegação foi concluída e, em seguida, verificada pelo Adobe, e permanecem funcionais.  Todas as ofertas da Adobe Campaign Cloud incluem a delegação de nome de domínio como padrão.

## Condições de faturamento e implementação

* De acordo com o contrato inicial e o tipo de pacote selecionado, podem ser incluídas outras delegações para além das incluídas como padrão para além desta delegação inicial,
* Além dessas delegações incluídas, delegações adicionais serão cobradas,
* O método de faturamento dessas delegações adicionais tem um custo mensal extra, conforme especificado no contrato inicial.

Essas delegações serão aceitas, desde que o CLIENTE escolha os nomes de domínio associados que são dedicados aos deliveries por meio da ferramenta Adobe Campaign e que os pré-requisitos de delegação detalhados no documento relevante sejam implementados corretamente.

## Descontinuação dos serviços

A qualquer momento, o CLIENTE poderá fazer uma solicitação por escrito para não se beneficiar mais dos serviços de delegação e assumir as próprias configurações de DNS necessárias.

Se isso acontecer, o Adobe fornecerá ao CLIENTE uma estimativa detalhando o número de dias de serviço necessários para retornar ao modo de não delegação de domínio.

A Adobe será exonerada de qualquer responsabilidade pelo compromisso da Taxa de capacidade de entrega mencionada acima se o Cliente não cumprir os compromissos estabelecidos acima.

O encerramento do Serviço de Marketing Cloud levará automaticamente ao fim das delegações de domínio e da manutenção de DNS para esses domínios por Adobe.

## Monitorar subdomínios usando o Painel de controle do Campaign

Depois que os subdomínios forem configurados para sua instância, você poderá monitorá-los usando o Painel de controle do Campaign.

Isso permite exibir todos os subdomínios que você delegou à Adobe Campaign, bem como solicitar a renovação dos certificados SSL.

Para obter mais informações, consulte a [documentação dedicada](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates).

>[!NOTE]
>
>O [Painel de Controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR) está disponível somente para clientes que usam o Adobe Managed Services.
