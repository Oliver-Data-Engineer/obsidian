## Resumo

Análise da **Tentativa 1 do Simulado 4** (Udemy · *[Simulados] AWS Certified AI Practitioner AIF-C01 PT-BR*), feita em 2026-11-14. Tempo usado: **1h16** de 1h30.

> [!warning] Placar: **46 / 65 (70%)**: aprovado no limite ⚠️
> Caiu **16 pontos** em relação ao Simulado 3 (86%). Ficou **exatamente** na linha de corte; na prova real isso é risco alto.
> 🏷️ **15 marcadas para revisão**: acertou só **6** e errou **9**. Quando ficou em dúvida, errou 60% das vezes.
> 🎯 **10 erros sem marcação**: você respondeu com segurança e errou. Esses são os mais perigosos, porque não aparecem na revisão.

## Evolução por domínio

| Domínio                               | Peso    | S1  | S2  | S3  | **S4**          | Tendência                              |
| ------------------------------------- | ------- | --- | --- | --- | --------------- | -------------------------------------- |
| 2. Fundamentos de IA Generativa       | 24%     | 94% | 81% | 94% | **88%** (14/16) | ➖ estável                             |
| 3. Aplicações de Foundation Models    | **28%** | 67% | 72% | 89% | **83%** (15/18) | ➖ estável                             |
| 1. Fundamentos de IA e ML             | 20%     | 54% | 77% | 77% | **69%** (9/13)  | 🔻 −8                                  |
| 5. Segurança, Compliance e Governança | 14%     | 44% | 89% | 89% | **44%** (4/9)   | 🔻🔻 **−45**: prioridade máxima        |
| 4. IA Responsável                     | 14%     | 67% | 67% | 78% | **44%** (4/9)   | 🔻🔻 **−34**: prioridade máxima        |

