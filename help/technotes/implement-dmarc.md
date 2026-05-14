---
title: Implementar os indicadores de marca do Gmail para identificação de mensagem (BIMI)
description: Saiba como implementar o BIMI
topics: Deliverability
role: Admin
level: Beginner
exl-id: f1c14b10-6191-4202-9825-23f948714f1e
TQID: https://experienceleague.adobe.com/gvO7rHqY-Dm6nUq9ssccY7Kt1xobV-pqLc26iITgmRA
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: e2290edd-b061-4880-9d79-dee306cf5aa9
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
  - id: f82558ea-6af5-44eb-a424-5b3389abb0a3
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 1326
ht-degree: 9%

---

# Implementar o [!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC)

O objetivo deste documento é fornecer ao leitor informações adicionais sobre o método de autenticação de email, DMARC. Ao explicar como o DMARC funciona e suas várias opções de políticas, os leitores entenderão melhor o impacto do DMARC na capacidade de entrega de email.

## O que é o DMARC? {#about}

O Domain-based Message Authentication, Reporting and Conformance é um método de autenticação de email que permite aos proprietários de domínios proteger seus domínios contra o uso não autorizado. O DMARC também fornece feedback sobre o status de autenticação do email e permite que os remetentes controlem o que acontece com os emails que falham na autenticação. Isso inclui opções para monitorar, colocar em quarentena ou rejeitar emails, dependendo de qual política do DMARC foi implementada.

O DMARC tem três opções de política:

* **Monitor (p=none):** Instrui o provedor/ISP a fazer o que normalmente faria com a mensagem.
* **Quarentena (p=quarentena):** Instrui o provedor de caixa de correio/ISP a entregar emails que não transmitem o DMARC para a pasta de spam ou lixo eletrônico do destinatário.
* **Rejeitar (p=rejeitar):** Instrui o provedor de caixa de correio/ISP a bloquear emails que não passam no DMARC, resultando em uma rejeição.

## Como funciona o DMARC? {#how}

O SPF e o DKIM são usados para associar um email a um domínio e trabalhar juntos para autenticar o email. O DMARC vai um passo além e ajuda a evitar a falsificação, combinando o Domínio verificado pelo DKIM e SPF. Para passar no DMARC, uma mensagem deve passar no SPF ou no DKIM. Se ambas as opções falharem na autenticação, o DMARC falhará e o email será entregue de acordo com a política do DMARC selecionada.

>[!NOTE]
>
>O DMARC exige alinhamento entre os endereços ‘From’ e ‘Return-Path’.

## Por que o DMARC deve ser implementado? {#why}

O DMARC é opcional e, embora não seja obrigatório, é gratuito e permite que os destinatários de email identifiquem facilmente a autenticação de emails, o que pode melhorar potencialmente a entrega. Um dos principais benefícios do DMARC é oferecer relatórios sobre quais mensagens falham no SPF e/ou no DKIM. Também dá aos remetentes um grau de controle sobre o que acontece com emails que não passam por nenhum desses métodos de autenticação. Por meio dos relatórios do DMARC, os remetentes obtêm visibilidade de quais mensagens estão falhando no DMARC, permitindo que etapas sejam executadas para atenuar mais erros.

>[!NOTE]
>
>Se você quiser implementar o BIMI, será necessária uma política de p=quarantine ou p=reject DMARC.

## Práticas recomendadas para a implementação do DMARC {#best-practice}

Como o DMARC é opcional, ele não será configurado por padrão em nenhuma plataforma do ESP. Um registro DMARC deve ser criado no DNS para o domínio funcionar. Além disso, um endereço de email de sua escolha é necessário para indicar para onde os relatórios do DMARC devem ir na organização. Como prática recomendada, é
é recomendável implantar lentamente a implementação do DMARC, escalando sua política do DMARC de p=none, para p=quarantine, para p=reject à medida que você obtém a compreensão do DMARC sobre o impacto potencial do DMARC.

1. Analise o feedback que você recebe e usa (p=none), que instrui o destinatário a não executar nenhuma ação em relação às mensagens com falha de autenticação, mas ainda enviar relatórios de email ao remetente. Além disso, revise e corrija problemas com o SPF/DKIM se as mensagens legítimas estiverem falhando na autenticação.
1. Determine se o SPF e o DKIM estão alinhados e transmitem a autenticação para todos os emails legítimos e, em seguida, mova a política para (p=quarantine), que instrui o servidor de email de recebimento a colocar em quarentena os emails que falham na autenticação (geralmente significa colocar essas mensagens na pasta de spam).
1. Ajuste a política para (p=reject). A política “Rejeitar” instrui o destinatário a bloquear completamente (rejeitar) qualquer email de um domínio que falhou na autenticação. Após habilitar essa política, somente os emails 100% autenticados pelo seu domínio serão enviados à caixa de entrada.

   >[!NOTE]
   >
   >Use essa política com cuidado e determine se ela é apropriada para sua organização.

## Relatórios do DMARC {#reporting}

O DMARC oferece a capacidade de receber relatórios sobre emails que falham no SPF/DKIM. Há dois relatórios diferentes gerados por servidores ISP como parte do processo de autenticação que os remetentes podem receber por meio das tags RUA/RUF em sua política do DMARC:

* **Relatórios de Agregação (RUA):** não contém nenhum PII (Informações de Identificação Pessoal) que seja sensível ao GDPR.
* **Relatórios Forenses (RUF):** Contém endereços de email que diferenciam o GDPR. Antes de usar o, é melhor verificar internamente como lidar com informações que precisam ser compatíveis com o GDPR.

