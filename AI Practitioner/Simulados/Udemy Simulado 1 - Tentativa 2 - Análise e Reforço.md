## Resumo

Análise da **Tentativa 2 do Simulado 1** (Udemy · *[Simulados] AWS Certified AI Practitioner AIF-C01 PT-BR*), feita em 2026-11-12.

> [!warning] Placar: **44 / 65 (68%)** — logo abaixo da faixa de aprovação
> A nota mínima é **700/1000**. Nos simulados, mire em **75%+** (49+ acertos) para ter folga no dia da prova.
> Os 21 erros **não** são de conteúdo desconhecido: tudo já está no vault. O problema é **diferenciar serviços e opções parecidas**. O reforço abaixo foca nisso.

## Desempenho por domínio

| Domínio | Peso na prova | Acertos | % | Situação |
|---|---|---|---|---|
| 2. Fundamentos de IA Generativa | 24% | 15 / 16 | **94%** | ✅ Forte |
| 3. Aplicações de Foundation Models | **28%** | 12 / 18 | 67% | ⚠️ Revisar (maior peso!) |
| 4. IA Responsável | 14% | 6 / 9 | 67% | ⚠️ Revisar |
| 1. Fundamentos de IA e ML | 20% | 7 / 13 | **54%** | 🔴 Prioridade |
| 5. Segurança, Compliance e Governança | 14% | 4 / 9 | **44%** | 🔴 Prioridade |

## Mapa dos erros por tema

Os 21 erros caem em **7 temas**. Ordem = prioridade (quantidade de erros × peso).

### 1. Modos de inferência do SageMaker (3 erros: #12, #19, #32) 🔴

| Questão | O que você marcou | Correto | Por quê |
|---|---|---|---|
| #12 Escanear contêiner no check-in, resposta **imediata**, **endpoint persistente** | Asynchronous | **Real-time** | "Imediato + persistente + requisição individual" = tempo real |
| #19 **Vários GB** de transações, à noite, pode esperar | Serverless | **Batch Transform** | Payload de **vários GB** passa do limite do async (1 GB) |
| #32 Datasets **< 800 MB**, pode esperar, endpoint ligado à toa | Batch | **Asynchronous** | Cabe em 1 GB, tolera atraso e **escala a zero** |

> [!tip] Regra de bolso: decida pelo **tamanho do payload** e pela **espera aceitável**
> | Modo | Payload | Espera | Palavra-chave |
> |---|---|---|---|
> | **Real-time** | Pequeno (até 25 MB) | Nenhuma | "imediato", "endpoint persistente", "interativo" |
> | **Serverless** | Pequeno (até 4 MB) | Aceita *cold start* | "tráfego intermitente", "dias sem uso" |
> | **Asynchronous** | **Até 1 GB**, processamento até 1 h | Minutos | "fila", "payload grande", "escala a zero", "quase em tempo real" |
> | **Batch Transform** | **Dataset inteiro (GBs)** | Horas | "dataset inteiro", "noturno", "sem endpoint" |
>
> **#19 x #32**: os dois "podem esperar". O que decide é **vários GB → Batch** e **< 1 GB → Async**.

Revisar: [[ML Inference]] · [[SageMaker - Recursos em Detalhe]]

### 2. Serviços de IA prontos (5 erros: #1, #3, #41, #48, #54) 🔴

| Questão | Marcou | Correto | Regra |
|---|---|---|---|
| #1 Sugestões ao **atendente durante a chamada** na central | Q Business | **Amazon Q in Connect** | Central de atendimento / assistência ao agente em tempo real = **Q in Connect** |
| #3 Encaminhar e-mails para o **departamento** certo | Reconhecimento de entidades | **Comprehend custom classification** | Atribuir o texto a **categorias fixas** = classificação. Entidades só **extraem** nomes, datas, locais |
| #41 Feedback de pacientes: sentimento, tópicos e **entidades médicas** | Textract + SageMaker | **Comprehend Medical** | Texto clínico → Comprehend **Medical** (já é texto, não precisa de Textract) |
| #48 Verificar **identidade** + detectar **fraude** (Selecione 2) | Liveness + **EPI + conteúdo impróprio** | Comparação facial com limiar dinâmico + **liveness com comparação facial** | EPI e moderação **não verificam identidade**: são distratores |
| #54 Vídeos: marcar **objetos/cenas/texto** + **transcrever áudio** (Selecione 2) | Comprehend + Transcribe | **Rekognition** + Transcribe | Imagem/vídeo = Rekognition; áudio→texto = Transcribe |

> [!tip] Família Amazon Q
> **Q Business** → perguntas sobre documentos internos (RH, TI) · **Q Developer** → código e AWS · **Q in QuickSight** → dashboards de BI · **Q in Connect** → **central de atendimento**, ajuda o atendente em tempo real.

