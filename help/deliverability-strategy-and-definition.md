---
title: Qual é a estratégia de entrega e como defini-la
description: Entenda como a capacidade de entrega é definida, por que ela é importante e quais são suas métricas principais
topics: Deliverability
jira: KT-5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: ACS
exl-id: 5285eda9-5099-48d5-b150-ce2c376ee549
TQID: https://experienceleague.adobe.com/0cwY27ArgkAVUOuF8aE4-qwaGpCq1dv-5S8mkdLQXhg
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b3b8a63f-51fc-40f6-a7d2-a31c5d49fb45id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: ed6be6bb-75bb-4ea9-9a42-3bcaa65e1bcc
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: beb7a3c1-66ab-4786-b879-7621375b3c40id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 855
ht-degree: 100%

---

# Estratégia e definição da capacidade de entrega

A criação de campanhas de marketing por email bem-sucedidas depende de uma compreensão clara das metas de marketing, sejam elas de prospecção ou de iniciativas de CRM (gestão de relacionamento com o cliente). Isso ajuda a determinar quem segmentar, o que promover e quando o alcance externo é ideal.

Estes são alguns exemplos de objetivos de estratégia de marketing por email:

* Obtenção de novos clientes
* Conversão de clientes potenciais em compradores pela primeira vez
* Incremento das relações atuais com o cliente por meio de ofertas adicionais
* Manutenção de clientes fiéis
* Aumento da satisfação do cliente e da fidelidade à marca
* Reativação de clientes perdidos ou antigos

## Definição da capacidade de entrega

Há duas métricas principais que desempenham uma função na definição da capacidade de entrega. A *taxa de entrega* é a porcentagem de emails que não são rejeitados e são aceitos pelo ISP. O próximo é *inbox placement*, aplicado às mensagens aceitas pelo ISP e determina se o email chega à caixa de entrada ou à pasta de spam.

É importante entender conjuntamente a taxa de entrega e a taxa de posicionamento da caixa de entrada ao medir o desempenho do email. Uma alta taxa de entrega não é a única faceta da capacidade de entrega. Apenas porque uma mensagem é recebida por meio de um ponto de verificação inicial do ISP não significa necessariamente que seu assinante realmente viu e interagiu com sua comunicação.

## Por que a capacidade de entrega é importante

Você deveria saber se seus emails estão sendo entregues ou se estão chegando na caixa de entrada ou na pasta de spam. Veja por quê.

Inúmeras horas vão para o planejamento e produção de suas campanhas de email. Se os emails forem devolvidos ou forem enviados à pasta de spam de seus assinantes, seus clientes provavelmente não os lerão, sua chamada para a ação (CTA) não será confirmada e você ficará aquém das metas de receita devido a conversões perdidas. Em termos simples, você não pode se dar ao luxo de ignorar a capacidade de entrega. É fundamental para o sucesso de suas iniciativas de marketing por email e de seus resultados finais.

Seguir as práticas recomendadas de entrega garante que seu email tenha a melhor chance possível de aberturas, cliques e o objetivo final que são as conversões. Você pode escrever uma linha de assunto brilhante e ter belas imagens e conteúdo envolvente. Mas se esse email não for entregue, o cliente não terá nenhuma oportunidade de conversão. Em resumo, na capacidade de entrega de email, cada etapa do processo de aceitação de email depende da etapa anterior para o sucesso do programa.

### Etapa 1: Email entregue

Fatores importantes para a entrega:

* **Infraestrutura sólida**: Configuração de IP e domínio, configuração de loop de feedback (FBL) (incluindo monitoramento e processamento de reclamações) e processamento de devolução regular. Para clientes próprios, a Adobe se responsabiliza por essa configuração em nome de seus clientes.
* **Autenticação forte**: [!DNL Sender Policy Framework] (SPF), [!DNL DomainKeys Identified Mail] (DKIM), [!DNL Domain-based Message Authentication], elaboração de relatórios e conformidade (DMARC).
* **Alta qualidade da lista**: Aceitação explícita, métodos válidos de aquisição de email e políticas de engajamento.
* **Cadência de envio consistente e minimização de flutuações de volume**.
* **Alta reputação de IP e domínio**.

