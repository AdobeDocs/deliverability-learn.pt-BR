---
title: Volume - dicas sobre como fazer a transição sem problemas
description: O volume de emails que você está enviando é essencial para estabelecer uma reputação positiva. Saiba o que você pode fazer para fazer a transição sem problemas.
topics: Deliverability
jira: KT-7055
thumbnail: kt7055.jpg
doc-type: article
activity: understand
role: Admin,User
level: Beginner
team: ACS
exl-id: 1bc56061-0c64-4033-b49c-66618916bca6
TQID: https://experienceleague.adobe.com/piIfp9yQkAa1F1bkO9zM7PcOConZhTrwARo4Y8wtMsQ
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: e64968b2-4ee5-47f9-8cae-0588f184b9ebid: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 600
ht-degree: 1%

---

# Volume

O volume de emails que você está enviando é essencial para estabelecer uma reputação positiva. Coloque-se no lugar dos provedores de internet — se você começar a ver uma tonelada de tráfego de alguém que você não conhece, seria alarmante. O envio imediato de um grande volume de e-mails é arriscado e causa problemas de reputação que geralmente são difíceis de resolver. Pode ser frustrante, demorado e caro se livrar da má reputação e resolver problemas de marcação e bloqueio resultantes de enviar muito cedo.

Os limites de volume variam de acordo com o ISP e também podem variar dependendo das métricas de envolvimento médio. Alguns remetentes requerem uma rampa de volume muito baixa e lenta, enquanto outros podem permitir uma rampa mais acentuada no volume. Recomendamos trabalhar com um especialista, como um consultor de capacidade de entrega da Adobe, para desenvolver um plano de volume personalizado.

Esta é uma lista de dicas e sugestões para fazer a transição descomplicada:

* **Permissão** é a base de qualquer programa de email bem-sucedido.
* **Baixo e lento** — comece com volumes de envio baixos e, em seguida, aumente à medida que você estabelece a reputação do remetente.
* Uma **estratégia de mala direta em tandem** permite que você aumente o volume no Campaign ao encerrar com seu ESP atual, sem interromper seu calendário de email.
* **A participação é importante** — comece com os assinantes que abrem e clicam em seus emails regularmente.
* **Siga o plano** — nossas recomendações ajudaram centenas de clientes do Campaign a incrementar seus programas de email com êxito.
* **Monitore sua conta de email de resposta**. É uma experiência ruim para o seu cliente usar o noreply@xyz.com ou não responder.
* Endereços inativos podem ter um impacto negativo na capacidade de delivery. **Reativar e transmitir na plataforma atual**, não nos novos IPs.
* **Domínios** — use um domínio de envio que seja um subdomínio do domínio real da sua empresa
   * Por exemplo, se o domínio da sua empresa for xyz.com, email.xyz.com fornece mais credibilidade aos ISPs do que xyzemail.com
* **Transparência** — os detalhes de registro do seu domínio de email devem estar disponíveis publicamente e não ser privados.

Em muitas circunstâncias, o correio transacional não segue a abordagem tradicional de aquecimento promocional. Obviamente, é difícil controlar o volume em emails transacionais devido à sua natureza, pois geralmente requer uma interação do usuário para acionar o toque do email. Em alguns casos, o e-mail transacional pode simplesmente ser transferido sem um plano formal. Em outros casos, pode ser melhor fazer a transição de cada tipo de mensagem ao longo do tempo para aumentar lentamente o volume. Por exemplo, talvez você queira fazer a transição da seguinte maneira:

1. Confirmações de compras — alto engajamento em geral
2. Abandono do carrinho — engajamento médio - alto em geral
3. Emails de boas-vindas — alto engajamento, mas pode conter endereços inválidos, dependendo dos métodos de coleção de listas
4. Emails de retorno — engajamento menor em geral

## Recursos específicos do produto

**Campaign**

* Saiba mais sobre como gerenciar a capacidade de entrega ao iniciar uma nova plataforma com o Adobe Campaign em [esta seção](/help/additional-resources/ac-starting-new-platform.md).
* Saiba como enviar usando várias ondas com o Adobe Campaign Classic em [esta seção](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves).
* Saiba como delegar completamente um subdomínio ao Adobe Campaign Classic ou Standard nesta [seção](/help/additional-resources/ac-domain-name-setup.md).
* [Painel de Controle: Delegação total de subdomínio (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Saiba como delegar completamente um subdomínio ao Adobe Campaign Classic.*
* [Painel de Controle: Delegação total de subdomínio (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Saiba como delegar completamente um subdomínio ao Adobe Campaign Standard.*

## Recursos adicionais

* Saiba mais sobre como aumentar sua reputação de email com o aquecimento de IP [nesta seção](/help/additional-resources/increase-reputation-with-ip-warming.md).
