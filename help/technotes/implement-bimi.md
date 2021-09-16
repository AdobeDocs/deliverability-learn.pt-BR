---
title: Implementar os indicadores de marca do Gmail para identificação de mensagem (BIMI)
description: Saiba como implementar o BIMI
topics: Deliverability
hide: true
hidefromtoc: true
source-git-commit: ab1595bac7ef136eb001609b9017950a2d01cbb4
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---


# Implementar os indicadores de marca do Gmail para identificação de mensagem (BIMI)

O Gmail anunciou recentemente que seria [o suporte geral do BIMI](https://cloud.google.com/blog/products/identity-security/bringing-bimi-to-gmail-in-google-workspace). Há vários itens com os quais você terá que lidar antes de aproveitar esse processo, incluindo: Certificados de marca verificados, logotipos marcados, logotipos corretamente formatados, configuração DMARC e, finalmente, publicação de um registro BIMI em seu DNS. Vamos analisar todas essas etapas neste artigo.

Indicadores de marca para identificação de mensagem (BIMI) é um padrão do setor que permite que um logotipo aprovado apareça ao lado do email de um remetente nas plataformas participantes. Além de impulsionar o engajamento, essa ação ofuscante também ajuda a confirmar a autenticidade do remetente, reduzindo o risco de phishing e outras táticas de spam.

## Certificado de Marca Verificado

Um dos principais componentes do programa Gmail&#39;s BIMI é o requisito de os remetentes terem um Certificado de Marca Verificada (VMC) emitido por uma autoridade de certificação válida. Atualmente, esses VMCs estão disponíveis apenas na Entrust e na DigiCert, mas essa lista de provedores provavelmente aumentará após o anúncio do Gmail.

Os VMCs serão semelhantes aos certificados SSL de algumas maneiras. Você precisará de um VMC para cada logotipo que deseja exibir, portanto, caso tenha muitas marcas, planeje utilizar vários VMCs. Cada VMC pode ser válido em vários domínios, embora você obtenha um VMC de várias SAN. Portanto, se quiser que um logotipo apareça em vários domínios de envio, será necessário apenas um VMC.

## Marca comercial do logotipo

Antes de obter seu VMC, há outra etapa principal que deve ser concluída: para obter um VMC, o logotipo que você deseja que seja exibido deve ser registrado com uma das oito marcas comerciais e escritórios de patentes globais aprovados.

* United States Patent and Trademark Office (USPTO)
* Escritório Canadiano de Propriedade Intelectual
* Instituto da Propriedade Intelectual da União Europeia
* Instituto de Propriedade Intelectual do Reino Unido
* Deutsches Patent- und Markenamt
* Escritório de marcas comerciais do Japão
* Escritório espanhol de patentes e marcas registradas O.A.
* IP Austrália

Se o logotipo que você deseja exibir não estiver registrado ou não estiver registrado em uma dessas 8 organizações, será necessário trabalhar com a equipe jurídica para resolvê-lo antes de se candidatar ao VMC.

## Formato de imagem de logotipo

Este seria também um bom momento para se certificar de que o seu logotipo cumprirá os requisitos do logotipo BIMI para o formato. Ele deve estar no formato SVG e aderir ao perfil SVG Portable/Secure (SVG-P/S). As orientações sobre como fazê-lo podem ser encontradas no [BIMI Working Group](https://bimigroup.org/svg-conversion-tools-released).

## DMARC

Depois de ter o Logotipo da marca registrada corretamente formatado e o Certificado de Marca Verificado, você também precisará verificar se o DMARC está totalmente configurado em qualquer domínio de envio para o qual deseja que o BIMI funcione.

Isso inclui verificar se P= está definido como Quarentena ou Rejeitar. Se o seu DMARC utilizar P=None, não se qualificará para o BIMI. A configuração P=None é altamente recomendável para garantir que você saiba qual email está saindo de um domínio e que nada será bloqueado acidentalmente se você tiver alterado para &quot;Quarentena&quot; ou &quot;Rejeitar&quot;, considere isso como a fase de teste e coleta de informações. Terá de ir além disso para a aplicação efetiva, antes de a BIMI lhe ser disponibilizada.

## Entrada de DNS

Com tudo o resto finalmente alinhado e pronto para ir, é hora de atualizar a entrada DNS com seu BIMI.

Esta é uma entrada simples que deve ser parecida com isto:

```
default._bimi.[domain] IN TXT “v=BIMI1; l=[SVG URL] 
```

Você pode obter os detalhes sobre essa entrada e até mesmo usar um verificador BIMI gratuito no [site do grupo de trabalho BIMI](https://bimigroup.org/implementation-guide).


## Takeaways de chave

Se você for um cliente Adobe Campaign ou Marketo, o Adobe pode ajudá-lo a criar a atualização do DNS do BIMI: entre em contato com o Atendimento ao cliente do Adobe para solicitar um. O Adobe também pode ajudar na solução de problemas se o BIMI não estiver funcionando corretamente para você.

Para obter ajuda com Marcas Registradas ou Certificados de Marca Verificados, trabalhe com sua equipe jurídica e um fornecedor autorizado de VMC.

A configuração do BIMI para Gmail pode não ser um processo rápido, mas pode ter benefícios significativos tanto do ponto de vista de Marketing quanto de segurança.
