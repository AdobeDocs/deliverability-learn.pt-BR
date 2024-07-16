---
title: Gmail
description: O Gmail é a maior parte das listas de email da maioria dos remetentes. Eles também tendem a tratar o email de forma um pouco diferente do resto.
topics: Deliverability
jira: KT-5262
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: a7319c85-32b5-4a9e-bee9-24f13630c408
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# [!DNL Gmail]

[!DNL Gmail] constitui a maior parte das listas de email da maioria dos remetentes. Eles também tendem a tratar o email de forma um pouco diferente do resto.

Estes são alguns destaques:

## Quais dados são importantes

O [!DNL Gmail] concentra-se nos comentários dos usuários para a maior parte das suas decisões de filtragem. Embora não possamos saber o molho secreto envolvido nessas decisões, há padrões comuns que a maioria dos profissionais de marketing pode monitorar. As taxas de abertura e de clique fornecerão informações sobre o engajamento do público-alvo e poderão ser usadas para promover reputação positiva e alta inserção na caixa de entrada.

## Quais dados estão disponíveis?

O [!DNL Gmail] oferece insights limitados sobre como ele visualiza suas práticas de envio por meio das Ferramentas do [!DNL Gmail Postmaster]. Essa ferramenta permite uma exibição de alto nível da reputação do IP e do domínio de envio, dos resultados de autenticação e de problemas de reclamação.

>[!NOTE]
>
>[!DNL Gmail] não exibe dados em todas as reclamações, nem facilitam um FBL tradicional. Em vez disso, apenas fornecem dados em determinadas circunstâncias, geralmente envolvendo tanto volumes elevados como taxas de reclamação muito elevadas. Embora manter as reclamações no mínimo seja fundamental para uma boa capacidade de entrega, é natural que algumas reclamações sejam filtradas. Se as reclamações são sincronizadas regularmente a zero, isso pode apontar para um problema que requer investigação adicional.

## Reputação do remetente

[!DNL Gmail] rastreia IP, domínio e até mesmo reputação da marca. Alterar seu IP ou domínio (ou ambos) não permitirá que você abale facilmente uma má reputação. Uma correção rápida ou criativa pode ser tentadora, mas é muito mais eficaz alocar tempo e esforço para corrigir a raiz de um problema de reputação relacionado aos ganhos de inserção na caixa de entrada.

## Insights

[!DNL Gmail] exibições envolviam assinantes de forma diferente da maioria dos remetentes tradicionalmente. Um remetente pode definir uma lista ativa ou engajada como alguém que abriu um email dentro de 30, 90 ou 180 dias (dependendo do modelo de negócios). O [!DNL Gmail], por outro lado, está observando a frequência com que seus usuários interagem com suas mensagens.

Por exemplo, se você enviar 3 emails por semana durante 90 dias, seriam aproximadamente 39 emails. Usando o método tradicional, se o assinante abriu um desses 39 emails, ele está envolvido. Para [!DNL Gmail], isso significa que eles ignoraram 38 emails e não estão envolvidos. Você pode obter uma sensação aproximada dos níveis de engajamento de seus próprios usuários em [!DNL Gmail] ao classificá-los na contagem aberta dos últimos 10 emails. Portanto, um assinante associado a 7 aberturas dos últimos 10 emails é mais engajado do que alguém que abriu 2 dos 10. Enviar emails com menos frequência para os usuários menos envolvidos ajudará a melhorar sua reputação de envio no [!DNL Gmail].

O [!DNL Gmail] usa guias diferentes para usuários distinguirem tipos diferentes de email. Estes são: *Caixa de Entrada*, *Social* e *Promocional*. Mesmo que o email seja entregue na guia Promocional, ele ainda será considerado um delivery de caixa de entrada. Os usuários têm controle para modificar a visualização e as guias.
