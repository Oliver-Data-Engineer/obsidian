## Como usar

Teste sobre o **Amazon Bedrock** no estilo da prova AIF-C01, com os **5 tipos de questão** cobrados: múltipla escolha, múltipla resposta, ordenação, associação e estudo de caso. Responda **antes** de abrir a resposta (no Obsidian, clique na seta `▶` do callout para expandir). Errou? Volte à nota indicada.

> [!info] Pontuação
> **30 questões.** Anote seus acertos no fim.
> **≥ 24 (80%)** pronto para a prova · **18–23** revise as notas dos erros · **< 18** releia o [[00 - Índice - Bedrock|Índice - Bedrock]] inteiro.
> Refaça o teste em **1 dia, 1 semana e 1 mês** (repetição espaçada).

## Parte 1 · Flashcards (aquecimento)

> [!question]- O que é o Amazon Bedrock em uma frase?
> Serviço **gerenciado e serverless** que dá acesso a vários **Foundation Models** de vários fornecedores por **uma única API**. → [[00 - Índice - Bedrock|Índice - Bedrock]]

> [!question]- Os prompts enviados ao Bedrock são usados para treinar os modelos?
> **Não.** Os dados não treinam os modelos base e não são compartilhados com os fornecedores. → [[00 - Índice - Bedrock|Índice - Bedrock]]

> [!question]- Fine-tuning x pré-treino contínuo: que tipo de dado cada um usa?
> **Fine-tuning** → dados **rotulados** (pares prompt/resposta). **Pré-treino contínuo** → dados **não rotulados** do domínio. → [[02 - Foundation Models|Foundation Models]]

> [!question]- O que é destilação de modelos?
> Um modelo grande (**professor**) ensina um modelo **menor** (**aluno**), que fica mais **barato e rápido**, com qualidade parecida. → [[02 - Foundation Models|Foundation Models]]

> [!question]- Quando o Provisioned Throughput é obrigatório?
> Para fazer inferência com **modelos customizados** (e é recomendado para cargas altas e constantes). → [[04 - ML Inference|ML Inference]]

> [!question]- O que é um embedding?
> Um **vetor numérico** que representa o **significado** de um texto (ou imagem). Textos parecidos geram vetores próximos. → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

> [!question]- Diferença entre as APIs Retrieve e RetrieveAndGenerate?
> **Retrieve** só devolve os **trechos** encontrados. **RetrieveAndGenerate** busca **e** gera a resposta com o FM. → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

> [!question]- O que é um action group?
> O conjunto de ações que um agente pode executar: **schema OpenAPI** + **função Lambda**. → [[06 - Bedrock Agents|Bedrock Agents]]

> [!question]- Quais são as 6 políticas do Guardrails?
> **Content filters, denied topics, word filters, sensitive information (PII), contextual grounding check, automated reasoning checks.** → [[07 - Bedrock Guardrails|Bedrock Guardrails]]

> [!question]- O que aconteceu com o Bedrock Agents em 2026?
> Virou **Agents Classic** (modo de manutenção, sem novas contas a partir de 30/07/2026). O sucessor é o **Bedrock AgentCore**. → [[06 - Bedrock Agents|Bedrock Agents]]

## Parte 2 · Múltipla escolha

**1.** Uma startup quer criar um chatbot usando **vários foundation models** e testar qual é melhor, **sem gerenciar infraestrutura**. Qual serviço atende com **menor esforço operacional**?

A) Amazon EC2 com GPUs · B) Amazon SageMaker AI (treino próprio) · C) **Amazon Bedrock** · D) Amazon Comprehend

> [!success]- Resposta
> **C.** Bedrock é serverless e dá acesso a vários FMs por uma API. → [[00 - Índice - Bedrock|Índice - Bedrock]]

**2.** Uma empresa quer que o assistente responda sobre **políticas internas que mudam toda semana**, com **citação da fonte**. Qual a melhor abordagem?

A) Fine-tuning semanal · B) Pré-treino do zero · C) **Bedrock Knowledge Bases (RAG)** · D) Aumentar a temperatura

> [!success]- Resposta
> **C.** RAG usa dados atuais sem retreinar e devolve citações. → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

