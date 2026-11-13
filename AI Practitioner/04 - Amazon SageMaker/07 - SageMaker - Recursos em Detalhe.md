## Resumo

Nota de aprofundamento do [[01 - Amazon SageMaker|Amazon SageMaker]]. O objetivo é **diferenciar cada recurso**: o que faz, quem usa, caso de uso e com o que a prova tenta confundir. A pergunta da prova quase sempre é: *"qual recurso do SageMaker resolve este problema?"*.

> [!info] Regra de ouro
> Leia o **verbo** do enunciado: **rotular** → Ground Truth · **preparar** → Data Wrangler · **guardar features** → Feature Store · **sem código** → Canvas · **modelo pronto** → JumpStart · **hiperparâmetros** → Automatic Model Tuning · **viés / explicar** → Clarify · **drift** → Model Monitor · **documentar** → Model Cards · **versionar/aprovar** → Model Registry · **automatizar fluxo** → Pipelines.

---

## 1. Preparação de dados

### SageMaker Ground Truth
- **O que faz:** **rotula (anota) dados** para treino usando humanos — sua equipe, fornecedores ou **Amazon Mechanical Turk** — com ajuda de ML (rotulagem ativa reduz custo).
- **Ground Truth Plus:** versão em que a **AWS fornece a força de trabalho** especializada (você só envia os dados).
- **Também usado para:** coletar **feedback humano** para GenAI (ex.: ranquear respostas → **RLHF**).
- **Caso de uso:** você tem 100 mil fotos de peças e precisa marcar quais têm defeito antes de treinar um modelo de visão.

### SageMaker Data Wrangler
- **O que faz:** **importa, limpa, transforma e visualiza dados** com interface visual (300+ transformações prontas), sem precisar escrever muito código. Gera relatório de qualidade dos dados.
- **Hoje** fica dentro do **SageMaker Canvas**.
- **Caso de uso:** tratar valores nulos, normalizar colunas, criar novas features (*feature engineering*) a partir de dados do S3, Athena, Redshift.

### SageMaker Feature Store
- **O que faz:** **repositório central de features** (variáveis já processadas) para **reutilizar** entre equipes e garantir que **treino e inferência usam a mesma feature**.
- Tem armazenamento **online** (baixa latência, inferência em tempo real) e **offline** (histórico, treino).
- **Caso de uso:** a feature "gasto médio do cliente nos últimos 30 dias" é usada por 3 modelos diferentes (fraude, churn, recomendação).

### SageMaker Processing
- **O que faz:** roda **jobs de processamento** (pré/pós-processamento, avaliação) em infraestrutura gerenciada com seus scripts (scikit-learn, Spark).
- **Caso de uso:** rodar um script Python pesado de limpeza de dados sem gerenciar servidor.

---

## 2. Construir e treinar

### SageMaker Studio
- **O que faz:** **IDE web** (ambiente central) para todo o ciclo de ML: notebooks **JupyterLab**, Code Editor (VS Code), jobs, pipelines, registry.
- **Quem usa:** cientistas de dados e engenheiros de ML.
- **Caso de uso:** "a equipe precisa de um único ambiente para desenvolver, treinar e implantar".

### SageMaker Canvas
- **O que faz:** **ML sem código** (*no-code*) com interface visual. Você aponta os dados, escolhe a coluna alvo e ele treina o modelo (AutoML por trás).
- Inclui **modelos prontos** (análise de sentimento, extração de texto, detecção de objetos) e acesso a **FMs** do Bedrock/JumpStart para GenAI.
- **Quem usa:** **analistas de negócio** sem experiência em ML/código.
- **Caso de uso:** analista de vendas quer prever demanda do próximo trimestre a partir de uma planilha.

### SageMaker Autopilot (AutoML)
- **O que faz:** **AutoML** — testa automaticamente algoritmos, pré-processamento e hiperparâmetros e entrega o **melhor modelo** com **transparência** (você vê os notebooks gerados).
- Hoje é o "motor" de AutoML exposto pelo **Canvas**.
- **Caso de uso:** "criar um modelo de classificação automaticamente, sem escolher algoritmo manualmente".

### SageMaker JumpStart
- **O que faz:** **hub de modelos pré-treinados** e **Foundation Models** (Llama, Mistral, Falcon, Stable Diffusion…) + soluções prontas. Implanta com 1 clique e permite **fine-tuning**.
- **Diferença-chave:** o modelo roda em **instâncias SageMaker na sua conta** → **você controla a infraestrutura** (tipo de instância, rede, VPC).
- **Caso de uso:** implantar um modelo open source e fazer fine-tuning com dados próprios, controlando a instância.

