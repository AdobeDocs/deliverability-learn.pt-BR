---
title: Configuração do nome de domínio
description: Saiba como delegar um subdomínio ao Adobe Campaign.
feature: Pôr isto em prática
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '2032'
ht-degree: 2%

---


# Configuração do nome de domínio

Este documento descreve os requisitos comerciais e técnicos para a configuração e delegação do nome de domínio. Você precisará selecionar um subdomínio de envio de email e, opcionalmente, um subdomínio voltado para o exterior para hospedar componentes da Web (páginas de aterrissagem, página de opção) para a plataforma do Adobe que está usando.

>[!NOTE]
>
>Você também pode configurar novos subdomínios usando o Painel de controle do Campaign (disponível como beta). Saiba mais [nesta seção](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read).

## Subdomínios

Com o Adobe, o marketing digital pode realmente se tornar o mecanismo contextual que alimenta o programa de marketing de engajamento do cliente da sua marca.  O email permanece a base dos programas de marketing digital. No entanto, alcançar a caixa de entrada ficou mais difícil do que nunca.

A criação de um subdomínio para campanhas de email permite que as marcas isolem vários tipos de tráfego (marketing vs. corporativo, por exemplo) em pools de IP específicos e com domínios específicos, o que agilizará o [processo de aquecimento de IP](../../help/additional-resources/increase-reputation-with-ip-warming.md) e melhorará a capacidade de entrega em geral. Se você compartilhar um domínio e ele for bloqueado ou adicionado à lista de bloqueios, isso poderá afetar seu delivery de email corporativo. No entanto, problemas ou blocos de reputação em um domínio específico para suas comunicações de marketing por email afetarão apenas esse fluxo de email.  Usar seu domínio principal como remetente ou endereço &quot;De&quot; para vários fluxos de email também pode quebrar a autenticação de email, fazendo com que suas mensagens sejam bloqueadas ou colocadas na pasta de spam.

### Delegação

A delegação de nome de domínio é um método que permite ao proprietário de um nome de domínio (tecnicamente: uma zona DNS) para delegar uma subdivisão dessa zona (tecnicamente: uma zona DNS sob ela, que pode ser chamada de subzona) para outra entidade. Basicamente, se um cliente estiver lidando com a zona &quot;example.com&quot;, ele poderá delegar a subzona &quot;marketing.example.com&quot; à Adobe Campaign.

Isso significa que os servidores DNS da Adobe Campaign terão autoridade total somente nessa zona e não no domínio de nível superior. Os servidores DNS da Adobe Campaign fornecerão respostas autoritárias a consultas sobre nomes de domínio nessa zona, como &quot;t.marketing.example.com&quot;, mas não &quot;www.example.com&quot;.

Ao delegar um subdomínio para uso com o Adobe Campaign, os clientes podem depender do Adobe para manter a infraestrutura de DNS necessária para atender aos requisitos de deliverability padrão do setor para seus domínios de envio de marketing de email, enquanto continuam a manter e controlar o DNS para seus domínios de email internos.  A delegação de subdomínio permite:

Clientes para manter a imagem da marca usando um alias DNS com seus nomes de domínio
Adobe para implementar livremente todas as práticas recomendadas técnicas para otimizar totalmente a capacidade de entrega durante o envio por email

## Opções de configuração de DNS

Para fornecer um serviço gerenciado baseado em nuvem, o Adobe incentiva fortemente os clientes a usar a delegação de subdomínio ao implantar o Adobe Campaign.  No entanto, o Adobe oferece aos clientes uma opção alternativa - Configuração CNAME - para configurar o DNS.

