## Resumo

O **Amazon Nova** é a **família de foundation models da própria Amazon**, disponível no **Amazon Bedrock**. Tem modelos de **texto e multimodais** (entendem imagem, vídeo e documentos), de **geração de imagem e vídeo**, de **voz em tempo real**, de **embeddings** e um serviço de **agentes que usam o navegador**. É o sucessor da família **Amazon Titan**.

> [!info] Ideia central
> **Nova = os modelos da Amazon dentro do Bedrock.** Você usa como qualquer outro FM: pela API do Bedrock, pagando por token, com Knowledge Bases, Agents e Guardrails.
> 🔑 Palavras-chave na prova: "**modelo da própria Amazon**", "**custo-benefício**", "**multimodal**", "**gerar imagem (Nova Canvas)**", "**gerar vídeo (Nova Reel)**", "**voz em tempo real (Nova Sonic)**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Machine Learning · Foundation Models (IA generativa) |
| **Onde roda** | **Amazon Bedrock** (serverless, por API) |
| **Entrada → Saída** | Depende do modelo: texto, imagem, vídeo, áudio → texto, imagem, vídeo ou fala |
| **Customização** | Fine-tuning e **destilação** no Bedrock; **Nova Forge** para criar modelos próprios a partir do Nova |
| **Preço** | Por **token** (texto), por **imagem/segundo de vídeo** (geração), como os outros FMs do Bedrock |
| **Na prova** | Domínios 2 e 3 · ⭐⭐ (novo na lista oficial de 29/10/2026) |
| **Status 2026** | ✅ Disponível |

## A família (o que cada um faz)

| Modelo / serviço | Tipo | Para quê |
|---|---|---|
| **Nova Micro** | Texto | Respostas rápidas e **muito baratas** (só texto) |
| **Nova Lite / Nova 2 Lite** | Multimodal (texto, imagem, vídeo → texto) | Tarefas do dia a dia com **ótimo custo-benefício**, inclusive **raciocínio** |
| **Nova Pro / Nova 2 Pro** | Multimodal | Modelo mais **capaz** para tarefas complexas e agentes |
| **Nova Premier** | Multimodal | O mais avançado da 1ª geração; também usado como **professor** em **destilação** |
| **Nova 2 Omni** | Multimodal (entrada texto, áudio, imagem, vídeo → texto **e imagem**) | Entender e gerar em várias modalidades num modelo só |
| **Nova Canvas** | **Geração de imagem** (modelo de difusão) | Criar e editar imagens a partir de texto; marca d'água invisível |
| **Nova Reel** | **Geração de vídeo** | Vídeos curtos a partir de texto/imagem |
| **Nova Sonic / Nova 2 Sonic** | **Fala ↔ fala** | Conversa por **voz em tempo real**, natural (assistentes de voz, call center) |
| **Nova Multimodal Embeddings** | **Embeddings** | Vetores de texto, imagem, vídeo e áudio para **busca semântica / RAG** |
| **Nova Act** | **Agente de navegador** | Automatizar tarefas em **interfaces web** (clicar, preencher, navegar) |
| **Nova Forge** | Serviço de **construção de modelos** | Treinar um modelo **próprio** partindo de checkpoints do Nova com seus dados |

> [!note] A prova não cobra versões
> Saiba o **tipo** de cada um: **texto/multimodal** (Micro, Lite, Pro, Premier), **imagem** (Canvas), **vídeo** (Reel), **voz** (Sonic), **embeddings**, **agente de navegador** (Act).

## Casos de uso

| Cenário | Modelo Nova |
|---|---|
| Chatbot barato e rápido para FAQ | **Nova Micro / Lite** |
| Analisar **fotos de sinistro** ou **vídeos** e responder perguntas | **Nova Lite / Pro** (multimodal) |
| Gerar **imagens de produto** para campanha | **Nova Canvas** |
| Criar **vídeo curto** de marketing | **Nova Reel** |
| Atendente de **voz** que conversa em tempo real | **Nova Sonic** |
| Busca semântica em catálogo com **fotos e textos** | **Nova Multimodal Embeddings** |
| Modelo pequeno que imita um grande, com menor custo | **Destilação** (Premier/Pro → Lite/Micro) |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[01 - Amazon Bedrock\|Amazon Bedrock]] | O Bedrock é a **plataforma** (API, RAG, agentes, guardrails). O Nova é **um dos fornecedores de modelos** dentro dela |
| **Amazon Titan** | Família anterior de modelos da Amazon (texto, imagem, **embeddings**). Ainda aparece em questões antigas, principalmente **Titan Embeddings** |
| [[05 - Amazon Polly\|Amazon Polly]] | Polly = **texto → fala** (TTS) clássico. **Nova Sonic** = **conversa de voz** em tempo real (entende e responde falando) |
| [[07 - Amazon Rekognition\|Amazon Rekognition]] | Rekognition = análise de imagem **pronta e especializada** (rostos, rótulos, moderação). Nova multimodal = **LLM** que entende imagens e responde **qualquer pergunta** sobre elas |
| **Nova Act** x **Bedrock AgentCore** | Nova Act = agente que **opera navegadores**. AgentCore = **plataforma** para implantar e operar qualquer agente → [[06 - Bedrock Agents\|Bedrock Agents]] |

> [!warning] Pegadinhas de prova
> - "Usar um **FM da própria Amazon** com o **melhor custo-benefício**" → **Amazon Nova** no **Bedrock**.
> - "Gerar **imagens** a partir de texto no Bedrock" → **Nova Canvas** (ou Stability AI). "Gerar **vídeo**" → **Nova Reel**.
> - O Nova **não** precisa de instância nem SageMaker: é **serverless pelo Bedrock**.
> - Dados enviados ao Nova (como a qualquer FM do Bedrock) **não são usados para treinar** o modelo base.

## Exemplo para Associação Mental

**A marca própria do supermercado.** No "shopping de modelos" do Bedrock há lojas da Anthropic, Meta, Mistral... e a **marca própria da Amazon: Nova**. Tem a versão econômica (**Micro**), a do dia a dia (**Lite**), a premium (**Pro/Premier**), a seção de **fotos** (**Canvas**), de **filmes** (**Reel**), o **atendente que conversa por voz** (**Sonic**) e o **robô que faz compras no site por você** (**Act**).

## 📝 Meu entendimento

> _Explique com suas palavras: qual a diferença entre o Amazon Nova e o Amazon Bedrock?_

---
Resumo: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · Relacionadas: [[01 - Amazon Bedrock|Amazon Bedrock]] · [[02 - Foundation Models|Foundation Models]] · [[00 - Índice - Bedrock|Índice - Bedrock]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [Amazon Nova](https://aws.amazon.com/ai/generative-ai/nova/) · [AWS unveils Nova 2, Nova Forge e Nova Act](https://www.aboutamazon.com/news/aws/aws-agentic-ai-amazon-bedrock-nova-models)
