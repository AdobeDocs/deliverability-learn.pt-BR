---
title: Atualizar qualificação de rejeição após interrupção online da Itália
description: Saiba como atualizar a qualificação de rejeição após a interrupção online da Itália
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
hidefromtoc: true
role: Admin
level: Beginner
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 22%

---

# Atualizar as rejeições permanentes incorretas após a interrupção do Italia Online {#update-bounce-italia}

## Contexto{#outage-context}

A partir de 22 de janeiro (horário local), o Italia Online passou por uma interrupção que resultou em vários atrasos e emails rejeitados. O serviço começou a ser retomado com capacidade limitada em 26 de janeiro.

Os domínios afetados são: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it**, e **blu.it**.

Esse problema ocorreu de 22/01/2023 a 26/01/2023, mas a maioria das quarentenas incorretas ocorreu em 26 de janeiro.

Saiba mais na comunicação oficial [aqui](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impacto{#outage-impact}

Como na maioria dos casos, quando há uma interrupção de um provedor de serviços de Internet (ISP), alguns emails enviados pelo Campaign ou Journey Optimizer foram marcados incorretamente como rejeições. Isso não estava afetando apenas o Adobe, mas todos tentando obter e-mails entregues à Italia Online durante o período da interrupção.

Os sintomas foram:

* **Rejeições temporárias** com a mensagem `452 requested action aborted: try again later` - eles foram repetidos automaticamente e nenhuma ação é necessária.

* **Devoluções permanentes** com a mensagem `550 <email address> recipient rejected` foram retornados pelo ISP em 26 de janeiro, entre 8h e 14h, horário local, para evitar que os remetentes continuem sobrecarregando seus servidores. Como confirmado pelo Italia Online Postmaster, essas não são rejeições permanentes reais, portanto, recomendamos cancelar a quarentena de todos os endereços de email que foram excluídos em 26 de janeiro de 2023 devido a essa mensagem.

## Processo para atualização{#outage-update}

### Adobe Campaign{#ac-update}

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Campaign adicionou automaticamente esses recipients à lista de quarentena com uma configuração **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corrigir isso, você precisa atualizar a tabela de quarentena no Campaign localizando e removendo esses recipients ou alterando seus **[!UICONTROL Status]** para **[!UICONTROL Valid]** para que o fluxo de trabalho de limpeza noturna os remova.

Para encontrar os recipients que foram afetados por esse problema, ou caso isso aconteça novamente com qualquer outro ISP, consulte as instruções abaixo:

* Para o Campaign Classic v7 e o Campaign v8, consulte [esta página](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Para o Campaign Standard, consulte [esta página](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Journey Optimizer adicionou automaticamente esses endereços de email à lista de supressão com um **[!UICONTROL Reason]** configuração de **[!UICONTROL Invalid Recipient]**. Para corrigir isso, você precisa atualizar a lista de supressão localizando e removendo esses endereços de email.

Depois de identificados, esses endereços podem ser removidos manualmente da lista de supressão usando o **[!UICONTROL Delete]** botão. Esses endereços podem ser incluídos em campanhas de email futuras.

Saiba mais em [nesta seção](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

