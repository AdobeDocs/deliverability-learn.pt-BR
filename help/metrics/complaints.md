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
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: ht
source-wordcount: '290'
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

* [Indicadores de rastreamento](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html?lang=pt-BR#tracking-indicators)

**Adobe Campaign Standard**

* [Relatório de reclamações](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html?lang=pt-BR#reporting)
