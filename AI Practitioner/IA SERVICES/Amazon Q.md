## Resumo

O **Amazon Q** é a família de **assistentes de IA generativa prontos** da AWS. Você **não constrói** nada: só usa. Na prova aparecem principalmente dois: o **Amazon Q Business** (assistente que responde com base nos **dados da empresa**) e o **Amazon Q Developer** (assistente de **programação** e de AWS).

> [!info] Ideia central
> **Assistente de GenAI pronto para usar.** Q Business = **funcionários** perguntando sobre a empresa. Q Developer = **desenvolvedores** escrevendo código e operando a AWS.
> 🔑 Palavras-chave na prova: "**assistente pronto**", "**funcionários perguntam sobre documentos internos**", "**gerar código**", "**assistente no IDE**", "**sem construir aplicação**".

> [!warning] Status 2026: Q Business em manutenção
> O **Amazon Q Business** entrou em **manutenção em 30/06/2026** e **não aceita novos clientes desde 30/07/2026**. O sucessor recomendado é o **Amazon Quick** (assistente de trabalho com dados, BI e automação de fluxos). O **Q Developer** continua disponível.
> **Na prova** (guia v1.4), os dois continuam no escopo.

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Assistente de IA generativa (aplicação pronta) |
| **Entrada** | Perguntas e pedidos em linguagem natural |
| **Saída** | Respostas com **citação da fonte**, código, resumos e ações |
| **Precisa saber ML?** | Não |
| **Customização** | Conectar fontes de dados (Q Business), **controles de administrador** e regras de tópicos |
| **Modos** | Chat em tempo real (web, IDE, console, CLI, Slack/Teams) |
| **Na prova** | Domínio 2 · Tarefa 2.3 · ⭐⭐⭐ |
| **Status 2026** | Q Developer ✅ · Q Business ⚠️ manutenção → **Amazon Quick** |

## Principais recursos

### Amazon Q Business ⚠️

| Recurso | O que faz |
|---|---|
| **Conectores** (40+) | S3, SharePoint, Confluence, Salesforce, Gmail, Slack… |
| **Respostas com citações** | Responde **com base nos documentos da empresa** e mostra de onde tirou |
| **Respeita permissões** | Cada funcionário só vê respostas sobre o que **tem acesso** |
| **Controles de administrador** | Bloquear tópicos, restringir respostas só aos dados da empresa (guardrails próprios) |
| **Q Apps** | Funcionários criam **mini-apps de IA** descrevendo-os em linguagem natural |
| **Ações (plugins)** | Executa tarefas: abrir ticket no Jira, criar caso no ServiceNow |

### Amazon Q Developer ✅

| Recurso | O que faz |
|---|---|
| **Geração de código** | Sugestões e funções inteiras no **IDE** (VS Code, JetBrains) e na linha de comando |
| **Agentes de desenvolvimento** | Implementa funcionalidades, escreve **testes** e documentação |
| **Varredura de segurança** | Encontra **vulnerabilidades** no código |
| **Transformação de código** | Moderniza aplicações (ex.: **upgrade de versão do Java**, .NET para Linux) |
| **Ajuda com AWS** | Responde dúvidas sobre serviços, **custos** e erros no **console** |

### Outros "Q" que podem aparecer

| Nome | O que é |
|---|---|
| **Q in QuickSight** (hoje **Quick Sight**) | Perguntas em linguagem natural sobre **dashboards e dados de BI** |
| **Q in Connect** | Ajuda **atendentes de call center** com respostas em tempo real |

## Casos de uso

| Cenário | Qual Q |
|---|---|
| Funcionário pergunta "qual é a política de home office?" | **Q Business** |
| Gerar resumo de documentos internos para a equipe | **Q Business** |
| Desenvolvedor quer gerar código e testes no IDE | **Q Developer** |
| Atualizar uma aplicação Java antiga | **Q Developer** (transformação) |
| Analista pergunta "quanto vendemos por região?" no dashboard | **Q in QuickSight / Quick** |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon Bedrock]] | Bedrock = **construir** sua aplicação de GenAI. Q = assistente **pronto** |
| [[Amazon Kendra]] | O Kendra **busca e devolve trechos** de documentos. O Q Business **conversa e gera respostas** (também em manutenção em 2026) |
| [[Amazon Lex]] | O Lex é um **construtor de chatbots** para os **seus clientes**. O Q é um assistente pronto para **funcionários e desenvolvedores** |
| **PartyRock** | Playground **gratuito** para aprender e criar apps de GenAI. Não é para uso corporativo |

> [!warning] Pegadinhas de prova
> - "Assistente para funcionários consultarem **dados internos**, **sem construir** uma aplicação" → **Q Business**.
> - "Ajudar desenvolvedores a **escrever código**" → **Q Developer**.
> - "Criar uma aplicação de GenAI **personalizada**" → **Bedrock**, não Q.

## Exemplo para Associação Mental

**O Estagiário Brilhante.** O **Q Business** é o estagiário que **leu todos os documentos da empresa** e responde qualquer pergunta, sempre mostrando a fonte e respeitando o que cada um pode saber. O **Q Developer** é o estagiário de TI que **programa ao seu lado**, revisa seu código e conhece a AWS de cor. Você não treina nenhum dos dois: eles **já chegam prontos**.

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, o que entendeu sobre o Amazon Q._

---
Resumo: [[Resumo]] · Anterior: [[Amazon Bedrock]]

Fontes: [Amazon Q](https://aws.amazon.com/pt/q/) · [Q Business: mudança de disponibilidade](https://docs.aws.amazon.com/amazonq/latest/qbusiness-ug/qbusiness-availability-change.html)
