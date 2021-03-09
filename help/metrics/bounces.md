---
title: Rejeições
description: Saiba mais sobre os diferentes tipos de devoluções
feature: Métricas
topics: Deliverability
kt: 7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 3%

---


# Rejeições

Rejeições são o resultado de uma tentativa de entrega e falha em que o ISP fornece avisos de falha. O processamento do tratamento de rejeição é uma parte essencial da higiene das listas. Depois que um determinado email tiver retornado várias vezes consecutivas, esse processo o sinaliza para supressão. O número e o tipo de devoluções necessárias para acionar a supressão variam de sistema para sistema. Esse processo impede que os sistemas continuem enviando endereços de email inválidos. As rejeições são um dos dados principais que os ISPs usam para determinar a reputação do IP. Acompanhar essa métrica é muito importante. &quot;Entregue&quot; versus &quot;devolvido&quot; é provavelmente a maneira mais comum de medir a entrega de mensagens de marketing: quanto maior a porcentagem entregue, melhor.

Vamos mergulhar em dois tipos diferentes de devoluções.

## Devoluções permanentes

As rejeições permanentes são falhas permanentes geradas depois que um ISP determina uma tentativa de envio por e-mail para um endereço de assinante como não entregável. No Adobe Campaign, as devoluções permanentes categorizadas como não entregues são adicionadas à quarentena, o que significa que elas não seriam tentadas novamente. Há alguns casos em que uma devolução permanente seria ignorada se a causa da falha fosse desconhecida.
Estes são alguns exemplos comuns de devoluções permanentes:

* Endereço não existe
* Conta desabilitada
* Sintaxe incorreta
* Domínio incorreto

## Devoluções temporárias

As devoluções temporárias são falhas temporárias que os ISPs geram quando têm dificuldade em entregar emails. As falhas leves serão repetidas vezes (com variação dependendo do uso de configurações de entrega personalizadas ou predefinidas) para tentar um delivery bem-sucedido. Os endereços que continuamente emitem rejeição não serão adicionados à quarentena até que o número máximo de tentativas tenha sido atingido (o que novamente varia dependendo das configurações). Algumas causas comuns de devoluções temporárias incluem o seguinte:

* Caixa de entrada cheia
* Recebendo servidor de email inativo
* Problemas de reputação do remetente

![tipos de devolução](../assets/bounce-types.png)

>[!NOTE]
>
>As rejeições são um indicador principal de um problema de reputação porque podem realçar uma fonte de dados incorreta (rejeição permanente) ou um problema de reputação com um ISP (rejeição temporária).
>
>As devoluções temporárias geralmente ocorrem como parte do envio de email e devem ter permissão para resolver durante o processamento de nova tentativa antes de caracterizar como um problema real de deliverability. Se sua taxa de rejeição temporária for maior que 30% para um único ISP e não for resolvida em 24 horas, é uma boa ideia levantar uma preocupação com seu consultor de capacidade de entrega do Adobe Campaign.

## Recursos específicos do produto

**Adobe Campaign Standard**

* [Lista de relatórios - Resumo da rejeição (documentação do produto)](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=en#reporting)
* [Noções básicas sobre falhas de delivery (documentação do produto)](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=en#about-delivery-failures)

**Adobe Campaign Classic**

* [Noções básicas sobre falhas de delivery (documentação do produto)](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=en#sending-messages)