> [!danger] O que os quatro simulados mostram juntos
> 1. **Os domínios 4 e 5 desabaram juntos** (10 dos 19 erros). Neste simulado as questões cobraram **conceitos de governança** (residência, registro de dados, trade-offs, Model Cards), não só nomes de serviço. A nota boa do S3 nesses domínios escondia essa lacuna.
> 2. **Viés x variância / overfitting**: **4º simulado seguido** com erro nesse tema (S2 #6; S4 #9, #30 e #45). É o ponto mais recorrente de todos.
> 3. **Audit Manager como distrator**: **3ª vez** (S2 #41 → Config; S3 #32 → Model Monitor; S4 #37 → Trusted Advisor). Regra: **Audit Manager só é a resposta quando o enunciado fala em "coletar evidências para auditoria"**.
> 4. **FMs aprendem com dados não rotulados** (auto-supervisionado): **2ª vez** (S2 #17, S4 #11).

## As 15 questões marcadas para revisão

| Questão | Resultado | Você marcou | Correto | Por que |
|---|---|---|---|---|
| #9 **Causa** do overfitting | ❌ | Modelo não é atualizado com dados novos | Modelo **complexo demais** decora o **ruído** do treino | Falta de atualização = **drift**, não overfitting |
| #12 Dimensão **Equidade** | ✅ | Inclusividade e evitar discriminação | — | Pode confiar |
| #22 Conceito de **registrar sistematicamente** os dados do processamento de IA | ❌ | Ciclo de vida dos dados | **Registro de dados** (*data logging*) | A pergunta descreve literalmente o nome. Ciclo de vida = coleta → uso → descarte |
| #30 **Indicadores** de overfitting (Escolha 2) | ❌ | Treino alto/teste baixo ✅ + **alto bias** | Treino alto/teste baixo + **complexidade/parâmetros em excesso** | **Alto bias = underfitting** |
| #34 Recurso do Bedrock que **automatiza tarefas** | ✅ | Agentes | — | Pode confiar |
| #35 Treinar modelos com **menor impacto ambiental** | ❌ | Instâncias C (compute optimized) | **AWS Trainium** | Chips próprios da AWS = mais **eficiência energética**. Trainium = **treino**; Inferentia = **inferência** |
| #36 **Injeção de prompt** x **exposição** | ❌ | D = exposição; B = injeção | **C = injeção** (comando "DELETE" embutido); **A = exposição** (vazou uma chave secreta) | **Exposição** = o modelo **revela dado sensível**. **Injeção** = a resposta/entrada carrega uma **instrução maliciosa** |
| #37 **Uma** ferramenta que **analisa continuamente** e dá **recomendações de boas práticas** | ❌ | Audit Manager | **Trusted Advisor** | "Recomendações / boas práticas / checks" = **Trusted Advisor** |
| #43 Capacidades do **Q Developer** (Escolha 2) | ❌ | Custos em linguagem natural ✅ + **modificar recursos** para otimizar custo | Custos em linguagem natural + **entender e gerenciar a infraestrutura** | O Q Developer **responde e orienta**; não sai alterando recursos por conta própria |
| #45 Trade-offs descritos **corretamente** (Escolha 2) | ❌ | Interpretabilidade x desempenho ✅ + "**alta variância → underfitting**" | Interpretabilidade x desempenho + **Controlabilidade x complexidade** | **Alta variância = overfitting**. A frase estava invertida de propósito |
| #48 Treinar modelo **personalizado** + integrar **LLM pré-treinado** | ❌ | SageMaker para as duas coisas | **SageMaker** (treino próprio) + **Bedrock** (LLM pronto) | "Pré-treinado, via API, sem gerenciar infra" = **Bedrock** |
| #53 Classificar tickets **sem dados rotulados** | ✅ | Zero-shot | — | Pode confiar |
| #54 Métrica que compara **sequências de palavras** com resumo humano | ✅ | ROUGE | — | Pode confiar. ROUGE = resumo; BLEU = tradução |
| #61 Leigos consultando dados em linguagem natural | ✅ | Modelo GPT | — | Pode confiar |
| #64 Papel do **discriminador** na GAN | ✅ | Classificar real x falso | — | Pode confiar |

> [!tip] Calibração da dúvida
> As 6 marcadas que você acertou eram de **definição direta** (equidade, ROUGE, GAN, zero-shot). As 9 que errou eram **pegadinhas de formulação**: frase invertida (#45), nome literal na pergunta (#22), distrator repetido (#37). Na revisão, **releia a alternativa palavra por palavra** procurando inversões ("alta variância → **underfitting**", "alto **bias**" como sinal de overfitting).

## Mapa dos erros por tema

### 1. Overfitting, viés e variância (3 erros: #9, #30, #45) 🔴 recorrente

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #9 Por que ocorre overfitting | Falta de atualização | Modelo **complexo** que captura **ruído** | Falta de atualização = **drift** |
| #30 Indicadores de overfitting | **Alto bias** | **Parâmetros em excesso** para poucos dados | Alto bias = **underfitting** |
| #45 Trade-off correto | "Alta variância → underfitting" | **Controlabilidade x complexidade** | Alta variância = **overfitting** |

> [!tip] Tabela para decorar de vez
> | | **Underfitting** | **Overfitting** |
> |---|---|---|
> | Erro dominante | **Alto viés (bias)** | **Alta variância** |
> | Treino | Ruim | **Ótimo** |
> | Teste / dados novos | Ruim | **Ruim** |
> | Causa | Modelo **simples demais**, poucas features, pouco treino | Modelo **complexo demais**, poucos dados, treino demais |
> | Correção | Modelo mais complexo, mais features, treinar mais | **Mais dados**, regularização, early stopping, menos features, data augmentation |
>
> Macete: **V**ariância = **V**ê demais (decora até o ruído). **B**ias = **B**urro (simples demais).
>
> **Drift** é outra coisa: o modelo era bom, mas o **mundo mudou** → retreinar com dados novos.

Revisar: [[01 - IA Responsável - Conceitos e Riscos#4. Viés x variância]] · [[02 - O que é Machine Learning|O que é Machine Learning]] · [[10 - Glossário do Exame|Glossário do Exame]]

### 2. Governança de dados: conceitos (2 erros: #4, #22) 🔴

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #4 Dados ambientais sensíveis em **várias jurisdições** e proteção contra acesso indevido | Políticas de bucket do S3 | **Residência regional dos dados** + **criptografia em trânsito e em repouso** | "Jurisdições / leis locais" = **residência**. Bucket policy é **um** controle de acesso, não garante as duas coisas |
| #22 **Registrar sistematicamente** dados do processamento de IA | Ciclo de vida | **Registro de dados** | Leia o verbo da pergunta |

> [!tip] Estratégias de governança de dados (tarefa 5.2 da ementa)
> | Conceito | O que é | Palavra-chave no enunciado |
> |---|---|---|
> | **Ciclo de vida dos dados** | Coleta → armazenamento → uso → arquivamento → descarte | "do início ao fim", "fases" |
> | **Registro de dados** (*logging*) | Gravar sistematicamente o que foi processado, por quem e quando | "registrar", "rastrear o processamento" |
> | **Residência dos dados** | Manter os dados numa **região/país** específico | "jurisdição", "lei local", "não pode sair do país" |
> | **Monitoramento de dados** | Acompanhar qualidade e anomalias continuamente | "qualidade", "anomalias", "drift" |
> | **Retenção de dados** | Por **quanto tempo** guardar e quando apagar | "por X anos", "excluir após" |
> | **Linhagem de dados** (*lineage*) | **De onde veio** e por quais transformações passou | "origem", "procedência" |

Revisar: [[06 - Domínio 5 - Segurança, Compliance e Governança]] · [[01 - Segurança, Identidade e Compliance|Segurança, Identidade e Compliance]]

### 3. Ferramentas de governança e conformidade (3 erros: #37, #40, #41) 🔴

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #37 Análise contínua + **recomendações de boas práticas** | Audit Manager | **Trusted Advisor** | Recomendações = Trusted Advisor |
| #40 Ferramentas de **governança** do SageMaker | Model Dashboard + Role Manager + **Clarify** | **Role Manager + Model Cards + Model Dashboard** | O trio de **governança** do SageMaker. Clarify é de **viés/explicabilidade** |
| #41 Afirmação correta sobre **Model Cards** | "Requisitos técnicos de implantação" | **Como o modelo deve ser usado** em produção | Model Card = **documentação**: uso pretendido, riscos, métricas, limitações |

> [!tip] Governança na AWS: quem faz o quê
> | Serviço | Faz | Palavra-chave |
> |---|---|---|
> | **Trusted Advisor** | Checks automáticos e **recomendações** (custo, segurança, desempenho, limites) | "recomendações", "boas práticas" |
> | **Audit Manager** | Coleta **evidências** para auditoria e frameworks de compliance | "evidências", "auditor", "relatório de auditoria" |
> | **Config** | Histórico de **configuração** e regras de conformidade | "mudança de configuração", "regra violada" |
> | **CloudTrail** | **Quem** chamou **qual API** e quando | "quem fez", "chamadas de API" |
> | **Artifact** | Baixar **relatórios de compliance da AWS** (SOC, ISO) | "relatório da AWS", "certificação" |
> | **SageMaker Role Manager** | Permissões **mínimas** para personas de ML | "papéis", "permissões de ML" |
> | **SageMaker Model Cards** | **Documentar** o modelo (uso, riscos, avaliação) | "documentar", "uso pretendido" |
> | **SageMaker Model Dashboard** | **Visão central** de todos os modelos e alertas | "visão única", "todos os modelos" |

Revisar: [[02 - Gerenciamento e Governança#Os 5 lado a lado]] · [[06 - SageMaker - Governança e Segurança|SageMaker - Governança e Segurança]]

### 4. Segurança de prompts (2 erros: #36, #38) ⚠️

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #36 Associar respostas a **injeção** e **exposição** | D = exposição; B = injeção | **C = injeção**; **A = exposição** | Exposição = **vazou segredo/dado sensível**. Injeção = **instrução maliciosa** embutida |
| #38 Manter respostas **seguras e no contexto** | API própria que filtra todas as saídas | **Instruções explícitas no prompt** para ficar no escopo e ignorar conteúdo malicioso | O gabarito prefere a solução **mais simples e direta**. Construir uma camada personalizada é exagero |

> [!note] Sobre a #38
> Na AWS, a resposta ideal costuma ser **Bedrock Guardrails**. Como essa opção não estava disponível, o gabarito ficou com **engenharia de prompt** (instruções de escopo/sistema), não com **construir uma API do zero**. Regra geral da prova: entre "configurar algo pronto/simples" e "desenvolver uma solução personalizada", escolha o **pronto/simples**.

Revisar: [[06 - Riscos e Segurança em Prompts|Riscos e Segurança em Prompts]] · [[07 - Bedrock Guardrails|Bedrock Guardrails]]

### 5. IA Responsável: dimensões e sustentabilidade (2 erros: #35, #51) ⚠️

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #35 Treinar com **menor impacto ambiental** | Instâncias C | **Trainium** | Sustentabilidade em ML = **Trainium** (treino) / **Inferentia** (inferência) |
| #51 Garantir que o modelo **não prejudique grupos demográficos** (Escolha 2) | Equidade ✅ + **Veracidade** | Equidade + **Transparência** | Veracidade = respostas **corretas** (alucinação). Grupos + confiança = **equidade + transparência** |

Revisar: [[01 - IA Responsável - Conceitos e Riscos|IA Responsável - Conceitos e Riscos]] · [[09 - O que é Deep Learning|O que é Deep Learning]]

### 6. Escolha de serviço (4 erros: #6, #19, #43, #48) ⚠️

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #6 **Extrair texto** de documentos no S3 + detectar **PII** (Escolha 2) | Comprehend ✅ + **Macie** | Comprehend + **Textract** | Documento escaneado → **Textract** primeiro. A detecção de PII no **texto** fica com o **Comprehend** |
| #19 Busca em linguagem natural priorizando **termos médicos** (Escolha 2) | Kendra ✅ + **Lex** | Kendra + **Comprehend Medical** | Lex = chatbot. Entidades médicas = **Comprehend Medical** |
| #43 Capacidades do **Q Developer** | "Modificar recursos" | **Entender e gerenciar a infraestrutura** + perguntas de custo | Q Developer **explica e sugere**; não altera recursos sozinho |
| #48 Modelo **próprio** + **LLM pré-treinado** | Só SageMaker | **SageMaker + Bedrock** | Modelo pronto via API = **Bedrock** |

Revisar: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · [[02 - Amazon Comprehend Medical|Amazon Comprehend Medical]] · [[16 - Amazon Q|Amazon Q]]

### 7. Foundation Models: treino, prompt e dados em tempo real (3 erros: #11, #13, #44)

| Questão | Você marcou | Correto | Regra |
|---|---|---|---|
| #11 Como os FMs são treinados | Dados **rotulados**, auto-supervisionado | Dados **não rotulados**, auto-supervisionado | Auto-supervisionado = o **próprio texto** gera o rótulo. Se tivesse rótulo, seria supervisionado |
| #13 Framework **obscuro**, pouco presente no treino | Chain-of-thought | **Few-shot** com 3–5 trechos da documentação interna | CoT melhora o **raciocínio**, não traz **conhecimento novo**. Exemplos reais ensinam a sintaxe |
| #44 Usar **sensores em tempo real** e **estoque atual** | Subir tudo no S3 para o FM usar | **Bedrock Agents** chamando APIs internas | Dado que muda **o tempo todo** → **Agent + API**. Documento estático → **Knowledge Base (RAG)** |

Revisar: [[07 - Diferenças entre os Tipos de Aprendizado|Diferenças entre os Tipos de Aprendizado]] · [[03 - Tipos de Prompt|Tipos de Prompt]] · [[06 - Bedrock Agents|Bedrock Agents]]

---

## 🔁 Reforço: 12 questões nos pontos fracos

### R1
Um modelo tem **99% de acurácia no treino** e **62% em produção**. Qual o diagnóstico e a correção?

- [ ] A) Underfitting; usar um modelo mais complexo
- [ ] B) Overfitting (alta variância); mais dados, regularização ou early stopping
- [ ] C) Alto viés; adicionar mais features
- [ ] D) Data drift; nada a fazer no treino

> [!success]- Gabarito
> **B.** Ótimo no treino e ruim fora = **overfitting** = **alta variância**.

### R2
Um modelo de previsão de vendas tem **acurácia baixa no treino e no teste**. O que está acontecendo?

- [ ] A) Alta variância
- [ ] B) Overfitting
- [ ] C) Alto viés (underfitting)
- [ ] D) Vazamento de dados

