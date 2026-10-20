## Resumo

O **Amazon Bedrock** é o serviço **totalmente gerenciado e serverless** para criar aplicações de **IA generativa** usando **Foundation Models** (FMs) de vários fornecedores (Amazon Nova, Anthropic Claude, Meta Llama, Mistral, Cohere…) por **uma única API**. Traz ferramentas prontas para RAG, agentes, guardrails, avaliação e customização de modelos.

> [!info] Ideia central
> **Prompt → FM → texto, imagem ou embedding gerado.** Usa IA generativa **sem gerenciar infraestrutura e sem treinar modelo do zero**.
> 🔑 Palavras-chave na prova: "**foundation model**", "**IA generativa**", "**serverless**", "**vários modelos por uma API**", "**RAG**", "**guardrails**", "**agentes**".

> [!tip] Estudo completo do Bedrock
> Esta é a ficha resumida. O conteúdo completo está na pasta **Bedrock**: [[Índice - Bedrock]] · [[Fondation Model]] · [[ML Inference]] · [[Beadrock Rag - Kb]] · [[Bedrock Agents]] · [[Bedrock Guardrail]] · 📝 [[Teste - Bedrock]]

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | IA generativa (plataforma de FMs) |
| **Entrada** | Prompt (texto, imagem, documento) |
| **Saída** | Texto, imagem, vídeo, áudio ou **embeddings** gerados |
| **Precisa saber ML?** | Não. Basta saber usar prompts e APIs |
| **Customização** | Prompt engineering → **RAG** (Knowledge Bases) → **fine-tuning** → pré-treino contínuo → destilação |
| **Modos** | On-demand · Batch · Provisioned Throughput |
| **Na prova** | Domínios 2, 3, 4 e 5 · ⭐⭐⭐ (o serviço **mais cobrado**) |
| **Status 2026** | ✅ Disponível · ⚠️ *Agents* virou **Agents Classic** (sem novos clientes desde 30/07/2026) → sucessor **AgentCore** |

## Principais recursos

| Recurso | O que faz | Nota |
|---|---|---|
| **Catálogo de modelos + Playgrounds** | Escolher e testar FMs sem código | [[Fondation Model]] |
| **Knowledge Bases** | **RAG** gerenciado com seus documentos | [[Beadrock Rag - Kb]] |
| **Agents / AgentCore** | Tarefas de várias etapas que **chamam APIs** | [[Bedrock Agents]] |
| **Guardrails** | Filtra conteúdo nocivo, PII, tópicos proibidos e alucinação | [[Bedrock Guardrail]] |
| **Model Evaluation** | Compara modelos (automática, humana, LLM-as-a-judge) | [[Fondation Model]] |
| **Customização** | Fine-tuning, pré-treino contínuo, destilação | [[Fondation Model]] |
| **Prompt Management / Flows** | Versionar prompts e encadear etapas | [[Prompt na AWS]] |
| **Preços** | On-demand, batch, provisioned throughput | [[ML Inference]] |

## Casos de uso

| Cenário | Recurso do Bedrock |
|---|---|
| Chatbot que responde com base em documentos internos | **Knowledge Bases (RAG)** |
| Assistente que **executa tarefas** (abrir chamado, consultar pedido) | **Agents / AgentCore** |
| Resumir, classificar ou gerar textos | **FMs + prompt engineering** |
| Gerar imagens de produtos | Modelos de imagem (Nova Canvas, Stability AI) |
| Bloquear conteúdo impróprio e dados pessoais | **Guardrails** |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon SageMaker]] (JumpStart) | Mais **controle** sobre modelo e infraestrutura. Bedrock = serverless, só usar |
| [[Amazon Q]] | Assistente **pronto**. Bedrock = **construir** a sua aplicação de GenAI |
| Serviços de IA prontos ([[Amazon Comprehend]], [[Amazon Translate]]…) | **Especializados** em uma tarefa, previsíveis e baratos. Bedrock = **generativo** e flexível |
| [[Amazon Lex]] | Chatbot de **fluxo estruturado** (intenções e slots). Bedrock = conversa **generativa** |

> [!warning] Pegadinhas de prova
> - "Usar **vários FMs** com o **menor esforço operacional**" → **Bedrock**.
> - "Os dados enviados ao Bedrock **treinam o modelo**?" → **Não**.
> - "Responder com **documentos atualizados** e **citar a fonte**" → **Knowledge Bases (RAG)**, não fine-tuning.

## Exemplo para Associação Mental

**O Shopping de Modelos.** Cada loja é um fornecedor de FMs e você paga só o que consome. A **Knowledge Base** é seu estoque particular, o **Agent** é o *personal shopper* que faz pedidos por você e o **Guardrail** é o segurança na porta.

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, o que entendeu sobre o Bedrock._

---
Resumo: [[Resumo]] · Anterior: [[Amazon SageMaker]] · Próximo: [[Amazon Q]]

Fontes: [What is Amazon Bedrock](https://docs.aws.amazon.com/bedrock/latest/userguide/what-is-bedrock.html) · [Amazon Bedrock Agents Classic](https://docs.aws.amazon.com/bedrock/latest/userguide/agents-classic-maintenance-mode.html)
