## Resumo

Serviços da categoria **Database** no escopo da AIF-C01. Para a prova, o mais importante é saber **quais servem como banco vetorial** (para guardar **embeddings** no **RAG**) e qual é o tipo de cada banco.

> [!info] Ideia central
> Pergunta da prova: "**onde guardar os embeddings** para o RAG?" → **OpenSearch** (padrão), **Aurora / RDS PostgreSQL (pgvector)**, **Neptune** (grafos), **DocumentDB**. O **DynamoDB** não é banco vetorial nativo.

| Serviço | Tipo | Busca vetorial? | Prioridade |
|---|---|---|---|
| **Amazon Aurora** | Relacional (MySQL/PostgreSQL), alto desempenho | ✅ **Aurora PostgreSQL + pgvector** (suportado pelo Bedrock KB) | ⭐⭐⭐ |
| **Amazon RDS** | Relacional gerenciado (PostgreSQL, MySQL, Oracle, SQL Server...) | ✅ **RDS for PostgreSQL + pgvector** | ⭐⭐ |
| **Amazon DocumentDB** | Documentos JSON (compatível com MongoDB) | ✅ Busca vetorial nativa | ⭐⭐ |
| **Amazon Neptune** | **Grafos** (relações entre entidades) | ✅ **Neptune Analytics** (usado no **GraphRAG** do Bedrock KB) | ⭐⭐ |
| **Amazon DynamoDB** | NoSQL **chave-valor**, serverless, milissegundos | ❌ (não é vetorial nativo) | ⭐⭐ |
| **Amazon ElastiCache** | **Cache em memória** (Valkey, Redis OSS, Memcached) | ✅ Valkey suporta vetores (ex.: **cache semântico** de respostas) | ⭐ |

---

## Amazon Aurora
Banco **relacional** da AWS, compatível com **MySQL** e **PostgreSQL**, mais rápido e altamente disponível (réplicas em 3 AZs). Tem versão **Serverless**.
- **Com IA:** **Aurora PostgreSQL com pgvector** é um dos **vector stores** aceitos pelas **Bedrock Knowledge Bases**; bom quando a empresa **já usa PostgreSQL** e quer dados relacionais e vetores juntos.

## Amazon RDS
Bancos **relacionais gerenciados** (a AWS cuida de backup, patches, réplicas).
- **Com IA:** **RDS for PostgreSQL + pgvector** guarda embeddings; fonte de dados estruturados para apps de IA.
- Aurora x RDS: Aurora é o motor **da AWS** com mais desempenho e escala; RDS roda motores **padrão** do mercado.

## Amazon DocumentDB (compatível com MongoDB)
Banco de **documentos JSON**, compatível com a API do MongoDB, com **busca vetorial**.
- **Com IA:** guardar documentos e embeddings juntos quando a aplicação já usa MongoDB.

## Amazon Neptune
Banco de **grafos** (nós e relações: "cliente → comprou → produto").
- **Com IA:** **GraphRAG**: o Bedrock Knowledge Base pode usar o **Neptune Analytics** para combinar busca vetorial com as **relações** entre entidades, melhorando respostas que dependem de conexões. Também detecção de fraude por relações e recomendação.
- Palavra-chave: "**relações**", "**grafo de conhecimento**", "**GraphRAG**".

## Amazon DynamoDB
NoSQL **chave-valor** e documento, **serverless**, latência de **milissegundos** em qualquer escala.
- **Com IA:** guardar **histórico de conversa / estado da sessão** de um chatbot, metadados, perfis de usuário, resultados de inferência.
- **Não** é a resposta para "banco vetorial" (para isso, integração zero-ETL com OpenSearch).

## Amazon ElastiCache
**Cache em memória** gerenciado (Valkey, Redis OSS, Memcached) para respostas em **microssegundos**.
- **Com IA:** **cache de respostas** do LLM para perguntas repetidas (reduz **custo e latência**); com vetores (Valkey), **cache semântico**: reaproveita a resposta de uma pergunta **parecida**.

> [!note] Saiu da lista
> **Amazon MemoryDB** (banco em memória durável, compatível com Redis, com busca vetorial) **não aparece mais** na lista oficial atual. **Aurora** entrou.

---

## Onde guardar os vetores do RAG (resumo para a prova)

| Situação | Escolha |
|---|---|
| Padrão, sem preferência, "menor esforço" ao criar uma Knowledge Base | **OpenSearch Serverless** → [[Analytics#Amazon OpenSearch Service]] |
| A empresa já usa **PostgreSQL** | **Aurora PostgreSQL** ou **RDS for PostgreSQL** (pgvector) |
| Dados com muitas **relações** entre entidades | **Neptune Analytics** (GraphRAG) |
| Aplicação já usa **MongoDB** | **DocumentDB** |
| Guardar **histórico do chat** / sessão | **DynamoDB** |
| **Cache** de respostas repetidas | **ElastiCache** |

Detalhes do fluxo de RAG: [[Beadrock Rag - Kb]]

## Fora do escopo
Amazon Keyspaces, Amazon Timestream.

## Exemplo para Associação Mental

**A biblioteca.** O **Aurora/RDS** é o **fichário** organizado em tabelas. O **DocumentDB** é a **pasta de documentos** soltos. O **Neptune** é o **mural de investigação** com barbantes ligando as fotos. O **DynamoDB** é o **guarda-volumes** numerado: você dá o número e pega na hora. O **ElastiCache** é o **post-it** na mesa com as respostas mais pedidas. E o **OpenSearch** é o **bibliotecário** que acha livros **parecidos** com o que você descreveu.

---
Voltar: [[07 - Serviços AWS do Exame]] · Relacionadas: [[Beadrock Rag - Kb]] · [[Analytics]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [Vector stores for Bedrock Knowledge Bases](https://docs.aws.amazon.com/bedrock/latest/userguide/knowledge-base-setup.html) · [Amazon Aurora](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html) · [Amazon Neptune Analytics](https://docs.aws.amazon.com/neptune-analytics/latest/userguide/what-is-neptune-analytics.html)