**3.** Um banco quer impedir que o chatbot **dê recomendações de investimento**. Qual recurso usar?

A) Word filters · B) **Guardrails: denied topics** · C) Model Evaluation · D) Provisioned Throughput

> [!success]- Resposta
> **B.** Denied topics bloqueiam **assuntos** descritos em linguagem natural. Word filters só pegam **palavras exatas**. → [[07 - Bedrock Guardrails|Bedrock Guardrails]]

**4.** Uma empresa precisa resumir **2 milhões de avaliações** de produtos. O resultado só é necessário **no dia seguinte** e o foco é **menor custo**. Qual opção?

A) On-demand · B) Provisioned Throughput · C) **Batch inference** · D) Priority tier

> [!success]- Resposta
> **C.** Batch é a opção mais barata para grandes volumes sem urgência. → [[04 - ML Inference|ML Inference]]

**5.** Uma empresa fez **fine-tuning** de um modelo no Bedrock. O que é necessário para usá-lo em produção?

A) Nada, funciona em on-demand como qualquer modelo · B) **Comprar Provisioned Throughput** · C) Exportar para o EC2 · D) Criar um guardrail

> [!success]- Resposta
> **B.** Modelos customizados exigem Provisioned Throughput para inferência. → [[04 - ML Inference|ML Inference]]

**6.** Um hospital tem milhares de **artigos médicos sem rótulo** e quer que o modelo aprenda o **vocabulário da área**. Qual customização?

A) Fine-tuning supervisionado · B) **Pré-treino contínuo** · C) Few-shot prompting · D) Destilação

> [!success]- Resposta
> **B.** Dados **não rotulados** + conhecimento de **domínio** = pré-treino contínuo. → [[02 - Foundation Models|Foundation Models]]

**7.** Qual componente transforma texto em **vetores** para busca por similaridade?

A) Modelo de difusão · B) **Modelo de embeddings (ex.: Titan Text Embeddings)** · C) Guardrails · D) Amazon Translate

> [!success]- Resposta
> **B.** → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

**8.** Um assistente precisa **consultar o status de um pedido** no ERP e **abrir um chamado** no sistema de suporte, decidindo os passos sozinho. Qual recurso?

A) Knowledge Bases · B) **Agents for Amazon Bedrock** · C) Prompt Management · D) Model Evaluation

> [!success]- Resposta
> **B.** Tarefas de várias etapas que **executam ações** em sistemas = agente. → [[06 - Bedrock Agents|Bedrock Agents]]

**9.** Uma aplicação RAG às vezes dá respostas que **não estão nos documentos**. Qual recurso do Guardrails detecta isso?

A) Word filters · B) Content filters · C) **Contextual grounding check** · D) Denied topics

> [!success]- Resposta
> **C.** Verifica se a resposta está apoiada na fonte (*grounding*) e é relevante. → [[07 - Bedrock Guardrails|Bedrock Guardrails]]

**10.** Um cliente pergunta se os dados enviados ao Bedrock são **compartilhados com o fornecedor do modelo**. Qual a resposta?

A) Sim, para melhorar o modelo · B) Sim, mas anonimizados · C) **Não, os dados não são compartilhados nem usados para treinar os modelos base** · D) Só em on-demand

> [!success]- Resposta
> **C.** → [[00 - Índice - Bedrock|Índice - Bedrock]]

**11.** Qual serviço garante que o tráfego entre a VPC e o Bedrock **não passe pela internet pública**?

A) Amazon CloudFront · B) **AWS PrivateLink (VPC endpoint)** · C) AWS Shield · D) Amazon Route 53

> [!success]- Resposta
> **B.** → [[00 - Índice - Bedrock|Índice - Bedrock]]

**12.** Qual métrica é mais indicada para avaliar a qualidade de **resumos** gerados?

A) BLEU · B) **ROUGE** · C) F1 · D) RMSE

> [!success]- Resposta
> **B.** ROUGE → resumo. BLEU → tradução. → [[02 - Foundation Models|Foundation Models]]

**13.** A equipe quer avaliar respostas por critérios **subjetivos** como **tom de voz e estilo da marca**. Qual tipo de avaliação?

