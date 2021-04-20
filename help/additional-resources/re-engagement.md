---
title: Práticas recomendadas de reengajamento
description: Saiba como melhorar a capacidade de entrega por meio de estratégias de reengajamento.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 62%

---


# Práticas recomendadas de reengajamento {#re-engagement}

Ao implementar a capacidade de entrega, algumas das práticas recomendadas consistem em tentar manter uma base de assinantes saudável e melhorar a capacidade de entrega por meio de estratégias de reengajamento (ou reconquista).

* Manter uma base de assinantes saudável é um dos principais aspectos para garantir um delivery adequado e consistente. Muitos problemas de deliverability surgem de práticas e manutenção de dados ruins.
* Um dos problemas mais comuns que os profissionais de marketing enfrentam hoje é a inatividade de assinantes (também conhecida como baixa ou sem engajamento), o que pode afetar negativamente o delivery de emails e gerar um ROI baixo.

>[!NOTE]
>
>Para obter mais informações sobre estratégias de campanha de reengajamento e serviços de capacidade de entrega da Adobe, entre em contato com seu consultor de capacidade de entrega ou fale com o seu agente de vendas da Adobe.

## Como os ISPs visualizam as atividades sem engajamento? {#how-do-isps-view-non-engagement-activity-}

Por anos, os ISPs usaram métricas de comentários de engajamento de seus usuários para decidir onde colocar mensagens ou mesmo se deveriam enviá-las. O usuário [envolvimento](/help/engagement.md) consiste em comentários positivos e negativos e os ISPs monitoram ambos constantemente. Não ter engajamento talvez seja um dos principais colaboradores para o engajamento negativo. Do ponto de vista de deliverability, o envio consistente de campanhas para usuários que não demonstram engajamento também pode piorar a reputação geral do seu endereço IP e domínios.

ISPs como Gmail, Microsoft e OATH consideram emails não desejados e começam a redirecionar mensagens para a pasta de spam. Além disso, esses assinantes podem não ter mais a conta de email, e isso pode ser usado como uma interceptação de spam &quot;reciclado&quot;. Isso significa que o endereço ficou inválido por algum tempo e todas as mensagens são rejeitadas. Se o seu sistema de gerenciamento de assinantes não estiver removendo endereços de &quot;devolução permanente&quot;, é muito provável que ele envie mensagens para interceptações de spam que possam levar a problemas significativos de delivery.

## Como abordar a inatividade? {#how-should-you-approach-inactivity-}

Os clientes que usam a plataforma Adobe podem visualizar a inatividade em sua instância, revisando os dados de abertura e clique de acordo com o segmento. Como o não engajamento pode atrapalhar o delivery, a primeira ideia pode ser remover os assinantes do banco de dados. No entanto, isso pode ser uma opção errada às vezes. Portanto, uma estratégia de reengajamento (também conhecida como reconquista) é a melhor recomendação para reter os assinantes que estão interessados em receber emails e eliminar gradativamente aqueles que não mostram mais atividade.

## As campanhas de reengajamento realmente funcionam? {#do-re-engagement-campaigns-really-work-}

De acordo com um estudo da Return Path, as campanhas de engajamento vêm com um resultado de 12% de taxa de abertura em comparação a uma média de 14% para campanhas normais. Embora apenas 24% dos assinantes tenham lido a campanha de reengajamento, cerca de 45% deles leram as mensagens subsequentes.

![](../../help/assets/deliverability_implementation_1.png)

## Como criar uma campanha de reengajamento? {#how-do-you-create-a-re-engagement-campaign-}

### Fase 1 {#phase-1}

* A primeira etapa é identificar os assinantes que têm pouca atividade de clique ou de abertura e segmentar esse grupo correspondente com base em um intervalo de tempo definido. A regra é rever os assinantes que não abriram ou não clicaram em um email nos últimos 90 dias. No entanto, isso varia de acordo com a natureza da empresa (por exemplo, envio sazonal).
* Outro ponto a considerar durante a definição de cronogramas é que os ISPs e as empresas na lista de bloqueios consideram que o engajamento está em algum ponto entre 1,5 e 1,8 ano. Além disso, atividades comportamentais, como compras e atividade do site, ou outros pontos de contato, como preferências durante a fase de inscrição ou o primeiro ponto de contato.

### Fase 2 {#phase-2}

* Depois que um segmento é definido, a próxima etapa é criar uma campanha de reengajamento que satisfaça o assinante de acordo com as métricas identificadas. Criar uma linha de assunto ajuda a aumentar o interesse do assinante. De acordo com um estudo dda Return Path, linhas e conteúdo de assunto que declaram &quot;sentimos sua falta&quot; geram taxas de resposta mais altas do que &quot;queremos você de volta&quot;.
* Um incentivo também pode ser oferecido para reengajamento com o email. Ao considerar ofertas com descontos, é melhor usar valores em reais em vez de porcentagens. A Return Path também sugere fazer isso, pois incorre em taxas de resposta mais altas. Finalmente, executar testes de divisão A/B para revisar a resposta e as taxas de sucesso também é uma opção útil.

### Fase 3 {#phase-3}

A próxima etapa é determinar a frequência da campanha de reengajamento. Ao contrário das mensagens de reconfirmação, as campanhas de reengajamento são destinadas a conquistar o assinante com uma série de emails com o tempo. O exemplo a seguir se refere à frequência.

![](../../help/assets/deliverability_implementation_2.png)

Os assinantes que interagem com a campanha seguindo a atividade de abertura ou de clique são adicionados novamente à lista de assinantes engajados.

### Fase 4 {#phase-4}

* A próxima fase é identificar os assinantes que não mostram nenhuma atividade continuamente e reduzir gradativamente o envio de emails a eles durante um período. Se não houve atividade no ano passado, é bom colocar a subscrição de email dos assinantes em espera. Embora eles não tenham mostrado interesse no conteúdo do email, há sempre uma última chance de reativarem sua subscrição ao enviar uma única campanha de reconfirmação.
* As campanhas de reconfirmação são uma boa maneira de perguntar aos assinantes que estão inativos por um longo período se querem permanecer na lista de subscrição. Ao criar a campanha, é preferível adicionar um link &quot;clique aqui&quot; para que possam confirmar a ação e verificar seu endereço. Dessa forma, a ação pode ser registrada no banco de dados. Veja abaixo um exemplo de um email de reconfirmação:

   ![](../../help/assets/deliverability_implementation_3.png)

   Depois que o assinante realizar uma ação, você pode oferecer uma landing page com a confirmação da renovação de subscrição. Veja um exemplo da landing page:

   ![](../../help/assets/deliverability_implementation_4.png)

## Recursos específicos do produto

**Adobe Campaign**

* [Logs de rastreamento no Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Logs de rastreamento no Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**Gerenciamento de Jornadas do cliente Adobe**

* [Rastreamento de mensagens](https://experienceleague.adobe.com/docs/customer-journey-management/using/reporting/message-tracking.html)