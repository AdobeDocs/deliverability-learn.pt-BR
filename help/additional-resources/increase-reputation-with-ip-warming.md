---
title: Aumente sua reputação de email com o aquecimento de IP
description: Saiba por que é importante melhorar sua reputação de email com o aquecimento de IP e como proceder para obter o delivery ideal.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: b553a13e-2055-4abc-b784-fd52792380d0
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '1600'
ht-degree: 3%

---

# Aumente sua reputação de email com o aquecimento de IP

<!--Increase your email reputation with IP warming

## IP Warming overview

In the Adobe Deliverability Consulting and Deliverability Operations teams, we have a vested interest in helping new Campaign customers be as successful as possible as they embark on the route of an IP warming process. If you’ve never been a part of such a project, you may have a lot of questions about it. Let’s get down to the details!-->

## Introdução

O Adobe exige que os clientes compartilhem a configuração para ajudar a equipe de avaliação de entrega de Adobe a entender seu programa exclusivo. As perguntas que fazemos foram projetadas para ajudar a equipe de Entregabilidade do Adobe a ter uma noção da reputação de envio e do volume de email. Sem uma compreensão concreta do seu modelo de negócios, das metas de marketing por email e das métricas de reputação, não poderemos personalizar a estratégia e há risco de problemas de entrega.

No início, você receberá seus próprios endereços IP dedicados (Internet Protocol, Protocolo de Internet). No contexto de envio de email, um endereço IP é a rota usada para entregar suas mensagens de email aos clientes. Endereços IP e domínios são usados para identificar os remetentes em uma rede para os ISPs de recebimento. O Adobe atribui o número apropriado de endereços IP dedicados para enviar emails, com base no volume de envio, programas de email, práticas de segmentação de dados e seu contrato.

