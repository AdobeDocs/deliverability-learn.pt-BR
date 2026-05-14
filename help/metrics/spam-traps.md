---
title: Coberturas de spam
description: Saiba mais sobre os diferentes tipos de coberturas de spam.
topics: Deliverability
jira: KT-7050
thumbnail: kt7050.jpg
doc-type: article
activity: understand
team: ACS
exl-id: ffacc1b1-bf3f-466e-9a1d-63aad4d2ec45
TQID: https://experienceleague.adobe.com/qandgsfuAA4E9uHfZ0jrgpkjs-kt9Izs8k-HvtgDF7A
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: b0bb9048-d951-48d8-8232-45cf248a7e27
  - id: e64968b2-4ee5-47f9-8cae-0588f184b9eb
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: beb7a3c1-66ab-4786-b879-7621375b3c40
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 495
ht-degree: 100%

---

# Coberturas de spam

Existem coberturas de spam para ajudar a identificar emails de remetentes fraudulentos ou que não estejam seguindo as práticas recomendadas de email. O endereço de email da interceptação de spam geralmente não é divulgado publicamente e é quase impossível de ser identificado. A entrega de emails para interceptações de spam pode afetar sua reputação com vários graus de gravidade, dependendo do tipo de cobertura e do ISP. Saiba mais sobre os diferentes tipos de coberturas de spam nas seções a seguir.

## Reciclada

As interceptações de spam recicladas são endereços que antes eram válidos, mas que não estão mais sendo usados. Uma maneira importante de manter as listas sempre limpas é enviar emails regularmente para toda a lista e suprimir adequadamente os emails devolvidos. Isso ajuda os endereços de email abandonados a serem colocados em quarentena e retidos na próxima utilização.

Em alguns casos, um endereço pode ser reciclado em 30 dias. O envio regular é um aspecto vital da boa higiene das listas, juntamente com a supressão regular de usuários inativos. **As campanhas de reengajamento** normalmente fazem parte de sofisticados programas de marketing por email. Esse estilo de campanha permite que o remetente tente recuperar usuários que, de outra forma, não receberiam mais emails.

## Erro de digitação

Uma interceptação de spam com erro de digitação é um endereço que contém um erro ortográfico ou má formação. Isso geralmente ocorre com erros ortográficos dos principais domínios conhecidos, como o Gmail (por exemplo: gmial é um erro de digitação comum). Os ISPs e outros operadores de lista de bloqueios registrarão domínios inválidos conhecidos para serem usados como interceptação de spam para identificar remetentes de spam e medir a integridade do remetente. A melhor maneira de evitar coberturas de spam é usar um **processo de aceitação duplo** para a coleção de listas.

## Pura

Uma cobertura de spam pura é um endereço que não tem e nunca teve usuário final. É um endereço que foi criado apenas para identificar o email de spam. Esse é o tipo de armadilha de spam mais impactante, pois é praticamente impossível de ser identificada e exige um esforço considerável para ser retirado da lista. A maioria das listas de bloqueios usa a cobertura de spam pura para listar remetentes com má reputação. A única maneira de evitar que coberturas de spam puras infectem sua lista de email de marketing mais ampla é utilizar um **processo de aceitação duplo** para a coleção de listas.

## Recursos adicionais

* Saiba mais sobre como identificar e evitar armadilhas de spam [nesta seção](/help/additional-resources/all-about-spam-traps.md).
* Saiba mais sobre como melhorar a capacidade de entrega por meio de estratégias de reengajamento [nesta seção](/help/additional-resources/re-engagement.md).

## Recursos específicos do produto

**Adobe Campaign Classic**

* [SpamAssassin](https://experienceleague.adobe.com/pt-br/docs/campaign-classic/using/sending-messages/deliverability-management/spamassassin#using-spamassassin)
* [Criar um formulário de assinatura com aceitação dupla](https://experienceleague.adobe.com/pt-br/docs/campaign-classic/using/designing-content/web-forms/use-cases-web-forms#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Pré-visualização de email e análise anti-spam](https://experienceleague.adobe.com/pt-br/docs/campaign-standard-learn/tutorials/designing-content/email-designer/preview-your-email#designing-content)
* [Processo de aceitação dupla](https://experienceleague.adobe.com/pt-br/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process#communication-channels)
