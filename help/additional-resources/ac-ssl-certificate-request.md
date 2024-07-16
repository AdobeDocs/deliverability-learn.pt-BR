---
title: Processo de solicitação de certificado SSL
description: Saiba como instalar certificados SSL nos subdomínios que você delegou ao Adobe.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 8a78abd3-afba-49a7-a2ae-8b2c75326749
source-git-commit: 57016f89df54d5c74755a6a108a92db45153ec18
workflow-type: tm+mt
source-wordcount: '2124'
ht-degree: 1%

---

# Processo de solicitação de certificado SSL

Depois de delegar um domínio ao Adobe para envio de email (consulte [Configuração do nome de domínio](/help/additional-resources/ac-domain-name-setup.md)), o Adobe criará e usará determinados subdomínios para funções específicas.

Por exemplo, se você delegou *email.example.com* ao Adobe para enviar emails, o Adobe criará subdomínios como o seguinte:
* *t.email.example.com* - para links de rastreamento
* *m.email.example.com* - para mirror pages
* *res.email.example.com* - para recursos hospedados (como imagens)

É recomendável **proteger esses domínios via SSL (HTTPS)**. Na verdade, os links inseguros (HTTP) são vulneráveis à interceptação e exibirão avisos em navegadores modernos.

Para instalar certificados SSL nesses subdomínios, o processo envolve a solicitação de um arquivo CSR e a compra subsequente de certificados SSL para instalação ou renovação do Adobe.

