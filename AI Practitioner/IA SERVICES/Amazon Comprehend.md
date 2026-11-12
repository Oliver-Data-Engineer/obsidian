## Resumo

O **Amazon Comprehend** é o serviço de **processamento de linguagem natural (NLP)** da AWS. Ele lê um **texto** e devolve **insights** em JSON: idioma, sentimento, entidades (pessoas, lugares, datas), frases-chave, dados pessoais (PII) e mais. Você só chama a API: não precisa treinar nenhum modelo de NLP.

> [!info] Ideia central
> **Texto → insights (JSON).** O Comprehend **entende** o texto. Ele não traduz, não gera texto novo e não lê imagens.
> 🔑 Palavras-chave na prova: "**análise de sentimento**", "**extrair entidades**", "**frases-chave**", "**detectar PII em texto**", "**classificar documentos**", "**idioma do texto**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Linguagem (NLP) |
| **Entrada** | Texto (UTF-8) ou documentos no **S3** |
| **Saída** | JSON com entidades, sentimento, frases-chave, idioma, PII… e **nível de confiança** |
| **Precisa saber ML?** | Não. Modelos **pré-treinados**, prontos por API |
| **Customização** | **Custom classification** e **custom entity recognition** (você dá exemplos rotulados e ele treina por você) |
| **Modos** | Tempo real (síncrono) · Lote (jobs assíncronos no S3) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐⭐ |
| **Status 2026** | ✅ Disponível · ⚠️ *Topic modeling*, *event detection* e *prompt safety classification* fechados para novos clientes (desde 30/04/2026) |

## Principais recursos

| Recurso | O que faz | Exemplo |
|---|---|---|
| **Detecção de idioma** | Identifica o idioma dominante | "Este texto está em espanhol" |
| **Análise de sentimento** | Positivo, negativo, neutro ou misto | Avaliação de produto → *NEGATIVE 0,97* |
| **Sentimento direcionado** (*targeted*) | Sentimento **por entidade** dentro do texto | "Comida ótima (+), atendimento lento (−)" |
| **Reconhecimento de entidades** | Pessoas, lugares, organizações, datas, quantidades | "Sam Ford" → PERSON |
| **Frases-chave** | Os trechos mais importantes do texto | "acidente de carro", "acionar o seguro" |
| **Detecção de PII** | Encontra e **mascara** dados pessoais | CPF, e-mail, telefone, cartão |
| **Detecção de toxicidade** | Identifica conteúdo ofensivo | Moderação de comentários |
| **Análise sintática** | Classes gramaticais (substantivo, verbo…) | Pré-processamento de texto |
| **Classificação personalizada** | Classifica nas **suas** categorias | Tickets → "Cobrança", "Suporte", "Cancelamento" |
| **Entidades personalizadas** | Reconhece entidades do **seu negócio** | Número de apólice, código de produto |
| **Comprehend Medical** | Entidades médicas e **PHI** em textos clínicos → [[Amazon Comprehend Medical]] | Medicamentos, dosagens, diagnósticos |

### Exemplo: entidade personalizada

Uma seguradora quer encontrar **números de apólice** nas mensagens dos clientes.

**Texto:** *"Olá, meu nome é Sam Ford e preciso acionar o seguro devido a um acidente de carro. O código da minha apólice é 456-YQT."*

| Entidade | Categoria | Contagem | Confiança |
|---|---|---|---|
| 456-YQT | ID da Apólice | 1 | 0.95 |

## Casos de uso

| Cenário | Como o Comprehend ajuda |
|---|---|
| **Voz do cliente** | Sentimento de avaliações, pesquisas e redes sociais |
| **Triagem de tickets** | Classificação automática por assunto e urgência |
| **Compliance / LGPD** | Detectar e mascarar PII antes de armazenar textos |
| **Análise de ligações** | Transcribe (áudio → texto) + Comprehend (sentimento) |
| **Organização de documentos** | Extrair entidades e frases-chave para indexar |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon Textract]] | O Textract **extrai** o texto de imagens e PDFs. O Comprehend **analisa o significado** do texto. Os dois costumam ser usados juntos |
| [[Amazon Translate]] | O Translate **traduz** o texto. O Comprehend **entende** o texto |
| [[Amazon Kendra]] | O Kendra **busca** respostas em documentos. O Comprehend **analisa** um texto |
| [[Amazon Bedrock]] | O Bedrock **gera** texto novo (LLM). O Comprehend **extrai** informações com modelos especializados, mais baratos e previsíveis |
| [[Amazon Comprehend Medical]] | Versão para **saúde**: entidades médicas, PHI e códigos ICD-10/RxNorm. Texto **clínico** → Medical |
| **Amazon Macie** | O Macie encontra PII em **buckets S3**. O Comprehend encontra PII em um **texto** enviado para a API |

> [!warning] Pegadinhas de prova
> - "Saber se o cliente está **satisfeito** pelos comentários" → **Comprehend (sentimento)**.
> - "Texto está **dentro de uma imagem/PDF escaneado**" → primeiro **Textract**, depois Comprehend.
> - "Áudio de ligação" → primeiro **Transcribe**, depois Comprehend.
> - "Categorias **próprias** da empresa" → **Custom classification** (não precisa ir para o SageMaker).

## Exemplo para Associação Mental

**O Leitor Atento.** *Comprehend* = **compreender**. Imagine um analista que lê uma carta e marca com canetas coloridas: **verde/vermelho** para o humor (sentimento), **amarelo** para nomes e datas (entidades), **azul** para as ideias principais (frases-chave) e **tarja preta** sobre o CPF (PII). Ele não escreve nada novo, só **entende e marca**.

## 📝 Meu entendimento

> O Amazon Comprehend é um serviço para facilitar a integração de modelos de NLP, facilitando assim trabalhos como analise de sentimento, classificação, categorização, cenários onde seriam necessários trinar um modelo complexo de NPL para extrair informações de texto o Amazon Comprehend faz, podendo analisar diretamente documento ou texto de diferentes formas e com N objetivos, como analise de sentimento, identificação de localidade, identificação de pernoas e identidades

---
Resumo: [[Resumo]] · Próximo: [[Amazon Translate]]

Fontes: [Recursos do Amazon Comprehend](https://aws.amazon.com/pt/comprehend/features/) · [Comprehend: mudança de disponibilidade](https://docs.aws.amazon.com/comprehend/latest/dg/comprehend-availability-change.html)
