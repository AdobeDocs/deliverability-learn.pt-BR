---
title: Reclamações
description: 'Saiba mais sobre reclamações que são registradas quando um usuário indica que um email é indesejado ou inesperado. '
feature: Métricas
topics: Deliverability
kt: 7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 550821608eb7049f739a156536dd31b6b2faa2fa
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---


# Reclamações

As reclamações são registradas quando um usuário indica que um email é indesejado ou inesperado. Normalmente, essa ação do assinante é registrada por meio do cliente de email do assinante quando ele aperta o botão de spam ou por meio de um sistema de relatórios de spam de terceiros.

## reclamação do ISP

A maioria dos ISPs de nível 1 e 2 fornecem um método de relatório de spam para seus usuários, pois os processos de recusa e cancelamento de subscrição foram usados de forma maliciosa no passado para validar um endereço de email. A Adobe Campaign recebe essas reclamações por meio de FBLs ISP. Isso é estabelecido durante o processo de configuração para qualquer ISPs que forneça FBLs e permite que o Adobe Campaign adicione automaticamente endereços de email que reclamaram para a tabela de quarentena para supressão. Os picos nas reclamações de ISP podem ser um indicador de qualidade de lista ruim, métodos de coleta de lista menos do que o ideal ou políticas de engajamento fracas. Elas também são notadas frequentemente quando o conteúdo não é relevante.

## Reclamações de terceiros

Há vários grupos antisspam que permitem relatórios de spam em um nível mais amplo. As métricas de reclamação usadas por esses terceiros são usadas para marcar o conteúdo do email para identificar email de spam. Esse processo também é conhecido como impressão digital. Os usuários desses métodos de reclamação de terceiros geralmente são mais seguros com relação ao email, portanto, podem ter um impacto maior do que outras reclamações podem ter se não responderem.

>[!NOTE]
>
>Os ISPs coletam reclamações e as usam para determinar a reputação geral de um remetente. Todas as reclamações devem ser suprimidas e não devem mais ser contatadas o mais rapidamente possível e de acordo com as leis e regulamentos locais.

## Recursos específicos do produto

**Adobe Campaign Classic**

* [Indicadores de rastreamento](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html#tracking-indicators)

**Adobe Campaign Standard**

* [Relatório de reclamações](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html#reporting)