## Resumo

Serviços AWS **dentro do escopo** da AIF-C01, exatamente nas **11 categorias da lista oficial** (revisão de **29/10/2026**), cada um com o link para a nota onde está explicado. Depois vêm os serviços que **saíram da lista** (mas ainda caem em simulados) e os que estão **fora do escopo**. A AWS avisa que as listas **não são exaustivas** e mudam; as mudanças valem na prova cerca de **1 mês** depois de publicadas.

> [!info] Ideia central
> Foque em **Machine Learning** (⭐⭐⭐) e em **Segurança + Governança** (⭐⭐). Os demais basta **reconhecer pelo nome** e saber **como se ligam à IA** (dados, vetores, rede privada, custo).
> O guia cita como **serviços essenciais** que o candidato deve conhecer: **EC2, S3, Lambda, Bedrock e SageMaker AI**, além de **IAM**, **responsabilidade compartilhada** e **modelos de preço**.

## Cobertura das notas

| Categoria oficial | Serviços | Nota |
|---|---|---|
| Machine Learning | 14 | Uma nota por serviço em **IA SERVICES**, **Bedrock** e **SageMaker** |
| Security, Identity, and Compliance | 6 | [[01 - Segurança, Identidade e Compliance\|Segurança, Identidade e Compliance]] |
| Management and Governance | 5 | [[02 - Gerenciamento e Governança\|Gerenciamento e Governança]] |
| Analytics | 8 | [[03 - Analytics\|Analytics]] |
| Database | 6 | [[04 - Banco de Dados\|Banco de Dados]] |
| Compute · Containers · Networking · Storage | 8 | [[05 - Computação, Containers, Rede e Armazenamento\|Computação, Containers, Rede e Armazenamento]] |
| Cloud Financial Management | 2 | [[06 - Gestão Financeira\|Gestão Financeira]] |
| Developer Tools | 2 | [[07 - Ferramentas de Desenvolvimento (Kiro e Strands)\|Ferramentas de Desenvolvimento (Kiro e Strands)]] |
| **Total** | **51** | ✅ todos com anotação |

---

## ✅ Dentro do escopo

### Machine Learning — ⭐⭐⭐ (prioridade máxima)

