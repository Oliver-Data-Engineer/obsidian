## Resumo

Os **serviços e ferramentas AWS** ligados ao Domínio 4, agrupados pelo que resolvem: **proteger em tempo real**, **detectar e monitorar viés**, **colocar humanos no loop** e **dar transparência / avaliar**.

> [!info] Ideia central
> - **Guardrails** → protege a **conversa** (entrada e saída do FM) em tempo real.
> - **Clarify** → mede **viés** e **explica** previsões (análise).
> - **Model Monitor** → vigia o modelo **em produção** (drift).
> - **A2I / Ground Truth** → **humanos** revisando previsões / rotulando dados.
> - **Model Cards / AI Service Cards / Bedrock Evaluations** → **documentar e avaliar**.

## Visão geral

| Serviço | Grupo | Para quê | Fase |
|---|---|---|---|
| **Amazon Bedrock Guardrails** | Proteger | Filtrar conteúdo nocivo, tópicos negados, PII, alucinação | Produção (runtime) |
| **SageMaker Clarify** | Detectar viés / explicar | Viés pré e pós-treino, SHAP, avaliação de FM | Dados, treino, produção |
| **SageMaker Model Monitor** | Monitorar | Drift de dados, qualidade, **viés** e atribuição de features | Produção |
| **Amazon A2I** | Humano no loop | Revisão humana de **previsões** com baixa confiança | Produção |
| **SageMaker Ground Truth** | Humano no loop | **Rotulagem** de dados, RLHF, auditoria de rótulos | Dados / treino |
| **SageMaker Model Cards** | Transparência | Documentar **seu** modelo | Governança |
| **AWS AI Service Cards** | Transparência | Documentação dos **serviços/modelos da AWS** | Escolha do serviço |
| **Amazon Bedrock Evaluations** | Avaliar | Comparar FMs e RAG (automática, humana, LLM-as-a-judge) | Escolha / validação |
| **fmeval** | Avaliar | Biblioteca open source de avaliação de FMs (base do Clarify FM eval) | Validação |
| **Well-Architected Responsible AI Lens** | Boas práticas | Guia para **projetar e operar** IA responsável | Todo o ciclo |

---

## Proteger em tempo real

### Amazon Bedrock Guardrails
Detalhado em [[07 - Bedrock Guardrails|Bedrock Guardrails]]. Resumo das políticas:

| Política | Resolve | Dimensão |
|---|---|---|
| **Content filters** | Ódio, insultos, sexual, violência, má conduta, **ataques de prompt** (texto e imagem) | Safety |
| **Denied topics** | Tópicos proibidos ("não dê conselho de investimento") | Safety / controlabilidade |
| **Word filters** | Palavras e palavrões específicos, nomes de concorrentes | Safety |
| **Sensitive information filters** | Detectar e **bloquear ou mascarar PII** (CPF, cartão, e-mail) e regex | Privacidade |
| **Contextual grounding check** | Resposta **não suportada** pela fonte ou **irrelevante** → reduz alucinação em RAG | Veracidade |
| **Automated Reasoning checks** | Valida a resposta com **lógica formal** contra regras definidas | Veracidade |

- Funciona com **qualquer FM** (inclusive fora do Bedrock via API `ApplyGuardrail`).
- Aplica-se ao **prompt (entrada)** e à **resposta (saída)**.

---

## Detectar e monitorar viés

O guia cita três **práticas** (não serviços): **análise da qualidade dos rótulos**, **auditorias humanas** e **análise por subgrupo**. Na AWS elas viram:

| Prática do guia | Como fazer na AWS |
|---|---|
| **Analisar qualidade dos rótulos** | **Ground Truth** com vários anotadores e consolidação; Clarify **DPL** (proporção de rótulos positivos por grupo) |
| **Auditorias humanas** | **A2I** (revisão de previsões), **Ground Truth**, avaliação humana no **Bedrock Evaluations** |
| **Análise por subgrupo** | Clarify (métricas por **facet**), Model Monitor (bias drift), métricas separadas por grupo |