A) Automática com métricas de toxicidade · B) **Avaliação humana** · C) Provisioned Throughput · D) Teste de carga

> [!success]- Resposta
> **B.** Critérios subjetivos pedem avaliação humana (ou LLM-as-a-judge com critérios definidos). → [[02 - Foundation Models|Foundation Models]]

**14.** Uma empresa quer um modelo **menor e mais barato** que mantenha qualidade parecida à de um modelo grande, para um caso de uso específico. Qual recurso?

A) Pré-treino contínuo · B) Cross-region inference · C) **Model distillation** · D) Word filters

> [!success]- Resposta
> **C.** → [[02 - Foundation Models|Foundation Models]]

**15.** Qual serviço registra **quem chamou** a API do Bedrock e **quando**, para auditoria?

A) Amazon CloudWatch · B) **AWS CloudTrail** · C) AWS Config · D) Amazon Inspector

> [!success]- Resposta
> **B.** CloudTrail = auditoria de chamadas de API. CloudWatch = métricas e logs de desempenho. → [[00 - Índice - Bedrock|Índice - Bedrock]]

**16.** Uma empresa quer **mais controle sobre a infraestrutura** (tipo de instância) ao implantar um modelo pré-treinado open source. O que usar?

A) Amazon Bedrock on-demand · B) **SageMaker JumpStart** · C) PartyRock · D) Amazon Q Business

> [!success]- Resposta
> **B.** Bedrock = sem gerenciar nada. JumpStart = mais controle. → [[00 - Índice - Bedrock|Índice - Bedrock]]

**17.** Qual destas opções **NÃO** é um banco vetorial citado pela ementa para soluções de GenAI na AWS?

A) Amazon OpenSearch Service · B) Amazon Aurora PostgreSQL · C) Amazon Neptune · D) **Amazon Athena**

> [!success]- Resposta
> **D.** Athena consulta dados no S3 com SQL; não é banco vetorial. → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

**18.** Um chatbot precisa **mascarar CPFs e e-mails** antes de exibir a resposta. Qual política?

A) Denied topics · B) **Sensitive information filters** · C) Automated Reasoning · D) Content filters

> [!success]- Resposta
> **B.** → [[07 - Bedrock Guardrails|Bedrock Guardrails]]

**19.** Uma aplicação tem **tráfego alto e constante 24h** com um modelo base do Bedrock e precisa de **capacidade garantida**. Qual opção?

A) Batch · B) Flex tier · C) **Provisioned Throughput** · D) PartyRock

> [!success]- Resposta
> **C.** → [[04 - ML Inference|ML Inference]]

**20.** Qual afirmação sobre RAG é **correta**?

A) Altera os pesos do modelo · B) Exige dados rotulados · C) **Adiciona contexto recuperado ao prompt no momento da pergunta** · D) Só funciona com imagens

> [!success]- Resposta
> **C.** → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

## Parte 3 · Múltipla resposta (acerte todas)

**21.** Quais **duas** opções reduzem o **custo de inferência** no Bedrock? *(Escolha 2)*

A) **Usar batch inference para cargas sem urgência** · B) Aumentar o número máximo de tokens de saída · C) **Usar um modelo menor ou destilado** · D) Colocar mais exemplos no prompt · E) Usar o tier Priority

> [!success]- Resposta
> **A e C.** Mais tokens e o tier Priority **aumentam** o custo. → [[04 - ML Inference|ML Inference]]

**22.** Quais **três** são políticas do Amazon Bedrock Guardrails? *(Escolha 3)*

A) **Content filters** · B) Hyperparameter tuning · C) **Denied topics** · D) **Sensitive information filters** · E) Batch transform

> [!success]- Resposta
> **A, C e D.** → [[07 - Bedrock Guardrails|Bedrock Guardrails]]

**23.** Quais **dois** componentes formam um **action group** de um agente? *(Escolha 2)*

A) **Schema OpenAPI** · B) Banco vetorial · C) **Função AWS Lambda** · D) Modelo de embeddings · E) Guardrail

> [!success]- Resposta
> **A e C.** → [[06 - Bedrock Agents|Bedrock Agents]]

## Parte 4 · Ordenação

