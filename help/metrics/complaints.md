---
title: Reclamações
description: Saiba mais sobre as reclamações que são registradas quando um usuário indica que um email é indesejado ou inesperado.
topics: Deliverability
jira: KT-7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 0343820d-f5af-4b8a-bcab-dbb47ae7aecb
TQID: https://experienceleague.adobe.com/W9G0ZPGeIm5KmVHu5-VuMd-Kb-4x4f7qhBPnpskxqqA
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 100%

---

# Reclamações

As reclamações são registradas quando um usuário indica que um email é indesejado ou inesperado. Normalmente, essa ação do assinante é registrada por meio do cliente de email do assinante quando ele clica no botão de spam ou por meio de um sistema de relatórios de spam de terceiros.

## Reclamação do ISP

A maioria dos ISPs de nível 1 e alguns de nível 2 fornecem um método de relatório de spam para seus usuários, pois os processos de recusa e cancelamento de assinatura foram usados de forma mal intencionada no passado para validar um endereço de email. O Adobe Campaign recebe essas reclamações por meio de FBLs ISP. Isso é estabelecido durante o processo de configuração para qualquer ISP que forneça FBLs e permita que o Adobe Campaign adicione automaticamente endereços de email que apresentaram uma reclamação de cancelamento à tabela de quarentena. Os picos nas reclamações de ISP podem ser um indicador de qualidade de lista ruim, métodos de coleta de lista abaixo do ideal ou políticas de engajamento inadequadas. Elas também são notadas frequentemente quando o conteúdo não é relevante.

## Reclamações de terceiros

Há vários grupos anti-spam que permitem relatórios de spam em um nível mais amplo. As métricas de reclamação usadas por esses terceiros servem para marcar o conteúdo do email para identificar email de spam. Esse processo também é conhecido como impressão digital. Os usuários desses métodos de reclamação de terceiros geralmente são mais seguros com relação ao email, portanto, podem ter um impacto maior do que outras reclamações sem resposta.

>[!NOTE]
>
>Os ISPs coletam reclamações e as usam para determinar a reputação geral de um remetente. De acordo com as leis e regulamentos locais, todas as reclamações devem ser suprimidas, não devendo mais ser contatadas a partir desse momento.

## Recursos específicos do produto

**Adobe Campaign Classic**

* [Indicadores de rastreamento](https://experienceleague.adobe.com/pt-br/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports#tracking-indicators)

**Adobe Campaign Standard**

* [Relatório de reclamações](https://experienceleague.adobe.com/pt-br/docs/campaign-standard/using/reporting/list-of-reports/complaints#reporting)
