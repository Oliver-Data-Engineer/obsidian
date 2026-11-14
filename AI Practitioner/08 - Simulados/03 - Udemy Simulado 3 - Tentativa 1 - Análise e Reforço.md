## Resumo

Análise da **Tentativa 1 do Simulado 3** (Udemy · *[Simulados] AWS Certified AI Practitioner AIF-C01 PT-BR*), feita em 2026-11-14 (simulado de 2026-11-13). Tempo usado: **1h20** de 1h30.

> [!success] Placar: **56 / 65 (86%)**: aprovado ✅
> Subiu **10 pontos** em relação ao Simulado 2 (76%) e passou a meta de folga de **80%**.
> ⏱️ Usou **89% do tempo** (no S2 foram 96%). Ainda dá para ganhar tempo: tente terminar a primeira passada em **~70 min**.
> 🏷️ **4 marcadas para revisão** (#6, #21, #40, #55): acertou 2 e errou 2. Na dúvida, o seu "chute" acertou metade das vezes.

## Evolução por domínio

| Domínio                               | Peso    | Simulado 1 | Simulado 2 | **Simulado 3**  | Tendência                         |
| ------------------------------------- | ------- | ---------- | ---------- | --------------- | --------------------------------- |
| 2. Fundamentos de IA Generativa       | 24%     | 94%        | 81%        | **94%** (15/16) | ⬆️ +13                            |
| 3. Aplicações de Foundation Models    | **28%** | 67%        | 72%        | **89%** (16/18) | 🚀 +17                            |
| 5. Segurança, Compliance e Governança | 14%     | 44%        | 89%        | **89%** (8/9)   | ➖ estável                        |
| 4. IA Responsável                     | 14%     | 67%        | 67%        | **78%** (7/9)   | ⬆️ +11 (finalmente saiu dos 67%)  |
| 1. Fundamentos de IA e ML             | 20%     | 54%        | 77%        | **77%** (10/13) | ➖ **parado**: prioridade         |

> [!warning] O que os três simulados mostram juntos
> 1. **Fundamentos de IA e ML** está parado em 77%. Os erros agora são de **qual serviço usar** (Ground Truth, Personalize, CloudWatch), não de teoria.
> 2. **Ground Truth x A2I** derrubou **2 questões** (#45 e #58). É a confusão mais cara deste simulado.
> 3. **Parâmetros de inferência** voltaram a cair (#6, top-k), depois de 3 erros no S2. O tema ainda não está firme.
> 4. **Audit Manager** apareceu de novo como distrator (#32). No S2 a resposta certa era Config; aqui era Model Monitor.

## As 4 questões marcadas para revisão

| Questão | Resultado | Você marcou | Correto | Por que |
|---|---|---|---|---|
| #6 Vantagem do **top-k** | ❌ | "Escolhe qualquer palavra de **todo o vocabulário**" | **Limita** a escolha às **k** palavras mais prováveis: diversidade **controlada** e sem lixo | Top-k **corta** o vocabulário. "Sempre a mais provável" = **greedy** |
| #21 Recurso do **Macie** que acha dados sensíveis no S3 | ✅ | Automated Data Discovery | — | Macie = **PII no S3**. Pode confiar |
| #40 Sensor **IoT** com **latência mínima** | ❌ | API central + SLM em endpoint **assíncrono** | **SLM otimizado no próprio dispositivo** | "Assíncrono" = latência **alta**. Ir à nuvem soma rede. Edge + baixa latência = **inferência local** |
| #55 Classificar ataques de prompt | ✅ | B = hijacking; D = jailbreaking | — | Acertou, mas a dúvida mostra que vale fixar a tabela de [[06 - Riscos e Segurança em Prompts\|Riscos e Segurança em Prompts]] |

## Mapa dos erros por tema

### 1. Ground Truth x A2I x Data Wrangler (2 erros: #45, #58) 🔴

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #45 **Revisão humana e auditoria** das **predições** de ML, fácil de implantar, com vários revisores | SageMaker Ground Truth | **Amazon Augmented AI (A2I)** | Humano revisando o que o modelo **previu** = **A2I** |
| #58 **Rotular** imagens médicas no S3, proteger dados de pacientes, pouco esforço manual e custo baixo | Data Wrangler | **Ground Truth com força de trabalho privada** | **Rotular** dados de treino = **Ground Truth**. Dado sensível = equipe **privada**. Data Wrangler **prepara** dados, não rotula |

> [!tip] Regra de bolso: humanos no ciclo de ML
> | Momento | Serviço | Palavra-chave |
> |---|---|---|
> | **Antes** do treino: criar rótulos | **Ground Truth** (self-service; workforce privada, terceirizada ou Mechanical Turk) | "rotular", "anotar", "labeling" |
> | Antes do treino, **totalmente gerenciado** por especialistas da AWS | **Ground Truth Plus** | "sem gerenciar rotuladores", "máxima precisão da anotação" |
> | **Depois** do deploy: revisar **predições** | **Augmented AI (A2I)** | "revisão humana", "baixa confiança", "auditoria das predições" |
> | Preparar e transformar dados | **Data Wrangler** | "limpar", "transformar", "feature engineering" |

Revisar: [[13 - Amazon Augmented AI|Amazon Augmented AI]] · [[04 - SageMaker - Models and Humans|SageMaker - Models and Humans]] · [[03 - SageMaker - Data Tools|SageMaker - Data Tools]]

### 2. Amazon Lex e serviços ao redor (2 erros: #28, #39) ⚠️

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #28 Chatbot do Lex precisa **autenticar usuários** e manter dados de sessão com segurança | IAM | **Amazon Cognito** | **Usuário final** do app (login, cadastro, tokens) = **Cognito**. IAM = permissões de identidades **da AWS** nos recursos |
| #39 Manter contexto **e registrar cada interação** para análise posterior (Escolha 2) | Atributos de sessão ✅ + **Kinesis** | Atributos de sessão + **CloudWatch Logs** | **Conversation logs** do Lex vão para **CloudWatch Logs** (texto) ou **S3** (áudio). Kinesis é streaming em tempo real, que não foi pedido |

> [!note] Cognito "fora do escopo"
> A nota [[01 - Segurança, Identidade e Compliance|Segurança, Identidade e Compliance]] lista o **Cognito** como fora do escopo do exame, mas ele **caiu aqui**. Guarde ao menos a regra: **login de usuário final = Cognito**.

Revisar: [[06 - Amazon Lex|Amazon Lex]] · [[01 - Segurança, Identidade e Compliance|Segurança, Identidade e Compliance]]

### 3. Implantação e parâmetros de inferência (2 erros: #6, #40) ⚠️

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #6 Vantagem do **top-k** | Escolha aleatória em **todo o vocabulário** | Só os **k** mais prováveis: diversidade controlada | Top-k = **K candidatos**. Top-p = soma de probabilidade até **P**. Greedy = sempre o mais provável |
| #40 Inferência **em tempo real** no hardware do sensor | API central + endpoint **assíncrono** | **SLM** otimizado **no dispositivo** | Edge + latência mínima = modelo **pequeno** rodando **local** |

> [!tip] Tipos de inferência
> | Requisito | Opção |
> |---|---|
> | Resposta imediata, tráfego constante | Endpoint **em tempo real** |
> | Payload grande ou processamento longo, pode esperar | Endpoint **assíncrono** |
> | Tráfego intermitente, pagar só pelo uso | **Serverless** |
> | Lote grande de dados, sem pressa | **Batch transform** |
> | Sem internet ou latência mínima no dispositivo | **Edge** (modelo pequeno/SLM local) |

Revisar: [[05 - Parâmetros de Inferência|Parâmetros de Inferência]] · [[04 - ML Inference#Inferência na borda (*edge*)]]

### 4. IA Responsável: quais ferramentas (1 erro: #32)

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #32 Serviços para implementar **IA Responsável** (Escolha 2) | Clarify ✅ + **Audit Manager** | Clarify + **SageMaker Model Monitor** | Ferramentas de IA Responsável: **Clarify** (viés/explicabilidade), **Model Monitor** (drift/qualidade), **A2I**, **Model Cards**, **Guardrails**. Audit Manager = **evidências de auditoria** da conta |

Revisar: [[03 - IA Responsável - Serviços AWS|IA Responsável - Serviços AWS]] · [[06 - SageMaker - Governança e Segurança|SageMaker - Governança e Segurança]]

### 5. Escolha do serviço de IA (1 erro: #44)

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #44 Extrair informações de documentos **escaneados e digitais** de projetos de energia (Escolha 3) | Comprehend ✅ + Textract ✅ + **Personalize** | Comprehend + Textract + **chatbot de sumarização com IA generativa** | **Personalize** = **recomendação**. Nada a ver com documentos |

Revisar: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · [[08 - Amazon Textract|Amazon Textract]] · [[10 - Amazon Personalize|Amazon Personalize]]

### 6. Generativo x discriminativo (1 erro: #27)

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #27 Modelo **generativo** aprendeu orelhas, olhos e caudas de animais. O que ele faz? | Classificar espécies | **Criar imagens novas** de animais que não estavam no treino | **Generativo** = cria conteúdo novo. **Classificar** = modelo **discriminativo** |

Revisar: [[10 - O que é IA Generativa|O que é IA Generativa]]

---

## 🔁 Reforço: 10 questões nos pontos fracos

### R1
Um banco quer que **analistas humanos revisem** as predições de fraude quando a **confiança do modelo for menor que 80%**. Qual serviço usar?

- [ ] A) SageMaker Ground Truth
- [ ] B) Amazon Augmented AI (A2I)
- [ ] C) SageMaker Data Wrangler
- [ ] D) SageMaker Clarify

> [!success]- Gabarito
> **B.** Revisão humana de **predições** = **A2I**. Ground Truth é para **rotular** dados de treino.

### R2
Um hospital precisa **rotular 50 mil raios-X** para treinar um modelo e **não pode** expor os dados a pessoas de fora. Qual a melhor opção?

- [ ] A) Ground Truth com força de trabalho do Mechanical Turk
- [ ] B) Ground Truth com força de trabalho privada
- [ ] C) Amazon A2I
- [ ] D) Data Wrangler

