Olá Time, boa tarde!

Agradecemos a participação de todos nesta reunião realizada com caráter de urgência para avançarmos em um dos temas mais críticos do projeto: a definição da estratégia de conectividade entre a plataforma Salesforce e os sistemas internos da Caixa. Foi uma sessão rica, com a presença de todas as áreas técnicas envolvidas — Segurança, Redes, Arquitetura, Dados e Infraestrutura — e saímos com um caminho concreto para seguir.

**Reunião:** Salesforce — Conectividade CAIXA (Urgente)
**Data:** 16/11/2026 | **Horário:** 16h00 – 17h27

---

**Objetivo:** Reunir todas as áreas técnicas da Caixa para discutir e definir a estratégia de conectividade entre a plataforma Salesforce (SaaS) e os sistemas internos da instituição, viabilizando a entrada em produção dos casos de uso prioritários até dezembro/2026.

---

**Tópicos Discutidos**

- Contextualização do problema: desde a assinatura do contrato em setembro/2026, a equipe busca resolver como conectar a plataforma Salesforce (SaaS) à infraestrutura interna da Caixa. Bruno Aprioto apresentou o histórico das tentativas e os bloqueios encontrados até o momento.

- Apresentação da arquitetura de integração: Bruno Aniceto (Salesforce/MuleSoft) apresentou o mapeamento dos sistemas da Caixa que precisam ser conectados às nuvens da Salesforce (Marketing Cloud, Data Cloud, Financial Services Cloud), incluindo IBM MQ, Azure Blob Storage, Databricks/GCP, APIs agregadoras, SuperApp e sistemas internos como CCL e Relacionamento Caixa.

- Modelos de implantação do MuleSoft: foram detalhados os dois modelos disponíveis — CloudHub (totalmente em nuvem, gerenciado pela Salesforce) e Runtime Fabric/RTF (híbrido, com o motor de execução rodando em Kubernetes gerenciado pelo cliente).

- Bloqueio no modelo CloudHub — range de IP: a equipe de Redes (Luiz Gilmar / Persiane) confirmou que a Caixa não pode alocar range de IP de intranet para ambientes externos. O modelo de extensão de rede corporativa para terceiros não é aceito pela arquitetura interna, e tamanhos de range /28 ou /29 também não são viáveis para iniciar a plataforma.

- Bloqueio no modelo CloudHub — acesso a banco de dados: a Caixa não permite que entidades externas acessem diretamente bancos de dados internos, independentemente do modelo de conectividade (VPN, Transit Gateway ou Direct Connect). Isso é uma restrição arquitetural e de segurança — resolver apenas o problema de NAT não endereça esse ponto.

- O que é viável no modelo cloud: ficou confirmado que integrações com filas IBM MQ, APIs expostas, Open Finance e Azure Blob Storage via SAS token são viáveis sem exigir a instalação do MuleSoft on-premises.

- Runtime Fabric (RTF) como solução estrutural: discutiu-se a instalação do MuleSoft dentro da infraestrutura da Caixa via Kubernetes (modelo híbrido), o que permite acessar bancos de dados internos e sistemas sensíveis sem expor a rede. O modelo funciona de forma similar ao Power BI Gateway já utilizado internamente.

- Estado da infraestrutura Kubernetes da Caixa: a Caixa trabalha atualmente com OKD (OpenShift Community), que apresenta limitações de rede para esse cenário. O OpenShift Enterprise ainda está em implantação. O ARO (Azure Red Hat OpenShift) foi identificado como o caminho mais rápido para provisionar o ambiente necessário, por permitir isolamento de rede com maior flexibilidade.

- Estratégia cloud-to-cloud como solução paliativa imediata: para o Caso de Uso 1, foi validada a leitura de arquivos batch do Azure Blob Storage diretamente pelo Data Cloud via SAS token — sem necessidade de MuleSoft. Eugênio (Segurança) confirmou que essa prática já é comum na Caixa e está dentro dos padrões aceitos.

---

**Decisões Tomadas:**

- O caminho de curto prazo para viabilizar o Caso de Uso 1 até dezembro/2026 será a integração cloud-to-cloud via Data Cloud ↔ Azure Blob Storage com SAS token, sem MuleSoft.

- Para os casos de uso que exigem integração com IBM MQ, APIs internas e banco de dados, a solução estrutural será o MuleSoft via Runtime Fabric (RTF) em cluster Kubernetes, preferencialmente via ARO.

- O processo formal será iniciado com a abertura de uma demanda de Arquitetura de Referência, paralelamente à busca de excepcionalização junto à área de Operações, dado o caráter urgente do projeto.

---

**Ações Definidas:**

➡️ **Ação 1:** Identificar o dono do Blob Storage (possivelmente área Gegod) e obter autorização formal para exposição do storage e geração do SAS token. | **Responsável:** Bruno Aprioto (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 2:** Enviar e-mail formal contextualizando a necessidade de publicação do Blob Storage com IP público e abrir chamado W para a equipe CSTI-35 operacionalizar a exposição. | **Responsável:** Bruno Aprioto (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 3:** Alinhar com Lindoso (Redes/CSTI-35) o fluxo correto para abertura do chamado W referente à publicação do Blob Storage. | **Responsável:** Bruno Aprioto + Lindoso (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 4:** Abrir demanda de Arquitetura de Referência com o time de André para o desenho da solução RTF/MuleSoft. | **Responsável:** Bruno Aprioto (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 5:** Articular excepcionalização junto à área de Operações para acelerar o processo de arquitetura fora do rito padrão, dado o prazo crítico de dezembro/2026. | **Responsável:** Bruno Aprioto (Caixa). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 6:** Confirmar oficialmente com o time de produtos Salesforce o suporte do RTF ao OKD (OpenShift Community/free). | **Responsável:** Bruno Aniceto (Salesforce). | **Prazo:** A definir. | **Status:** Futuro

➡️ **Ação 7:** Preparar e compartilhar a arquitetura detalhada do RTF (componentes, clusters, requisitos) para submissão ao processo de aprovação interna da Caixa. | **Responsável:** Bruno Aniceto (Salesforce). | **Prazo:** A definir. | **Status:** Futuro

---

Abs, Adriana Visentin
