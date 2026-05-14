---
title: Rejeições
description: Saiba mais sobre os diferentes tipos de rejeições.
topics: Deliverability
jira: KT-7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 6338eb67-3efd-476e-8b26-97bbb6a1d35f
TQID: https://experienceleague.adobe.com/0Gly4dAgTpfrmnFD3N-RphZf9vmctJ57fMi1hSmfMTg
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 527
ht-degree: 100%

---

# Rejeições

As rejeições são o resultado de uma tentativa de entrega e falha em que o ISP fornece avisos de falha. O processamento do tratamento de rejeição é parte essencial da higiene das listas. Após um determinado email ser rejeitado várias vezes consecutivas, esse processo o sinaliza para supressão. O número e o tipo de rejeições necessárias para acionar a supressão variam de sistema para sistema. Esse processo impede que os sistemas continuem enviando endereços de email inválidos. As rejeições são um dos dados principais que os ISPs usam para determinar a reputação do IP. É muito importante acompanhar essa métrica. &quot;Entregue&quot; versus &quot;rejeitado&quot; é provavelmente a maneira mais comum de medir a entrega de mensagens de marketing: quanto maior a porcentagem entregue, melhor.

Vamos analisar dois tipos diferentes de rejeições.

## Rejeições permanentes

As rejeições permanentes são falhas permanentes geradas depois que um ISP classifica uma tentativa de envio por email para um endereço de assinante como não entregue. No Adobe Campaign, as rejeições permanentes categorizadas como não entregues são adicionadas à quarentena, o que significa que elas não retornarão novamente. Há alguns casos em que uma rejeição permanente é ignorada se a causa da falha for desconhecida.
Estes são alguns exemplos comuns de rejeições permanentes:

* Endereço não existe
* Conta desabilitada
* Sintaxe incorreta
* Domínio incorreto

## Rejeições temporárias

As rejeições temporárias são falhas temporárias que os ISPs geram quando têm dificuldade em entregar emails. As falhas leves serão repetidas várias vezes (com variação dependendo do uso de configurações de entrega personalizadas ou predefinidas) para tentar um delivery bem-sucedido. Os endereços que continuamente emitem rejeição não serão adicionados à quarentena até que o número máximo de tentativas tenha sido atingido (o que novamente varia de acordo com as configurações). Algumas causas comuns de rejeições temporárias incluem:

* Caixa de entrada cheia
* Servidor de email do destinatário inativo
* Problemas de reputação do remetente

![tipos de rejeição](../assets/bounce-types.png)

>[!NOTE]
>
>As rejeições são o principal indicador de um problema de reputação, pois podem realçar uma fonte de dados incorreta (rejeição permanente) ou um problema de reputação com um ISP (rejeição temporária).
>
>As rejeições temporárias geralmente ocorrem como parte do envio de email e devem ter permissão para a resolução durante o processamento de nova tentativa antes de serem caracterizadas como um problema real de entrega. Se sua taxa de rejeição temporária for maior que 30% para um único ISP e não for resolvida em 24 horas, é importante relatar sua preocupação ao consultor de capacidade de entrega do Adobe Campaign.

## Recursos específicos do produto

**Adobe Campaign Classic**

* [Tipos e motivos de falha de entrega](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=pt-BRvery-failure-types-and-reasons)
* [Gestão de emails rejeitados](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=pt-BR#bounce-mail-management)
* [Relatório de não entregáveis e rejeições](https://experienceleague.adobe.com/pt-br/docs/campaign-classic/using/reporting/reports-on-deliveries/global-reports#non-deliverables-and-bounces)

**Adobe Campaign Standard**

* [Tipos e motivos de falha de entrega](https://experienceleague.adobe.com/pt-br/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures#delivery-failure-types-and-reasons)
* [Qualificação de email de rejeição](https://experienceleague.adobe.com/pt-br/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures#bounce-mail-qualification)
* [Relatório de resumo de rejeições](https://experienceleague.adobe.com/pt-br/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary#reporting)
