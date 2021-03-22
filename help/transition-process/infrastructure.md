---
title: Infraestrutura
description: 'Saiba o que é necessário para construir corretamente uma infraestrutura de email. '
feature: Processo de transição
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 550821608eb7049f739a156536dd31b6b2faa2fa
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---


# Infraestrutura

A capacidade de delivery bem-sucedida depende de uma base sólida. A infraestrutura de email é um elemento principal. Uma infraestrutura de email construída corretamente inclui vários componentes, ou seja, domínios e endereços IP. Esses componentes são como a maquinaria por trás dos emails enviados e geralmente são a âncora do envio da reputação. Os consultores de deliverability garantem que esses elementos sejam configurados corretamente durante a implementação, mas devido ao elemento de reputação, é importante que você tenha essa compreensão básica.

## Configuração e estratégia de domínio {#domain-setup-and-strategy}

Os tempos mudaram e alguns ISPs (como Gmail e Yahoo) agora incorporam a reputação do domínio como um ponto adicional quando se trata de anexar a reputação do email a um remetente. A reputação do seu domínio baseia-se no seu domínio de envio em vez do seu endereço IP. Isso significa que sua marca tem precedência quando se trata de decisões de filtragem ISP.

Parte do processo de integração de novos remetentes em plataformas de Adobe incluem a configuração de seus domínios de envio e a garantia de que sua infraestrutura seja estabelecida corretamente. Você deve trabalhar com um especialista em quais domínios planeja usar a longo prazo. Estas são algumas dicas que moldam uma boa estratégia de domínio:

* Seja o mais claro e reflexo possível da marca com o domínio escolhido para que os usuários não identifiquem incorretamente o email como spam. Alguns exemplos são newsletter.foo.com, receipt.foo.com e assim por diante.
* Você não deve usar seu domínio pai ou corporativo, pois isso pode afetar o delivery de emails de sua organização para ISPs.
* Considere usar um subdomínio do domínio pai para legitimar seu domínio de envio.
* Separe os subdomínios para categorias de mensagens transacionais e de marketing. Isso ajudará seu fluxo de tráfego de email de forma mais confiável, à medida que os ISPs procurarem esse método de envio, que é uma prática recomendada de email conhecida e altamente recomendada.

## Estratégia de IP {#ip-strategy}

É importante formar uma estratégia de PI bem estruturada para ajudar a estabelecer uma reputação positiva. O número de IPs e configurações varia dependendo do modelo de negócios e das metas de marketing. Trabalhar com um especialista para desenvolver uma estratégia clara para começar corretamente. Considere esses itens que são importantes observar:

* **Muitos** IPscan acionam problemas de reputação, pois é uma tática comum de remetentes de spam a  **snowshoe**, uma tática usada por remetentes de spam, onde o tráfego é distribuído por vários IPs para maximizar a entrega de emails de spam. Mesmo que você não seja um spammer, talvez pareça um se usar muitos IPs, especialmente se esses IPs não tiverem tráfego anterior.
* **Poucos** IPscan causam problemas de taxa de transferência e possivelmente geram problemas de reputação. A taxa de transferência varia de acordo com o ISP. A velocidade e a velocidade com que um ISP está disposto a aceitar normalmente se baseia em sua infraestrutura e no envio de limites de reputação.
* Separar o tráfego para tipos de mensagens é fundamental. É importante, no mínimo, separar o marketing e o email transacional em pools de IP separados.
* Dependendo da sua estratégia de email, também pode ser aconselhável separar diferentes produtos ou fluxos de marketing em diferentes pools de IP se a sua reputação for drasticamente diferente. Alguns profissionais de marketing também segmentam por região. Separar o IP para o tráfego com uma reputação mais baixa não corrigirá o problema de reputação, mas evitará problemas com as entregas de e-mail de reputação &quot;boa&quot;. Afinal, você não quer sacrificar seu bom público por um mais arriscado.

## Loops de comentários {#feedback-loops}

Em segundo plano, as plataformas Adobe estão processando dados relacionados a devoluções, reclamações, cancelamentos de assinaturas e muito mais. A configuração desses loops de comentários é um aspecto importante para o deliverability. As reclamações podem prejudicar uma reputação, portanto, você deve enviar por email endereços que registrem reclamações do público-alvo. É importante observar que o Gmail não fornece esses dados de volta. Os cabeçalhos de cancelamento de assinatura de lista e a filtragem de envolvimento são especialmente importantes para os assinantes do Gmail, que agora compõem a maioria dos bancos de dados de assinantes.

## Autenticação {#authentication}

Autenticação é o processo que os ISPs usam para validar a identidade de um remetente. Os dois protocolos de autenticação mais comuns são [!DNL Sender Policy Framework] (SPF) e [!DNL DomainKeys Identified Mail] (DKIM). Elas não estão visíveis para o usuário final, mas ajudam os ISPs a filtrar o email de remetentes verificados. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) está ganhando popularidade, embora suas políticas ainda não sejam incorporadas por todos os ISPs em seus sistemas de reputação.

### SPF

[!DNL Sender Policy Framework] (SPF) é um método de autenticação que permite ao proprietário de um domínio especificar quais servidores de email eles usam para enviar emails desse domínio.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) é um método de autenticação usado para detectar endereços de remetente forjados (geralmente chamado de falsificação). Se o DKIM estiver ativado, ele permitirá que o destinatário confirme se o remetente está autorizado a enviar emails desse domínio.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) é um método de autenticação que permite aos proprietários de domínio proteger seu domínio de uso não autorizado. O DMARC usa SPF ou DKIM ou ambos para permitir que um proprietário de domínio controle o que acontece com emails que falham na autenticação: entregues, em quarentena ou rejeitadas.

## Recursos específicos do produto

**Campaign**

* Saiba como delegar completamente um subdomínio ao Adobe Campaign Classic ou Standard em [esta seção](/help/putting-it-in-practice/ac-domain-name-setup.md).
* [Painel de controle do Campaign: Delegação completa de subdomínio (tutorial)](https://experienceleague.corp.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *saiba como delegar totalmente um subdomínio ao Adobe Campaign Classic.*
* [Painel de controle do Campaign: Delegação completa de subdomínio (tutorial)](https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *saiba como delegar totalmente um subdomínio ao Adobe Campaign Standard.*
* Saiba mais sobre como implementar um loop de comentários para uma instância do Campaign Classic em [esta seção](/help/putting-it-in-practice/acc-technical-recommendations.md#feedback-loop-acc).

## Recursos adicionais

* Saiba mais sobre os métodos de autenticação SPF, DKIM e DMARC em [esta seção](/help/additional-resources/authentication.md).
* Saiba mais sobre como aumentar sua reputação de email com o aquecimento de IP em [this section](/help/additional-resources/increase-reputation-with-ip-warming.md).