### SageMaker Clarify
Detalhado em [[04 - SageMaker - Models and Humans#1. SageMaker Clarify]].

| Função | O que faz |
|---|---|
| **Viés pré-treino** | Analisa o **dataset** antes de treinar (não depende do modelo) |
| **Viés pós-treino** | Analisa as **previsões** do modelo treinado por grupo |
| **Explicabilidade** | **SHAP** (importância de cada feature, local e global) e **PDP** (*partial dependence plots*) |
| **Avaliação de FM** | Acurácia, robustez, toxicidade, estereótipos (via **fmeval**) |

Métricas de viés pré-treino que valem conhecer pelo nome:

| Sigla | Nome | Pergunta |
|---|---|---|
| **CI** | *Class Imbalance* | Um grupo (facet) tem **muito menos exemplos** que o outro? |
| **DPL** | *Difference in Proportions of Labels* | Um grupo tem **mais rótulos positivos** (ex.: aprovado) que o outro? |
| **KL / JS** | Divergência Kullback-Leibler / Jensen-Shannon | As **distribuições** de resultados dos grupos são diferentes? |
| **CDD** | *Conditional Demographic Disparity* | Há disparidade também **dentro de subgrupos**? |

> **Facet** = o atributo sensível analisado (idade, gênero, raça...).

> [!warning] Situação atual do Clarify (2026)
> A AWS informa que o **SageMaker Clarify não está mais aberto a novos clientes**: quem já usa continua normalmente, mas não haverá novos recursos. Substitutos indicados: métricas de viés calculadas direto (pandas/scikit-learn), biblioteca **SHAP**, **SageMaker MLflow**, **fmeval** e **Amazon Bedrock Evaluations / Guardrails** (para FMs).
> **Para a prova:** o banco de questões ainda trata o **Clarify como a resposta** para "detectar viés" e "explicar previsões". Estude-o assim.

### SageMaker Model Monitor
- Monitora endpoints em **produção** e gera alertas (CloudWatch).
- 4 tipos: **qualidade dos dados**, **qualidade do modelo**, **bias drift** e **feature attribution drift** (os dois últimos usam o Clarify).
- Palavra-chave: "**ao longo do tempo**", "**em produção**", "**drift**".

---

## Humanos no loop

| | **SageMaker Ground Truth** | **Amazon A2I** |
|---|---|---|
| Quando | **Antes** do treino | **Depois**, com o modelo em produção |
| O que o humano faz | **Rotula** dados (e ranqueia respostas para **RLHF**) | **Revisa previsões** com baixa confiança ou por amostragem |
| Força de trabalho | Mechanical Turk, fornecedores, equipe própria | Mesmas opções |
| Integra com | Treino de modelos | Textract, Rekognition, modelos próprios |

Detalhes: [[13 - Amazon Augmented AI|Amazon Augmented AI]] · [[04 - SageMaker - Models and Humans|SageMaker - Models and Humans]].

---

## Transparência e avaliação

### SageMaker Model Cards x AWS AI Service Cards

| | **SageMaker Model Cards** | **AWS AI Service Cards** |
|---|---|---|
| Documenta | **O seu** modelo (que você treinou) | **Serviços e modelos da AWS** (Rekognition, Polly, Textract, Nova, Guardrails...) |
| Quem escreve | **Você** | **A AWS** |
| Conteúdo | Uso pretendido, nível de risco, dados de treino, métricas, resultados de viés | Casos de uso pretendidos, **limitações**, escolhas de design de IA responsável, boas práticas de desempenho |

> [!tip] Dica para lembrar
> "**Model** Card = **meu** modelo." "**Service** Card = **serviço** da AWS."

### Amazon Bedrock Evaluations

| Tipo | Como funciona | Quando usar |
|---|---|---|
| **Automática (programática)** | Métricas prontas: **acurácia, robustez, toxicidade**; datasets **embutidos** ou seus | Comparar FMs rápido e barato |
| **Humana** | Sua equipe ou especialistas avaliam e dão preferências | Critérios **subjetivos**: tom, empatia, voz da marca |
| **LLM-as-a-judge** | Um segundo LLM dá nota e **explica** cada resposta | Qualidade "humana" em **escala**, mais barato que humanos |
| **Avaliação de RAG** | Mede se a Knowledge Base **recupera** o trecho certo e gera resposta correta (precisa de *ground truth*) | Validar um sistema RAG |

### Well-Architected Responsible AI Lens
- Lente do **AWS Well-Architected** (lançada em nov/2025) com **boas práticas** para projetar, desenvolver e operar IA responsável.
- Organizada em **focus areas** ligadas às fases do ciclo de vida, começando por **"descrever o caso de uso"** (validar se precisa mesmo de IA, identificar partes interessadas).
- Não confundir com a **Generative AI Lens** (arquitetura de GenAI em geral).

---

## Pares que confundem

| Se a questão diz... | É... | Não é... |
|---|---|---|
| "bloquear resposta ofensiva **na hora**" | Guardrails | Clarify |
| "medir viés do **dataset**" | Clarify | Guardrails |
| "viés **piorando** em produção" | Model Monitor | Clarify (pontual) |
| "pessoa **revisa a previsão**" | A2I | Ground Truth |
| "pessoa **rotula dados**" | Ground Truth | A2I |
| "documentar **meu** modelo" | Model Cards | AI Service Cards |
| "limitações do **Rekognition**" | AI Service Cards | Model Cards |
| "comparar FMs em toxicidade" | Bedrock Evaluations | Model Monitor |

## Exemplo para Associação Mental

**O estádio de futebol.** O **Guardrails** é o **segurança na catraca**: revista quem entra e o que sai. O **Clarify** é o **VAR**: analisa o lance e explica por que foi falta. O **Model Monitor** é o **olheiro** que acompanha o time a temporada inteira e avisa quando o desempenho cai. O **A2I** é o **árbitro** chamado quando o VAR fica em dúvida. O **Ground Truth** são os **professores da escolinha** que ensinam os jogadores. O **Model Card** é a **ficha técnica** do seu jogador; o **AI Service Card** é a ficha que a **federação** (AWS) publica dos jogadores dela. O **Bedrock Evaluations** é a **peneira** que compara candidatos.

---
Voltar: [[00 - Índice - IA Responsável|Índice - IA Responsável]] · Anterior: [[02 - IA Responsável - Transparência e Explicabilidade|IA Responsável - Transparência e Explicabilidade]] · Próximo: [[04 - IA Responsável - Formulário de Respostas|IA Responsável - Formulário de Respostas]]

Fontes: [AWS Responsible AI](https://aws.amazon.com/ai/responsible-ai/) · [AWS AI Service Cards](https://aws.amazon.com/ai/responsible-ai/resources/) · [Clarify availability change](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-availability-change.html) · [Clarify – métricas de viés pré-treino](https://docs.aws.amazon.com/sagemaker/latest/dg/clarify-measure-data-bias.html) · [Amazon Bedrock Evaluations](https://docs.aws.amazon.com/bedrock/latest/userguide/evaluation.html) · [Responsible AI Lens](https://docs.aws.amazon.com/wellarchitected/latest/responsible-ai-lens/responsible-ai-lens.html)
