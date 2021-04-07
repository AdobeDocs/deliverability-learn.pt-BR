---
title: Coberturas de spam
description: Saiba mais sobre os diferentes tipos de coberturas de spam.
feature: Métricas
topics: Deliverability
kt: 7050
thumbnail: kt7050.jpg
doc-type: article
activity: understand
team: ACS
translation-type: ht
source-git-commit: 550821608eb7049f739a156536dd31b6b2faa2fa
workflow-type: ht
source-wordcount: '454'
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

* [SpamAssassin](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/spamassassin.html?lang=pt-BR#using-spamassassin)
* [Criar um formulário de assinatura com aceitação dupla](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=pt-BR#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Pré-visualização de email e análise anti-spam](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/designing-content/email-designer/preview-your-email.html?lang=pt-BR#designing-content)
* [Processo de aceitação dupla](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=br#communication-channels)

