## Resumo

Mapa de estudo do tema **Prompt / Prompt Engineering** para a certificação **AWS AI Practitioner**. Siga a ordem abaixo: do conceito → estrutura → técnicas → boas práticas → parâmetros → segurança → AWS → revisão.

> [!info] Ideia central
> **Prompt é a instrução; Prompt Engineering é escrevê-la, testá-la e refiná-la** para obter respostas melhores *sem treinar o modelo*.

## Trilha de Estudo

| # | Nota | Foco | Prioridade p/ prova |
|---|---|---|---|
| 1 | [[O que é um Prompt]] | Definição, conceitos-chave, por que importa | ⭐⭐⭐ |
| 2 | [[Anatomia de um Prompt]] | Blocos, template, delimitadores | ⭐⭐ |
| 3 | [[Tipos de Prompt]] | Zero/One/Few-shot, CoT, persona, formato, interativo | ⭐⭐⭐ |
| 4 | [[Boa Praticas]] | Checklist, erros comuns, redução de alucinação | ⭐⭐⭐ |
| 5 | [[Parâmetros de Inferência]] | Temperatura, Top-P, Top-K, max tokens | ⭐⭐⭐ |
| 6 | [[Riscos e Segurança em Prompts]] | Injection, jailbreak, leaking, poisoning, defesas | ⭐⭐⭐ |
| 7 | [[Prompt na AWS]] | Bedrock, Prompt Management, Guardrails, PartyRock | ⭐⭐⭐ |
| 8 | [[Perguntas de Revisão - Prompt]] | Flashcards, questões, exercício | ⭐⭐⭐ |

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

- [[O que é  Generative IA]] — onde prompt, tokens, temperatura e alucinação aparecem como conceitos-chave.
- [[O que é  Deep Learn]] — a base dos LLMs que respondem aos prompts.
- [[Comparação Geral e Casos de Uso]] — visão geral dos tipos de IA.

---
Voltar: [[O que é  Generative IA]] · 🗺️ [[Níveis de IA.canvas]]
