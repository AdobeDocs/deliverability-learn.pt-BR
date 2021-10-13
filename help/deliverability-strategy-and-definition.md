---
title: Qual é a estratégia de entrega e como defini-la
description: Entenda como a capacidade de entrega é definida, por que ela é importante e quais são suas métricas principais
topics: Deliverability
kt: 5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 5285eda9-5099-48d5-b150-ce2c376ee549
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Estratégia e definição da capacidade de entrega

A criação de campanhas de marketing por email bem-sucedidas depende de uma compreensão clara das metas de marketing, sejam elas de prospecção ou de iniciativas de CRM (gestão de relacionamento com o cliente). Isso ajuda a determinar quem segmentar, o que promover e quando o alcance externo é ideal.

Estes são alguns exemplos de objetivos de estratégia de marketing por email:

* Obtenção de novos clientes
* Conversão de prospectos em compradores pela primeira vez
* Incremento das relações atuais com o cliente por meio de ofertas adicionais
* Manutenção de clientes fiéis
* Aumento da satisfação do cliente e da lealdade à marca
* Reativação de clientes perdidos ou antigos

## Definição da capacidade de entrega

Há duas métricas principais que desempenham uma função na definição da capacidade de entrega. A *taxa de entrega* é a porcentagem de emails que não são rejeitados e são aceitos pelo ISP. O próximo é *inbox placement*, aplicado às mensagens aceitas pelo ISP e determina se o email chega à caixa de entrada ou à pasta de spam.

É importante entender conjuntamente a taxa de entrega e a taxa de posicionamento da caixa de entrada ao medir o desempenho do email. Uma alta taxa de entrega não é a única faceta da capacidade de entrega. Apenas porque uma mensagem é recebida por meio de um ponto de verificação inicial do ISP não significa necessariamente que seu assinante realmente viu e interagiu com sua comunicação.

## Por que a capacidade de entrega é importante

Você deveria saber se seus emails estão sendo entregues ou se estão chegando na caixa de entrada ou na pasta de spam. Aqui está o porquê.

Inúmeras horas vão para o planejamento e produção de suas campanhas de email. Se os emails forem devolvidos ou forem enviados à pasta de spam de seus assinantes, seus clientes provavelmente não os lerão, sua chamada para a ação (CTA) não será confirmada e você ficará aquém das metas de receita devido a conversões perdidas. Em termos simples, você não pode se dar ao luxo de ignorar a capacidade de entrega. É fundamental para o sucesso de suas iniciativas de marketing por email e de seus resultados finais.

Seguir as práticas recomendadas de entrega garante que seu email tenha a melhor chance possível de aberturas, cliques e o objetivo final que são as conversões. Você pode escrever uma linha de assunto brilhante e ter belas imagens e conteúdo envolvente. Mas se esse email não for entregue, o cliente não terá nenhuma oportunidade de conversão. Em resumo, na capacidade de fornecimento de email, cada etapa do processo de aceitação de email depende da etapa anterior para o sucesso do programa.

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

* Email enviado
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
* Transição de email por meio de um URL de trabalho para uma página de aterrissagem ou página de vendas
* Experiência da página de aterrissagem
* Reconhecimento de marca, percepção e fidelidade

### Impacto potencial na receita

A conversão é a chave, mas qual é a alternativa? Sua estratégia de entrega pode fortalecer ou destruir o programa de marketing por email. O gráfico a seguir ilustra a possível perda de receita que uma política de capacidade de delivery fraca pode ter em seu programa de marketing. Como demonstrado, para uma empresa com uma taxa de conversão de 2% e compra média de US$ 100, cada redução de 10% na inserção da caixa de entrada equivale a uma perda de receita de quase US$ 20.000,00. Lembre-se de que esses números são exclusivos para cada remetente.

| Enviado | Porcentagem | Entregues | Porcentagem | Caixa de entrada | Número na caixa de entrada | Índice de conversão | Número de perdas | Média | Perdas |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|  | Entregues |  | Caixa de entrada |  |  |  | Conversões | Aquisição | Receita |
| 100 mil | 99% | 99 mil | 100% | 99 mil | - | 2% | 0 | US$ 100 | US$ - |
| 100 mil | 99% | 99 mil | 90% | 89,1 mil | 9.900 | 2% | 198 | US$ 100 | US$ 19.800 |
| 100 mil | 99% | 99 mil | 80% | 79,2 mil | 19.800 | 2% | 396 | US$ 100 | US$ 39.600 |
| 100 mil | 99% | 99 mil | 70% | 69,3 mil | 29.700 | 2% | 594 | US$ 100 | US$ 59.400 |
| 100 mil | 99% | 99 mil | 60% | 59,4 mil | 39.600 | 2% | 792 | US$ 100 | US$ 79.200 |
| 100 mil | 99% | 99 mil | 50% | 49,5 mil | 49.500 | 2% | 990 | US$ 100 | US$ 99.000 |
| 100 mil | 99% | 99 mil | 40% | 39,6 mil | 59.400 | 2% | 1188 | US$ 100 | US$ 118.800 |
| 100 mil | 99% | 99 mil | 30% | 29,7 mil | 69.300 | 2% | 1386 | US$ 100 | US$ 138.600 |
| 100 mil | 99% | 99 mil | 20% | 19,8 mil | 79.200 | 2% | 1584 | US$ 100 | US$ 158.400 |
