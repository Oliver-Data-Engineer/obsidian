## Resumo

**Prompt** é a **entrada em linguagem natural** (instrução, pergunta, contexto, exemplos) que você entrega a um modelo de [[10 - O que é IA Generativa|IA Generativa]] para que ele produza uma resposta. É a "interface" entre o humano e o *Foundation Model* / LLM: o modelo não adivinha a sua intenção, ele **continua o texto com a resposta mais provável dada a entrada** — por isso a qualidade do prompt influencia diretamente a qualidade da saída.

**Engenharia de Prompt (*Prompt Engineering*)** é a prática de **projetar, testar e refinar prompts** para obter respostas mais **precisas, úteis, seguras e consistentes** — sem precisar treinar ou alterar o modelo.

> [!info] Ideia central
> **Prompt = a instrução que você dá ao modelo.**
> **Prompt Engineering = escrever essa instrução do jeito certo, iterando até a resposta ficar boa.**

## Conceitos-Chave

| Termo | Significado |
|---|---|
| **Prompt** | Texto (ou imagem/áudio, em modelos multimodais) enviado ao modelo como entrada |
| **Completion / Resposta** | O que o modelo devolve |
| **Instrução** | A tarefa que o modelo deve executar ("resuma", "classifique", "traduza") |
| **Contexto** | Informação de apoio que ajuda o modelo a responder melhor (público, cenário, dados) |
| **Entrada (*input data*)** | O conteúdo sobre o qual a tarefa será feita (o texto a resumir, a pergunta do cliente) |
| **Indicador de saída (*output indicator*)** | O formato/estilo esperado da resposta (tabela, JSON, 3 bullets) |
| **Prompt negativo (*negative prompt*)** | Diz ao modelo o que **evitar** ("não use jargões", "sem incluir preços") |
| **Prompt de sistema (*system prompt*)** | Instruções fixas que definem papel, regras e tom do assistente durante toda a conversa |
| **Prompt de usuário (*user prompt*)** | A mensagem que a pessoa digita a cada turno |
| **Janela de contexto** | Limite de **tokens** que cabem no prompt + resposta |
| **Espaço latente (*latent space*)** | Representação interna de "conhecimento" do modelo; o prompt serve para **navegar** até a região certa dele |

> [!tip] Dica para lembrar
> O prompt é lido em **tokens** (≈ ¾ de palavra). Prompts maiores = **mais custo, mais latência** e consomem a janela de contexto.

## Por que Prompt Engineering importa?

- **Não exige treinar o modelo** → é a técnica mais **barata e rápida** de adaptar um LLM (veja a escala: Prompt Engineering → RAG → Fine-tuning → Pré-treino em [[10 - O que é IA Generativa|O que é IA Generativa]]).
- **Melhora a qualidade** das respostas e **reduz alucinações**.
- **Dá consistência** (mesmo formato de saída sempre) — essencial para colocar GenAI em produção.
- **Aumenta a segurança**, delimitando o que o modelo pode ou não fazer (ver [[06 - Riscos e Segurança em Prompts|Riscos e Segurança em Prompts]]).
- **Reduz custo**: um prompt bem feito acerta de primeira, com menos chamadas e tokens.

## Prompt ruim x Prompt bom

| ❌ Prompt vago | ✅ Prompt específico |
|---|---|
| "Fale sobre investimentos." | "Você é um educador financeiro. Explique **CDB, Tesouro Selic e LCI** para um **iniciante**, em **uma tabela** com colunas *rendimento*, *liquidez* e *risco*. Use no máximo **120 palavras** de introdução." |

O segundo define **papel, público, formato, escopo e tamanho** — veja o detalhamento em [[02 - Anatomia de um Prompt|Anatomia de um Prompt]].

## Exemplo para Associação Mental

**O Pedido ao Garçom** Imagine que o modelo é um **garçom extremamente competente, mas que só sabe o que você disse**.

- "Quero comida" → ele traz *qualquer coisa* (resposta genérica).
- "Quero um risoto de cogumelos, sem queijo, porção pequena, para uma pessoa vegana" → ele traz **exatamente** o que você precisa.

O **cardápio** é o conhecimento do modelo; o **pedido** é o prompt. Quanto mais claro o pedido, mais perto do prato desejado.

## Na AWS (AI Practitioner)

- **Amazon Bedrock** → você envia prompts via **API** (ou pelos **Playgrounds** de Chat/Texto/Imagem) para vários Foundation Models; o **Bedrock Prompt Management** guarda e versiona prompts. Detalhes em [[07 - Prompt na AWS|Prompt na AWS]].
- **PartyRock** → playground gratuito: você descreve um app com **prompts** e ele monta a interface.
- **Amazon Q Business / Q Developer** → assistentes onde você interage por prompts em linguagem natural.
- No exame, Prompt Engineering aparece como a **opção mais simples/barata** de adaptação, antes de RAG e Fine-tuning.

---
Índice: [[00 - Índice - Prompt|Índice - Prompt]] · Próximo: [[02 - Anatomia de um Prompt|Anatomia de um Prompt]] · Relacionados: [[03 - Tipos de Prompt|Tipos de Prompt]] · [[04 - Boas Práticas de Prompt|Boas Práticas de Prompt]] · [[05 - Parâmetros de Inferência|Parâmetros de Inferência]]