### Etapa 2: Inserção da caixa de entrada de email

Os ISPs têm algoritmos exclusivos, complexos e dinâmicos para determinar se seu email é colocado na caixa de entrada, na lixeira ou na pasta de spam.

Estes são alguns fatores importantes para a inserção da caixa de entrada:

* Email entregue
* Alto engajamento
* Poucas reclamações (menos de 0,1% no total)
* Volume consistente
* Baixa cobertura de spam
* Baixa taxa de rejeição de disco rígido
* Ausência de problemas na lista de bloqueios

### Etapa 3: Engajamento no email — aberturas

Estes são alguns fatores importantes para a taxa de abertura:

* Email entregue e colocado na caixa de entrada
* Reconhecimento da marca
* Linha de assunto e pré-cabeçalhos obrigatórios
* Personalização
* Frequência
* Relevância ou valor do conteúdo

### Etapa 4: Engajamento no email — cliques

Estes são alguns fatores importantes para a taxa de cliques:

* Email entregue, enviado à caixa de entrada e aberto
* CTA forte
   * Essa é a ação principal que você deseja realizar com seu público-alvo. Normalmente, é um clique em um URL. Verifique se é claro e fácil para o usuário encontrar o URL.
* Relevância ou valor do conteúdo

### Etapa 5: Conversão

Estes são alguns fatores importantes para a conversão:

* Tudo acima
* Transição de email por meio de um URL de trabalho para uma página de destino ou página de vendas
* Experiência da página de destino
* Reconhecimento de marca, percepção e fidelidade

### Impacto potencial na receita

A conversão é a chave, mas qual é a alternativa? Sua estratégia de entrega pode fortalecer ou destruir o programa de marketing por email. O gráfico a seguir ilustra a possível perda de receita que uma política de capacidade de entrega fraca pode ter em seu programa de marketing. Como demonstrado, para um negócio com uma taxa de conversão de 2% e compra média de US$ 100, cada redução de 10% na inserção da caixa de entrada equivale a uma perda de receita de quase US$ 20.000,00. Lembre-se de que esses números são exclusivos para cada remetente.

| Enviado | Porcentagem | Entregues | Porcentagem | Caixa de entrada | Número na caixa de entrada | Índice de conversão | Número de perdas | Média | Perdas |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|      | Entregues |           | Caixa de entrada |       |                     |                 | Conversões | compra | Receita |
| 100 mil | 99% | 99 mil | 100% | 99 mil | - | 2% | 0 | US$ 100 | US$ - |
| 100 mil | 99% | 99 mil | 90% | 89,1 mil | 9.900 | 2% | 198 | US$ 100 | US$ 19.800 |
| 100 mil | 99% | 99 mil | 80% | 79,2 mil | 19.800 | 2% | 396 | US$ 100 | US$ 39.600 |
| 100 mil | 99% | 99 mil | 70% | 69,3 mil | 29.700 | 2% | 594 | US$ 100 | US$ 59.400 |
| 100 mil | 99% | 99 mil | 60% | 59,4 mil | 39.600 | 2% | 792 | US$ 100 | US$ 79.200 |
| 100 mil | 99% | 99 mil | 50% | 49,5 mil | 49.500 | 2% | 990 | US$ 100 | US$ 99.000 |
| 100 mil | 99% | 99 mil | 40% | 39,6 mil | 59.400 | 2% | 1188 | US$ 100 | US$ 118.800 |
| 100 mil | 99% | 99 mil | 30% | 29,7 mil | 69.300 | 2% | 1386 | US$ 100 | US$ 138.600 |
| 100 mil | 99% | 99 mil | 20% | 19,8 mil | 79.200 | 2% | 1584 | US$ 100 | US$ 158.400 |
