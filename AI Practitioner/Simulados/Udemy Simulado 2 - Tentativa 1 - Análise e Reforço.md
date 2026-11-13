## Resumo

Análise da **Tentativa 1 do Simulado 2** (Udemy · *[Simulados] AWS Certified AI Practitioner AIF-C01 PT-BR*), feita em 2026-11-12. Tempo usado: **1h26** de 1h30.

> [!success] Placar: **50 / 65 (76%)**: aprovado ✅
> Subiu **8 pontos** em relação ao Simulado 1 (68%). Você passou a faixa de aprovação (70%), mas a meta de folga é **80%+** (52 acertos), porque a prova real tem questões mais longas e pegadinhas novas.
> ⏱️ Usou **96% do tempo**: no próximo, tente terminar a primeira passada em **~70 min** e use o resto para revisar as marcadas.

## Evolução por domínio

| Domínio | Peso | Simulado 1 | **Simulado 2** | Tendência |
|---|---|---|---|---|
| 5. Segurança, Compliance e Governança | 14% | 44% | **89%** (8/9) | 🚀 +45 (o reforço funcionou) |
| 2. Fundamentos de IA Generativa | 24% | 94% | **81%** (13/16) | 🔻 −13 |
| 1. Fundamentos de IA e ML | 20% | 54% | **77%** (10/13) | ⬆️ +23 |
| 3. Aplicações de Foundation Models | **28%** | 67% | **72%** (13/18) | ⬆️ +5 (ainda o que mais perde pontos) |
| 4. IA Responsável | 14% | 67% | **67%** (6/9) | ➖ **parado**: prioridade |

