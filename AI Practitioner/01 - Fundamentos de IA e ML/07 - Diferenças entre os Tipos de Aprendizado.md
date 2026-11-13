
## Resumo

Os algoritmos de [[02 - O que é Machine Learning|Machine Learning]] são divididos principalmente pela **forma como aprendem**, ou seja, pelo **tipo de "sinal"** que recebem durante o treinamento:

1. **[[04 - Aprendizado Supervisionado|Aprendizado Supervisionado]]** → aprende com **exemplos + respostas corretas** (dados rotulados).
2. **[[05 - Aprendizado Não Supervisionado|Aprendizado Não Supervisionado]]** → aprende **só com os dados**, sem respostas, descobrindo padrões sozinho.
3. **[[06 - Aprendizado por Reforço|Aprendizado por Reforço]]** → aprende **interagindo com um ambiente**, recebendo **recompensas e punições**.

> [!tip] Pergunta-chave para identificar o tipo
> - Tenho a **resposta certa** para cada exemplo? → **Supervisionado**
> - Tenho dados, mas **não sei as respostas** e quero **descobrir grupos/padrões**? → **Não Supervisionado**
> - Preciso que um agente **tome decisões em sequência** e aprenda com **recompensa**? → **Reforço**

## Tabela Comparativa Direta

| Critério | Supervisionado | Não Supervisionado | Por Reforço |
|---|---|---|---|
| **Tipo de dado** | Rotulado (X + y) | Não rotulado (só X) | Sem dataset fixo — gerado pela interação |
| **Sinal de aprendizado** | Resposta correta (gabarito) | Nenhum — similaridade entre os dados | Recompensa / penalidade |
| **Objetivo** | **Prever** um rótulo ou valor | **Descobrir** estrutura escondida | **Decidir** a melhor ação ao longo do tempo |
| **Pergunta que responde** | "Qual é?" / "Quanto é?" | "Como esses dados se organizam?" | "O que devo fazer agora?" |
| **Tarefas típicas** | Classificação, Regressão | Clusterização, Anomalias, Associação, Redução de dimensionalidade | Controle, jogos, robótica, otimização de decisões |
| **Algoritmos** | Regressão Linear/Logística, Árvores, Random Forest, XGBoost, SVM | K-Means, DBSCAN, PCA, Apriori, Random Cut Forest | Q-Learning, DQN, PPO, RLHF |
| **Feedback** | Direto e imediato (certo/errado) | Não há feedback | Atrasado (a recompensa pode vir só no fim) |
| **Avaliação** | Fácil e objetiva (acurácia, F1, RMSE) | Difícil, muitas vezes subjetiva | Recompensa acumulada |
| **Maior custo** | Rotular os dados | Interpretar os resultados | Tempo de treinamento / simulação |
| **Analogia** | 📘 Aluno com gabarito | 🧦 Organizar a gaveta de meias | 🐶 Adestrar um cachorro com petiscos |
| **Exemplo real** | Filtro de spam, preço de imóvel | Segmentação de clientes, fraude nova | AlphaGo, DeepRacer, RLHF em LLMs |
| **Na AWS** | SageMaker XGBoost, Linear Learner, Ground Truth | SageMaker K-Means, PCA, Random Cut Forest | AWS DeepRacer, SageMaker RL |

## Mesmo Problema, Três Abordagens: Cenário "Loja Online"

Para fixar a diferença, veja como uma loja online usaria cada tipo:

- **Supervisionado:** Com o histórico de clientes que **cancelaram** ou **não cancelaram** a assinatura (rótulo), o modelo aprende a **prever quem vai cancelar** no próximo mês (*churn*).
- **Não Supervisionado:** Sem rótulo nenhum, o modelo analisa o comportamento de compra e **descobre 5 perfis de clientes** (ex.: "caçadores de promoção", "compradores de fim de mês"), que o marketing nem sabia que existiam.
- **Por Reforço:** Um agente testa **qual oferta mostrar** para cada cliente em cada momento. Se o cliente compra, ele ganha **recompensa**; com o tempo, aprende a **estratégia de ofertas** que maximiza as vendas.

## Tipos "Intermediários" (bom saber para a prova)

- **Semi-supervisionado:** usa **poucos dados rotulados + muitos não rotulados**. Ex.: rotular 100 fotos manualmente e deixar o modelo aprender com outras 100.000 sem rótulo.
- **Auto-supervisionado (*self-supervised*):** o próprio dado gera o rótulo. Ex.: esconder uma palavra da frase e pedir para o modelo adivinhar. É assim que os **LLMs / Foundation Models** da [[10 - O que é IA Generativa|IA Generativa]] são pré-treinados.
- **RLHF:** combina modelos pré-treinados com **Aprendizado por Reforço a partir de feedback humano** para ajustar o comportamento de LLMs.

## Exemplo para Associação Mental

**Três formas de aprender a cozinhar** 👨‍🍳

- **Supervisionado:** Você segue uma **receita com foto do prato pronto**. Compara o seu resultado com a foto e corrige.
- **Não Supervisionado:** Você abre a despensa e, sem receita, **organiza os ingredientes** por grupos: temperos, massas, doces, enlatados... descobrindo a estrutura sozinho.
- **Por Reforço:** Você cozinha para a família todo dia **sem receita**. Quando elogiam, você repete (recompensa); quando torcem o nariz, muda (penalidade). Com o tempo, vira um chef.

---
Canvas visual: [[03 - Tipos de Aprendizado de Machine Learning.canvas|Tipos de Aprendizado de Machine Learning]]
Índice: [[08 - Tipos de Algoritmos de Machine Learning|Tipos de Algoritmos de Machine Learning]]
