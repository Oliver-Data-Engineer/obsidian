## Resumo

Ponto de partida para estudar o **Amazon SageMaker AI** no AI Practitioner. Aqui ficam todas as notas do SageMaker, na ordem recomendada de estudo, e a **matriz de cobertura da ementa**.

> [!info] Ideia central
> **SageMaker** = plataforma **completa** para **construir, treinar, implantar e monitorar** seus próprios modelos de ML. Use quando nenhum serviço pronto (Comprehend, Rekognition…) ou o Bedrock resolver.

## Ordem de estudo

| # | Nota | Para que serve |
|---|---|---|
| 1 | [[Amazon SageMaker]] | Visão geral, ficha rápida, mapa do ciclo de vida e pegadinhas |
| 2 | [[SageMaker - Ciclo de Vida e MLOps]] | Pipeline de ML, origem dos modelos, API gerenciada x auto-hospedada, algoritmos, MLOps, métricas |
| 3 | [[SageMaker - Data Tools]] | Data Wrangler, Feature Store, Processing e Canvas Data Prep |
| 4 | [[SageMaker - Models and Humans]] | Clarify (avaliação, explicabilidade, viés), Ground Truth (rotulagem, RLHF) e A2I |
| 5 | [[SageMaker - IA Generativa]] | JumpStart x Bedrock x PartyRock x Q, fine-tuning, pré-treino, HyperPod, Scoping Matrix |
| 6 | [[SageMaker - Governança e Segurança]] | Model Cards, Registry, Lineage, IAM, KMS, VPC/PrivateLink, CloudTrail/CloudWatch |
| 7 | [[ML Inference]] | Modos de inferência (real-time, serverless, async, batch) |
| 8 | [[SageMaker - Recursos em Detalhe]] | Revisão: todos os recursos, pares que confundem, mapa por persona |
| 9 | [[SageMaker - Formulário de Respostas]] | Simulado com 30 questões para responder e se corrigir (sempre limpo) |
| 10 | [[SageMaker - Formulário 2026-11-11 (respondido)]] | Tentativa 1: 25/30 (83%), com correção e plano de revisão |

## Matriz de cobertura da ementa (AIF-C01)

Tudo o que o [[00 - Início - Guia do Exame|Guia do Exame]] cobra sobre SageMaker e onde está nesta pasta.

| Domínio / Tarefa | O que o guia cobra | Onde estudar | Questões |
|---|---|---|---|
| **D1 · 1.1** | Inferência batch x tempo real | [[ML Inference]] · [[SageMaker - Recursos em Detalhe]] | 6, 9, 15 |
| **D1 · 1.2** | SageMaker entre os serviços de IA/ML; regressão, classificação, clusterização | [[Amazon SageMaker]] · [[SageMaker - Ciclo de Vida e MLOps]] (algoritmos) | 21 |
| **D1 · 1.3** | Etapas do pipeline e serviços (Data Wrangler, Feature Store, Model Monitor) | [[SageMaker - Ciclo de Vida e MLOps]] · [[SageMaker - Data Tools]] | 3, 8, 13 |
| **D1 · 1.3** | Modelos pré-treinados open source x treinados sob medida | [[SageMaker - Ciclo de Vida e MLOps]] | 5 |
| **D1 · 1.3** | API gerenciada x auto-hospedada | [[SageMaker - Ciclo de Vida e MLOps]] | 22 |
| **D1 · 1.3** | MLOps: experimentação, repetibilidade, escala, dívida técnica, produção, monitoramento, retreino | [[SageMaker - Ciclo de Vida e MLOps]] | 10, 16, 23 |
| **D1 · 1.3** | Métricas técnicas e de negócio | [[SageMaker - Ciclo de Vida e MLOps]] | 24 |
| **D2 · 2.3** | Bedrock x JumpStart x PartyRock x Amazon Q | [[SageMaker - IA Generativa]] | 5, 20 |
| **D3 · 3.1** | Custos de customização (prompt, RAG, fine-tuning, pré-treino) | [[SageMaker - IA Generativa]] | 25 |
| **D3 · 3.3** | Fine-tuning, pré-treino contínuo, transfer learning, RLHF | [[SageMaker - IA Generativa]] · [[SageMaker - Models and Humans]] | 19, 25, 26 |
| **D3 · 3.4** | Avaliação de FMs (humana e benchmark) | [[SageMaker - Models and Humans]] (Clarify) | 27 |
| **D4 · 4.1** | Viés: Clarify, Model Monitor, A2I, Ground Truth, auditoria humana | [[SageMaker - Models and Humans]] | 1, 2, 14 |
| **D4 · 4.2** | Transparência: Model Cards, open source, licenças | [[SageMaker - Governança e Segurança]] | 7 |
| **D5 · 5.1** | IAM, criptografia, PrivateLink, Macie, linhagem de dados | [[SageMaker - Governança e Segurança]] | 28, 29 |
| **D5 · 5.2** | CloudTrail, CloudWatch, Config; retenção, residência, logs | [[SageMaker - Governança e Segurança]] | 30 |

## Mapa do ciclo de vida

```mermaid
flowchart LR
  A[1. Dados<br/>Ground Truth<br/>Data Wrangler<br/>Feature Store] --> B[2. Construir e treinar<br/>Studio · Canvas · Autopilot<br/>JumpStart · Training · HyperPod]
  B --> C[3. Ajustar e avaliar<br/>Model Tuning · Clarify<br/>Experiments · Debugger]
  C --> D[4. Implantar<br/>Endpoints · Model Registry<br/>Inference Recommender]
  D --> E[5. Monitorar e governar<br/>Model Monitor · Model Cards<br/>Model Dashboard · Pipelines]
  E -.->|retreino| A
```

## Relacionadas
- [[Amazon Bedrock]] · [[Índice - Bedrock]]
- [[Amazon Augmented AI]] (não confundir com Ground Truth)
- [[Resumo]] dos serviços de IA
- Guia: [[02 - Domínio 1 - Fundamentos de IA e ML]] · [[03 - Domínio 2 - Fundamentos de IA Generativa]] · [[04 - Domínio 3 - Aplicações de Foundation Models]] · [[05 - Domínio 4 - Diretrizes para IA Responsável]] · [[06 - Domínio 5 - Segurança, Compliance e Governança]]

## Checklist

- [ ] Li a visão geral
- [ ] Sei o recurso do SageMaker de cada etapa do pipeline
- [ ] Sei diferenciar API gerenciada x auto-hospedada e modelo pré-treinado x sob medida
- [ ] Sei os conceitos de MLOps e o recurso de cada um
- [ ] Sei o que fazem as Data Tools
- [ ] Sei as 3 funções do Clarify e a diferença Ground Truth x A2I
- [ ] Sei quando usar JumpStart x Bedrock x PartyRock x Q
- [ ] Sei as camadas de segurança e governança do SageMaker
- [ ] Fiz o formulário e acertei 24+ de 30