| Serviço | Para que serve | Nota |
|---|---|---|
| **Amazon Bedrock** | FMs de vários fornecedores por API serverless; Knowledge Bases (RAG), Guardrails, Evaluations, customização | [[01 - Amazon Bedrock\|Amazon Bedrock]] · [[00 - Índice - Bedrock\|Índice - Bedrock]] |
| **Amazon Bedrock AgentCore** 🆕 | Plataforma gerenciada para **implantar e operar agentes** (runtime, memória, gateway de ferramentas MCP, identidade) com qualquer framework | [[06 - Bedrock Agents#Novidade de 2026: Bedrock AgentCore]] |
| **Amazon Nova** 🆕 | Família de **FMs da Amazon** no Bedrock: texto/multimodal, imagem (Canvas), vídeo (Reel), voz (Sonic), embeddings, agente de navegador (Act) | [[14 - Amazon Nova\|Amazon Nova]] |
| **Amazon SageMaker AI** | Plataforma completa para **construir, treinar, implantar e monitorar** modelos próprios | [[01 - Amazon SageMaker\|Amazon SageMaker]] · [[00 - Índice - SageMaker\|Índice - SageMaker]] |
| **Amazon SageMaker JumpStart** 🆕 | **Hub de modelos** pré-treinados/FMs para implantar e ajustar **em instâncias suas** | [[05 - SageMaker - IA Generativa#2. SageMaker JumpStart em detalhe]] |
| **Amazon Comprehend** | NLP: sentimento, entidades, frases-chave, idioma, PII, classificação personalizada | [[01 - Amazon Comprehend\|Amazon Comprehend]] (+ [[02 - Amazon Comprehend Medical\|Amazon Comprehend Medical]]) |
| **Amazon Lex** | Chatbots de voz e texto | [[06 - Amazon Lex\|Amazon Lex]] |
| **Amazon Personalize** | Recomendações personalizadas | [[10 - Amazon Personalize\|Amazon Personalize]] |
| **Amazon Polly** | Texto → fala | [[05 - Amazon Polly\|Amazon Polly]] |
| **Amazon Rekognition** | Análise de imagem e vídeo (objetos, rostos, texto, moderação) | [[07 - Amazon Rekognition\|Amazon Rekognition]] |
| **Amazon Textract** | Extrai texto, formulários e tabelas de documentos | [[08 - Amazon Textract\|Amazon Textract]] |
| **Amazon Transcribe** | Fala → texto | [[04 - Amazon Transcribe\|Amazon Transcribe]] |
| **Amazon Translate** | Tradução automática | [[03 - Amazon Translate\|Amazon Translate]] |
| **AWS Transform** 🆕 | **Agentes de IA** para modernizar legado (.NET, mainframe, VMware) | [[15 - AWS Transform\|AWS Transform]] |

### Security, Identity, and Compliance — ⭐⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **AWS IAM** | Usuários, roles, políticas; **menor privilégio** | [[01 - Segurança, Identidade e Compliance#AWS Identity and Access Management (IAM)]] |
| **AWS KMS** | Chaves de **criptografia** (inclui chaves do cliente) | [[01 - Segurança, Identidade e Compliance#AWS Key Management Service (KMS)]] |
| **Amazon Macie** | Descobre **dados sensíveis (PII)** no **S3** | [[01 - Segurança, Identidade e Compliance#Amazon Macie]] |
| **AWS Secrets Manager** | Guarda e **rotaciona** senhas e chaves de API | [[01 - Segurança, Identidade e Compliance#AWS Secrets Manager]] |
| **Amazon Inspector** | Varredura de **vulnerabilidades** (EC2, containers, Lambda) | [[01 - Segurança, Identidade e Compliance#Amazon Inspector]] |
| **AWS Artifact** | Relatórios de compliance **da AWS** (SOC, ISO) e acordos | [[01 - Segurança, Identidade e Compliance#AWS Artifact]] |

### Management and Governance — ⭐⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **AWS CloudTrail** | **Quem** chamou **qual API** (auditoria) | [[02 - Gerenciamento e Governança#AWS CloudTrail]] |
| **Amazon CloudWatch** | Métricas, logs, alarmes, dashboards | [[02 - Gerenciamento e Governança#Amazon CloudWatch]] |
| **AWS Config** | Histórico de **configuração** e regras de conformidade | [[02 - Gerenciamento e Governança#AWS Config]] |
| **AWS Trusted Advisor** | **Recomendações** de custo, segurança, desempenho, limites | [[02 - Gerenciamento e Governança#AWS Trusted Advisor]] |
| **AWS Well-Architected Tool** | Revisa a carga contra o **Well-Architected** (lentes de GenAI, ML e IA Responsável) | [[02 - Gerenciamento e Governança#AWS Well-Architected Tool]] |

### Analytics — ⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **AWS Data Exchange** | Assinar **dados de terceiros** | [[03 - Analytics#AWS Data Exchange]] |
| **Amazon EMR** | **Big data** com Spark/Hadoop | [[03 - Analytics#Amazon EMR]] |
| **AWS Glue** | **ETL** serverless + **Data Catalog** | [[03 - Analytics#AWS Glue]] |
| **AWS Glue DataBrew** | Preparação de dados **visual, sem código** | [[03 - Analytics#AWS Glue DataBrew]] |
| **AWS Lake Formation** | **Governança e permissões** do data lake | [[03 - Analytics#AWS Lake Formation]] |
| **Amazon OpenSearch Service** | Busca e **banco vetorial** (padrão do RAG) ⭐⭐⭐ | [[03 - Analytics#Amazon OpenSearch Service]] |
| **Amazon Quick** 🆕 | Ex-**QuickSight**: **BI (Quick Sight)** + agentes e automação; sucessor do **Q Business** | [[03 - Analytics#Amazon Quick]] |
| **Amazon Redshift** | **Data warehouse** SQL | [[03 - Analytics#Amazon Redshift]] |

### Database — ⭐ (atenção a quem faz **busca vetorial**)

| Serviço | Para que serve | Nota |
|---|---|---|
| **Amazon Aurora** 🆕 | Relacional MySQL/PostgreSQL; **pgvector** para RAG | [[04 - Banco de Dados#Amazon Aurora]] |
| **Amazon DocumentDB** | Documentos JSON (MongoDB); busca vetorial | [[04 - Banco de Dados#Amazon DocumentDB (compatível com MongoDB)]] |
| **Amazon DynamoDB** | NoSQL chave-valor serverless; **histórico de chat** | [[04 - Banco de Dados#Amazon DynamoDB]] |
| **Amazon ElastiCache** | **Cache** em memória; cache semântico | [[04 - Banco de Dados#Amazon ElastiCache]] |
| **Amazon Neptune** | **Grafos**; **GraphRAG** | [[04 - Banco de Dados#Amazon Neptune]] |
| **Amazon RDS** | Relacional gerenciado; PostgreSQL + pgvector | [[04 - Banco de Dados#Amazon RDS]] |

### Compute — ⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **Amazon EC2** | Servidores virtuais; GPU, **Trainium** (treino), **Inferentia** (inferência) | [[05 - Computação, Containers, Rede e Armazenamento#Amazon EC2]] |
| **AWS Lambda** 🆕 | Código **serverless** por evento; **ações de agentes**, fulfillment do Lex | [[05 - Computação, Containers, Rede e Armazenamento#AWS Lambda]] |

### Containers — ⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **Amazon ECS** | Orquestrador de containers da AWS | [[05 - Computação, Containers, Rede e Armazenamento#Amazon ECS e Amazon EKS]] |
| **Amazon EKS** | **Kubernetes** gerenciado | [[05 - Computação, Containers, Rede e Armazenamento#Amazon ECS e Amazon EKS]] |

### Networking and Content Delivery — ⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **Amazon VPC** | **Rede privada**; endpoints **PrivateLink** para Bedrock/SageMaker | [[05 - Computação, Containers, Rede e Armazenamento#Amazon VPC]] |
| **Amazon CloudFront** | CDN de baixa latência | [[05 - Computação, Containers, Rede e Armazenamento#Amazon CloudFront]] |

### Storage — ⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **Amazon S3** | Datasets, documentos do RAG, artefatos de modelo, logs | [[05 - Computação, Containers, Rede e Armazenamento#Amazon S3]] |
| **Amazon S3 Glacier** | **Arquivamento** barato (retenção de dados) | [[05 - Computação, Containers, Rede e Armazenamento#Amazon S3 Glacier]] |

### Cloud Financial Management — ⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **AWS Budgets** | Orçamento + **alertas** | [[06 - Gestão Financeira#AWS Budgets]] |
| **AWS Cost Explorer** | **Análise** e previsão de gastos | [[06 - Gestão Financeira#AWS Cost Explorer]] |

### Developer Tools 🆕 — ⭐

| Serviço | Para que serve | Nota |
|---|---|---|
| **Kiro** | IDE/CLI **agêntica**, *spec-driven*; sucessor do Q Developer CLI | [[07 - Ferramentas de Desenvolvimento (Kiro e Strands)#Kiro]] |
| **Strands Agents** | **SDK open source** para construir agentes (MCP, multiagente) | [[07 - Ferramentas de Desenvolvimento (Kiro e Strands)#Strands Agents]] |

---

## ⚠️ Saíram da lista (mas ainda caem em simulados)

Estes serviços estavam na versão anterior do guia (ou caem muito em simulados) e **não aparecem** na lista atual. A maioria entrou em **manutenção** em 2026. Continue sabendo **o conceito**: os bancos de questões demoram a ser atualizados.

| Serviço | Situação | Sucessor / alternativa | Nota |
|---|---|---|---|
| **Amazon Q** (Business / Developer) | Q Business em manutenção; Q Developer CLI → **Kiro** | **Amazon Quick**, **Kiro** | [[16 - Amazon Q\|Amazon Q]] |
| **Amazon Augmented AI (A2I)** | Manutenção, sem novos clientes | — (conceito de **humano no loop** continua cobrado) | [[13 - Amazon Augmented AI\|Amazon Augmented AI]] |
| **Amazon Kendra** | Manutenção, sem novos clientes | **Bedrock Knowledge Bases** | [[09 - Amazon Kendra\|Amazon Kendra]] |
| **Amazon Fraud Detector** | Sem novos clientes desde 07/11/2025 | SageMaker / AutoGluon | [[12 - Amazon Fraud Detector\|Amazon Fraud Detector]] |
| **AWS Audit Manager** | Fora da lista | — | [[01 - Segurança, Identidade e Compliance#Serviço que saiu da lista: AWS Audit Manager]] |
| **Amazon MemoryDB** | Fora da lista (entrou **Aurora**) | Aurora, ElastiCache | [[04 - Banco de Dados#Amazon ElastiCache]] |
| **Amazon QuickSight** | Renomeado | **Amazon Quick** (Quick Sight) | [[03 - Analytics#Amazon Quick]] |
| **Amazon Forecast** | Sem novos clientes desde 2024; nunca esteve na lista | SageMaker Canvas | [[11 - Amazon Forecast\|Amazon Forecast]] |
| **Amazon Comprehend Medical** | Não está na lista, mas cai em simulados (#41) | — | [[02 - Amazon Comprehend Medical\|Amazon Comprehend Medical]] |

> [!tip] Como responder
> Se uma questão antiga tiver **Kendra**, **A2I** ou **Q Business** como alternativa e o cenário pedir exatamente aquilo (busca corporativa, revisão humana, assistente com dados da empresa), **escolha-os**: a questão testa o **conceito**.

---

## ❌ Fora do escopo (pode ignorar)

Lista oficial atual. Se uma alternativa citar um destes, ela **provavelmente não** é a resposta.

| Categoria | Serviços |
|---|---|
| Analytics | AWS Clean Rooms, Amazon CloudSearch, Amazon MSK |
| Integração de aplicações | Amazon AppFlow, Amazon MQ, Amazon SWF |
| Aplicações de negócio | Amazon SES, AWS Supply Chain, AWS Wickr |
| Gestão financeira | AWS Application Cost Profiler, AWS Billing Conductor |
| Computação | AWS Elastic Beanstalk, EC2 Image Builder, Amazon Lightsail |
| Containers | Red Hat OpenShift Service on AWS (ROSA) |
| Suporte ao cliente | AWS Managed Services, AWS re:Post Private, AWS Support |
| Banco de dados | Amazon Keyspaces, Amazon Timestream |
| Ferramentas de dev | AWS AppConfig, AWS Application Composer, AWS CloudShell, AWS Fault Injection Service, AWS X-Ray |
| Computação do usuário final | Amazon AppStream 2.0, Amazon WorkSpaces (incl. Thin Client e Secure Browser) |
| Web e mobile | AWS Amplify, AWS Device Farm, Amazon Location Service |
| IoT | IoT Core, IoT Device Defender, IoT Device Management, IoT FleetWise, FreeRTOS, IoT Greengrass, IoT SiteWise, IoT TwinMaker |
| Machine Learning | AWS HealthImaging, AWS HealthOmics |
| Gerenciamento e governança | Control Tower, Health Dashboard, Launch Wizard, License Manager, Managed Grafana, Managed Service for Prometheus, Resilience Hub, Resource Explorer, Resource Groups, Systems Manager Incident Manager, Service Catalog, Service Quotas, Telco Network Builder, User Notifications |
| Mídia | Elemental MediaConnect / MediaConvert / MediaLive / MediaPackage / MediaTailor, Amazon IVS |
| Migração e transferência | Application Discovery Service, Application Migration Service, DMS, DataSync, Mainframe Modernization, Migration Hub, Transfer Family |
| Rede | Cloud Map, Direct Connect, Global Accelerator, Route 53, Route 53 ARC, VPC IPAM |
| Segurança | ACM, CloudHSM, **Cognito**, Detective, Directory Service, Firewall Manager, **GuardDuty**, Payment Cryptography, Private CA, RAM, **Security Hub**, Security Lake, Shield, Signer, Verified Permissions, **WAF** |
| Armazenamento | AWS Backup, AWS Elastic Disaster Recovery |

> [!warning] Pegadinha
> Se uma alternativa citar um serviço **fora do escopo** (ex.: GuardDuty, WAF, Cognito), ela provavelmente **não** é a resposta esperada.

---
Início: [[00 - Início - Guia do Exame]] · Anterior: [[06 - Domínio 5 - Segurança, Compliance e Governança]] · Próximo: [[08 - Roadmap de Estudo]]

Fontes: [AIF-C01 – In-scope AWS services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [AIF-C01 – Out-of-scope AWS services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-out-of-scope-services.html) · [AIF-C01 – Revisions](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-revisions.html)
