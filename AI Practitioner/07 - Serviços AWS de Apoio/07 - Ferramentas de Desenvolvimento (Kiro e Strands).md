## Resumo

A categoria **Developer Tools** entrou na lista oficial com **dois itens novos de IA**: **Kiro** e **Strands Agents**. Os dois são sobre **construir software e agentes com IA**.

> [!info] Ideia central
> - **Kiro** = **IDE (e CLI) com agentes de IA** para **escrever software** a partir de **especificações** (*spec-driven development*). Sucessor do **Amazon Q Developer CLI**.
> - **Strands Agents** = **SDK open source** para **programar seus próprios agentes de IA** em poucas linhas, com ferramentas e **MCP**. Os agentes podem rodar no **Bedrock AgentCore**.

| | **Kiro** | **Strands Agents** |
|---|---|---|
| O que é | Ambiente de desenvolvimento **agêntico** (IDE + **Kiro CLI**) | **SDK** (biblioteca) Python/TypeScript, licença **Apache 2.0** |
| Para quem | Desenvolvedor que quer **ajuda da IA para programar** | Desenvolvedor que quer **criar um agente** para a sua aplicação |
| Resultado | **Código** da sua aplicação (requisitos → design → tarefas → código) | Um **agente** (modelo + prompt + ferramentas) rodando na sua app |
| Palavra-chave | "**IDE**", "**spec-driven**", "**gerar código a partir de requisitos**", "**hooks**" | "**SDK open source**", "**construir agentes**", "**model-driven**", "**MCP**", "**multiagente**" |
| Relação com outros | Substitui o **Q Developer CLI**; usa FMs como Claude | Usado internamente pelo Kiro, Amazon Q e Glue; deploy no **AgentCore**, Lambda, EKS... |

---

## Kiro

- Lançado pela AWS em **2025**. Funciona como **IDE** e como **Kiro CLI** (terminal).
- **Spec-driven development**: o prompt vira **3 documentos** (requisitos, design e lista de tarefas) que os agentes implementam. Mais **estrutura e rastreabilidade** que o "vibe coding".
- **Steering files**: regras do projeto que orientam os agentes (padrões, tecnologias).
- **Agent hooks**: automações disparadas por eventos (ex.: ao salvar um arquivo, gerar testes ou atualizar a documentação).
- Integra ferramentas via **MCP**.
- O **Amazon Q Developer CLI** foi integrado ao **Kiro CLI**: novidades saem só no Kiro → [[16 - Amazon Q|Amazon Q]].

> [!tip] Na prova
> "Ferramenta da AWS para **desenvolvedores** gerarem e manterem código com **agentes**, a partir de **especificações**" → **Kiro**.
> "Assistente de código no IDE para **explicar, gerar, testar e atualizar código** e tirar dúvidas da AWS" → **Amazon Q Developer** (questões antigas) / **Kiro** (lista nova).

## Strands Agents

- SDK **open source** lançado pela AWS em **maio de 2025**, abordagem **model-driven**: em vez de programar cada passo do fluxo, você dá ao modelo um **prompt** e **ferramentas** e ele **planeja** sozinho o que chamar.
- Um agente = **modelo** (Bedrock ou outros provedores) + **system prompt** + **ferramentas** (funções Python, servidores **MCP**).
- Suporta **multiagentes** (agentes que chamam agentes, padrão **A2A**) e observabilidade.
- Roda **em qualquer lugar**; na AWS, normalmente no **Amazon Bedrock AgentCore** → [[06 - Bedrock Agents#Novidade de 2026: Bedrock AgentCore]].

> [!tip] Na prova
> | Cenário | Resposta |
> |---|---|
> | "**Framework/SDK open source** para escrever o código de um agente" | **Strands Agents** |
> | "**Serviço gerenciado** para **implantar e operar** agentes em produção (runtime, memória, identidade, gateway de ferramentas)" | **Bedrock AgentCore** |
> | "Criar um agente **no console**, sem código, com action groups e Knowledge Base" | **Bedrock Agents** (Classic) |

---

## Exemplo para Associação Mental

**A construtora.** O **Kiro** é o **engenheiro com uma equipe de robôs**: você entrega o pedido, ele escreve a **planta** (spec), divide em **tarefas** e os robôs constroem a casa (código). O **Strands** é o **kit de peças** para você montar o **seu próprio robô** (agente). O **AgentCore** é a **garagem gerenciada** onde os robôs ficam ligados, com memória e crachá de acesso.

---
Voltar: [[07 - Serviços AWS do Exame]] · Relacionadas: [[06 - Bedrock Agents|Bedrock Agents]] · [[16 - Amazon Q|Amazon Q]] · [[07 - Prompt na AWS|Prompt na AWS]]

Fontes: [AIF-C01 – In-scope services](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/aif-01-in-scope-services.html) · [Kiro](https://kiro.dev/about/) · [Kiro: migrating from Q Developer CLI](https://kiro.dev/docs/cli/migrating-from-q/) · [Introducing Strands Agents](https://aws.amazon.com/blogs/opensource/introducing-strands-agents-an-open-source-ai-agents-sdk/) · [Strands Agents – AWS Prescriptive Guidance](https://docs.aws.amazon.com/prescriptive-guidance/latest/agentic-ai-frameworks/strands-agents.html)