### Training Jobs e algoritmos integrados
- **O que faz:** treino **gerenciado** — você escolhe instâncias, o SageMaker sobe, treina e desliga (paga só pelo tempo). Suporta **algoritmos integrados** (XGBoost, Linear Learner, k-means, PCA, Image Classification, BlazingText, DeepAR…), frameworks (TensorFlow, PyTorch) ou container próprio.
- **Managed Spot Training:** usa instâncias Spot → **até ~90% mais barato**.
- **Distributed Training:** divide o treino em várias GPUs/instâncias.

### SageMaker HyperPod
- **O que faz:** **clusters resilientes** para treinar **modelos muito grandes** (FMs) por semanas/meses, com recuperação automática de falhas de nós.
- **Caso de uso:** treinar ou pré-treinar um LLM próprio em centenas de GPUs.

---

## 3. Ajustar, avaliar e explicar

### Automatic Model Tuning (AMT)
- **O que faz:** **otimização de hiperparâmetros** (*hyperparameter tuning*) — roda vários treinos com combinações diferentes (bayesiana, random, grid, hyperband) e escolhe a melhor pela métrica alvo.
- **Caso de uso:** "melhorar a acurácia ajustando taxa de aprendizado e profundidade da árvore automaticamente".

### SageMaker Clarify
- **O que faz:** duas coisas, ambas de **IA Responsável**:
  1. **Detecta viés** (*bias*) nos **dados** (antes do treino) e no **modelo** (depois do treino).
  2. **Explicabilidade**: mostra **quais features** mais influenciaram a previsão (usa **SHAP**).
- Também faz **avaliação de Foundation Models** (precisão, toxicidade, robustez, estereótipos).
- **Caso de uso:** banco precisa provar que o modelo de crédito não discrimina por gênero e explicar por que negou um empréstimo.

### SageMaker Experiments
- **O que faz:** **rastreia e compara** execuções de treino (parâmetros, métricas, artefatos). Hoje integra com **MLflow gerenciado**.

### SageMaker Debugger
- **O que faz:** monitora o treino **em tempo real** e alerta sobre problemas (gradientes que somem/explodem, overfitting, uso ruim de GPU).

---

## 4. Implantar (inferência)

Detalhes em [[04 - ML Inference|ML Inference]]. Escolha pelo **padrão de tráfego**:

| Opção | Quando usar | Palavra-chave |
|---|---|---|
| **Real-time** | Resposta imediata, tráfego constante | "baixa latência", "tempo real" |
| **Serverless** | Tráfego **intermitente/imprevisível**, tolera *cold start* | "sem gerenciar servidor", "picos ocasionais" |
| **Asynchronous** | Payload **grande** (até 1 GB) ou processamento **longo** (até 1h), fila | "arquivos grandes", "não precisa resposta imediata" |
| **Batch Transform** | Prever um **dataset inteiro** de uma vez, sem endpoint | "milhões de registros", "offline", "uma vez por dia" |

Outros recursos de implantação:
- **Model Registry:** catálogo de **versões** do modelo com status de **aprovação** (pendente/aprovado/rejeitado) antes de ir para produção.
- **Inference Recommender:** testa e **recomenda o tipo de instância** ideal (custo x latência).
- **Shadow testing:** testa um novo modelo recebendo **cópia do tráfego real** sem afetar o usuário.
- **SageMaker Neo:** **compila/otimiza** o modelo para rodar em dispositivos de **borda** (edge, IoT).

---

## 5. Monitorar, governar e automatizar (MLOps)

### SageMaker Model Monitor
- **O que faz:** monitora o modelo **em produção** e alerta quando há **drift** (desvio): qualidade dos dados, qualidade do modelo, viés e explicabilidade (com Clarify). Envia métricas ao **CloudWatch**.
- **Caso de uso:** o comportamento dos clientes mudou após uma crise e a acurácia caiu → alerta para **retreinar**.

### SageMaker Model Cards
- **O que faz:** **documentação padronizada** do modelo: uso pretendido, riscos, dados de treino, métricas de avaliação. Foco em **transparência, auditoria e governança**.

### SageMaker Model Dashboard
- **O que faz:** **painel central** com todos os modelos em produção, seus alertas do Model Monitor e Model Cards.

### SageMaker Role Manager
- **O que faz:** cria **permissões IAM** prontas por **persona** (cientista de dados, engenheiro de MLOps) com menor privilégio.

### SageMaker Pipelines
- **O que faz:** **orquestra e automatiza** o fluxo de ML (processar → treinar → avaliar → registrar → implantar). É o **CI/CD de ML (MLOps)**.
- **Caso de uso:** retreinar e reimplantar o modelo automaticamente toda semana com dados novos.

---

## Pares que mais confundem

