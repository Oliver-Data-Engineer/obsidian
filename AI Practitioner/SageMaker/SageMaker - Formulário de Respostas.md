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
- [ ] B) SageMaker Ground Truth
- [ ] C) SageMaker Clarify
- [ ] D) SageMaker Data Wrangler

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Ground Truth** — rotular dados **para treino** com humanos. A2I é revisão humana de **previsões** já feitas.

---

### Questão 2
Um banco precisa **explicar ao cliente** quais fatores levaram à recusa do crédito e provar que o modelo **não discrimina por idade**.

- [ ] A) SageMaker Model Monitor
- [ ] B) SageMaker Model Cards
- [ ] C) SageMaker Clarify
- [ ] D) SageMaker Debugger

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Clarify** — detecta **viés** e dá **explicabilidade** (SHAP).

---

### Questão 3
Seis meses após o deploy, a acurácia do modelo caiu porque o **comportamento dos clientes mudou**. Como detectar isso automaticamente?

- [ ] A) SageMaker Model Monitor
- [ ] B) SageMaker Experiments
- [ ] C) Automatic Model Tuning
- [ ] D) SageMaker Feature Store

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Model Monitor** — monitora **drift** de dados e de qualidade em produção.

---

### Questão 4
Um analista de marketing **sem experiência em programação** quer prever churn a partir de uma planilha CSV.

- [ ] A) SageMaker Studio
- [ ] B) SageMaker JumpStart
- [ ] C) SageMaker Pipelines
- [ ] D) SageMaker Canvas

**Minha justificativa:** 

> [!success]- Gabarito
> **D) Canvas** — ML **sem código** para analistas de negócio.

---

### Questão 5
A empresa quer implantar um modelo **Llama** em **instâncias próprias dentro da VPC**, escolhendo o tipo de instância, e fazer fine-tuning.

- [ ] A) Amazon Bedrock
- [ ] B) SageMaker JumpStart
- [ ] C) SageMaker Canvas
- [ ] D) Amazon Q

**Minha justificativa:** 

> [!success]- Gabarito
> **B) JumpStart** — modelo roda na **sua instância** (controle de infraestrutura). Bedrock seria a resposta se fosse "serverless, só via API".

---

### Questão 6
É preciso gerar previsões para **10 milhões de registros uma vez por noite**, sem manter um endpoint ligado.

- [ ] A) Real-time Inference
- [ ] B) Serverless Inference
- [ ] C) Batch Transform
- [ ] D) Asynchronous Inference

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Batch Transform** — processa o **dataset inteiro** offline e desliga.

---

### Questão 7
Um auditor pede um documento com **uso pretendido, limitações, riscos e métricas** do modelo.

- [ ] A) SageMaker Model Registry
- [ ] B) SageMaker Model Dashboard
- [ ] C) SageMaker Model Cards
- [ ] D) SageMaker Experiments

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Model Cards** — **documentação** para transparência e auditoria.

---

### Questão 8
Várias equipes calculam a variável "média de compras em 30 dias" de **formas diferentes**, e o valor no treino não bate com o da inferência.

- [ ] A) SageMaker Feature Store
- [ ] B) SageMaker Data Wrangler
- [ ] C) SageMaker Processing
- [ ] D) Amazon S3

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Feature Store** — repositório central para **reutilizar** features e manter treino e inferência consistentes.

---

### Questão 9
O modelo recebe **vídeos grandes** e leva cerca de **20 minutos** para processar cada um. O usuário não precisa da resposta na hora.

- [ ] A) Real-time Inference
- [ ] B) Asynchronous Inference
- [ ] C) Serverless Inference
- [ ] D) Batch Transform

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Asynchronous** — payload **grande** e processamento **longo**, com fila.

---

### Questão 10
A equipe quer automatizar **processar → treinar → avaliar → registrar → implantar** toda semana.

- [ ] A) SageMaker Experiments
- [ ] B) SageMaker Pipelines
- [ ] C) SageMaker Debugger
- [ ] D) SageMaker Canvas

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Pipelines** — orquestração e automação (**MLOps / CI/CD de ML**).

---

### Questão 11
Um cientista de dados escolheu o algoritmo XGBoost e quer encontrar automaticamente a **melhor taxa de aprendizado e profundidade da árvore**.

