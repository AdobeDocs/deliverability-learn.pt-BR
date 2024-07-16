---
title: Coleta de endereços e crescimento de listas
description: Saiba quais são as melhores fontes para novos endereços de email, como garantir alta qualidade dos dados e alinhamento às diretrizes legais.
topics: Deliverability
jira: KT-7063
thumbnail: kt7063.jpg
doc-type: article
activity: understand
team: TM
exl-id: 350950dc-4703-402a-8e22-3862f4e21d52
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '1594'
ht-degree: 3%

---

# Coleta de endereços e crescimento de listas

As melhores fontes de novos endereços de email são fontes diretas, como inscrições em seu site ou em lojas físicas. Nessas situações, você pode controlar a experiência para garantir que ela seja positiva e que o assinante esteja interessado em obter email da sua marca.

Algumas observações sobre esses métodos de inscrição:

A coleção de listas de **Armazenamento físico** pode apresentar desafios devido a entradas de endereço verbais ou escritas que causam erros ortográficos nos endereços. Recomenda-se enviar um email de confirmação o mais rápido possível após as inscrições na loja.

A forma mais comum de **inscrição no site** é a &quot;aceitação única&quot;. É o padrão mínimo absoluto que você deve usar para adquirir endereços de email. A aceitação única ocorre quando o detentor de um endereço de email específico concede a um remetente permissão para enviar emails de marketing, geralmente enviando o endereço por meio de um formulário web ou inscrições na loja. Embora seja possível executar uma campanha de email bem-sucedida usando esse método, ela pode ser a causa de alguns problemas.

* Endereços de email não confirmados podem ter erros de digitação ou serem malformados, incorretos ou usados de forma mal intencionada. Erros de digitação e endereços malformados causam altas taxas de rejeição, o que pode e provoca bloqueios emitidos por ISPs ou perda de reputação de IP.

* O envio mal-intencionado de armadilhas de spam conhecidas (às vezes chamadas de &quot;envenenamento de lista&quot;) pode causar enormes problemas na entrega e na reputação se o proprietário dessa armadilha agir. É impossível saber se o recipient realmente deseja ser adicionado a uma lista de marketing sem uma confirmação. Isso torna igualmente impossível definir as expectativas do recipient e pode levar a um aumento nas reclamações de spam — e, às vezes, incluindo na lista de bloqueios se o email coletado é uma interceptação de spam.

Para obter orientação sobre como minimizar os problemas apresentados no armazenamento físico e na aceitação única, acesse a seção [Qualidade e higiene dos dados](#data-quality-and-hygiene) neste guia para obter os detalhes e os benefícios da aceitação dupla.

>[!NOTE]
>
>Os assinantes geralmente usam endereços descartáveis, endereços expirados ou endereços que não são deles para obter o que desejam de um site, mas também evitar serem adicionados a listas de marketing. Quando isso acontece, as listas de profissionais de marketing resultam em um alto número de devoluções permanentes, altas taxas de reclamação de spam e assinantes que não clicam, abrem ou se envolvem positivamente com emails. Ele pode ser visto como um sinalizador vermelho para provedores de caixa de correio e ISPs.

## Formulários de inscrição

Além de adicionar os campos para os dados, que você deseja coletar sobre os novos assinantes, há algumas outras coisas que você deve fazer com o formulário de inscrição no site.

* Defina expectativas claras com o assinante de que ele está concordando em receber emails, o que receberá e com que frequência o receberá.
* Adicione opções que permitam ao assinante selecionar a frequência ou o tipo de comunicações que recebe. Essas opções permitem conhecer as preferências do assinante desde o início, para que você possa fornecer a melhor experiência possível ao novo cliente.
* Equilibre o risco de perder o interesse do assinante durante o processo de inscrição solicitando o máximo de informações possível. Coisas como aniversário, local ou interesses ajudam a enviar conteúdo mais personalizado. Os assinantes de cada marca têm expectativas e limites de tolerância diferentes, portanto, testar é fundamental para encontrar o equilíbrio certo para sua situação.

>[!NOTE]
>
> Não use caixas pré-marcadas durante o processo de inscrição. Embora isso possa causar problemas legalmente, também é uma experiência negativa para o cliente.

## Qualidade e higiene dos dados

Coletar dados é apenas parte do desafio. Você também deve garantir que os dados sejam precisos e utilizáveis. Você deve ter filtros de formato básicos em vigor. Um endereço de email não é válido se não incluir &quot;@&quot; ou &quot;.&quot; por exemplo. Não permita endereços de alias comuns, que também são chamados de contas de função (como &quot;informações&quot;, &quot;administrador&quot;, &quot;vendas&quot;, &quot;suporte&quot;). As contas de função podem apresentar risco porque, por sua natureza, o recipient contém um grupo de pessoas em vez de um único assinante. As expectativas e a tolerância podem variar em um grupo, o que pode gerar reclamações, variação de engajamento, cancelamentos de subscrições e confusão geral.

Estas são algumas soluções para problemas comuns que você pode encontrar com os dados de endereço de email:

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] é considerado a prática recomendada de capacidade de entrega pela maioria dos especialistas em email. Se você estiver tendo problemas com armadilhas de spam ou reclamações em seus emails de boas-vindas, o DOI é uma boa maneira de garantir que o assinante que recebe seus emails realmente se inscreveu em seu programa de email e deseja receber seus emails.

