## Como usar

1. Leia a questão e **marque a caixinha** da alternativa que você acha correta (clique no `[ ]`).
2. Escreva em **Minha justificativa** por que escolheu (ajuda a fixar).
3. Só então abra o **Gabarito** (clique na seta) e corrija.
4. Anote seus acertos na **Folha de resultado** no final.

> [!tip] Para refazer
> Desmarque as caixinhas (ou duplique esta nota e renomeie com a data, ex.: `Formulário - 2026-11-12`).

---

### Questão 1
Uma empresa tem 80 mil imagens de raio-X e precisa que médicos **marquem as regiões com fratura** antes de treinar um modelo. Qual recurso usar?

- [ ] A) Amazon Augmented AI (A2I)
- [x] B) SageMaker Ground Truth
- [ ] C) SageMaker Clarify
- [ ] D) SageMaker Data Wrangler

**Minha justificativa:** Porque esse serviço é responsavel por rotular dados com humanos 

> [!success]- Gabarito
> **B) Ground Truth** — rotular dados **para treino** com humanos. A2I é revisão humana de **previsões** já feitas.

---

### Questão 2
Um banco precisa **explicar ao cliente** quais fatores levaram à recusa do crédito e provar que o modelo **não discrimina por idade**.

- [ ] A) SageMaker Model Monitor
- [ ] B) SageMaker Model Cards
- [x] C) SageMaker Clarify
- [ ] D) SageMaker Debugger

**Minha justificativa:** Porque exibe os vieses a explicabilidade das decisões do modelo

> [!success]- Gabarito
> **C) Clarify** — detecta **viés** e dá **explicabilidade** (SHAP).

---

### Questão 3
Seis meses após o deploy, a acurácia do modelo caiu porque o **comportamento dos clientes mudou**. Como detectar isso automaticamente?

- [x] A) SageMaker Model Monitor
- [ ] B) SageMaker Experiments
- [ ] C) Automatic Model Tuning
- [ ] D) SageMaker Feature Store

**Minha justificativa:** Monitora o drift

> [!success]- Gabarito
> **A) Model Monitor** — monitora **drift** de dados e de qualidade em produção.

---

### Questão 4
Um analista de marketing **sem experiência em programação** quer prever churn a partir de uma planilha CSV.

- [ ] A) SageMaker Studio
- [ ] B) SageMaker JumpStart
- [ ] C) SageMaker Pipelines
- [x] D) SageMaker Canvas

**Minha justificativa:** Interface no-code para treinamento de dados

> [!success]- Gabarito
> **D) Canvas** — ML **sem código** para analistas de negócio.

---

### Questão 5
A empresa quer implantar um modelo **Llama** em **instâncias próprias dentro da VPC**, escolhendo o tipo de instância, e fazer fine-tuning.

- [ ] A) Amazon Bedrock
- [x] B) SageMaker JumpStart
- [ ] C) SageMaker Canvas
- [ ] D) Amazon Q

**Minha justificativa:** Serviço completo de deploy de FMs

> [!success]- Gabarito
> **B) JumpStart** — modelo roda na **sua instância** (controle de infraestrutura). Bedrock seria a resposta se fosse "serverless, só via API".

---

### Questão 6
É preciso gerar previsões para **10 milhões de registros uma vez por noite**, sem manter um endpoint ligado.

- [ ] A) Real-time Inference
- [ ] B) Serverless Inference
- [x] C) Batch Transform
- [ ] D) Asynchronous Inference

**Minha justificativa:** Processamento em Lote

> [!success]- Gabarito
> **C) Batch Transform** — processa o **dataset inteiro** offline e desliga.

---

### Questão 7
Um auditor pede um documento com **uso pretendido, limitações, riscos e métricas** do modelo.

- [ ] A) SageMaker Model Registry
- [x] B) SageMaker Model Dashboard
- [ ] C) SageMaker Model Cards
- [ ] D) SageMaker Experiments

**Minha justificativa:** Model Cards é reponsavel do documentar o modelo

> [!success]- Gabarito
> **C) Model Cards** — **documentação** para transparência e auditoria.

---