> [!warning] O que os dois simulados mostram juntos
> 1. **IA Responsável** ficou em 67% nos dois. O ponto fraco agora é **mitigar viés** (o que fazer), não mais identificar os serviços.
> 2. **"Ajustar parâmetro" como solução errada** apareceu **4 vezes** em dois simulados (#2 do S1; #30, #32 e #42 do S2). Veja o tema 1.
> 3. **Alucinação → RAG**: você errou essa ideia **duas vezes** (S1 #2 com tokens, S2 #30 com temperatura).

## Mapa dos erros por tema

### 1. Parâmetros de inferência não resolvem fatos nem custo (3 erros: #30, #32, #42) 🔴

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #30 Recomendação de **dosagem** inventa combinações, e o modelo precisa lidar com **condições raras** | Temperatura 0,1 | **RAG** com base curada de interações medicamentosas | Temperatura baixa deixa o modelo **previsível**, não **correto**. Fatos → **RAG** |
| #32 Manter os **10 exemplos** no prompt e **reduzir custo** | Reduzir **Top-P** | **Reduzir tokens de entrada** | O custo é **por token**. Top-P muda a **diversidade**, não o preço |
| #42 O que o **Top P** faz | "Probabilidade de escolher saídas de menor probabilidade" | "**Percentual** dos candidatos mais prováveis considerados para o próximo token" | Top P = **probabilidade acumulada** do conjunto de candidatos (*nucleus*) |

> [!tip] Regra de bolso: qual alavanca resolve o quê
> | Problema | Alavanca certa | Não é |
> |---|---|---|
> | Inventa fatos / alucina | **RAG**, grounding check, revisão humana | temperatura, tokens, top-P |
> | Custo alto | **Menos tokens** (prompt menor, resposta menor), modelo menor, batch, prompt caching | top-P, temperatura |
> | Resposta muito "criativa" ou variada | **Temperatura / Top-P / Top-K** mais baixos | RAG |
> | Resposta longa demais | **Max tokens** | temperatura |
> | Formato ou tom errado | **Prompt** (instruções, exemplos) | fine-tuning (exagero) |
>
> **Top-P** = pega os candidatos mais prováveis até somar P (ex.: 0,9 = 90% de probabilidade). **Top-K** = pega os **K** mais prováveis. **Temperatura** = achata ou acentua as probabilidades.

Revisar: [[Parâmetros de Inferência]] · [[Beadrock Rag - Kb]] · [[Gestão Financeira#Modelos de preço de IA que caem na prova]]

### 2. Fundamentos de ML e GenAI (5 erros: #5, #6, #15, #17, #65) ⚠️

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #5 As 2 etapas do **modelo de difusão** | Difusão direta + **geração autorregressiva** | Difusão **direta** + difusão **reversa** | Direta = **adiciona** ruído (treino). Reversa = **remove** ruído (geração). Autorregressivo é **LLM** |
| #6 Trade-off **viés x variância** | Opção com os nomes **trocados** ("capturar ruído = bias") | Viés = suposições **simplistas** → underfitting; variância = **sensibilidade** aos dados → overfitting | Capturar **ruído** é **variância** |
| #15 Treino, validação e teste (Escolha 2) | "Teste ajusta hiperparâmetros" + "validação mede generalização" | **Validação é opcional** + **teste mede generalização** | Validação → hiperparâmetros (opcional). Teste → nota final |
| #17 Como os **FMs** aprendem | Supervisionado no pré-treino e no fine-tuning | **Auto-supervisionado** no pré-treino; **supervisionado** no fine-tuning | O próprio texto gera o rótulo (prever a próxima palavra) |
| #65 Exemplos de **semissupervisionado** (Escolha 2) | Fraude ✅ + **Rede neural** | Fraude + **Análise de sentimento** | Rede neural é **arquitetura**, não paradigma de aprendizado |

> [!note] Inconsistência entre os simulados
> No **Simulado 1 (#30)**, "rede neural" foi aceita como exemplo de **supervisionado**; no **Simulado 2 (#65)**, foi rejeitada como "arquitetura, não paradigma". Na prova real, prefira a leitura do S2: **rede neural é uma arquitetura** que pode ser usada em **qualquer** paradigma. Só escolha "rede neural" se nenhuma alternativa for um paradigma/tarefa mais claro.

Revisar (conteúdo **novo** adicionado hoje):
- Difusão → [[O que é  Generative IA#As duas etapas do modelo de difusão (cai na prova)]]
- Treino/validação/teste → [[Aprendizado Supervisionado]]
- Viés x variância → [[IA Responsável - Conceitos e Riscos#4. Viés x variância]]
- Auto e semissupervisionado → [[Diferenças entre os Tipos de Aprendizado]]

### 3. IA Responsável: como mitigar viés (3 erros: #25, #35, #61) 🔴

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #25 Testar viés de um LLM **continuamente** com **pouco trabalho administrativo** | Benchmarking com **revisores humanos** | **Datasets de benchmark** prontos para viés | "Pouco esforço + padronizado" → benchmark. Humanos = caro e lento |
| #35 Modelo trata **idosos** de forma desigual | **Remover** os atributos de idade | **Métricas de equidade** + **reponderar** grupos sub-representados | Remover o atributo não resolve (**proxies**) e impede **medir** |
| #61 Dataset sem diversidade de produtores | **Regularização** | **Aumento de dados** para os grupos sub-representados | Regularização é para **overfitting**, não para **desbalanceamento** |

Revisar (conteúdo **novo**): [[IA Responsável - Conceitos e Riscos#Como corrigir viés e desbalanceamento nos dados]]

### 4. Bedrock e assistentes (2 erros: #22, #52) ⚠️

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #22 Técnicas que o **Amazon Q Business** usa (Escolha 2) | RAG ✅ + **GAN** | RAG + **LLM** | Q Business = **LLM + RAG** sobre os dados da empresa. GAN gera **imagens** |
| #52 Para que serve um **action group** | "Especificar manualmente cada etapa" | **Definir as tarefas e chamadas de API** que o agente pode executar | O agente **planeja sozinho**; o action group só diz **o que ele pode fazer** (OpenAPI + Lambda) |

Revisar: [[Amazon Q]] · [[Bedrock Agents]]

### 5. Prompting (1 erro: #45)

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #45 Conteúdo deve **excluir** marcas concorrentes e temas sensíveis | Few-shot | **Prompting negativo** | "Não mencione / evite / exclua" = **negativo**. Few-shot = **dar exemplos** |

Revisar: [[Tipos de Prompt]] · [[Anatomia de um Prompt]]

### 6. Governança (1 erro: #41)

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #41 Monitorar **continuamente**, **rastrear mudanças de configuração** e verificar conformidade | Audit Manager | **AWS Config** | "**Configuração** + **mudanças** + regras" = Config. Audit Manager = **evidências para auditoria** |

> No Simulado 1 a resposta era Audit Manager porque o cenário falava em **coletar evidências**. Aqui fala em **alterações de configuração**. A palavra-chave decide.

Revisar: [[Gerenciamento e Governança#Os 5 lado a lado]]

---

## 🔁 Reforço: 12 questões nos pontos fracos

### R1
Um chatbot de seguros **inventa coberturas** que não existem na apólice. A equipe propõe **reduzir a temperatura para 0**. O que acontece?

- [ ] A) Resolve, porque o modelo fica determinístico e passa a dizer a verdade
- [ ] B) Não resolve: o modelo fica previsível, mas continua sem acesso às apólices. O certo é RAG com as apólices
- [ ] C) Resolve, se também reduzir o Top-K
- [ ] D) Não resolve; o certo é aumentar o max tokens

> [!success]- Gabarito
> **B.** Temperatura controla **aleatoriedade**, não **veracidade**. Fatos vêm de **RAG** (grounding).

### R2
Um app envia **um prompt de 8.000 tokens** com o manual inteiro em toda chamada e a conta do Bedrock disparou. O que reduz o custo **sem perder qualidade**?

- [ ] A) Reduzir o Top-P para 0,5
- [ ] B) Aumentar a temperatura
- [ ] C) Usar RAG para enviar só os trechos relevantes do manual (menos tokens de entrada)
- [ ] D) Trocar para Provisioned Throughput sem compromisso

> [!success]- Gabarito
> **C.** Custo = **tokens**. RAG manda só o necessário. Top-P e temperatura não mudam o preço.

### R3
Com **Top-P = 0,9**, o modelo:

- [ ] A) Escolhe sempre o token com 90% de probabilidade
- [ ] B) Considera só os 9 tokens mais prováveis
- [ ] C) Considera o menor conjunto de tokens mais prováveis cuja probabilidade somada chega a 90%
- [ ] D) Gera respostas com 90% do tamanho máximo

> [!success]- Gabarito
> **C.** Top-P = probabilidade **acumulada** (*nucleus sampling*). "9 tokens" seria Top-K = 9.

### R4 (Escolha 2)
Sobre **modelos de difusão**, quais afirmações estão corretas?

- [ ] A) Na difusão direta, o modelo adiciona ruído às imagens de treino
- [ ] B) Geram imagens prevendo o próximo token de forma autorregressiva
- [ ] C) Na difusão reversa, o modelo parte do ruído e o remove passo a passo para criar a imagem
- [ ] D) Usam um gerador e um discriminador que competem entre si

