## Como usar

1. Leia a questão e **marque a caixinha** da alternativa que você acha correta (clique no `[ ]`).
2. Escreva em **Minha justificativa** por que escolheu (ajuda a fixar).
3. Só então abra o **Gabarito** (clique na seta) e corrija.
4. Anote seus acertos na **Folha de resultado** no final.

> [!info] Cobertura
> **30 questões** no estilo AIF-C01. Questões **1–20 → Tarefa 4.1** · **21–30 → Tarefa 4.2**. As marcadas com **(Escolha 2)** são de **múltipla resposta**: só vale se acertar as duas.

> [!tip] Para refazer
> Ao terminar, peça a correção ou duplique esta nota como `IA Responsável - Formulário AAAA-MM-DD (respondido)`. Esta versão fica sempre limpa, e a Folha de resultado guarda o histórico.

---

### Questão 1
Um banco descobre que seu modelo de crédito tem **a mesma acurácia geral** de antes, mas **aprova muito menos pedidos de pessoas acima de 60 anos** com perfil financeiro igual. Qual dimensão de IA responsável está sendo violada?

- [ ] A) Robustez
- [ ] B) Controlabilidade
- [ ] C) Justiça (*fairness*)
- [ ] D) Transparência

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Justiça** — o modelo trata **grupos demográficos** de forma diferente. → [[IA Responsável - Conceitos e Riscos#1. As dimensões de IA responsável]]

---

### Questão 2
Um chatbot responde bem a perguntas normais, mas quando o usuário escreve com **erros de digitação** ou frases **propositalmente confusas**, ele passa a dar respostas erradas. Qual dimensão precisa melhorar?

- [ ] A) Veracidade e robustez
- [ ] B) Justiça
- [ ] C) Governança
- [ ] D) Privacidade

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Veracidade e robustez** — saída correta mesmo com entradas **inesperadas ou adversárias**. → [[IA Responsável - Conceitos e Riscos#1. As dimensões de IA responsável]]

---

### Questão 3
Uma corretora criou um assistente com Amazon Bedrock e quer garantir que ele **nunca dê recomendações de investimento** e **bloqueie discurso de ódio**, com o **menor esforço**. O que usar?

- [ ] A) SageMaker Clarify
- [ ] B) Amazon Bedrock Guardrails (denied topics + content filters)
- [ ] C) Amazon A2I
- [ ] D) Fine-tuning do modelo com exemplos de recusa

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Guardrails** — **denied topics** para o assunto proibido e **content filters** para ódio. Fine-tuning dá muito mais trabalho e não garante. → [[Bedrock Guardrail]]

---

### Questão 4
Um assistente com **RAG** às vezes responde com informações que **não estão nos documentos** da Knowledge Base. Qual política do Guardrails ajuda a detectar e bloquear isso?

- [ ] A) Word filters
- [ ] B) Denied topics
- [ ] C) Sensitive information filters
- [ ] D) Contextual grounding check

**Minha justificativa:** 

> [!success]- Gabarito
> **D) Contextual grounding check** — verifica se a resposta está **apoiada na fonte** e é relevante → reduz alucinação. → [[IA Responsável - Serviços AWS#Amazon Bedrock Guardrails]]

---

### Questão 5
Um app de atendimento não pode exibir **números de cartão de crédito e CPF** nas respostas do modelo, mas o resto da resposta deve ser mostrado. O que configurar?

- [ ] A) Guardrails com sensitive information filter no modo **mascarar**
- [ ] B) Amazon Macie no bucket S3
- [ ] C) Guardrails com denied topics
- [ ] D) Model Monitor com alerta de PII

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Sensitive information filter (mask)** — detecta PII e **mascara** só o trecho sensível. Macie acha PII em **dados armazenados no S3**, não em respostas do modelo.

---

### Questão 6
Uma agência gera imagens com IA para campanhas. Uma das imagens ficou **praticamente igual a um personagem famoso** de um estúdio de cinema. Qual risco legal da GenAI é esse?

