---
title: Solução de problemas da capacidade de entrega
description: Saiba como identificar e solucionar problemas da capacidade de entrega.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4cc85124-e7e4-4cd5-99a9-23d2d8cf08fe
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 91%

---

# Solução de problemas da capacidade de entrega {#troubleshooting}

Abaixo estão algumas práticas recomendadas que podem ajudar a identificar e solucionar os problemas da capacidade de entrega.

## Identifique um problema da capacidade de entrega {#identify-deliverability-issue}

Para identificar um possível problema, os elementos listados em [essa página](/help/ongoing-monitoring.md) pode chamar a sua atenção.

<!--
Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
Subscriber activity: opens, clicks and/or transactions are lower than usual.
Seed accounts show filtered or non-delivered mailings.
-->

## Hipóteses de possíveis causas {#potential-causes}

Faça as seguintes perguntas para identificar as possíveis causas para o problema da capacidade de entrega:

* Houve uma mudança recente na segmentação das listas?
* Foram adquiridas novas fontes de dados?
* Algum arquivo foi enviado acidentalmente para quarentena?
* O problema pode ser devido ao conteúdo da mensagem?
* Os emails são enviados com frequência suficiente para manter os IPs aquecidos?
* As mensagens estão sendo segmentadas por atividade/envolvimento ou estão enviando arquivos completos?
* Qual é o segmento &quot;seguro&quot; no arquivo em termos de recenticidade?
* Existem estratégias de reativação e reconfirmação em vigor para os segmentos que não estão definidos como seguros?

## Resolver o problema {#address-issue}

### Reclamações

[](/help/metrics/complaints.md)As reclamações são definidas por assinantes que relatam os emails como spam ao pressionar o botão correspondente em sua caixa de entrada.

Se o problema com seu delivery foi causado por reclamações:
* Você deve tentar determinar por que os recipients estão reclamando.
* Você pode mudar o link de cancelamento de assinatura para a parte superior do email. Os assinantes serão incentivados a cancelar a assinatura em vez de reclamar com o botão de spam.

Os remetentes podem obter uma grande quantidade de informações a partir das reclamações de [loop de feedback](/help/transition-process/infrastructure.md#feedback-loops):
* É importante agrupar os dados e procurar por padrões em coisas como origem da aceitação, quanto tempo o endereço está inscrito ou até mesmo alguns dados demográficos comportamentais.
* As queixas podem frequentemente identificar uma fonte de dados ou segmento com risco dentro do arquivo. O risco é definido como o mais provável de reclamação, o que pode prejudicar a reputação e, por sua vez, as taxas da caixa de entrada.

As reclamações também vêm de assinantes que não querem mais receber email:
* Isso pode ocorrer, muitas vezes, ao excesso de mensagens, à percepção dos assinantes sobre a mensagem, por não esperarem a mensagem ou não se lembrarem de aceitar o recebimento.
* Também é importante executar uma auditoria para garantir que todos os pontos de coleta estejam claros e que não haja caixas pré-marcadas nos pontos de aquisição.
* Também é necessário enviar um email de boas-vindas quando os assinantes optarem por definir o tom e explicar com que frequência eles podem receber emails.

### Validade dos dados

**As rejeições** ocorrem quando você envia para um **endereço que não pode ser entregue** em um ISP. Um endereço pode não ser entregue por vários motivos, como:
* Endereço com erro ortográfico. Isso pode ser resolvido com um serviço de validação de dados em tempo real ou por meio da exigência de uma aceitação confirmada antes de enviar emails de marketing para esse endereço.
* Lista ou fonte de dados incorreta. Se for proveniente de uma nova fonte, analise como os endereços foram coletados e verifique se havia permissão.
* Enviar mala direta para um endereço que já esteve ativo, mas que foi fechado ou encerrado após um período de inatividade.

### Envolvimento

Além das reclamações e da validade dos dados, os provedores de internet estão se concentrando mais do que nunca no **envolvimento positivo** para tomar decisões de entrega. Eles procuram saber se os assinantes estão abrindo seus emails ou se estão os excluindo antes de ler. Como eles não compartilham esses dados com remetentes, devemos usar as informações que temos disponíveis e traduzir aberturas/cliques/transações como envolvimento.

Como parte da manutenção contínua da reputação, é importante entender como os assinantes estão envolvidos em sua lista e desenvolver uma **hierarquia de risco de recenticidade** para os assinantes em cada arquivo. A recenticidade é definida como a última data de abertura/clique/transação ou de assinatura. Esse período pode diferir por setor. Para fazer isso:

1. Determine os segmentos ativos (&quot;seguros&quot;) para cada setor. Normalmente, são assinantes que estiveram ativos nos últimos 3 a 6 meses.
1. Reduza a frequência para inativos.
1. Crie uma série de [reenvolvimentos](/help/additional-resources/re-engagement.md) para iniciativas de risco moderado. Normalmente, são de 6 a 9 meses sem envolvimento.
1. Desenvolva uma campanha de reconfirmação para iniciativas de maior risco. Normalmente, são assinantes que não leem um email há um período de 9 a 12 meses.
1. Por fim, defina uma regra suspensa e remova os assinantes que não abriram seus emails em &quot;x&quot; meses. Normalmente, recomendamos mais de 12 meses, mas isso pode ser diferente com base no ciclo de vendas e compras.