> [!success]- Gabarito
> **A e C.** B descreve **LLMs**; D descreve **GANs**.

### R5
O time ajustou a taxa de aprendizado olhando o desempenho no **conjunto de teste** até ficar ótimo. Qual o problema?

- [ ] A) Nenhum, é o uso correto do teste
- [ ] B) O teste "vazou" para o ajuste; a nota final ficou otimista. Hiperparâmetros devem ser ajustados com a validação
- [ ] C) O conjunto de treino ficou pequeno demais
- [ ] D) Deveriam ter usado o teste para treinar também

> [!success]- Gabarito
> **B.** **Validação** ajusta hiperparâmetros; **teste** só mede a generalização no final.

### R6
Durante o **pré-treino** de um LLM, o modelo esconde a próxima palavra e tenta adivinhá-la, sem rótulos humanos. Que tipo de aprendizado é esse?

- [ ] A) Supervisionado
- [ ] B) Por reforço
- [ ] C) Auto-supervisionado
- [ ] D) Não supervisionado com clustering

> [!success]- Gabarito
> **C.** O próprio dado gera o rótulo. O **fine-tuning** depois é **supervisionado** (pares prompt → resposta).

### R7
Um modelo de crédito trata pior **mulheres**. A gerente propõe **apagar a coluna "gênero"**. Qual a melhor resposta segundo IA Responsável?

- [ ] A) Concordar: sem a coluna não há viés
- [ ] B) Manter a coluna para medir o viés por grupo com métricas de equidade e corrigir com reponderação/reequilíbrio dos dados
- [ ] C) Aplicar regularização L2
- [ ] D) Aumentar a temperatura do modelo

> [!success]- Gabarito
> **B.** Outras colunas funcionam como **proxy** do gênero; sem a coluna você nem consegue **medir**. Mede (Clarify / subgrupo) → corrige (reponderar, aumentar dados).

