---
title: Implementar os indicadores de marca do Gmail para identificação de mensagem (BIMI)
description: Saiba como implementar o BIMI
topics: Deliverability
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: 05f6cd331f4e610e2442d43405333823644d349e
workflow-type: tm+mt
source-wordcount: '1063'
ht-degree: 0%

---

# Implementar [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) é um padrão do setor que permite que um logotipo aprovado apareça ao lado do email de um remetente em plataformas participantes.

Com esse padrão, uma marca pode determinar um logotipo que deve ser exibido nas caixas de entrada dos provedores de caixa de correio. Depois de publicado em um registro chamado BIMI DNS (Domain Name System), um provedor de caixa de correio pode selecionar esse logotipo e exibi-lo na caixa de entrada se determinados critérios forem atendidos.

Fornecedores diferentes fazem implementações diferentes, mas os benefícios são claros: destacar-se na caixa de entrada, reforçar a confiança e estar no controle do que está sendo mostrado.

O BIMI não melhora diretamente a capacidade de entrega ou sua reputação. Ela pode ajudar a criar mais confiança com seus recipients e, portanto, impulsionar mais engajamento.

## Como se parece?

Você pode encontrar alguns exemplos de implementações de diferentes provedores e mais detalhes sobre quais provedores exibem o logotipo na [Página do Grupo BIMI](https://bimigroup.org/where-is-my-bimi-logo-displayed/).

## Quem é o Grupo BIMI?

O grupo BIMI é um grupo de trabalho que desenvolve a BIMI, uma vez que abrange não só o logótipo, mas também os requisitos técnicos, jurídicos e de conformidade.

O grupo BIMI é composto por vários interessados de diferentes setores da indústria: Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail e Validity.

## Quem apoia a BIMI?

A lista de provedores de caixas de correio que apoia a BIMI está crescendo continuamente. Uma lista atualizada pode ser encontrada [here](https://bimigroup.org/bimi-infographic/) quer para os prestadores de apoio, quer para os prestadores que considerem a BIMI.

A partir de abril de 2023, a lista inclui Gmail, Yahoo, La Poste, Fastmail, Onet.pl e Zone, Proofpoint como dispositivo antisspam e Apple Mail (a partir do iOS 16).

Os nomes mais proeminentes dessa lista são obviamente Yahoo, Gmail e um adotante recente: Apple com iOS 16. A Apple desempenha um papel especial na combinação, pois não é um provedor de caixa de correio, mas adicionou o suporte BIMI ao aplicativo de email nativo. Os emails compatíveis com o BIMI serão exibidos como &quot;email certificado digitalmente&quot;, o que aumenta a confiança na marca.

## Implementação

A implementação do BIMI vem em várias etapas:

1. Implementação DMARC (Domain-based Message Authentication, Reporting and Conformance) no nível de imposição para o domínio de envio e seu domínio organizacional - [Saiba mais](#dmarc)

1. Criação do logotipo da sua marca no formato SVG TinyPS - [Saiba mais](#create-brand-logo)

1. Inscrever-se em um Certificado de Marca Verificado (necessário apenas para alguns provedores) - [Saiba mais](#vmc)

1. Publicar um registro DNS do BIMI com o logotipo e o certificado - [Saiba mais](#publish-bimi-record)

1. Boa reputação - [Saiba mais](#good-reputation)

>[!NOTE]
>
>Observe que todas as etapas precisam ser verificadas.


### DMARC {#dmarc}

O DMARC é um padrão que permite à marca decidir o que um provedor de caixa de correio deve fazer com um email que falha [autenticação](../additional-resources/authentication.md). As chamadas políticas variam de &quot;nenhum&quot; em &quot;quarentena&quot; (posicionamento da pasta de spam) a &quot;rejeitar&quot; (bloquear totalmente o email). Apenas as duas últimas políticas são chamadas de &quot;execução&quot; e podem beneficiar da BIMI. O email enviado pelo Adobe está transmitindo a autenticação, pois o SPF (Estrutura de Política do Remetente) e o DKIM (Domain Keys Identified Mail) são configurados por padrão. O Adobe está configurando o DMARC em seu domínio de envio mediante solicitação.

Além do DMARC no domínio de envio, o DMARC também precisa ser empregado no nível de imposição para o domínio organizacional (se o domínio de envio for news.example.com, example.com é o domínio organizacional).

### Criação do logotipo de sua marca {#create-brand-logo}

A criação do logotipo precisa seguir os requisitos para 100%. Consulte sempre a [Orientações do Grupo BIMI](https://bimigroup.org/creating-bimi-svg-logo-files/).

Além dos requisitos técnicos, há algumas recomendações práticas como ter um logotipo quadrado, ter uma cor sólida como fundo e outras. Essas recomendações são para melhor visualização.
Observe que a não conformidade pode fazer com que o logotipo não seja exibido.

### Certificado de Marca Verificado (VMC) {#vmc}

Um Certificado de Marca Verificada (VMC) é necessário apenas para alguns provedores de caixa de correio, como Gmail e Apple, e, portanto, é opcional. No entanto, recomendamos obter um VMC para realmente utilizar o BIMI.

Um Certificado de Marca Verificado é uma validação legal de que a marca pode usar o logotipo. Uma autoridade certificadora verificará esse fato através do escritório de marcas comerciais onde o logotipo da marca está registrado. Esse processo envolve várias validações e verificações legais e pode levar algum tempo. Atualmente, duas AC (autoridades de certificação) estão emitindo VMCs: Digicert e Entrust. O primeiro conjunto de escritórios de marcas comerciais é EUA, Canadá, UE, Reino Unido, Alemanha, Japão, Austrália e Espanha.

Como regra geral, você precisará de um VMC por logotipo. Ter um VMC para seu domínio organizacional cobrirá subdomínios e com um recurso adicionado, até mesmo domínios diferentes. Caso tenha logotipos diferentes, é necessário mais de um VMC. A Autoridade de Certificação ou o parceiro com o qual você opta por trabalhar ajudará você a configurar isso.

>[!NOTE]
>
>Observe que os VMCs têm uma taxa anual.

### Publicação do registro do BIMI {#publish-bimi-record}

Depois que as outras etapas forem executadas, o registro DNS do BIMI poderá ser publicado. O registro tem esta aparência:

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;URL PEM&quot; é o local do arquivo do Certificado de Marca Verificado.

Para o seu domínio de envio, isso precisa ser feito pelo Adobe.

### Boa reputação {#good-reputation}

A confiança é fundamental para o BIMI. O usuário confia no provedor de caixa de correio para mostrar apenas o logotipo de remetentes legítimos, de modo que o provedor de caixa de correio precisa confiar na marca, e isso está sendo feito pela reputação do remetente. Se você tiver uma reputação alta, tudo é bom, mas se você não tiver, o logotipo não será exibido. Infelizmente, não há informações ou métricas que possamos observar para descobrir se a reputação é alta o suficiente.

Mesmo passar pelo esforço e despesas de um VMC não tira essa parte. Se o provedor de caixa de correio não confiar na marca, o logotipo não será exibido.

## Dicas e truques

* O Grupo BIMI oferece um instrumento de validação útil para o BIMI. Se quiser verificar novamente se tudo está pronto e configurado, ou se deseja apenas ver se o logotipo está em conformidade, acesse [este link](https://bimigroup.org/bimi-generator/). Para o último clique **[!UICONTROL Generate BIMI]** e insira um domínio de espaço reservado, mas o URL de logotipo correto. O inspetor informará se o logotipo é compatível.

* Você pode começar com segurança sem um VMC, não há nenhum dano na sua reputação se seu registro do BIMI não incluir um URL do VMC, mas o logotipo já pode ser mostrado no Yahoo.

* A implementação da DMARC a nível organizacional é uma grande empresa. Algumas empresas são especializadas para ajudar as marcas a alcançar uma adoção completa do DMARC.

* Uma extensa lista de perguntas frequentes é publicada [here](https://bimigroup.org/faqs-for-senders-esps/).