- [ ] A) Alucinação
- [ ] B) Violação de propriedade intelectual
- [ ] C) Saída enviesada
- [ ] D) Risco ao usuário final

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Violação de PI** — conteúdo gerado reproduz obra protegida. → [[IA Responsável - Conceitos e Riscos#2. Riscos legais da IA generativa]]

---

### Questão 7
Um escritório de advocacia usou um LLM para escrever uma petição e o texto citou **decisões judiciais que não existem**. Qual o risco e a melhor mitigação?

- [ ] A) Toxicidade → content filters
- [ ] B) Violação de PI → usar modelo open source
- [ ] C) Alucinação → RAG com base de jurisprudência real + revisão humana
- [ ] D) Viés → SageMaker Clarify

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Alucinação** — mitigar com **RAG** (fontes reais), **grounding check** e **revisão humana** antes de usar.

---

### Questão 8
Um sistema de reconhecimento facial foi treinado com um dataset em que **90% das fotos são de pessoas de pele clara**. Ele erra muito mais com pessoas de pele escura. Qual a causa principal?

- [ ] A) Dataset não inclusivo/desbalanceado
- [ ] B) Temperatura alta na inferência
- [ ] C) Modelo com poucos parâmetros
- [ ] D) Falta de criptografia nos dados

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Dataset não inclusivo/desbalanceado** — o modelo aprende pouco sobre o grupo sub-representado. → [[IA Responsável - Conceitos e Riscos#3. Características de um bom dataset]]

---

### Questão 9
Um modelo tem **98% de acurácia no treino** e **61% no teste**. O que está acontecendo?

- [ ] A) Alto viés (underfitting)
- [ ] B) Alta variância (overfitting)
- [ ] C) Dataset balanceado demais
- [ ] D) Drift de dados

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Alta variância / overfitting** — decorou o treino e não generaliza. → [[IA Responsável - Conceitos e Riscos#4. Viés x variância]]

---

### Questão 10
Um modelo de previsão de preço de imóveis usa **só a metragem** como feature e erra muito **tanto no treino quanto no teste**. Diagnóstico?

- [ ] A) Overfitting
- [ ] B) Alta variância
- [ ] C) Alto viés (underfitting)
- [ ] D) Alucinação

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Alto viés / underfitting** — modelo **simples demais**. Solução: mais features ou modelo mais complexo.

---

### Questão 11
**Antes de treinar** um modelo de contratação, o RH quer verificar se o dataset tem **muito menos exemplos de mulheres** que de homens. Qual ferramenta e métrica?

- [ ] A) SageMaker Model Monitor · bias drift
- [ ] B) Amazon Bedrock Guardrails · content filter
- [ ] C) SageMaker Clarify · Class Imbalance (CI)
- [ ] D) Amazon A2I · revisão humana

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Clarify · CI** — métrica de viés **pré-treino** que mede desequilíbrio de quantidade entre grupos (*facets*). → [[IA Responsável - Serviços AWS#SageMaker Clarify]]

---

### Questão 12
Um modelo de aprovação de empréstimos estava justo no lançamento, mas **ao longo de 6 meses** a taxa de aprovação de um grupo começou a cair. Como detectar isso **automaticamente**?

- [ ] A) SageMaker Model Cards
- [ ] B) SageMaker Model Monitor (bias drift)
- [ ] C) SageMaker Ground Truth
- [ ] D) AWS AI Service Cards

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Model Monitor** — monitora **bias drift** em **produção** e dispara alertas.

---

### Questão 13
Um modelo de análise de sinistros de seguro deve enviar para **um analista humano** apenas os casos em que a **confiança da previsão for menor que 80%**. Qual serviço?

- [ ] A) Amazon Augmented AI (A2I)
- [ ] B) SageMaker Ground Truth
- [ ] C) SageMaker Clarify
- [ ] D) Amazon Bedrock Evaluations