| Confusão | Diferença |
|---|---|
| **Ground Truth** x **Amazon A2I** | Ground Truth = humano **rotula dados para treinar**. A2I = humano **revisa previsões** de um modelo já em produção (baixa confiança) |
| **Data Wrangler** x **Feature Store** | Wrangler **cria/transforma** features. Feature Store **guarda e compartilha** features |
| **Canvas** x **Autopilot** | Canvas = **interface no-code** para analistas. Autopilot = **motor de AutoML** (com visibilidade técnica). Canvas usa o Autopilot por trás |
| **Canvas** x **Studio** | Canvas = analista **sem código**. Studio = cientista de dados **com código** (IDE) |
| **JumpStart** x **Bedrock** | JumpStart = modelo roda **na sua instância**, mais **controle**. Bedrock = **serverless por API**, sem gerenciar infraestrutura |
| **Clarify** x **Model Monitor** | Clarify = **analisa viés/explica** (pontual, antes ou depois do treino). Model Monitor = **vigia continuamente** o modelo em produção (drift). Monitor usa Clarify para monitorar viés |
| **Model Cards** x **Model Registry** | Cards = **documentação** (transparência). Registry = **controle de versões e aprovação** para deploy |
| **Automatic Model Tuning** x **Autopilot** | AMT ajusta **hiperparâmetros de um algoritmo** que você escolheu. Autopilot escolhe **o algoritmo inteiro** e tudo mais |
| **Experiments** x **Debugger** | Experiments **compara execuções**. Debugger **acha problemas dentro** de uma execução de treino |
| **Serverless** x **Asynchronous** | Serverless = requisições pequenas, tráfego intermitente. Async = payload **grande** / processamento **longo** |
| **Real-time** x **Batch Transform** | Real-time = **endpoint** sempre ligado. Batch = processa **dataset inteiro** e desliga |
| **Pipelines** x **Step Functions** | Pipelines é o orquestrador **específico de ML** dentro do SageMaker |

---

## Mapa por persona

| Persona | Recursos típicos |
|---|---|
| **Analista de negócio** (sem código) | Canvas (com Data Wrangler e Autopilot por trás) |
| **Cientista de dados** | Studio, Notebooks, Training, AMT, Experiments, Clarify, JumpStart |
| **Engenheiro de ML / MLOps** | Pipelines, Model Registry, Endpoints, Model Monitor, Inference Recommender |
| **Governança / Compliance** | Model Cards, Model Dashboard, Clarify, Role Manager |
| **Equipe de rotulagem** | Ground Truth (Plus) |

---

## Teste rápido

> [!question]- 1. Uma empresa precisa que humanos marquem caixas ao redor de carros em 50 mil imagens para treinar um modelo. Qual recurso?
> **SageMaker Ground Truth** (rotular dados para treino).

> [!question]- 2. Um modelo de crédito precisa mostrar quais fatores levaram à recusa do cliente. Qual recurso?
> **SageMaker Clarify** (explicabilidade, SHAP).

> [!question]- 3. Seis meses após o deploy, a precisão caiu porque o perfil dos clientes mudou. Como detectar isso automaticamente?
> **SageMaker Model Monitor** (data/model drift).

> [!question]- 4. Um analista de marketing sem experiência em programação quer prever churn a partir de um CSV.
> **SageMaker Canvas**.

> [!question]- 5. A empresa quer implantar o Llama em instâncias próprias, dentro da VPC, e fazer fine-tuning.
> **SageMaker JumpStart** (controle de infraestrutura). Se fosse "serverless, só via API" → Bedrock.

> [!question]- 6. É preciso prever 10 milhões de registros uma vez por noite, sem endpoint permanente.
> **Batch Transform**.

> [!question]- 7. O auditor pede documentação com uso pretendido, limitações e métricas do modelo.
> **SageMaker Model Cards**.

> [!question]- 8. Várias equipes recalculam a mesma variável "média de compras" de jeitos diferentes.
> **SageMaker Feature Store**.

> [!question]- 9. O modelo recebe arquivos de vídeo grandes e o processamento leva ~20 minutos por arquivo.
> **Asynchronous Inference**.

> [!question]- 10. A equipe quer automatizar processar → treinar → avaliar → aprovar → implantar a cada semana.
> **SageMaker Pipelines** (+ Model Registry para aprovação).

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, a diferença entre os recursos que mais te confundem._

---
Voltar: [[01 - Amazon SageMaker|Amazon SageMaker]] · Relacionadas: [[04 - ML Inference|ML Inference]] · [[01 - Amazon Bedrock|Amazon Bedrock]] · [[13 - Amazon Augmented AI|Amazon Augmented AI]]

Fontes: [Amazon SageMaker AI](https://aws.amazon.com/pt/sagemaker-ai/) · [Documentação do SageMaker AI](https://docs.aws.amazon.com/sagemaker/latest/dg/whatis.html)