### Questão 8
Várias equipes calculam a variável "média de compras em 30 dias" de **formas diferentes**, e o valor no treino não bate com o da inferência.

- [x] A) SageMaker Feature Store
- [ ] B) SageMaker Data Wrangler
- [ ] C) SageMaker Processing
- [ ] D) Amazon S3

**Minha justificativa:** Armazena features para compartilhamento

> [!success]- Gabarito
> **A) Feature Store** — repositório central para **reutilizar** features e manter treino e inferência consistentes.

---

### Questão 9
O modelo recebe **vídeos grandes** e leva cerca de **20 minutos** para processar cada um. O usuário não precisa da resposta na hora.

- [ ] A) Real-time Inference
- [x] B) Asynchronous Inference
- [ ] C) Serverless Inference
- [ ] D) Batch Transform

	**Minha justificativa:** Videos gransde são processados em asynchonus

> [!success]- Gabarito
> **B) Asynchronous** — payload **grande** e processamento **longo**, com fila.

---

### Questão 10
A equipe quer automatizar **processar → treinar → avaliar → registrar → implantar** toda semana.

- [ ] A) SageMaker Experiments
- [x] B) SageMaker Pipelines
- [ ] C) SageMaker Debugger
- [ ] D) SageMaker Canvas

**Minha justificativa:** Atomação de processos são feitos com pipeline

> [!success]- Gabarito
> **B) Pipelines** — orquestração e automação (**MLOps / CI/CD de ML**).

---

### Questão 11
Um cientista de dados escolheu o algoritmo XGBoost e quer encontrar automaticamente a **melhor taxa de aprendizado e profundidade da árvore**.

- [ ] A) SageMaker Autopilot
- [ ] B) SageMaker Clarify
- [x] C) Automatic Model Tuning
- [ ] D) SageMaker Debugger

**Minha justificativa:** Responsavel por melhorar os Hyperparams dos modelos

> [!success]- Gabarito
> **C) Automatic Model Tuning** — ajusta **hiperparâmetros** de um algoritmo já escolhido. Autopilot escolheria o **algoritmo inteiro**.

---

### Questão 12
A empresa quer que o SageMaker **teste vários algoritmos automaticamente** e entregue o melhor modelo, com visibilidade dos notebooks gerados.

- [x] A) SageMaker Autopilot
- [ ] B) Automatic Model Tuning
- [ ] C) SageMaker JumpStart
- [ ] D) SageMaker Ground Truth

**Minha justificativa:** Teste Automático de Augoritimo

> [!success]- Gabarito
> **A) Autopilot** — **AutoML** com transparência.

---

### Questão 13
Os dados brutos têm **valores nulos e colunas em formatos diferentes**. O time quer limpar e transformar com uma **interface visual**.

- [ ] A) SageMaker Feature Store
- [x] B) SageMaker Data Wrangler
- [ ] C) SageMaker Ground Truth
- [ ] D) SageMaker Model Monitor

**Minha justificativa:** Limpeza e transformação de dados

> [!success]- Gabarito
> **B) Data Wrangler** — **preparar e transformar** dados visualmente.

---

### Questão 14
Um modelo em produção faz previsões e, quando a **confiança é baixa**, uma pessoa precisa **revisar** a previsão.

- [ ] A) SageMaker Ground Truth
- [ ] B) SageMaker Clarify
- [x] C) Amazon Augmented AI (A2I)
- [ ] D) SageMaker Model Monitor

**Minha justificativa:** revisão após baixa confiança

> [!success]- Gabarito
> **C) A2I** — revisão humana de **previsões**. (Ground Truth = rotular dados **para treino**.)

---

### Questão 15
O tráfego do endpoint é **imprevisível**: há dias sem nenhuma requisição e picos ocasionais. A empresa **não quer gerenciar servidores** e aceita *cold start*.

- [x] A) Serverless Inference
- [ ] B) Real-time Inference
- [ ] C) Batch Transform
- [ ] D) SageMaker HyperPod

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Serverless** — tráfego **intermitente**, paga só pelo uso.

---

### Questão 16
Antes de colocar uma nova versão do modelo em produção, ela precisa ser **aprovada** e ter **histórico de versões**.

