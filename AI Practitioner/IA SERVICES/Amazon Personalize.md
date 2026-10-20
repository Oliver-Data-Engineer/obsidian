## Resumo

O **Amazon Personalize** cria **recomendações personalizadas em tempo real** para cada usuário, usando a mesma tecnologia de ML da **Amazon.com**. Você envia os dados de **interações** (cliques, compras, visualizações), de **itens** e de **usuários**, e ele treina e hospeda o modelo de recomendação, sem exigir experiência em ML.

> [!info] Ideia central
> **Histórico de interações → "quem comprou isto também gostará de…".** É o "vendedor que conhece seu gosto".
> 🔑 Palavras-chave na prova: "**recomendação**", "**personalização**", "**produtos sugeridos**", "**itens similares**", "**ranking personalizado**", "**marketing segmentado**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Recomendação (ML gerenciado) |
| **Entrada** | 3 datasets: **interações** (obrigatório), **itens** e **usuários** + eventos em tempo real |
| **Saída** | Lista de itens recomendados, ranking personalizado ou segmentos de usuários |
| **Precisa saber ML?** | Não. Você escolhe uma **receita** (*recipe*) e ele treina |
| **Customização** | Treina **com os seus dados** (o modelo é seu); filtros e regras de negócio |
| **Modos** | Tempo real (API de campanha) · Lote (*batch recommendations*) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐ |
| **Status 2026** | ✅ Disponível |

## Principais recursos

| Recurso | O que faz | Exemplo |
|---|---|---|
| **Personalização por usuário** | Itens recomendados **para cada pessoa** | "Recomendados para você" |
| **Itens similares** | Itens parecidos com o que o usuário vê | "Quem viu isto também viu…" |
| **Ranking personalizado** | Reordena uma lista para cada usuário | Resultados de busca personalizados |
| **Populares / em alta** | Itens mais populares ou em alta agora | "Em alta hoje" |
| **Segmentação de usuários** | Encontra **usuários com afinidade** por um item | Público de uma campanha de e-mail |
| **Eventos em tempo real** | Atualiza as recomendações conforme o usuário navega | Mudou de interesse no meio da sessão |
| **Filtros** | Aplica regras de negócio | Não recomendar itens fora de estoque |
| **Recomendadores por domínio** | Configurações prontas para **e-commerce** e **vídeo sob demanda** | Começar rápido sem escolher receitas |

## Casos de uso

| Cenário | Como o Personalize ajuda |
|---|---|
| **E-commerce** | Produtos recomendados, "compre junto" |
| **Streaming / mídia** | Filmes, músicas e notícias sugeridos |
| **Marketing** | E-mails e notificações com ofertas personalizadas |
| **Busca** | Resultados reordenados pelo gosto de cada usuário |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon SageMaker]] | No SageMaker você **constrói** seu sistema de recomendação do zero. O Personalize já entrega **pronto e gerenciado** |
| [[Amazon Forecast]] | O Forecast prevê **números no tempo** (demanda). O Personalize sugere **itens para pessoas** |
| [[Amazon Kendra]] | O Kendra **busca** o que o usuário pede. O Personalize **sugere** o que ele nem pediu |

> [!warning] Pegadinhas de prova
> - "Recomendar **produtos** com base no **histórico** do cliente" → **Personalize**.
> - "Sem experiência em ML" + "recomendação" → **Personalize** (não SageMaker).
> - "Prever **quantas unidades** vão vender" → é **previsão** (Forecast/SageMaker Canvas), não recomendação.

## Exemplo para Associação Mental

**O Vendedor da Livraria de Bairro.** Ele lembra **tudo o que você já comprou** e, quando você entra, já separa três livros "que você vai adorar". Se você para na seção de ficção científica (evento em tempo real), ele muda as sugestões na hora. *Personalize* = **personalizar** para cada cliente.

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, o que entendeu sobre o Personalize._

---
Resumo: [[Resumo]] · Anterior: [[Amazon Kendra]] · Próximo: [[Amazon Fraud Detector]]

Fontes: [Amazon Personalize](https://aws.amazon.com/pt/personalize/) · [Recursos do Amazon Personalize](https://aws.amazon.com/pt/personalize/features/)
