---
title: Infraestrutura
description: Saiba o que é necessário para construir corretamente uma infraestrutura de email.
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 2%

---

# Infraestrutura

A capacidade de entrega bem-sucedida depende de uma base sólida. A infraestrutura de email é um elemento principal. Uma infraestrutura de email construída corretamente inclui vários componentes, a saber, domínios e endereços IP. Esses componentes são como o maquinário por trás dos emails enviados e, muitas vezes, são a âncora da reputação de envio. Os consultores de capacidade de entrega garantem que esses elementos sejam configurados corretamente durante a implementação, mas devido ao elemento de reputação, é importante que você tenha essa compreensão básica.

## Configuração e estratégia de domínio {#domain-setup-and-strategy}

Os tempos mudaram e alguns ISPs (como Gmail e Yahoo) agora incorporam a reputação do domínio como um ponto adicional quando se trata de anexar a reputação do email a um remetente. A reputação do seu domínio é baseada no seu domínio de envio em vez do seu endereço IP. Isso significa que sua marca tem prioridade quando se trata de decisões de filtragem de ISP.

Parte do processo de integração para novos remetentes nas plataformas Adobe inclui configurar seus domínios de envio e garantir que sua infraestrutura seja estabelecida corretamente. Você deve trabalhar com um especialista em quais domínios planeja usar a longo prazo. Estas são algumas dicas que moldam uma boa estratégia de domínio:

* Seja o mais claro e reflexivo possível sobre a marca com o domínio escolhido, para que os usuários não identifiquem incorretamente o email como spam. Alguns exemplos são newsletter.foo.com, receipts.foo.com e assim por diante.
* Você não deve usar seu domínio primário ou corporativo, pois isso pode afetar a entrega de emails de sua organização para ISPs.
* Considere usar um subdomínio do domínio pai para legitimar o domínio de envio.
* Separe os subdomínios para categorias de mensagem transacional e de marketing. Isso ajudará seu fluxo de tráfego de email de forma mais confiável à medida que os ISPs procurarem esse método de envio, que é uma prática recomendada conhecida por email e é altamente recomendada.

## Estratégia de IP {#ip-strategy}

É importante formar uma estratégia de IP bem estruturada para ajudar a estabelecer uma reputação positiva. O número de IPs e a configuração variam dependendo do modelo de negócios e das metas de marketing. Trabalhe com um especialista para desenvolver uma estratégia clara para começar do jeito certo. Considere estes itens que são importantes observar:

* **Muitos IPs** pode causar problemas de reputação, pois é uma tática comum de remetentes de spam para **snowshoes**, que é uma tática usada por remetentes de spam em que o tráfego é distribuído por vários IPs para maximizar a entrega de emails de spam. Mesmo que você não seja um remetente de spam, poderá se parecer com um se usar muitos IPs, especialmente se esses IPs não tiverem tido tráfego anterior.
* **Poucos IPs** O pode causar problemas de taxa de transferência e possivelmente problemas de reputação. A taxa de transferência varia por ISP. A quantidade e a rapidez com que um ISP está disposto a aceitar normalmente se baseiam em sua infraestrutura e nos limites de reputação de envio.
* A separação de tráfego para tipos de mensagens é fundamental. É importante, no mínimo, separar emails de marketing e transacionais em pools de IP separados.
* Dependendo de sua estratégia de email, também pode ser aconselhável separar diferentes produtos ou fluxos de marketing em diferentes pools de IP se sua reputação for drasticamente diferente. Alguns profissionais de marketing também segmentam por região. Separar o IP para tráfego com reputação mais baixa não corrigirá o problema de reputação, mas evitará problemas com seus deliveries de email de reputação &quot;boa&quot;. Afinal de contas, você não quer sacrificar seu bom público-alvo por um mais arriscado.

## Loops de comentários {#feedback-loops}

Nos bastidores, as plataformas Adobe estão processando dados sobre rejeições, reclamações, cancelamentos de assinatura e muito mais. A configuração desses loops de feedback é um aspecto importante para a capacidade de entrega. As reclamações podem prejudicar uma reputação, portanto, você deve enviar endereços de email que registram reclamações do público-alvo. É importante observar que o Gmail não fornece esses dados de volta. Os cabeçalhos de cancelamento de inscrição em lista e a filtragem de engajamento são especialmente importantes para assinantes do Gmail, que agora compõem a maioria dos bancos de dados de assinantes.

## Autenticação {#authentication}

Autenticação é o processo que os ISPs usam para validar a identidade de um remetente. Os dois protocolos de autenticação mais comuns são [!DNL Sender Policy Framework] (SPF) e [!DNL DomainKeys Identified Mail] (DKIM). Eles não estão visíveis para o usuário final, mas ajudam os ISPs a filtrar emails de remetentes verificados. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) está ganhando popularidade, embora suas políticas ainda não sejam incorporadas por todos os ISPs em seus sistemas de reputação.

### SPF

[!DNL Sender Policy Framework] O (SPF) é um método de autenticação que permite ao proprietário de um domínio especificar quais servidores de email eles usam para enviar emails desse domínio.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) é um método de autenticação usado para detectar endereços de remetente falsificados (geralmente chamado de falsificação). Se o DKIM estiver ativado, ele permitirá que o destinatário confirme se o remetente está autorizado a enviar emails desse domínio.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) é um método de autenticação que permite aos proprietários do domínio proteger seu domínio contra o uso não autorizado. O DMARC usa o SPF ou o DKIM, ou ambos, para permitir que um proprietário de domínio controle o que acontece com emails com falha de autenticação: entregues, colocados em quarentena ou rejeitados.

## Recursos específicos do produto

**Campaign**

* Saiba como delegar completamente um subdomínio ao Adobe Campaign Classic ou Standard no [nesta seção](/help/additional-resources/ac-domain-name-setup.md).
* [Painel de controle do Campaign: Delegação completa de subdomínio (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Saiba como delegar completamente um subdomínio ao Adobe Campaign Classic.*
* [Painel de controle do Campaign: Delegação completa de subdomínio (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Saiba como delegar completamente um subdomínio ao Adobe Campaign Standard.*
* Saiba mais sobre como implementar um loop de comentários para uma instância do Campaign Classic no [nesta seção](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Recursos adicionais

* Saiba mais sobre os métodos de autenticação SPF, DKIM e DMARC no [nesta seção](/help/additional-resources/authentication.md).
* Saiba mais sobre como aumentar sua reputação de email com o aquecimento de IP no [nesta seção](/help/additional-resources/increase-reputation-with-ip-warming.md).
