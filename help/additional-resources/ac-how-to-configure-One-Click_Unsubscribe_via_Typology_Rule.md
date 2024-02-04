---
source-git-commit: 0332be5688f9d0375d1dba97c39a87d0e8d28c52
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 8%

---
# Criação de uma regra de tipologia para suportar o cancelamento de inscrição em lista com um clique:

**1. Crie a nova Regra de tipologia:**
* Na Árvore de navegação, clique em &quot;novo&quot; para criar uma nova Tipologia

![imagem](/help/assets/CreatingTypologyRules1.png)

**2. Continue a configurar a regra de tipologia:**
* Tipo de regra: controle
* Fase: no início do direcionamento
* Canal: Email
* Nível: sua escolha
* Ativo


![imagem](/help/assets/CreatingTypologyRules2.png)


**Codifique o javascript da regra de Tipologia:**


>[!NOTE]
>
>O código descrito abaixo deve ser referenciado apenas como exemplo.
>Este exemplo detalha como:
>* Configure um URL List-Unsubscribe e adicionará os cabeçalhos ou anexará os parâmetros mailto: existentes e os substituirá por: &lt;mailto..>>, https://...
>* Adicionar no cabeçalho List-Unsubscribe-Post
>O exemplo de URL de publicação usa var headerUnsubUrl = &quot;https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;
>* É possível adicionar outros parâmetros (como &amp;service = ...)
>


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
var headerUnsubUrl = "https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"; 
  
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


![imagem](/help/assets/CreatingTypologyRules3.png)

**3. Adicionar sua nova regra a uma tipologia a um email (a tipologia padrão é ok):**

![imagem](/help/assets/CreatingTypologyRules4.png)

**4. Preparar um novo delivery (verifique se os cabeçalhos SMTP adicionais na propriedade de delivery estão vazios)**

![imagem](/help/assets/CreatingTypologyRules5.png)

**5. Durante a preparação do delivery, verifique se a nova Regra de tipologia é aplicada.**

![imagem](/help/assets/CreatingTypologyRules6.png)



**6. Validar se o List-Unsubscribe está presente.**

![imagem](/help/assets/CreatingTypologyRules7.png)