**Minha justificativa:** 

> [!success]- Gabarito
> **A) A2I** — revisão humana de **previsões** com baixa confiança. Ground Truth é para **rotular dados de treino**.

---

### Questão 14
O time percebeu que **anotadores diferentes rotulam os mesmos exemplos de formas diferentes**, e isso está gerando viés no modelo. Qual prática o guia recomenda?

- [ ] A) Aumentar a temperatura do modelo
- [ ] B) Usar provisioned throughput
- [ ] C) Trocar o modelo por um maior
- [ ] D) Analisar a qualidade dos rótulos (ex.: vários anotadores por item e consolidação no Ground Truth)

**Minha justificativa:** 

> [!success]- Gabarito
> **D) Analisar qualidade dos rótulos** — prática citada no guia; o **Ground Truth** permite vários anotadores por item e consolida as respostas.

---

### Questão 15
Um modelo de triagem médica tem **95% de acurácia geral**, mas o time suspeita que ele é **bem pior para pacientes idosos**. Qual prática revela isso?

- [ ] A) Aumentar o dataset geral
- [ ] B) Análise por subgrupo
- [ ] C) Medir só a acurácia global com mais precisão
- [ ] D) Usar inferência batch

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Análise por subgrupo** — calcular as métricas **separadas por grupo**; a média esconde a diferença.

---

### Questão 16 (Escolha 2)
Uma empresa quer escolher um modelo de GenAI considerando **sustentabilidade e impacto ambiental**. Quais práticas são adequadas?

- [ ] A) Treinar um LLM próprio do zero para ter controle total
- [ ] B) Usar o **menor modelo** que atende à qualidade necessária
- [ ] C) Sempre escolher o maior modelo disponível
- [ ] D) Usar hardware eficiente como **AWS Inferentia / Trainium**
- [ ] E) Manter endpoints ligados 24h mesmo sem uso

**Minha justificativa:** 

> [!success]- Gabarito
> **B e D** — modelo do tamanho certo e hardware com melhor desempenho por watt. Treinar do zero e deixar recursos ociosos desperdiçam energia. → [[IA Responsável - Conceitos e Riscos#5. Escolha responsável do modelo (sustentabilidade)]]

---

### Questão 17 (Escolha 2)
Quais características descrevem um **bom dataset** segundo o guia?

- [ ] A) Vir de **fontes curadas** e confiáveis
- [ ] B) Ser o maior possível, não importa a origem
- [ ] C) Ser **inclusivo e diverso**, representando todos os grupos de usuários
- [ ] D) Conter só dados do grupo de clientes mais lucrativo
- [ ] E) Ter rótulos gerados aleatoriamente

**Minha justificativa:** 

> [!success]- Gabarito
> **A e C** — o guia cita: **inclusivo, diverso, fontes curadas, balanceado**.

---

### Questão 18 (Escolha 2)
Quais são **riscos legais** de usar IA generativa citados no guia?

- [ ] A) Perda de confiança do cliente
- [ ] B) Latência alta
- [ ] C) Custo por token
- [ ] D) Saídas enviesadas
- [ ] E) Limite de tamanho da janela de contexto

**Minha justificativa:** 

> [!success]- Gabarito
> **A e D** — os riscos do guia são: **violação de PI, saídas enviesadas, perda de confiança do cliente, risco ao usuário final e alucinações**. Latência, custo e contexto são limitações técnicas.

---

### Questão 19
Antes de adotar o **Amazon Rekognition**, a equipe jurídica quer ler os **casos de uso pretendidos, as limitações** e as escolhas de design responsável **publicadas pela AWS** para esse serviço. Onde encontrar?

- [ ] A) SageMaker Model Cards
- [ ] B) AWS Artifact
- [ ] C) AWS AI Service Cards
- [ ] D) SageMaker Model Registry

**Minha justificativa:** 

