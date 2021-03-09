---
title: Armadilhas de spam
description: Saiba mais sobre os diferentes tipos de armadilhas de spam.
feature: Métricas
topics: Deliverability
kt: 7050
thumbnail: kt7050.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 3%

---


# Armadilhas de spam

Existem armadilhas de spam para ajudar a identificar emails de remetentes fraudulentos ou que não estão seguindo as práticas recomendadas de email. O endereço de email da interceptação de spam geralmente não é publicado publicamente e é quase impossível de identificar. A entrega de emails para interceptações de spam pode afetar sua reputação com vários graus de gravidade, dependendo do tipo de armadilha e do ISP. Saiba mais sobre os diferentes tipos de armadilhas de spam nas seções a seguir.

## Reciclado

As interceptações de spam reciclado são endereços que antes eram válidos, mas não estão mais sendo usados. Uma maneira importante de manter as listas o mais limpos possível é enviar emails regularmente para toda a lista e suprimir adequadamente os emails devolvidos. Isso ajuda os endereços de email abandonados a serem colocados em quarentena e retidos do uso posterior.

Em alguns casos, um endereço pode ser reciclado em 30 dias. O envio regular é um aspecto vital da boa higiene das listas, juntamente com a supressão regular de usuários inativos. **[As ](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/re-engagement-best-practices.html?lang=en#sending-messages)** campanhas de reengajamento normalmente fazem parte de sofisticados programas de marketing por email. Esse estilo de campanha permite que o remetente tente recuperar usuários que, de outra forma, não seriam mais enviados por email.

## Typo

Uma interceptação de spam de tipo é um endereço que contém um erro ortográfico ou malformação. Isso geralmente ocorre com erros ortográficos conhecidos dos principais domínios, como o Gmail (por exemplo: o gmial é um dactipo comum). Os ISPs e outros operadores de lista de bloqueios registrarão domínios inválidos conhecidos para serem usados como interceptação de spam para identificar remetentes de spam e medir a integridade do remetente. A melhor maneira de evitar armadilhas de spam é usar um **processo de aceitação duplo** para a coleção de listas.

## Pristina

Uma interceptação de spam incomparável é um endereço que não tem usuário final e nunca teve um usuário final. É um endereço que foi criado apenas para identificar o email de spam. Esse é o tipo de armadilha de spam mais impactante, pois é virtualmente impossível de identificar e exigiria um esforço substancial para limpar de sua lista. A maioria das listas de bloqueios usa armadilhas de spam impressas para listar remetentes não reputados. A única maneira de evitar que armadilhas de spam inéditas infectem sua lista de email de marketing mais ampla é utilizar um **processo de aceitação duplo** para a coleção de listas.

## Recursos específicos do produto

**Adobe Campaign Classic**

* [SpamAssassin](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/spamassassin.html?lang=en#using-spamassassin)

**Adobe Campaign Standard**

* [Pré-visualização de email e análise anti spam](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/designing-content/email-designer/preview-your-email.html#designing-content)
* [Processo duplo de aceitação](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=en#communication-channels)

