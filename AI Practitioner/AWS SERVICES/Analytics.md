## Resumo

Serviços da categoria **Analytics** no escopo da AIF-C01. Na prova, aparecem como **apoio** ao ciclo de ML e GenAI: **conseguir dados**, **preparar dados**, **guardar e governar** o data lake, **buscar vetores** para RAG e **visualizar** resultados.

> [!info] Ideia central
> Pense no caminho do dado: **comprar** (Data Exchange) → **preparar** (Glue, DataBrew, EMR) → **governar** (Lake Formation) → **analisar** (Redshift) → **buscar por significado** (OpenSearch) → **mostrar e agir** (Amazon Quick).

| Serviço | Em uma linha | Prioridade |
|---|---|---|
| **AWS Data Exchange** | Encontrar, assinar e usar **dados de terceiros** | ⭐ |
| **Amazon EMR** | **Big data** com Spark/Hadoop gerenciado | ⭐ |
| **AWS Glue** | **ETL serverless** + **Data Catalog** | ⭐⭐ |
| **AWS Glue DataBrew** | Preparação de dados **visual, sem código** | ⭐⭐ |
| **AWS Lake Formation** | Criar e **governar permissões** de um data lake | ⭐ |
| **Amazon OpenSearch Service** | Busca, análise de logs e **banco vetorial** para RAG | ⭐⭐⭐ |
| **Amazon Quick** | Espaço de trabalho com **agentes de IA**, **BI (Quick Sight)** e automação | ⭐⭐ |
| **Amazon Redshift** | **Data warehouse** SQL | ⭐ |

---

## AWS Data Exchange
Catálogo para **encontrar, assinar e usar dados de terceiros** (mercado financeiro, clima, demografia) direto na AWS.
- **Com IA:** enriquecer um dataset de treino com dados externos licenciados.
- Palavra-chave: "**dados de terceiros**", "**assinar datasets**".

## Amazon EMR
Clusters gerenciados de **Apache Spark, Hadoop, Hive, Presto** para processar **grandes volumes**.
- **Com IA:** processar **terabytes** de dados brutos antes do treino; engenharia de dados em escala.
- Palavra-chave: "**Spark**", "**Hadoop**", "**petabytes**".

## AWS Glue
**ETL serverless** (extrair, transformar, carregar) + **Glue Data Catalog** (metadados e esquemas das tabelas) + crawlers que descobrem esquemas.
- **Com IA:** limpar e juntar dados de várias fontes para treino; o **Data Catalog** ajuda na **linhagem e catalogação** de dados (Domínio 5).
- Palavra-chave: "**ETL**", "**catálogo de dados**", "**serverless**".

> [!warning] Pegadinha
> Glue **não** descobre PII com segurança: para dados sensíveis no S3 a resposta é **Macie** (questão #55 do simulado).

## AWS Glue DataBrew
Preparação de dados **visual e sem código**, com centenas de transformações prontas (remover nulos, normalizar, mascarar colunas) e perfil de qualidade dos dados.
- **Com IA:** analista prepara o dataset sem programar.
- Não confunda com **SageMaker Data Wrangler** (preparação visual **dentro do SageMaker**, voltada a ML) e **SageMaker Canvas** (ML **sem código**).

## AWS Lake Formation
Cria um **data lake** no S3 e centraliza **permissões finas** (por banco, tabela, coluna e linha).
- **Com IA:** "cientistas de dados só podem ver as colunas **não sensíveis**" → Lake Formation.
- Palavra-chave: "**governança do data lake**", "**permissão por coluna/linha**".

## Amazon OpenSearch Service
Busca de texto, análise de logs e **mecanismo vetorial** (busca por similaridade de **embeddings**). Existe em modo **gerenciado** e **Serverless**.
- **Com IA:** **banco vetorial** mais comum para **RAG**. O **OpenSearch Serverless** é a opção padrão quando o Bedrock cria uma **Knowledge Base** automaticamente.
- Palavra-chave: "**busca vetorial**", "**embeddings**", "**busca semântica**", "**k-NN**".
- Detalhes: [[Beadrock Rag - Kb]]

## Amazon Quick
Novo nome da família que veio do **Amazon QuickSight** (2025: *Quick Suite*; 2026: *Amazon Quick*). Reúne:
- **Quick Sight**: **dashboards de BI** e perguntas em linguagem natural sobre os dados (o antigo *Q in QuickSight*).
- **Agentes e chat** sobre dados e documentos da empresa, pesquisa e **automação de fluxos**. É o **sucessor indicado do Amazon Q Business** → [[Amazon Q]].
- Palavra-chave: "**dashboard**", "**BI**", "**perguntar aos dados em linguagem natural**", "**assistente de trabalho com dados da empresa**".

> [!tip] Questões antigas
> Se a alternativa disser **QuickSight** ou **Q in QuickSight**, trate como **Amazon Quick (Quick Sight)**: é o mesmo conceito de BI.

## Amazon Redshift
**Data warehouse** colunar para consultas **SQL analíticas** em grande escala. Tem **Redshift ML** (treinar/usar modelos com SQL) e integração com Bedrock.
- **Com IA:** fonte de dados estruturados para análises e para modelos; o Bedrock Knowledge Base pode consultar dados estruturados no Redshift (pergunta em linguagem natural → SQL).
- Palavra-chave: "**data warehouse**", "**SQL analítico**", "**BI em petabytes**".

---

## Lado a lado: preparar dados

| Ferramenta | Quem usa | Código? |
|---|---|---|
| **Glue** | Engenheiro de dados | Sim (ou visual no Glue Studio) |
| **Glue DataBrew** | Analista | **Não** |
| **EMR** | Engenheiro de big data | Sim (Spark) |
| **SageMaker Data Wrangler** | Cientista de dados, dentro do SageMaker | Pouco → [[SageMaker - Data Tools]] |

## Fora do escopo
AWS Clean Rooms, Amazon CloudSearch, Amazon MSK.

## Exemplo para Associação Mental

**A cozinha do restaurante.** O **Data Exchange** é o **fornecedor** que vende ingredientes. **Glue** e **EMR** são os **cozinheiros** que lavam e cortam (EMR é a cozinha industrial). O **DataBrew** é o **processador** que qualquer um usa sem saber cozinhar. O **Lake Formation** é o **despenseiro** que decide quem pega o quê. O **Redshift** é o **estoque organizado** para consultas. O **OpenSearch** é o **sommelier** que acha o vinho **parecido** com o que você gostou (busca por similaridade). O **Amazon Quick** é o **painel do gerente** com um assistente que responde perguntas.

---
Voltar: [[07 - Serviços AWS do Exame]] · Relacionadas: [[Beadrock Rag - Kb]] · [[SageMaker - Data Tools]] · [[Amazon Q]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [Amazon Quick](https://docs.aws.amazon.com/quicksuite/latest/userguide/what-is.html) · [AWS Glue](https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html) · [OpenSearch vector search](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/knn.html)