O DOI consiste em enviar um email de confirmação para o endereço de email do assinante que se inscreveu no seu programa de email e que contém um link que deve ser clicado para confirmar o consentimento. Com esse método de aquisição, se o assinante não confirmar, o remetente não enviará mais emails. Informe os novos assinantes que você está fazendo isso no site, incentivando-os a concluir a inscrição antes de continuar. Esse método mostra uma redução no número de inscrições, mas as pessoas que se inscrevem tendem a se envolver muito e permanecer por um longo período. Normalmente, isso resulta em um ROI muito maior para o remetente.

**Campo oculto**
Aplicar um campo oculto em seu formulário de inscrição é uma ótima maneira de diferenciar as inscrições de bot automatizadas dos assinantes humanos reais. Como o campo de dados não está visível, oculto no código HTML, um bot inserirá dados em que um humano não estaria. Usando esse método, você pode criar regras para suprimir qualquer inscrição que inclua dados preenchidos nesse campo oculto.

**[!DNL re-CAPTCHA] é um método de validação que você pode usar para reduzir as chances do assinante ser um bot e não uma pessoa real. Há várias versões, algumas das quais contêm identificação de palavras-chave ou imagens. Algumas versões são mais eficazes que outras, e o que você ganha em prevenção de problemas de segurança e capacidade de entrega é muito maior do que qualquer impacto negativo nas conversões.

## Diretrizes legais

Consulte seus advogados para interpretar as leis locais e nacionais relacionadas ao email. Lembre-se de que as leis de email variam muito de acordo com os países e, às vezes, entre as diferentes regiões locais de um país.

* Colete as informações de localização de um assinante para estar em conformidade com as leis de país do assinante. Sem esse detalhe, você pode ficar limitado em como vender para o assinante.
* Todas as leis relevantes são determinadas pela localização do recipient, não do remetente. Portanto, você deve conhecer e seguir as leis de qualquer país onde você possa ter um assinante.
* Muitas vezes, é difícil saber com total certeza o país de residência do assinante. Os dados fornecidos pelo cliente podem estar desatualizados e os dados de localização de pixels podem ser imprecisos devido à VPN ou ao armazenamento de imagens, como no Gmail e no Yahoo. Na dúvida, é mais seguro aplicar as leis e diretrizes mais rigorosas possíveis.

## Outros métodos de coleção de listas não recomendados

Há muitas outras maneiras de coletar endereços, cada uma com suas próprias oportunidades, desafios e desvantagens. O Adobe não recomenda esses itens em geral, pois o uso é frequentemente restrito por meio de políticas de uso aceitáveis do provedor. Examinaremos alguns exemplos comuns para que você possa aprender os perigos e ajudá-lo a limitar ou evitar os riscos:

**Comprar ou alugar uma lista**
Há muitos tipos de endereços de email por aí. Email primário, email comercial, email escolar, email secundário e email inativo, para citar alguns. Os tipos de endereços coletados e compartilhados por meio de listas compradas ou alugadas raramente são contas de email principais, que são onde quase toda a atividade de envolvimento e compra ocorre.

Se você tiver sorte, obterá contas secundárias, nas quais as pessoas procuram ofertas e ofertas quando estiverem prontas para comprar algo. Isso geralmente resulta em níveis baixos de engajamento, se houver. Se você não tiver sorte, a lista está cheia de emails inativos, que agora podem ser armadilhas de spam. Geralmente, você recebe uma combinação de emails secundários e inativos. Em geral, a qualidade desses tipos de listas causa mais danos do que benefícios a um programa de email. Esta prática é proibida pela [Política de Uso Aceitável da Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Listas anexadas**
Esses são clientes que optaram por se envolver com a sua marca, o que é ótimo. Mas eles escolheram se engajar por um método diferente do email (na loja, nas redes sociais etc.). Eles não podiam ser receptivos a receber um email não solicitado de você e também podem se preocupar com a maneira como você obteve o endereço de email deles, pois não o forneceram. Esse método tem o risco de transformar um cliente ou cliente potencial que interagiu com sua marca em um detrator que não confia mais em sua marca e, em vez disso, vai para a concorrência. Esta prática é proibida pela [Política de Uso Aceitável da Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Feira de negócios ou outra coleção de eventos**
Coletar endereços em um estande ou por meio de outro método oficial, com marca clara, pode ser útil. O risco é que muitos eventos como esse coletem todos os endereços e os distribuam pelo promotor ou host do evento. O que significa que os proprietários desses endereços de email nunca solicitaram o recebimento de emails da sua marca. É provável que esses assinantes reclamem e marquem seus emails como spam e talvez eles não tenham fornecido informações de contato precisas.

**Sweepstakes**

Os sorteios fornecem rapidamente um grande número de endereços de email. Mas esses assinantes querem o prêmio, não seus emails. Eles podem nem ter prestado atenção ao nome de quem estaria entrando em contato com eles. É provável que eles reclamem e marquem seus e-mails como spam e é improvável que façam uma compra ou engajamento.

## Recursos específicos do produto

**Adobe Campaign Classic**

* [Criar um formulário de assinatura com aceitação dupla](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=pt-BR#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Processo de aceitação dupla](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=br#communication-channels)
