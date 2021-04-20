---
title: Duplicidades
description: Saiba como identificar e limitar duplicatas para melhorar a capacidade de entrega.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 59%

---


# Duplicidades {#duplicates}

Ter endereços de email duplicados pode ter várias consequências:

* A mesma mensagem é enviada mais de uma vez. Mesmo que o Adobe execute um procedimento de desduplicação por padrão antes de enviar, não há nada que impeça o envio da mesma mensagem por ações diferentes com o mesmo conteúdo quando um target é dividido.
* Solicitações de cancelamento de assinatura não respeitadas. Se um recipient cancelar a inscrição depois de receber uma mensagem, o perfil duplicado ainda será qualificado para mensagens futuras.

Além de evitar os procedimentos de aceitação, essa situação levará os usuários a considerar as mensagens como spam e a acionar um procedimento de lista de bloqueios no ISP.

Você deve agir com cautela especial ao executar operações no banco de dados:

* As importações devem ser meticulosamente configuradas, em especial ao escolher a chave de reconciliação.
* Endereços de email alterados também podem ser uma fonte de duplicidades. Em particular, dois endereços com domínios diferentes podem ser roteados para a mesma caixa de correio, por exemplo, se uma empresa mudou de nome e manteve o domínio anterior por um determinado tempo: joe.doe@amce-co.com e joe.doe@acme-rebranded.com.
* As importações automáticas, sejam de listas ou de outros bancos de dados, são elementos a serem considerados ao gerenciar perfis. O que acontece quando você exclui ou move um perfil em outra partição? Ele pode ser recriado na partição inicial por uma importação automática, por exemplo, quando um pedido de compra é feito.
* O armazenamento de perfis em pastas diferentes pode ser implementado usando exibições em vez de partições. Dessa forma, você tem certeza de que os perfis estão na mesma partição física e, ao mesmo tempo, permite que os direitos adequados sejam exibidos e gerenciados.

Há, contudo, casos em que duplicidades entre as diferentes partições são normais. Por exemplo, ao enviar para terceiros ou entidades de empresas diferentes, é lógico que a mesma pessoa seja um recipient por vários motivos. No entanto, raramente é normal encontrar duplicidades na mesma partição.

## Recursos específicos do produto

O cancelamento da duplicação de endereços protege a reputação de envio e garante um bom gerenciamento de quarentena. Saiba mais nas seguintes seções da documentação do produto:

**Adobe Campaign Classic**

* [Atividade de desduplicação](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Uso da funcionalidade de mesclagem da atividade de desduplicação](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html)

**Adobe Campaign Standard**

* [Desduplicação de dados a partir de um arquivo importado](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)