Revisar: [[Amazon Q]] · [[Amazon Comprehend]] · [[Amazon Rekognition]] · [[Amazon Transcribe]] · [[Resumo]]

### 3. Segurança e governança (5 erros: #24, #37, #55, #62 + #48) 🔴

| Questão | Marcou | Correto | Regra |
|---|---|---|---|
| #24 Auditoria **contínua** + **coleta automática de evidências** para frameworks de compliance | CloudTrail | **AWS Audit Manager** | "evidências" + "frameworks" + "contínuo" = Audit Manager |
| #37 Cada equipe só pode acessar **seus** dados no S3 via Bedrock | Uma role com acesso total + restrições | **Uma service role por equipe**, com acesso só ao seu bucket | **Menor privilégio**: separar por equipe |
| #55 LLM no SageMaker precisa tratar **dados pessoais sensíveis** com segurança | AWS Glue | **Amazon Macie** | **Descobrir PII** no S3 = Macie. Glue = ETL/catálogo |
| #62 Visibilidade **completa das invocações** do Bedrock (prompts e respostas) | CloudTrail | **Model invocation logging** | CloudTrail registra **quem chamou a API**, não o **conteúdo** do prompt/resposta |

> [!tip] Os 4 de auditoria que confundem
> | Serviço | Responde |
> |---|---|
> | **CloudTrail** | **Quem** chamou **qual API**, e quando |
> | **Bedrock model invocation logging** | **O que** foi enviado e respondido (payload completo) → S3/CloudWatch |
> | **AWS Audit Manager** | Estou em **conformidade** com o framework X? Coleta **evidências** automaticamente |
> | **AWS Artifact** | Baixar os relatórios de compliance **da própria AWS** (SOC, ISO) |
> | **AWS Config** | **Histórico de configuração** dos recursos |
> | **Trusted Advisor** | **Recomendações** de boas práticas (custo, segurança) |

Revisar: [[06 - Domínio 5 - Segurança, Compliance e Governança]] · [[SageMaker - Governança e Segurança]] · [[Índice - Bedrock]]

### 4. Customização e parâmetros de FMs (4 erros: #2, #28, #33, #40) ⚠️

| Questão | Marcou | Correto | Regra |
|---|---|---|---|
| #2 Chatbot **inventa** recursos que não existem | Reduzir limite de tokens | **RAG com base curada** | Alucinação → **RAG** (grounding). Tokens só controlam **tamanho** |
| #28 FM especialista em domínio marítimo (Selecione 2) | Supervised learning + fine-tuning | **Domain adaptation fine-tuning** + **continued pre-training** | Especialização de **domínio** = esses dois |
| #33 Fine-tuning no Bedrock e depois **usar o modelo customizado** | On-Demand | **Provisioned Throughput** | Modelo **customizado** no Bedrock **exige** Provisioned Throughput |
| #40 Parâmetros que influenciam a **criatividade** (Selecione 2) | Temperature + tamanho do modelo | **Temperature + Top-p** | Tamanho do modelo **não é** parâmetro de inferência |

> [!warning] O #33 já estava nos seus flashcards
> Está no [[Teste - Bedrock]] ("Quando o Provisioned Throughput é obrigatório?"). Vale reler esses flashcards antes de cada simulado.

Revisar: [[Fondation Model]] · [[Parâmetros de Inferência]] · [[Beadrock Rag - Kb]]

### 5. Tipos de aprendizado (2 erros: #18, #30) ⚠️

| Questão | Marcou | Correto | Regra |
|---|---|---|---|
| #18 Chatbot melhora **continuamente** com o **feedback** (👍) dos pacientes | Treinamento incremental | **Aprendizado por reforço** | **Recompensa** / feedback em tempo real = RL. Incremental = retreinar com novos **lotes** |
| #30 Exemplos de supervisionado (Selecione 2) | Regressão linear + classificação de documentos | Regressão linear + **rede neural** | No contexto da questão, classificação de documentos com poucos rótulos = **semissupervisionado** |

Revisar: [[Aprendizado por Reforço]] · [[Diferenças entre os Tipos de Aprendizado]]

### 6. IA Responsável (3 erros: #9, #43, #60) ⚠️

| Questão | Marcou | Correto | Regra |
|---|---|---|---|
| #9 Classificar respostas do chatbot | B = poisoning, C = leaking | **A = poisoning, B = prompt leaking** | Link malicioso/promoção sem relação = **poisoning**. Cita **sessão anterior** = **prompt leaking** |
| #43 Serviço que **explica** como as features contribuem para a previsão | Model Monitor | **SageMaker Clarify** | Explicar previsão = **Clarify**. Model Monitor = **drift em produção** |
| #60 Shapley x PDP | Shapley = global | **Shapley = local** (uma previsão); **PDP = global** (efeito médio da feature) | "explicar **este** cliente" → SHAP; "como a renda afeta **em geral**" → PDP |

