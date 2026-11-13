## Resumo

Como o SageMaker aparece nos **Domínios 4 e 5** ([[05 - Domínio 4 - Diretrizes para IA Responsável]] · [[06 - Domínio 5 - Segurança, Compliance e Governança]]): **transparência**, **governança de modelos**, **linhagem de dados**, **segurança** (IAM, criptografia, rede) e **auditoria**.

> [!info] Ideia central
> - **Governança** = saber **o que** cada modelo é, **quem** aprovou, **de onde** vieram os dados e **como** ele está se comportando.
> - **Segurança** = **quem** acessa (IAM), dados **criptografados** (KMS) e tráfego **privado** (VPC / PrivateLink).

---

## 1. Transparência e explicabilidade (Tarefa 4.2)

| Conceito | Em uma linha | Recurso no SageMaker |
|---|---|---|
| **Transparência** | Saber **como** o modelo foi feito (dados, treino, limitações) | **Model Cards** |
| **Explicabilidade** | Entender **por que** ele deu uma resposta | **Clarify** (SHAP) → [[04 - SageMaker - Models and Humans\|SageMaker - Models and Humans]] |
| **Modelos open source** | Pesos, arquitetura e (às vezes) dados conhecidos → mais transparência | **JumpStart** |
| **Licenças** | Cada modelo tem uma licença (uso comercial ou não) | Mostrada no **JumpStart** ao escolher o modelo |
| **Interpretabilidade x desempenho** | Modelos simples (Linear Learner, árvores) são mais explicáveis; redes profundas são mais precisas e opacas | Escolha do algoritmo |

---

## 2. Ferramentas de governança de ML

| Recurso | Para que serve | Pergunta que responde |
|---|---|---|
| **Model Cards** | **Documentação padronizada**: uso pretendido, nível de risco, dados de treino, métricas, resultados de viés | "O que é este modelo e para que pode ser usado?" |
| **Model Registry** | **Versões** do modelo, metadados e **status de aprovação** | "Qual versão está aprovada para produção?" |
| **Model Dashboard** | **Painel único** com todos os modelos, endpoints e alertas | "Como estão todos os meus modelos agora?" |
| **Model Monitor** | Alerta de **drift** (dados, qualidade, viés, explicabilidade) | "O modelo continua bom em produção?" |
| **Role Manager** | Cria **roles IAM** por **persona** com menor privilégio | "Quem pode fazer o quê no SageMaker?" |
| **ML Lineage Tracking** | Registra a **linhagem**: quais dados, código e parâmetros geraram cada modelo | "De onde veio este modelo?" |

> [!note] Linhagem de dados (*data lineage*)
> O guia (Tarefa 5.1) cobra **citação de fontes e origem dos dados**. No SageMaker, isso é feito com **ML Lineage Tracking** (rastreia dataset → treino → modelo → endpoint), **Model Registry** (metadados da versão) e **Model Cards** (documenta os dados usados). Para catalogar dados fora do SageMaker: **AWS Glue Data Catalog**.

---

## 3. Segurança do SageMaker (Tarefa 5.1)

| Camada | Como proteger | Serviço |
|---|---|---|
| **Identidade e acesso** | Roles com **menor privilégio** para usuários, notebooks, jobs e endpoints | **IAM**, **Role Manager** |
| **Criptografia em repouso** | Dados no S3, volumes de notebooks/treino, modelos | **AWS KMS** |
| **Criptografia em trânsito** | **TLS** nas chamadas de API; criptografia do tráfego **entre instâncias** no treino distribuído | TLS (padrão) |
| **Rede privada** | Rodar notebooks, treino e endpoints **dentro da VPC**; acessar a API do SageMaker **sem internet** | **VPC**, **VPC endpoints (AWS PrivateLink)** |
| **Isolamento de rede** | Modo *network isolation*: o container de treino/inferência **não acessa a internet** | Configuração do job |
| **Dados sensíveis** | Descobrir **PII** nos dados de treino no S3 | **Amazon Macie** |
| **Segredos** | Senhas e chaves de API usadas no código | **AWS Secrets Manager** |
| **Vulnerabilidades** | Varredura de imagens de container | **Amazon Inspector** (no ECR) |

> [!tip] Responsabilidade compartilhada no SageMaker
> **AWS:** infraestrutura física, serviço gerenciado, patches da plataforma.
> **Você:** **seus dados**, **permissões IAM**, configurar **criptografia** e **VPC**, o **código** e o **modelo** que você treina, e a **qualidade/viés** dos dados.

---

## 4. Auditoria e monitoramento (Tarefa 5.2)

| Serviço | Papel com o SageMaker |
|---|---|
| **AWS CloudTrail** | Registra **chamadas de API** do SageMaker: quem criou o endpoint, quem treinou o modelo |
| **Amazon CloudWatch** | **Logs** de treino e endpoints, **métricas** (latência, erros, uso de CPU/GPU) e **alarmes**. Recebe as métricas do Model Monitor |
| **AWS Config** | Verifica se recursos estão **configurados conforme as regras** (ex.: notebooks sem acesso direto à internet) |
| **AWS Audit Manager** | Coleta **evidências** para auditorias |
| **AWS Artifact** | **Relatórios de compliance da AWS** (ISO, SOC) que cobrem o SageMaker |

**Estratégias de governança de dados** (guia): **ciclo de vida** e **retenção** dos dados (políticas de lifecycle no S3), **residência** (escolher a **região** onde dados e modelos ficam), **logs** (CloudTrail/CloudWatch) e **monitoramento** (Model Monitor).

> [!warning] Pegadinhas de prova
> - "**Documentar** uso pretendido e riscos do modelo" → **Model Cards**.
> - "Treinar **sem que os dados passem pela internet**" → **VPC + PrivateLink (VPC endpoints)**.
> - "Container de treino **não pode acessar a internet**" → **network isolation**.
> - "**Quem** excluiu o endpoint?" → **CloudTrail**. "Latência do endpoint subiu" → **CloudWatch**.
> - "Encontrar **PII** nos dados de treino no S3" → **Macie**.
> - "Permissões prontas por **persona de ML**" → **Role Manager**.
> - "Rastrear **quais dados geraram** o modelo" → **ML Lineage Tracking** / Model Registry.

## 📝 Meu entendimento

> _Liste as 3 camadas de segurança do SageMaker e um serviço para cada._

---
Voltar: [[00 - Índice - SageMaker|Índice - SageMaker]] · Relacionadas: [[04 - SageMaker - Models and Humans|SageMaker - Models and Humans]] · [[06 - Domínio 5 - Segurança, Compliance e Governança]] · [[07 - Bedrock Guardrails|Bedrock Guardrails]]

Fontes: [Governança de ML no SageMaker](https://aws.amazon.com/sagemaker-ai/ml-governance/) · [Segurança no SageMaker AI](https://docs.aws.amazon.com/sagemaker/latest/dg/security.html)
