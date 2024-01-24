---
title: Campaign Classic - Recomendações técnicas
description: Descubra técnicas, configurações e ferramentas que você pode usar para melhorar a taxa de entrega com o Adobe Campaign Classic.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 39ed3773-18bf-4653-93b6-ffc64546406b
source-git-commit: 69655998dfaadd59daf0f65fe04f16f67ff955ee
workflow-type: tm+mt
source-wordcount: '1870'
ht-degree: 55%

---

# Campaign Classic - Recomendações técnicas {#technical-recommendations}

Várias técnicas, configurações e ferramentas que você pode usar para melhorar a taxa de entrega ao usar o Adobe Campaign Classic estão listadas abaixo.

## Configuração {#configuration}

### DNS reverso {#reverse-dns}

O Adobe Campaign verifica se um DNS reverso é fornecido para um endereço IP e que isso seja apontado corretamente ao IP.

Um ponto importante na configuração da rede é verificar se um DNS reverso correto está definido para cada um dos endereços IP de mensagens de saída. Isso significa que, para determinado endereço IP, há um registro de DNS reverso (registro PTR) com um DNS correspondente (registro A) fazendo looping para o endereço IP inicial.

A escolha de domínio para um DNS reverso tem impacto ao lidar com determinados ISPs. A AOL, em particular, aceita apenas loops de comentários com um endereço no mesmo domínio que o DNS reverso (consulte [Loop de comentários](#feedback-loop)).

>[!NOTE]
>
>Você pode usar [esta ferramenta externa](https://mxtoolbox.com/SuperTool.aspx) para verificar a configuração de um domínio.

### Regras MX {#mx-rules}

As regras MX (Mail eXchanger) são as regras que gerenciam a comunicação entre um servidor de envio e um servidor de recebimento.

Mais precisamente, eles são usados para controlar a velocidade na qual o MTA da Adobe Campaign (agente de transferência de mensagens) envia emails para cada domínio de email individual ou ISP (por exemplo, hotmail.com, comcast.net). Normalmente, essas regras se baseiam nos limites publicados pelos ISPs (por exemplo, não incluir mais de 20 mensagens por cada conexão SMTP).

>[!NOTE]
>
>Para obter mais informações sobre gestão MX no Adobe Campaign Classic, consulte [nesta seção](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration).

### TLS {#tls}

TLS (Transport Layer Security) é um protocolo de criptografia que pode ser usado para proteger a conexão entre dois servidores de email e proteger o conteúdo de um email de ser lido por qualquer pessoa que não seja os destinatários pretendidos.

### Domínio do remetente {#sender-domain}

Para definir o domínio usado para o comando HELO, edite o arquivo de configuração da instância (conf/config-instance.xml) e defina um atributo &quot;localDomain&quot; da seguinte maneira:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

O domínio MAIL FROM é o domínio usado nas mensagens técnicas de devolução. Esse endereço é definido no assistente de implantação ou por meio da opção NmsEmail_DefaultErrorAddr.

### Registro SPF {#dns-configuration}

Um registro SPF pode ser definido atualmente em um servidor DNS como um registro de tipo TXT (código 16) ou um registro de tipo SPF (código 99). Um registro SPF assume o formato de uma cadeia de caracteres. Por exemplo:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

O define os dois endereços IP, 12.34.56.78 e 12.34.56.79, como autorizados a enviar emails para o domínio. **~all** significa que qualquer outro endereço deve ser interpretado como SoftFail.

Recommendations para definir um registro SPF:

* Adicionar **~all** (SoftFail) ou **-all** (Falha) ao final para rejeitar todos os servidores diferentes daqueles definidos. Sem isso, os servidores poderão forjar esse domínio (com uma avaliação neutra).
* Não adicionar **ptr** (openspf.org recomenda que isso seja dispendioso e não confiável).

>[!NOTE]
>
>Saiba mais sobre SPF em [nesta seção](/help/additional-resources/authentication.md#spf).

## Autenticação

>[!NOTE]
>
>Saiba mais sobre as diferentes formas de autenticação de email no [nesta seção](/help/additional-resources/authentication.md).

### DKIM {#dkim-acc}

>[!NOTE]
>
>Para instalações hospedadas ou híbridas, se você atualizou para o [MTA aprimorado](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages), a assinatura de autenticação de email do DKIM é feita pelo MTA aprimorado para todas as mensagens em todos os domínios.

Usar [DKIM](/help/additional-resources/authentication.md#dkim) com o Adobe Campaign Classic exige o seguinte pré-requisito:

**Declaração de opção do Adobe Campaign**: no Adobe Campaign, a chave privada DKIM é baseada em um seletor DKIM e um domínio. No momento, não é possível criar várias chaves privadas para o mesmo domínio/subdomínio com seletores diferentes. Não é possível definir qual domínio/subdomínio do seletor deve ser usado para a autenticação em nenhuma plataforma ou email. A plataforma selecionará alternativamente uma das chaves privadas, o que significa que a autenticação tem uma grande chance de falha.

* Se você configurou o DomainKeys para a instância do Adobe Campaign, basta selecionar **dkim** nas [regras de gerenciamento do domínio](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules). Caso contrário, siga as mesmas etapas de configuração (chave privada/pública) do DomainKeys (que substituiu o DKIM).
* Não é necessário ativar DomainKeys e DKIM para o mesmo domínio, pois DKIM é uma versão aprimorada do DomainKeys.
* Os domínios a seguir validam atualmente o DKIM: AOL, Gmail.

## Loop de comentários {#feedback-loop-acc}

Um loop de cometários funciona declarando no nível do ISP determinado endereço de email para um intervalo de endereços IP usados para enviar mensagens. O ISP enviará para esta caixa de entrada, de maneira semelhante ao que é feito para mensagens devolvidas, essas mensagens são relatadas por recipients como spam. A plataforma deve estar configurada para bloquear futuras entregas para os usuários que reclamaram. É importante deixar de entrar em contato com eles, mesmo que não tenham usado o link de opt out adequado. Com base nessas reclamações, um ISP adicionará um endereço IP ao seu incluo na lista de bloqueios. Dependendo do ISP, uma taxa de reclamação de cerca de 1% resultará no bloqueio de um endereço IP.

No momento, um padrão está sendo projetado para definir o formato de mensagens de loop de comentários: o [ARF (Abuse Feedback Reporting Format)](https://tools.ietf.org/html/rfc6650).

A implementação de um loop de comentários para uma instância requer:

* Uma caixa de entrada dedicada à instância, que pode ser a caixa de entrada de devolução
* Endereços IP de envio dedicados à instância

A implementação de um loop de comentários simples no Adobe Campaign usa a funcionalidade de mensagem de devolução. A caixa de entrada do loop de comentários é usada como uma caixa de entrada de devolução e uma regra é definida para detectar essas mensagens. Os endereços de email dos recipients que relataram a mensagem como spam serão adicionados à lista de quarentena.

* Criar ou modificar uma regra para emails devolvidos, **Feedback_loop**, em **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** com o motivo **Recusado** e o tipo **Difícil**.
* Se uma caixa de entrada tiver sido definida especialmente para o loop de comentários, defina os parâmetros para acessá-la criando uma nova conta externa para emails devolvidos em **[!UICONTROL Administration > Platform > External accounts]**.

O mecanismo fica operacional imediatamente para processar as notificações de reclamação. Para garantir que essa regra funcione corretamente, você pode desativar temporariamente as contas para que elas não coletem essas mensagens e verificar manualmente o conteúdo da caixa de entrada do loop de comentários. No servidor, execute os seguintes comandos:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Se você for forçado a usar um único endereço de loop de comentários para várias instâncias, será necessário:

* Replicar as mensagens recebidas em quantas caixas de entrada houver instâncias,
* Selecionar cada caixa de entrada para uma única instância,
* Configure as instâncias de modo que elas só processem as mensagens que lhes dizem respeito: as informações da instância são incluídas no cabeçalho Message-ID de mensagens enviadas pelo Adobe Campaign e, portanto, também estão localizadas nas mensagens de loop de comentários. Basta especificar o parâmetro **checkInstanceName** no arquivo de configuração da instância (por padrão, a instância não é verificada e isso pode fazer com que alguns endereços sejam colocados em quarentena incorretamente):

  ```
  <serverConf>
    <inMail checkInstanceName="true"/>
  </serverConf>
  ```

O serviço de Deliverability do Adobe Campaign gerencia sua subscrição para serviços de loop de comentários para os seguintes ISPs: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe}

### Sobre o List-Unsubscribe {#about-list-unsubscribe}

Adição de um cabeçalho SMTP chamado **List-Unsubscribe** é obrigatório para garantir o gerenciamento ideal de deliverability.A partir de 1º de junho de 2024, o Yahoo e o Gmail exigirão que os remetentes cumpram o One-Click List-Unsubscribe. Para entender como configurar o One-Click List-Unsubscribe, veja abaixo.


Esse cabeçalho pode ser usado como um ícone alternativo para o ícone &quot;Denunciar como SPAM&quot;. Ele será exibido como um link de cancelamento de inscrição na interface de email.

Usar essa funcionalidade ajuda a proteger sua reputação e os comentários serão executados como um cancelamento de inscrição.

Para usar o List-Unsubscribe, você deverá inserir uma linha de comando semelhante à seguinte:

```
List-Unsubscribe: <mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe>
```

>[!CAUTION]
>
>O exemplo acima é baseado na tabela do recipient. Se a implementação do banco de dados for feita a partir de outra tabela, reescreva a linha de comando com as informações corretas.

A linha de comando a seguir pode ser usada para criar um **List-Unsubscribe** dinâmico:

```
List-Unsubscribe: <mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%>
```

O Gmail, o Outlook.com e o Microsoft Outlook são compatíveis com esse método e um botão de cancelamento de inscrição está disponível diretamente nas interfaces deles. Essa técnica reduz as taxas de reclamação.

Você pode implementar o **List-Unsubscribe** por:

* Diretamente [adicionar a linha de comando no template do delivery](#adding-a-command-line-in-a-delivery-template)
* [Criação de uma regra de tipologia](#creating-a-typology-rule)

### Adição de uma linha de comando em um template do delivery {#adding-a-command-line-in-a-delivery-template}

A linha de comando deve ser incluída na seção adicional do cabeçalho SMTP do email.

Essa adição pode ser feita em cada email ou nos templates da entrega existentes. Você também poderá criar um novo template da entrega que inclua essa funcionalidade.

* List-Unsubscribe: <mailto:unsubscribe@domain.com>
Clicar no link de cancelamento de inscrição abrirá o cliente de email padrão do usuário. Essa regra de tipologia deverá ser adicionada em uma tipologia usada para criar emails.

* List-Unsubscribe: <https://domain.com/unsubscribe.jsp>
Clicar no link de cancelamento de subscrição redireciona o usuário para o formulário de cancelamento de subscrição.
  ![imagem](https://git.corp.adobe.com/storage/user/38257/files/3b46450f-2502-48ed-87b9-f537e1850963)


### Criação de uma regra de tipologia {#creating-a-typology-rule}

A regra deverá conter o script que gera a linha de comando e deverá ser incluída no cabeçalho do email.

>[!NOTE]
>
>Recomendamos a criação de uma regra de tipologia: a funcionalidade List-Unsubscribe será adicionada automaticamente em cada email.

>[!NOTE]
>
>Saiba como criar regras de tipologia no Adobe Campaign Classic em [nesta seção](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules).

### Cancelamento de inscrição na lista com um clique

A partir de 1º de junho de 2024, o Yahoo e o Gmail exigirão que os remetentes cumpram o One-Click List-Unsubscribe. Para estar em conformidade com o requisito de Lista de um clique - Cancelar inscrição, os remetentes devem:

* Adicione em um &quot;List-Unsubscribe-Post: List-Unsubscribe=One-Click&quot;
* Incluir um link de cancelamento de inscrição de URI
* Suporte à recepção da resposta POST HTTP do receptor, compatível com Adobe Campaign.

Para configurar o One-Click List-Unsubscribe diretamente:

* Adicione no seguinte aplicativo web &quot;Unsubscribe recipients no click&quot; 
* Vá para Recursos -> Online -> Aplicativos da Web
* Carregue o XML &quot;Cancelar inscrição de destinatários sem clique&quot;
* Configurar List-Unsubscribe e List-Unsubscribe-Post
* Acesse a seção SMTP das propriedades de delivery.
* Em Additional SMTP Headers, insira nas linhas de comando (Cada cabeçalho deve estar em uma linha separada):

```
List-Unsubscribe-Post: List-Unsubscribe=One-Click
List-Unsubscribe: <https//domain.com/webApp/unsubNoClick?id=<%= recipient.cryptidcamp %>>, <mailto: %=errorAddress%?
subject=unsubscribe%=message.mimeMessageId%>
```

O exemplo acima habilitará o One-Click List-Unsubscribe para ISPs com suporte a One-Click, ao mesmo tempo em que garante que os destinatários que não oferecem suporte ao URL list-unsubscribe ainda possam solicitar um cancelamento de inscrição por email.


### Criação de uma regra de tipologia para suportar o cancelamento de inscrição em lista com um clique:

Criar a nova regra de tipologia

Na Árvore de navegação, clique em novo para criar uma nova Tipologia

![typologyrues1](help/assets/CreatingTypologyRules1.png)

Continue a configurar a regra de tipologia

* Tipo de Regra : controle
* Canal: email
* Fase: no início da personalização
* Nível: sua escolha
* Ativo

![imagem](https://git.corp.adobe.com/AdobeDocs/deliverability-learn.en/blob/main/help/assets/CreatingTypologyRules2.png)

Codifique o javascript da regra de Tipologia.

>[!NOTE]
>
>O código descrito abaixo deve ser referenciado apenas como exemplo.
>

Este exemplo detalha como:
* Configure um URL List-Unsubscribe e adicionará os cabeçalhos ou anexará os parâmetros mailto: existentes e os substituirá por: &lt;mailto..>, <http://…>
* Adicionar no cabeçalho List-Unsubscribe-Post

O exemplo de url de publicação usa var headerUnsubUrl = &quot;http;//campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;;

É possível adicionar outros parâmetros (como &amp;service = ...)

```
// Function to add or replace a header in the provided headers 
function addHeader(headers, header, value)  { 
    
  // Create the new header line 
  var headerLine = header + ": " + value; 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop through each line 
  for (var i=0; i < headerLines.length; i++) { 
      
    // Check if the specified header exists 
    var match = headerLines[i].match(regExp) 
      
    // If it exists 
    if ( match != null ) { 
        
      // Replace the existing header line 
      headerLines[i] = headerLine; 
        
      // Return the modified headers 
      return headerLines.join("\n"); 
    } 
  } 
    
  // If the header does not exist, add the new header line 
  headerLines.push(headerLine); 
    
  // Return the modified headers 
  return headerLines.join("\n"); 
} 
  
// Function to get the value of a specified header from the provided headers 
function getHeader(headers, header) { 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop each line 
  for each (line in headerLines) { 
      
    // Check if the specified header exists 
    var match = line.match(regExp); 
      
    // If it exists 
    if ( match != null ) { 
        
      // Return the header value, removing leading whitespace 
      return match[1].replace(/^\s*/, ""); 
    } 
  } 
    
  // If the header does not exist, return an empty string 
  return ""; 
} 
  
  
// Define the unsubscribe URL 
var headerUnsubUrl = "http://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"; 
  
// Get the value of the List-Unsubscribe header 
var headerUnsub = getHeader(delivery.mailParameters.headers, "List-Unsubscribe"); 
  
// If the List-Unsubscribe header does not exist 
if ( headerUnsub === "" ) { 
  // Add the List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
// If the List-Unsubscribe header exists and contains 'mailto' 
else if(headerUnsub.search('mailto')){ 
  // Replace the existing List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
  
// Get the value of the List-Unsubscribe-Post header 
var headerUnsubPost = getHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post"); 
  
// If the List-Unsubscribe-Post header does not exist 
if ( headerUnsubPost === "" ) { 
  // Add the List-Unsubscribe-Post header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post", "List-Unsubscribe=One-Click"); 
} 
  
// Return true to indicate success 
return true; 
```

![imagem](https://git.corp.adobe.com/AdobeDocs/deliverability-learn.en/blob/main/help/assets/CreatingTypologyRules3.png)

Adicione a nova regra a uma Tipologia a um email (a tipologia padrão está OK).

![imagem](https://git.corp.adobe.com/AdobeDocs/deliverability-learn.en/blob/main/help/assets/CreatingTypologyRules4.png)

Preparar um novo delivery (verifique se os cabeçalhos SMTP adicionais na propriedade de delivery estão vazios).

![imagem](https://git.corp.adobe.com/AdobeDocs/deliverability-learn.en/blob/main/help/assets/CreatingTypologyRules5.png)

Durante a preparação do delivery, verifique se a nova Regra de tipologia é aplicada.

![imagem](https://git.corp.adobe.com/AdobeDocs/deliverability-learn.en/blob/main/help/assets/CreatingTypologyRules6.png)

Validar se o List-Unsubscribe está presente.

![imagem](https://git.corp.adobe.com/AdobeDocs/deliverability-learn.en/blob/main/help/assets/CreatingTypologyRules6.png)

## Otimização de email {#email-optimization}

### SMTP {#smtp}

O SMTP (Simple Mail Transfer Protocol) é um protocolo padrão da Internet para transmissão de email.

Os erros SMTP que não são verificados por uma regra são listados na pasta **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Delivery log qualification]**. Essas mensagens de erro são interpretadas por padrão como erros de software inacessíveis.

Os erros mais comuns devem ser identificados e uma regra correspondente adicionada em **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Mail rule sets]** se você quiser qualificar corretamente o feedback dos servidores SMTP. Sem isso, a plataforma executará tentativas desnecessárias (caso de usuários desconhecidos) ou colocará alguns recipients em quarentena de forma equivocada após determinado número de testes.

### IPs dedicados {#dedicated-ips}

A Adobe fornece uma estratégia de IP dedicada para cada cliente com um IP ampliado para criar uma reputação e otimizar o desempenho de entrega.
