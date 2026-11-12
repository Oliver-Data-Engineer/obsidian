## Resumo

**Peso: 14%** · Como desenvolver IA **justa, segura, transparente e explicável**, os riscos legais da GenAI e as ferramentas AWS para detectar viés e monitorar modelos.

> [!info] Ideia central
> IA responsável = **justiça + segurança + veracidade + transparência**, com **humanos supervisionando** e ferramentas medindo viés.

## Tarefa 4.1 — Desenvolvimento de sistemas de IA responsáveis

**O que a prova espera:**
- Características de IA responsável: **viés, justiça, inclusão, robustez, segurança (safety), veracidade**.
- Ferramentas que ajudam nisso (ex.: **Guardrails for Amazon Bedrock**).
- Práticas responsáveis na escolha de modelo: questões **ambientais e de sustentabilidade**.
- Riscos legais da GenAI: violação de **propriedade intelectual**, resultados enviesados, **perda de confiança** do cliente, risco para o usuário final, **alucinações**.
- Características de bons datasets: **inclusivos, diversos, de fontes curadas, balanceados**.
- Efeitos de **viés e variância**: impacto em grupos demográficos, imprecisão, overfitting, underfitting.
- Ferramentas para detectar e monitorar viés e confiabilidade: análise da qualidade dos rótulos, **auditorias humanas**, análise por **subgrupo**, **SageMaker Clarify**, **SageMaker Model Monitor**, **Amazon A2I**.

| Ferramenta | Para quê |
|---|---|
| **Guardrails for Amazon Bedrock** | Filtra conteúdo nocivo, tópicos negados, PII; checa grounding |
| **SageMaker Clarify** | Detecta **viés** nos dados/modelo e **explica** previsões (importância de features) |
| **SageMaker Model Monitor** | Monitora **drift** de dados/qualidade/viés em produção |
| **Amazon A2I (Augmented AI)** | **Revisão humana** de previsões com baixa confiança |
| **SageMaker Ground Truth** | Rotulagem com humanos (inclui RLHF) |

| Viés x Variância | Sintoma |
|---|---|
| **Alto viés** | **Underfitting** — modelo simples demais, erra no treino e no teste |
| **Alta variância** | **Overfitting** — vai bem no treino, mal em dados novos |

## Tarefa 4.2 — Importância de modelos transparentes e explicáveis

**O que a prova espera:**
- Diferença entre modelos **transparentes/explicáveis** e modelos "caixa-preta".
- Ferramentas para transparência: **SageMaker Model Cards**, modelos open source, documentação de dados e licenças.
- Trade-offs entre **segurança e transparência** (interpretabilidade x desempenho).
- Princípios de **design centrado no humano** para IA explicável.

| Conceito | Em uma linha |
|---|---|
| **Transparência** | Saber **como** o modelo foi feito (dados, treino, limitações) |
| **Explicabilidade** | Entender **por que** ele deu uma resposta específica |
| **Interpretabilidade x desempenho** | Modelos simples (árvore de decisão) são mais explicáveis; redes profundas, mais precisas e opacas |
| **SageMaker Model Cards** | Documento padronizado do modelo: uso pretendido, riscos, métricas |
| **Human-centered design** | Explicações pensadas para quem usa: claras, úteis e acionáveis |

> [!tip] Estudo aprofundado
> Notas completas, serviços e simulado deste domínio: [[Índice - IA Responsável]] · 📝 [[IA Responsável - Formulário de Respostas]]

## Autoavaliação

- [ ] Sei citar as dimensões de IA responsável.
- [ ] Sei para que servem Clarify, Model Monitor, A2I e Guardrails.
- [ ] Sei os riscos legais da GenAI.
- [ ] Sei relacionar viés/variância com under/overfitting.
- [ ] Sei a diferença entre transparência e explicabilidade e o que é um Model Card.

---
Início: [[00 - Início - Guia do Exame]] · Anterior: [[04 - Domínio 3 - Aplicações de Foundation Models]] · Próximo: [[06 - Domínio 5 - Segurança, Compliance e Governança]] · ✅ [[09 - Checklist de Estudo]]