**Tópicos relacionados:**
* [Como fazer a transição descomplicada ao alternar plataformas de email](../../help/transition-process/switching-email-platforms.md)
* [Estratégia de IP](../../help/transition-process/infrastructure.md#ip-strategy)
* [Considerações específicas do ISP durante o aquecimento de IP](../../help/transition-process/isp-specific-considerations-during-ip-warming.md)

## Aquecimento de IP: Por que isso é feito? {#why-ip-warming}

Os provedores de serviço de internet (ISPs) ou provedores de caixa de correio (MBPs) tomam precauções ao detectar um IP e um domínio de envio desconhecidos. Esse é o procedimento padrão associado a qualquer novo IP de envio, independentemente do tipo de remetente. Os ISPs/MBPs colocam o IP e o domínio de envio sob alta análise para determinar se os emails enviados desse IP e domínio são spam ou não.  Esse é o procedimento padrão associado a qualquer novo IP de envio, independentemente do tipo de remetente.

Os ISPs examinam cuidadosamente o volume de envio, a frequência de envio, as reclamações e as taxas de rejeição geradas por essas correspondências. Todos são verificados atentamente porque são indicadores de reputação do remetente - seja bom ou ruim.

Naturalmente, esse processo de análise desses pontos de dados leva tempo e não pode ser feito em um ou dois dias. A reputação é construída ao longo do tempo. Esse processo é como deixar um estranho em sua casa. Você teria reservas sobre alguém que você nunca conheceu entrar em sua casa?

Muito provavelmente a resposta é sim. Você gostaria de analisar esta pessoa e seus motivos. Eles querem dizer mal? Eles são uma ameaça? Os ISPs fazem o mesmo para proteger sua rede contra tráfego mal-intencionado ou indesejado. Métricas de reputação positivas ajudam você a percorrer um longo caminho em um processo bem-sucedido de aquecimento de IP. É por isso que enfatizamos a importância de começar com o envio de pequenos volumes de email e o envio para seus clientes altamente engajados primeiro. Para obter mais informações, consulte [Critérios de direcionamento ao enviar novo tráfego](/help/transition-process/targeting-criteria.md).

Enviar grandes quantidades de email de um IP totalmente novo ou de IPs diretamente da porta é uma prática ruim e provavelmente causará algumas dificuldades de entrega. É importante observar que, mesmo que você comece a enviar volumes pequenos e aumentá-los gradualmente conforme recomendado, ainda será necessário seguir as práticas recomendadas de email.

![](../../help/assets/ip-warming-volume-trend.png)

## Permissão para email (aceitação explícita)

Esse é o componente mais importante do gerenciamento e do crescimento de uma lista de email de assinante. À medida que as leis antisspam crescem e se tornam mais abrangentes internacionalmente, deve ser o foco principal do profissional de marketing garantir que ele receba consentimento explícito (ou expresso) de cada assinante em sua lista. Ou seja, cada assinante concordou ativamente em receber emails da sua marca. Isso é diferente do consentimento implícito em que uma pessoa é adicionada a uma lista de email após realizar uma ação que não estava se inscrevendo explicitamente em um programa de email.

Saiba mais sobre [Política de uso aceitável do Adobe](https://www.adobe.com/legal/terms/aup.html).

## Métricas de reputação: o que os ISPs procuram?

Os ISPs usam tecnologia sofisticada para tomar decisões conscientes sobre entregar ou não e-mails que estão recebendo de redes externas. Às vezes, eles têm algoritmos complicados e proprietários em seu conjunto de ferramentas para ajudá-los nesse processo.

Alguns dos dados examinados são:

* Ocorrências de interceptação de spam
* Incluir na lista de bloqueios ocorrências
* Rejeições de email
* Engajamento do assinante

Os ISPs exigem configurações técnicas específicas alinhadas às suas políticas e práticas recomendadas. O Adobe configura seus IPs e subdomínios delegados para identificá-lo como um remetente responsável e confiável. Isso é chamado de [autenticação de email](/help/transition-process/infrastructure.md#authentication). A autenticação ajuda os receptores a validar se um remetente tem os direitos para enviar desse IP ou domínio.

A autenticação permite que os ISPs validem se a empresa que envia de um domínio ou IP tem o direito de fazer isso. É essencialmente feito para provar sua identidade e garantir que você não esteja fingindo ser outra pessoa e que outra pessoa não esteja fingindo ser você.

No Adobe, configuraremos o SPF e o DKIM por padrão e o DMARC será configurado por solicitação. Os ISPs referenciam o SPF e o DKIM como as formas primárias de autenticação. Muitos ISPs também estão incorporando DMARC (Domain-based Message Authentication, Reporting &amp; Conformance) em suas decisões de filtragem. Emails não autenticados não são necessariamente bloqueados, mas passam por filtragens adicionais.

## Aquecimento de IP: o que esperar

### Email limitado ou bloqueado

Os remetentes de spam enviam de novos IPs o tempo todo; eles gravarão em um pool de IPs até que sejam desligados e repitam o processo em outro pool de IPs. Como resultado, os ISPs tratam o tráfego que está sendo enviado de novos IPs com cuidado. Eles bloqueiam o envio de grande quantidade de e-mails por IPs porque suspeitam que essa atividade esteja sendo executada por remetentes de spam.

Consequentemente, não é incomum receber mensagens de diferimento ou limitadas quando você começa a enviar de seus novos IPs. Após algumas tentativas, a mensagem geralmente é aceita e entregue.

Alcançar um fluxo normal de tráfego para os ISPs que adiam novos remetentes pode levar alguns dias. Mesmo assim, não pare de enviar emails - continue se concentrando em enviar somente para os assinantes de email mais engajados.

Em casos raros, o ISP bloqueia o novo remetente. O Adobe está monitorando sua conta e, se houver suspeita de um bloqueio, entrará em contato com o ISP para tentar ajudar a corrigir a situação da melhor maneira possível.

Lembre-se de que a consistência é fundamental aqui. Padrões de volume de envio irregulares e padrões de envio pouco frequentes causarão alguns desafios de deliverability ao longo do caminho.

### Reclamações

[Reclamações](/help/metrics/complaints.md) ocorrem quando um assinante rotula um email como spam por meio de seu programa de email. Isso envia um aviso ao ISP sobre a atividade de reclamação. Se houver um número suficiente dessas reclamações que chegam ao ISP, esse ISP atuará para proteger seus clientes - possivelmente bloqueará o acesso de muitos emails aos assinantes ou direcionará uma parte dos emails para a pasta em massa em vez das caixas de entrada dos assinantes. Se o problema do delivery for causado por reclamações, é importante determinar por que os recipients estão reclamando.

Os assinantes reclamam por vários motivos. Às vezes, um assinante não quer receber mais nenhum email seu, talvez porque sinta que está recebendo muitas mensagens sobre o mesmo tópico, não estava esperando a mensagem ou não se lembra de se inscrever para receber seus emails.

### Validade dos dados

As rejeições ocorrem quando você envia para um endereço que não pode ser entregue em um ISP. Um endereço pode não ser entregue por vários motivos, como um erro ao digitar o endereço ou enviar para um endereço que estava anteriormente ativo, mas foi fechado ou encerrado após um período de inatividade.

Se você encontrar um número substancial de rejeições permanentes, é importante entender o porquê. Revise como os endereços foram coletados e confirme se a permissão foi fornecida. Às vezes, as pessoas fecham sua conta de email e não notificam aqueles que têm esse endereço em sua lista de marketing.

### Envolvimento

Os ISPs procuram um volume consistente e boa qualidade dos dados. Você aumentará lenta e constantemente o tráfego nas próximas quatro a oito semanas. Às vezes, os aumentos exigem mais ou menos tempo com base no volume e nas metas, mas normalmente é um processo de pelo menos 8 semanas.

O tráfego de email deve ser implantado em uma progressão lenta e constante, aumentando a cada semana até que toda a lista seja enviada. Além disso, cada segmento seguirá a programação até a conclusão. Comece com os assinantes mais recentes primeiro e termine com os assinantes menos engajados por último. Observe também que alguns ISPs podem exigir uma abordagem mais personalizada devido à maneira como lidam com o novo tráfego.

Saiba mais sobre [envolvimento](/help/engagement.md).

## Mantenha o curso

Você pode se sentir tentado a apressar o processo de aquecimento de IP, enviando mais volume do que o recomendado, negligenciando a identificação de seus assinantes mais engajados e deixando de enviar esses assinantes primeiro, em um esforço para criar uma reputação positiva. Por favor, resista a este impulso! Não vai ajudá-lo a longo prazo.

É muito importante começar a enviar o seu altamente engajado (com e-mail!) assinantes somente para os estágios iniciais do aquecimento de IP. Esses clientes são os mais valiosos e sua propensão a abrir emails ajudará a começar a mostrar aos ISPs que você é um profissional de marketing que envia emails interessantes e solicitados. Ele também mostra aos ISPs que você está seguindo as regras e seguindo as práticas recomendadas.

## Conclusão

Lembre-se: O aquecimento de IP é uma maratona - não um sprint!  Embora o processo possa parecer trabalhoso e demorado, seria mais trabalhoso tentar reparar uma reputação danificada por não seguir as práticas recomendadas de email testadas e verdadeiras.

Quanto melhores forem suas práticas de envio e maior for sua pontuação de reputação com os ISPs, mais provável será que seus emails sejam entregues. O aquecimento e o aumento do IP, juntamente com o cumprimento das práticas recomendadas para o design de sua mala direta, ajudarão a otimizar o delivery da sua caixa de entrada.

Nossa equipe de entrega global é sua parceira neste processo e ajudará você durante esta fase de aquecimento de IP para posicioná-lo para o sucesso.
