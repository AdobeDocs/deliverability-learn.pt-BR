---
title: Início de uma nova plataforma
description: Saiba mais sobre como gerenciar a capacidade de delivery ao iniciar uma nova plataforma com o Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 65%

---

# Início de uma nova plataforma {#starting-new-platform}

A manutenção da reputação do seu domínio e endereço IP é essencial ao configurar uma nova plataforma para usar com o Adobe Campaign.

## Uma etapa delicada

Tenha muito cuidado ao começar a enviar emails em uma nova plataforma, pois a plataforma não tem histórico de uso e reputação quando os IPs de envio nunca foram usados para essa finalidade.

Os ISPs desconfiam naturalmente dos endereços IP que nunca foram usados para enviar emails e que, de repente, começam a enviar grandes volumes de tráfego de emails. Na verdade, os remetentes de spam geralmente usam endereços IP &quot;desconhecidos&quot; (ou seja, endereços que nunca foram incluídos na lista de bloqueios) para enviar o maior número possível de mensagens antes que sejam detectados.

Não se pode esperar atingir a velocidade operacional em termos de saída no início da fase de produção. Além disso, você não deve tentar enviar mensagens a essa taxa, pois isso pode levar os ISPs a bloquear os endereços de envio e comprometer seriamente o restante da fase de inicialização.

## Princípios fundamentais

Abaixo estão listados os principais fundamentos que devem ser seguidos ao iniciar uma nova plataforma.

* Configure um subdomínio dedicado específico para campanhas de email enviadas do Adobe.

* Se você tiver essas informações, **importe endereços inválidos para a tabela quarentena**.
A inicialização de uma plataforma geralmente ocorre ao usar uma lista de endereços pela primeira vez e que podem não ser totalmente qualificados. Se você enviar para endereços inválidos ou para endereços armadilha, isso contribuirá para diminuir a reputação da plataforma.

   * Se você tiver uma lista de endereços inválidos, é do seu interesse importá-la para a tabela de quarentena antes dos primeiros envios. A tabela de quarentena está disponível por meio do **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** (Campaign Classic) e **[!UICONTROL Administration > Channels > Quarantines > Addresses]** Menus (Campaign Standard).

   * Se, mesmo assim, você quiser requalificar os endereços inválidos, é preferível fazer isso assim que a reputação da plataforma for estabelecida e pouco a pouco para &quot;diluir&quot; o uso de endereços inválidos ao longo do tempo.

* **Limite a taxa de transferência** limitando o número de mtachilds. Para obter mais informações sobre como ajustar essa configuração técnica, entre em contato com o administrador do Adobe Campaign.

* **Aumente progressivamente os volumes enviados** para evitar que sejam marcados como spam. Não direcione todo o banco de dados desde o início, mas adicione uma fração extra da lista sempre que enviar. Isso deve permitir aumentar o volume em cada etapa e reduzir a taxa geral de endereços inválidos. Para garantir o desenvolvimento perfeito da fase de início, você pode usar ondas.

* **Enviar regularmente**. Em certa medida, é melhor enviar pouca coisa regularmente do que campanhas grandes esporadicamente.
* **Preste muita atenção aos relatórios do delivery**. Muito erros podem significar que uma configuração técnica está mal feita.

## Recursos adicionais

Para obter mais informações sobre os princípios listados acima e sua implementação com o Adobe Campaign, consulte as seguintes seções:

* [Aumente sua reputação de email com o aquecimento de IP](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [Tudo sobre armadilhas de spam](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Otimize seu delivery por meio da quarentena](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identificar endereços em quarentena para toda a plataforma](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [Enviar usando várias ondas](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [Monitoramento de delivery](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html#sending-messages)

**Adobe Campaign Standard**

* [Otimize seu delivery por meio da quarentena](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identificar endereços em quarentena para toda a plataforma](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)
* [Monitoramento de um delivery](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html)
