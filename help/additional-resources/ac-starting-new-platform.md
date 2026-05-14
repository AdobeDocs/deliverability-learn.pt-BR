---
title: Início de uma nova plataforma
description: Saiba mais sobre como gerenciar a capacidade de delivery ao iniciar uma nova plataforma com o Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
TQID: https://experienceleague.adobe.com/cQa5nOTSJwxDGX-QkXGez5dpm5N-8I7QZ-LsEW0FRLo
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
  - id: d1d0a9cd-295d-4976-8c39-ddae266f240e
  - id: e2290edd-b061-4880-9d79-dee306cf5aa9
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
  - id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 666
ht-degree: 53%

---

# Início de uma nova plataforma {#starting-new-platform}

A manutenção da reputação do seu domínio e endereço IP é essencial ao configurar uma nova plataforma para usar com o Adobe Campaign.

## Uma etapa delicada

Você deve ter muito cuidado ao começar a enviar emails em uma nova plataforma, pois a plataforma não tem histórico de uso e reputação quando os IPs de envio nunca foram usados para essa finalidade.

Os ISPs desconfiam naturalmente dos endereços IP que nunca foram usados para enviar emails e que, de repente, começam a enviar grandes volumes de tráfego de emails. Na verdade, os remetentes de spam geralmente usam endereços IP &quot;desconhecidos&quot; (ou seja, endereços que nunca foram incluídos na lista de bloqueios) para enviar o maior número possível de mensagens antes que sejam detectados.

Não se pode esperar atingir a velocidade operacional em termos de saída no início da fase de produção. Além disso, você não deve tentar enviar mensagens a essa taxa, pois isso pode levar os ISPs a bloquear os endereços de envio e comprometer seriamente o restante da fase de inicialização.

## Princípios fundamentais

Abaixo estão listados os principais princípios a serem seguidos ao iniciar uma nova plataforma.

* Configure um subdomínio dedicado específico para campanhas de email enviadas do Adobe.

* Se você tiver essas informações, **importe endereços inválidos para a tabela quarentena**.
A inicialização de uma plataforma geralmente ocorre ao usar uma lista de endereços pela primeira vez e que podem não ser totalmente qualificados. Se você enviar para endereços inválidos ou para endereços armadilha, isso contribuirá para diminuir a reputação da plataforma.

   * Se você tiver uma lista de endereços inválidos, é do seu interesse importá-la para a tabela de quarentena antes dos primeiros envios. A tabela de quarentena está disponível por meio dos menus **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** (Campaign Classic) e **[!UICONTROL Administration > Channels > Quarantines > Addresses]** (Campaign Standard).

   * Se, mesmo assim, você quiser requalificar os endereços inválidos, é preferível fazer isso assim que a reputação da plataforma for estabelecida e pouco a pouco para &quot;diluir&quot; o uso de endereços inválidos ao longo do tempo.

* **Limite a taxa de transferência** limitando o número de mtachilds. Para obter mais informações sobre como ajustar essa configuração técnica, entre em contato com o administrador do Adobe Campaign.

* **Aumente progressivamente os volumes enviados** para evitar que sejam marcados como spam. Não direcione todo o banco de dados desde o início, mas adicione uma fração extra da lista sempre que enviar. Isso deve permitir aumentar o volume em cada etapa e reduzir a taxa geral de endereços inválidos. Para garantir o desenvolvimento suave da fase de inicialização, você pode usar ondas.

* **Enviar regularmente**. Em certa medida, é melhor enviar pouca coisa regularmente do que campanhas enormes esporadicamente.
* **Preste muita atenção aos relatórios da entrega**. Indicadores de erro altos podem significar que uma configuração técnica está mal configurada.

## Recursos adicionais

Para obter mais informações sobre os princípios listados acima e sua implementação com o Adobe Campaign, consulte as seguintes seções:

* [Aumente sua reputação de email com o aquecimento de IP](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [Tudo sobre armadilhas de spam](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Otimizar seu delivery por meio da quarentena](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identificar endereços em quarentena para toda a plataforma](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [Enviar usando várias ondas](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [Monitoramento de entrega](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=pt-BR#sending-messages)

**Adobe Campaign Standard**

* [Otimizar seu delivery por meio da quarentena](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identificar endereços em quarentena para toda a plataforma](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=pt-BR)
* [Monitoramento de uma entrega](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=pt-BR)
