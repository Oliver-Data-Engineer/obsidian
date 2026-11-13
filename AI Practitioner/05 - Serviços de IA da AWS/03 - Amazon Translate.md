## Resumo

O **Amazon Translate** é o serviço de **tradução automática neural** da AWS. Ele traduz **texto** entre dezenas de idiomas com alta qualidade, sob demanda. Serve para traduzir documentos ou para criar aplicações **multilíngues** (sites, chats, e-commerce).

> [!info] Ideia central
> **Texto no idioma A → texto no idioma B.** Só trabalha com **texto**: para áudio, combine com Transcribe e Polly.
> 🔑 Palavras-chave na prova: "**traduzir**", "**multilíngue**", "**localização de conteúdo**", "**terminologia da marca**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Linguagem (tradução automática neural) |
| **Entrada** | Texto UTF-8 ou arquivos (.txt, .html, .docx; em lote também .xlsx, .pptx, .xlf) |
| **Saída** | Texto ou arquivo traduzido, **no mesmo formato** da entrada |
| **Precisa saber ML?** | Não. Modelo pré-treinado |
| **Customização** | **Terminologia personalizada** e **dados paralelos** (*Active Custom Translation*) |
| **Modos** | Tempo real · Lote (arquivos no S3) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐⭐ |
| **Status 2026** | ✅ Disponível |

## Principais recursos

### Formatos de entrada

| Modo | Entrada aceita | Saída |
|---|---|---|
| **Tempo real** | **Texto** UTF-8 | Texto UTF-8 |
| **Tempo real** | **Um arquivo**: .txt, .html ou .docx | Arquivo no mesmo formato |
| **Lote** (*batch*) | **Vários arquivos no S3**: .txt, .html, .docx, .xlsx, .pptx e XLIFF 1.2 (.xlf) | Arquivos no mesmo formato, no S3 |

### Personalização da tradução

| Recurso | O que faz | Exemplo |
|---|---|---|
| **Detecção automática do idioma de origem** | Descobre sozinho o idioma de entrada | Não precisa informar "de português" |
| **Terminologia personalizada** | Define **como traduzir termos específicos** | Nome da marca **não** é traduzido; "ticket" vira sempre "chamado" |
| **Dados paralelos** (*parallel data*) | Adapta **estilo, tom e vocabulário** a partir de exemplos seus de tradução | Manter o tom da empresa |
| **Formalidade** | Define o nível de formalidade da saída | "Você" x "o senhor" |
| **Profanidade** | **Mascara** palavrões na tradução | Chat público |
| **Brevidade** | Gera traduções **mais curtas** (só tempo real) | Legendas, telas de celular |
| **Tags *do-not-translate*** | Marca trechos do HTML que **não** devem ser traduzidos | Código, nomes de produto |

## Casos de uso

| Cenário | Como o Translate ajuda |
|---|---|
| **E-commerce global** | Traduz descrições de produtos e avaliações |
| **Atendimento multilíngue** | Chat em tempo real entre cliente e atendente de idiomas diferentes |
| **Análise de conteúdo** | Traduz para um idioma comum antes de usar o Comprehend |
| **Comunicação interna** | Traduz documentos e comunicados |
| **Legendas** | Transcribe (fala → texto) + Translate (texto → outro idioma) |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[04 - Amazon Transcribe\|Amazon Transcribe]] | O Transcribe converte **fala em texto** no mesmo idioma. O Translate muda o **idioma** do texto |
| [[05 - Amazon Polly\|Amazon Polly]] | O Polly converte **texto em fala**. O Translate não gera áudio |
| [[01 - Amazon Comprehend\|Amazon Comprehend]] | O Comprehend **analisa** o texto (sentimento, entidades). O Translate **traduz** |
| [[01 - Amazon Bedrock\|Amazon Bedrock]] | Um LLM também traduz, mas o Translate é **especializado**, mais barato, previsível e tem terminologia controlada |

> [!tip] Pipeline clássico: tradução de voz
> **Transcribe** (fala → texto) → **Translate** (texto → outro idioma) → **Polly** (texto → fala).
> Exemplo: um atendente brasileiro conversando por voz com um cliente japonês.

> [!warning] Pegadinhas de prova
> - "Traduzir **áudio**" → o Translate sozinho **não** faz. Use o pipeline acima.
> - "Garantir que o **nome da marca** seja sempre traduzido do mesmo jeito" → **Terminologia personalizada**.
> - "Traduzir milhares de arquivos de uma vez" → **Tradução em lote** com o S3.

## Exemplo para Associação Mental

**O Intérprete com Glossário.** *Translate* = **traduzir**. É um intérprete profissional que carrega um **glossário da empresa** (terminologia personalizada) e um **caderno de exemplos** de como a empresa escreve (dados paralelos). Ele só trabalha com **papel escrito**: se alguém falar, outro colega precisa anotar primeiro (Transcribe).

## 📝 Meu entendimento

> Basicamente um serviço tradutor, serve para traduzir textos não estruturados e pode ser configurada formas de traduzir exemplo de tradução não literal para nomes específicos podem ser configuradas

---
Resumo: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · Anterior: [[01 - Amazon Comprehend|Amazon Comprehend]] · Próximo: [[04 - Amazon Transcribe|Amazon Transcribe]]

Fontes: [O que é o Amazon Translate](https://docs.aws.amazon.com/pt_br/translate/latest/dg/what-is.html) · [Amazon Translate](https://aws.amazon.com/pt/translate/)