> [!success]- Gabarito
> **C.** Ruim nos dois = modelo **simples demais** = **alto viés**.

### R3
Um modelo de crédito funcionou bem por 2 anos e agora piorou depois de uma mudança nas taxas de juros. Qual a causa?

- [ ] A) Overfitting
- [ ] B) Underfitting
- [ ] C) Drift dos dados; retreinar com dados recentes
- [ ] D) Alta variância

> [!success]- Gabarito
> **C.** O modelo não mudou; o **mundo** mudou. Isso é **drift**, não overfitting (era o distrator da #9).

### R4
Uma lei exige que dados de pacientes **brasileiros não saiam do Brasil**. Que conceito de governança atende?

- [ ] A) Retenção de dados
- [ ] B) Residência de dados (usar a Região sa-east-1)
- [ ] C) Linhagem de dados
- [ ] D) Ciclo de vida dos dados

> [!success]- Gabarito
> **B.** País/jurisdição = **residência**.

### R5
Uma empresa precisa saber **de onde veio** cada dado de treino e **quais transformações** ele sofreu. Que conceito é esse?

- [ ] A) Linhagem de dados
- [ ] B) Retenção de dados
- [ ] C) Registro de dados
- [ ] D) Residência de dados

> [!success]- Gabarito
> **A.** Origem + transformações = **linhagem**. (Registro = gravar **o que foi processado**.)

