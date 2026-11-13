## Resumo

O **Amazon Kendra** é um serviço de **busca corporativa inteligente**. Ele usa ML para entender **perguntas em linguagem natural** e encontrar a **resposta exata** dentro dos documentos da empresa (SharePoint, S3, Confluence, Salesforce…), e não só uma lista de links por palavra-chave.

> [!info] Ideia central
> **Pergunta em linguagem natural → resposta/trecho exato nos documentos da empresa.** É o "Google interno" da empresa.
> 🔑 Palavras-chave na prova: "**busca corporativa**", "**enterprise search**", "**pesquisar documentos internos**", "**perguntas em linguagem natural**", "**intranet**".

> [!warning] Status 2026: em manutenção
> O Kendra entrou em **modo de manutenção em 30/06/2026** e **não aceita novos clientes desde 30/07/2026**. Quem já usa continua normalmente. A AWS recomenda migrar para o **Amazon Bedrock (Managed) Knowledge Base** → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]].
> **Na prova** (guia v1.4), o Kendra continua no escopo: responda pelo **conceito** de busca corporativa.

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Busca inteligente (NLP + ML) |
| **Entrada** | Pergunta em linguagem natural + documentos indexados de várias fontes |
| **Saída** | **Resposta direta**, trechos relevantes, FAQ correspondente e documentos ranqueados |
| **Precisa saber ML?** | Não |
| **Customização** | Sinônimos, ajuste de relevância, metadados e **aprendizado incremental** com o feedback dos usuários |
| **Modos** | Consulta em tempo real sobre um **índice** |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐ |
| **Status 2026** | ⚠️ Manutenção (sem novos clientes desde 30/07/2026) |

## Principais recursos

| Recurso | O que faz |
|---|---|
| **Busca semântica** | Entende o **significado** da pergunta, não só palavras-chave |
| **Respostas diretas** | Devolve o **trecho exato** que responde ("O reembolso leva 5 dias úteis") |
| **Conectores** (30+) | S3, SharePoint, Confluence, Salesforce, ServiceNow, OneDrive, bancos de dados… |
| **Controle de acesso** | Mostra a cada usuário **só os documentos que ele pode ver** |
| **Aprendizado incremental** | Melhora o ranking com base nos **cliques e avaliações** dos usuários |
| **Retriever para RAG** | A API *Retrieve* entrega trechos para um LLM gerar respostas (RAG) |

## Casos de uso

| Cenário | Como o Kendra ajuda |
|---|---|
| **Intranet / RH** | Funcionário pergunta "quantos dias de férias tenho?" e recebe a resposta da política |
| **Suporte técnico** | Atendente encontra a solução nos manuais em segundos |
| **Portal do cliente** | Busca inteligente na base de conhecimento pública |
| **Jurídico e pesquisa** | Encontrar cláusulas e trechos em milhares de documentos |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[01 - Amazon Bedrock\|Amazon Bedrock]] Knowledge Bases | Faz **RAG**: busca **e gera** uma resposta nova com LLM. O Kendra **encontra** a resposta existente. É o **sucessor** recomendado |
| [[16 - Amazon Q\|Amazon Q]] Business | Assistente **pronto** que conversa sobre os dados da empresa (também em manutenção em 2026) |
| **Amazon OpenSearch** | Mecanismo de busca que **você configura e opera**. O Kendra é busca inteligente **gerenciada** |
| [[01 - Amazon Comprehend\|Amazon Comprehend]] | O Comprehend **analisa** um texto. O Kendra **pesquisa** em muitos documentos |
| [[08 - Amazon Textract\|Amazon Textract]] | O Textract **extrai** texto de documentos. O Kendra **busca** neles |

> [!warning] Pegadinhas de prova
> - "Funcionários precisam **pesquisar** documentos internos com **perguntas em linguagem natural**" → **Kendra**.
> - "Gerar uma **resposta nova** com base nos documentos" → **Bedrock Knowledge Bases (RAG)**.
> - "Busca que **respeita as permissões** de cada usuário" → **Kendra** (ou Q Business).

## Exemplo para Associação Mental

**O Bibliotecário Expert.** Você não procura no índice por palavra: você **pergunta** "qual é a política de reembolso?" e o bibliotecário vai direto ao livro certo, abre na página e **aponta o parágrafo**. Ele sabe **quais livros você tem permissão para ler** e aprende com o tempo quais respostas as pessoas acham mais úteis.

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, o que entendeu sobre o Kendra._

---
Resumo: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · Anterior: [[08 - Amazon Textract|Amazon Textract]] · Próximo: [[10 - Amazon Personalize|Amazon Personalize]]

Fontes: [Amazon Kendra](https://aws.amazon.com/pt/kendra/) · [Kendra: mudança de disponibilidade](https://docs.aws.amazon.com/kendra/latest/dg/kendra-availability-change.html)
