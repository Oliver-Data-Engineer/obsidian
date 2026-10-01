## Resumo

**Peso: 20%** · Base de tudo: vocabulário de IA, tipos de aprendizado, casos de uso, ciclo de vida de ML e métricas. Pouca AWS "profunda", mas é preciso conhecer os **serviços de IA prontos** e o **SageMaker**.

> [!info] Ideia central
> Saber **o que é** cada conceito, **qual técnica** usar para cada problema e **quais etapas** um projeto de ML percorre.

## Tarefa 1.1 — Conceitos e terminologia básica de IA

**O que a prova espera:**
- Definir os termos básicos: IA, ML, deep learning, redes neurais, visão computacional, NLP, modelo, algoritmo, treino x inferência, viés, justiça (*fairness*), ajuste (*fit*) e LLM.
- Comparar IA, ML e deep learning (o que têm em comum e onde diferem).
- Diferenciar tipos de inferência: **em lote (batch)** x **tempo real**.
- Reconhecer os tipos de dados: rotulados x não rotulados, tabulares, séries temporais, imagem, texto, estruturados x não estruturados.
- Explicar aprendizado **supervisionado, não supervisionado e por reforço**.

**Conceitos para dominar:**

| Conceito | Em uma linha |
|---|---|
| IA ⊃ ML ⊃ Deep Learning ⊃ GenAI | Cada um é um subconjunto do anterior |
| Algoritmo x Modelo | Algoritmo = a "receita"; modelo = o resultado treinado |
| Treino x Inferência | Aprender com dados x usar o modelo para prever |
| Batch x Tempo real | Muitos dados de uma vez, sem pressa x resposta imediata, baixa latência |
| Overfitting / Underfitting | Decorou o treino x não aprendeu o suficiente |
| Viés (*bias*) | Erro sistemático / resultado injusto para certos grupos |

📚 Notas: [[O que é Inteligência Artificial]] · [[O que é  Machine Learn]] · [[O que é  Deep Learn]] · [[Aprendizado Supervisionado]] · [[Aprendizado Não Supervisionado]] · [[Aprendizado por Reforço]] · [[Diferenças entre os Tipos de Aprendizado]]

## Tarefa 1.2 — Casos de uso práticos de IA

**O que a prova espera:**
- Reconhecer onde IA/ML gera valor: apoiar decisões humanas, escalar soluções, automatizar.
- Saber quando IA/ML **não** é adequada: custo-benefício ruim, ou quando é preciso um **resultado exato e determinístico** em vez de uma previsão.
- Escolher a técnica certa: **regressão, classificação, clusterização**.
- Identificar aplicações reais: visão computacional, NLP, reconhecimento de fala, recomendação, detecção de fraude, previsão (*forecasting*).
- Conhecer os serviços gerenciados de IA/ML da AWS (SageMaker, Transcribe, Translate, Comprehend, Lex, Polly…).

**Mapa problema → técnica → serviço:**

| Problema | Técnica | Serviço AWS típico |
|---|---|---|
| Prever um número (preço, demanda) | Regressão | SageMaker |
| Prever uma categoria (spam, fraude) | Classificação | SageMaker, Fraud Detector |
| Agrupar sem rótulos (segmentar clientes) | Clusterização | SageMaker |
| Fala → texto | Reconhecimento de fala | **Transcribe** |
| Texto → fala | Síntese de voz | **Polly** |
| Traduzir | NLP | **Translate** |
| Sentimento, entidades em texto | NLP | **Comprehend** |
| Chatbot por voz/texto | Conversação | **Lex** |
| Imagens e vídeos | Visão computacional | **Rekognition** |
| Extrair texto de documentos | OCR + IA | **Textract** |
| Recomendações | Recomendação | **Personalize** |
| Busca inteligente em documentos | Busca com ML | **Kendra** |

> [!tip] Dica para lembrar
> Se a regra é **fixa e exata** (ex.: calcular imposto), **não use ML** — use programação tradicional.

📚 Notas: [[Comparação Geral e Casos de Uso]] · [[Tipos de Algoritimos de Machine Learn]] · [[07 - Serviços AWS do Exame]]

## Tarefa 1.3 — Ciclo de vida de desenvolvimento de ML

**O que a prova espera:**
- Conhecer as etapas de um pipeline de ML.
- Saber de onde vêm os modelos: **pré-treinados open source** x **treinados sob medida**.
- Saber como colocar em produção: **API gerenciada** x **API auto-hospedada**.
- Associar cada etapa a serviços AWS (SageMaker, Data Wrangler, Feature Store, Model Monitor).
- Entender **MLOps**: experimentação, processos repetíveis, sistemas escaláveis, dívida técnica, prontidão para produção, monitoramento e retreino.
- Avaliar modelos com **métricas técnicas** (acurácia, AUC, F1) e **métricas de negócio** (custo por usuário, custo de desenvolvimento, feedback de clientes, ROI).

**Pipeline de ML e serviços:**

| # | Etapa | Serviço / recurso AWS |
|---|---|---|
| 1 | Coleta de dados | S3, Glue, Data Exchange |
| 2 | Análise exploratória (EDA) | SageMaker Studio / Notebooks, Data Wrangler |
| 3 | Pré-processamento | **SageMaker Data Wrangler**, Glue DataBrew |
| 4 | Engenharia de features | Data Wrangler, **SageMaker Feature Store** |
| 5 | Treinamento | SageMaker Training |
| 6 | Ajuste de hiperparâmetros | SageMaker Automatic Model Tuning |
| 7 | Avaliação | SageMaker (métricas), Clarify |
| 8 | Implantação | SageMaker Endpoints (real-time, serverless, batch, assíncrono) |
| 9 | Monitoramento | **SageMaker Model Monitor**, CloudWatch |

**Métricas:**

| Métrica | Uso |
|---|---|
| Acurácia | % de acertos (cuidado com classes desbalanceadas) |
| Precisão / Recall | Evitar falso positivo / evitar falso negativo |
| F1-score | Equilíbrio entre precisão e recall |
| AUC-ROC | Capacidade de separar classes (quanto mais perto de 1, melhor) |
| MAE / RMSE / R² | Métricas de regressão |
| ROI, custo por usuário | Métricas de **negócio** |

📚 Notas: [[Aprendizado Supervisionado]] (seção de métricas)

## Autoavaliação

- [ ] Sei explicar a diferença entre IA, ML e DL com um exemplo.
- [ ] Sei escolher entre regressão, classificação e clusterização.
- [ ] Sei associar cada serviço de IA pronto ao seu caso de uso.
- [ ] Sei as etapas do pipeline e onde entram Data Wrangler, Feature Store e Model Monitor.
- [ ] Sei o que é MLOps e quando retreinar um modelo.

---
Início: [[00 - Início - Guia do Exame]] · Anterior: [[01 - Visão Geral do Exame]] · Próximo: [[03 - Domínio 2 - Fundamentos de IA Generativa]] · ✅ [[09 - Checklist de Estudo]]