| Opção | Descrição | Responsabilidades do Adobe | Responsabilidades do cliente |
|--- |------- |--- |--- |
| Delegação de subdomínio para o Adobe Campaign | O cliente delega um subdomínio (email.example.com) ao Adobe. Neste cenário, o Adobe pode fornecer o Campaign como um serviço gerenciado controlando e mantendo todos os aspectos do DNS necessários para fornecer, renderizar e rastrear campanhas de email. | Gerenciamento completo do subdomínio e de todos os registros DNS necessários para o Adobe Campaign. | Delegação adequada do subdomínio para o Adobe |
| Uso de CNAMEs | O cliente cria um subdomínio e usa CNAMEs para apontar para registros específicos do Adobe.  Usando essa configuração, a Adobe e o cliente compartilham a responsabilidade pela manutenção do DNS. | Gerenciamento de registros DNS necessários para o Adobe Campaign. | Criação e controle do subdomínio e criação/gerenciamento dos registros CNAME necessários para o Adobe Campaign. |

## Registros DNS necessários

| Tipo de registro | Propósito | Exemplos de registro/conteúdo |
|--- |--- |--- |
| MX | Especificar servidores de correio para mensagens recebidas | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Estrutura de Política do Remetente | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM (TXT) | DomainKeys Identified Mail | <i>cliente._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY AQUI&quot; |
| DMARC (TXT) | Autenticação de Mensagem Baseada em Domínio | Relatórios e conformidade | _dmarc.email.example.com</br>&quot;v=DMARC1; p=none; Rua=mailto:mailauth-reports@myemail.com&quot; |
| Registros de hosts (A) | Mirror pages, hospedagem de imagens e links de rastreamento, todos os domínios de envio | m.email.example.com EM A 123.111.100.99</br>t.email.example.com EM A 123.111.100.98</br>email.example.com EM A 123.111.100.97 |
| DNS reverso (PTR) | Mapeia os endereços IP do cliente para um nome de host da marca do cliente | 18.101.100.192.in-addr.arpa ponteiro do nome de domínio r18.email.example.com |
| CNAME | Fornece um alias para outro nome de domínio | t1.email.example.com é um alias para | t1.email.example.campaign.adobe.com |

## Requisitos de configuração

### Delegação de subdomínio

Isso requer que o cliente crie um subdomínio em seus servidores DNS e defina os servidores de nomes para esse subdomínio como os mantidos pelo Adobe.  Por exemplo, um cliente cujo nome de domínio principal é &quot;example.com&quot; e que deseja delegar o gerenciamento de &quot;marketing.example.com&quot; ao Adobe para seus deliveries de email terá que materializar essa delegação para adicionar os seguintes registros do tipo ao DNS:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

A delegação de um nome de domínio implica que esse domínio será dedicado ao delivery de emails por meio da plataforma Adobe Campaign e, portanto, não poderá ser usado para outros meios (por exemplo, envio de emails de outra infraestrutura de email).

Durante o processo de configuração, o Adobe garantirá que o domínio esteja anexado à infraestrutura de email de entrada do Adobe para gerenciar e processar os emails de reassociação que retornam a esses domínios (configuração de registro DNS do tipo MX).

### Uso de CNAMEs

Se o cliente optar por usar CNAMEs em vez de delegar um subdomínio ao Adobe, durante a fase de configuração, o Adobe fornecerá os registros a serem colocados nos servidores DNS do cliente e configurará os valores correspondentes nos servidores DNS da Adobe Campaign.

## Requisitos gerais para implantação

Ao implementar uma nova solução de marketing empresarial, há requisitos para componentes voltados para o exterior.  Isso inclui a hospedagem de páginas de aterrissagem e formulários web, a configuração de links e páginas da Web a serem rastreadas, a exibição de mirror pages e a configuração de uma página de opção de não participação.

Embora esses requisitos estejam sendo gerenciados por meio de componentes hospedados pelo Adobe e pelo cliente, eles incluem URLs que podem ser vistos pelos recipients dos emails.  Para evitar URLs que indicam a solução técnica subjacente ou o provedor de hospedagem, os subdomínios podem ser configurados para tornar isso transparente para os recipients dos emails.  Por exemplo, ao analisar um URL como, por exemplo, http://www.customer.com/, o domínio seria &quot;www.customer.com&quot;.  O subdomínio disso seria &quot;www&quot;.

