## Resumo

Os "tipos" de prompt são **técnicas de prompting** — maneiras diferentes de montar a entrada conforme a **tarefa**. Não são excludentes: você pode combinar (ex.: *persona + few-shot + formato de saída*). As 6 primeiras abaixo são as mais cobradas/usadas; as demais são extras para aprofundar.

> [!info] Ideia central
> **Quanto mais difícil ou específica a tarefa, mais "ajuda" (exemplos, raciocínio, estrutura) você coloca no prompt.**
> Zero-shot (sem ajuda) → Few-shot (exemplos) → Chain-of-Thought (raciocínio).

## Visão Geral

| Técnica                    | Em uma frase                        | Quando usar                                                           |
| -------------------------- | ----------------------------------- | --------------------------------------------------------------------- |
| **Zero-shot**              | Pede a tarefa **sem exemplos**      | Tarefas simples e comuns (resumo, tradução, definição)                |
| **One-shot**               | Dá **1 exemplo**                    | Mostrar o formato/estilo de forma rápida                              |
| **Few-shot**               | Dá **vários exemplos**              | Tarefas com padrão específico (classificação, tom de marca, extração) |
| **Chain-of-Thought (CoT)** | Pede o **raciocínio passo a passo** | Matemática, lógica, análises e comparações complexas                  |
| **Role / Persona**         | Atribui um **papel** ao modelo      | Ajustar tom, profundidade e ponto de vista                            |
| **Formato específico**     | Define a **forma da saída**         | Tabela, JSON, lista, e-mail, código                                   |
| **Interativo / Refinado**  | **Itera** na conversa               | Ajustar o resultado sem recomeçar                                     |

## 1 – Zero-shot prompting

Você faz o pedido **sem nenhum exemplo**; o modelo usa só o que aprendeu no treino. É o tipo mais simples e rápido.

- **Exemplo:** *"Classifique o sentimento do texto como positivo, negativo ou neutro: 'O atendimento foi excelente.'"*
- ✅ Rápido, curto, barato em tokens.
- ❌ Pode errar em tarefas ambíguas ou com formato muito específico.

## 2 – One-shot e Few-shot prompting

Você inclui **um (one-shot)** ou **vários (few-shot)** pares de exemplo para o modelo **imitar o padrão** (também chamado de *in-context learning* — o modelo "aprende" pelo exemplo, **sem ser treinado**).

```text
Classifique o sentimento:

Texto: "Adorei o produto!"      → Positivo
Texto: "Demorou e veio quebrado" → Negativo
Texto: "Chegou na data prevista" → Neutro

Texto: "O suporte resolveu tudo em minutos" →
```

- ✅ Ótimo para fixar **estilo, formato e rótulos**.
- ❌ Gasta mais tokens; **a qualidade e a variedade dos exemplos importam** (exemplos ruins ou desbalanceados enviesam a resposta).

> [!tip] Dica para lembrar
> **Zero** = 0 exemplos · **One** = 1 · **Few** = alguns (em geral 2 a 5).

## 3 – Chain-of-Thought (CoT)

Você pede que o modelo **mostre o raciocínio em etapas** antes da resposta final ("pense passo a passo"). Isso melhora o desempenho em tarefas de **lógica, cálculo e decisão**, porque o modelo "gasta" tokens organizando a solução antes de concluir.

- **Exemplo:** *"Compare CDB, Tesouro Selic e LCI por liquidez, risco e retorno. **Raciocine passo a passo** e só depois indique o mais adequado para iniciantes."*
- **Variações:** *Zero-shot CoT* (apenas "pense passo a passo") e *Few-shot CoT* (exemplos já com o raciocínio escrito).
- ✅ Mais precisão em problemas complexos e respostas **auditáveis**.
- ❌ Respostas mais longas → **mais custo e latência**.

## 4 – Role / Persona prompting

Você define **quem** o modelo é, e ele responde sob essa perspectiva, ajustando vocabulário, profundidade e tom.

- **Exemplo:** *"Você é um planejador financeiro que ensina famílias. Explique como economizar em casal em 6 dicas práticas."*
- Pode definir também **público-alvo** ("explique para uma criança de 10 anos").

## 5 – Prompts com formato específico

A **forma** da resposta é tão importante quanto o conteúdo. Você descreve exatamente a estrutura desejada (tabela, JSON, Markdown, número de itens).

- **Exemplo:** *"Monte uma tabela comparando CDB, Tesouro Selic e LCI/LCA, com colunas de rendimento, liquidez e garantia."*
- Essencial quando a saída será **lida por outro sistema** (ex.: JSON válido para uma API).

## 6 – Prompt interativo (refinado)

Você **vai ajustando** o pedido com base nas respostas anteriores, em vez de recomeçar do zero.

- **Exemplo:** *"Reescreva o parágrafo acima mantendo a ideia, mas com linguagem menos técnica."*
- Aproveita o **histórico da conversa** (dentro da janela de contexto).

## Técnicas Extras (aprofundamento)

| Técnica                            | Ideia                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------- |
| **Prompt Chaining (encadeamento)** | Quebrar uma tarefa grande em **etapas**, usando a saída de um prompt como entrada do próximo |
| **Self-consistency**               | Gerar **várias respostas** com raciocínio e escolher a **mais frequente**                    |
| **Tree of Thoughts**               | O modelo explora **vários caminhos** de raciocínio e escolhe o melhor                        |
| **ReAct (Reason + Act)**           | Alterna **raciocinar** e **usar ferramentas** (busca, API) — base dos *Agents*               |
| **Negative prompting**             | Diz **o que evitar** ("não mencione concorrentes")                                           |
| **Prompts com RAG**                | Injeta **trechos de documentos recuperados** no prompt como contexto                         |
| **Prompt Template**                | Prompt com **variáveis** preenchidas em tempo de execução                                    |

## Exemplo para Associação Mental

**Ensinando um Estagiário**

- **Zero-shot:** "Faz esse relatório." (sem mostrar nada)
- **One/Few-shot:** "Faz igual a *estes* relatórios aqui." (mostra modelos)
- **Chain-of-Thought:** "Me explica como chegou nesse número, passo a passo."
- **Persona:** "Responda como se fosse o diretor financeiro."
- **Formato:** "Quero em uma tabela de 3 colunas."
- **Interativo:** "Ficou bom, só deixa a segunda parte mais curta."

## Na AWS (AI Practitioner)

- O exame cobra principalmente: **zero-shot, single-shot (one-shot), few-shot, chain-of-thought e prompt templates**.
- No **Amazon Bedrock Playground** você testa essas técnicas direto, trocando de modelo e comparando saídas.
- **Agents for Amazon Bedrock** usam raciocínio em etapas (ideia do **ReAct / CoT**) para decidir quais ferramentas chamar.

---
Índice: [[00 - Índice - Prompt|Índice - Prompt]] · Anterior: [[02 - Anatomia de um Prompt|Anatomia de um Prompt]] · Próximo: [[04 - Boas Práticas de Prompt|Boas Práticas de Prompt]] · Relacionado: [[05 - Parâmetros de Inferência|Parâmetros de Inferência]]

Fonte inicial: infomoney.com.br/minhas-financas/tipos-de-prompts/ (reescrito e ampliado)