> [!success]- Gabarito
> **B.** Rotular = **Ground Truth**. Dados sensíveis = equipe **privada** (Mechanical Turk é público).

### R3
Uma empresa quer rotular imagens com **máxima precisão** e **sem gerenciar** nenhum rotulador nem fluxo de trabalho. Qual serviço?

- [ ] A) SageMaker Ground Truth Plus
- [ ] B) SageMaker Ground Truth com equipe interna
- [ ] C) Amazon Rekognition Custom Labels
- [ ] D) Amazon A2I

> [!success]- Gabarito
> **A.** **Ground Truth Plus** = rotulagem **totalmente gerenciada** por especialistas, com controle de qualidade incluído.

### R4
Um app de delivery usa um chatbot no **Amazon Lex**. Os clientes precisam **fazer login** antes de consultar pedidos. Qual serviço gerencia o login?

- [ ] A) AWS IAM
- [ ] B) Amazon Cognito
- [ ] C) AWS Secrets Manager
- [ ] D) AWS IAM Identity Center

> [!success]- Gabarito
> **B.** Usuário **final** de app = **Cognito**. IAM e Identity Center são para identidades **da AWS** e funcionários.

### R5
A equipe quer **guardar todas as conversas** do chatbot do Lex para analisar depois e melhorar as intenções. O que configurar?

