---
title: Coleta de endereços e crescimento de listas
description: 'Saiba quais são as melhores fontes para novos endereços de email, como garantir alta qualidade dos dados e alinhamento às diretrizes legais. '
feature: Públicos-alvo
topics: Deliverability
kt: 7063
thumbnail: kt7063.jpg
doc-type: article
activity: understand
team: TM
translation-type: tm+mt
source-git-commit: 131e3f06ac8d593d4b67711ee3688ff895aa380c
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 0%

---


# Coleta de endereços e crescimento de listas

As melhores fontes de novos endereços de email são fontes diretas, como inscrições em seu site ou em lojas físicas. Nessas situações, você pode controlar a experiência para garantir que ela seja positiva e que o assinante esteja interessado em receber emails de sua marca.

Algumas observações sobre esses métodos de inscrição:

**A coleção de** listas de armazenamento físico pode apresentar desafios devido a entradas de endereço verbais ou escritas que causam erro ortográfico nos endereços. É recomendado enviar um email de confirmação o mais rápido possível após inscrições na loja.

A forma mais comum de **inscrição no site** é &quot;aceitação única&quot;. É o padrão mínimo absoluto que você deve usar para adquirir endereços de email. A aceitação única ocorre quando o titular de um endereço de email específico concede a um remetente permissão para enviar emails de marketing, geralmente ao enviar o endereço por meio de um formulário da Web ou de assinaturas na loja. Embora seja possível executar uma campanha de email bem-sucedida usando esse método, isso pode ser a causa de alguns problemas.

* Endereços de email não confirmados podem ter erros de digitação ou ser malformados, incorretos ou maliciosos. Tipos e endereços malformados causam altas taxas de rejeição, o que pode e provoca bloqueios emitidos por ISPs ou perda de reputação do IP.

* O envio mal-intencionado de interceptações de spam conhecidas (às vezes chamadas de &quot;envenenamento por lista&quot;) pode causar grandes problemas de delivery e reputação se o proprietário dessa armadilha tomar uma ação. É impossível saber se o recipient realmente deseja ser adicionado a uma lista de marketing sem uma confirmação. Isso torna igualmente impossível definir as expectativas do recipient e pode levar a maiores reclamações de spam, e às vezes à inclusão na blacklist se o email coletado for uma armadilha de spam.

Para obter orientação sobre como minimizar os problemas apresentados na loja física e na aceitação única, acesse a seção [Data quality and clean&lt; a1/> neste guia para obter os detalhes e os benefícios da aceitação dupla.](#data-quality-and-hygiene)

>[!NOTE]
>
>Os assinantes geralmente usam endereços lances, endereços expirados ou endereços que não são deles para obter o que desejam de um site, mas também evitar de ser adicionados a listas de marketing. Quando isso acontece, as listas dos profissionais de marketing resultam em um alto número de devoluções permanentes, altas taxas de reclamação de spam e assinantes que não clicam, abrem ou interagem positivamente com emails. Ele pode ser visto como um sinalizador vermelho para provedores de caixa de correio e ISPs.

## Formulários de inscrição

Além de adicionar os campos para os dados, você deseja coletar sobre seus novos assinantes, há outras coisas que você deve fazer com seu formulário de inscrição no site.

* Defina expectativas claras com o assinante de que ele está concordando em receber emails, o que eles receberão e com que frequência eles o receberão.
* Adicione opções que permitem que o assinante selecione a frequência ou o tipo de comunicação que recebe. Essas opções permitem conhecer as preferências do assinante desde o início, para que você possa fornecer a melhor experiência possível para seu novo cliente.
* Equilibre o risco de perder o interesse do assinante durante o processo de inscrição, solicitando a maior quantidade possível de informações. Coisas como aniversário, localização ou interesses deles ajudam a enviar conteúdo mais personalizado. Todos os assinantes de marcas têm expectativas e limites de tolerância diferentes, portanto, testar é fundamental para encontrar o equilíbrio correto para sua situação.

>[!NOTE]
>
> Não use caixas pré-marcadas durante o processo de inscrição. Embora possa causar problemas legais, também é uma experiência negativa para o cliente.

## Qualidade e higiene dos dados

A coleta de dados é apenas parte do desafio. Você também deve garantir que os dados sejam precisos e utilizáveis. Você deve ter filtros de formato básicos em vigor. Um endereço de email não é válido se não incluir &quot;@&quot; ou &quot;.&quot; por exemplo. Certifique-se de não permitir endereços de alias comuns, que também são chamados de contas de função (como &quot;informações&quot;, &quot;administrador&quot;, &quot;vendas&quot;, &quot;suporte&quot; ). As contas de função podem apresentar risco porque, por sua natureza, o recipient contém um grupo de pessoas em vez de um único assinante. As expectativas e a tolerância podem variar dentro de um grupo, o que corre o risco de reclamações, envolvimento variável, cancelamentos de assinaturas e confusão geral.

Estas são algumas soluções para problemas comuns que você pode encontrar com seus dados de endereço de email:

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] O é considerado a melhor prática de deliverability pela maioria dos especialistas em email. Se tiver problemas com armadilhas de spam ou reclamações nos emails de boas-vindas, o DOI é uma boa maneira de garantir que o assinante que recebe seus emails realmente se inscreveu no seu programa de email e deseja receber seus emails.

