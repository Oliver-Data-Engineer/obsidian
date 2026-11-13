
## Resumo

O Aprendizado Supervisionado é o tipo mais comum de [[02 - O que é Machine Learning|Machine Learning]]. Nele, o modelo é treinado com **dados rotulados**: cada exemplo de entrada vem acompanhado da **resposta correta** (o "rótulo" ou *label*). O algoritmo compara as previsões dele com as respostas certas, mede o erro e vai se ajustando até errar cada vez menos.

Depois de treinado, o modelo recebe dados **novos, sem rótulo**, e consegue prever a resposta sozinho.

> [!info] Ideia central
> **Entrada (X) + Resposta correta (y) → o modelo aprende a função que leva X até y.**

## Os Dois Grandes Tipos de Problema

### 1. Classificação — prever uma **categoria**
A resposta é um rótulo dentro de um conjunto fechado de opções.

- **Binária:** duas classes → "Spam" ou "Não Spam", "Fraude" ou "Legítima".
- **Multiclasse:** várias classes → identificar se a foto é de "gato", "cachorro" ou "pássaro".
- **Multirrótulo:** mais de um rótulo ao mesmo tempo → um filme ser "Ação" **e** "Comédia".

### 2. Regressão — prever um **número contínuo**
A resposta é um valor numérico.

- Prever o **preço de um imóvel** a partir da área, bairro e número de quartos.
- Prever a **demanda de vendas** do próximo mês.
- Estimar a **temperatura** de amanhã.

> [!tip] Dica para lembrar
> **Classificação** responde "**qual?**" (categoria). **Regressão** responde "**quanto?**" (número).

## Algoritmos Mais Comuns

| Algoritmo | Tipo | Uso típico |
|---|---|---|
| **Regressão Linear** | Regressão | Prever preços, vendas, valores contínuos |
| **Regressão Logística** | Classificação | Sim/Não, churn, aprovação de crédito |
| **Árvore de Decisão** | Ambos | Regras fáceis de explicar ("se renda > X, então...") |
| **Random Forest** | Ambos | Várias árvores votando juntas → mais precisão |
| **XGBoost / Gradient Boosting** | Ambos | Dados tabulares, muito usado em competições |
| **SVM (Support Vector Machine)** | Principalmente classificação | Separar classes com uma "fronteira" ótima |
| **k-NN (k-Vizinhos Mais Próximos)** | Ambos | Classifica pelo que os vizinhos mais parecidos são |
| **Redes Neurais** | Ambos | Imagens, texto, áudio (ver [[09 - O que é Deep Learning\|Deep Learning]]) |

## Como se Avalia um Modelo Supervisionado

Como existe a resposta certa, é possível **medir objetivamente** o quanto o modelo acerta:

- **Classificação:** Acurácia, Precisão, Recall (Sensibilidade), F1-Score, Matriz de Confusão, AUC-ROC.
- **Regressão:** MAE (erro absoluto médio), MSE / RMSE (erro quadrático), R².

Os dados normalmente são divididos em **treino**, **validação** e **teste**, para verificar se o modelo generaliza bem e não apenas "decorou" os exemplos (**overfitting**).

| Conjunto | Para que serve | Quando é usado | Obrigatório? |
|---|---|---|---|
| **Treino** (~70–80%) | O modelo **aprende** os padrões (ajusta os pesos) | Durante o treino | ✅ Sim |
| **Validação** (~10–15%) | **Ajustar hiperparâmetros** e escolher entre modelos; detectar overfitting cedo | Durante o desenvolvimento | ❌ **Opcional** (pode ser substituído por validação cruzada) |
| **Teste** (~10–15%) | Medir **o quão bem o modelo generaliza** para dados nunca vistos | **Só no final**, uma vez | ✅ Sim |

> [!warning] Pegadinha (questão #15 do Simulado 2)
> - **Teste** → mede a **generalização** (nota final). **Nunca** use o teste para ajustar hiperparâmetros: isso "vaza" o gabarito.
> - **Validação** → ajusta **hiperparâmetros**. É **opcional**.
> - Analogia: **treino** = estudar com a apostila · **validação** = simulados para ajustar o método de estudo · **teste** = a prova oficial.

## Vantagens e Desvantagens

| ✅ Vantagens | ❌ Desvantagens |
|---|---|
| Resultados precisos e mensuráveis | Precisa de **muitos dados rotulados** |
| Objetivo claro (sabemos o que prever) | Rotular dados é **caro e demorado** (muitas vezes manual) |
| Fácil de avaliar e comparar modelos | Não descobre padrões "novos" além do que foi rotulado |
| Muitos algoritmos maduros e conhecidos | Rótulos errados ou enviesados geram um modelo enviesado |

## Exemplo para Associação Mental

**O Aluno com o Gabarito** Imagine um estudante se preparando para o vestibular com uma apostila de exercícios **que tem o gabarito no final**.

- Ele resolve a questão, confere a resposta no gabarito e, se errou, entende onde errou e ajusta o raciocínio.
- Depois de centenas de exercícios, ele chega na prova (dados novos, **sem gabarito**) e consegue acertar sozinho.

O **gabarito é o rótulo**, e o **professor que preparou o gabarito é a "supervisão"**.

No dia a dia, é o Aprendizado Supervisionado que faz o **filtro de spam** do e-mail funcionar (aprendeu com milhões de e-mails que usuários marcaram como "spam"), o **banco aprovar ou negar crédito** (aprendeu com o histórico de quem pagou e quem não pagou) e o **app de imóveis estimar o preço** de um apartamento.

## Na AWS (AI Practitioner)

- **Amazon SageMaker** possui algoritmos prontos (*built-in*) como **XGBoost**, **Linear Learner**, **k-NN** e **Image Classification**.
- **Amazon SageMaker Ground Truth** é o serviço usado para **rotular dados** (com humanos e/ou ajuda de ML) — justamente o gargalo do aprendizado supervisionado.
- **Amazon Rekognition**, **Amazon Comprehend** e **Amazon Fraud Detector** são serviços prontos que usam modelos supervisionados por baixo dos panos.

---
Relacionados: [[05 - Aprendizado Não Supervisionado|Aprendizado Não Supervisionado]] · [[06 - Aprendizado por Reforço|Aprendizado por Reforço]] · [[07 - Diferenças entre os Tipos de Aprendizado|Diferenças entre os Tipos de Aprendizado]]
