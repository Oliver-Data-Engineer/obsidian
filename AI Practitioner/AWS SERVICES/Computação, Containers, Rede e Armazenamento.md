## Resumo

Serviços de **infraestrutura** no escopo da AIF-C01, em 4 categorias oficiais: **Compute** (EC2, Lambda), **Containers** (ECS, EKS), **Networking and Content Delivery** (VPC, CloudFront) e **Storage** (S3, S3 Glacier). Na prova, aparecem quando a questão fala de **onde o modelo roda**, **como a rede fica privada** e **onde ficam os dados**.

> [!info] Ideia central
> - **Rodar modelos com controle total** → EC2 (GPU, **Trainium**, **Inferentia**) ou containers (ECS/EKS).
> - **Código que reage a eventos, sem servidor** → **Lambda** (ex.: ações de agentes).
> - **Tráfego privado** → **VPC** + endpoints (PrivateLink).
> - **Dados de treino, documentos do RAG, logs** → **S3**; **guardar barato por anos** → **S3 Glacier**.

---

## Compute

### Amazon EC2
**Servidores virtuais**. Para IA, o que importa são as **famílias de instância aceleradas**:

| Família | Chip | Uso |
|---|---|---|
| **P** (ex.: P5) | GPU NVIDIA | **Treino** de modelos grandes |
| **G** (ex.: G6) | GPU NVIDIA | **Inferência** e gráficos, mais barata |
| **Trn** (Trn1, Trn2) | **AWS Trainium** | **Treino** com melhor custo-benefício |
| **Inf** (Inf2) | **AWS Inferentia** | **Inferência** de alto desempenho e **baixo custo/energia** |

- **Com IA:** auto-hospedar um modelo com controle total (você gerencia SO, patches e escala); SageMaker e Bedrock usam essas instâncias por baixo.
- Palavra-chave: "**Trainium** = treinar", "**Inferentia** = inferir"; ambos ajudam em **custo e sustentabilidade** → [[IA Responsável - Conceitos e Riscos]].

### AWS Lambda
Executa **código sem servidor** em resposta a **eventos**, cobrando por milissegundo.
- **Com IA:**
  - Lógica das **ações dos agentes** do Bedrock (*action groups*: OpenAPI + **Lambda**) → [[Bedrock Agents]].
  - **Fulfillment** de intents do **Lex** → [[Amazon Lex]].
  - "Quando um arquivo chegar no S3, chamar o Bedrock/Comprehend" → **Lambda** acionada pelo evento.
  - Pré e pós-processamento de prompts.
- O guia cita **Lambda** entre os serviços **essenciais** que o candidato deve conhecer.

---

## Containers

### Amazon ECS e Amazon EKS
Orquestração de **containers**: **ECS** = orquestrador **da AWS** (mais simples); **EKS** = **Kubernetes** gerenciado.
- **Com IA:** rodar **modelos auto-hospedados** ou aplicações de GenAI em containers; o **SageMaker HyperPod** pode usar EKS para orquestrar treinos grandes.
- Palavra-chave: "**Kubernetes**" → EKS; "**containers Docker** sem Kubernetes" → ECS.
- Trade-off da prova: **auto-hospedar** (EC2/ECS/EKS) dá **mais controle**, mas **mais esforço operacional** que uma **API gerenciada** (Bedrock, SageMaker endpoint).

---

## Networking and Content Delivery

### Amazon VPC
**Rede privada isolada** na AWS (sub-redes, tabelas de rota, security groups).
- **Com IA:**
  - Notebooks, treinos e endpoints do SageMaker **dentro da VPC**.
  - **VPC endpoints (AWS PrivateLink)** para chamar **Bedrock** e **SageMaker** **sem passar pela internet pública** (questão #28 do formulário de SageMaker).
- Palavra-chave: "**não pode trafegar pela internet**", "**rede privada**", "**isolamento**".

### Amazon CloudFront
**CDN**: entrega conteúdo (sites, APIs, mídia) com **baixa latência** a partir de pontos de presença no mundo todo.
- **Com IA:** distribuir o **front-end** de um chatbot ou conteúdo gerado (imagens) para usuários globais com baixa latência.
- Raro em questões de IA; reconheça pelo nome.

---

## Storage

### Amazon S3
**Armazenamento de objetos** praticamente ilimitado, durável (11 noves).
- **Com IA:** é o centro de tudo:
  - **Datasets de treino** e **dados de fine-tuning** do Bedrock/SageMaker.
  - **Fonte de documentos** das **Knowledge Bases** (RAG).
  - **Artefatos de modelo**, saídas de **Batch Transform** e de inferência em lote.
  - Destino dos **logs de invocação** do Bedrock.
  - **Data lake** (com Glue e Lake Formation).
- Segurança: criptografia **SSE-KMS**, políticas de bucket, **Block Public Access**, versionamento; **Macie** acha PII nos buckets.

### Amazon S3 Glacier
Classes de armazenamento de **arquivamento** com custo muito baixo (Instant Retrieval, Flexible Retrieval, Deep Archive), com recuperação de **milissegundos a horas**.
- **Com IA:** **retenção de dados** por exigência legal (Domínio 5): guardar por anos **logs de invocação**, datasets antigos e versões de modelo que não são mais usadas.
- Palavra-chave: "**arquivar**", "**reter por 7 anos**", "**menor custo**", "**acesso raro**".

---

## Fora do escopo
- **Compute:** Elastic Beanstalk, EC2 Image Builder, Lightsail.
- **Containers:** Red Hat OpenShift (ROSA).
- **Rede:** Cloud Map, Direct Connect, Global Accelerator, Route 53, Route 53 ARC, VPC IPAM.
- **Storage:** AWS Backup, Elastic Disaster Recovery.

## Exemplo para Associação Mental

**A fábrica.** O **EC2** é o **galpão alugado** onde você monta as máquinas (GPU, **Trainium** para fabricar, **Inferentia** para entregar). O **Lambda** é o **funcionário freelancer** que só aparece quando toca a campainha (evento). **ECS/EKS** são as **esteiras** que organizam as caixas (containers). A **VPC** é o **muro com portão próprio**; o **PrivateLink** é o **túnel** até o fornecedor sem sair na rua. O **CloudFront** são as **filiais** perto dos clientes. O **S3** é o **depósito** e o **Glacier** é o **arquivo morto** no subsolo.

---
Voltar: [[07 - Serviços AWS do Exame]] · Relacionadas: [[ML Inference]] · [[SageMaker - Governança e Segurança]] · [[Bedrock Agents]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [AWS Trainium](https://aws.amazon.com/ai/machine-learning/trainium/) · [AWS Inferentia](https://aws.amazon.com/ai/machine-learning/inferentia/) · [Bedrock interface VPC endpoints](https://docs.aws.amazon.com/bedrock/latest/userguide/vpc-interface-endpoints.html)