O DOI consiste em enviar um email de confirmação para o endereço de email do assinante que se inscreveu no seu programa de email que contém um link que deve ser clicado para confirmar o consentimento. Com esse método de aquisição, se o assinante não confirmar, o remetente não enviará mais emails. Informe aos novos assinantes que você está fazendo isso no site, incentivando-os a concluir a inscrição antes de continuar. Este método permite reduzir o número de inscrições, mas as pessoas que se inscrevem tendem a ser altamente envolvidas e a permanecer a longo prazo. Geralmente resulta em um ROI muito mais alto para o remetente.

**Campo**
ocultoA aplicação de um campo oculto no formulário de inscrição é uma ótima maneira de diferenciar inscrições automatizadas de bot de assinantes humanos reais. Como o campo de dados não é visível, oculto no código HTML, um bot inserirá dados onde um humano não o faria. Usando esse método, você pode criar regras para suprimir qualquer inscrição que inclua dados preenchidos nesse campo oculto.

**[!DNL re-CAPTCHA] é um método de validação que pode ser usado para reduzir as chances de o assinante ser um bot e não uma pessoa real. Há várias versões, algumas contendo identificação de palavra-chave ou imagens. Algumas versões são mais eficazes do que outras, e o que você ganha em segurança e na prevenção de problemas de entrega é muito mais alto do que qualquer impacto negativo nas conversões.

## Orientações jurídicas

Consulte seus advogados para interpretar as leis locais e nacionais sobre email. Lembre-se de que as leis de e-mail variam muito de país para país e, às vezes, de país para país.

* Certifique-se de coletar as informações de localização de um assinante para que você esteja em conformidade com as leis de país do assinante. Sem esse detalhe, você pode se limitar a comercializar para o assinante.
* As leis relevantes são determinadas pela localização do recipient, não pelo remetente. Então você deve conhecer e seguir as leis de qualquer país onde você possa ter um assinante.
* Geralmente é difícil saber com total certeza o país de residência do assinante. Os dados fornecidos pelo cliente podem estar desatualizados, e os dados de localização de pixel podem estar imprecisos devido à VPN ou ao armazenamento de imagem, como com Gmail e Yahoo. Em caso de dúvida, é mais seguro aplicar as leis e orientações mais rigorosas possíveis.

## Outros métodos de coleta de listas não recomendados

Há muitas outras maneiras de coletar endereços, cada um com suas próprias oportunidades, desafios e desvantagens. O Adobe não os recomenda em geral, pois o uso geralmente é restrito por meio de políticas de uso aceitáveis para o provedor. Vamos ver alguns exemplos comuns, para que você possa aprender os perigos para ajudá-lo a limitar ou evitar os riscos:

**Compre ou alugue uma**
listaHá muitos tipos de endereços de email por aí. E-mail principal, e-mails de trabalho, e-mails escolares, e-mails secundários e emails inativos para nomear alguns. Os tipos de endereços coletados e compartilhados por meio de listas compradas ou alugadas raramente são contas de email primárias, que são onde quase todas as atividades de envolvimento e compra ocorrem.

Se tiver sorte, você terá contas secundárias, onde as pessoas procuram ofertas e ofertas quando estão prontas para comprar algo. Isso geralmente resulta em níveis baixos de engajamento, se houver. Se você não tiver sorte, a lista está cheia de emails inativos, que agora podem ser armadilhas de spam. Geralmente, você obtém uma combinação de emails secundários e inativos. Em geral, a qualidade desses tipos de listas é mais prejudicial do que boa para um programa de email. Esta prática é proibida pela [Política de Uso Aceitável do Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Listas**
anexarEsses são clientes que optaram por se envolver com sua marca, o que é ótimo. Mas eles optaram por participar de um método diferente de email (na loja, mídia social etc.). Eles não podiam ser receptivos a receber um email não solicitado de você e também podem se preocupar com como você ganhou seu endereço de email, pois não o forneciam. Esse método tem o risco de transformar um cliente ou cliente potencial que tenha contrato com sua marca em um destrator que não confia mais em sua marca e vai para a concorrência. Esta prática é proibida pela [Política de Uso Aceitável do Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Programa comercial ou outra**
coleção de eventosA coleta de endereços em uma cabine ou por meio de outro método oficial com marca clara pode ser útil. O risco é que muitos eventos como esse coletem todos os endereços e os distribuam por meio do promotor ou do host do evento. O que significa que os proprietários desses endereços de email nunca solicitaram receber emails de sua marca. Esses assinantes provavelmente reclamam e marcam seu email como spam e talvez não tenham fornecido informações de contato precisas.

****
SorteioOs sorteios fornecem um grande número de endereços de email rapidamente. Mas esses assinantes querem o prêmio, não seus emails. Eles podem nem ter prestado atenção ao nome de quem estaria se aproximando deles. É provável que eles reclamem e marquem seu email como spam, e talvez seja improvável que alguma vez façam uma compra ou façam uma compra.
