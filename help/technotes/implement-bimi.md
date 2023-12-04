---
title: Implementar os indicadores de marca do Gmail para identificação de mensagem (BIMI)
description: Saiba como implementar o BIMI
topics: Deliverability
role: Admin
level: Beginner
jira: KT-14079
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: ad0646da88f2b1474e74b6c741d0dd5701e88978
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 0%

---

# Implementar [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) é um padrão do setor que permite que um logotipo aprovado apareça ao lado do email de um remetente nas plataformas participantes.

Com esse padrão, uma marca pode determinar um logotipo que deve ser exibido nas caixas de entrada dos provedores de caixa de correio. Depois de publicado em um registro chamado BIMI DNS (Domain Name System, Sistema de nomes de domínio), um provedor de caixa de correio pode coletar esse logotipo e exibi-lo na caixa de entrada, se determinados critérios forem atendidos.

Diferentes provedores fazem implementações diferentes, mas os benefícios são claros: destacar-se na caixa de entrada, criar confiança e estar no controle do que está sendo mostrado.

O BIMI não melhora diretamente a capacidade de entrega ou a sua reputação. Ele pode ajudar a criar mais confiança com seus recipients e, portanto, impulsionar mais engajamento.

## Como se parece?

Você pode encontrar alguns exemplos de implementações de diferentes provedores e mais detalhes sobre quais provedores exibem o logotipo no [Página do grupo BIMI](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## Quem é o grupo BIMI?

O grupo BIMI é um grupo de trabalho que desenvolve o BIMI, pois abrange não só o logotipo, mas também os requisitos técnicos, legais e de conformidade.

O Grupo BIMI é composto por várias partes interessadas de diferentes áreas do setor: Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail e Validity.

## Quem está apoiando o BIMI?

A lista de provedores de caixa de correio que oferecem suporte ao BIMI está crescendo constantemente. Uma lista atualizada pode ser encontrada [aqui](https://bimigroup.org/bimi-infographic/){target="_blank"} para provedores de suporte e provedores que consideram BIMI.

A partir de abril de 2023, a lista inclui Gmail, Yahoo, La Poste, Fastmail, Onet.pl e Zone, Proofpoint como um appliance antisspam e Apple Mail (da iOS 16 em diante).

Os nomes mais proeminentes nessa lista são obviamente Yahoo, Gmail e um adotante recente: Apple com iOS 16. O Apple desempenha um papel especial na combinação, pois não é um provedor de caixa de correio, mas adicionou suporte a BIMI ao aplicativo de email nativo. O e-mail compatível com o BIMI será exibido como &quot;e-mail digitalmente certificado&quot;, o que aumenta a confiança na marca.

## Implementação

A implementação do BIMI vem em várias etapas:

1. Implementação DMARC (Domain based Message Authentication, Reporting and Conformance) no nível de imposição para o domínio de envio e seu domínio organizacional - [Saiba mais](#dmarc)

1. Criação do logotipo da sua marca no formato SVG TinyPS - [Saiba mais](#create-brand-logo)

1. Inscrever-se para um Certificado de Marca Verificada (necessário apenas para alguns provedores) - [Saiba mais](#vmc)

1. Publicar um registro DNS BIMI com o logotipo e o certificado - [Saiba mais](#publish-bimi-record)

1. Ter uma boa reputação - [Saiba mais](#good-reputation)

>[!NOTE]
>
>Observe que todas as etapas precisam ser desmarcadas.


### DMARC {#dmarc}

DMARC é um padrão que permite que a marca decida o que um provedor de caixa de correio deve fazer com um email que falha [autenticação](../additional-resources/authentication.md). As chamadas políticas variam de &quot;nenhum&quot; a &quot;quarentena&quot; (inserção de pastas de spam) a &quot;rejeitar&quot; (bloquear completamente o email). Apenas as duas últimas políticas são chamadas de &quot;imposição&quot; e qualificam-se para BIMI. O email enviado pelo Adobe está passando a autenticação, já que o SPF (Estrutura de Política do Remetente) e o DKIM (Chaves do Domínio e Email Identificado) estão configurados por padrão. O Adobe está configurando o DMARC no seu domínio de envio mediante solicitação.

Além do DMARC no domínio de envio, o DMARC também precisa ser empregado no nível de imposição do domínio organizacional (se o domínio de envio for news.example.com, example.com é o domínio organizacional).

### Criação do logotipo da sua marca {#create-brand-logo}

A criação do logotipo precisa seguir os requisitos para 100%. Consulte sempre a [Diretrizes do grupo BIMI](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

O logotipo precisa ser armazenado em um local seguro (HTTPS), caso uma rede de entrega de conteúdo (CDN) seja usada, qualquer proteção que impeça os Provedores de Caixa de Correio de obter o logotipo (por exemplo, Proteção de bot) precisa ser desativada.

Além dos requisitos técnicos, há algumas recomendações práticas como ter um logotipo quadrado, ter uma cor sólida como fundo e outros. Essas recomendações são para melhor visualização. Alguns provedores têm seus próprios requisitos, que são adicionais aos do grupo de trabalho BIMI. [Gmail](https://support.google.com/a/answer/10911027?sjid=903725605955621707-EU){target="_blank"}. por exemplo, exige que o logotipo tenha pelo menos 96 x 96 pixels.
Observe que a não conformidade pode impedir a exibição do logotipo.

### Certificado de Marca Verificada (VMC) {#vmc}

Um Certificado de Marca Verificada (VMC) só é necessário para alguns provedores de caixa de correio, como Gmail e Apple, e, portanto, é opcional. Recomendamos obter um VMC para realmente aproveitar o BIMI.

Um Certificado de Marca Verificada é uma validação legal de que a marca pode usar o logotipo. Uma autoridade de certificação verificará isso através do escritório de marcas comerciais onde o logotipo da marca está registrado. Esse processo envolve várias validações e verificações legais e pode levar algum tempo. Atualmente, duas CAs (autoridades de certificação) estão emitindo VMCs: Digicert e Entrust. O primeiro conjunto de escritórios de marcas registradas são EUA, Canadá, UE, Reino Unido, Alemanha, Japão, Austrália e Espanha.

Como regra geral, você precisará de um VMC por logotipo. Ter um VMC para seu domínio organizacional cobrirá subdomínios e, com um recurso adicionado, até domínios diferentes. Caso você tenha logotipos diferentes, é necessário mais de um VMC. A Autoridade de Certificação ou o parceiro com o qual você escolher trabalhar ajudará você a configurar isso.

>[!NOTE]
>
>Observe que os VMCs têm uma taxa anual.

### Publicação do registro BIMI {#publish-bimi-record}

Depois que as outras etapas forem executadas, o registro de DNS BIMI poderá ser publicado. O registro tem esta aparência:

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;PEM URL&quot; é o local do arquivo do Certificado de marca verificada.

Para o domínio de envio, isso precisa ser feito pelo Adobe.

### Boa reputação {#good-reputation}

A confiança é a chave para o BIMI. O usuário confia em seu provedor de caixa de correio para mostrar apenas o logotipo de remetentes legítimos, portanto, o provedor de caixa de correio precisa confiar na marca, e isso está sendo feito pela reputação do remetente. Se você tiver alta reputação, tudo é bom, mas se não for, o logotipo não será exibido. Infelizmente, não há informações ou métricas que possamos examinar para descobrir se a reputação é alta o suficiente.

Mesmo passar pelo esforço e as despesas de um VMC não tira essa parte. Se o provedor de caixa de correio não confiar na marca, o logotipo não será exibido.

## Dicas e truques

* O Grupo BIMI oferece uma ferramenta útil de validação para BIMI. Se você quiser verificar novamente se tudo está configurado e pronto, ou apenas se o logotipo é compatível, acesse [este link](https://bimigroup.org/bimi-generator/){target="_blank"}. Para o último, clique em **[!UICONTROL Generate BIMI]** e insira um domínio de espaço reservado, mas o URL do logotipo correto. O inspetor informará se o logotipo está em conformidade.

* Você pode começar com segurança sem um VMC, não há dano em sua reputação se seu registro BIMI não incluir um URL VMC, mas o logotipo já pode ser mostrado no Yahoo.

* A implementação do DMARC a nível organizacional é uma tarefa de grande envergadura. Algumas empresas são especializadas para ajudar as marcas a alcançarem uma adoção completa do DMARC.

* Uma extensa lista de perguntas frequentes é publicada [aqui](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