- [ ] A) Kinesis Data Streams
- [ ] B) Conversation logs do Lex no CloudWatch Logs
- [ ] C) AWS CloudTrail
- [ ] D) Amazon Personalize

> [!success]- Gabarito
> **B.** Os conversation logs vão para o **CloudWatch Logs** (texto) ou **S3** (áudio). O CloudTrail registra **chamadas de API**, não o conteúdo das conversas.

### R6
Com **top-k = 5**, o modelo:

- [ ] A) Sempre escolhe o token mais provável
- [ ] B) Sorteia o próximo token entre os 5 mais prováveis
- [ ] C) Considera tokens até a probabilidade somada chegar a 5%
- [ ] D) Pode escolher qualquer token do vocabulário

> [!success]- Gabarito
> **B.** A descreve **greedy**; C lembra **top-p**; D é **sem truncamento**.

### R7
Uma câmera de inspeção numa fábrica **sem internet estável** precisa detectar defeitos em **milissegundos**. Qual abordagem?

- [ ] A) Endpoint assíncrono no SageMaker
- [ ] B) Batch transform a cada hora
- [ ] C) Modelo pequeno e otimizado rodando no próprio dispositivo (edge)
- [ ] D) Chamar um LLM grande no Bedrock

> [!success]- Gabarito
> **C.** Sem rede + latência mínima = **inferência local na borda**.