Revisar: [[IA Responsável - Serviços AWS]] · [[IA Responsável - Transparência e Explicabilidade]] · [[Riscos e Segurança em Prompts]]

---

## 🔁 Reforço: 15 questões novas nos seus pontos fracos

Mesmo formato dos outros formulários: marque, justifique e só então abra o gabarito.

### R1
Um app de fotos chama um modelo **algumas vezes por semana**, sem padrão, e fica dias parado. A empresa **não quer pagar por endpoint ocioso** e aceita alguns segundos de *cold start*.

- [ ] A) Real-time Inference
- [ ] B) Serverless Inference
- [ ] C) Batch Transform
- [ ] D) Asynchronous Inference

> [!success]- Gabarito
> **B) Serverless** — tráfego **intermitente** e *cold start* aceito.

### R2
Cada requisição envia um **arquivo de áudio de 300 MB** que leva **15 minutos** para processar. O cliente consulta o resultado depois.

- [ ] A) Asynchronous Inference
- [ ] B) Real-time Inference
- [ ] C) Serverless Inference
- [ ] D) Amazon Bedrock On-Demand

> [!success]- Gabarito
> **A) Async** — payload grande **(≤ 1 GB)**, processamento longo **(≤ 1 h)**, com fila.

### R3
Toda madrugada é preciso pontuar **um arquivo de 40 GB** com milhões de registros. Ninguém espera resposta imediata.

- [ ] A) Asynchronous Inference
- [ ] B) Serverless Inference
- [ ] C) Batch Transform
- [ ] D) Real-time Inference

> [!success]- Gabarito
> **C) Batch Transform** — **vários GB**, dataset inteiro, sem endpoint. Async não aceita payload acima de 1 GB.

### R4
Uma operadora de telefonia quer que seus **atendentes recebam sugestões de resposta em tempo real** durante as ligações, com base nos manuais internos.

- [ ] A) Amazon Q Business
- [ ] B) Amazon Lex
- [ ] C) Amazon Q in Connect
- [ ] D) Amazon Kendra

> [!success]- Gabarito
> **C) Q in Connect** — assistência **ao atendente** na central (Amazon Connect). Lex seria um **bot** atendendo sozinho.

### R5
Um hospital precisa extrair **medicamentos, dosagens e diagnósticos** de anotações clínicas em texto livre.

- [ ] A) Amazon Comprehend (entidades padrão)
- [ ] B) Amazon Comprehend Medical
- [ ] C) Amazon Textract
- [ ] D) Amazon Transcribe Medical

> [!success]- Gabarito
> **B) Comprehend Medical** — NLP para **entidades médicas** em texto. Textract lê documentos digitalizados; Transcribe Medical converte **fala** em texto.

### R6
Uma seguradora quer classificar cada **reclamação** em "Sinistro", "Cobrança" ou "Cancelamento" a partir de milhares de exemplos já rotulados.

- [ ] A) Comprehend — análise de sentimento
- [ ] B) Comprehend — extração de frases-chave
- [ ] C) Comprehend — custom classification
- [ ] D) Comprehend — detecção de PII

> [!success]- Gabarito
> **C) Custom classification** — texto → **categorias fixas** suas, treinado com exemplos rotulados.

### R7 (Escolha 2)
Uma plataforma de cursos quer **gerar legendas** das videoaulas e **detectar automaticamente texto e objetos** exibidos nos slides dos vídeos.

- [ ] A) Amazon Transcribe
- [ ] B) Amazon Polly
- [ ] C) Amazon Rekognition
- [ ] D) Amazon Comprehend
- [ ] E) Amazon Translate

> [!success]- Gabarito
> **A e C** — Transcribe (fala → texto) e Rekognition (objetos e texto em vídeo). Polly é o contrário: texto → fala.

### R8
O time de compliance quer verificar **continuamente** se a conta AWS segue o **framework PCI DSS** e **juntar evidências automaticamente** para o auditor.

- [ ] A) AWS Artifact
- [ ] B) AWS Audit Manager
- [ ] C) AWS CloudTrail
- [ ] D) AWS Trusted Advisor

> [!success]- Gabarito
> **B) Audit Manager** — avaliação contínua contra frameworks + **coleta de evidências**.

### R9
O auditor pede o **relatório SOC 2 da própria AWS** para anexar à documentação do projeto.

- [ ] A) AWS Artifact
- [ ] B) AWS Audit Manager
- [ ] C) AWS Config
- [ ] D) Amazon Macie