> [!success]- Gabarito
> **C) AI Service Cards** — documentação da AWS sobre **seus serviços e modelos**. Model Cards documentam **o seu** modelo. AWS Artifact traz relatórios de **compliance** (SOC, ISO). → [[IA Responsável - Serviços AWS#SageMaker Model Cards x AWS AI Service Cards]]

---

### Questão 20
Um arquiteto quer um **conjunto de boas práticas** da AWS para **projetar, desenvolver e operar** cargas de IA de forma responsável, começando pela definição do caso de uso. O que consultar?

- [ ] A) AWS Trusted Advisor
- [ ] B) AWS Well-Architected **Responsible AI Lens**
- [ ] C) Amazon Bedrock Guardrails
- [ ] D) AWS Config

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Responsible AI Lens** — lente do Well-Architected com boas práticas para todo o ciclo de vida de IA responsável.

---

### Questão 21
Qual afirmação descreve corretamente a diferença entre **transparência** e **explicabilidade**?

- [ ] A) São sinônimos
- [ ] B) Transparência = por que o modelo deu esta resposta; explicabilidade = com quais dados foi treinado
- [ ] C) Transparência = saber como o modelo foi construído (dados, treino, limitações); explicabilidade = entender por que ele deu uma resposta específica
- [ ] D) Transparência só existe em modelos open source

**Minha justificativa:** 

> [!success]- Gabarito
> **C)** — **transparência** = "como foi feito"; **explicabilidade** = "por que decidiu isso". → [[IA Responsável - Transparência e Explicabilidade#1. Transparente x explicável x caixa-preta]]

---

### Questão 22
Uma fintech precisa mostrar ao cliente **quais fatores** (renda, histórico, dívidas) **mais pesaram** na recusa do seu cartão. Qual técnica/ferramenta?

- [ ] A) Explicabilidade com valores SHAP (SageMaker Clarify)
- [ ] B) Bedrock Guardrails
- [ ] C) Model Registry
- [ ] D) Avaliação com ROUGE

**Minha justificativa:** 

> [!success]- Gabarito
> **A) SHAP / Clarify** — atribui a **importância de cada feature** à previsão individual.

---

### Questão 23
Um auditor pede um documento padronizado do **modelo que a própria empresa treinou**, com **uso pretendido, nível de risco, dados de treino e métricas de avaliação**. O que usar?

- [ ] A) AWS AI Service Cards
- [ ] B) SageMaker Model Dashboard
- [ ] C) Amazon CloudTrail
- [ ] D) SageMaker Model Cards

**Minha justificativa:** 

> [!success]- Gabarito
> **D) Model Cards** — documentação do **seu** modelo para transparência e auditoria.

---

### Questão 24
Uma empresa quer comparar **três FMs** no Bedrock quanto a **acurácia, robustez e toxicidade**, usando **datasets prontos**, sem montar equipe de avaliadores. Qual opção?

- [ ] A) Avaliação humana no Bedrock Evaluations
- [ ] B) Avaliação automática (programática) no Amazon Bedrock Evaluations
- [ ] C) SageMaker Model Monitor
- [ ] D) Amazon A2I

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Avaliação automática** — métricas prontas (acurácia, robustez, toxicidade) com datasets embutidos. → [[IA Responsável - Serviços AWS#Amazon Bedrock Evaluations]]

---

### Questão 25
Um hospital quer avaliar se as respostas de um assistente são **empáticas e adequadas para pacientes**, um critério subjetivo que exige **especialistas da área**. Qual tipo de avaliação?

- [ ] A) Avaliação automática com BLEU
- [ ] B) Avaliação de RAG
- [ ] C) Avaliação humana (equipe própria de especialistas) no Bedrock Evaluations
- [ ] D) Clarify pré-treino

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Avaliação humana** — critérios **subjetivos** (empatia, tom) pedem pessoas, de preferência especialistas.

---

### Questão 26
A equipe precisa avaliar **milhares de respostas** de um sistema RAG quanto a **correção e relevância**, com nota e **justificativa** para cada uma, mas **sem custo de avaliadores humanos**. Qual opção?

