## Resumo

Serviços AWS que o guia lista como **dentro do escopo**, organizados por categoria, cada um com uma descrição curta e sua prioridade para a prova. No fim, os serviços **fora do escopo**, que você pode ignorar. A AWS avisa que as duas listas não são exaustivas e podem mudar.

> [!info] Ideia central
> Foque nos serviços de **Machine Learning** (⭐⭐⭐) e nos de **segurança/governança** (⭐⭐). Os demais basta reconhecer pelo nome e saber para que servem.

## ✅ Dentro do escopo

### Machine Learning — ⭐⭐⭐ (prioridade máxima)

| Serviço                       | Para que serve                                                                                                                                                                            |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon Bedrock**            | FMs via API serverless; Knowledge Bases (RAG), Agents, Guardrails, Model Evaluation, Prompt Management                                                                                    |
| **Amazon SageMaker**          | Plataforma completa de ML: preparar, treinar, ajustar, implantar e monitorar (Studio, JumpStart, Clarify, Model Monitor, Data Wrangler, Feature Store, Ground Truth, Model Cards, Canvas) |
| **Amazon Q**                  | Assistente de GenAI: Q Business (dados da empresa) e Q Developer (código)                                                                                                                 |
| **Amazon Augmented AI (A2I)** | Revisão **humana** de previsões de ML                                                                                                                                                     |
| **Amazon Comprehend**         | NLP: sentimento, entidades, frases-chave, idioma, PII em texto                                                                                                                            |
| **Amazon Fraud Detector**     | Detecção de fraude online                                                                                                                                                                 |
| **Amazon Kendra**             | Busca corporativa inteligente em documentos                                                                                                                                               |
| **Amazon Lex**                | Chatbots de voz e texto (a tecnologia da Alexa)                                                                                                                                           |
| **Amazon Personalize**        | Recomendações personalizadas                                                                                                                                                              |
| **Amazon Polly**              | Texto → fala                                                                                                                                                                              |
| **Amazon Rekognition**        | Análise de imagem e vídeo (objetos, rostos, moderação)                                                                                                                                    |
| **Amazon Textract**           | Extrai texto, formulários e tabelas de documentos                                                                                                                                         |
| **Amazon Transcribe**         | Fala → texto                                                                                                                                                                              |
| **Amazon Translate**          | Tradução automática                                                                                                                                                                       |

### Segurança, Identidade e Compliance — ⭐⭐

| Serviço | Para que serve |
|---|---|
| **AWS IAM** | Usuários, roles, políticas e permissões |
| **AWS KMS** | Gerenciamento de chaves de criptografia |
| **Amazon Macie** | Descobre dados sensíveis (PII) no S3 |
| **AWS Secrets Manager** | Armazena e rotaciona segredos |
| **Amazon Inspector** | Varredura de vulnerabilidades |
| **AWS Artifact** | Relatórios de compliance da AWS (ISO, SOC…) |
| **AWS Audit Manager** | Automatiza a coleta de evidências de auditoria |

### Gerenciamento e Governança — ⭐⭐

| Serviço | Para que serve |
|---|---|
| **AWS CloudTrail** | Log de chamadas de API (quem fez o quê) |
| **Amazon CloudWatch** | Métricas, logs e alarmes |
| **AWS Config** | Histórico de configuração e conformidade |
| **AWS Trusted Advisor** | Recomendações de boas práticas |
| **AWS Well-Architected Tool** | Revisa cargas de trabalho segundo o Well-Architected Framework |

### Analytics — ⭐

| Serviço | Para que serve |
|---|---|
| **AWS Data Exchange** | Encontrar e assinar dados de terceiros |
| **Amazon EMR** | Big data com Spark/Hadoop |
| **AWS Glue** | ETL serverless e catálogo de dados |
| **AWS Glue DataBrew** | Preparação visual de dados, sem código |
| **AWS Lake Formation** | Criar e governar data lakes |
| **Amazon OpenSearch Service** | Busca e análise; **banco vetorial** para RAG |
| **Amazon QuickSight** | Dashboards de BI |
| **Amazon Redshift** | Data warehouse |

### Banco de dados — ⭐ (atenção aos que fazem **busca vetorial**)

| Serviço | Para que serve |
|---|---|
| **Amazon DocumentDB** (compatível com MongoDB) | Documentos JSON; suporta vetores |
| **Amazon DynamoDB** | NoSQL chave-valor serverless |
| **Amazon ElastiCache** | Cache em memória (Redis/Memcached) |
| **Amazon MemoryDB** | Banco em memória durável, compatível com Redis; suporta vetores |
| **Amazon Neptune** | Banco de grafos; suporta vetores |
| **Amazon RDS** | Bancos relacionais gerenciados (PostgreSQL + pgvector) |

