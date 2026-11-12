## Resumo

Serviços da categoria **Security, Identity, and Compliance** que estão no escopo da AIF-C01. Caem principalmente no **Domínio 5** ([[06 - Domínio 5 - Segurança, Compliance e Governança]]): **quem acessa** (IAM), **dados criptografados** (KMS), **dados sensíveis** (Macie), **segredos** (Secrets Manager), **vulnerabilidades** (Inspector) e **relatórios de compliance** (Artifact).

> [!info] Ideia central
> Na prova, cada serviço responde **uma pergunta só**. Descubra a pergunta do cenário:
> **Quem pode?** IAM · **Está criptografado?** KMS · **Onde tem PII?** Macie · **Onde guardo a senha?** Secrets Manager · **Tem vulnerabilidade?** Inspector · **Cadê o certificado da AWS?** Artifact

| Serviço | Pergunta que responde | Prioridade |
|---|---|---|
| **AWS IAM** | Quem pode fazer o quê em qual recurso? | ⭐⭐⭐ |
| **AWS KMS** | Com que chave os dados são criptografados? | ⭐⭐⭐ |
| **Amazon Macie** | Onde existem dados sensíveis (PII) no S3? | ⭐⭐⭐ |
| **AWS Secrets Manager** | Onde guardar e rotacionar senhas e chaves de API? | ⭐⭐ |
| **Amazon Inspector** | Minhas instâncias, containers e Lambdas têm vulnerabilidades? | ⭐⭐ |
| **AWS Artifact** | Onde baixo os relatórios de compliance da AWS (SOC, ISO)? | ⭐⭐ |

---

## AWS Identity and Access Management (IAM)

Controla **autenticação e autorização** em toda a AWS.

| Conceito | O que é |
|---|---|
| **Usuário / grupo** | Pessoa (ou app) e conjunto de usuários |
| **Role (função)** | Identidade **temporária** assumida por serviço, app ou pessoa. **Service role** = role que um serviço (Bedrock, SageMaker) usa para acessar outros recursos |
| **Policy (política)** | Documento JSON que **permite ou nega** ações em recursos |
| **Menor privilégio** | Dar **só** as permissões necessárias |