O principal uso desses relatórios é receber uma visão geral dos emails que são tentados de falsificação. Esses relatórios são altamente técnicos e são melhor analisados por meio de uma ferramenta de terceiros. Algumas empresas especializadas em monitoramento do DMARC são:

* [ValiMail](https://www.valimail.com/products/#automated-delivery)
* [Agari](https://www.agari.com/)
* [Demarciano](https://dmarcian.com/)
* [Proofpoint](https://www.proofpoint.com/us)

>[!CAUTION]
>
>Se os endereços de email que você está adicionando para receber relatórios estiverem fora do domínio para o qual o registro DMARC é criado, será necessário autorizar o domínio externo para especificar ao DNS que você possui esse domínio. Para fazer isso, siga as etapas detalhadas na [Documentação do dmarc.org](https://dmarc.org/2015/08/receiving-dmarc-reports-outside-your-domain)

### Exemplo de registro DMARC {#example}

```
v=DMARC1; p=reject; fo=1; rua=mailto:dmarc_rua@emaildefense.proofpoint.com;ruf=mailto:dmarc_ruf@emaildefense.proofpoint.co
```

## Tags do DMARC e o que elas fazem {#tags}

Os registros DMARC têm vários componentes chamados tags DMARC. Cada tag tem um valor que especifica um determinado aspecto do DMARC.

| Nome da tag | Obrigatório/Opcional | Função | Exemplo | Valor padrão |
|  ---  |  ---  |  ---  |  ---  |  ---  |
| v | Obrigatório | Esta tag DMARC especifica a versão. Há apenas uma versão a partir de agora, portanto, terá um valor fixo de v=DMARC1 | V=DMARC1 DMARC1 | DMARC1 |
| p | Obrigatório | Mostra a política do DMARC selecionada e direciona o destinatário para relatar, colocar em quarentena ou rejeitar emails que não passaram nas verificações de autenticação. | p=nenhum, colocar em quarentena ou rejeitar | - |
| fo | Opcional | Permite que o proprietário do domínio especifique opções de relatório. | 0: Gerar relatório se tudo falhar<br/>1: gerar relatório se algo falhar<br/>d: gerar relatório se o DKIM falhar<br/>s: gerar relatório se o SPF falhar | 1 (recomendado para relatórios do DMARC) |
| pct | Opcional | Informa a porcentagem de mensagens sujeitas à filtragem. | pct=20 | 100 |
| rua | Opcional (recomendado) | Identifica onde os relatórios agregados serão entregues. | `rua=mailto:aggrep@example.com` | - |
| ruf | Opcional (recomendado) | Identifica onde os relatórios forenses serão entregues. | `ruf=mailto:authfail@example.com` | - |
| sp | Opcional | Especifica a política do DMARC para subdomínios do domínio pai. | sp=reject | - |
| adkim | Opcional | Pode ser Estrito (s) ou Relaxado (r). Alinhamento simples significa que o domínio usado na assinatura do DKIM pode ser um subdomínio do endereço &quot;De&quot;. Alinhamento estrito significa que o domínio usado na assinatura do DKIM deve corresponder exatamente ao domínio usado no endereço do remetente. | adkim=r | r |
| aspf | Opcional | Pode ser Estrito (s) ou Relaxado (r). Alinhamento relaxado significa que o Domínio do ReturnPath pode ser um subdomínio do Endereço do remetente. Alinhamento estrito significa que o domínio Return-Path deve ter uma correspondência exata com o endereço From. | aspf=r | r |

## DMARC e ADOBE CAMPAIGN {#campaign}

>[!NOTE]
>
>Se sua instância do Campaign estiver hospedada no AWS, você poderá implementar o DMARC para seus subdomínios com o Painel de controle do Campaign. [Saiba como implementar o DMARC Records usando o Painel de Controle do Campaign](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/txt-records/dmarc.html).

Um motivo comum para falhas do DMARC é o alinhamento incorreto entre o endereço &quot;De&quot; e &quot;Para erros&quot; ou &quot;Caminho de retorno&quot;. Para evitar isso, ao configurar o DMARC, é recomendável verificar novamente suas configurações de endereço &quot;De&quot; e &quot;Erros para&quot; nos Modelos de entrega.

1. No Modelo de entrega, analise qual endereço está definido atualmente como seu endereço &quot;De&quot;.

   ![](../assets/dmarc1.png)

1. Aqui, selecione &quot;Properties&quot; que permitirá editar ainda mais seu template do delivery. Nessa janela, selecione SMTP e desmarque &quot;Use the default error address defined for the platform&quot; (Usar o endereço de erro padrão definido para a plataforma) se selecionado. Os templates de delivery no Adobe Campaign marcam essa caixa de seleção por padrão. O Endereço de Erro padrão pode não ser o endereço associado ao Endereço do Remetente neste modelo de entrega.

   ![](../assets/dmarc2.png)

1. Quando essa caixa estiver desmarcada, será exibido um campo de texto que permitirá inserir um Endereço de erro exclusivo que usa o mesmo domínio definido no Endereço de origem.

   ![](../assets/dmarc3.png)

Depois que essas alterações forem salvas, você poderá prosseguir com a implementação do DMARC com o alinhamento correto do domínio.

## Links úteis {#links}

* [DMARC.org](https://dmarc.org/){target="_blank"}
* [Autenticação de email M3AWG](https://www.m3aawg.org/sites/default/files/document/M3AAWG_Email_Authentication_Update-2015.pdf){target="_blank"}
