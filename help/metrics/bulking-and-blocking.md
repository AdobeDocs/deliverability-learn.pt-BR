---
title: Como marcar e bloquear emails
description: Saiba por que os ISPs colocam mensagens de email em pastas de spam ou as bloqueiam.
topics: Deliverability
jira: KT-7051
thumbnail: kt7051.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4b280f90-73b9-4b88-adb8-57b6a46ddad7
TQID: https://experienceleague.adobe.com/mNz7Z6yQjlK7-NShGkgXNR8hp9kKUXDl9nHzMG4j3Q4
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 327
ht-degree: 100%

---

# Marcação e bloqueio

## Marcação

A marcação é a entrega de correio para a pasta de spam ou lixo eletrônico de um ISP. É identificável quando uma taxa de abertura inferior ao normal (e às vezes uma taxa de cliques) é igualada a uma alta taxa de entrega. As causas para os emails serem marcados variam por ISP. Em geral, se as mensagens estiverem sendo colocadas na pasta de spam, um sinalizador que influencia o envio de reputação (higiene de lista, por exemplo) exigirá uma reavaliação. É um sinal de que a reputação está diminuindo, sendo um problema a ser corrigido imediatamente antes que afete outras campanhas. Trabalhe com seu consultor de entrega da Adobe para solucionar quaisquer problemas de marcação dependendo da sua situação.

## Bloqueio

Um bloqueio ocorre quando os indicadores de spam atingem limites de ISP proprietários e o ISP começa a bloquear o email (perceptível por meio de tentativas de mala direta) de um remetente. Há vários tipos de bloqueios. Geralmente, os bloqueios ocorrem especificamente para um endereço IP, mas também podem ocorrer no nível de domínio ou entidade de envio. Solucionar um bloqueio requer experiência específica, portanto, entre em contato com o consultor de entrega da Adobe para obter assistência.

## Lista de bloqueios

Uma lista de bloqueios ocorre quando um gerenciador de lista de bloqueios de terceiros registra um comportamento semelhante a um remetente. Às vezes a causa de uma lista de bloqueios é publicada pela parte da lista de bloqueios. Uma lista geralmente é baseada em endereço IP, mas em casos mais severos pode ser por intervalo IP ou até mesmo por um domínio de envio. A solução de uma lista de bloqueios deve envolver o suporte do seu consultor de capacidade de entrega da Adobe para resolver e evitar mais listas. Algumas listas são extremamente graves e podem causar problemas de reputação prolongados, que são difíceis de resolver. O resultado de uma lista de bloqueios varia de acordo com a lista, mas tem o potencial de afetar a entrega de todos os emails.

## Recursos adicionais

* Saiba mais sobre [Listas de buraco negro em tempo real](/help/additional-resources/blocklist-databases.md) que mantêm bancos de dados de endereços IP e domínios que provavelmente serão usados por remetentes de spam.