### Requisitos de subdomínio

Determine os subdomínios que serão usados para URLs de marca (mirror pages e URLs de rastreamento) do aplicativo Adobe Campaign.  Decida também o que serão &quot;Endereço de origem&quot;, &quot;Nome de origem&quot; e &quot;Endereço de resposta&quot; para cada subdomínio em deliveries de email.

Preencha a tabela abaixo, a primeira linha é apenas um exemplo.

| Subdomain | Endereço de origem | Nome de origem | Endereço para resposta |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Cliente | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* A finalidade do campo &quot;Endereço para resposta&quot; é quando você deseja que o recipient responda a um endereço diferente do &quot;Endereço de origem&quot;.  Embora não seja um campo obrigatório, o Adobe recomenda enfaticamente que o &quot;Endereço de Responder para&quot; seja válido e vinculado a uma caixa de correio monitorada.  Esta caixa de entrada deve ser hospedada pelo cliente.  Pode ser uma caixa de entrada de suporte, por exemplo, customercare@customer.com, onde os emails são lidos e respondidos.
>* Se nenhum &quot;Endereço de Responder para&quot; for escolhido pelo cliente, o endereço padrão será sempre `<tenant>-<type>-<env>@<subdomain>`.
>* Quando o &quot;Endereço de resposta&quot; é configurado dessa forma, as respostas são enviadas a uma caixa de correio não monitorada.
>* Ao enviar emails do Adobe Campaign, a caixa de entrada &quot;Endereço de origem&quot; não é monitorada e os usuários de marketing não podem acessar essa caixa de entrada. A Adobe Campaign também não oferece a capacidade de responder automaticamente ou encaminhar emails recebidos nessa caixa de entrada.
>* O endereço De/Remetente da campanha e o endereço de Erro não podem ser &quot;abuso&quot; ou &quot;postmaster&quot;.


## Delegar subdomínios

Os subdomínios escolhidos para serem usados na plataforma do Adobe Campaign devem ser delegados criando quatro registros de servidor de nomes (NS).  Isso permite que o subdomínio seja delegado corretamente ao Adobe.  Veja abaixo um exemplo de uma delegação de subdomínio e as respectivas instruções de DNS.  Substitua &quot;emails.customer.com&quot; pelo subdomínio que você deseja delegar.  Observe que o subdomínio deve ser exclusivo e ainda não pode ser usado por outra parte (por exemplo, um ESP ou MSP existente).

| Subdomínio delegado | Instruções DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.  </br> `<subdomain>` NS b.ns.campaign.adobe.com.  </br> `<subdomain>` NS c.ns.campaign.adobe.com.  </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

## Rastreamento, Mirror pages, Recursos

Depois que os subdomínios de envio de email forem delegados corretamente na Adobe Campaign, a equipe TechOps do Adobe criará dois ou mais domínios de nível inferior para gerenciar o rastreamento e as mirror pages de maneira independente.

| Tipo | Domain |
|--- |--- |
| Mirror pages | m.`<subdomain>` |
| Rastreamento | t.`<subdomain>` |
| Recursos | res.`<subdomain>` |

## Implantação na nuvem (opcional)

Isso só se aplica se o Adobe Campaign Classic estiver totalmente hospedado na nuvem pelo Adobe.  Essa é uma configuração opcional.

Qualquer pesquisa, formulário da Web e landing pages a serem desenvolvidas são gerenciadas pelo Adobe Campaign totalmente hospedadas na nuvem.  Se necessário, um subdomínio adicional pode ser delegado ao Adobe (por exemplo, web.customer.com) para usar em qualquer componente da Web dentro da ferramenta.  Observe que o subdomínio deve ser exclusivo e não pode ser usado por outra parte (por exemplo, um ESP ou MSP existente).

| Subdomínio delegado | Instruções DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>Por padrão, qualquer componente da Web na ferramenta usará o subdomínio inicial delegado para ser usado em email.

## Implantação de mensagens em nuvem (opcional)

