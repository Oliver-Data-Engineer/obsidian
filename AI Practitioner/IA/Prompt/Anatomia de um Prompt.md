## Resumo

Um bom prompt raramente é uma frase solta: ele é **montado em blocos**. Nem todo bloco é obrigatório, mas quanto mais deles você preenche, **menos o modelo precisa "adivinhar"**. Esta nota mostra os blocos, uma estrutura reutilizável (template) e como separar cada parte.

> [!info] Ideia central
> **Instrução + Contexto + Entrada + Formato de saída** (+ Papel + Exemplos + Restrições).

## Os Blocos de um Prompt

| Bloco | Pergunta que responde | Exemplo |
|---|---|---|
| **Papel / Persona** | *Quem* o modelo deve ser? | "Você é um analista de segurança sênior." |
| **Instrução (Tarefa)** | *O que* fazer? (verbo claro) | "Classifique o sentimento do comentário." |
| **Contexto** | *Por quê / para quem / em que cenário?* | "Os comentários vêm de um app de delivery; o público é o time de produto." |
| **Dados de entrada** | *Sobre o quê?* | `Comentário: "Chegou frio e atrasado."` |
| **Exemplos** (*shots*) | *Como* é uma boa resposta? | Pares entrada → saída (ver [[Tipos de Prompt]]) |
| **Restrições / Prompt negativo** | *O que evitar? Limites?* | "Não invente informações. Máximo 50 palavras." |
| **Formato de saída** | *Em que forma entregar?* | "Responda em JSON com as chaves `sentimento` e `justificativa`." |

> [!tip] Dica para lembrar
> Pense em **P-I-C-E-R-F**: **P**apel · **I**nstrução · **C**ontexto · **E**ntrada · **R**estrições · **F**ormato. (Os **E**xemplos entram quando o formato é difícil de descrever só com palavras.)

## Template reutilizável

```text
# PAPEL
Você é [especialista] que atende [público].

# TAREFA
[Verbo no imperativo + o que fazer].

# CONTEXTO
[Informações de fundo relevantes].

# ENTRADA
"""
[texto ou dados a serem processados]
"""

# RESTRIÇÕES
- [o que NÃO fazer]
- [limite de tamanho / tom / fontes permitidas]

# FORMATO DE SAÍDA
[tabela | JSON | lista numerada | parágrafo] com [campos/colunas].
```

## Separadores e delimitadores

Use **marcadores claros** para o modelo não confundir instrução com dados — especialmente quando a entrada vem de um usuário (reduz [[Riscos e Segurança em Prompts|prompt injection]]):

- Aspas triplas `"""..."""`, cercas de código ```` ``` ````, ou linhas `---`.
- Títulos simples (`# TAREFA`, `# ENTRADA`).
- **Tags XML** (`<documento>...</documento>`) — muito eficazes em modelos como o Claude.

## Exemplo completo

**Antes (vago):** *"Resuma esse e-mail."*

**Depois (estruturado):**

```text
Você é um assistente executivo.

Resuma o e-mail abaixo para o diretor, que tem 30 segundos para ler.
Não invente informações que não estejam no texto.

<email>
{{texto_do_email}}
</email>

Responda em até 3 bullets e termine com uma linha "Ação necessária:".
```

Repare no **papel**, **instrução**, **contexto** (30 segundos), **restrição negativa**, **delimitador** (`<email>`) e **formato** definidos.

## Exemplo para Associação Mental

**A Receita de Bolo** Um prompt é uma receita: **ingredientes** (contexto + dados), **modo de preparo** (instrução), **forma e tamanho** (formato de saída) e **"não leve ao forno acima de 180°"** (restrições). Faltou um item? O bolo sai diferente do esperado.

## Na AWS (AI Practitioner)

- Os **Prompt Templates** do exame são justamente isso: um prompt com **variáveis** (`{{variavel}}`) que é preenchido em tempo de execução — o **Amazon Bedrock Prompt Management** permite criar, versionar e reutilizar templates assim.
- Os blocos **Instrução / Contexto / Entrada / Indicador de saída** são os componentes citados nos materiais oficiais da AWS sobre prompt engineering.

---
Índice: [[Índice - Prompt]] · Anterior: [[O que é um Prompt]] · Próximo: [[Tipos de Prompt]] · Relacionado: [[Boa Praticas]]
