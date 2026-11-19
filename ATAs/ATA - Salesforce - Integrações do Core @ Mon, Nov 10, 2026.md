Olá Time, boa tarde!

Segue abaixo a ata da reunião **Integrações do Core — FSC Private**, realizada em 10/11/2026. Agradecemos a participação e contribuição de todos — foi uma sessão muito rica de mapeamento técnico que nos permite avançar com clareza para o MVP.

📅 **10/NOVEMBRO/2026** — Horário: 16h38 – 18h00

---

**Objetivo:** Mapear e priorizar as integrações necessárias para o Financial Services Cloud (FSC) Private, percorrendo a lista de ~30 necessidades de integração para compor a visão 360 do gerente private da Caixa. O foco foi identificar fontes de dados, decidir arquitetura (pull vs. bidirecional) e delimitar o escopo do MVP.

---

**Tópicos Discutidos**

- Apresentação da planilha de integrações elaborada por Karina Santos (SA FSC), item a item, com participação ativa de Fábio Netto (Caixa) para validação das fontes de dados e regras de negócio.
- Definição de que a fonte primária de dados para o MVP será o **Databricks** (sistema de dados da Caixa), com SICL como referência para dados cadastrais em tempo real — a decisão final será tomada com Jeyson e o time de dados.
- **Grupos Econômicos**: integração unidirecional (pull-only) a partir do relacionamento.caixa. O FSC não escreve de volta. Dúvida aberta sobre o status de membros não-private dentro de grupos de clientes private.
- **Dados Cadastrais**: campos CPF, nome, data de nascimento, sexo e pontos de contato. Identificadas duas chaves externas (CPF e CCP — nova chave em implantação). Escrita de volta ao SICL é necessária no longo prazo, mas postergada para fase pós-MVP.
- **Investimentos e Open Finance**: integrações via Open Finance Aggregator API. Previdência tem fonte separada (dado D-1) e baixa prioridade para MVP.
- **Feed de Inteligência / Recomendações**: conjunto de modelos preditivos e recomendações disponíveis no Databricks/relacionamento.caixa (propensão, perfil de risco, recomendações de produtos, etc.) — importar como "substrato de inteligência" no FSC.
- **Alertas de Transação** (grandes depósitos): integrar via fila MQ já mapeada no Caso de Uso 2, gerando alerta direto para o gerente private no momento de captação.
- **Análise de Agenda — Agente Coworker (Teams)**: conector nativo FSC com Microsoft Teams via Agentforce/Einstein Copilot para que o gerente consulte agenda e pendências diretamente no Teams. Primeira implementação para a equipe — explorar viabilidade.
- **Suitability (perfil de investidor)**: incluir via API SIGPI como campo adicional nos dados cadastrais do cliente.
- **Indicadores / Metas (Alcance)**: espelhamento consultivo apenas — dado tem delay, não pode ser base de responsabilização formal. Agendar sessão com Lino para entender escopo do Alcance no contexto private.
- **Carteiramento**: fonte Databricks; discutida dúvida sobre tratamento de clientes recém-chegados ao private (vinculação temporária ao superintendente).
- Discussão sobre necessidade de criar uma aba separada na planilha para mapear o que o FSC precisará **devolver** aos sistemas legados da Caixa (interações, atualizações cadastrais, etc.).
- Confirmação de que a **Ficha Resumo do Cliente** será composta exclusivamente com dados já disponíveis no FSC — sem novas integrações dedicadas.

---

**Decisões Tomadas:**

- Arquitetura MVP: integrações serão **unidirecionais (pull)** via MuleSoft em loop por CPF para os ~20k clientes Private. Escrita de volta postergada.
- Fonte principal: **Databricks** para MVP (confirmado por Fábio como opção de 99% de probabilidade).
- Alertas de grande depósito integrados via fila **MQ** (mesma infraestrutura do CU2).
- **Suitability** incluído no cadastral via API SIGPI.
- Conector **Outlook** (agenda/e-mail bidirecional) a implementar via conector nativo FSC, sujeito a aprovação de segurança.
- Agente **Coworker Teams** entra no roadmap; avaliação de viabilidade para MVP ou fase seguinte.
- Ficha resumo do cliente: sem novas integrações — composta com dados disponíveis.
- Nova sessão de ~30 minutos a agendar para finalizar itens restantes da lista.

---

**Ações Definidas:**

➡️ Ação 1: Enviar planilha de integrações (versão atual) para Fábio revisar pontos abertos e anotar dúvidas. | Responsável: Karina Santos (Salesforce). | Prazo: 11/Nov/2026. | Status: Futuro

➡️ Ação 2: Agendar nova sessão de ~30 minutos para finalizar itens restantes da lista de integrações (Planejamento de Visitas e demais pendentes). | Responsável: Adriana Visentin (PM) / Andryelle Verissimo (PM Orange). | Prazo: 12/Nov/2026. | Status: Futuro

➡️ Ação 3: Agendar sessão com Jeyson e time de dados para definir fonte definitiva de dados cadastrais e carteiramento (SICL direto vs. Databricks). | Responsável: Fábio Netto Pinheiro Grande (Caixa). | Prazo: A definir. | Status: Futuro

➡️ Ação 4: Levantar com Lima/Jeyson: (a) se débito automático e adesão SMS são "produtos" no FSC, (b) onde ficam dados de interesses pessoais, (c) onde ficam marcações de impedimento (bloqueio judicial, CPF irregular). | Responsável: Fábio Netto Pinheiro Grande (Caixa). | Prazo: A definir. | Status: Futuro

➡️ Ação 5: Confirmar regra de membro não-private dentro de grupo econômico de cliente private — qual status recebe no FSC? | Responsável: Fábio Netto Pinheiro Grande (Caixa) / Karina Santos. | Prazo: A definir. | Status: Futuro

➡️ Ação 6: Agendar sessão com Lino para entender o escopo de indicadores/metas do Alcance no contexto Private e viabilidade de espelhamento. | Responsável: Fábio Netto Pinheiro Grande (Caixa). | Prazo: A definir. | Status: Futuro

---

Abs, Adriana Visentin
