---
title: Tudo sobre armadilhas de spam
description: Saiba como entender, identificar e evitar armadilhas de spam ao gerenciar a capacidade de delivery.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 45cdcda0-70e4-47f4-8713-a834500e7881
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Tudo sobre armadilhas de spam

Um [interceptação de spam](/help/metrics/spam-traps.md) é um endereço válido, sem mensagem de erro quando os emails são enviados para o. Uma armadilha de spam tem uma missão principal: identificar remetentes de spam ou remetentes sem processo de higiene de dados.

## Quem gerencia esses endereços de interceptação de spam?

O primeiro tipo de endereço de interceptação de spam é a empresa de  de IP e Domínio lista de bloqueios como SpamHaus, Sorbs, SpamCop. Essas empresas têm uma enorme rede de endereços que são enviados em várias páginas da Internet como website, blog, fóruns para que seus endereços sejam coletados por remetentes de spam.

O segundo tipo de interceptação de spam é baseado em endereços ISP ativos antigos. Esses ISPs têm sua própria rede de interceptação de spam criada em endereços inativos reconvertidos na interceptação e cada ocorrência afeta o IP do remetente e a reputação do domínio.

## Como funciona?

**Um endereço de email sem usuário** final: Esses endereços não têm e nunca terão um usuário final que possa se registrar em informativos ou em qualquer outro tipo de comunicação.

**Um endereço de email abandonado por um usuário**: Após um período de inatividade, os endereços são desativados pelos ISPs. As mensagens de rejeição são enviadas aos remetentes para informá-los sobre esse novo status. Os remetentes devem colocar esses endereços em quarentena ou removê-los de comunicações futuras. Os ISPs usam esses endereços transformados em &quot;interceptação de spam&quot; para monitorar remetentes com práticas inadequadas.

## Como reconhecer ou identificar uma armadilha de spam?

É um trabalho difícil identificar armadilhas de spam, esses endereços devem permanecer anônimos, pois são usados para identificar remetentes ruins. A maioria dos ISPs não tem o sistema de clique e abertura para monitorar ocorrências de remetentes ruins. De acordo com definições anteriores, é possível determinar um pod de endereços suspeitos e testar a eficiência da seleção do pod.

## Por que seu banco de dados está infectado por armadilhas de spam?

Seu banco de dados de endereços de email contém interceptação de spam, como é possível? As duas principais razões são a falta de higiene no banco de dados ou a disfunção de coleta.

Esses poucos pontos ajudam você a verificar seus processos:

* Disfunção colateral:
   * De onde vêm seus endereços de email? Quantas fontes são usadas para coletar esses endereços? Você consegue identificá-los? Interno/registro correto?
   * Seu sistema de opt-in está funcionando corretamente?
   * Você verificou domínios e alias de seus endereços? Faça com a tabela abaixo!
* Processo de higiene do banco de dados:
   * Qual é o seu processo em relação ao endereço inativo nos últimos 12 meses?
   * Você está processando uma quarentena em devoluções temporárias como &quot;usuário inativo&quot;?
   * Quando é a última vez que você cuida de seu banco de dados e tenta limpá-lo? Faça isso regularmente.

## Aliases e domínios para evitar

**Aliases**

![](../../help/assets/aliases.png)

**Domínios**

![](../../help/assets/domains.png)
