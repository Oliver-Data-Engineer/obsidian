## Resumo

Um **Foundation Model (FM)** é um modelo grande, **pré-treinado com enormes volumes de dados genéricos**, que serve de "base" para muitas tarefas diferentes (texto, código, imagem, embeddings). Esta nota mostra como o Bedrock oferece, deixa escolher, **customizar** e **avaliar** esses modelos.

> [!info] Ideia central
> FM = **um modelo, muitas tarefas**. No Bedrock você **escolhe** o FM, **testa** no playground, **adapta** (prompt → RAG → fine-tuning) e **avalia** antes de ir para produção.

## FM x LLM x modelo de ML tradicional

| | Modelo de ML tradicional | Foundation Model | LLM |
|---|---|---|---|
| Treino | Dados rotulados de **uma tarefa** | Dados enormes **não rotulados** (auto-supervisionado) | É um FM focado em **texto** |
| Uso | **Uma** tarefa (ex.: prever churn) | **Muitas** tarefas | Gerar, resumir, traduzir, classificar texto |
| Exemplo | XGBoost para fraude | Claude, Nova, Llama, Stable Diffusion | Claude, Llama, Mistral |

## Catálogo de modelos no Bedrock (exemplos)

| Fornecedor | Família | Tipo / uso típico |
|---|---|---|
| **Amazon** | **Nova** (Micro, Lite, Pro, Premier, Canvas, Reel, Sonic) | Texto, multimodal, imagem (Canvas), vídeo (Reel), voz (Sonic) |
| **Amazon** | **Titan** | **Embeddings** (Titan Text Embeddings) e imagem |
| **Anthropic** | **Claude** | Texto, raciocínio, código, visão |
| **Meta** | **Llama** | Texto, pesos abertos |
| **Mistral AI** | Mistral / Mixtral | Texto, pesos abertos |
| **Cohere** | Command, **Embed**, **Rerank** | Texto, embeddings, reranqueamento para RAG |
| **AI21 Labs** | Jamba | Texto com contexto longo |
| **Stability AI** | Stable Diffusion / Stable Image | **Geração de imagem** (modelo de difusão) |
| **Outros** | DeepSeek, OpenAI (pesos abertos), Qwen e outros | Texto e raciocínio |

> [!note] O catálogo muda quase todo mês
> A prova **não cobra versões** de modelos. Ela cobra **o tipo**: "gerar imagem → modelo de difusão (Stability, Nova Canvas)", "criar vetores → modelo de embeddings (Titan, Cohere Embed)".

Outras formas de acesso:
- **Bedrock Marketplace**: mais de 100 modelos especializados de terceiros, implantados em *endpoints*.
- **Playgrounds** (Chat, Text, Image): testar prompts e parâmetros **sem código**.

## Como escolher o FM (Tarefa 3.1)

| Critério | Pergunta a fazer |
|---|---|
| **Modalidade** | Texto, imagem, áudio, vídeo, embeddings? |
| **Custo** | Preço por token de entrada e saída cabe no orçamento? |
| **Latência** | Precisa de resposta em tempo real (chat) ou pode esperar (batch)? |
| **Janela de contexto** | Quantos tokens cabem na entrada (documentos longos)? |
| **Idiomas** | Suporta português? |
| **Tamanho / complexidade** | Modelo menor = mais barato e rápido; maior = raciocina melhor |
| **Customização** | Aceita fine-tuning no Bedrock? |
| **Compliance / licença** | Licença permite o uso? Disponível na sua região? |

Parâmetros de inferência (temperatura, top-p, top-k, tamanho máximo, stop sequences) → [[05 - Parâmetros de Inferência|Parâmetros de Inferência]].

## Customização de modelos

> [!tip] Ordem de custo (cai muito)
> **Prompt engineering → RAG → Fine-tuning → Pré-treino contínuo → Pré-treino do zero**
> Do **mais barato e rápido** ao **mais caro e demorado**. Sempre comece pelo mais simples que resolve.

