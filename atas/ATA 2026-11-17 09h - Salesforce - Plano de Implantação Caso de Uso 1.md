Olá Time, bom dia!

Agradecemos a participação de todos nesta reunião em que apresentamos ao Bruno Aprioto o plano de implantação do Caso de Uso 1. Foi uma conversa muito produtiva e alinhamos pontos fundamentais sobre cronograma, bloqueios críticos e estratégia de execução para chegarmos ao Go Live ainda em dezembro.

**Reunião:** Salesforce — Plano de Implantação Caso de Uso 1
**Data:** 17/11/2026 | **Horário:** 09h35 – 10h01

---

**Objetivo:** Apresentar à Caixa o plano de implantação do Caso de Uso 1 (Oferta de Crédito / Limite de Crédito), alinhar dependências críticas, coletar feedback sobre a viabilidade do cronograma e definir os próximos passos.

---

**Tópicos Discutidos**

- Apresentação do plano de implantação: Karina Curvina apresentou o plano estruturado com canais em paralelo (e-mail, SMS e WhatsApp), de forma que, se um canal travar, os outros continuam avançando. A ideia é chegar em dezembro e habilitar pelo menos um canal para o Go Live.

- Três pontos críticos do plano: (1) a integração de dados via conexão nativa do Data Cloud com o Azure Blob Storage por SAS token; (2) a disponibilização dos dados no Blob Storage de forma estruturada; e (3) a habilitação e configuração de pelo menos um canal de comunicação.

- Discussão sobre datas e viabilidade: a Salesforce propôs Go Live interno (testes) para 10/12 e produção para ~15/12. Bruno foi honesto sobre a complexidade dos processos internos da Caixa e sinalizou que o prazo é apertado, sugerindo ~23/12 como data-limite mais realista. Ficou alinhado que o objetivo do Go Live é **estratégico** — mostrar que a jornada está no ar — mais do que gerar resultados de negócio imediatos.

- Status da autorização do SAS token: Bruno confirmou que a Segurança (reunião de 16/11) aprovou a abordagem cloud-to-cloud. O próximo bloqueio é a autorização formal para consumo do dado na internet. Bruno acionou seu superintendente e vai consultar o Eugênio sobre o prazo estimado.

- Canais de comunicação — pontos em aberto: a configuração do domínio de e-mail (delegação DNS) está pendente de alinhamento com o time Jambeiro/Caixa e leva no mínimo 2 semanas. O SMS está sendo tratado em paralelo pelo Fábio com o Jambeiro. O WhatsApp será configurado sem conexão com o Gênesis neste primeiro momento — o cliente recebe a mensagem e retorna ao aplicativo para concluir a contratação.

- Aprovação de layout das campanhas: identificado como ponto crítico que pode travar o Go Live no último momento. Bruno foi enfático — a solicitação de aprovação de layout (e-mail, SMS, WhatsApp) precisa ser feita imediatamente, sem aguardar a resolução dos bloqueios técnicos.

- Estratégia de foco e sequenciamento: Bruno propôs trabalhar de forma sequencial — primeiro desbloquear o Azure/Blob Storage, depois GCP/Firebase, depois MuleSoft — para não envolver múltiplas áreas da Caixa ao mesmo tempo e evitar sobrecarregar o Fábio, que é o principal interlocutor técnico da Caixa para o CU1.

- Atualização da apresentação para o Comitê Diretivo: Bruno solicitou que, assim que a data de Go Live estiver confirmada, a apresentação previamente elaborada seja rapidamente atualizada para submissão ao comitê. Andreas confirmou.

---

**Decisões Tomadas:**

- A data-limite de Go Live do CU1 será ajustada para ~23/12/2026, como horizonte mais realista dado o contexto atual de impedimentos.

- A estratégia de canais segue com paralelismo (e-mail, SMS e WhatsApp), sem dependência do SDK de Push neste primeiro momento.

- Foco total no Caso de Uso 1 e no desbloqueio do Azure como caminho prioritário. Casos de uso 2, 3 e 4 não devem sobrecarregar o Fábio enquanto o CU1 não estiver resolvido.

- A aprovação de layout das campanhas deve ser solicitada imediatamente, em paralelo à resolução dos bloqueios técnicos.

---

**Ações Definidas:**

➡️ **Ação 1:** Consultar Eugênio (Segurança) sobre prazo estimado para disponibilização do SAS token e informar a Salesforce via WhatsApp. | **Responsável:** Bruno Aprigio e Silva (Caixa). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

➡️ **Ação 2:** Acionar Jeyson para movimentar internamente a autorização formal para consumo do dado do Blob Storage na internet. | **Responsável:** Bruno Aprigio e Silva (Caixa). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

➡️ **Ação 3:** Revisar o plano de implantação do CU1 com novas datas (~23/12 como limite), destacar itens críticos em vermelho e enviar para Bruno ao final do dia. | **Responsável:** Karina Curvina (Salesforce). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

➡️ **Ação 4:** Enviar relatório técnico dos canais (e-mail, SMS, WhatsApp) para Bruno ao final do dia. | **Responsável:** Andreas Miller (Salesforce). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

➡️ **Ação 5:** Tratar com Fábio (Caixa) na reunião da tarde: status da aprovação de layout de e-mail, delegação de domínio DNS e andamento da conversa com Jambeiro sobre canais. | **Responsável:** Karina Curvina (Salesforce). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

➡️ **Ação 6:** Solicitar imediatamente aprovação do layout das campanhas (e-mail, SMS, WhatsApp) para o CU1 — não aguardar resolução dos bloqueios técnicos. | **Responsável:** Bruno Aprigio e Silva (Caixa) + Karina Curvina (Salesforce). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

➡️ **Ação 7:** Confirmar se a fonte dos dados dos casos de uso 2 e 3 está no Databricks como pré-requisito para decidir se avança o planejamento desses casos. | **Responsável:** Karina Curvina (Salesforce) + Fábio Grande (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 8:** Quando a data de Go Live do CU1 estiver confirmada, acionar Andreas para atualizar rapidamente a apresentação para submissão ao Comitê Diretivo. | **Responsável:** Bruno Aprigio e Silva (Caixa). | **Prazo:** A confirmar. | **Status:** Futuro

---

Abs, Adriana Visentin