### R6
A equipe quer uma ferramenta que **verifique continuamente** a conta e **recomende** melhorias de segurança, custo e desempenho. Qual?

- [ ] A) AWS Audit Manager
- [ ] B) AWS Config
- [ ] C) AWS Trusted Advisor
- [ ] D) AWS Artifact

> [!success]- Gabarito
> **C.** "Recomendações de boas práticas" = **Trusted Advisor**. Audit Manager = **evidências**.

### R7
Um auditor externo pede **evidências** de que os controles do framework de compliance foram seguidos no último trimestre. Qual serviço?

- [ ] A) AWS Trusted Advisor
- [ ] B) AWS Audit Manager
- [ ] C) Amazon CloudWatch
- [ ] D) SageMaker Model Cards

> [!success]- Gabarito
> **B.** Este é o **único** cenário em que Audit Manager ganha: **evidências para auditoria**.

### R8 (Escolha 3)
Quais são ferramentas de **governança de modelos** do SageMaker?

- [ ] A) SageMaker Role Manager
- [ ] B) SageMaker Model Cards
- [ ] C) SageMaker Model Dashboard
- [ ] D) SageMaker Data Wrangler

> [!success]- Gabarito
> **A, B e C.** Data Wrangler prepara dados. (Clarify, que você marcou na #40, é de **viés/explicabilidade**.)

### R9
Um chatbot responde: "Seu pedido foi enviado. Aliás, a senha do banco de dados é `admin123`." Que risco é esse?

- [ ] A) Injeção de prompt
- [ ] B) Jailbreak
- [ ] C) Exposição (vazamento de dado sensível)
- [ ] D) Alucinação

