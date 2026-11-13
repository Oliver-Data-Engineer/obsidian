## Resumo

Boas práticas de prompt são **hábitos que aumentam a chance de acertar de primeira**: ser claro, dar contexto, mostrar o formato esperado, usar exemplos, restringir o escopo e **iterar**. Não existe prompt perfeito de primeira — prompt engineering é um ciclo de **escrever → testar → avaliar → ajustar**.

> [!info] Ideia central
> **Seja específico, dê contexto, mostre o formato, teste e itere.**

## As Boas Práticas

### 1. Seja claro, específico e conciso
Diga exatamente **o que** quer, **para quem** e **em que tamanho**. Evite ambiguidade, mas sem encher de texto desnecessário (cada token custa).

| ❌ | ✅ |
|---|---|
| "Fale de nuvem." | "Explique **computação em nuvem** em **3 frases**, para um **gestor não técnico**." |

### 2. Comece pela instrução
Coloque a **tarefa no início** (ou repita-a no fim, em textos longos) para o modelo saber o que fazer com o conteúdo que vem depois.

### 3. Forneça contexto relevante
Informe cenário, público, objetivo e restrições. O modelo só conhece o que está no prompt (e no seu treino).

### 4. Defina o formato da resposta
Peça **tabela, JSON, lista, número de itens, tom** etc. Deixa a saída **previsível** e fácil de processar.

### 5. Use exemplos (one/few-shot)
Se o padrão é difícil de descrever, **mostre** 2–5 exemplos bons e variados. Veja [[03 - Tipos de Prompt|Tipos de Prompt]].

### 6. Peça raciocínio em etapas para tarefas complexas
Use **Chain-of-Thought** ("pense passo a passo") em cálculos, lógica e comparações — e quebre tarefas grandes em **vários prompts** (*prompt chaining*).

### 7. Atribua um papel (persona)
"Você é um auditor…" ajusta tom, vocabulário e profundidade.

### 8. Diga o que fazer (e, quando preciso, o que **não** fazer)
Prefira instruções **positivas** ("responda em linguagem simples") e use **prompt negativo** para limites claros ("não invente dados; se não souber, diga que não sabe").

### 9. Use delimitadores
Separe instruções de dados com `"""`, `---` ou tags `<texto>`. Evita confusão e ajuda contra [[06 - Riscos e Segurança em Prompts|prompt injection]].

### 10. Reduza alucinações
- Peça para **basear a resposta apenas no texto fornecido**.
- Autorize o modelo a dizer **"não sei"**.
- Peça **citações/trechos** que sustentem a resposta.
- Combine com **RAG** quando precisar de dados atuais/proprietários.

### 11. Ajuste os parâmetros de inferência
Temperatura, Top-P, Top-K e tamanho máximo mudam a criatividade e o tamanho da saída. Veja [[05 - Parâmetros de Inferência|Parâmetros de Inferência]].

### 12. Itere, teste e documente
Teste com **vários casos** (inclusive casos-limite), compare versões, **versione** os prompts que funcionam e reutilize como **templates**.

### 13. Proteja o prompt (segurança)
Nunca ponha **segredos/dados sensíveis** no prompt; valide entradas de usuário; use **Guardrails**. Veja [[06 - Riscos e Segurança em Prompts|Riscos e Segurança em Prompts]].

## Checklist Rápido

```text
[ ] A tarefa está clara, com verbo de ação?
[ ] Informei público, contexto e objetivo?
[ ] Defini formato e tamanho da saída?
[ ] Dei exemplos (se o padrão é difícil)?
[ ] Separei dados de instruções (delimitadores)?
[ ] Disse o que evitar e permiti "não sei"?
[ ] Testei com mais de um caso e iterei?
[ ] Não incluí dados sensíveis?
```

## Erros Comuns (o que evitar)

| Erro | Consequência |
|---|---|
| Prompt vago ("melhore isso") | Resposta genérica ou fora do que você queria |
| Várias tarefas misturadas num só prompt | Respostas incompletas ou confusas → **divida em etapas** |
| Exemplos ruins/enviesados no few-shot | Modelo imita o viés/erro |
| Instruções contraditórias | Comportamento imprevisível |
| Prompt enorme sem necessidade | Mais **custo, latência** e risco de estourar a janela de contexto |
| Confiar sem verificar | **Alucinação** passa despercebida → valide fatos importantes |
| Colocar dados sensíveis no prompt | Risco de **vazamento/privacidade** |

## Exemplo para Associação Mental

**Briefing para um Designer** Quando você contrata um designer, não diz só "faz um logo". Você passa **objetivo, público, cores, referências (exemplos), o que não quer e o formato de entrega** — e depois dá **feedback em rodadas**. Um bom prompt é um bom briefing, e a iteração é a rodada de revisão.

## Na AWS (AI Practitioner)

- Boas práticas aparecem no domínio de **Aplicações de Foundation Models**: **especificidade e concisão**, **contexto**, **exemplos**, **experimentação/iteração**, **prompt templates** e **guardrails**.
- **Amazon Bedrock Guardrails** → aplica filtros de conteúdo, tópicos negados, filtros de PII e *grounding* (redução de alucinação) nas entradas e saídas.
- **Bedrock Prompt Management** → criar, **versionar** e comparar prompts; **Playgrounds** → experimentar rápido.

---
Índice: [[00 - Índice - Prompt|Índice - Prompt]] · Anterior: [[03 - Tipos de Prompt|Tipos de Prompt]] · Próximo: [[05 - Parâmetros de Inferência|Parâmetros de Inferência]] · Relacionado: [[07 - Prompt na AWS|Prompt na AWS]]
