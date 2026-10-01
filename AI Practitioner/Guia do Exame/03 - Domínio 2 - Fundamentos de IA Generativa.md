## Resumo

**Peso: 24%** · Conceitos de IA Generativa (tokens, embeddings, transformers, foundation models), vantagens e limitações, e os serviços AWS para construir aplicações de GenAI.

> [!info] Ideia central
> Entender **como** a GenAI funciona (em alto nível), **quando** ela ajuda ou atrapalha um negócio, e **qual serviço AWS** usar.

## Tarefa 2.1 — Conceitos básicos de IA Generativa

**O que a prova espera:**
- Entender: **tokens, chunking, embeddings, vetores, prompt engineering, LLMs baseados em transformers, foundation models, modelos multimodais e modelos de difusão**.
- Identificar casos de uso: geração de imagem, vídeo e áudio; resumo; chatbots; tradução; geração de código; agentes de atendimento; busca; recomendação.
- Descrever o **ciclo de vida de um foundation model**: seleção de dados → seleção do modelo → pré-treino → fine-tuning → avaliação → implantação → feedback.

| Conceito | Em uma linha |
|---|---|
| **Token** | Pedaço de texto que o modelo processa e pelo qual se cobra |
| **Chunking** | Quebrar documentos em pedaços menores (essencial no RAG) |
| **Embedding** | Representação numérica (vetor) do **significado** de um texto/imagem |
| **Vetor / banco vetorial** | Guarda embeddings e busca por **similaridade** |
| **Transformer** | Arquitetura com mecanismo de **atenção**, base dos LLMs |
| **Foundation Model (FM)** | Modelo grande pré-treinado, adaptável a muitas tarefas |
| **Multimodal** | Entende/gera vários tipos de dado (texto, imagem, áudio) |
| **Modelo de difusão** | Gera imagens partindo de ruído e "limpando" aos poucos |

📚 Notas: [[O que é  Generative IA]] · [[O que é um Prompt]]

## Tarefa 2.2 — Capacidades e limitações da GenAI para negócios

**O que a prova espera:**
- Vantagens: **adaptabilidade, rapidez de resposta, simplicidade**.
- Desvantagens: **alucinações, baixa interpretabilidade, imprecisão, não determinismo**.
- Critérios para escolher um modelo: tipo de modelo, requisitos de desempenho, capacidades, restrições, compliance.
- Métricas de valor de negócio: desempenho entre domínios, eficiência, taxa de conversão, receita média por usuário (ARPU), acurácia, valor do tempo de vida do cliente (CLV).

| ✅ Vantagens | ❌ Limitações |
|---|---|
| Adapta-se a muitas tarefas sem retreino | **Alucina** (inventa com confiança) |
| Respostas rápidas em linguagem natural | Difícil explicar **por que** respondeu algo |
| Fácil de usar (basta um prompt) | **Não determinística**: mesma pergunta, respostas diferentes |
| | Pode ser imprecisa ou desatualizada |

## Tarefa 2.3 — Infraestrutura e tecnologias AWS para GenAI

**O que a prova espera:**
- Conhecer os serviços: **SageMaker JumpStart, Amazon Bedrock, PartyRock (playground do Bedrock), Amazon Q**.
- Vantagens de usar GenAI gerenciada na AWS: acessibilidade, barreira de entrada menor, eficiência, custo-benefício, rapidez para chegar ao mercado, alinhamento com objetivos de negócio.
- Benefícios da infraestrutura AWS: segurança, compliance, responsabilidade, *safety*.
- Trade-offs de custo: capacidade de resposta, disponibilidade, redundância, desempenho, cobertura regional, **preço por token**, **throughput provisionado**, modelos customizados.

| Serviço | Para quê |
|---|---|
| **Amazon Bedrock** | API serverless para vários FMs (Claude, Llama, Nova, Mistral…) + Knowledge Bases, Agents, Guardrails |
| **SageMaker JumpStart** | Hub de modelos pré-treinados para implantar e fazer fine-tuning com mais controle |
| **PartyRock** | Playground gratuito para criar apps de GenAI sem código |
| **Amazon Q** | Assistente pronto: **Q Business** (dados da empresa) e **Q Developer** (código) |

**Modelos de preço do Bedrock:**

| Modelo | Quando usar |
|---|---|
| **On-demand** (por token) | Uso variável/imprevisível — paga o que usar |
| **Batch** | Grandes volumes sem urgência — mais barato |
| **Provisioned Throughput** | Carga constante e alta, ou **obrigatório para modelos customizados** |

> [!tip] Dica para lembrar
> **Bedrock** = "quero usar FMs por API sem gerenciar nada". **JumpStart/SageMaker** = "quero mais controle sobre modelo e infraestrutura".

## Autoavaliação

- [ ] Sei explicar token, embedding, chunking e transformer.
- [ ] Sei citar 3 vantagens e 4 limitações da GenAI.
- [ ] Sei diferenciar Bedrock, JumpStart, PartyRock e Amazon Q.
- [ ] Sei quando usar on-demand x provisioned throughput.

---
Início: [[00 - Início - Guia do Exame]] · Anterior: [[02 - Domínio 1 - Fundamentos de IA e ML]] · Próximo: [[04 - Domínio 3 - Aplicações de Foundation Models]] · ✅ [[09 - Checklist de Estudo]]