**Com IA na prova:**
- Restringir **quais modelos** do Bedrock cada equipe pode invocar (política com `bedrock:InvokeModel` em modelos específicos).
- **Uma service role por equipe/projeto**, cada uma com acesso só ao **seu** bucket S3 (questão #37 do simulado).
- **SageMaker Role Manager** cria roles por persona (cientista de dados, MLOps).
- Na **responsabilidade compartilhada**, configurar o IAM é sempre **responsabilidade do cliente**.

> [!warning] Pegadinhas
> - "Uma role com acesso total e confiar que cada equipe só use o seu" → **errado** (viola menor privilégio).
> - **IAM Identity Center**, **Cognito** e **Verified Permissions** estão **fora do escopo**: se aparecerem, provavelmente não são a resposta.

---

## AWS Key Management Service (KMS)

Cria e gerencia **chaves de criptografia** usadas pelos serviços AWS.

| Conceito | O que é |
|---|---|
| **AWS managed key** | Chave criada e gerida pela AWS, por serviço |
| **Customer managed key (CMK)** | Chave **sua**: você controla rotação, política e pode **desabilitar/revogar** |
| **Criptografia em repouso** | Dados armazenados (S3, volumes, modelos customizados) |
| **Criptografia em trânsito** | **TLS** (não é o KMS) |

**Com IA na prova:**
- Criptografar **datasets de treino**, **modelos customizados** do Bedrock, **Knowledge Bases**, volumes de notebooks e jobs do SageMaker.
- "A empresa precisa **controlar e revogar** a chave que protege os dados" → **customer managed key no KMS**.

> [!tip] Não confunda
> **KMS** = chaves de **criptografia**. **Secrets Manager** = **senhas e tokens** que o código usa. **CloudHSM** (fora do escopo) = hardware dedicado.

---

## Amazon Macie

Usa **ML** para **descobrir e classificar dados sensíveis** (PII, dados financeiros, credenciais) **em buckets S3**, e alerta sobre buckets públicos ou sem criptografia.

**Com IA na prova:**
- Verificar se o **dataset de treino** ou os documentos de uma **Knowledge Base** contêm **CPF, cartão, e-mail** antes de usar.
- "Garantir que o modelo trate **dados pessoais sensíveis**" com dados no S3 → **Macie** (questão #55 do simulado).

> [!tip] PII: quem encontra onde
> | Onde está a PII | Serviço |
> |---|---|
> | Em **arquivos no S3** | **Macie** |
> | Em um **texto** enviado a uma API | **Comprehend** (PII detection) |
> | Em **texto clínico** (PHI) | **Comprehend Medical** |
> | No **prompt ou na resposta** do LLM | **Bedrock Guardrails** (sensitive information filter) |
> | Em uma **transcrição** de áudio | **Transcribe** (redação de PII) |

---

## AWS Secrets Manager

Guarda **segredos** (senhas de banco, chaves de API, tokens) com **criptografia (KMS)** e **rotação automática**.

**Com IA na prova:**
- O agente ou a função **Lambda** precisa da **chave de API** de um sistema externo → buscar no Secrets Manager, **nunca** colocar no código ou no **prompt**.
- Credenciais do banco vetorial usado pela Knowledge Base (ex.: Aurora, Pinecone) ficam no Secrets Manager.

---

## Amazon Inspector

Varredura **automática e contínua** de **vulnerabilidades** (CVEs) e exposição de rede em **instâncias EC2**, **imagens de container no ECR** e **funções Lambda**.

**Com IA na prova:**
- Containers usados para **treino ou inferência** (SageMaker, ECS/EKS) → Inspector verifica as imagens.
- Palavra-chave: "**vulnerabilidades de software**", "**CVE**", "**patches**".

> [!tip] Não confunda
> **Inspector** = vulnerabilidade **no software**. **Macie** = dado **sensível** no S3. **GuardDuty** (fora do escopo) = **ameaças** e atividade maliciosa.

---

## AWS Artifact

Portal **self-service** para **baixar os relatórios de compliance da própria AWS** (SOC 1/2/3, ISO 27001, ISO/IEC 42001 para sistemas de gestão de IA, PCI) e **aceitar acordos** (ex.: BAA para HIPAA).

**Com IA na prova:**
- "O auditor pede **evidência de que a AWS** é certificada" → **Artifact**.
- Não audita a **sua** conta: só entrega os documentos **da AWS**.

---

## Serviço que saiu da lista: AWS Audit Manager

> [!note] Fora da lista atual
> O **AWS Audit Manager** não aparece mais na lista oficial (revisão de 29/10/2026), mas ainda cai em **simulados**. Saiba distingui-lo.

**O que faz:** avalia **continuamente** sua conta contra **frameworks** (PCI DSS, HIPAA, GDPR, frameworks de IA generativa) e **coleta evidências automaticamente** para auditoria.

| Serviço | Responde |
|---|---|
| **Audit Manager** | "Estou em conformidade com o framework X?" + **evidências** da **minha** conta |
| **Artifact** | Relatórios de compliance **da AWS** |
| **Config** | **Configuração** dos recursos ao longo do tempo |
| **CloudTrail** | **Quem** chamou **qual API** |

---

## Fora do escopo (provavelmente distratores)

ACM, CloudHSM, **Cognito**, Detective, Directory Service, Firewall Manager, **GuardDuty**, Payment Cryptography, Private CA, RAM, **Security Hub**, Security Lake, Shield, Signer, Verified Permissions, **WAF**.

## Exemplo para Associação Mental

**O prédio da empresa.** O **IAM** é o **crachá**: define em que andar cada um entra. O **KMS** é o **chaveiro** com as chaves dos cofres. O **Secrets Manager** é o **cofre de senhas** que troca o segredo sozinho. O **Macie** é o **cão farejador** que acha documentos sigilosos esquecidos nas salas (buckets). O **Inspector** é o **vistoriador** que procura rachaduras (vulnerabilidades). O **Artifact** é a **pasta de alvarás e certificados** do prédio, emitidos para a AWS.

---
Voltar: [[07 - Serviços AWS do Exame]] · Domínio: [[06 - Domínio 5 - Segurança, Compliance e Governança]] · Relacionadas: [[SageMaker - Governança e Segurança]] · [[Bedrock Guardrail]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html) · [AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) · [Amazon Macie](https://docs.aws.amazon.com/macie/latest/user/what-is-macie.html) · [AWS Artifact](https://docs.aws.amazon.com/artifact/latest/ug/what-is-aws-artifact.html)
