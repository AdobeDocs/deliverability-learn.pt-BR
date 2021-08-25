---
title: Autenticação
description: Saiba mais sobre os métodos de autenticação SPF, DKIM e DMARC.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 03609139-b39b-4051-bcde-9ac7c5358b87
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 57%

---

# Autenticação

## SPF {#spf}

O SPF (Sender Policy Framework) é um padrão de autenticação de email que permite ao proprietário de um domínio especificar quais servidores de email podem enviar emails em nome desse domínio. Este padrão usa o domínio no cabeçalho &quot;Return-Path&quot; do email (também conhecido como o endereço &quot;Envelope From&quot;).

>[!NOTE]
>
>Você pode usar [esta ferramenta externa](https://www.kitterman.com/spf/validate.html) para verificar um registro SPF.

O SPF é uma técnica que, até certo ponto, permite que você verifique se o nome de domínio usado em um email não foi falsificado. Quando uma mensagem é recebida de um domínio, o servidor DNS do domínio é consultado. A resposta é um registro curto (o registro SPF) que detalha quais servidores estão autorizados a enviar emails desse domínio. Partindo do princípio que somente o proprietário do domínio tem o meio de alterar esse registro, podemos considerar que essa técnica não permite que o endereço do remetente seja falsificado, pelo menos não a parte à direita do &quot;@&quot;.

Na especificação [RFC 4408 final](https://www.rfc-editor.org/info/rfc4408), dois elementos da mensagem são usados para determinar o domínio considerado como remetente: o domínio especificado pelo comando SMTP &quot;HELO&quot; (ou &quot;EHLO&quot;) e o domínio especificado pelo endereço do cabeçalho &quot;Return-Path&quot; (ou &quot;MAIL FROM&quot;), que também é o endereço de devolução. As diferentes considerações possibilitam levar em conta apenas um desses valores; recomendamos garantir que ambas as fontes especifiquem o mesmo domínio.

A verificação do SPF fornece uma avaliação da validade do domínio do remetente:

* **None**: Não foi possível executar nenhuma avaliação.
* **Neutral**: O domínio consultado não habilita a avaliação.
* **Pass**: O domínio é considerado autêntico.
* **Fail**: O domínio é falso e a mensagem deve ser rejeitada.
* **SoftFail**: O domínio provavelmente é falso, mas a mensagem não deve ser rejeitada exclusivamente com base nesse resultado.
* **TempError**: Um erro temporário interrompeu a avaliação. A mensagem pode ser rejeitada.
* **PermError**: Os registros SPF do domínio são inválidos.

Vale observar que os registros feitos no nível dos servidores DNS podem levar até 48 horas para serem levados em conta. Esse atraso depende da frequência com que os caches DNS dos servidores receptores são atualizados.

## DKIM {#dkim}

A autenticação DKIM (DomainKeys Identified Mail) é sucessora do SPF. Ela usa criptografia de chave pública que permite ao servidor de email de recebimento verificar se uma mensagem foi de fato enviada pela pessoa ou entidade pela qual alega ter sido enviada e se o conteúdo da mensagem foi alterado entre o momento em que foi originalmente enviada (e o DKIM &quot;assinado&quot;) e o momento em que foi recebida. Normalmente, esse padrão usa o domínio no cabeçalho &quot;From&quot; ou &quot;Sender&quot;.

O DKIM vem de uma combinação dos princípios de autenticação do DomainKeys, Yahoo! e Cisco Identified Internet Mail, e é usado para verificar a autenticidade do domínio emissor e garantir a integridade da mensagem.

O DKIM substituiu a autenticação **DomainKeys** .

O uso de DKIM requer alguns pré-requisitos:

* **Segurança**: A criptografia é um elemento essencial do DKIM. Para garantir o nível de segurança do DKIM, o 1024b é o tamanho de criptografia recomendado pela prática recomendada. As chaves DKIM inferiores não são consideradas válidas pela maioria dos provedores de acesso.
* **Reputação**: A reputação baseia-se no IP e/ou no domínio, mas um seletor de DKIM menos transparente também é um elemento essencial para ser levado em conta. A escolha do seletor é importante: evite manter o padrão que poderia ser usado por qualquer pessoa e, portanto, tem uma reputação fraca. Você deve implementar um seletor diferente para **comunicações de retenção versus aquisições** e para autenticação.

Saiba mais sobre os pré-requisitos de DKIM ao usar o Campaign Classic [nesta seção](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) é a forma mais recente de autenticação de email e depende da autenticação SPF e DKIM para determinar se um email é aprovado ou reprovado. O DMARC é único e poderoso de duas maneiras importantes:

* Conformidade - permite que o remetente instrua os ISPs sobre o que fazer com qualquer mensagem que não seja autenticada (por exemplo: não aceitar).
* Relatório - fornece ao remetente um relatório detalhado mostrando todas as mensagens que falharam na autenticação DMARC, juntamente com o domínio &quot;From&quot; e o endereço IP usados para cada uma. Isso permite que uma empresa identifique emails legítimos que estejam falhando na autenticação e precise de algum tipo de &quot;correção&quot; (por exemplo, adicionar endereços IP ao registro SPF), bem como as fontes e a prevalência de tentativas de phishing em seus domínios de email.

>[!NOTE]
>
>O DMARC pode se beneficiar dos relatórios gerados por [250ok](https://250ok.com/).
