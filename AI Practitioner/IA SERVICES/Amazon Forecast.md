## Resumo

O **Amazon Forecast** é um serviço de **previsão de séries temporais** com machine learning, feito para métricas de negócio: demanda de produtos, estoque, equipe necessária, tráfego. Ele usa dados históricos e fatores relacionados (preço, promoções, feriados) para **prever o futuro** com níveis de probabilidade.

> [!info] Ideia central
> **Histórico no tempo → previsão do futuro (com faixa de probabilidade).**
> 🔑 Palavras-chave: "**previsão de demanda**", "**série temporal**", "**planejamento de estoque**", "**prever vendas**".

> [!warning] Status: fora da lista da prova e fechado para novos clientes
> - O Forecast **não aparece** na lista de serviços dentro do escopo do guia **AIF-C01 v1.4** → [[07 - Serviços AWS do Exame]].
> - **Não aceita novos clientes desde 29/07/2024**. A AWS recomenda o **Amazon SageMaker Canvas** (previsão de séries temporais sem código) → [[Amazon SageMaker]].
> - Vale estudar o **conceito**: "prever valores ao longo do tempo" é **regressão em série temporal** → [[Aprendizado Supervisionado]].

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Previsão (séries temporais) |
| **Entrada** | Série temporal alvo (ex.: vendas por dia) + séries relacionadas (preço, promoções) + metadados dos itens |
| **Saída** | Previsões **probabilísticas** (quantis P10, P50, P90) |
| **Precisa saber ML?** | Não. **AutoML** escolhe o melhor algoritmo |
| **Customização** | Treina com os **seus dados**; análise *what-if* |
| **Modos** | Lote (gera previsões) + consulta por API |
| **Na prova** | Fora da lista oficial · ⭐ conceito |
| **Status** | ⚠️ Sem novos clientes desde 29/07/2024 → SageMaker Canvas |

## Principais recursos

| Recurso | O que faz |
|---|---|
| **AutoPredictor (AutoML)** | Testa vários algoritmos e escolhe/combina os melhores |
| **Previsões probabilísticas** | Dá uma **faixa**: P10 (cenário baixo), P50 (mais provável), P90 (cenário alto) |
| **Séries relacionadas** | Considera preço, promoções, clima e **feriados** |
| **Análise *what-if*** | "E se eu der 10% de desconto?" |
| **Explicabilidade** | Mostra quais fatores mais influenciaram a previsão |

## Casos de uso

| Cenário | Como o Forecast ajuda |
|---|---|
| **Varejo e estoque** | Reduz desperdício, aumenta o giro e melhora a disponibilidade prevendo a demanda dos produtos em **níveis de probabilidade** específicos |
| **Planejamento da força de trabalho** | Prevê quantas pessoas são necessárias em **intervalos de 15 minutos** para os períodos de alta e baixa demanda |
| **Demanda de viagens** | Prevê tráfego de pedestres, número de visitantes e demanda por canal, para controlar custos operacionais |
| **Finanças e energia** | Receita, consumo de energia, uso de capacidade de servidores |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon SageMaker]] Canvas | **Sucessor recomendado**: previsão de séries temporais sem código |
| [[Amazon Personalize]] | O Personalize **recomenda itens** para pessoas. O Forecast **prevê números** no tempo |
| **Amazon QuickSight** | Faz dashboards e previsões simples em gráficos. Não é um serviço de ML de previsão |

> [!warning] Pegadinhas de prova
> - Em questões novas, "**prever demanda sem experiência em ML**" tende a apontar para **SageMaker Canvas**.
> - Previsão de valor **numérico** = **regressão**. Previsão **ao longo do tempo** = **série temporal**.

## Exemplo para Associação Mental

**A Meteorologista dos Negócios.** Assim como a previsão do tempo diz "**70% de chance** de chuva amanhã", o Forecast diz "amanhã venderemos **entre 80 e 120 unidades**, provavelmente 100". Ela olha o **histórico**, o **calendário de feriados** e as **promoções** antes de prever.

## 📝 Meu entendimento

> Forecast (Previsão) - Prever um resultado baseado em dados, Utilizando Machine Learn

---
Resumo: [[Resumo]] · Anterior: [[Amazon Fraud Detector]] · Próximo: [[Amazon Augmented AI]]

Fontes: [Recursos do Amazon Forecast](https://aws.amazon.com/pt/forecast/features/) · [Migrar do Forecast para o SageMaker Canvas](https://aws.amazon.com/blogs/machine-learning/transition-your-amazon-forecast-usage-to-amazon-sagemaker-canvas)
