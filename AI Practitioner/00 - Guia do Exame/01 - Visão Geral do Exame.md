## Resumo

Versão em português, organizada para estudo, do guia oficial **AWS Certified AI Practitioner (AIF-C01)** — versão **1.4** do documento. Esta nota cobre a parte "administrativa": para quem é o exame, o que fica fora do escopo, tipos de questão e como funciona a nota.

> [!info] Ideia central
> O exame testa **conhecimento geral** de IA, ML, IA Generativa e dos serviços AWS relacionados — para quem **usa** essas soluções, não para quem as **programa**.

## Objetivo do exame

A certificação valida que o candidato consegue:

- Entender conceitos, métodos e estratégias de **IA, ML e IA Generativa**, em geral e na AWS.
- Saber **quando faz sentido usar** essas tecnologias e levantar as perguntas certas na sua organização.
- Escolher o **tipo certo de tecnologia** de IA/ML para cada caso de uso.
- Usar IA de forma **responsável**.

## Perfil do candidato

- Cerca de **6 meses de contato** com tecnologias de IA/ML na AWS.
- **Usa** soluções de IA/ML, mas não necessariamente as **constrói**.

### Conhecimento AWS recomendado

| Tema | O que saber |
|---|---|
| Serviços principais | EC2, S3, Lambda, SageMaker e seus casos de uso |
| Modelo de responsabilidade compartilhada | O que é segurança **da** nuvem (AWS) x **na** nuvem (cliente) |
| IAM | Controle de acesso a recursos AWS |
| Infraestrutura global | Regiões, Zonas de Disponibilidade e *edge locations* |
| Preços | Modelos de cobrança dos serviços AWS |

## O que NÃO cai (tarefas fora do escopo)

O candidato **não** precisa saber fazer:

- Programar modelos ou algoritmos de IA/ML.
- Engenharia de dados ou de *features* na prática.
- Ajuste de hiperparâmetros ou otimização de modelos.
- Construir/implantar *pipelines* ou infraestrutura de ML.
- Análises matemáticas/estatísticas de modelos.
- Implementar protocolos de segurança/compliance.
- Criar frameworks e políticas de governança.

> [!tip] Dica para lembrar
> Você precisa **reconhecer e explicar** esses conceitos (ex.: o que é *hyperparameter tuning*), mas **não executá-los**.

## Tipos de questão

| Tipo | Como funciona |
|---|---|
| **Múltipla escolha** | 1 correta, 3 distratores |
| **Múltipla resposta** | 2+ corretas entre 5+ opções — precisa acertar **todas** |
| **Ordenação** | 3 a 5 itens para colocar na **ordem certa** |
| **Associação (*matching*)** | Ligar respostas a 3 a 7 itens — precisa acertar **todos os pares** |
| **Estudo de caso** | Um cenário com 2+ questões; cada questão vale separadamente |

- Questão em branco = **errada**. **Não há penalidade por chutar** → nunca deixe em branco.

## Estrutura e pontuação

| Item | Valor |
|---|---|
| Questões que contam nota | **50** |
| Questões não pontuadas (teste, não identificadas) | **15** |
| Total aproximado | **65** |
| Escala | **100 a 1.000** |
| Nota mínima | **700** |
| Resultado | **Aprovado / Reprovado** |
| Modelo | **Compensatório**: não precisa passar em cada domínio, só no total |

O relatório pode mostrar seu desempenho por domínio, mas é só indicativo de pontos fortes e fracos.

## Domínios e pesos

| Domínio | Tema | Peso |
|---|---|---|
| 1 | [[02 - Domínio 1 - Fundamentos de IA e ML\|Fundamentos de IA e ML]] | **20%** |
| 2 | [[03 - Domínio 2 - Fundamentos de IA Generativa\|Fundamentos de IA Generativa]] | **24%** |
| 3 | [[04 - Domínio 3 - Aplicações de Foundation Models\|Aplicações de Foundation Models]] | **28%** |
| 4 | [[05 - Domínio 4 - Diretrizes para IA Responsável\|Diretrizes para IA Responsável]] | **14%** |
| 5 | [[06 - Domínio 5 - Segurança, Compliance e Governança\|Segurança, Compliance e Governança]] | **14%** |

> [!warning] Atenção
> Os domínios **2 + 3 = 52%** da prova. IA Generativa e Foundation Models são o coração do exame.

---
Início: [[00 - Início - Guia do Exame]] · Próximo: [[02 - Domínio 1 - Fundamentos de IA e ML]]

Fonte: *AWS Certified AI Practitioner (AIF-C01) Exam Guide*, versão 1.4 — conteúdo adaptado e resumido em português.
