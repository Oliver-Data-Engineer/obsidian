## Resumo

O **Amazon Fraud Detector** é um serviço gerenciado para **detectar fraudes online** em tempo real, como cadastro de contas falsas, pagamentos fraudulentos e roubo de contas. Ele usa os **seus dados históricos** de fraude e a experiência de mais de 20 anos da Amazon para treinar modelos, sem exigir experiência em ML.

> [!info] Ideia central
> **Evento (cadastro, compra, login) → pontuação de risco de fraude → ação (aprovar, revisar, bloquear).**
> 🔑 Palavras-chave na prova: "**fraude online**", "**pagamento fraudulento**", "**contas falsas**", "**account takeover**", "**pontuação de risco**".

> [!warning] Status 2026: fechado para novos clientes
> O Fraud Detector **não aceita novos clientes desde 07/11/2025**. Quem já usa continua normalmente. A AWS sugere **Amazon SageMaker / AutoGluon** (ML para fraude) e **AWS WAF Fraud Control** (fraude em criação de contas e login).
> **Na prova** (guia v1.4), ele continua no escopo: "detectar fraude online sem experiência em ML" → **Fraud Detector**.

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Detecção de fraude (ML gerenciado) |
| **Entrada** | Dados históricos rotulados (fraude / legítimo) + eventos em tempo real |
| **Saída** | **Pontuação de risco** (0–1000) e **resultado** definido por regras (aprovar, revisar, bloquear) |
| **Precisa saber ML?** | Não |
| **Customização** | Modelo treinado **com os seus dados** + **regras de negócio** |
| **Modos** | Tempo real (API de previsão) · Lote |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐ |
| **Status 2026** | ⚠️ Sem novos clientes desde 07/11/2025 |

## Principais recursos

| Recurso | O que faz |
|---|---|
| **Online Fraud Insights** | Detecta fraude em **cadastros** e **pagamentos/checkouts** |
| **Transaction Fraud Insights** | Focado em **transações** (usa o histórico de cada cliente) |
| **Account Takeover Insights** | Detecta **roubo de conta** em logins |
| **Regras** | Combinam a pontuação com regras ("se risco > 900 → bloquear") |
| **Detectores** | Juntam modelo + regras + resultados em um ponto de decisão |
| **Explicação** | Mostra **quais variáveis** mais influenciaram a pontuação |

## Casos de uso

| Cenário | Como ajuda |
|---|---|
| **E-commerce** | Bloquear compras com cartão roubado |
| **Cadastro de contas** | Barrar contas falsas e abuso de cupons de boas-vindas |
| **Login** | Detectar invasão de conta |
| **Programas de fidelidade** | Detectar abuso de pontos |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[01 - Amazon SageMaker\|Amazon SageMaker]] | No SageMaker você **constrói** seu modelo de fraude. O Fraud Detector é **pronto** e gerenciado (e é a alternativa recomendada em 2026) |
| **Amazon GuardDuty** | Detecta **ameaças à sua conta AWS** (segurança da infraestrutura), não fraude de clientes. **Fora do escopo** da prova |
| **AWS WAF** | Firewall de aplicação web; o *Fraud Control* usa **regras gerenciadas**, não um modelo treinado com seus dados |

> [!warning] Pegadinhas de prova
> - "Identificar **transações fraudulentas** sem equipe de ML" → **Fraud Detector**.
> - "Detectar **ameaças/invasões na conta AWS**" → não é Fraud Detector (é GuardDuty, fora do escopo).
> - Fraude é um problema de **classificação binária** (fraude/não fraude) → [[04 - Aprendizado Supervisionado|Aprendizado Supervisionado]].

## Exemplo para Associação Mental

**O Segurança do Shopping com Ficha Policial.** Ele conhece o **histórico de golpes** que já aconteceram (dados rotulados) e dá uma **nota de suspeita** para cada cliente que entra. Nota alta → **barra na porta**. Nota média → **chama o gerente** (revisão manual).

## 📝 Meu entendimento

> _Escreva aqui, com suas palavras, o que entendeu sobre o Fraud Detector._

---
Resumo: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · Anterior: [[10 - Amazon Personalize|Amazon Personalize]] · Próximo: [[11 - Amazon Forecast|Amazon Forecast]]

Fontes: [Amazon Fraud Detector](https://aws.amazon.com/frauddetector) · [Fraud Detector: mudança de disponibilidade](https://docs.aws.amazon.com/frauddetector/latest/ug/frauddetector-availability-change.html)
