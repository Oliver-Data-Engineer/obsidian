## Resumo

O **Amazon Polly** é o serviço de **conversão de texto em fala** (*TTS, Text-to-Speech*) da AWS. Ele transforma artigos, páginas web, PDFs e qualquer texto em **áudio com voz natural**, usando deep learning. Oferece dezenas de vozes realistas em muitos idiomas para criar aplicações que **falam**.

> [!info] Ideia central
> **Texto → fala (áudio).** O Polly **lê em voz alta**. Ele não entende nem responde.
> 🔑 Palavras-chave na prova: "**text-to-speech**", "**voz natural**", "**ler em voz alta**", "**acessibilidade**", "**audiobook**", "**pronúncia**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Fala (TTS) |
| **Entrada** | Texto simples ou **SSML** |
| **Saída** | Áudio (MP3, OGG, PCM) em **streaming** ou arquivo, mais *speech marks* opcionais |
| **Precisa saber ML?** | Não. Vozes prontas |
| **Customização** | **Léxicos** (pronúncia), **SSML** (entonação) e **Brand Voice** (voz exclusiva da marca) |
| **Modos** | Tempo real (streaming) · Lote (tarefas longas salvas no S3) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐⭐ |
| **Status 2026** | ✅ Disponível |

## Principais recursos

| Recurso | O que faz |
|---|---|
| **Motores de voz** | **Standard** (básico), **Neural** (mais natural), **Long-form** (textos longos, tom de narrador) e **Generative** (o mais expressivo, parecido com humano) |
| **SSML** (*Speech Synthesis Markup Language*) | Tags para controlar **pausas, ênfase, velocidade, tom, volume** e até **sussurro** |
| **Léxicos personalizados** | Ensinam a **pronúncia** de siglas, nomes de empresas e termos internos (ex.: "AWS" → "A-W-S") |
| **Speech marks** | Metadados que dizem **quando cada palavra é falada**: sincroniza **legenda destacada** ou **movimento da boca** de um avatar |
| **Estilos de fala** | Ex.: estilo **apresentador de notícias** (*newscaster*) |
| **Brand Voice** | Cria uma **voz exclusiva** para a marca (projeto com a equipe da AWS) |
| **Reaproveitar o áudio** | Você pode **guardar e reproduzir** o áudio gerado quantas vezes quiser |

## Casos de uso

| Cenário | Como o Polly ajuda |
|---|---|
| **Acessibilidade** | Ler conteúdo para pessoas com deficiência visual |
| **Conteúdo em áudio** | Transformar artigos e notícias em podcast ou audiobook |
| **URA / atendimento** | Mensagens faladas em centrais telefônicas (ex.: com Amazon Connect) |
| **E-learning** | Narração de cursos em vários idiomas |
| **Dispositivos e apps** | Respostas faladas em apps, carros e IoT |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon Transcribe]] | **O oposto**: fala → texto |
| [[Amazon Lex]] | O Lex **conversa** (entende e responde). Quando a resposta é falada, o Lex usa a mesma tecnologia de voz do Polly |
| [[Amazon Translate]] | O Translate **traduz** o texto. O Polly só **lê** o texto no idioma em que ele está |

> [!warning] Pegadinhas de prova
> - "Converter **texto em áudio**" → **Polly**.
> - "A voz pronuncia errado o **nome da empresa**" → **Léxico personalizado**.
> - "Adicionar **pausa** ou **ênfase** na fala" → **SSML**.
> - "Destacar cada palavra na tela **enquanto é falada**" → **Speech marks**.

## Exemplo para Associação Mental

**O Papagaio Locutor.** *Polly* é um nome clássico de papagaio. Ele **repete em voz alta** qualquer texto que você der, com a voz que escolher. Com o **léxico** você ensina a pronúncia certa, com o **SSML** você diz onde respirar e o que enfatizar. Mas ele **não entende** o que está falando.

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, o que entendeu sobre o Polly._

---
Resumo: [[Resumo]] · Anterior: [[Amazon Transcribe]] · Próximo: [[Amazon Lex]]

Fontes: [Amazon Polly](https://aws.amazon.com/pt/polly/) · [Recursos do Amazon Polly](https://aws.amazon.com/pt/polly/features/)