### R8
O dataset de um gerador de imagens tem **poucas fotos de pessoas idosas**. Como corrigir?

- [ ] A) Aumentar os dados (coletar ou gerar exemplos) do grupo sub-representado
- [ ] B) Aplicar regularização
- [ ] C) Reduzir o número de épocas
- [ ] D) Remover as fotos de idosos

> [!success]- Gabarito
> **A.** Desbalanceamento → **aumento de dados / reamostragem / reponderação**. Regularização é para overfitting.

### R9
Uma empresa quer verificar **toda semana**, sem montar equipe, se seu LLM produz **estereótipos**. Qual abordagem?

- [ ] A) Contratar revisores humanos para ler as respostas
- [ ] B) Rodar avaliação automática com datasets de benchmark de viés (ex.: CrowS-Pairs no FMEval / Bedrock Evaluations)
- [ ] C) Usar o CloudTrail
- [ ] D) Fazer fine-tuning semanal

> [!success]- Gabarito
> **B.** Benchmark pronto = **padronizado, repetível e barato**. Humanos para critérios subjetivos.

### R10
Num agente do Bedrock, a equipe quer que ele possa **consultar o status de um pedido** no ERP. O que configurar?

- [ ] A) Um action group com o schema da API do ERP e uma função Lambda
- [ ] B) Uma Knowledge Base com os PDFs do ERP
- [ ] C) Um Guardrail com denied topics
- [ ] D) Um prompt com todos os passos que o agente deve seguir

> [!success]- Gabarito
> **A.** Action group = **o que o agente pode fazer** (APIs). Knowledge Base = **o que ele pode consultar** em documentos.

### R11
Um prompt de marketing diz: "**Não** cite preços, **não** mencione concorrentes e **evite** gírias." Que técnica é essa?

- [ ] A) Few-shot
- [ ] B) Chain-of-thought
- [ ] C) Prompting negativo
- [ ] D) Zero-shot com role prompting

> [!success]- Gabarito
> **C.** Instruções sobre o que **evitar** = **negativo**.

### R12
A equipe precisa saber **quando** alguém **desativou a criptografia** de um bucket com dados de treino e receber **alerta** se a regra for violada de novo.

- [ ] A) AWS Audit Manager
- [ ] B) AWS Config
- [ ] C) AWS Artifact
- [ ] D) Amazon Macie

> [!success]- Gabarito
> **B) Config**: histórico de **configuração** + **regras** de conformidade. (Quem fez a chamada de API também aparece no **CloudTrail**.)

**Resultado do reforço:** ___ / 12 (meta: 11+)

---

## Plano até o Simulado 3

| Dia | Foco | Notas |
|---|---|---|
| 1 | Tabela "qual alavanca resolve o quê" + R1–R3 | [[Parâmetros de Inferência]] · [[Beadrock Rag - Kb]] |
| 2 | Mitigação de viés + R7–R9 + [[IA Responsável - Formulário de Respostas]] | [[IA Responsável - Conceitos e Riscos]] |
| 3 | Fundamentos: difusão, treino/validação/teste, auto/semissupervisionado + R4–R6 | [[O que é  Generative IA]] · [[Aprendizado Supervisionado]] · [[Diferenças entre os Tipos de Aprendizado]] |
| 4 | Serviços novos da lista oficial (Nova, AgentCore, Lambda, bancos vetoriais) | [[07 - Serviços AWS do Exame]] |
| 5 | **Simulado 3** com meta de **80%** e primeira passada em ~70 min | — |

## Histórico de simulados

| Data | Simulado | Tentativa | Nota | Pior domínio |
|---|---|---|---|---|
| 2026-11-12 | Udemy Simulado 1 | 2 | 44/65 (68%) | Segurança (44%) · Fundamentos IA/ML (54%) |
| 2026-11-12 | Udemy Simulado 2 | 1 | **50/65 (76%)** ✅ | IA Responsável (67%) · Aplicações de FMs (72%) |
|  |  |  |  |  |

---
Anterior: [[Udemy Simulado 1 - Tentativa 2 - Análise e Reforço]] · Início: [[00 - Início - Guia do Exame]] · Checklist: [[09 - Checklist de Estudo]]