### Computação, Containers, Rede, Armazenamento e Custos — ⭐

| Serviço | Para que serve |
|---|---|
| **Amazon EC2** | Servidores virtuais (inclui instâncias com GPU, Inferentia e Trainium) |
| **Amazon ECS / EKS** | Orquestração de containers (Docker / Kubernetes) |
| **Amazon VPC** | Rede privada isolada |
| **Amazon CloudFront** | CDN, entrega de conteúdo com baixa latência |
| **Amazon S3** | Armazenamento de objetos (data lakes e datasets de ML) |
| **Amazon S3 Glacier** | Arquivamento de baixo custo |
| **AWS Budgets** | Orçamentos e alertas de custo |
| **AWS Cost Explorer** | Análise de gastos |

## ❌ Fora do escopo (pode ignorar)

| Categoria | Serviços |
|---|---|
| Analytics | AWS Clean Rooms, Amazon CloudSearch, Amazon FinSpace, Amazon MSK |
| Integração de aplicações | Amazon AppFlow, Amazon MQ, Amazon SWF |
| Aplicações de negócio | Amazon Chime, Amazon Honeycode, Amazon Pinpoint, Amazon SES, AWS Supply Chain, AWS Wickr, Amazon WorkDocs, Amazon WorkMail |
| Gestão financeira | AWS Application Cost Profiler, AWS Billing Conductor, AWS Marketplace |
| Computação | AWS App Runner, AWS Elastic Beanstalk, EC2 Image Builder, Amazon Lightsail |
| Containers | Red Hat OpenShift Service on AWS (ROSA) |
| Suporte ao cliente | AWS IQ, AWS Managed Services, AWS re:Post Private, AWS Support |
| Banco de dados | Amazon Keyspaces, Amazon QLDB, Amazon Timestream |
| Ferramentas de dev | AWS AppConfig, AWS Application Composer, AWS CloudShell, Amazon CodeCatalyst, AWS CodeStar, AWS Fault Injection Service, AWS X-Ray |
| Computação do usuário final | Amazon AppStream 2.0, Amazon WorkSpaces (incl. Thin Client e Web) |
| Web e mobile | AWS Amplify, AWS AppSync, AWS Device Farm, Amazon Location Service |
| IoT | AWS IoT Analytics, IoT Core, IoT Device Defender, IoT Device Management, IoT Events, IoT FleetWise, FreeRTOS, IoT Greengrass, IoT 1-Click, IoT RoboRunner, IoT SiteWise, IoT TwinMaker |
| Machine Learning | AWS DeepComposer, AWS HealthImaging, AWS HealthOmics, Amazon Monitron, AWS Panorama |
| Gerenciamento e governança | AWS Control Tower, Health Dashboard, Launch Wizard, License Manager, Managed Grafana, Managed Service for Prometheus, OpsWorks, Organizations, Proton, Resilience Hub, Resource Explorer, Resource Groups, Systems Manager Incident Manager, Service Catalog, Service Quotas, Telco Network Builder, User Notifications |
| Mídia | Elastic Transcoder, Elemental MediaConnect / MediaConvert / MediaLive / MediaPackage / MediaStore / MediaTailor, Amazon IVS, Nimble Studio |
| Migração e transferência | Application Discovery Service, Application Migration Service, DMS, DataSync, Mainframe Modernization, Migration Hub, Snow Family, Transfer Family |
| Rede | App Mesh, Cloud Map, Direct Connect, Global Accelerator, Private 5G, Route 53, Route 53 ARC, VPC IPAM |
| Segurança | ACM, CloudHSM, Cognito, Detective, Directory Service, Firewall Manager, GuardDuty, IAM Identity Center, Payment Cryptography, Private CA, RAM, Security Hub, Security Lake, Shield, Signer, Verified Permissions, WAF |
| Armazenamento | AWS Backup, AWS Elastic Disaster Recovery |

> [!warning] Pegadinha
> Se uma alternativa citar um serviço **fora do escopo** (ex.: GuardDuty, WAF, Cognito), ela provavelmente **não** é a resposta esperada.

---
Início: [[00 - Início - Guia do Exame]] · Anterior: [[06 - Domínio 5 - Segurança, Compliance e Governança]] · Próximo: [[08 - Roadmap de Estudo]]