**24.** Coloque as etapas de **ingestão e consulta do RAG** na ordem certa:

- Gerar embeddings dos chunks
- Dividir os documentos em chunks
- Buscar os chunks mais similares à pergunta
- Guardar os vetores no banco vetorial
- Enviar prompt + contexto ao FM

> [!success]- Resposta
> 1. Dividir em **chunks** → 2. Gerar **embeddings** → 3. Guardar no **banco vetorial** → 4. **Buscar** os similares → 5. Enviar **prompt + contexto** ao FM. → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

**25.** Ordene as formas de adaptar um FM da **mais barata/rápida** para a **mais cara/demorada**:

- Fine-tuning
- Pré-treino do zero
- Prompt engineering
- RAG

> [!success]- Resposta
> **Prompt engineering → RAG → Fine-tuning → Pré-treino do zero.** → [[02 - Foundation Models|Foundation Models]]

## Parte 5 · Associação

**26.** Associe cada necessidade ao recurso do Bedrock:

| Necessidade | Recurso |
|---|---|
| 1. Testar prompts sem escrever código | A. Knowledge Bases |
| 2. Responder com base em PDFs da empresa | B. Guardrails |
| 3. Bloquear linguagem ofensiva | C. Playground |
| 4. Comparar dois modelos com um dataset | D. Agents |
| 5. Executar uma tarefa que chama APIs | E. Model Evaluation |

> [!success]- Resposta
> **1-C · 2-A · 3-B · 4-E · 5-D.** → [[00 - Índice - Bedrock|Índice - Bedrock]]

**27.** Associe a métrica à tarefa:

| Métrica | Tarefa |
|---|---|
| 1. ROUGE | A. Tradução |
| 2. BLEU | B. Similaridade de significado |
| 3. BERTScore | C. Resumo |

> [!success]- Resposta
> **1-C · 2-A · 3-B.** → [[02 - Foundation Models|Foundation Models]]

## Parte 6 · Estudo de caso

> [!example] Cenário
> Uma seguradora quer lançar um **assistente virtual** para clientes. Requisitos:
> - Responder dúvidas sobre **apólices** usando **contratos em PDF** guardados no S3, que são atualizados todo mês.
> - **Abrir sinistros** no sistema interno quando o cliente pedir.
> - **Nunca exibir** números de documentos dos clientes e **não falar de concorrentes**.
> - Usar **o mínimo de infraestrutura** possível.

**28.** Qual combinação atende ao requisito de **responder sobre apólices**?

A) Fine-tuning mensal com os PDFs · B) **Bedrock Knowledge Bases com o S3 como fonte de dados** · C) Amazon Textract sozinho · D) Prompt com todos os PDFs colados

> [!success]- Resposta
> **B.** Os documentos mudam todo mês → RAG. Basta sincronizar a fonte de dados. → [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

**29.** Para **abrir sinistros** no sistema interno, o que usar?

A) Guardrails · B) **Agent com action group (OpenAPI + Lambda) que chama a API de sinistros** · C) Batch inference · D) Model Evaluation

> [!success]- Resposta
> **B.** → [[06 - Bedrock Agents|Bedrock Agents]]

**30.** Para **não exibir documentos dos clientes** e **não citar concorrentes**, quais políticas do Guardrails usar?

A) Contextual grounding + Automated Reasoning · B) **Sensitive information filters + word filters (ou denied topics)** · C) Content filters de violência · D) Nenhuma, basta temperatura baixa

> [!success]- Resposta
> **B.** PII → sensitive information filters. Nomes de concorrentes → word filters (o *assunto* concorrência → denied topics). → [[07 - Bedrock Guardrails|Bedrock Guardrails]]

## Resultado

| Tentativa | Data | Acertos (de 30) | % | Notas para revisar |
|---|---|---|---|---|
| 1ª | | | | |
| 2ª (+1 dia) | | | | |
| 3ª (+1 semana) | | | | |
| 4ª (+1 mês) | | | | |

---
Índice: [[00 - Índice - Bedrock|Índice - Bedrock]] · Anterior: [[07 - Bedrock Guardrails|Bedrock Guardrails]] · Roadmap: [[11 - Road Map|Road Map]]
