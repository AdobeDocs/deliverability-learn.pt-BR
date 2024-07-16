---
title: Verizon Media Group (Yahoo, AOL, Verizon, etc.)
description: "[!DNL Verizon Media Group] geralmente é um dos três principais domínios para a maioria das listas B2C. Eles se comportam de maneira um pouco exclusiva, pois geralmente limitam ou enviam emails em massa se surgirem problemas de reputação."
topics: Deliverability
jira: KT-5320
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: 43e6d3cb-23c3-4076-8026-a1a08e76bd1b
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 3%

---

# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon etc.)

[!DNL Verizon Media Group] geralmente é um dos três principais domínios para a maioria das listas B2C. Eles se comportam de maneira um pouco exclusiva, pois geralmente limitam ou enviam emails em massa se surgirem problemas de reputação.

Estes são alguns destaques:

## Quais dados são importantes

O [!DNL Verizon Media Group] (VMG) criou e mantém seus próprios filtros de spam proprietários, usando uma mistura de conteúdo e filtragem de URL e reclamações de spam. Junto com o Gmail, eles são um dos primeiros ISPs a adotar o filtro de email por domínio e endereço IP.

## Quais dados eles disponibilizam?

O VMG tem um FBL usado para enviar informações de reclamação de volta aos remetentes. Eles também estão explorando a possibilidade de adicionar mais dados no futuro.

## Reputação do remetente

A reputação de um remetente é composta por uma combinação de endereço IP, domínio e endereço do remetente. A reputação é calculada usando os componentes tradicionais, incluindo reclamações, armadilhas de spam, endereços inativos ou malformados e engajamento. O VMG usa limitação de taxa (também conhecida como limitação) junto com a pasta em massa para se defender contra spam. Eles complementam seus sistemas internos de filtragem com algumas listas negras do [!DNL Spamhaus], incluindo as listas PBL, SBL e XBL para proteger seus usuários.

## Insights

O VMG tem períodos de manutenção regulares para endereços de email antigos e inativos ultimamente. Isso significa que é comum observar um aumento significativo nas rejeições de endereço inválido, o que pode afetar a taxa de entrega por um curto período de tempo. Eles também são sensíveis a altas taxas de rejeições de endereço inválido de um remetente, o que indica a necessidade de reforçar as políticas de aquisição ou engajamento. Os remetentes podem enfrentar impacto negativo em cerca de 1% dos endereços inválidos.