Se a instância de marketing do Adobe Campaign Classic estiver hospedada no local do cliente, configurações técnicas adicionais precisarão ser feitas pelo cliente.

Qualquer pesquisa, formulário da Web e landing page a ser desenvolvida será gerenciada por meio da instância de marketing do Adobe Campaign, onde os registros do recipient existem.

É necessária uma configuração adicional de DNS CNAME para implantar componentes da Web externos hospedados pela instância de marketing do Adobe Campaign.  Isso permitirá que os componentes da Web (por exemplo, web.customer.com) sejam acessíveis publicamente à Internet e rotulados com o domínio do cliente.

Os Firewall(s) também precisarão ser configurados para permitir acesso à instância de marketing do Adobe Campaign que hospeda esses componentes da Web (na porta 80 ou 443).

**Recommendations de práticas recomendadas:**

O subdomínio para hospedar componentes da Web estará visível para os clientes, portanto, certifique-se de torná-lo corretamente marcado e simples de lembrar, pois pode ser necessário digitar manualmente, por exemplo: https://web.customer.com.
Se algum formulário precisar ser hospedado em páginas seguras (HTTPS), a configuração técnica adicional será necessária, descrita abaixo.

| Subdomínio delegado | Instruções DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME  `<internal customer server>` |

## Serviços renderizados

Na sequência destas delegações, a infraestrutura criada pela Adobe garante que os seguintes serviços sejam executados para cada domínio de envio delegado ou com alias CNAME:

* Criação de caixas de entrada postmaster@ e abusivas@
* Configuração de loops de comentários para o domínio delegado
* Mediante solicitação, o Adobe também configurará um registro DMARC, conforme especificado. Seu consultor de capacidade de entrega pode ajudar a projetar uma política DMARC de longo prazo e planejar seus domínios de envio.
Os parâmetros estabelecidos pelo Adobe só são válidos a partir do momento em que a delegação foi concluída e depois verificada pelo Adobe, e permanecem funcionais.  Todas as ofertas da Adobe Campaign Cloud incluem delegação de nome de domínio como padrão.

## Condições de faturação e de execução

* De acordo com o contrato inicial e o tipo de pacote selecionado, podem ser incluídas outras delegações para além das que foram incluídas como norma para além desta delegação inicial,
* Para além destas delegações incluídas, serão cobradas delegações adicionais,
* O método de faturação destas delegações adicionais é efetuado a um custo mensal adicional, tal como especificado no contrato inicial.

Essas delegações serão aceitas desde que o CLIENTE escolha os nomes de domínio associados que são dedicados aos deliveries por meio da ferramenta Adobe Campaign e que os pré-requisitos de delegação detalhados no documento relevante sejam implementados corretamente.

## Descontinuação dos serviços

A qualquer momento, o CLIENTE poderá fazer uma demanda por escrito para deixar de se beneficiar dos serviços de delegação e assumir elas próprias as configurações de DNS necessárias.

Se isso acontecer, o Adobe fornecerá ao CLIENT uma estimativa detalhando o número de dias de serviço necessários para retornar ao modo de delegação de não domínio.

O Adobe ficará isento de qualquer responsabilidade pelo envolvimento da Taxa de Entregabilidade acima mencionada se o Cliente não cumprir os compromissos estabelecidos acima.

A cessação do Serviço Marketing Cloud resultará automaticamente no fim das delegações de domínio e na manutenção de DNS para esses domínios pelo Adobe.

## Monitorar subdomínios usando o Painel de controle do Campaign

Depois que os subdomínios forem configurados para sua instância, você poderá monitorá-los usando o Painel de controle do Campaign.

Isso permite visualizar todos os subdomínios que você delegou à Adobe Campaign, bem como solicitar a renovação dos certificados SSL.

Para obter mais informações, consulte a [documentação dedicada](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates).

>[!NOTE]
>
>[Os ](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR) Painéis de Controle estão disponíveis somente para clientes que usam o Adobe Managed Services.