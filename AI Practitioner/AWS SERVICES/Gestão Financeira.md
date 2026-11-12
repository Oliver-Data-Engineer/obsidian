## Resumo

Serviços da categoria **Cloud Financial Management** no escopo da AIF-C01: **AWS Budgets** e **AWS Cost Explorer**. O guia também pede que o candidato conheça os **modelos de preço** dos serviços de IA, então esta nota junta os dois assuntos.

> [!info] Ideia central
> **Budgets** = **avisar antes** de estourar (orçamento + alerta). **Cost Explorer** = **olhar para trás e prever** (análise e gráficos de gastos).

| Serviço | Em uma linha | Prioridade |
|---|---|---|
| **AWS Budgets** | Define um **orçamento** e **alerta** (ou age) quando o gasto ou o uso passa do limite | ⭐⭐ |
| **AWS Cost Explorer** | **Visualiza e analisa** gastos por serviço, conta, tag; faz **previsão** de custo | ⭐⭐ |

---

## AWS Budgets
- Orçamentos de **custo**, **uso** (ex.: horas de instância) e de reservas/Savings Plans.
- Envia **alertas** (e-mail, SNS) e pode disparar **ações** (ex.: aplicar política IAM que impede criar recursos).
- **Com IA:** "avisar o time quando o gasto com **Bedrock** passar de US$ 1.000 no mês" → **Budgets**.

## AWS Cost Explorer
- Gráficos e relatórios do **histórico de gastos**; filtra por serviço, região, **tags de alocação de custo**.
- **Previsão** dos próximos meses e recomendações (rightsizing, Savings Plans).
- **Com IA:** "descobrir **qual projeto** de IA está gastando mais" → Cost Explorer com **tags** por projeto.

> [!tip] Não confunda
> **Budgets** alerta **no futuro** (limite). **Cost Explorer** analisa o **passado** e projeta. **Trusted Advisor** recomenda economias (recursos ociosos) → [[Gerenciamento e Governança]].

---

## Modelos de preço de IA que caem na prova

| Serviço / modo | Como cobra | Quando usar |
|---|---|---|
| **Bedrock On-Demand** | Por **token** de entrada e saída (imagens: por imagem) | Uso variável, começar rápido |
| **Bedrock Batch** | Por token, com **desconto** em relação ao on-demand | Grandes volumes sem pressa |
| **Bedrock Provisioned Throughput** | Por **hora** de capacidade reservada (com compromisso opcional de 1 ou 6 meses) | Carga **alta e constante** e **obrigatório para modelos customizados** |
| **SageMaker real-time endpoint** | Por **hora de instância** ligada | Tráfego constante, baixa latência |
| **SageMaker Serverless / Async (escala a zero)** | Pelo **uso** | Tráfego intermitente |
| **Serviços de IA prontos** (Comprehend, Rekognition, Polly...) | Por **unidade processada** (caracteres, imagens, minutos de áudio) | Pague pelo uso |

**Fatores que aumentam o custo de GenAI:** modelo **maior**, **mais tokens** (prompts longos, contexto do RAG, respostas longas), **fine-tuning** e **pré-treino** (custo de treino + Provisioned Throughput), endpoints **ligados sem uso**.

**Como reduzir:** modelo **menor** que atenda, **prompt caching**, **batch**, encurtar prompts, **destilação**, desligar recursos ociosos.

Detalhes: [[ML Inference]] · [[Fondation Model]]

---

## Fora do escopo
AWS Application Cost Profiler, AWS Billing Conductor.

## Exemplo para Associação Mental

**A conta de luz.** O **Budgets** é o **alerta do app do banco** quando você passa do limite do mês. O **Cost Explorer** é o **extrato detalhado** com gráfico de "onde foi o dinheiro" e a previsão do próximo mês. Os **tokens** são os **kWh** da IA: quanto mais você fala com o modelo, mais gasta.

---
Voltar: [[07 - Serviços AWS do Exame]] · Relacionadas: [[ML Inference]] · [[Gerenciamento e Governança]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [AWS Budgets](https://docs.aws.amazon.com/cost-management/latest/userguide/budgets-managing-costs.html) · [AWS Cost Explorer](https://docs.aws.amazon.com/cost-management/latest/userguide/ce-what-is.html) · [Amazon Bedrock Pricing](https://aws.amazon.com/bedrock/pricing/)