### R8 (Escolha 2)
Quais serviços ajudam a **monitorar viés e qualidade** de um modelo **em produção**, como parte de IA Responsável?

- [ ] A) SageMaker Clarify
- [ ] B) AWS Audit Manager
- [ ] C) SageMaker Model Monitor
- [ ] D) AWS Artifact

> [!success]- Gabarito
> **A e C.** Clarify = viés e explicabilidade; Model Monitor = drift e qualidade contínuos. Audit Manager e Artifact são de **conformidade/auditoria**.

### R9
Um e-commerce quer mostrar **"clientes que compraram isso também compraram"**. Qual serviço?

- [ ] A) Amazon Textract
- [ ] B) Amazon Comprehend
- [ ] C) Amazon Personalize
- [ ] D) Amazon Kendra

> [!success]- Gabarito
> **C.** **Personalize** = recomendação. (Para lembrar por que ele **não** servia na #44.)

### R10
Um modelo foi treinado com milhares de fotos de rostos e agora **cria rostos que não existem**. Que tipo de modelo é esse?

- [ ] A) Discriminativo
- [ ] B) Generativo
- [ ] C) De regressão
- [ ] D) De clustering

> [!success]- Gabarito
> **B.** Criar conteúdo **novo** = **generativo**. Discriminativo **classifica** o que já existe.

**Resultado do reforço:** ___ / 10 (meta: 9+)

---

## Plano até o Simulado 4

| Dia | Foco | Notas |
|---|---|---|
| 1 | Humanos no ciclo de ML: Ground Truth, Ground Truth Plus, A2I e Data Wrangler + R1–R3 | [[13 - Amazon Augmented AI\|Amazon Augmented AI]] · [[04 - SageMaker - Models and Humans\|SageMaker - Models and Humans]] |
| 2 | Lex + Cognito + CloudWatch Logs; tabela "qual serviço de IA faz o quê" + R4, R5 e R9 | [[06 - Amazon Lex\|Amazon Lex]] · [[00 - Resumo - Serviços de IA\|Resumo - Serviços de IA]] |
| 3 | Parâmetros de inferência (de novo) + tipos de inferência e edge + R6 e R7 | [[05 - Parâmetros de Inferência\|Parâmetros de Inferência]] · [[04 - ML Inference\|ML Inference]] |
| 4 | Ferramentas de IA Responsável x governança (Clarify, Model Monitor, Model Cards, Audit Manager, Config) + R8 | [[03 - IA Responsável - Serviços AWS\|IA Responsável - Serviços AWS]] · [[02 - Gerenciamento e Governança\|Gerenciamento e Governança]] |
| 5 | **Simulado 4** com meta de **85%+** e primeira passada em ~70 min | — |

## Histórico de simulados

| Data | Simulado | Tentativa | Nota | Pior domínio |
|---|---|---|---|---|
| 2026-11-12 | Udemy Simulado 1 | 2 | 44/65 (68%) | Segurança (44%) · Fundamentos IA/ML (54%) |
| 2026-11-12 | Udemy Simulado 2 | 1 | 50/65 (76%) ✅ | IA Responsável (67%) · Aplicações de FMs (72%) |
| 2026-11-13 | Udemy Simulado 3 | 1 | **56/65 (86%)** ✅ | Fundamentos IA/ML (77%) · IA Responsável (78%) |
| 2026-11-14 | Udemy Simulado 4 | 1 | **46/65 (70%)** ⚠️ | Segurança (44%) · IA Responsável (44%) → [[04 - Udemy Simulado 4 - Tentativa 1 - Análise e Reforço\|Udemy Simulado 4 - Tentativa 1 - Análise e Reforço]] |
|  |  |  |  |  |

---
Anterior: [[02 - Udemy Simulado 2 - Tentativa 1 - Análise e Reforço|Udemy Simulado 2 - Tentativa 1 - Análise e Reforço]] · Próximo: [[04 - Udemy Simulado 4 - Tentativa 1 - Análise e Reforço|Udemy Simulado 4 - Tentativa 1 - Análise e Reforço]] · Início: [[00 - Início - Guia do Exame]] · Checklist: [[09 - Checklist de Estudo]]
