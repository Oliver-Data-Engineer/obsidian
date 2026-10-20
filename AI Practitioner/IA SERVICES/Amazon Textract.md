## Resumo

O **Amazon Textract** extrai automaticamente **texto, escrita à mão e dados estruturados** (formulários e tabelas) de **documentos escaneados, PDFs e imagens**. Ele vai além do OCR tradicional: entende a **estrutura** do documento e devolve pares **campo → valor** e **tabelas** prontas para usar.

> [!info] Ideia central
> **Documento (imagem/PDF) → texto + campos + tabelas.** É o "digitador" da AWS: tira os dados do papel.
> 🔑 Palavras-chave na prova: "**extrair texto de documentos**", "**OCR**", "**formulários**", "**tabelas**", "**notas fiscais/recibos**", "**documentos escaneados**", "**escrita à mão**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Documentos (OCR inteligente) |
| **Entrada** | Imagens (JPEG/PNG/TIFF) e **PDFs** (no S3 ou enviados direto) |
| **Saída** | JSON com texto, linhas, palavras, **pares chave-valor**, **tabelas**, assinaturas e confiança |
| **Precisa saber ML?** | Não. Modelos pré-treinados |
| **Customização** | **Queries** (perguntas em linguagem natural sobre o documento) e **Adapters** (ajuste com exemplos dos seus documentos) |
| **Modos** | Síncrono (1 página) · Assíncrono (documentos com várias páginas) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐ |
| **Status 2026** | ✅ Disponível |

## Principais recursos

| Recurso / API | O que faz | Exemplo |
|---|---|---|
| **Detect Document Text** | OCR: extrai **texto impresso e manuscrito** | Digitalizar cartas antigas |
| **Analyze Document · Forms** | Extrai **pares chave-valor** | "Nome: Maria", "CPF: 123…" |
| **Analyze Document · Tables** | Extrai **tabelas** mantendo linhas e colunas | Extrato bancário |
| **Analyze Document · Queries** | Responde a **perguntas** sobre o documento | "Qual é a data de vencimento?" |
| **Analyze Document · Signatures / Layout** | Detecta **assinaturas** e a estrutura (títulos, parágrafos) | Contratos |
| **Analyze Expense** | Especializado em **notas fiscais e recibos** | Fornecedor, total, impostos, itens |
| **Analyze ID** | Extrai dados de **documentos de identidade** | Passaporte, carteira de motorista |
| **Analyze Lending** | Classifica e extrai dados de documentos de **financiamento** | Processo de crédito imobiliário |
| **Integração com A2I** | Envia campos de **baixa confiança** para revisão humana | Formulário com letra difícil |

## Casos de uso

| Cenário | Como o Textract ajuda |
|---|---|
| **Contas a pagar** | Lê notas fiscais e recibos automaticamente (Analyze Expense) |
| **Onboarding de clientes** | Extrai dados de documentos de identidade |
| **Seguros e saúde** | Processa formulários de sinistro e fichas de pacientes |
| **Financiamentos** | Automatiza a análise de documentos de crédito |
| **Digitalização de arquivo** | Torna documentos antigos **pesquisáveis** |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon Rekognition]] | O Rekognition lê textos **curtos em fotos de cenas** (placas). O Textract lê **documentos** e entende formulários e tabelas |
| [[Amazon Comprehend]] | O Textract **extrai** o texto. O Comprehend **entende** o texto (sentimento, entidades). Pipeline comum: Textract → Comprehend |
| [[Amazon Augmented AI]] | O A2I faz a **revisão humana** dos campos em que o Textract ficou em dúvida |
| [[Amazon Kendra]] | O Kendra **busca** dentro de documentos. O Textract **extrai** os dados deles |

> [!tip] Pipeline clássico: processamento inteligente de documentos (IDP)
> **Textract** (extrai) → **Comprehend** (classifica e encontra entidades) → **A2I** (humano revisa os casos duvidosos) → banco de dados.

> [!warning] Pegadinhas de prova
> - "Extrair dados de **formulários** e **tabelas** de PDFs escaneados" → **Textract**.
> - "Processar **notas fiscais/recibos**" → **Textract (Analyze Expense)**.
> - "OCR simples sem estrutura" também é Textract, mas a vantagem dele é a **estrutura** (chave-valor e tabelas).

## Exemplo para Associação Mental

**O Digitador Perfeito.** *Textract* = **text + extract** (extrair texto). É o funcionário que recebe uma pilha de **formulários em papel** e preenche a planilha: sabe que "Nome:" é o **campo** e "Maria" é o **valor**, copia as **tabelas** linha por linha e até entende **letra de mão**.

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, o que entendeu sobre o Textract._

---
Resumo: [[Resumo]] · Anterior: [[Amazon Rekognition]] · Próximo: [[Amazon Kendra]]

Fontes: [Amazon Textract](https://aws.amazon.com/pt/textract/) · [Recursos do Amazon Textract](https://aws.amazon.com/pt/textract/features/)