> [!success]- Gabarito
> **C.** O modelo **revelou** um segredo = **exposição**.

### R10
Uma startup quer **treinar** um modelo grande com **menor custo e menor consumo de energia**. Qual instância?

- [ ] A) AWS Inferentia
- [ ] B) AWS Trainium
- [ ] C) Instâncias C (compute optimized)
- [ ] D) Instâncias T (burstable)

> [!success]- Gabarito
> **B.** **Trainium = treino**; **Inferentia = inferência**. Os dois são a resposta de **sustentabilidade**.

### R11
Um assistente precisa responder com o **preço atual** dos produtos, que muda várias vezes por dia no ERP. Qual a melhor abordagem no Bedrock?

- [ ] A) Fine-tuning semanal com a tabela de preços
- [ ] B) Knowledge Base com um PDF de preços
- [ ] C) Agent com action group chamando a API do ERP
- [ ] D) Colocar a tabela inteira no prompt

> [!success]- Gabarito
> **C.** Dado que muda **em tempo real** = **Agent + API**. Knowledge Base é para documentos relativamente estáticos.

### R12
O modelo gera código errado para uma **biblioteca interna** que não existe na internet. Qual técnica de prompt ajuda mais?

- [ ] A) Chain-of-thought
- [ ] B) Zero-shot
- [ ] C) Few-shot com exemplos reais da documentação interna
- [ ] D) Aumentar a temperatura