- [ ] A) SageMaker Autopilot
- [ ] B) SageMaker Clarify
- [ ] C) Automatic Model Tuning
- [ ] D) SageMaker Debugger

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Automatic Model Tuning** — ajusta **hiperparâmetros** de um algoritmo já escolhido. Autopilot escolheria o **algoritmo inteiro**.

---

### Questão 12
A empresa quer que o SageMaker **teste vários algoritmos automaticamente** e entregue o melhor modelo, com visibilidade dos notebooks gerados.

- [ ] A) SageMaker Autopilot
- [ ] B) Automatic Model Tuning
- [ ] C) SageMaker JumpStart
- [ ] D) SageMaker Ground Truth

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Autopilot** — **AutoML** com transparência.

---

### Questão 13
Os dados brutos têm **valores nulos e colunas em formatos diferentes**. O time quer limpar e transformar com uma **interface visual**.

- [ ] A) SageMaker Feature Store
- [ ] B) SageMaker Data Wrangler
- [ ] C) SageMaker Ground Truth
- [ ] D) SageMaker Model Monitor

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Data Wrangler** — **preparar e transformar** dados visualmente.

---

### Questão 14
Um modelo em produção faz previsões e, quando a **confiança é baixa**, uma pessoa precisa **revisar** a previsão.

- [ ] A) SageMaker Ground Truth
- [ ] B) SageMaker Clarify
- [ ] C) Amazon Augmented AI (A2I)
- [ ] D) SageMaker Model Monitor

**Minha justificativa:** 

> [!success]- Gabarito
> **C) A2I** — revisão humana de **previsões**. (Ground Truth = rotular dados **para treino**.)

---

### Questão 15
O tráfego do endpoint é **imprevisível**: há dias sem nenhuma requisição e picos ocasionais. A empresa **não quer gerenciar servidores** e aceita *cold start*.

- [ ] A) Serverless Inference
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
- [ ] B) SageMaker Model Registry
- [ ] C) SageMaker Experiments
- [ ] D) SageMaker Feature Store

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Model Registry** — **versões** e status de **aprovação** para deploy.

---

### Questão 17
Uma equipe precisa de **um único ambiente web** com notebooks JupyterLab para desenvolver, treinar e implantar modelos com código.

- [ ] A) SageMaker Canvas
- [ ] B) SageMaker Studio
- [ ] C) Amazon Bedrock Playground
- [ ] D) PartyRock

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Studio** — **IDE web** para cientistas de dados (com código).

---

### Questão 18
Durante o treino de uma rede neural, os **gradientes estão explodindo** e a GPU está subutilizada. Qual recurso alerta isso em tempo real?

- [ ] A) SageMaker Model Monitor
- [ ] B) SageMaker Experiments
- [ ] C) SageMaker Debugger
- [ ] D) Amazon CloudWatch apenas

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Debugger** — acha problemas **dentro do treino**. Model Monitor é para **produção**.

---

### Questão 19
Uma empresa quer **treinar o próprio LLM** em centenas de GPUs por semanas, com **recuperação automática** se um nó falhar.

- [ ] A) SageMaker Canvas
- [ ] B) Amazon Bedrock
- [ ] C) SageMaker HyperPod
- [ ] D) SageMaker Serverless Inference

**Minha justificativa:** 

> [!success]- Gabarito
> **C) HyperPod** — clusters **resilientes** para treinar modelos muito grandes.

---

### Questão 20
Uma startup quer usar um **Foundation Model por API**, **sem gerenciar infraestrutura** nem treinar nada, pagando por uso. SageMaker é a melhor escolha?

- [ ] A) Sim, SageMaker JumpStart
- [ ] B) Sim, SageMaker Studio
- [ ] C) Não, Amazon Bedrock
- [ ] D) Não, Amazon Comprehend

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Amazon Bedrock** — FMs **serverless por API**. A prova cobra saber quando **não** usar o SageMaker.

---

## Folha de resultado

| Data | Acertos (de 20) | Questões que errei | O que revisar |
|---|---|---|---|
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

> [!note] Meta
> **16+ acertos** = pronto para as questões de SageMaker. Abaixo disso, revise [[SageMaker - Recursos em Detalhe]] (seção *Pares que mais confundem*).

---
Voltar: [[Índice - SageMaker]] · [[Amazon SageMaker]] · [[SageMaker - Recursos em Detalhe]]
