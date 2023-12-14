---
title: Orientação sobre as alterações anunciadas em [!DNL Google] e [!DNL Yahoo]
description: Orientação sobre as alterações anunciadas em [!DNL Google] e [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06T00:00:00Z
jira: KT-14320
thumbnail: KT-14320.jpeg
exl-id: 879e9124-3cfe-4d85-a7d1-64ceb914a460
source-git-commit: 16ff60cdcb1ca1558b8021d27b235b6977c2f40a
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 0%

---

# Orientação sobre as alterações anunciadas em [!DNL Google] e [!DNL Yahoo]

Em 3 de outubro, ambos [!DNL Google] e [!DNL Yahoo] anunciaram mudanças planejadas em conjunto através dos seus blogues. Essas alterações foram projetadas para manter os usuários mais seguros e fornecer uma melhor experiência de email, aplicando algumas práticas recomendadas comuns do setor como novos requisitos a partir de 1º de fevereiro de 2024.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] Notificação_](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] Aviso](/help/assets/Yahoo.png)

Os especialistas em capacidade de delivery de email do Adobe leram essas postagens de blog e toda a documentação vinculada para que você não precise fazer isso. Eis os principais argumentos.

## Então, o que são exatamente [!DNL Google] e [!DNL Yahoo] fazendo?

No mundo do email, há requisitos legais, requisitos práticos e práticas recomendadas gerais. Os requisitos legais variam muito de local para local e não fazem parte desse tópico. Em vez disso, [!DNL Google] e [!DNL Yahoo] estão adotando práticas recomendadas e transformando-as em requisitos práticos.

Nenhum dos itens [!DNL Google] e [!DNL Yahoo] Começarão a exigir em fevereiro são novos e muitas vezes são recomendações de práticas recomendadas há anos, mas a adoção tem sido lenta e desigual no setor. Isso é [!DNL Google] e [!DNL Yahoo]A maneira do de ajudar a fazer avançar esse processo de adoção dizendo: &quot;Se você quiser implantar email para nossos usuários (isso pode representar uma parte significativa de sua lista de email, em alguns casos até 70%, dependendo da região e do setor), você precisa fazer essas coisas.&quot;

## Quais são os detalhes?

Se você for um Adobe, a maioria do que eles exigem já faz parte da configuração, mas há alguns itens principais que são tecnicamente opcionais, e você desejará ter certeza de que sua organização adotou e configurou esses itens corretamente antes de fevereiro de 2024.

## DMARC:

[!DNL Google] e [!DNL Yahoo] ambos exigirão que você tenha um registro DMARC para qualquer domínio que usar para enviar emails para eles. Eles NÃO estão exigindo atualmente uma configuração p=reject ou p=quarentena, portanto, uma configuração de p=none, comumente chamada de configuração de &quot;monitoramento&quot;, é perfeitamente aceitável. Isso não alterará a maneira como seus emails são processados. Eles farão o que normalmente fariam sem o DMARC. Configurar isso é o primeiro passo para se proteger com o DMARC e, além disso, o novo benefício de ajudar você a enviar emails para o [!DNL Google] e [!DNL Yahoo] ele também pode ajudar você a ver se há problemas de autenticação em qualquer lugar no seu ecossistema de email.

As regras do DMARC não estão sendo alteradas, o que significa que, a menos que configurado para impedi-lo, um registro DMARC no domínio pai (adobe.com, por exemplo) será herdado e cobrirá qualquer subdomínio (como email.adobe.com). Você não precisa de registros DMARC diferentes para seus subdomínios, a menos que deseje ou precise adicioná-los por uma variedade de motivos comerciais.

No momento, o DMARC é totalmente compatível com o Adobe, mas não é necessário. Use qualquer verificador DMARC gratuito para ver se você tem a configuração DMARC para seus subdomínios e, se não tiver, fale com a equipe de suporte Adobe para saber como obter essa configuração.

Você também pode encontrar mais informações sobre o DMARC e como implementá-lo [aqui](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=pt-BR){target="_blank"} for Adobe Campaign or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html){target="_blank"} para Marketo Engage.

## 1-Clique (Lista) Cancelar Inscrição:

Não entre em pânico. [!DNL Google] e [!DNL Yahoo] não estão falando sobre os links de cancelamento de inscrição no corpo do email ou rodapé que podem ser clicados por um bot de segurança que está apenas fazendo o trabalho ou por acidente. O que eles significam é a funcionalidade do cabeçalho List-Unsubscribe para as versões &quot;mailto&quot; ou &quot;http/URL&quot;. Essa é a função na variável [!DNL Yahoo] e Gmail, onde os usuários podem clicar em cancelar inscrição. O Gmail solicita até mesmo que os usuários que clicarem em &quot;Denunciar spam&quot; vejam se a intenção é cancelar a inscrição, o que pode reduzir o número de reclamações recebidas (as reclamações prejudicam sua reputação), transformando-as em cancelamentos de assinatura (não prejudica sua reputação).

É importante observar que [!DNL Google] e [!DNL Yahoo] ambos se referem à opção &quot;http/URL&quot; pelo nome &quot;1-Click&quot; e isso é intencional. Tecnicamente, a opção original &quot;http/URL&quot; permitia redirecionar recipients para um site. Esse não é o foco da [!DNL Yahoo] e [!DNL Google], que fazem referência à versão atualizada [RFC8058](https://datatracker.ietf.org/doc/html/rfc8058){target="_blank"} que se concentra no processamento do cancelamento de inscrição por meio de uma solicitação POST HTTPS, em vez de um site, tornando-o &quot;1-Click&quot;.

Hoje, o Gmail aceita a opção de cancelamento de inscrição de &quot;mailto&quot;. O Gmail disse que o &quot;mailto&quot; não atende às suas expectativas a partir de agora, e os remetentes precisarão ter a opção &quot;post&quot; list-unsubscribe habilitada. Os remetentes que já tiverem o list-unsubscribe de algum tipo em vigor terão até 1º de junho de 2024 para terem o list-unsubscribe de &quot;1 clique&quot; em vigor.

[!DNL Yahoo] disse que continuarão a honrar a opção do &quot;mailto&quot;, por enquanto, mas que também exigirão o &quot;post&quot; no futuro.

A Adobe recomenda o uso das opções &quot;mailto&quot; e &quot;post/1-Click&quot; list-unsubscribe. O Adobe está trabalhando para habilitar o suporte &quot;post&quot; em todas as nossas plataformas de envio de email para ajudar nossos usuários a atender a esses requisitos, além de atualizações para contornar isso.

A necessidade de cabeçalhos de cancelamento de inscrição em lista não se aplica a emails transacionais. Observe que mensagens acionadas, como Carrinho Abandonado e comunicações semelhantes não geradas pelo assinante, são consideradas marketing por provedores de caixa de correio como [!DNL Google] e [!DNL Yahoo] e eles precisariam de list-unsubscribe.

[!DNL Google] e [!DNL Yahoo] Ambos estão cientes de que, em alguns casos, um recipient cancelará a subscrição e depois fará a subscrição novamente em uma data posterior. Embora não estejam dispostos a compartilhar o molho secreto de como eles identificam essas situações, eles estão trabalhando em métodos para evitar a penalização dos remetentes incorretamente nesses casos.

>[!INFO]
> Para obter mais informações sobre como implementar o list-unsubscribe para a sua solução, verifique:
> * [!DNL Adobe Campaign Classic]: [Recomendações técnicas](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=en#list-unsubscribe){target="_blank"}
>* [!DNL Adobe Campaign Standard]: [O que é o cabeçalho List-Unsubscribe? E como isso pode ser implementado no ACS?](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-14778.html?lang=en){target="_blank"}
>* [!DNL Adobe Journey Optimizer]: [Gerenciamento de opção de não participação de email](https://experienceleague.adobe.com/docs/journey-optimizer/using/email/email-opt-out.html?lang=en){target="_blank"}
>
> Ou entre em contato com a equipe de Suporte ao cliente do Adobe a qualquer momento.


## Processar cancelamentos de assinatura em 2 dias:

Essa tem sido uma prática recomendada há algum tempo, pois cada email implantado para alguém que cancelou a assinatura normalmente resulta em uma reclamação de spam, portanto, quanto mais cedo você parar de enviar emails, melhor. Mais uma vez, os requisitos legais podem ser muito mais longos em alguns casos, mas [!DNL Google] e [!DNL Yahoo] saberá que o usuário cancelou a assinatura por meio do List-Unsubscribe e que você ainda está enviando emails para ele no dia 3, e afirmaram que não permitirão que os remetentes que fizerem isso continuem enviando emails para QUALQUER um de seus usuários.

Esse requisito de 2 dias é para qualquer cancelamento de inscrição por meio dos vários métodos list-unsubscribe. Em alguns casos (como &quot;mailto&quot;), isso significa que o Adobe os processará. O Adobe processa todas as solicitações de cancelamento de inscrição imediatamente após o recebimento da solicitação, dentro do limite de 2 dias. Em outros casos, você pode processá-los. Se você estiver processando essas solicitações, talvez precise fazer alterações no seu calendário para cumprir esse prazo de 2 dias.

## Taxas de reclamação:

Manter as taxas de reclamação baixas abaixo de 0,2% tem sido uma prática recomendada há muito tempo. [!DNL Google] a fixação do limite superior em 0,3% durante um longo período de tempo, mas declarou claramente que há vantagens em mantê-lo abaixo de 0,1%. Aqui estão os detalhes que eles compartilharam:

* Seu objetivo é manter a taxa de spam abaixo de 0,10%.
* Evite uma taxa de spam de 0,30% ou superior, especialmente por qualquer período de tempo prolongado.
* Manter uma baixa taxa de spam torna os remetentes mais resilientes a picos ocasionais no feedback dos usuários.
* Da mesma forma, manter uma alta taxa de spam resultará em uma classificação de spam maior. Pode levar tempo para que as melhorias na taxa de spam reflitam positivamente sobre a classificação de spam.

[!DNL Yahoo] que o seu limiar de reclamação também se situará no intervalo de 0,30%.

[!DNL Google] e [!DNL Yahoo]O objetivo do não é punir os remetentes por um único dia ruim ou por um erro que cause um pico temporário nas reclamações. Em vez disso, eles estão se concentrando nos remetentes que têm altas taxas de reclamação por um período de tempo estendido ou um padrão de comportamento de envio incorreto.

Se você precisar de assistência para monitorar suas taxas de reclamação ou se quiser ajuda com estratégias para reduzir reclamações, entre em contato com o consultor de capacidade de entrega do Adobe ou fale com a equipe de conta sobre como adicionar um consultor de capacidade de entrega, caso ainda não tenha um.

## Como isso vai me afetar como profissional de marketing?

O não cumprimento desses novos requisitos por parte do Gmail e do [!DNL Yahoo] espera-se que resulte no envio de emails para a pasta de spam ou no bloqueio (ou seja, um retorno do MBP indicando que o email não foi entregue).

Dessa forma, a Adobe recomenda que você verifique as alterações descritas acima e garanta que comece a cumpri-las o mais rápido possível. Agora também é um ótimo momento para começar a fazer o benchmark de seu desempenho em [!DNL Yahoo] e [!DNL Google] para permitir que você veja se há alguma alteração material em suas métricas, veja em fevereiro.

Estamos aqui para ajudar. Se tiver dúvidas ou precisar de suporte, entre em contato com seu consultor de capacidade de entrega do Adobe ou fale com a equipe de conta sobre como adicionar um consultor de capacidade de entrega, caso ainda não tenha um.

## Existem maneiras de contornar isso?

Embora essa seja sempre uma questão que surge, a realidade é que essas alterações fazem sentido para os usuários finais do [!DNL Google] e [!DNL Yahoo]Plataformas do. Elas são motivadas pelas expectativas desses usuários para aplicar essas regras. Não recomendamos tentar contornar nenhuma dessas alterações, mas dar um passo para trás e pensar em como acomodar essas alterações.

## Nota final:

Isso não se aplica atualmente a emails enviados para o [!DNL Yahoo].JP ou [!DNL Gmail] contas do Workspace, aplica-se a emails provenientes desses locais.

## Recursos adicionais (não específicos a essas alterações):

[Diretrizes do remetente do Google](https://support.google.com/mail/answer/81126){target="_blank"}

[Perguntas frequentes sobre o Google](https://support.google.com/a/answer/14229414?sjid=2864589551334481470-NC){target="_blank"}

[Diretrizes do remetente do Yahoo](https://senders.yahooinc.com/best-practices/){target="_blank"}

[Perguntas frequentes sobre o Yahoo](https://senders.yahooinc.com/faqs/){target="_blank"}