>[!CAUTION]
>
>Antes de instalar um certificado SSL, verifique se você está ciente dos pré-requisitos listados em [esta página](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=pt-BR#installing-ssl-certificate).
>
>O Adobe só suporta certificados de até 2048 bits. Os certificados de 4096 bits ainda não são compatíveis.

## Glossário

| Termo | Descrição |
|--- |--- |
| CA (Autoridade de Certificação) | Um provedor de certificados SSL que emite certificados digitais para organizações ou indivíduos após verificar sua identidade, como DigiCert, Symantec etc.<ul><li>Uma CA confiável geralmente é considerada uma CA de terceiros que emite um certificado raiz.</li><li>Se o certificado for assinado pela mesma organização/empresa que o está usando, ele será classificado como CA não confiável, mesmo quando se tratar de certificados SSL, como certificados autoassinados.</li></ul> |
| Certificado de corrente | Um certificado que inclui um certificado raiz e um ou mais certificados intermediários é chamado de certificado de cadeia (ou encadeado). |
| CSR (Solicitação de assinatura de certificado) | Um bloco de texto codificado que é fornecido a uma autoridade de certificação ao solicitar um certificado SSL. Normalmente, ela é gerada no servidor onde o certificado está instalado. |
| DER (Regras de Codificação Distintas) | Um tipo de extensão de certificado. A extensão .der é usada para certificados codificados DER binários. Esses arquivos também podem suportar a extensão .cer ou .crt. |
| Certificado EV (Extended Validation) | Um certificado EV é um novo tipo de certificado projetado para impedir ataques de phishing. Requer validação estendida de sua empresa e da pessoa que solicita o certificado. |
| Certificado de alta garantia | Os certificados de alta garantia são emitidos pela CA após verificar a propriedade do nome de domínio e o registro comercial válido. |
| CA Intermediário | Uma autoridade de certificação de certificados intermediários incluídos em um certificado de cadeia. |
| Certificado intermediário | Uma autoridade de certificação emite certificados na forma de uma estrutura em árvore. O certificado raiz é o certificado mais alto da árvore. Qualquer certificado entre seu certificado e o certificado raiz é chamado de certificado em cadeia ou intermediário. |
| Certificado de baixa garantia | Um certificado de baixa garantia, também chamado de certificado validado de domínio, inclui somente o nome do domínio no certificado (e não o nome da empresa/organização). |
| PEM (Privacy Enhanced Mail) | Um certificado com uma extensão .pem que contém dados ASCII (Base64). Esses certificados começam com uma linha &quot; - - - - - INICIAR CERTIFICADO - - - - - -&quot;. |
| Certificado raiz | Uma autoridade de certificação emite certificados na forma de uma estrutura em árvore. O certificado raiz é o certificado mais alto da árvore. |
| SAN (Nome alternativo do assunto) | Os nomes alternativos do assunto são nomes de host adicionais (sites, endereços IP, nomes comuns etc.) que devem ser assinados como parte de um único certificado SSL. |
| Certificado autoassinado | Um certificado que é assinado pela pessoa que o cria, em vez de uma autoridade de certificação confiável. Certificados autoassinados podem habilitar o mesmo nível de criptografia que um certificado assinado por uma CA, mas há duas desvantagens principais:<ul><li>A conexão de um visitante pode ser sequestrada, permitindo que um invasor visualize todos os dados enviados (anulando a finalidade de criptografar a conexão)</li><li> O certificado não pode ser revogado como um certificado confiável.</li></ul> |
| SSL (Secure Sockets Layer, Camada de soquete seguro) | A tecnologia de segurança padrão para estabelecer um link criptografado entre um servidor Web e um navegador. |
| Certificado curinga | Um certificado curinga pode proteger um número ilimitado de subdomínios de primeiro nível em um único nome de domínio, como *.adobe.com. |

## Etapas principais

1. Solicite um arquivo de Solicitação de assinatura de certificado (CSR) e forneça as informações necessárias (país, estado, cidade, nome da organização, nome da unidade organizacional etc.) para Adobe.
1. Valide o arquivo CSR gerado pelo Adobe e verifique se todas as informações fornecidas estão corretas.
1. Use os detalhes da CSR para gerar um certificado assinado por uma Autoridade de Certificação confiável<!--taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server-->.
1. Valide o certificado SSL e verifique se ele corresponde à CSR.
1. Forneça o certificado SSL ao Adobe, que o instalará.
1. Teste se o certificado SSL foi instalado com êxito para cada subdomínio seguro.
1. Monitore o período de validade do certificado SSL.
1. Atualize qualquer configuração específica no Adobe Campaign.

## Processo detalhado

### Pré-requisitos

Você deve identificar os nomes de domínio e as funções (rastreamento, mirror pages, aplicativos web, etc.) para proteger.
>[!NOTE]
>
>O Adobe pode ajudar a definir os nomes de domínio e as funções a serem envolvidas. Para obter mais informações, entre em contato com a equipe de conta da Adobe.

### Etapa 1 - Obter um arquivo CSR

Para obter um arquivo CSR (Certificate Signing Request, Solicitação de assinatura de certificado), siga as etapas abaixo.

* Se você tiver acesso ao [Painel de Controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR), siga as instruções em [esta página](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=pt-BR#subdomains-and-certificates) para gerar e baixar um arquivo CSR do Painel de Controle.

* Caso contrário, crie um tíquete de Suporte via https://adminconsole.adobe.com/ para obter um arquivo CSR do Atendimento ao cliente do Adobe para os subdomínios necessários.

Estas são algumas das práticas recomendadas a serem seguidas:

* Gerar uma solicitação por subdomínio delegado.
* É possível combinar vários subdomínios em uma única solicitação CSR, mas somente no mesmo ambiente. Por exemplo, no Campaign Classic, o servidor de marketing, o [servidor de mid-sourcing](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/mid-sourcing-server.html) e a [instância de execução](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/configure-transactional-messaging/configuring-instances.html#execution-instance) são três ambientes separados.
* Você deve obter uma nova CSR antes de qualquer renovação do certificado SSL. Não use um arquivo CSR antigo de um ano atrás ou mais.

Você precisará fornecer as seguintes informações.

>[!CAUTION]
>
>Todos os campos indicados nas tabelas abaixo devem ser preenchidos. Caso contrário, a solicitação CSR não poderá ser processada.

**Informações a serem fornecidas com a assistência da equipe do Adobe:**

| Informações a fornecer | Exemplo de valor | Observação |
|--- |--- |--- |
| Nome do cliente | Minha empresa Inc. | Nome da sua organização. Esse campo é usado pelo Adobe para rastrear sua solicitação (não fará parte do certificado CSR/SSL). |
| URL de ambiente do Adobe Campaign | https://client-mid-prod1.campaign.adobe.com | URL da instância do Adobe Campaign. |
| Nome Comum [CN] | t.subdomain.customer.com | Pode ser qualquer um dos domínios relevantes, mas geralmente o domínio de rastreamento. |
| Nome Alternativo da Entidade [SAN] | t.subdomain.customer.com | Certifique-se de incluir o subdomínio de rastreamento como uma SAN. |
| Nome Alternativo da Entidade [SAN] | m.subdomain.customer.com |
| Nome Alternativo da Entidade [SAN] | res.subdomain.customer.com |

**Informações a serem fornecidas pela equipe interna de TI/SSL:**

| Informações a fornecer | Exemplo de valor | Observação |
|--- |--- |--- |
| País [C] | EUA | Deve ser um código de duas letras. Acesse a lista completa de países [aqui](https://www.ssl.com/csrs/country_codes/).</br>*Observação: para o Reino Unido, use GB (não Reino Unido).* |
| Estado (ou Província) [ST] | Illinois | Se aplicável. O valor deve ser um nome completo, não abreviado. |
| Nome da Cidade/Localidade [L] | Chicago |
| Nome da Organização [O] | ACME |
| Nome da Unidade Organizacional [UO] | IT |

>[!NOTE]
>
>Substitua &quot;subdomain.customer.com&quot; pelo subdomínio delegado e os outros valores de exemplo pelos valores apropriados.

### Etapa 2 - Validar o arquivo CSR

Após enviar sua solicitação com as informações relevantes, o Adobe gera e fornece um arquivo de Solicitação de assinatura de certificado (CSR).

O texto no arquivo CSR resultante deve começar com **&quot;—INICIAR SOLICITAÇÃO DE CERTIFICADO—&quot;**.

Depois de receber o arquivo CSR do Adobe, siga as etapas abaixo:

1. Copie e cole o texto do arquivo CSR em um decodificador online, como https://www.sslshopper.com/csr-decoder.html, <!--https://www.certlogik.com/decoder/,--> ou https://www.entrust.net/ssl-technical/csr-viewer.cfm.
Como alternativa, você pode usar o comando *OpenSSL* localmente em um computador Linux.
1. Verifique se todas as verificações foram bem-sucedidas.
1. Verifique se os parâmetros e nomes de domínio corretos foram incluídos.
1. Verifique se todos os outros dados correspondem aos detalhes fornecidos ao enviar sua solicitação.

### Etapa 3 - Gerar o certificado SSL

Após fornecer o arquivo CSR, você deve comprar e gerar um certificado SSL para os domínios apropriados usando o arquivo CSR.

* O certificado SSL:
   * deve estar no formato Apache PEM;
   * não deve ter mais de 2048 bits;
   * deve ser assinado por uma autoridade de certificação (autoridade de certificação) válida;
   * deve incluir todas as SANs (Subject Alternative Names, Nomes alternativos da entidade), conforme mencionado no arquivo CSR.
* Se houver um ou mais certificados intermediários, você deverá fornecer o certificado raiz e todos os certificados intermediários ao Adobe.
* Você pode definir qualquer período de validade do certificado, mas o Adobe recomenda escolhê-lo por tempo suficiente (dois anos, por exemplo).

>[!NOTE]
>
>Se você estiver usando suas próprias ferramentas internas ou um portal fornecido por uma CA para solicitar o certificado, certifique-se de usar os mesmos detalhes fornecidos na solicitação CSR para evitar atrasos ou discrepâncias no processo de geração do certificado.

### Etapa 4 - Validar o certificado SSL

Depois que o certificado SSL for gerado, você deverá validá-lo antes de enviá-lo para o Adobe. Para isso, siga as etapas abaixo:

1. Verifique se o certificado tem a extensão .pem. Se esse não for o caso, converta-o para o formato PEM. Você pode fazer a conversão usando o *OpenSSL*.
1. Confirme se o certificado começa com **&quot;—INICIAR CERTIFICADO—&quot;**.
1. Copie o texto do certificado em um decodificador online, como https://www.sslshopper.com/certificate-decoder.html ou https://www.entrust.net/ssl-technical/csr-viewer.cfm.
Como alternativa, você pode usar o comando *OpenSSL* localmente em um computador Linux. Para obter mais informações, consulte [esta página externa](https://www.shellhacks.com/decode-ssl-certificate/).
1. Verifique se o certificado foi resolvido corretamente, incluindo Nome comum, SAN, Emissor e Período de validade.
1. Se a verificação do certificado SSL for bem-sucedida, verifique se o certificado corresponde à CSR usando [este site](https://www.sslshopper.com/certificate-key-matcher.html): selecione **Verificar se uma CSR e um certificado correspondem** e insira seu certificado e sua CSR nos campos correspondentes. Eles devem corresponder.

### Etapa 5 - Solicitar a instalação do certificado SSL

* Se você tiver acesso ao [Painel de Controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR), siga as instruções em [esta página](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=pt-BR#installing-ssl-certificate) para carregar o certificado para o Painel de Controle.

* Caso contrário, crie outro tíquete de suporte via https://adminconsole.adobe.com/ para solicitar ao Adobe a instalação do certificado nos servidores Adobe.

Você precisará fornecer:

* O arquivo do certificado, o certificado raiz e quaisquer certificados intermediários (anexados ao ticket), de preferência no formato Apache PEM.
* O número do tíquete de suporte anterior gerado para a CSR.
* Os mesmos dados fornecidos para o ticket CSR (incluindo Nome comum, URL da instância, Estado, Cidade/Localidade, Nome da organização, Nome da unidade da organização etc.).

### Etapa 6 - Testar a instalação do certificado SSL

Depois que o certificado SSL for instalado e confirmado pelo Atendimento ao cliente do Adobe, verifique se ele foi instalado com êxito para todos os URLs.

Execute os testes abaixo antes de fechar o tíquete de instalação do SSL. Atualize também qualquer configuração específica conforme instruído em [esta seção](#update-configuration).

Navegue até os seguintes URLs no seu navegador (substitua &quot;subdomain.customer.com&quot; pelo seu subdomínio):

* https://subdomain.customer.com/r/test (somente para subdomínios [aplicativos Web](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/about-web-applications.html?lang=pt-BR) - não se aplica a subdomínios de email)
* https://t.subdomain.customer.com/r/test
* https://m.subdomain.customer.com/r/test
* https://res.subdomain.customer.com/r/test

Um resultado bem-sucedido fornece informações do ambiente, e a barra de endereços no URL indica que a conexão é segura. Por exemplo, você pode ver a seguinte mensagem no Google Chrome:

![](../../help/assets/ssl-google-successful-result.png)

Se o certificado SSL não estiver instalado corretamente, o seguinte aviso será exibido:

![](../../help/assets/ssl-google-unsuccessful-result.png)

### Etapa 7 - Verificar o período de validade do certificado

Você pode verificar o período de validade do certificado no navegador. Por exemplo, no Google Chrome, clique em **Seguro** > **Certificado**.

É sua responsabilidade verificar o período de validade. A Adobe recomenda que você implemente um processo para monitorar a expiração do certificado. Saiba mais sobre o que acontece quando o certificado SSL expira em [este artigo](https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/).

* Crie um tíquete de suporte para solicitar um certificado atualizado pelo menos duas semanas antes da data de expiração do certificado. Não é necessário solicitar uma CSR adicional, a menos que os detalhes da CSR tenham sido alterados.

* Se você tiver acesso ao [Painel de Controle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=pt-BR) e seu ambiente estiver hospedado pelo Adobe em um ambiente AWS, poderá usar o Painel de Controle para renovar o certificado antes que ele expire. Saiba mais [nesta seção](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-ssl-certificates.html#monitoring-certificates).

### Etapa 8 - Atualizar qualquer configuração específica {#update-configuration}

Depois de ter certeza de que os certificados SSL solicitados foram instalados corretamente, você poderá atualizar todas as referências no Adobe Campaign, desde HTTP até HTTPS.

>[!NOTE]
>
>Para o Campaign Classic, as URLs a serem atualizadas estão localizadas principalmente no [Assistente de implantação](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/initial-configuration/deploying-an-instance.html#deployment-wizard) e nas [Contas externas](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/accessing-external-database/external-accounts.html) (rastreamento, mirror page e domínios de recursos públicos). Para o Campaign Standard, consulte [Configuração de marca](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/application-settings/branding.html#about-brand-identity).

Depois que as configurações forem atualizadas, novos emails serão enviados com URLs HTTPS em vez de HTTP. Para verificar se os URLs agora estão seguros, você pode executar rapidamente os seguintes testes:

* Faça upload de uma imagem do Adobe Campaign. Assim que a imagem for carregada, o URL retornado deverá ser HTTPS.
* Crie um delivery de email de teste incluindo um link de mirror page, algumas imagens, texto e um link de unsubscription. Envie o email para uma ID de email externa (como seu endereço do Gmail). Depois de recebido, abra o email e verifique se todos os links dentro dele estão abertos corretamente no formulário HTTPS (não HTTP), sem avisos ou erros de certificado SSL.

## Recursos específicos do produto

**Campaign Classic**

* [Painel de Controle: Adicionar certificados SSL (tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - Saiba como adicionar certificados SSL para proteger seus subdomínios.

**Campaign Standard**

* [Painel de Controle: Adicionar certificados SSL (tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - Saiba como adicionar certificados SSL para proteger seus subdomínios.
