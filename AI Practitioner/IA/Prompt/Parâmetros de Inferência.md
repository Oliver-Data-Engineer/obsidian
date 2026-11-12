## Resumo

Além do texto do prompt, você controla **como o modelo gera a resposta** por meio dos **parâmetros de inferência**. Eles **não mudam o que o modelo sabe**, apenas **o quanto ele arrisca, o quanto fala e quando para**. Ajustá-los é parte da engenharia de prompt.

> [!info] Ideia central
> **Prompt = *o que* você pede. Parâmetros = *como* o modelo escolhe as palavras.**
> O modelo gera **token por token**, sorteando entre os próximos tokens mais prováveis; os parâmetros mexem nesse sorteio.

## Os Parâmetros

| Parâmetro                                     | O que controla                                                    | Valor baixo                             | Valor alto                                 |
| --------------------------------------------- | ----------------------------------------------------------------- | --------------------------------------- | ------------------------------------------ |
| **Temperatura**                               | Aleatoriedade/criatividade da escolha do próximo token            | Previsível, **determinístico**, factual | **Criativo**, variado, mais risco de errar |
| **Top-P** (*nucleus sampling*)                | Considera só os tokens cuja **probabilidade acumulada** chega a P | Poucos candidatos → mais conservador    | Mais candidatos → mais diverso             |
| **Top-K**                                     | Considera só os **K tokens mais prováveis**                       | K pequeno → conservador                 | K grande → mais diverso                    |
| **Tamanho máximo da resposta** (*max tokens*) | Limite de tokens gerados                                          | Resposta cortada/curta                  | Resposta longa (mais custo)                |
| **Sequências de parada** (*stop sequences*)   | Texto que, ao ser gerado, **encerra** a resposta                  | —                                       | —                                          |
| **Penalidades** (repetição/frequência)        | Desencoraja repetir palavras (em alguns modelos)                  | Pode repetir                            | Evita repetição                            |

> [!tip] Dica para lembrar
> **Temperatura baixa → "advogado"** (preciso, consistente). **Temperatura alta → "poeta"** (criativo, imprevisível).
> **Top-P e Top-K** = "quantas opções o modelo pode considerar" (P por probabilidade, K por quantidade).

## Qual valor usar?

| Tarefa | Temperatura sugerida |
|---|---|
| Extração de dados, classificação, respostas factuais, código | **Baixa** (0 – 0,3) |
| Resumos, Q&A, atendimento | **Média** (0,3 – 0,7) |
| Brainstorm, histórias, slogans, ideias | **Alta** (0,7 – 1,0) |

Dica prática: **mude um parâmetro de cada vez** (em geral temperatura *ou* Top-P) para entender o efeito.

## Não confundir

| Conceito | Diferença |
|---|---|
| **Parâmetro de inferência** | Ajusta **a geração** em tempo de uso — não altera o modelo |
| **Hiperparâmetro de treino** (ex.: *learning rate*, épocas) | Ajusta **o treinamento / fine-tuning** |
| **Janela de contexto** | Limite **total** de tokens (prompt + resposta) |
| **Max tokens** | Limite só da **resposta** gerada |

## Exemplo para Associação Mental

**O Botão de Ousadia do Chef** O modelo é um chef que sabe milhares de receitas. Com **temperatura baixa**, ele segue a receita clássica sempre igual. Com **temperatura alta**, ele **improvisa** — pode inventar um prato incrível ou um desastre. O **Top-K/Top-P** é o tamanho da "prateleira de ingredientes" que ele pode alcançar na hora de improvisar, e o **max tokens** é o tamanho do prato.

## Na AWS (AI Practitioner)

- No **Amazon Bedrock** (API e Playgrounds) você configura **temperature, top P, top K, max tokens e stop sequences** (os disponíveis variam por modelo).
- Pergunta clássica de prova: *"Como deixar a resposta mais criativa/variada?"* → **aumentar a temperatura**. *"Como deixar mais determinística e consistente?"* → **diminuir a temperatura**.
- Temperatura também aparece em [[O que é  Generative IA|Conceitos-Chave de IA Generativa]].

---
Índice: [[Índice - Prompt]] · Anterior: [[Boa Praticas]] · Próximo: [[Riscos e Segurança em Prompts]] · Relacionado: [[Prompt na AWS]]
