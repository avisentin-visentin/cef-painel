Olá Time, boa tarde!

Segue abaixo a ata da nossa sessão de exploração técnica do CCP realizada hoje com o time da Caixa. Agradecemos a disponibilidade do Fabio Netto e do Emerson, que nos trouxeram uma visão detalhada e muito clara da arquitetura — foi uma conversa bastante produtiva que nos ajuda a avançar com segurança na estratégia de identidade do projeto.

**Reunião:** Salesforce – Exploração do CCP
**Data:** 17/11/2026 | **Horário:** 14h04 – 14h34

---

**Objetivo:** Entender a estrutura técnica do CCP (Código Cliente Personalização), seu fluxo de geração e integração com o Super App, e alinhar como esse identificador será utilizado na integração com o Data Cloud e o Marketing Cloud Personalization.

---

**Tópicos Discutidos**

- Origem e estrutura do CCP: identificador único de 23 caracteres gerado a partir da ingestão diária de CPFs/CNPJs da Receita Federal no Databricks, transformado em CCP para uso na API e armazenado em cache Redis para acesso rápido no login do usuário.
- Tabela De-Para (tabela mestre): contém todos os CPFs/CNPJs da receita, independentemente de serem clientes Caixa, e é essencial para identificar usuários em jornadas digitais antes de constarem na tabela de clientes ativa (atualização D+1).
- Importância para o caso de uso de Onboarding (UC3): um usuário abrindo conta já possui CCP na camada do app, mas ainda não aparece na tabela de clientes — sem a tabela De-Para, esse novo cliente seria descartado no primeiro acesso.
- Fluxo de integração no Super App: a API do CCP está integrada ao Pagamento (Super App) e em fase final de testes. A mudança prevista é passar a enviar o CCP como user ID para o Firebase, substituindo o CPF hasheado utilizado até então.
- Estratégia de resolução de identidade no Data Cloud: como fontes distintas usarão CCP (Databricks/app) e CPF (sistemas legados), o Data Cloud utilizará dois identity types para fazer o merge de perfis e evitar duplicidades na transição.
- Dados históricos: a decisão foi desconsiderar dados pré-virada (user ID em formato antigo) e iniciar a base de comportamento do zero a partir da data de virada do CCP no app.
- Pontos em aberto: prazo exato da virada ainda indefinido (aguardando resolução de inconsistências pontuais na base); outras fontes de dados para o Data Cloud precisam ser mapeadas quanto ao tipo de chave utilizada (CCP vs. CPF/CNPJ).

---

**Decisões Tomadas:**

- A Caixa disponibilizará a tabela De-Para já com o CCP formatado (23 caracteres), eliminando a necessidade de codificação/decodificação pelo lado Salesforce.
- A Salesforce adotará dois identity types no Data Cloud (CCP + CPF) para garantir a resolução de identidade sem duplicidades durante a transição.
- Dados históricos com user ID em formato pré-CCP serão desconsiderados; a base de comportamento iniciará do zero com a virada no app.
- O MuleSoft/Personalization (SF) está pronto para receber eventos com user ID = CCP, aguardando apenas a virada no Super App.

---

**Ações Definidas:**

➡️ **Ação 1:** Disponibilizar a tabela De-Para com o campo CCP formatado (23 chars) para consumo pela Salesforce. | **Responsável:** Fabio Netto Pinheiro Grande (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 2:** Concluir os testes de integração da API do CCP no Super App e confirmar a virada do user ID no Firebase para CCP. | **Responsável:** Tamie Silva Takeda (Caixa). | **Prazo:** A definir. | **Status:** Em Andamento

➡️ **Ação 3:** Mapear todos os pontos de contato e fontes de dados do projeto que utilizam CCP versus CPF/CNPJ, para garantir cobertura completa na resolução de identidade do Data Cloud. | **Responsável:** Renan Polonio (Salesforce). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 4:** Definir e implementar a estratégia de dois identity types (CCP + CPF) no Data Cloud para resolução de identidade sem duplicidades. | **Responsável:** Flávia Adrieli (Salesforce). | **Prazo:** A definir. | **Status:** Futuro

---

Abs, Adriana Visentin
