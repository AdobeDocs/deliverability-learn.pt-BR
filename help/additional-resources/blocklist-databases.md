---
title: Listas de buraco negro em tempo real
description: Saiba mais sobre organizações que mantêm listas de endereços IP e domínios que provavelmente serão usados por remetentes de spam.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4155b89f-a636-404c-8951-563c1b4d0289
TQID: https://experienceleague.adobe.com/dsyoiAT3fYro3L8HkRT6OuXGfBqaVOJNy-IoFXQK37I
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 423
ht-degree: 91%

---

# Listas de buraco negro em tempo real

Várias organizações mantêm bancos de dados de endereços IP e domínios que são reputados para serem usados por remetentes de spam. Consultar esses sites pode ser útil para entender por que determinadas mensagens foram rejeitadas como spam. Geralmente é possível solicitar a remoção de um endereço adicionado incorretamente a essas listas.

Esses bancos de dados são chamados de RBLs (Listas de Buraco Negro em Tempo Real) e são consultados por meio de um mecanismo DNS. Há três tipos de RBLs:

* Por endereço IP: lista endereços IP que enviam spam ou provavelmente retransmitem spam.
* Por domínio remetente: lista domínios de remetente (domínio completo do endereço de email de devolução) enviando spam ou configurado incorretamente.
* Por domínio da Web: lista os domínios (domínios de alto nível como registrados com os registradores) encontrados nas URLs dos links e imagens contidas no conteúdo de spam. Nas soluções da Adobe, o domínio a ser considerado geralmente é o endereço usado para rastreamento.

Veja a seguir uma lista das RBLs mais utilizadas. Para obter uma lista mais abrangente, consulte [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

  Consulte [https://www.spamhaus.org/](https://www.spamhaus.org/)

  O banco de dados é mais importante. Estar classificado nesta lista geralmente é uma situação grave. Se isso acontecer, você deverá agir IMEDIATAMENTE e avisar os serviços comerciais, a capacidade de entrega e o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

  Consulte [https://www.spamcop.net/](https://www.spamcop.net/)

  É um dos bancos de dados mais conhecidos. Se um dos seus endereços IP for colocado nessa lista, isso geralmente significa que os usuários do SpamCop declararam suas mensagens como spam ou que você enviou mensagens para uma armadilha SpamCop.

* **URIBL**

  Consulte [https://www.uribl.com/](https://www.uribl.com/)

  Esta lista identifica os domínios que aparecem regularmente nas mensagens declaradas como spam. Se o seu domínio aparecer nessa lista, ele poderá afetar significativamente seu deliverability. Você deve informar os serviços de capacidade de entrega e o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) imediatamente.

* **SURBL**

  Consulte [https://surbl.org/](https://surbl.org/)

  SURBL identifica os sites que aparecem regularmente como spam. Se o seu domínio aparecer nessa lista, ele poderá afetar significativamente seu deliverability. Você deve informar os serviços de capacidade de entrega e o [Atendimento ao cliente da Adobe](https://helpx.adobe.com/br/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) imediatamente.

* **iX Manitu**

  Esta é uma lista de IPs amplamente usada na Alemanha. Consulte [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/)

<!--
* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.
-->
