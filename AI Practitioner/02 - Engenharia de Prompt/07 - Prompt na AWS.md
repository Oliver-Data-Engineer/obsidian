## Resumo

Reunião, em uma só nota, de **tudo que conecta Prompt Engineering aos serviços AWS** cobrados no AI Practitioner. Serve de ponte entre a teoria (notas anteriores) e as perguntas de prova.

> [!info] Ideia central
> **Bedrock** é o lugar onde você **usa** prompts; **Prompt Management** **organiza** prompts; **Guardrails** **protege** prompts; **Playground / PartyRock** servem para **experimentar**.

## Serviços e Recursos

| Serviço / recurso | Papel em relação a prompts |
|---|---|
| **Amazon Bedrock** | Acesso via API a vários Foundation Models (Claude, Llama, Nova, Mistral…) — onde os prompts são enviados |
| **Bedrock Playgrounds** (Chat, Text, Image) | Testar prompts, técnicas e **parâmetros de inferência** sem escrever código |
| **Bedrock Prompt Management** | **Criar, versionar, comparar e reutilizar** prompts e *prompt templates* com variáveis |
| **Bedrock Prompt Flows** | Encadear prompts, modelos e serviços em **fluxos** visuais (*prompt chaining*) |
| **Bedrock Guardrails** | **Filtros** de entrada/saída: conteúdo nocivo, tópicos negados, PII, grounding |
| **Bedrock Knowledge Bases (RAG)** | Injeta **contexto recuperado** dos seus documentos no prompt |
| **Bedrock Agents** | O modelo **raciocina em etapas** e chama ferramentas/APIs (ideia de CoT/ReAct) |
| **Bedrock Model Evaluation** | **Avalia** respostas (automática ou humana) para comparar modelos/prompts |
| **PartyRock** | Playground gratuito: crie apps de GenAI **descrevendo-os por prompt** |
| **Amazon Q Business / Developer** | Assistentes prontos usados por **prompts em linguagem natural** |

## Prompt Engineering x RAG x Fine-tuning

| Técnica | Muda o modelo? | Custo/Esforço | Quando |
|---|---|---|---|
| **Prompt Engineering** | ❌ Não | 💲 Baixo, imediato | Primeira tentativa: melhorar instrução, exemplos, formato |
| **RAG** | ❌ Não | 💲💲 Médio | Precisa de **dados atuais/privados** e menos alucinação |
| **Fine-tuning** | ✅ Sim | 💲💲💲 Alto | Mudar **estilo/especialização** de forma consistente |

> [!tip] Dica para lembrar
> Comece sempre pelo **mais barato**: **Prompt → RAG → Fine-tuning → Pré-treino**.

## Mapa: Conceito de Prompt → O que o exame costuma perguntar

| Tópico | Armadilha / dica de prova |
|---|---|
| Few-shot | "Dar **exemplos** no prompt **sem treinar**" = few-shot / in-context learning |
| Chain-of-Thought | "Raciocínio **passo a passo**" |
| Temperatura | **Alta** = criativo · **Baixa** = determinístico/consistente |
| Prompt template | Prompt com **variáveis** reutilizável |
| Reduzir alucinação | Contexto no prompt, **RAG**, **Guardrails (grounding)**, temperatura baixa |
| Proteger de abuso | **Guardrails**, menor privilégio, validação |
| Adaptar sem treinar | **Prompt Engineering** (e RAG) — **não** é fine-tuning |

## Exemplo para Associação Mental

**A Cozinha Profissional** O **Bedrock** é a cozinha com vários chefs (modelos). O **Playground** é a bancada de testes. O **Prompt Management** é o caderno de receitas versionado. O **Guardrails** é a vigilância sanitária. O **Knowledge Base** é a despensa com ingredientes do restaurante. O **Agent** é o chefe que conduz várias etapas e chama os ajudantes certos.

---
Índice: [[00 - Índice - Prompt|Índice - Prompt]] · Anterior: [[06 - Riscos e Segurança em Prompts|Riscos e Segurança em Prompts]] · Próximo: [[08 - Perguntas de Revisão - Prompt|Perguntas de Revisão - Prompt]] · Visão geral: [[10 - O que é IA Generativa|O que é IA Generativa]]
