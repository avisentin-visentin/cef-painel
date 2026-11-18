Olá Time, bom dia!

Segue a ata da reunião de Status Report Semanal realizada em 16/11/2026, agradecendo a participação de todos — em especial ao Bruno Aprigio pelos direcionamentos estratégicos sobre conectividade e priorização dos casos de uso.

**Reunião:** PC — Projeto Caixa (Status Report Semanal)
**Data:** 16/11/2026 | **Horário:** 09h00 – 10h14

---

**Objetivo:** Apresentar o status da semana para os times Salesforce, Orange e Caixa, alinhar o novo cenário de conectividade MuleSoft, revisar a agenda da semana e definir prioridades de execução.

---

**Tópicos Discutidos**

- Apresentação do status report da semana: entrega de relatórios técnicos (SDK, canais integrados, conectividade Data Cloud e MuleSoft — pendentes de revisão), formação dos squads definida, plano de implantação agressivo para UC1 em andamento com meta de dezembro/2026.

- Kickoff dos Squads não realizado na sexta 13/11 — reagendado para terça 17/11 às 17h (proposta de Jeyson).

- Volumetria de mensageria ainda pendente: Fábio confirmou que enviará estimativa baseada em média diária de 1 mês. Alertou que a base do Super App cresce diariamente, tornando a volumetria estimada. Ponto adicional: SMS usa número do alerta financeiro do cliente — fonte separada da base de contatos CRM. Caminho sugerido por Bruno Aprigio: levar essa tabela para o Databricks.

- Novo cenário de conectividade MuleSoft apresentado por Andreas: a solução CloudHub original não foi viável por restrições técnicas de ambos os lados. Duas fases definidas: **Fase 1** (curto prazo) — conexão Cloud-to-Cloud via SAS Token Azure (Databricks → Data Cloud), sem dependência de MuleSoft/RTF, viabiliza UC1 para dezembro; **Fase 2** (solução definitiva) — MuleSoft RTF on-premise dentro da infraestrutura da Caixa, requer Kubernetes, aprovação de arquitetura e conectividade, prazo indeterminado.

- Bruno Aprigio orientou separação clara de responsabilidades: **conectividade** é com ele e o time de tecnologia da Caixa; **origem dos dados** é com Fábio Grande.

- Impacto nos casos de uso: UC1 (Crédito) mantido com Fase 1 via Databricks — foco total. UC2.1 (Carrinho Abandonado) dependente do Google/tracking — incerto. UC2.2 (Ofertas Investimento) e UC4 (FSC Private) dependentes de MuleSoft — apenas discovery no momento. UC Depósito bloqueado (fila MQ). UC3 (Onboarding) explorado como alternativa via Databricks.

- CCP (Chave de Contato): Bruno Aprigio alertou que o CCP não existe em outras bases da Caixa — não pode ser chave única de unificação de cliente, precisa ser cruzado com CPF/CNPJ. API do CCP subida e em testes. Reunião agendada para terça 17/11 às 14h para explicar o CCP ao time.

- Revisão dos riscos do projeto: Andreas apresentou atualização dos slides de risco. Bruno Aprigio solicitou separar R-01 em dois riscos distintos: R-01a (Conectividade — Bruno Aprigio/TI Caixa) e R-01b (Origem dos Dados — Fábio Grande). Risco de conectividade classificado como o mais crítico.

- Reunião executiva SF × Caixa prevista para ~3 semanas. Bruno Aprigio solicitou pauta clara (nível diretor/superintendente) antes de agendar.

- Time SF planeja visita presencial a Brasília na semana de 24–26/11. Fechar agendas até quarta-feira 18/11.

- Agenda de 10h30 de quinta 19/11: apresentação do Marketing Cloud com foco no Journey Builder (Cleiton + Renata → mesa de performance) — agenda de Customer Success, conduzida pelo time de Samuel.

---

**Decisões Tomadas:**

- Estratégia de conectividade redefinida: priorizar Fase 1 (Cloud-to-Cloud via SAS Token Azure/Databricks) para viabilizar UC1 em dezembro; MuleSoft RTF como solução definitiva de médio prazo.
- UC1 permanece como prioridade absoluta da semana. Demais casos de uso seguem em discovery, sem compromisso de entrega imediata.
- Bruno Aprigio autorizou contato direto de Bruno Aniceto (SF) para agilizar reuniões de conectividade — sem necessidade de agenda formal prévia; acionar Diego Freitas (Orange) se necessário.
- Kickoff dos Squads reagendado para terça 17/11 às 17h.
- Visita presencial a Brasília confirmada para 24–26/Nov — agendas a fechar até quarta 18/11.
- R-01 separado em R-01a (Conectividade) e R-01b (Origem dos Dados).

---

**Ações Definidas:**

➡️ **Ação 1:** Enviar estimativa de volumetria de mensageria (média diária baseada em 1 mês). | **Responsável:** Fábio Grande (Caixa). | **Prazo:** 18/Nov/2026. | **Status:** Futuro

➡️ **Ação 2:** Preparar e enviar relatórios técnicos com as opções de conectividade (Fase 1 e Fase 2) para a Caixa tomar decisão formal. | **Responsável:** Andreas Miller / Bruno Aniceto (Salesforce). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

➡️ **Ação 3:** Confirmar viabilidade de conexão Cloud-to-Cloud com Google Cloud (tracking/tagueamento) além do Azure/Databricks. | **Responsável:** Bruno Aprigio e Silva (Caixa) / Bruno Aniceto (SF). | **Prazo:** 18/Nov/2026. | **Status:** Futuro

➡️ **Ação 4:** Realizar reunião de Exploração do CCP — explicar alcance, limitações e necessidade de cruzamento de chaves. | **Responsável:** Fábio Grande (Caixa) + Samuel, Renan, Maciel (SF). | **Prazo:** 17/Nov/2026 14h. | **Status:** Futuro

➡️ **Ação 5:** Enviar invites das agendas definidas na reunião (Plano UC1, CCP, APIs, Arquitetura BU, Kickoff Squads). | **Responsável:** Adriana Visentin (Salesforce). | **Prazo:** 16/Nov/2026. | **Status:** Futuro

➡️ **Ação 6:** Atualizar documento de status com novo cenário de conectividade e redistribuir para os times. | **Responsável:** Andryelle Verissimo (Orange). | **Prazo:** 16/Nov/2026. | **Status:** Futuro

➡️ **Ação 7:** Fechar agendas da semana de Brasília (24–26/Nov) até quarta 18/Nov. | **Responsável:** Fábio Grande (Caixa) / Adriana Visentin (SF). | **Prazo:** 18/Nov/2026. | **Status:** Futuro

➡️ **Ação 8:** Atualizar painel de riscos — separar R-01 em R-01a (Conectividade) e R-01b (Origem dos Dados). | **Responsável:** Adriana Visentin (Salesforce). | **Prazo:** 16/Nov/2026. | **Status:** Concluído

---

Abs, Adriana Visentin
