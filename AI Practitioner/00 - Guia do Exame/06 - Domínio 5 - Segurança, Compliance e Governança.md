## Resumo

**Peso: 14%** · Como proteger sistemas de IA na AWS, documentar a origem dos dados, normas de compliance e os serviços de governança e auditoria.

> [!info] Ideia central
> **Segurança** (quem acessa, criptografia, rede privada) + **Governança** (rastrear, auditar, reter, cumprir normas).

## Tarefa 5.1 — Métodos para proteger sistemas de IA

**O que a prova espera:**
- Serviços e recursos de segurança: **IAM** (roles, políticas, permissões), **criptografia**, **Amazon Macie**, **AWS PrivateLink**, **modelo de responsabilidade compartilhada**.
- **Citação de fontes e origem dos dados**: linhagem de dados (*data lineage*), catalogação, SageMaker Model Cards.
- Boas práticas de engenharia de dados segura: qualidade dos dados, tecnologias que aumentam a privacidade, controle de acesso, integridade.
- Segurança e privacidade em IA: segurança de aplicação, detecção de ameaças, gestão de vulnerabilidades, proteção de infraestrutura, **prompt injection**, **criptografia em repouso e em trânsito**.

| Serviço | Papel |
|---|---|
| **IAM** | Quem pode fazer o quê (menor privilégio) |
| **AWS KMS** | Chaves de criptografia (dados em repouso) |
| **Amazon Macie** | Descobre **dados sensíveis/PII** no S3 |
| **AWS PrivateLink / VPC** | Acesso a serviços (ex.: Bedrock) **sem passar pela internet** |
| **AWS Secrets Manager** | Guarda senhas e chaves de API |
| **Amazon Inspector** | Varredura de **vulnerabilidades** |
| **Guardrails for Bedrock** | Protege contra prompt injection, conteúdo nocivo, PII |

> [!tip] Responsabilidade compartilhada em GenAI
> **AWS** protege a infraestrutura e os serviços gerenciados. **Você** cuida dos seus dados, das permissões IAM, da criptografia que configura e do que coloca nos prompts. No Bedrock, **seus dados não são usados para treinar os modelos base**.

## Tarefa 5.2 — Governança e regulações de compliance

**O que a prova espera:**
- Normas de compliance: **ISO**, **SOC**, leis de responsabilidade algorítmica.
- Serviços de governança e compliance: **AWS Config, Amazon Inspector, AWS Audit Manager, AWS Artifact, AWS CloudTrail, AWS Trusted Advisor**.
- Estratégias de governança de dados: ciclo de vida, logs, **residência**, monitoramento, observação, **retenção**.
- Processos de governança: políticas, frequência e estratégias de revisão, frameworks como a **Generative AI Security Scoping Matrix**, padrões de transparência, treinamento de equipes.

| Serviço | Papel | Dica |
|---|---|---|
| **AWS CloudTrail** | Registra **quem fez o quê** (chamadas de API) | Auditoria / "câmera de segurança" |
| **Amazon CloudWatch** | Métricas, logs e alarmes | Monitoramento |
| **AWS Config** | Histórico de **configuração** e conformidade com regras | "Está configurado certo?" |
| **AWS Audit Manager** | Coleta evidências para **auditorias** | Automatiza auditoria |
| **AWS Artifact** | Baixar **relatórios de compliance da AWS** (ISO, SOC, PCI) | "Documentos da AWS" |
| **AWS Trusted Advisor** | Recomendações de custo, segurança, desempenho | Conselheiro |
| **Amazon Inspector** | Vulnerabilidades em EC2, containers, Lambda | Scanner |

**Generative AI Security Scoping Matrix** — classifica o uso de GenAI em **5 escopos**, do menor ao maior controle/responsabilidade do cliente:

| Escopo | Situação | Exemplo |
|---|---|---|
| 1 | App de consumidor | Usar um chatbot público |
| 2 | App corporativo (SaaS) | Ferramenta empresarial com GenAI embutida |
| 3 | Modelo pré-treinado | Construir app sobre um FM via API (Bedrock) |
| 4 | Modelo com fine-tuning | Ajustar um FM com seus dados |
| 5 | Modelo treinado do zero | Treinar seu próprio modelo |

## Autoavaliação

- [ ] Sei para que servem IAM, KMS, Macie, PrivateLink e Secrets Manager.
- [ ] Sei explicar a responsabilidade compartilhada em IA.
- [ ] Sei diferenciar CloudTrail, CloudWatch, Config, Audit Manager, Artifact e Trusted Advisor.
- [ ] Sei os 5 escopos da Security Scoping Matrix.
- [ ] Sei o que é linhagem de dados, residência e retenção.

---
Início: [[00 - Início - Guia do Exame]] · Anterior: [[05 - Domínio 4 - Diretrizes para IA Responsável]] · Próximo: [[07 - Serviços AWS do Exame]] · ✅ [[09 - Checklist de Estudo]]
