## Resumo

O **Amazon Transcribe** é o serviço de **reconhecimento automático de fala** (*ASR, Automatic Speech Recognition*) da AWS. Ele converte **áudio em texto**, tanto de **arquivos gravados** quanto de **áudio ao vivo (streaming)**. Você pode usá-lo como serviço de transcrição independente ou colocar a conversão de fala em texto em qualquer aplicação.

> [!info] Ideia central
> **Fala → texto.** O Transcribe **escreve o que foi dito**, mas não entende a intenção nem responde.
> 🔑 Palavras-chave na prova: "**transcrever**", "**legendas**", "**speech-to-text**", "**ligações do call center**", "**identificar quem falou**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Fala (ASR) |
| **Entrada** | Áudio/vídeo (arquivo no S3 ou streaming em tempo real) |
| **Saída** | Texto com **timestamps**, nível de confiança por palavra e falantes identificados |
| **Precisa saber ML?** | Não. Modelo de fala pré-treinado com bilhões de parâmetros |
| **Customização** | **Vocabulário personalizado** e **modelo de linguagem personalizado** |
| **Modos** | Lote (arquivos) · Streaming (tempo real) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐⭐ |
| **Status 2026** | ✅ Disponível |

## Principais recursos

| Recurso | O que faz |
|---|---|
| **Identificação automática de idioma** | Descobre o idioma falado e lida com áudio **multilíngue** |
| **Identificação de falantes** (*speaker diarization*) | Separa **quem falou o quê** ("Falante 1", "Falante 2") |
| **Identificação de canal** | Separa atendente e cliente em canais diferentes |
| **Redação de PII** | **Remove/mascara** dados pessoais (CPF, cartão, telefone) da transcrição |
| **Filtro de vocabulário** | Esconde palavras indesejadas (ex.: palavrões) |
| **Detecção de toxicidade** | Sinaliza fala ofensiva em áudio |
| **Vocabulário personalizado** | Ensina **termos técnicos**, nomes de produtos e siglas |
| **Modelo de linguagem personalizado** | Treina o modelo com textos do seu **domínio** para mais precisão |
| **Legendas** | Gera arquivos de legenda **SRT/VTT** |
| **Transcribe Call Analytics** | Para call centers: sentimento, problemas, resumo da ligação, tempo de fala |
| **Transcribe Medical** | Transcrição de termos médicos (consultas, ditados clínicos) |

## Como medir a qualidade: WER

A qualidade de uma transcrição é medida pela **WER** (*Word Error Rate*): **(substituições + deleções + inserções) ÷ palavras da referência humana**. **Quanto menor, melhor** (WER 5% ≈ 95% de acerto). Para **reduzir a WER**: **vocabulário personalizado** (termos técnicos, nomes) e **modelo de linguagem personalizado** (textos do seu domínio). → [[03 - Métricas de Avaliação - Resumo, Tradução e Transcrição|Métricas de Avaliação - Resumo, Tradução e Transcrição]]

## Casos de uso

| Cenário | Como o Transcribe ajuda |
|---|---|
| **Call center** | Transcreve ligações para análise de qualidade e sentimento |
| **Legendas e acessibilidade** | Legendas automáticas para vídeos e eventos ao vivo |
| **Busca em mídia** | Torna áudios e vídeos **pesquisáveis** por texto |
| **Atas de reunião** | Transcreve reuniões separando os participantes |
| **Saúde** | Documentação clínica a partir da fala do médico |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[05 - Amazon Polly\|Amazon Polly]] | **Polly é o oposto**: texto → fala. Transcribe: fala → texto |
| [[06 - Amazon Lex\|Amazon Lex]] | O Lex também "ouve" (usa ASR por dentro), mas **entende a intenção e conversa**. O Transcribe só **escreve** o que foi dito |
| [[01 - Amazon Comprehend\|Amazon Comprehend]] | O Comprehend **analisa** o texto que o Transcribe gerou (sentimento, entidades) |
| [[03 - Amazon Translate\|Amazon Translate]] | O Translate **traduz** o texto. O Transcribe mantém o idioma original |

> [!tip] Dica para lembrar
> **Trans*crib*e** = **escriba** (quem escreve). **Pol*ly*** = papagaio (quem **fala**).

> [!warning] Pegadinhas de prova
> - "Converter **gravações de ligações** em texto" → **Transcribe**.
> - "Remover **dados pessoais** das transcrições" → recurso de **redação de PII** do Transcribe.
> - "Entender o **sentimento** da ligação" → Transcribe **+ Comprehend** (ou Transcribe Call Analytics).
> - "Termos técnicos sendo transcritos errado" → **Vocabulário personalizado**.

## Exemplo para Associação Mental

**O Taquígrafo do Tribunal.** Ele escreve **tudo o que é dito**, anota **quem falou** (diarização) e a **hora** (timestamps). Por ordem do juiz, ele **tarja os dados pessoais** (PII). Mas ele **não opina**, **não responde** e **não traduz**: só escreve.

## 📝 Meu entendimento

> **O que faz:** Converte Fala para Texto
> **Como faz:** Por meio de ASR (Automatic Speech Recognition)
> **Características:**
> - PII (Person Indentify Information) - Não mostra e traduz informações pessoais
> - e multilanguage

> [!note] Correção de um detalhe
> No Transcribe, PII é **Personally Identifiable Information**. O recurso **esconde/mascara** os dados pessoais na transcrição (*redaction*), mas **não traduz** nada. Tradução é com o [[03 - Amazon Translate|Amazon Translate]].

---
Resumo: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · Anterior: [[03 - Amazon Translate|Amazon Translate]] · Próximo: [[05 - Amazon Polly|Amazon Polly]]

Fontes: [Amazon Transcribe](https://aws.amazon.com/pt/transcribe/) · [Recursos do Amazon Transcribe](https://aws.amazon.com/pt/transcribe/features/)
