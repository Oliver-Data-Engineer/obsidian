## Resumo

Mapa de estudo do tema **Prompt / Prompt Engineering** para a certificação **AWS AI Practitioner**. Siga a ordem abaixo: do conceito → estrutura → técnicas → boas práticas → parâmetros → segurança → AWS → revisão.

> [!info] Ideia central
> **Prompt é a instrução; Prompt Engineering é escrevê-la, testá-la e refiná-la** para obter respostas melhores *sem treinar o modelo*.

## Trilha de Estudo

| # | Nota | Foco | Prioridade p/ prova |
|---|---|---|---|
| 1 | [[01 - O que é um Prompt\|O que é um Prompt]] | Definição, conceitos-chave, por que importa | ⭐⭐⭐ |
| 2 | [[02 - Anatomia de um Prompt\|Anatomia de um Prompt]] | Blocos, template, delimitadores | ⭐⭐ |
| 3 | [[03 - Tipos de Prompt\|Tipos de Prompt]] | Zero/One/Few-shot, CoT, persona, formato, interativo | ⭐⭐⭐ |
| 4 | [[04 - Boas Práticas de Prompt\|Boas Práticas de Prompt]] | Checklist, erros comuns, redução de alucinação | ⭐⭐⭐ |
| 5 | [[05 - Parâmetros de Inferência\|Parâmetros de Inferência]] | Temperatura, Top-P, Top-K, max tokens | ⭐⭐⭐ |
| 6 | [[06 - Riscos e Segurança em Prompts\|Riscos e Segurança em Prompts]] | Injection, jailbreak, leaking, poisoning, defesas | ⭐⭐⭐ |
| 7 | [[07 - Prompt na AWS\|Prompt na AWS]] | Bedrock, Prompt Management, Guardrails, PartyRock | ⭐⭐⭐ |
| 8 | [[08 - Perguntas de Revisão - Prompt\|Perguntas de Revisão - Prompt]] | Flashcards, questões, exercício | ⭐⭐⭐ |

## Resumo Relâmpago (cola de 1 minuto)

- **Prompt** = entrada do modelo · **Prompt Engineering** = otimizar essa entrada **sem treinar**.
- **Bloco de um prompt:** papel · instrução · contexto · entrada · restrições · formato.
- **Técnicas:** zero-shot (0 exemplos) · one-shot (1) · few-shot (vários) · **CoT** (passo a passo) · persona · formato · interativo.
- **Parâmetros:** **temperatura alta = criativo / baixa = consistente** · Top-P / Top-K limitam candidatos · max tokens limita o tamanho · stop sequences encerram.
- **Riscos:** injection · hijacking · jailbreak · leaking · poisoning · alucinação · viés · vazamento de PII.
- **Defesas:** **Guardrails**, delimitadores, menor privilégio, validação, humano no circuito.
- **AWS:** Bedrock (+ Playgrounds, Prompt Management, Prompt Flows, Guardrails, Knowledge Bases, Agents) · PartyRock · Amazon Q.
- **Ordem de adaptação:** **Prompt Engineering → RAG → Fine-tuning → Pré-treino**.

## Conexões com outras notas

- [[10 - O que é IA Generativa|O que é IA Generativa]] — onde prompt, tokens, temperatura e alucinação aparecem como conceitos-chave.
- [[09 - O que é Deep Learning|O que é Deep Learning]] — a base dos LLMs que respondem aos prompts.
- [[11 - Comparação Geral e Casos de Uso|Comparação Geral e Casos de Uso]] — visão geral dos tipos de IA.

---
Voltar: [[10 - O que é IA Generativa|O que é IA Generativa]] · 🗺️ [[00 - Níveis de IA.canvas|Níveis de IA]]