- [ ] A) SageMaker Model Cards
- [x] B) SageMaker Model Registry
- [ ] C) SageMaker Experiments
- [ ] D) SageMaker Feature Store

**Minha justificativa:** Aprovação de modelo pasam pelo Registry 

> [!success]- Gabarito
> **B) Model Registry** — **versões** e status de **aprovação** para deploy.

---

### Questão 17
Uma equipe precisa de **um único ambiente web** com notebooks JupyterLab para desenvolver, treinar e implantar modelos com código.

- [ ] A) SageMaker Canvas
- [x] B) SageMaker Studio
- [ ] C) Amazon Bedrock Playground
- [ ] D) PartyRock

**Minha justificativa:** Ambiente de desenvolvimento (IDE)

> [!success]- Gabarito
> **B) Studio** — **IDE web** para cientistas de dados (com código).

---

### Questão 18
Durante o treino de uma rede neural, os **gradientes estão explodindo** e a GPU está subutilizada. Qual recurso alerta isso em tempo real?

- [x] A) SageMaker Model Monitor
- [ ] B) SageMaker Experiments
- [ ] C) SageMaker Debugger
- [ ] D) Amazon CloudWatch apenas

**Minha justificativa:** monitora as variaveis e alerta

> [!success]- Gabarito
> **C) Debugger** — acha problemas **dentro do treino**. Model Monitor é para **produção**.

---

### Questão 19
Uma empresa quer **treinar o próprio LLM** em centenas de GPUs por semanas, com **recuperação automática** se um nó falhar.

- [ ] A) SageMaker Canvas
- [ ] B) Amazon Bedrock
- [x] C) SageMaker HyperPod
- [ ] D) SageMaker Serverless Inference

**Minha justificativa:** Treinamento maxivo de FMs

> [!success]- Gabarito
> **C) HyperPod** — clusters **resilientes** para treinar modelos muito grandes.

---

### Questão 20
Uma startup quer usar um **Foundation Model por API**, **sem gerenciar infraestrutura** nem treinar nada, pagando por uso. SageMaker é a melhor escolha?

- [ ] A) Sim, SageMaker JumpStart
- [ ] B) Sim, SageMaker Studio
- [x] C) Não, Amazon Bedrock
- [ ] D) Não, Amazon Comprehend

**Minha justificativa:** api de modelo usamos o beadrock

> [!success]- Gabarito
> **C) Amazon Bedrock** — FMs **serverless por API**. A prova cobra saber quando **não** usar o SageMaker.

---

### Questão 21
Uma loja quer **segmentar clientes em grupos** por comportamento de compra. **Não existem rótulos** prontos. Qual técnica e qual algoritmo do SageMaker?

- [ ] A) Classificação com XGBoost
- [ ] B) Regressão com Linear Learner
- [x] C) Clusterização com k-means
- [ ] D) Série temporal com DeepAR

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Clusterização com k-means** — sem rótulos + agrupar = **não supervisionado**.

---

### Questão 22
Uma empresa com **equipe pequena de infraestrutura** quer disponibilizar um modelo sem cuidar de servidores, patches e escala. O que é mais adequado?

- [ ] A) Hospedar o modelo em instâncias EC2 gerenciadas pela própria equipe
- [x] B) Usar uma API gerenciada (SageMaker Endpoint ou Bedrock)
- [ ] C) Rodar o modelo on-premises
- [ ] D) Criar um cluster EKS próprio

**Minha justificativa:** 

> [!success]- Gabarito
> **B) API gerenciada** — a AWS cuida da infraestrutura. Auto-hospedar (EC2/EKS/on-prem) dá mais controle, mas muito mais esforço operacional.

---

### Questão 23
Cada cientista de dados roda **scripts manuais diferentes** para treinar o modelo, e ninguém consegue **reproduzir** os resultados. Qual conceito de MLOps está faltando e qual recurso ajuda?

- [ ] A) Escalabilidade → HyperPod
- [x] B) Processos repetíveis → SageMaker Pipelines
- [ ] C) Explicabilidade → Clarify
- [ ] D) Monitoramento → CloudWatch

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Processos repetíveis → Pipelines** — automatiza o fluxo para que ele rode sempre igual.

