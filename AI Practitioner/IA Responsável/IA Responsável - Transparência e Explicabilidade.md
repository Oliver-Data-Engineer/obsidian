## Resumo

**Tarefa 4.2** do guia: diferença entre modelos **transparentes/explicáveis** e **caixa-preta**, as ferramentas que ajudam a enxergar dentro do modelo, os **trade-offs** envolvidos e os princípios de **design centrado no humano**.

> [!info] Ideia central
> - **Transparência** = saber **como o modelo foi feito** (dados, treino, limitações, licença).
> - **Explicabilidade** = entender **por que ele deu esta resposta**.
> - Mais simples = mais explicável; mais complexo = geralmente mais preciso e mais opaco.

---

## 1. Transparente x explicável x caixa-preta

| | **Transparente / explicável** | **Caixa-preta** (*black box*) |
|---|---|---|
| Exemplos | Regressão linear/logística, árvore de decisão, regras | Redes neurais profundas, LLMs, ensembles grandes |
| Consegue mostrar o raciocínio? | **Sim**, direto no modelo (coeficientes, caminho na árvore) | **Não diretamente**; precisa de técnicas *post-hoc* (SHAP, PDP) |
| Desempenho | Bom em problemas simples | Melhor em problemas complexos (imagem, texto) |
| Auditoria / regulação | Fácil de justificar | Mais difícil; exige documentação e explicações extras |

| Termo | Pergunta que responde |
|---|---|
| **Transparência** | "Com quais dados, como e para que este modelo foi construído?" |
| **Interpretabilidade** | "Um humano entende o **mecanismo interno** do modelo?" |
| **Explicabilidade** | "Por que o modelo decidiu **isto** para **este caso**?" |

> [!warning] Pegadinha
> Explicabilidade **não** exige abrir todo o código ou os pesos do modelo. Basta explicar a decisão de forma compreensível (ex.: "renda e histórico de pagamento foram os fatores que mais pesaram").

---

## 2. Ferramentas de transparência e explicabilidade

| Ferramenta (guia) | O que traz | Detalhes |
|---|---|---|
| **SageMaker Model Cards** | Documentação padronizada do **seu** modelo: uso pretendido, nível de risco, dados de treino, métricas, resultados de viés | → [[SageMaker - Governança e Segurança]] |
| **Amazon Bedrock Model Evaluations** | Avaliar e **comparar FMs** em acurácia, robustez, toxicidade (automática, humana ou LLM-as-a-judge) | → [[IA Responsável - Serviços AWS#Amazon Bedrock Evaluations]] |
| **Modelos open source** | Pesos, arquitetura e às vezes dados **abertos para inspeção** | Disponíveis no **SageMaker JumpStart** e no Bedrock |
| **Dados (documentação)** | Saber a **origem** e a **linhagem** dos dados | ML Lineage Tracking, Glue Data Catalog |
| **Licenciamento** | Saber se o modelo/dados podem ser usados **comercialmente** | Mostrado no JumpStart/Bedrock |
| **AWS AI Service Cards** | Uso pretendido e limitações dos **serviços e modelos da AWS** (Rekognition, Polly, Nova, Guardrails...) | Publicados pela AWS |
| **SHAP / Clarify** | Importância de cada **feature** numa previsão (local) ou no modelo todo (global) | → [[IA Responsável - Serviços AWS#SageMaker Clarify]] |

---

## 3. Os trade-offs

### Interpretabilidade x desempenho
- Um modelo **simples** (árvore, regressão) é fácil de explicar, mas pode ser **menos preciso**.
- Um modelo **complexo** (rede profunda) é mais preciso, mas **opaco**.
- **Regra da prova:** se o cenário é **regulado** (crédito, saúde, seguros, RH) e exige justificar **cada decisão**, prefira o modelo **interpretável**, mesmo com um pouco menos de acurácia, ou use técnicas de explicação (SHAP) + documentação.

### Segurança x transparência
- Transparência **total** pode ajudar atacantes: publicar exatamente como funcionam os filtros e os dados de treino facilita **jailbreak**, **prompt injection**, **envenenamento de dados** ou extração de dados sensíveis.
- Abrir os dados de treino pode expor **PII** ou segredos comerciais.
- **Equilíbrio:** documentar uso pretendido, limitações e métricas (Model/Service Cards) **sem** revelar detalhes que permitam burlar as proteções.

| Mais transparência | Mais segurança |
|---|---|
| Auditoria, confiança, compliance | Menos superfície de ataque, proteção de PI e de dados |

---

## 4. Design centrado no humano

Princípios do guia para IA explicável (*human-centered design*):

| Princípio | Na prática |
|---|---|
| **Mecanismos de feedback do usuário** | 👍/👎, "reportar resposta", correções que voltam para melhorar o modelo (RLHF, Ground Truth) |
| **Transparência da decisão da IA** | Dizer que é uma IA, mostrar **fontes/citações** (RAG), mostrar o **motivo** da recomendação e o **nível de confiança** |
| **Explicações para quem usa** | Linguagem clara, adequada ao público (cliente ≠ cientista de dados), **acionável** ("melhore X para ser aprovado") |
| **Humano no controle** | Decisões de alto impacto revisadas por pessoas (**A2I**); usuário pode contestar |
| **Projetar para todos** | Acessibilidade e inclusão desde o início |

---

## Exemplo para Associação Mental

**O médico.** Um médico **transparente** mostra o diploma, onde estudou e em que é especialista (**Model Card**). Um médico **explicável** diz *por que* receitou aquele remédio para **você** (**SHAP**). O médico **caixa-preta** acerta muito, mas só diz "confie em mim". Em decisão grave, o paciente quer uma **segunda opinião humana** (**A2I**) e um canal para reclamar (**feedback**). E o hospital não publica o código do cofre de remédios só para ser "transparente" (**segurança x transparência**).

## 📝 Meu entendimento
> _Explique com suas palavras a diferença entre transparência e explicabilidade, com um exemplo._

---
Voltar: [[Índice - IA Responsável]] · Anterior: [[IA Responsável - Conceitos e Riscos]] · Próximo: [[IA Responsável - Serviços AWS]]

Fontes: [AIF-C01 Exam Guide – Domínio 4](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/ai-practitioner-01-domain4.html) · [AWS AI Service Cards](https://aws.amazon.com/ai/responsible-ai/resources/) · [SageMaker Model Cards](https://docs.aws.amazon.com/sagemaker/latest/dg/model-cards.html)
