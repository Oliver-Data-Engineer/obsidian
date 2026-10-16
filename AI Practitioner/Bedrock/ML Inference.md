## Resumo

**Inferência** é usar um modelo **já treinado** para gerar uma previsão ou resposta a partir de uma entrada nova. Nesta nota: os **tipos de inferência**, como o **Bedrock cobra** por ela e as opções equivalentes no **SageMaker**. A prova cobra muito a escolha entre **custo** e **latência**.

> [!info] Ideia central
> **Treino** = o modelo aprende (caro, de vez em quando). **Inferência** = o modelo responde (barato por chamada, acontece o tempo todo).
> Precisa de resposta **na hora** → tempo real. Muito volume **sem pressa** → batch (mais barato).

## Tempo real x Batch

| | Tempo real (*real-time / on-demand*) | Lote (*batch*) |
|---|---|---|
| Resposta | Em **milissegundos/segundos** | Minutos a horas |
| Entrada | Uma requisição por vez | Arquivo com **muitas** requisições (no S3) |
| Custo | Maior por requisição | **Menor** (no Bedrock, cerca de 50% mais barato que on-demand) |
| Exemplo | Chatbot, assistente | Resumir 1 milhão de avaliações durante a noite |

## Como o Bedrock cobra a inferência

| Opção | Como funciona | Quando usar |
|---|---|---|
| **On-demand** | Paga por **token** (entrada + saída), sem compromisso | Uso **variável**, protótipos, POCs |
| **Batch** | Envia um lote via S3 e recebe depois, com **desconto** | Grandes volumes **sem urgência** |
| **Provisioned Throughput** | Reserva **model units** por hora (compromisso de 1 ou 6 meses, ou sem compromisso) | Carga **alta e constante**; **obrigatório para modelos customizados** |

**Tiers de serviço** (on-demand):

| Tier | Ideia | Preço |
|---|---|---|
| **Standard** | Padrão | Base |
| **Priority** | Prioridade de processamento para cargas críticas | Mais caro |
| **Flex** | Aceita esperar mais, para cargas não urgentes | Mais barato |

> [!tip] Como o preço por token funciona
> - **Tokens de saída costumam custar mais** que os de entrada.
> - Prompts longos (muito contexto, muitos exemplos) = **mais tokens = mais caro**.
> - Para economizar: modelo **menor**, prompt **mais curto**, **batch**, **cache de prompt**, **destilação**.

## Recursos para otimizar inferência no Bedrock

| Recurso | O que faz |
|---|---|
| **Cross-region inference** (*inference profiles*) | Distribui as requisições entre **várias regiões** para ter mais capacidade e disponibilidade |
| **Prompt caching** | Reaproveita partes repetidas do prompt (ex.: um documento grande) → **menos custo e latência** |
| **Intelligent prompt routing** | Envia cada pedido ao modelo **mais barato** da família que mantém a qualidade |
| **Model distillation** | Cria um modelo menor e mais barato para inferência → [[Fondation Model]] |

## Inferência no SageMaker AI (para modelos próprios)

| Opção | Características | Caso de uso |
|---|---|---|
| **Real-time endpoint** | Instância **sempre ligada**, baixa latência | Tráfego constante que precisa de resposta imediata |
| **Serverless inference** | Escala **até zero**, paga por uso, pode ter *cold start* | Tráfego **intermitente** e imprevisível |
| **Asynchronous inference** | Fila; entradas **grandes** (até 1 GB) e processamento **longo** (até 1h) | Arquivos grandes, perto de tempo real |
| **Batch transform** | Processa um **dataset inteiro** do S3, sem endpoint | Previsões em massa, offline |

> [!warning] Pegadinhas
> - "**Menor custo** e não precisa ser imediato" → **batch**.
> - "Tráfego **imprevisível**, com períodos sem uso" → **serverless** (SageMaker) ou **on-demand** (Bedrock).
> - "Usar um **modelo customizado** no Bedrock" → **Provisioned Throughput**.
> - "Arquivos **grandes** com processamento **demorado**" → **asynchronous inference**.

## Inferência na borda (*edge*)

Rodar o modelo **no próprio dispositivo** (celular, câmera, fábrica) quando há **pouca conectividade** ou é preciso **latência mínima**. Usa modelos **menores** (SLMs). Na nuvem é possível usar modelos maiores, mas há latência de rede.

## Exemplo para Associação Mental

**A Padaria.** **On-demand** é comprar pão avulso: paga cada um, quando quiser. **Batch** é encomendar 500 pães para amanhã: sai mais barato, mas não é na hora. **Provisioned Throughput** é **alugar o forno** por mês: compensa se você assa o tempo todo, e é o único jeito de assar a **sua receita própria** (modelo customizado).

---
Índice: [[Índice - Bedrock]] · Anterior: [[Fondation Model]] · Próximo: [[Beadrock Rag - Kb]]

Fontes: [Amazon Bedrock Pricing](https://aws.amazon.com/bedrock/pricing/) · [SageMaker AI – Deploy models for inference](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html)