| Método | Dados de entrada | O que muda | Quando usar |
|---|---|---|---|
| **Prompt engineering** | Nenhum (só o prompt) | Nada no modelo | Primeira tentativa → [[00 - Índice - Prompt\|Índice - Prompt]] |
| **RAG** (Knowledge Bases) | Seus documentos | Nada no modelo; injeta contexto | Dados **atuais/privados**, reduzir alucinação → [[05 - Bedrock RAG - Knowledge Bases\|Bedrock RAG - Knowledge Bases]] |
| **Fine-tuning supervisionado** | **Rotulados**: pares prompt → resposta | Pesos do modelo | Ensinar **estilo, formato ou tarefa** específica |
| **Pré-treino contínuo** (*continued pre-training*) | **Não rotulados**: textos do domínio | Pesos do modelo | Ensinar **vocabulário/conhecimento de um domínio** (jurídico, médico) |
| **Destilação** (*distillation*) | Prompts; o modelo "professor" gera as respostas | Cria um modelo **menor** | Ter qualidade parecida com **menos custo e latência** |
| **Reinforcement fine-tuning** | Sinais de recompensa / feedback | Pesos do modelo | Alinhar respostas a critérios de qualidade |
| **Custom Model Import** | Pesos treinados fora do Bedrock | — | Usar no Bedrock um modelo seu (ex.: treinado no SageMaker) |

> [!warning] Pegadinhas
> - **Rotulado → fine-tuning**. **Não rotulado → pré-treino contínuo**.
> - Os dados de treino ficam no **Amazon S3**. O modelo customizado é **privado** e só a sua conta usa.
> - Modelo customizado costuma exigir **Provisioned Throughput** para inferência → [[04 - ML Inference|ML Inference]].
> - Fine-tuning **não** dá ao modelo dados que mudam todo dia. Para isso use **RAG**.

## Avaliação de modelos (Tarefa 3.4)

**Amazon Bedrock Model Evaluation** compara modelos para escolher o melhor para o seu caso.

| Tipo | Como funciona | Exemplo de métricas |
|---|---|---|
| **Automática** | Datasets prontos ou seus + métricas calculadas | Acurácia, robustez, toxicidade |
| **Humana** | Sua equipe ou equipe gerenciada pela AWS dá notas | Relevância, estilo, tom (critérios **subjetivos**) |
| **LLM-as-a-judge** | Um FM "juiz" dá notas às respostas de outro | Correção, completude, fidelidade (alucinação), recusa, nocividade |
| **Avaliação de RAG** | Avalia a Knowledge Base: só recuperação ou recuperação + resposta | Relevância do contexto, cobertura, fidelidade |

Métricas clássicas de texto (cobradas na prova):

| Métrica | Mede | Tarefa típica |
|---|---|---|
| **ROUGE** | Sobreposição com o texto de referência (*recall*) | **Resumo** |
| **BLEU** | Precisão de n-gramas em relação à referência | **Tradução** |
| **BERTScore** | **Similaridade semântica** via embeddings | Significado, mesmo com palavras diferentes |
| **Perplexidade** | Quão "surpreso" o modelo fica com o texto | Qualidade de modelo de linguagem |
| **METEOR** | Como BLEU/ROUGE, mas aceita **sinônimos e variações** | Tradução e resumo |
| **WER** | % de palavras **substituídas, apagadas ou inseridas** (menor = melhor) | **Transcrição de fala** |

Detalhes, exemplos de cálculo e diferenças: [[03 - Métricas de Avaliação - Resumo, Tradução e Transcrição|Métricas de Avaliação - Resumo, Tradução e Transcrição]]

## Exemplo para Associação Mental

**O Médico Recém-formado.** O **FM** é um médico generalista: sabe um pouco de tudo. O **prompt** é a pergunta bem feita na consulta. O **RAG** é entregar a ele o **prontuário** do paciente. O **fine-tuning** é uma **residência** curta numa especialidade. O **pré-treino contínuo** é fazê-lo **ler todos os livros** de cardiologia. A **destilação** é ele treinar um assistente mais rápido para os casos comuns. A **avaliação** é a **prova de residência**.

---
Índice: [[00 - Índice - Bedrock|Índice - Bedrock]] · Próximo: [[04 - ML Inference|ML Inference]]

Fontes: [Customize your model – Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/custom-models.html) · [Evaluate the performance of Amazon Bedrock resources](https://docs.aws.amazon.com/bedrock/latest/userguide/evaluation.html) · [RAG evaluation and LLM-as-a-judge](https://aws.amazon.com/blogs/aws/new-rag-evaluation-and-llm-as-a-judge-capabilities-in-amazon-bedrock)
