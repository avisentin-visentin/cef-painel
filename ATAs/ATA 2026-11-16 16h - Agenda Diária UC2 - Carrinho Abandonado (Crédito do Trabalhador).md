Olá Time, boa tarde!

Segue a ata da reunião de Agenda Diária UC2 — Carrinho Abandonado (Crédito do Trabalhador), realizada em 16/11/2026, agradecendo a participação de todos — em especial ao Fábio e à Tamie pelos detalhes ricos sobre a jornada e pelas bases de dados apresentadas ao vivo, que vão nos ajudar a estruturar o caso de uso com mais precisão.

**Reunião:** Agenda Diária — UC2 Carrinho Abandonado (Crédito do Trabalhador)
**Data:** 16/11/2026 | **Horário:** 16h00 – 17h02

---

**Objetivo:** Detalhar a jornada de Crédito do Trabalhador no Super App, mapear os pontos de abandono que serão tratados no UC2 de Carrinho Abandonado, alinhar dependências técnicas de tagueamento e GCP, e levantar as bases de dados de contato disponíveis para os canais de retargeting.

---

**Tópicos Discutidos**

- **Escopo do UC2 revisado e confirmado:** o produto do caso de uso é o Crédito do Trabalhador. A abordagem de capturar o cliente aprovado que não contratou foi adaptada — o resultado de avaliação de risco não estará disponível em tempo real nesta fase (dependência de MuleSoft interno). O UC2 tratará o **abandono intermediário da jornada**, com mensagem de retorno do tipo "Volte e continue sua simulação", sem personalização de oferta aprovada neste momento.

- **Mapeamento da jornada (Crédito do Trabalhador):** Tamie apresentou o fluxo via Figma. A jornada contempla: aceite de consulta DataPrev → simulação por valor de parcela ou valor total → detalhes da proposta → opção de contratar com ou sem seguro → termos de contratação → confirmação de pagamento → finalização. Em jornada feliz, o crédito é liberado entre 15 e 20 minutos; a mensagem ao cliente informa "em até 24 horas o crédito entra na conta".

- **Pontos de abandono identificados (gatilhos para retargeting):**
  - Cliente visualizou os detalhes da proposta e não avançou
  - Cliente clicou em contratar com seguro e não prosseguiu
  - Cliente chegou à tela de termos de contratação e não finalizou
  - Tamie ficou de mapear e compartilhar os detalhes das regras negociais que bloqueiam simulação ou contratação (reprovações do sistema corporativo, não visíveis no canal).

- **Tagueamento e dependência GCP:** o tagueamento do Super App é feito via Firebase e cobre telas e cliques. Algumas etapas da jornada são templates sobre telas — podem não estar tagueadas. Tamie ficará de verificar ao baixar as telas completas do Figma. Dependência crítica: a **habilitação do GCP (Google Cloud Platform)** é pré-requisito para que o tagueamento funcione como gatilho de retargeting. Fábio confirmou que Bruno Aprigio já está conduzindo o processo de habilitação com arquitetura, segurança digital e COI de Nuvem.

- **CCP como chave de identificação no Firebase:** o CCP (Chave de Contato Padrão) será utilizado como `user ID` no tagueamento — é o único identificador que permite cruzar o usuário entre sistemas. CCP ainda está em implementação no tagueamento do Super App.

- **Base de contato — SMS/Telefone:** base cadastral com múltiplos celulares por cliente. Campo prioritário: **telefone do alerta financeiro** (número cadastrado voluntariamente pelo cliente para receber alertas de depósito, Pix e WhatsApp). Será disponibilizado via Databricks. Considerado o contato mais "quente" da base.

- **Base de contato — E-mail:** sistema de scoring com múltiplos e-mails cadastrados por cliente. O sistema seleciona o e-mail de maior nota com base em critérios de qualidade: validade de domínio, sintaxe, similaridade, presença em Boa Vista e Open Finance. Fábio demonstrou o funcionamento ao vivo. Ficou de agendar reunião específica para apresentar o conceito e a estrutura dos campos dessa base ao time SF.

- **Continuidade durante férias de Tamie:** Tamie entra de férias na semana seguinte (retorna dia 8). Gabriel (Caixa) assumirá os pontos de contato com o time SF durante o período. Samuel solicitou que o catálogo/dicionário de tagueamento (eventos Firebase) seja entregue antes das férias — Fábio confirmou que está no plano de entrega de Tamie.

- **UC de Cartão de Crédito (mencionado como futuro):** Fábio mencionou brevemente o caso de uso de identificação de comportamento transacional em tempo real (ex: compra de passagem aérea identificada no cartão). Alta dependência de MuleSoft para streaming de transações — postergado para segundo momento.

---

**Decisões Tomadas:**

- Escopo do UC2 confirmado como Crédito do Trabalhador, com foco em abandono intermediário da jornada (sem personalização de oferta aprovada nesta fase).
- Mensagem de retargeting será do tipo "retorno à jornada" — sem dados de crédito aprovado.
- Três pontos de abandono definidos como gatilhos: detalhe da proposta, contratação com seguro e termos de contratação.
- GCP como dependência crítica para viabilizar tagueamento — tratamento já iniciado por Bruno Aprigio.
- Telefone do alerta financeiro eleito como campo prioritário para canal SMS.
- Gabriel (Caixa) assumirá a interface com SF durante férias de Tamie.

---

**Ações Definidas:**

➡️ **Ação 1:** Enviar prints e fluxo completo das telas da jornada de Crédito do Trabalhador (Figma), incluindo mapeamento detalhado dos pontos de abandono e regras negociais de reprovação. | **Responsável:** Tamie Silva Takeda (Caixa). | **Prazo:** 16/Nov/2026. | **Status:** Futuro

➡️ **Ação 2:** Verificar quais telas da jornada de Crédito do Trabalhador não estão tagueadas no Firebase e compartilhar o catálogo/dicionário de eventos antes das férias. | **Responsável:** Tamie Silva Takeda (Caixa). | **Prazo:** 21/Nov/2026. | **Status:** Futuro

➡️ **Ação 3:** Reorganizar o material do UC2 e fazer double check com Gabriel (substituto de Tamie) no início da próxima semana para fechar a proposta do caso de uso. | **Responsável:** Karina Curvina (Salesforce). | **Prazo:** 23/Nov/2026. | **Status:** Futuro

➡️ **Ação 4:** Agendar reunião específica para apresentar ao time SF o conceito e estrutura dos campos da base de scoring de e-mail. | **Responsável:** Fábio Netto Pinheiro Grande (Caixa). | **Prazo:** 23/Nov/2026. | **Status:** Futuro

---

Abs, Adriana Visentin
