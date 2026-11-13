## Resumo

Serviços da categoria **Management and Governance** no escopo da AIF-C01. Servem para **auditar, monitorar e revisar** cargas de IA (Domínio 5, tarefa 5.2: governança, logs, retenção, monitoramento).

> [!info] Ideia central
> **CloudTrail** = **quem fez** (API). **CloudWatch** = **como está** (métricas, logs, alarmes). **Config** = **como estava configurado** (histórico). **Trusted Advisor** = **o que melhorar** (recomendações). **Well-Architected Tool** = **revisão da arquitetura** contra boas práticas.

| Serviço | Pergunta que responde | Prioridade |
|---|---|---|
| **AWS CloudTrail** | Quem chamou qual API, de onde e quando? | ⭐⭐⭐ |
| **Amazon CloudWatch** | Como estão o desempenho, os erros e os logs? Alerte se passar do limite | ⭐⭐⭐ |
| **AWS Config** | Como cada recurso estava configurado e se segue as regras | ⭐⭐ |
| **AWS Trusted Advisor** | O que posso melhorar em custo, segurança, desempenho e limites? | ⭐⭐ |
| **AWS Well-Architected Tool** | Minha carga segue o Well-Architected Framework (e as lentes de IA)? | ⭐⭐ |

---

## AWS CloudTrail

Registra as **chamadas de API** e ações na conta: **quem**, **o quê**, **quando**, **de qual IP**.

**Com IA na prova:**
- "Quem **excluiu** o endpoint do SageMaker?", "quem **alterou** o Guardrail?", "quem **invocou** o modelo X?" → **CloudTrail**.
- Base para **auditoria** e investigação forense.

> [!warning] Pegadinha clássica
> O CloudTrail registra **que** houve uma chamada `InvokeModel`, mas **não guarda o texto do prompt e da resposta**. Para o **conteúdo**, use o **Bedrock model invocation logging** (envia para **S3** ou **CloudWatch Logs**). Foi a questão #62 do simulado.

---

## Amazon CloudWatch

**Métricas**, **logs**, **alarmes** e **dashboards** de praticamente todos os serviços.

**Com IA na prova:**
- Métricas do Bedrock: **número de invocações, latência, tokens de entrada/saída, erros, throttling**.
- Métricas e logs de **endpoints do SageMaker**; o **Model Monitor** publica alertas de drift no CloudWatch.
- Destino dos **logs de invocação** do Bedrock (CloudWatch Logs).
- "Avisar quando a **latência** passar de 2 s" → **alarme do CloudWatch**.

---

## AWS Config

Mantém o **histórico de configuração** dos recursos e avalia se seguem **regras** (*Config rules*, *conformance packs*).

**Com IA na prova:**
- "Garantir que todo bucket S3 com dados de treino esteja **criptografado** e alertar se mudar" → **Config rule**.
- "Como estava configurado o endpoint **na semana passada**?" → **Config**.

---

## AWS Trusted Advisor

Faz **verificações automáticas** e dá **recomendações** de boas práticas em: **otimização de custos, desempenho, segurança, tolerância a falhas, limites de serviço** e excelência operacional.

**Com IA na prova:**
- "Encontrar **instâncias ociosas** (ex.: notebook ou endpoint esquecido ligado) para economizar" → **Trusted Advisor** (ou Cost Explorer).
- Não faz auditoria de compliance nem coleta evidências.

---

## AWS Well-Architected Tool

Ferramenta no console para **revisar uma carga de trabalho** respondendo perguntas dos **6 pilares** (excelência operacional, segurança, confiabilidade, eficiência de desempenho, otimização de custos, **sustentabilidade**). Aceita **lentes** específicas.

| Lente relevante para IA | Foco |
|---|---|
| **Generative AI Lens** | Boas práticas para arquitetar aplicações de GenAI |
| **Machine Learning Lens** | Boas práticas para todo o ciclo de ML |
| **Responsible AI Lens** | Projetar e operar IA **responsável** → [[03 - IA Responsável - Serviços AWS\|IA Responsável - Serviços AWS]] |

**Com IA na prova:** "revisar a arquitetura da aplicação de GenAI segundo as **boas práticas da AWS**" → **Well-Architected Tool** (com a lente de GenAI).

---

## Os 5 lado a lado

| Cenário | Serviço |
|---|---|
| "Quem fez?" | **CloudTrail** |
| "O que foi perguntado e respondido ao modelo?" | **Bedrock invocation logging** (→ S3 / CloudWatch Logs) |
| "Está lento / com erro? Me avise" | **CloudWatch** |
| "A configuração mudou? Está fora da regra?" | **Config** |
| "Onde estou gastando à toa / que boa prática falta?" | **Trusted Advisor** |
| "Minha arquitetura de GenAI segue o framework?" | **Well-Architected Tool** |
| "Estou em conformidade com o framework X, com evidências?" | **Audit Manager** (fora da lista atual) → [[01 - Segurança, Identidade e Compliance#Serviço que saiu da lista: AWS Audit Manager]] |

## Fora do escopo

Control Tower, Health Dashboard, Launch Wizard, License Manager, Managed Grafana, Managed Prometheus, Resilience Hub, Resource Explorer, Resource Groups, Systems Manager Incident Manager, Service Catalog, Service Quotas, Telco Network Builder, User Notifications.

## Exemplo para Associação Mental

**O condomínio.** O **CloudTrail** é o **livro da portaria** (quem entrou, a que horas). O **CloudWatch** são as **câmeras e o alarme** (o que está acontecendo agora). O **Config** é a **planta do prédio com histórico de reformas**. O **Trusted Advisor** é o **síndico** que sugere economizar luz e trocar a fechadura. O **Well-Architected Tool** é a **vistoria do engenheiro** com checklist oficial.

---
Voltar: [[07 - Serviços AWS do Exame]] · Domínio: [[06 - Domínio 5 - Segurança, Compliance e Governança]] · Relacionadas: [[00 - Índice - Bedrock|Índice - Bedrock]] · [[06 - SageMaker - Governança e Segurança|SageMaker - Governança e Segurança]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [Bedrock model invocation logging](https://docs.aws.amazon.com/bedrock/latest/userguide/model-invocation-logging.html) · [AWS Well-Architected Tool](https://docs.aws.amazon.com/wellarchitected/latest/userguide/intro.html) · [AWS Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html)
