Olá Time, bom dia!

Agradecemos a participação de todos nesta sessão de discovery voltada ao Financial Services Cloud para o segmento Private da Caixa. Foi uma conversa muito rica, conduzida pela Camila Pacheco, em que levantamos os requisitos de acesso, compartilhamento de dados e os fluxos de encarteiramento do Private — informações essenciais para o design correto da solução no FSC.

**Reunião:** Salesforce — Acessos e Encarteiramento (FSC Private)
**Data:** 17/11/2026 | **Horário:** 10h35 – 11h40

---

**Objetivo:** Levantar os requisitos de configuração de acesso e compartilhamento de dados no Financial Services Cloud para o segmento Private da Caixa, bem como entender os fluxos de encarteiramento (entrada e saída de clientes no Private) para desenho correto da solução.

---

**Tópicos Discutidos**

- Apresentação dos modelos de compartilhamento do Salesforce (Sharing Settings): Camila apresentou os três modelos — privado (acesso restrito ao owner), público somente leitura e público leitura e escrita — explicando as implicações práticas de cada um.

- Discussão sobre o modelo ideal para o Private: Lino destacou duas preocupações principais — segurança dos dados (clientes de alto patrimônio e perfil público) e risco de canibalismo por bônus atrelado à carteira. Propôs diferenciação por perfil: bankers e superintendentes com acesso amplo, assistentes restritos ao próprio escritório.

- Separação entre dados cadastrais e dados financeiros: Camila trouxe que no Salesforce esses dados ficam em objetos separados, o que permite dar acesso à visão cadastral para todos e restringir os dados financeiros ao owner da carteira. Lino considerou essa distinção estrategicamente importante.

- Grupos econômicos: Lino explicou que é um conceito exclusivo do Private, gerido pelo banker no Relacionamento.Caixa. Cada cliente é ao mínimo líder de si mesmo; grupos com múltiplos membros são criados pelo banker. Hoje os assistentes não têm acesso a grupos econômicos — identificado como dor, com intenção de resolver no FSC.

- Visualização de empresas vinculadas: o Relacionamento.Caixa já exibe as empresas das quais o cliente é sócio (inclusive empresas sem conta na Caixa, via dados da Receita Federal). Lino manifestou interesse em ter essa visão integrada no painel do FSC.

- Clientes PEP (Pessoas Politicamente Expostas): assistentes não acessam dados de clientes PEP. Bankers acessam com alerta na tela. A marca PEP vem de sistemas externos, persiste por 5 anos após o cliente deixar o cargo. Lino sinalizou que esse comportamento de restrição deve ser mantido no FSC.

- Rastreamento de acessos (Shield): Camila apresentou o Shield como solução Salesforce para auditoria de quem acessou quais registros. Não é nativo na plataforma padrão — precisa ser habilitado. Lino confirmou que não seria uso recorrente, mas é necessário como capacidade de investigação em casos de incidente.

- Dados editáveis no Relacionamento.Caixa: dados de interação, carteira, preferências pessoais e marcas do cliente. Dados cadastrais (nome, CPF, e-mail) não são editados pelo banker — têm fluxo próprio de aprovação em outros sistemas.

- Fluxos de entrada no Private: (1) onboarding padrão — cliente varejo atinge R$5M investidos, monitoramento diário, lapso temporal de 20–40 dias para evitar recursos transitórios, inserção automática nos primeiros 5 dias úteis de cada mês; (2) inclusão como membro de grupo pelo banker — CPF incluso no grupo, migração automática em 1–2 semanas; (3) segmentação estratégica — cliente prospectado diretamente pelo banker, inclusão manual pela equipe de estratégia em até 15 minutos.

- Fluxos de saída do Private: ocorrem apenas em janeiro e julho — deliberadamente semestral para evitar manipulação de resultados entre redes. Clientes que perdem o critério (saldo < R$5M, saída de grupo, etc.) são retirados na janela correspondente.

- Gestão de carteiras pelo superintendente: tem acesso para mover clientes entre carteiras de bankers dentro do escritório a qualquer momento.

- Cobertura de férias: normalmente feita pelo assistente, que tem a função alterada temporariamente no sistema para "banker", herdando os acessos correspondentes. Karina reforçou que permissões temporárias são possíveis no FSC. A funcionalidade de delegação explícita de carteira não é nativa no Salesforce — pode ser desenvolvida em entrega futura.

---

**Decisões Tomadas:**

- O comportamento de restrição de acesso a clientes PEP deve ser replicado no FSC, mantendo o mesmo padrão do Relacionamento.Caixa.

- A separação entre dados cadastrais e financeiros será adotada como princípio de design de segurança — acesso cadastral mais amplo, dados financeiros restritos ao owner da carteira.

- A funcionalidade de delegação de carteira não será priorizada no MVP — pode entrar em entrega futura, priorizando o que é nativo da plataforma.

- Agenda de continuação do discovery de Acessos/Encarteiramento mantida para quinta-feira, 19/11/2026, às 14h.

---

**Ações Definidas:**

➡️ **Ação 1:** Montar matriz de acesso (perfil × tipo de dado × visibilidade) para definição formal dos níveis de acesso no FSC e retornar à Salesforce. | **Responsável:** Lino Raphael Brancaglion Muffato (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 2:** Confirmar com área interna da Caixa como funciona o fluxo de cobertura de férias — se o assistente muda de grupo de função no sistema ao assumir a substituição. | **Responsável:** Lino Raphael Brancaglion Muffato (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 3:** Incluir habilitação do Shield como requisito funcional para rastreamento de acessos a clientes PEP e investigação de incidentes. | **Responsável:** Camila Pacheco (Salesforce). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 4:** Incluir Diego Lima de Freitas (Orange) na agenda presencial de quinta-feira, 19/11/2026, às 14h (continuação do discovery de Acessos/Encarteiramento). | **Responsável:** Adriana Corsino Visentin (Salesforce). | **Prazo:** 17/Nov/2026. | **Status:** Futuro

---

Abs, Adriana Visentin
