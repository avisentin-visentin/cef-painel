Olá Time, boa tarde!

Segue abaixo a ata da reunião **Agenda Diária — Limite de Crédito (Validação do Novo Fluxo sem PUSH)**, realizada em 11/11/2026. Agradecemos a participação de todos, especialmente à Josie pela apresentação clara da proposta e ao Fábio Grande pelos alinhamentos de dados.

📅 **11/NOVEMBRO/2026** — Horário: 14h00 – 15h00

---

**Objetivo:** Validar com a Caixa a proposta de jornada alternativa para o Caso de Uso 1 (Oferta de Crédito — Limite Disponível) sem dependência do SDK/Push, utilizando canais nativos da plataforma, e identificar as pendências de dados necessárias para viabilizar os primeiros disparos.

---

**Tópicos Discutidos**

- Josie apresentou o contexto da mudança: o SDK de push notification ainda não tem data de entrega confirmada. Para não bloquear o MVP, o fluxo foi redesenhado para usar canais nativos disponíveis (WhatsApp, SMS, E-mail e Banner/Personalization no App), iniciando pelo primeiro canal que estiver habilitado.
- A regra de entrada do CU1 não muda: cliente com limite de crédito disponibilizado D-1. A evolução para near real-time está mapeada como débito técnico pós-MVP.
- Foram apresentadas opções de jornada para cada canal: banner no app (para quem acessou o app recentemente), WhatsApp, SMS e e-mail — todos com lógica de mensagem principal + repique.
- Discutida a visão futura de roteamento inteligente por canal de preferência, usando Calculated Insights do Data Cloud para identificar o melhor canal por cliente com base em histórico de engajamento.
- Identificadas novas pendências de dados decorrentes da mudança de canal: a jornada original (Push/Personalization) não exigia e-mail nem telefone. Com os novos canais, essas fontes precisam ser confirmadas e mapeadas.
- Fábio Grande levantou incerteza sobre a fonte de telefone de contato principal (SICL ou outra) e sobre qualidade do e-mail na base (muitos endereços de domínios extintos, como oi.com.br). A Caixa já tem modelo de validação de e-mail (filtra hard bounces) que deverá ser aplicado antes da ingestão.
- Josie apresentou proposta de KPIs para a jornada: clientes habilitados, alcançados, engajados, convertidos e time-to-convert.

---

**Decisões Tomadas:**

- Jornada do CU1 será implementada sem dependência de SDK/Push — primeiro canal habilitado dispara o MVP.
- Lógica de orquestração: clientes que acessaram o app nos últimos 15 dias recebem apenas banner; demais recebem disparo por canal externo.
- Roteamento inteligente por canal de preferência (Calculated Insights) é roadmap, não MVP.
- Josie enviará documento consolidado e apresentação visual do fluxo ainda hoje.

---

**Ações Definidas:**

➡️ Ação 1: Enviar documento consolidado da jornada + apresentação visual do fluxo alternativo do CU1 para a equipe. | Responsável: Josie (Salesforce — MC). | Prazo: 11/Nov/2026. | Status: Futuro

➡️ Ação 2: Confirmar fonte de telefone de contato principal (SICL / Cicli ou EC) para uso nos canais WhatsApp e SMS — conversar com Edvaldo. | Responsável: Fábio Grande (Caixa). | Prazo: 12/Nov/2026. | Status: Futuro

➡️ Ação 3: Confirmar volumetria das tabelas complementares necessárias (além do Limite de Crédito): e-mail, telefone e demais campos exigidos pelos novos canais. | Responsável: Fábio Grande (Caixa). | Prazo: 12/Nov/2026. | Status: Futuro

➡️ Ação 4: Confirmar aplicação do modelo de qualidade de e-mail (filtro de hard bounce / domínios inválidos) antes da ingestão da base para o canal e-mail. | Responsável: Fábio Grande (Caixa). | Prazo: 12/Nov/2026. | Status: Futuro

---

Abs, Adriana Visentin
