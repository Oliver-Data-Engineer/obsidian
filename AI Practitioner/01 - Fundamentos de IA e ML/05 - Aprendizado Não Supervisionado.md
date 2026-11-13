
## Resumo

No Aprendizado Não Supervisionado, o modelo recebe **dados sem rótulo** — ou seja, **ninguém diz qual é a resposta certa**. O objetivo não é prever algo conhecido, mas sim **descobrir estruturas escondidas** nos dados: grupos parecidos, padrões, relações e comportamentos fora do normal.

É muito útil quando temos **muitos dados, mas não sabemos exatamente o que procurar**, ou quando rotular tudo seria caro demais.

> [!info] Ideia central
> **Apenas Entrada (X), sem resposta → o modelo encontra a organização natural dos dados.**

## Principais Tarefas

### 1. Clusterização (Agrupamento)
Junta itens **parecidos entre si** em grupos (*clusters*), sem saber de antemão quais grupos existem.
- **Segmentação de clientes:** "clientes que compram à noite e gastam pouco", "clientes premium de fim de semana"...
- Agrupar notícias por assunto automaticamente.

### 2. Detecção de Anomalias
Identifica o que **foge do padrão** normal.
- Uma transação de cartão às 3h da manhã em outro país.
- Um sensor de máquina industrial com leitura estranha (manutenção preditiva).
- Tráfego de rede suspeito (segurança).

### 3. Regras de Associação
Descobre itens que **costumam aparecer juntos**.
- Análise de "cesta de compras": quem compra **pão** frequentemente compra **manteiga**.
- "Quem comprou este produto também comprou..."

### 4. Redução de Dimensionalidade
Resume dados com **muitas colunas** em poucas, mantendo o essencial.
- Simplificar um dataset com 500 variáveis para 10 antes de treinar outro modelo.
- Visualizar dados complexos em gráficos 2D/3D.

## Algoritmos Mais Comuns

| Algoritmo | Tarefa | Uso típico |
|---|---|---|
| **K-Means** | Clusterização | Segmentação de clientes (você define quantos grupos, o "K") |
| **DBSCAN** | Clusterização | Grupos de formatos irregulares, identifica ruído |
| **Clusterização Hierárquica** | Clusterização | Monta uma "árvore" de grupos e subgrupos |
| **Isolation Forest / Random Cut Forest** | Detecção de anomalias | Fraudes, falhas, outliers |
| **Apriori** | Regras de associação | Cesta de compras, recomendação simples |
| **PCA (Análise de Componentes Principais)** | Redução de dimensionalidade | Comprimir variáveis mantendo a informação |
| **Autoencoders** | Redução / Anomalias | Redes neurais que aprendem a "comprimir e reconstruir" os dados |

## Como se Avalia

Como **não existe resposta certa**, a avaliação é mais difícil e muitas vezes **subjetiva**:
- Métricas internas como **Silhouette Score** (quão bem separados estão os grupos) e o **método do cotovelo** (*elbow*) para escolher o número de clusters.
- Na prática, é comum um **especialista de negócio** analisar se os grupos encontrados fazem sentido.

## Vantagens e Desvantagens

| ✅ Vantagens | ❌ Desvantagens |
|---|---|
| **Não precisa rotular** dados (mais barato) | Resultados mais difíceis de **avaliar e interpretar** |
| Descobre padrões que **ninguém tinha pensado** | Os grupos encontrados podem não ter significado de negócio |
| Ótimo para **explorar** dados novos | Menos preciso para tarefas de previsão específicas |
| Base para outras técnicas (pré-processamento, anomalias) | Sensível à escolha de parâmetros (ex.: o K do K-Means) |

## Exemplo para Associação Mental

**A Gaveta de Meias Bagunçada** Imagine que você despeja no chão uma gaveta com 200 meias misturadas e **ninguém te diz como organizá-las**.

- Naturalmente, você começa a separar: meias **pretas** de um lado, **brancas** de outro, **esportivas** num canto, **de lã** em outro.
- Ninguém te deu as categorias — **você descobriu os grupos sozinho** olhando as semelhanças.
- E aquela meia de Natal com pisca-pisca? Ela não se encaixa em lugar nenhum: é uma **anomalia**. 🎄

No dia a dia, é o Aprendizado Não Supervisionado que ajuda o **Spotify a agrupar músicas com "vibe" parecida**, o **supermercado a decidir colocar a cerveja perto do salgadinho** e o **banco a perceber uma compra estranha** no seu cartão, mesmo que aquele golpe específico nunca tenha acontecido antes.

## Na AWS (AI Practitioner)

- **Amazon SageMaker** possui algoritmos built-in como **K-Means**, **PCA**, **Random Cut Forest** (anomalias) e **IP Insights**.
- **Amazon Lookout for Metrics / Equipment** e o **Random Cut Forest** do **Kinesis Data Analytics** usam detecção de anomalias.

---
Relacionados: [[04 - Aprendizado Supervisionado|Aprendizado Supervisionado]] · [[06 - Aprendizado por Reforço|Aprendizado por Reforço]] · [[07 - Diferenças entre os Tipos de Aprendizado|Diferenças entre os Tipos de Aprendizado]]