> [!success]- Gabarito
> **A) Artifact** — portal para baixar os relatórios de compliance **da AWS**.

### R10
A empresa precisa guardar **o texto de cada prompt e de cada resposta** do Bedrock para investigar respostas inadequadas.

- [ ] A) AWS CloudTrail
- [ ] B) AWS Config
- [ ] C) Bedrock model invocation logging
- [ ] D) Amazon EventBridge

> [!success]- Gabarito
> **C) Model invocation logging** — grava o **conteúdo** (entrada e saída) em S3/CloudWatch Logs. CloudTrail só registra a **chamada de API**.

### R11
Antes de treinar um modelo, a empresa quer **descobrir automaticamente** se há **CPFs e e-mails** nos arquivos guardados no S3.

- [ ] A) AWS Glue
- [ ] B) Amazon Macie
- [ ] C) Amazon Inspector
- [ ] D) AWS KMS

> [!success]- Gabarito
> **B) Macie** — descobre **PII** em buckets S3. Glue = ETL, Inspector = vulnerabilidades, KMS = chaves.

### R12
Depois de fazer **fine-tuning** de um modelo no Bedrock, a equipe tenta chamá-lo no modo **On-Demand** e não consegue. O que precisa fazer?

- [ ] A) Comprar Provisioned Throughput para o modelo customizado
- [ ] B) Usar inferência batch
- [ ] C) Habilitar o Guardrails
- [ ] D) Mover o modelo para o SageMaker Canvas

> [!success]- Gabarito
> **A) Provisioned Throughput** — obrigatório para usar **modelos customizados** no Bedrock.

### R13 (Escolha 2)
Quais parâmetros de inferência aumentam a **diversidade/criatividade** da resposta de um LLM?

- [ ] A) Temperature
- [ ] B) Número de parâmetros do modelo
- [ ] C) Top-p
- [ ] D) Tamanho do dataset de treino
- [ ] E) Região da AWS

> [!success]- Gabarito
> **A e C** — Temperature e Top-p (e Top-k) controlam a aleatoriedade. Tamanho do modelo e dataset **não** são parâmetros de inferência.

### R14
Um jogo treina um agente que **ganha pontos** quando vence e **perde pontos** quando erra, melhorando a cada partida.

- [ ] A) Aprendizado supervisionado
- [ ] B) Aprendizado não supervisionado
- [ ] C) Aprendizado por reforço
- [ ] D) Transfer learning

> [!success]- Gabarito
> **C) Aprendizado por reforço** — **recompensa/penalidade** vinda do ambiente.

### R15
O gerente quer saber **como a feature "idade" afeta, em média, todas as previsões** do modelo. Já o cliente quer saber **por que o pedido dele** foi recusado. Quais técnicas, respectivamente?

- [ ] A) SHAP para os dois
- [ ] B) PDP para o gerente; SHAP para o cliente
- [ ] C) SHAP para o gerente; PDP para o cliente
- [ ] D) Model Monitor para o gerente; A2I para o cliente

> [!success]- Gabarito
> **B)** — **PDP = visão global** (efeito médio de uma feature). **SHAP = explicação local** (uma previsão específica).

**Resultado do reforço:** ___ / 15 (meta: 13+)

---

## Plano até o próximo simulado

| Dia | Foco | Notas |
|---|---|---|
| 1 | Modos de inferência (tabela da regra de bolso) + refazer R1–R3 | [[ML Inference]] |
| 2 | Serviços de IA prontos: família Amazon Q, Comprehend x Comprehend Medical, Rekognition x Transcribe | [[Resumo]] · [[Amazon Q]] · [[Amazon Comprehend]] |
| 3 | Domínio 5: Audit Manager x Artifact x CloudTrail x Config x invocation logging; Macie; IAM com menor privilégio | [[06 - Domínio 5 - Segurança, Compliance e Governança]] |
| 4 | Customização de FMs + parâmetros de inferência + flashcards do [[Teste - Bedrock]] | [[Fondation Model]] · [[Parâmetros de Inferência]] |
| 5 | Tipos de aprendizado + IA Responsável (poisoning x leaking, SHAP x PDP) + [[IA Responsável - Formulário de Respostas]] | [[Diferenças entre os Tipos de Aprendizado]] · [[Índice - IA Responsável]] |
| 6 | **Simulado 2** na Udemy → pedir nova análise | — |

## Histórico de simulados

| Data | Simulado | Tentativa | Nota | Pior domínio |
|---|---|---|---|---|
| 2026-11-12 | Udemy Simulado 1 | 2 | **44/65 (68%)** | Segurança (44%) · Fundamentos IA/ML (54%) |
|  |  |  |  |  |

---
Início: [[00 - Início - Guia do Exame]] · Checklist: [[09 - Checklist de Estudo]]