- [ ] A) LLM-as-a-judge / avaliação de RAG no Bedrock Evaluations
- [ ] B) Amazon A2I com Mechanical Turk
- [ ] C) SageMaker Model Cards
- [ ] D) Guardrails com word filters

**Minha justificativa:** 

> [!success]- Gabarito
> **A) LLM-as-a-judge** — um segundo LLM dá nota e **explica** cada resposta, em escala e mais barato que humanos.

---

### Questão 27
Uma seguradora precisa **justificar ao regulador cada decisão** de preço. Uma rede neural profunda tem **2% mais acurácia** que uma árvore de decisão. O que é mais adequado?

- [ ] A) Rede neural, porque acurácia é sempre prioridade
- [ ] B) Árvore de decisão (modelo interpretável), aceitando um pouco menos de desempenho
- [ ] C) Um LLM com temperatura alta
- [ ] D) Não documentar o modelo

**Minha justificativa:** 

> [!success]- Gabarito
> **B) Modelo interpretável** — trade-off **interpretabilidade x desempenho**: em cenário regulado, explicar cada decisão pesa mais que 2% de acurácia. → [[IA Responsável - Transparência e Explicabilidade#3. Os trade-offs]]

---

### Questão 28
Uma empresa publica a documentação do seu chatbot (uso pretendido, limitações, métricas), mas **não divulga os detalhes exatos** de como seus filtros de segurança funcionam. Por quê?

- [ ] A) Porque transparência é proibida por lei
- [ ] B) Porque filtros de segurança não podem ser documentados
- [ ] C) Para reduzir custos de armazenamento
- [ ] D) Trade-off segurança x transparência: detalhes demais facilitam burlar as proteções (jailbreak)

**Minha justificativa:** 

> [!success]- Gabarito
> **D) Segurança x transparência** — transparência total pode dar a atacantes o mapa para burlar os filtros. Equilíbrio: documentar sem expor o que permite o ataque.

---

### Questão 29
Um app de recomendação mostra **"Recomendado porque você assistiu X"** e tem botões **👍 / 👎** cujas respostas voltam para melhorar o modelo. Que princípios do guia isso aplica?

- [ ] A) Design centrado no humano: transparência da decisão e mecanismo de feedback do usuário
- [ ] B) Sustentabilidade e eficiência energética
- [ ] C) Criptografia em trânsito
- [ ] D) Inferência assíncrona

**Minha justificativa:** 

> [!success]- Gabarito
> **A) Design centrado no humano** — explica a decisão e coleta **feedback** do usuário. → [[IA Responsável - Transparência e Explicabilidade#4. Design centrado no humano]]

---

### Questão 30
Uma startup quer usar um **modelo open source** pela **transparência** (pode inspecionar arquitetura e pesos). Antes de colocar em um **produto comercial**, o que mais precisa verificar?

- [ ] A) Se o modelo tem mais de 100 bilhões de parâmetros
- [ ] B) Se o modelo roda em GPU
- [ ] C) A **licença** do modelo e a origem dos dados de treino
- [ ] D) Se o modelo tem um Guardrail embutido

**Minha justificativa:** 

> [!success]- Gabarito
> **C) Licença e dados** — o guia cita **open source, dados e licenciamento** como itens de transparência; nem toda licença permite uso comercial.

---

## Folha de resultado

| Data | Acertos (de 30) | Questões que errei | O que revisar |
|---|---|---|---|
|  |  |  |  |
|  |  |  |  |
|  |  |  |  |

> [!note] Meta
> **24+ acertos (80%)** = pronto para o Domínio 4. Abaixo disso, use a tabela **"O que a prova exige"** no [[Índice - IA Responsável]] para achar a nota de cada questão errada.

---
Voltar: [[Índice - IA Responsável]] · [[IA Responsável - Serviços AWS]]
