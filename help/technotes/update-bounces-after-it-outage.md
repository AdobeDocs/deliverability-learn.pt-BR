---
title: Atualizar qualificação de devolução após interrupção do Italia Online
description: Saiba como atualizar a qualificação de devolução após a interrupção do Italia Online
feature: Deliverability
source-git-commit: 4494363c060b7e2e1efde46f7ab8260fa900ffd7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 24%

---

# Atualize as devoluções incorretas após a interrupção do Italia Online {#update-bounce-italia}

## Contexto{#outage-context}

A partir de 22 de janeiro (horário local), o Italia Online passou por uma interrupção que resultou em vários atrasos e rejeitou emails. O serviço começou a retomar com capacidade limitada em 26 de janeiro.

Os domínios afetados são: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** e **blu.it**.

Esse problema ocorreu de 22/01/2023 a 26/01/2023, mas a maioria das quarentenas equivocadas aconteceu em 26 de janeiro.

Saiba mais na comunicação oficial [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impacto{#outage-impact}

Como na maioria dos casos em que há uma interrupção de um ISP, alguns emails enviados pelo Campaign foram marcados incorretamente como rejeições. Isso não afetou apenas o Adobe, mas todos tentando receber emails para o Italia Online durante a interrupção.

Os sintomas foram:

* **Devoluções diferenciais** com a mensagem `452 requested action aborted: try again later` - foram automaticamente repetidas e nenhuma ação é necessária.

* **Devoluções permanentes** com a mensagem `550 <email address> recipient rejected` foram retornados pelo ISP em 26 de janeiro, entre 8h e 14h horário local, para evitar que os remetentes continuem sobrecarregando seus servidores. Como confirmado pelo Italia Online Postmaster, essas não são devoluções reais, então recomendamos cancelar a quarentena de todos os endereços de email que foram excluídos em 26 de janeiro de 2023 devido a essa mensagem.

## Processo para atualização{#outage-update}

De acordo com a lógica padrão de manipulação de rejeição, o Adobe Campaign adicionou automaticamente esses recipients à lista de quarentena com uma configuração **[!UICONTROL Status]** de **[!UICONTROL Quarantine]**. Para corrigir isso, você precisa atualizar a tabela de quarentena no Campaign localizando e removendo esses recipients ou alterando seus **[!UICONTROL Status]** para **[!UICONTROL Valid]** para que o fluxo de trabalho de limpeza noturna os remova.

Para encontrar os recipients que foram afetados por esse problema, ou caso isso aconteça novamente com qualquer outro ISP, consulte as instruções abaixo:

* Para o Campaign Classic v7 e o Campaign v8, consulte [esta página](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Para o Campaign Standard, consulte [esta página](https://experienceleague.corp.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.



