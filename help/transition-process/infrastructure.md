---
title: Infraestrutura
description: Saiba o que é necessário para construir corretamente uma infraestrutura de email.
topics: Deliverability
jira: KT-7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
role: Admin, Leader
level: Beginner
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
TQID: https://experienceleague.adobe.com/FWlVtNGACEM6dKsnYQJU-z04mP902M5EXZmxxsKDyqU
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b0bb9048-d951-48d8-8232-45cf248a7e27
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
  - id: e2290edd-b061-4880-9d79-dee306cf5aa9
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 923
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

* **Muitos IPs** podem causar problemas de reputação, pois é uma tática comum de remetentes de spam para **snowshoes**, que é uma tática usada pelos remetentes de spam em que o tráfego é distribuído por muitos IPs para maximizar a entrega de emails de spam. Mesmo que você não seja um remetente de spam, poderá se parecer com um se usar muitos IPs, especialmente se esses IPs não tiverem tido nenhum tráfego anterior.
* **Poucos IPs** podem causar problemas de taxa de transferência e possivelmente acionar problemas de reputação. A taxa de transferência varia por ISP. A quantidade e a rapidez com que um ISP está disposto a aceitar normalmente se baseiam em sua infraestrutura e nos limites de reputação de envio.
* A separação de tráfego para tipos de mensagens é fundamental. É importante, no mínimo, separar emails de marketing e transacionais em pools de IP separados.
* Dependendo de sua estratégia de email, também pode ser aconselhável separar diferentes produtos ou fluxos de marketing em diferentes pools de IP se sua reputação for drasticamente diferente. Alguns profissionais de marketing também segmentam por região. Separar o IP para tráfego com reputação mais baixa não corrigirá o problema de reputação, mas evitará problemas com seus deliveries de email de reputação &quot;boa&quot;. Afinal de contas, você não quer sacrificar seu bom público-alvo por um mais arriscado.

## Loops de comentários {#feedback-loops}

Nos bastidores, as plataformas do Adobe estão processando dados sobre rejeições, reclamações, cancelamentos de assinatura e muito mais. A configuração desses loops de feedback é um aspecto importante para a capacidade de entrega. As reclamações podem prejudicar uma reputação, portanto, você deve enviar endereços de email que registram reclamações do público-alvo. É importante observar que o Gmail não fornece esses dados de volta. Os cabeçalhos de cancelamento de inscrição em lista e a filtragem de engajamento são especialmente importantes para assinantes do Gmail, que agora compõem a maioria dos bancos de dados de assinantes.

## Autenticação {#authentication}

Autenticação é o processo que os ISPs usam para validar a identidade de um remetente. Os dois protocolos de autenticação mais comuns são [!DNL Sender Policy Framework] (SPF) e [!DNL DomainKeys Identified Mail] (DKIM). Eles não estão visíveis para o usuário final, mas ajudam os ISPs a filtrar emails de remetentes verificados. [!DNL Domain-based Message Authentication Reporting and Conformance] O (DMARC) está ganhando popularidade, embora suas políticas ainda não sejam incorporadas por todos os ISPs em seus sistemas de reputação.

### SPF

O [!DNL Sender Policy Framework] (SPF) é um método de autenticação que permite ao proprietário de um domínio especificar quais servidores de email eles usam para enviar emails desse domínio.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) é um método de autenticação usado para detectar endereços de remetentes falsificados (comumente chamado de falsificação). Se o DKIM estiver ativado, ele permitirá que o destinatário confirme se o remetente está autorizado a enviar emails desse domínio.

### DMARC

O [!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) é um método de autenticação que permite aos proprietários do domínio proteger seu domínio contra o uso não autorizado. O DMARC usa o SPF ou o DKIM, ou ambos, para permitir que um proprietário de domínio controle o que acontece com emails com falha de autenticação: entregues, em quarentena ou rejeitados.

## Recursos específicos do produto

**Campaign**

* Saiba como delegar completamente um subdomínio ao Adobe Campaign Classic ou Standard nesta [seção](/help/additional-resources/ac-domain-name-setup.md).
* [Painel de Controle: Delegação total de subdomínio (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html?lang=pt-BR) - *Saiba como delegar completamente um subdomínio ao Adobe Campaign Classic.*
* [Painel de Controle: Delegação total de subdomínio (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html?lang=pt-BR) - *Saiba como delegar completamente um subdomínio ao Adobe Campaign Standard.*
* Saiba mais sobre como implementar um loop de comentários para uma instância do Campaign Classic em [esta seção](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Recursos adicionais

* Saiba mais sobre os métodos de autenticação SPF, DKIM e DMARC em [esta seção](/help/additional-resources/authentication.md).
* Saiba mais sobre como aumentar sua reputação de email com o aquecimento de IP [nesta seção](/help/additional-resources/increase-reputation-with-ip-warming.md).
