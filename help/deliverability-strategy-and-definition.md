---
title: Qual é a estratégia de deliverability e como definir a deliverability
description: Entenda como a capacidade de entrega é definida, por que ela é importante e as métricas principais de capacidade de entrega.
feature: Avaliação do delivery
topics: Deliverability
kt: 5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 11%

---


# Estratégia e definição da capacidade de entrega

Criar campanhas de marketing por email bem-sucedidas depende de ter uma compreensão clara das metas de marketing, sejam elas de prospecção ou de iniciativas de CRM (relacionamento com o cliente). Isso ajuda a determinar quem segmentar, o que promover e quando o alcance externo é ideal.

Estes são alguns exemplos de objetivos de estratégia de marketing por email:

* Adquirir novos clientes
* Conversão de prospetos em compradores pela primeira vez
* Crescendo os atuais relacionamentos do cliente com outras ofertas do cliente
* Manter clientes fiéis
* Aprimoramento da satisfação do cliente e da fidelidade da marca
* Reativação de clientes perdidos ou perdidos

## Deliverability defined

Há duas métricas principais que desempenham uma função na definição de deliverability. A *taxa de entrega* é a porcentagem de emails que não saltam e são aceitos pelo ISP. O próximo é *inbox placement* — é aplicado às mensagens aceitas pelo ISP e determina se o email chega à caixa de entrada ou à pasta de spam.

É importante entender a taxa de entrega e a taxa de posicionamento da caixa de entrada em conjunto ao medir o desempenho do email. Uma alta taxa de entrega não é a única faceta da capacidade de entrega. Apenas porque uma mensagem é recebida por meio de um ponto de verificação inicial do ISP não significa necessariamente que seu assinante realmente viu e interagiu com sua comunicação.

## Por que a capacidade de entrega é importante

Se você não sabe se seus emails estão sendo entregues ou se estão chegando na caixa de entrada versus a pasta de spam, é necessário. Aqui está o porquê.

Inúmeras horas vão para o planejamento e produção de suas campanhas de email. Se os emails devolverem ou acabarem chegando à pasta de spam de seus assinantes, seus clientes provavelmente não os lerão, sua chamada para a ação (CTA) não será confirmada e você ficará aquém das metas de receita devido a conversões perdidas. Em termos simples, você não pode se dar ao luxo de ignorar a capacidade de entrega. É fundamental para o sucesso de seus esforços de marketing por email e de seus resultados finais.

Seguir as práticas recomendadas de deliverability garante que seu email tenha a melhor chance possível de aberturas, cliques e o objetivo final - conversão. Você pode escrever uma linha de assunto brilhante e ter belas imagens e conteúdo envolvente. Mas se esse email não for entregue, o cliente não terá nenhuma oportunidade de conversão. Em suma, na capacidade de fornecimento de email, cada etapa do processo de aceitação de email depende da primeira para o sucesso do programa.

### Etapa 1: Email entregue

Fatores importantes para a entrega:

* **Infraestrutura** sólida: Configuração de IP e domínio, configuração de loop de feedback (FBL) (incluindo monitoramento e processamento de reclamações) e processamento de devolução regular. Para clientes da Adobe, a Adobe é responsável por essa configuração em nome de nossos clientes.
* **Autenticação** forte:  [!DNL Sender Policy Framework] (SPF),  [!DNL DomainKeys Identified Mail] (DKIM),  [!DNL Domain-based Message Authentication], elaboração de relatórios e conformidade (DMARC).
* **Alta qualidade** da lista: Aceitação explícita, métodos válidos de aquisição de email e políticas de envolvimento.
* **Uma cadência de envio consistente e a minimização das flutuações** de volume.
* **Alta reputação de IP e domínio**.

### Etapa 2: Inserção da caixa de entrada de email

Os ISPs têm algoritmos exclusivos, complexos e em constante mudança para determinar se seu email é colocado na caixa de entrada, no lixo ou na pasta de spam.

Estes são alguns fatores importantes para o posicionamento da caixa de entrada:

* Email enviado
* Alto engajamento
* Baixas reclamações (menos de 0,1% no total)
* Volume consistente
* Baixas de spam
* Taxa de rejeição de disco rígido baixa
* Falta de problemas da lista de bloqueios

### Etapa 3: Participação no email — aberturas

Estes são alguns fatores importantes para a taxa de abertura:

* Email entregue e colocado na caixa de entrada
* Reconhecimento da marca
* Linha de assunto e pré-cabeçalhos obrigatórios
* Personalização
* Frequência
* Relevância ou valor do conteúdo

### Etapa 4: Participação no email — cliques

Estes são alguns fatores importantes para a taxa de cliques:

* Email entregue, entregue na caixa de entrada e aberto
* CTA forte
   * Essa é a ação principal que você deseja realizar com seu público-alvo. Normalmente, é um clique em um URL. Certifique-se de que seja claro e fácil para o usuário encontrar.
* Relevância ou valor do conteúdo

### Etapa 5: Conversão

Estes são alguns fatores importantes para a conversão:

* Tudo acima
* Transição de email por meio de um URL de trabalho para uma página de aterrissagem ou página de vendas
* Experiência da página de aterrissagem
* Reconhecimento de marca, percepção e fidelidade

### Impacto potencial na receita

A conversão é a chave, mas qual é a alternativa? Sua estratégia de deliverability pode fortalecer ou causar estrago no programa de marketing por email nirvana. O gráfico a seguir ilustra a possível perda de receita que uma política de capacidade de delivery fraca pode ter em seu programa de marketing. Como demonstrado, para uma empresa com uma taxa de conversão de 2% e compra média de US$ 100, cada redução de 10% na colocação da caixa de entrada equivale a uma perda de receita de quase US$ 20.000. Lembre-se de que esses números são exclusivos para cada remetente.

| Enviado | Porcentagem | Entregues | Porcentagem | Caixa de entrada | Número na caixa de entrada | Índice de conversão | Número de perdidos | Average | Perdido |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|  | entregues |  | caixa de entrada |  |  |  | Conversões | purchase | receita |
| 100 K | 99% | 99K | 100% | 99K | - | 2% | 0 | US$ 100 | $ - |
| 100 K | 99% | 99K | 90% | 89,1K | 9.900 | 2% | 198 | US$ 100 | US$ 19.800 |
| 100 K | 99% | 99K | 80% | 79,2 K | 19 800 | 2% | 396 | US$ 100 | US$ 39.600 |
| 100 K | 99% | 99K | 70% | 69,3 K | 29 700 | 2% | 594 | US$ 100 | US$ 59.400 |
| 100 K | 99% | 99K | 60% | 59,4 K | 39 600 | 2% | 792 | US$ 100 | 79.200 $ |
| 100 K | 99% | 99K | 50% | 49,5 K | 49 500 | 2% | 990 | US$ 100 | 99.000 $ |
| 100 K | 99% | 99K | 40% | 39,6 K | 59 400 | 2% | 1188 | US$ 100 | US$ 118.800 |
| 100 K | 99% | 99K | 30% | 29,7 K | 69 300 | 2% | 1386 | US$ 100 | US$ 138.600 |
| 100 K | 99% | 99K | 20% | 19,8 K | 79 200 | 2% | 1584 | US$ 100 | US$ 158.400 |