---

### Questão 24
Um modelo de fraude tem **99% de acurácia**, mas apenas 1% das transações são fraudes e ele **quase nunca detecta as fraudes**. Qual métrica avaliar?

- [x] A) Acurácia
- [ ] B) RMSE
- [ ] C) Recall / F1-score
- [ ] D) BLEU

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Recall / F1** — com classes **desbalanceadas** a acurácia engana. Recall mede quantas fraudes reais foram encontradas.

---

### Questão 25
Um escritório de advocacia quer que o modelo entenda **profundamente o vocabulário jurídico** e tem milhões de documentos **não rotulados**. Qual abordagem?

- [ ] A) Prompt engineering
- [ ] B) Fine-tuning com pares prompt → resposta
- [ ] C) Pré-treino contínuo
- [x] D) RAG

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Pré-treino contínuo** — ensina um **domínio novo** com muitos dados **não rotulados**. Fine-tuning usa dados **rotulados**.

---

### Questão 26
A empresa quer que humanos **ranqueiem as respostas** de um LLM ("A é melhor que B") para **alinhar** o modelo às preferências humanas. Qual técnica e recurso?

- [ ] A) RAG com Bedrock Knowledge Bases
- [x] B) RLHF com SageMaker Ground Truth
- [ ] C) Explicabilidade com Clarify
- [ ] D) Revisão humana com A2I

**Minha justificativa:** 

> [!success]- Gabarito
> **B) RLHF com Ground Truth** — feedback humano para treinar/alinhar o modelo.

---

### Questão 27
O time precisa avaliar se dois LLMs respondem com o **tom e a voz da marca**, algo difícil de medir com métricas automáticas. Qual opção?

- [ ] A) Avaliação automática com ROUGE
- [x] B) Avaliação humana com SageMaker Clarify (ou Bedrock Model Evaluation)
- [ ] C) SageMaker Model Monitor
- [ ] D) Automatic Model Tuning

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Avaliação humana** — critérios **subjetivos** (tom, estilo, marca) pedem avaliadores humanos.

---

### Questão 28
Por exigência de compliance, os dados de treino **não podem trafegar pela internet** ao acessar o SageMaker. O que usar?

- [ ] A) Amazon Macie
- [x] B) VPC com VPC endpoints (AWS PrivateLink)
- [ ] C) AWS Artifact
- [ ] D) SageMaker Model Cards

**Minha justificativa:** 

> [!success]- Gabarito
> **B) VPC + PrivateLink** — comunicação **privada** com o SageMaker, sem internet pública.

---

### Questão 29
Um auditor quer saber **quais datasets, código e parâmetros** geraram a versão do modelo que está em produção. Qual recurso ajuda?

- [ ] A) SageMaker ML Lineage Tracking / Model Registry
- [ ] B) Amazon Macie
- [ ] C) SageMaker Debugger
- [ ] D) AWS Trusted Advisor

**Minha justificativa:** 

> [!success]- Gabarito
> **A) ML Lineage Tracking / Model Registry** — **linhagem** (origem) do modelo e dos dados.

---

### Questão 30
Um endpoint de produção foi **excluído** e a empresa quer descobrir **quem fez isso e quando**.

- [ ] A) Amazon CloudWatch
- [ ] B) SageMaker Model Monitor
- [ ] C) AWS CloudTrail
- [ ] D) AWS Config

**Minha justificativa:** 

> [!success]- Gabarito
> **C) CloudTrail** — registra **chamadas de API** (quem fez o quê). CloudWatch é para métricas e logs de desempenho.

---

## Folha de resultado

| Data | Acertos (de 30) | Questões que errei | O que revisar |
|---|---|---|---|
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

> [!note] Meta
> **24+ acertos** = pronto para as questões de SageMaker. Abaixo disso, use a **matriz de cobertura** no [[Índice - SageMaker]] para achar a nota de cada questão errada.

---
Voltar: [[Índice - SageMaker]] · [[Amazon SageMaker]] · [[SageMaker - Recursos em Detalhe]]
