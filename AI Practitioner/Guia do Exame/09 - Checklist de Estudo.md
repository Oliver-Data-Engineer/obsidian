## Como usar

Marque `[x]` só quando conseguir **explicar o item em voz alta, sem consultar**. Cada bloco segue uma tarefa da ementa oficial. No Obsidian, clique na caixa para marcar.

> [!info] Legenda
> ⭐⭐⭐ cai muito · ⭐⭐ importante · ⭐ reconhecer

## Preparação

- [ ] Li a [[01 - Visão Geral do Exame]] (65 questões, 50 pontuadas, nota mínima 700)
- [ ] Conheço os 5 tipos de questão (múltipla escolha, múltipla resposta, ordenação, associação, estudo de caso)
- [ ] Sei os pesos: D1 20% · D2 24% · D3 28% · D4 14% · D5 14%
- [ ] Revisei o conhecimento AWS básico: EC2, S3, Lambda, IAM, Regiões/AZs, responsabilidade compartilhada, preços

## Domínio 1 — Fundamentos de IA e ML (20%) → [[02 - Domínio 1 - Fundamentos de IA e ML]]

**1.1 Conceitos e terminologia**
- [ ] ⭐⭐⭐ Defino IA, ML, deep learning, redes neurais, visão computacional, NLP
- [ ] ⭐⭐ Defino modelo, algoritmo, treino, inferência, viés, fairness, fit, LLM
- [ ] ⭐⭐⭐ Comparo IA x ML x Deep Learning
- [ ] ⭐⭐ Diferencio inferência em lote (batch) x tempo real
- [ ] ⭐⭐ Diferencio dados rotulados/não rotulados, tabulares, séries temporais, imagem, texto, estruturados/não estruturados
- [ ] ⭐⭐⭐ Explico aprendizado supervisionado, não supervisionado e por reforço

**1.2 Casos de uso**
- [ ] ⭐⭐ Sei onde IA agrega valor (decisão, escala, automação)
- [ ] ⭐⭐⭐ Sei quando **não** usar IA (custo-benefício, necessidade de resultado exato)
- [ ] ⭐⭐⭐ Escolho entre regressão, classificação e clusterização
- [ ] ⭐⭐ Reconheço aplicações: visão, NLP, fala, recomendação, fraude, previsão
- [ ] ⭐⭐⭐ Sei o que fazem SageMaker, Transcribe, Translate, Comprehend, Lex, Polly
- [ ] ⭐⭐ Sei o que fazem Rekognition, Textract, Kendra, Personalize, Fraud Detector

**1.3 Ciclo de vida de ML**
- [ ] ⭐⭐⭐ Listo as etapas: coleta, EDA, pré-processamento, features, treino, tuning, avaliação, deploy, monitoramento
- [ ] ⭐⭐ Diferencio modelo pré-treinado open source x modelo treinado sob medida
- [ ] ⭐⭐ Diferencio API gerenciada x API auto-hospedada
- [ ] ⭐⭐⭐ Associo Data Wrangler, Feature Store e Model Monitor às etapas
- [ ] ⭐⭐ Explico MLOps: experimentação, repetibilidade, escala, dívida técnica, monitoramento, retreino
- [ ] ⭐⭐⭐ Conheço métricas técnicas (acurácia, AUC, F1) e de negócio (custo por usuário, ROI, feedback)

## Domínio 2 — Fundamentos de IA Generativa (24%) → [[03 - Domínio 2 - Fundamentos de IA Generativa]]

**2.1 Conceitos**
- [ ] ⭐⭐⭐ Explico tokens, chunking, embeddings e vetores
- [ ] ⭐⭐⭐ Explico transformers, LLMs e foundation models
- [ ] ⭐⭐ Explico modelos multimodais e de difusão
- [ ] ⭐⭐ Reconheço casos de uso: imagem, vídeo, áudio, resumo, chatbot, tradução, código, atendimento, busca, recomendação
- [ ] ⭐⭐ Descrevo o ciclo de vida de um FM: dados → modelo → pré-treino → fine-tuning → avaliação → deploy → feedback

**2.2 Capacidades e limitações**
- [ ] ⭐⭐ Cito vantagens: adaptabilidade, rapidez de resposta, simplicidade
- [ ] ⭐⭐⭐ Cito limitações: alucinação, interpretabilidade, imprecisão, não determinismo
- [ ] ⭐⭐ Sei os fatores de escolha de modelo: tipo, desempenho, capacidades, restrições, compliance
- [ ] ⭐ Conheço métricas de negócio: conversão, ARPU, CLV, eficiência, acurácia

**2.3 Infraestrutura AWS para GenAI**
- [ ] ⭐⭐⭐ Diferencio Bedrock, SageMaker JumpStart, PartyRock e Amazon Q
- [ ] ⭐⭐ Sei as vantagens dos serviços gerenciados: acessibilidade, barreira de entrada menor, custo, tempo de mercado
- [ ] ⭐⭐ Sei os benefícios da infraestrutura AWS: segurança, compliance, responsabilidade, safety
- [ ] ⭐⭐⭐ Entendo os trade-offs de custo: preço por token, provisioned throughput, modelos customizados, disponibilidade, região

## Domínio 3 — Aplicações de Foundation Models (28%) → [[04 - Domínio 3 - Aplicações de Foundation Models]]

