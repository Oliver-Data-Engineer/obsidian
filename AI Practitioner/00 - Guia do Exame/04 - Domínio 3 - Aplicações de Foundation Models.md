## Resumo

**Peso: 28% (o maior da prova)** · Como projetar aplicações com Foundation Models: escolher o modelo, parâmetros de inferência, **RAG**, bancos vetoriais, custos de customização, **agentes**, **prompt engineering**, **fine-tuning** e **avaliação**.

> [!info] Ideia central
> Dado um problema de negócio, saber **qual modelo**, **qual forma de adaptação** (prompt, RAG, fine-tuning) e **como medir** se funcionou.

## Tarefa 3.1 — Considerações de design para aplicações com FMs

**O que a prova espera:**
- Critérios para escolher um modelo pré-treinado: **custo, modalidade, latência, suporte a vários idiomas, tamanho e complexidade do modelo, possibilidade de customização, tamanho de entrada/saída**.
- Efeito dos **parâmetros de inferência** (temperatura, tamanho de entrada/saída).
- O que é **RAG** e onde aplicar (ex.: Bedrock Knowledge Bases).
- Serviços AWS que armazenam **embeddings em bancos vetoriais**.
- Trade-offs de custo entre formas de customização: **pré-treino, fine-tuning, in-context learning, RAG**.
- Papel dos **agentes** em tarefas de várias etapas (Agents for Amazon Bedrock).

**Bancos vetoriais na AWS:**

| Serviço | Observação |
|---|---|
| **Amazon OpenSearch Service** (e Serverless) | Opção mais comum para busca vetorial / Knowledge Bases |
| **Amazon Aurora** (PostgreSQL + pgvector) | Banco relacional com vetores |
| **Amazon RDS for PostgreSQL** (pgvector) | Idem, em RDS |
| **Amazon Neptune** | Banco de grafos com busca vetorial |
| **Amazon DocumentDB** (compatível com MongoDB) | Documentos JSON com busca vetorial |

**Customização — do mais barato ao mais caro:**

| Abordagem | Altera o modelo? | Custo | Quando |
|---|---|---|---|
| **In-context learning / Prompt engineering** | ❌ | 💲 | Instruções e exemplos no prompt |
| **RAG** | ❌ | 💲💲 | Dados atuais/privados, menos alucinação, citar fontes |
| **Fine-tuning** | ✅ | 💲💲💲 | Mudar estilo/tarefa com dados rotulados |
| **Pré-treino contínuo** | ✅ | 💲💲💲💲 | Ensinar um domínio novo com muito dado não rotulado |
| **Pré-treino do zero** | ✅ | 💲💲💲💲💲 | Raríssimo |

**RAG em 4 passos:** documentos → *chunking* → embeddings em banco vetorial → na pergunta, busca os trechos mais similares e os injeta no prompt.

**Agentes (Agents for Amazon Bedrock):** o modelo divide a tarefa em etapas, decide quais **APIs/ferramentas** chamar (via *action groups*/Lambda), consulta Knowledge Bases e monta a resposta final.

📚 Notas: [[05 - Parâmetros de Inferência|Parâmetros de Inferência]] · [[07 - Prompt na AWS|Prompt na AWS]] · [[10 - O que é IA Generativa|O que é IA Generativa]]

## Tarefa 3.2 — Técnicas eficazes de prompt engineering

**O que a prova espera:**
- Conceitos: **contexto, instrução, prompts negativos, espaço latente do modelo**.
- Técnicas: **chain-of-thought, zero-shot, single-shot, few-shot, prompt templates**.
- Benefícios e boas práticas: melhor qualidade de resposta, experimentação, guardrails, descoberta, especificidade e concisão, uso de vários comentários/instruções.
- Riscos e limitações: **exposição, envenenamento (poisoning), sequestro (hijacking), jailbreaking**.

📚 Notas (já completas): [[00 - Índice - Prompt|Índice - Prompt]] · [[02 - Anatomia de um Prompt|Anatomia de um Prompt]] · [[03 - Tipos de Prompt|Tipos de Prompt]] · [[04 - Boas Práticas de Prompt|Boas Práticas de Prompt]] · [[06 - Riscos e Segurança em Prompts|Riscos e Segurança em Prompts]]

## Tarefa 3.3 — Treinamento e fine-tuning de FMs

**O que a prova espera:**
- Elementos do treino de um FM: **pré-treino, fine-tuning, pré-treino contínuo**.
- Métodos de fine-tuning: **instruction tuning**, adaptação a domínios específicos, **transfer learning**, pré-treino contínuo.
- Preparo de dados para fine-tuning: curadoria, governança, tamanho, rotulagem, **representatividade**, **RLHF**.

| Termo | Em uma linha |
|---|---|
| **Pré-treino** | Treino inicial com enorme volume de dados **não rotulados** |
| **Fine-tuning** | Ajuste com dados **rotulados** (pares prompt → resposta) para uma tarefa |
| **Instruction tuning** | Fine-tuning com exemplos de **instruções** para o modelo seguir comandos melhor |
| **Pré-treino contínuo** | Continuar o pré-treino com dados **não rotulados** de um domínio (ex.: jurídico) |
| **Transfer learning** | Reaproveitar um modelo treinado em uma tarefa para outra |
| **RLHF** | Humanos avaliam respostas e o modelo aprende com essa preferência |

## Tarefa 3.4 — Avaliação de desempenho de FMs

**O que a prova espera:**
- Abordagens: **avaliação humana** e **datasets de benchmark**.
- Métricas: **ROUGE, BLEU, BERTScore**.
- Verificar se o modelo atende ao **negócio**: produtividade, engajamento do usuário, engenharia de tarefas.

| Métrica | Uso principal | Dica |
|---|---|---|
| **ROUGE** | **Resumos** (compara com resumo de referência) | ROUGE → "Resumo" |
| **BLEU** | **Tradução** | BLEU → "Bilíngue" |
| **BERTScore** | Similaridade **semântica** (significado, não só palavras iguais) | Usa embeddings |
| **Perplexidade** | Quão "surpreso" o modelo fica com o texto (menor = melhor) | Extra |
| **METEOR** | Tradução/resumo aceitando **sinônimos** | Entre ROUGE e BERTScore |
| **WER** | **Transcrição** de fala: % de palavras erradas (menor = melhor) | (S + D + I) ÷ N |

📏 Detalhes e exemplos: [[03 - Métricas de Avaliação - Resumo, Tradução e Transcrição|Métricas de Avaliação - Resumo, Tradução e Transcrição]]

**Na AWS:** Amazon Bedrock **Model Evaluation** (automática ou com humanos) e SageMaker Clarify (avaliação de FMs).

## Autoavaliação

- [ ] Sei os critérios para escolher um FM.
- [ ] Sei explicar RAG e citar 3 bancos vetoriais da AWS.
- [ ] Sei ordenar prompt → RAG → fine-tuning → pré-treino por custo.
- [ ] Sei o que um agente do Bedrock faz.
- [ ] Sei zero/one/few-shot, CoT e os riscos de prompt.
- [ ] Sei diferenciar fine-tuning, instruction tuning, pré-treino contínuo e RLHF.
- [ ] Sei quando usar ROUGE, BLEU, METEOR, BERTScore e WER (e quais são "menor = melhor").

---
Início: [[00 - Início - Guia do Exame]] · Anterior: [[03 - Domínio 2 - Fundamentos de IA Generativa]] · Próximo: [[05 - Domínio 4 - Diretrizes para IA Responsável]] · ✅ [[09 - Checklist de Estudo]]