> [!success]- Gabarito
> **C.** Falta **conhecimento** → dar **exemplos**. CoT só ajuda no **raciocínio**.

**Resultado do reforço:** ___ / 12 (meta: 11+)

---

## Plano até o Simulado 5

| Dia | Foco | Notas |
|---|---|---|
| 1 | **Overfitting x underfitting x drift** (tabela + macete) + R1–R3. Escrever a tabela de memória até acertar | [[01 - IA Responsável - Conceitos e Riscos#4. Viés x variância]] · [[02 - O que é Machine Learning\|O que é Machine Learning]] |
| 2 | **Governança de dados** (residência, registro, ciclo de vida, retenção, linhagem, monitoramento) + R4–R5 | [[06 - Domínio 5 - Segurança, Compliance e Governança]] |
| 3 | **Trusted Advisor x Audit Manager x Config x CloudTrail x Artifact** + trio de governança do SageMaker + R6–R8 | [[02 - Gerenciamento e Governança\|Gerenciamento e Governança]] · [[06 - SageMaker - Governança e Segurança\|SageMaker - Governança e Segurança]] |
| 4 | Dimensões de IA Responsável + trade-offs + Trainium/Inferentia + riscos de prompt + R9–R10 + [[04 - IA Responsável - Formulário de Respostas\|IA Responsável - Formulário de Respostas]] | [[01 - IA Responsável - Conceitos e Riscos\|IA Responsável - Conceitos e Riscos]] · [[06 - Riscos e Segurança em Prompts\|Riscos e Segurança em Prompts]] |
| 5 | Refazer os **reforços dos Simulados 2, 3 e 4** (só as questões erradas) + R11–R12 | [[02 - Udemy Simulado 2 - Tentativa 1 - Análise e Reforço\|S2]] · [[03 - Udemy Simulado 3 - Tentativa 1 - Análise e Reforço\|S3]] |
| 6 | **Simulado 5** com meta de **80%+**, e **domínios 4 e 5 acima de 70%** | — |

## Histórico de simulados

| Data | Simulado | Tentativa | Nota | Pior domínio |
|---|---|---|---|---|
| 2026-11-12 | Udemy Simulado 1 | 2 | 44/65 (68%) | Segurança (44%) · Fundamentos IA/ML (54%) |
| 2026-11-12 | Udemy Simulado 2 | 1 | 50/65 (76%) ✅ | IA Responsável (67%) · Aplicações de FMs (72%) |
| 2026-11-13 | Udemy Simulado 3 | 1 | 56/65 (86%) ✅ | Fundamentos IA/ML (77%) · IA Responsável (78%) |
| 2026-11-14 | Udemy Simulado 4 | 1 | **46/65 (70%)** ⚠️ | Segurança (44%) · IA Responsável (44%) |
|  |  |  |  |  |

---
Anterior: [[03 - Udemy Simulado 3 - Tentativa 1 - Análise e Reforço|Udemy Simulado 3 - Tentativa 1 - Análise e Reforço]] · Início: [[00 - Início - Guia do Exame]] · Checklist: [[09 - Checklist de Estudo]]