**3.1 Design de aplicações**
- [ ] ⭐⭐⭐ Sei os critérios de escolha: custo, modalidade, latência, idiomas, tamanho, complexidade, customização, tamanho de entrada/saída
- [ ] ⭐⭐⭐ Sei o efeito da temperatura e do tamanho de entrada/saída → [[Parâmetros de Inferência]]
- [ ] ⭐⭐⭐ Explico RAG e Bedrock Knowledge Bases
- [ ] ⭐⭐⭐ Cito os bancos vetoriais: OpenSearch, Aurora, Neptune, DocumentDB, RDS for PostgreSQL
- [ ] ⭐⭐⭐ Ordeno por custo: in-context learning → RAG → fine-tuning → pré-treino
- [ ] ⭐⭐ Explico o papel dos Agents for Amazon Bedrock

**3.2 Prompt engineering** → [[Índice - Prompt]]
- [ ] ⭐⭐ Explico contexto, instrução, prompt negativo e espaço latente → [[Anatomia de um Prompt]]
- [ ] ⭐⭐⭐ Explico chain-of-thought, zero-shot, single-shot, few-shot e prompt templates → [[Tipos de Prompt]]
- [ ] ⭐⭐ Conheço as boas práticas: especificidade, concisão, experimentação, guardrails → [[Boa Praticas]]
- [ ] ⭐⭐⭐ Explico os riscos: exposição, poisoning, hijacking, jailbreaking → [[Riscos e Segurança em Prompts]]

**3.3 Treino e fine-tuning**
- [ ] ⭐⭐⭐ Diferencio pré-treino, fine-tuning e pré-treino contínuo
- [ ] ⭐⭐ Explico instruction tuning, adaptação de domínio e transfer learning
- [ ] ⭐⭐ Sei preparar dados: curadoria, governança, tamanho, rotulagem, representatividade
- [ ] ⭐⭐ Explico RLHF

**3.4 Avaliação**
- [ ] ⭐⭐ Diferencio avaliação humana x benchmarks
- [ ] ⭐⭐⭐ Sei quando usar ROUGE (resumo), BLEU (tradução), METEOR (sinônimos), BERTScore (semântica) e WER (transcrição) → [[Métricas de Avaliação - Resumo, Tradução e Transcrição]]
- [ ] ⭐ Sei avaliar o valor de negócio: produtividade, engajamento, engenharia de tarefas
- [ ] ⭐⭐ Conheço o Bedrock Model Evaluation

## Domínio 4 — IA Responsável (14%) → [[05 - Domínio 4 - Diretrizes para IA Responsável]]

**4.1 Sistemas responsáveis**
- [ ] ⭐⭐⭐ Cito as dimensões: viés, justiça, inclusão, robustez, segurança, veracidade
- [ ] ⭐⭐⭐ Sei usar Guardrails for Amazon Bedrock
- [ ] ⭐ Considero sustentabilidade e impacto ambiental na escolha do modelo
- [ ] ⭐⭐ Cito os riscos legais: PI, viés, perda de confiança, risco ao usuário, alucinação
- [ ] ⭐⭐ Sei as características de bons datasets: inclusivos, diversos, curados, balanceados
- [ ] ⭐⭐ Relaciono viés/variância com underfitting/overfitting e impacto em grupos
- [ ] ⭐⭐⭐ Sei para que servem SageMaker Clarify, Model Monitor e Amazon A2I

**4.2 Transparência e explicabilidade**
- [ ] ⭐⭐ Diferencio modelo transparente/explicável x caixa-preta
- [ ] ⭐⭐⭐ Conheço SageMaker Model Cards, modelos open source e licenças
- [ ] ⭐⭐ Entendo o trade-off interpretabilidade x desempenho
- [ ] ⭐ Conheço os princípios de design centrado no humano

## Domínio 5 — Segurança, Compliance e Governança (14%) → [[06 - Domínio 5 - Segurança, Compliance e Governança]]

**5.1 Segurança**
- [ ] ⭐⭐⭐ Sei usar IAM (roles, políticas, permissões) e criptografia (KMS)
- [ ] ⭐⭐ Sei o que fazem Macie e PrivateLink
- [ ] ⭐⭐⭐ Explico a responsabilidade compartilhada aplicada à IA
- [ ] ⭐⭐ Explico linhagem de dados, catalogação e citação de fontes
- [ ] ⭐⭐ Conheço as práticas de engenharia de dados segura: qualidade, privacidade, acesso, integridade
- [ ] ⭐⭐ Conheço os riscos: prompt injection, vulnerabilidades, criptografia em repouso e em trânsito

**5.2 Governança e compliance**
- [ ] ⭐⭐ Conheço as normas ISO, SOC e leis de responsabilidade algorítmica
- [ ] ⭐⭐⭐ Diferencio Config, Inspector, Audit Manager, Artifact, CloudTrail e Trusted Advisor
- [ ] ⭐⭐ Conheço a governança de dados: ciclo de vida, logs, residência, monitoramento, retenção
- [ ] ⭐⭐ Explico a Generative AI Security Scoping Matrix (5 escopos)
- [ ] ⭐ Conheço os processos: políticas, cadência de revisão, transparência, treinamento de equipe

## Serviços e revisão final

- [ ] Sei descrever em uma frase cada serviço de ML de [[07 - Serviços AWS do Exame]]
- [ ] Reconheço os serviços fora do escopo
- [ ] Revisei o [[10 - Glossário do Exame]]
- [ ] Fiz o simulado nº 1 e revisei os erros
- [ ] Fiz o simulado nº 2 e revisei os erros
- [ ] Fiz o Official Practice Question Set (Skill Builder) com ≥ 80%
- [ ] Agendei a prova 📅

---
Início: [[00 - Início - Guia do Exame]] · Roadmap: [[08 - Roadmap de Estudo]]
