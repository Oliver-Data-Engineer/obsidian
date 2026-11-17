## Resumo

Análise da **Tentativa 1 do Simulado 5** (Udemy · *[Simulados] AWS Certified AI Practitioner AIF-C01 PT-BR*), feita em 2026-11-16.

> [!success] Placar: **60 / 65 (92%)**: aprovado com folga ✅
> Subiu **22 pontos** em relação ao Simulado 4 (70%). É a **melhor nota** até agora e passa da meta de 80%.
> 🏷️ **15 marcadas para revisão**: acertou **13** e errou **2** (#14 e #63). A sua dúvida virou acerto em 87% dos casos. No S4 foram só 40%.
> 🎯 **3 erros sem marcação** (#17, #20, #33): você respondeu com segurança e errou. Revise esses primeiro.

## Evolução por domínio

| Domínio                               | Peso    | S1  | S2  | S3  | S4  | **S5**           | Tendência                         |
| ------------------------------------- | ------- | --- | --- | --- | --- | ---------------- | --------------------------------- |
| 2. Fundamentos de IA Generativa       | 24%     | 94% | 81% | 94% | 88% | **100%** (16/16) | 🚀 +12                            |
| 5. Segurança, Compliance e Governança | 14%     | 44% | 89% | 89% | 44% | **100%** (9/9)   | 🚀 **+56**: o plano funcionou     |
| 1. Fundamentos de IA e ML             | 20%     | 54% | 77% | 77% | 69% | **92%** (12/13)  | ⬆️ +23                            |
| 3. Aplicações de Foundation Models    | **28%** | 67% | 72% | 89% | 83% | **89%** (16/18)  | ⬆️ +6                             |
| 4. IA Responsável                     | 14%     | 67% | 67% | 78% | 44% | **78%** (7/9)    | ⬆️ +34, mas **ainda o mais fraco** |

> [!warning] O que os cinco simulados mostram juntos
> 1. **IA Responsável** é o domínio mais fraco em **4 dos 5 simulados**. Neste, os 2 erros foram de **tipos de viés** (#17) e de **qual princípio foi violado** (#63).
> 2. **Viés**: é o **5º simulado seguido** com erro nesse tema. Antes o erro era viés x variância. Agora é saber **de onde vem o viés** (humano x dados) e **qual princípio ele fere**.
> 3. **Avaliação de modelos** (#33): a ideia "ROUGE para resumo" está certa, mas a questão pediu **qualidade** do resumo, e aí a resposta é **avaliação humana**. Leia o que a pergunta mede.
> 4. **RAG x fine-tuning** (#20): o par que mais confunde em Aplicações de FMs. **Só o fine-tuning muda os pesos** do modelo.
> 5. ✅ **Governança de dados** (residência x registro), que derrubou o D5 no S4, agora está certa (#50).

## ❌ As 5 questões erradas

| Questão | Domínio | Marcada? | Você marcou | Correto | Regra para fixar |
|---|---|---|---|---|---|
| #14 Personalize precisa **acompanhar mudanças** de compra por temporada e **novas linhas** de produto (2 respostas) | D1 | 🏷️ sim | Exploration weight ✅ + **transformação de recursos** ❌ | **Rastreamento de eventos em tempo real** + exploration weight | "Acompanhar mudanças" = mandar **eventos novos** (PutEvents). "Itens novos" = **exploration weight** |
| #17 Exemplo de **viés humano**, diferente de outros vieses | D4 | não | Modelo treinado com **histórico** de contratação favorece homens | Cientista escolhe atributos pelas **crenças pessoais** dele | Histórico nos dados = viés **algorítmico/histórico**. Viés **humano** = uma **pessoa decide** com base no julgamento dela |
| #20 Como o Bedrock faz **fine-tuning** | D3 | não | Adicionar **Knowledge Base** e buscar contexto na consulta | Dataset **rotulado** (prompt → resposta) que **ajusta os pesos** | Knowledge Base = **RAG**: não muda o modelo. Fine-tuning = **muda os pesos** |
| #33 Melhor forma de avaliar a **qualidade** de resumos antes da implantação | D3 | não | ROUGE / BLEU | **Avaliação humana** | ROUGE mede **sobreposição de palavras**, não coerência nem legibilidade. "Qualidade" subjetiva → **humanos** |
| #63 Modelo de saúde **subestima risco** de grupos **sub-representados** (2 respostas) | D4 | 🏷️ sim | Justiça ✅ + **Responsabilização** ❌ | **Justiça** + **Robustez** | Desempenho que **cai em um subgrupo** = falha de **robustez**. Responsabilização só aparece quando falta **dono** ou **trilha de auditoria** |

### O que estudar em cada erro

> [!example] #14 · Amazon Personalize: o que mantém as recomendações atualizadas
> | Necessidade | Recurso |
> |---|---|
> | Reagir ao que o usuário **acabou de fazer** (clique, compra) | **Event tracker + API PutEvents** (rastreamento em tempo real) |
> | Mostrar **itens novos** ou com pouca interação (*cold start*) | **Exploration weight** (0 = só o que já é popular; 1 = mais descoberta) |
> | Gerar recomendações **para todos de uma vez**, sem tempo real | Inferência **em lote** (batch) |
> | Preparar dados antes do treino | Transformação de recursos: o Personalize **já faz quase tudo sozinho**, e isso **não acompanha mudanças** ao longo do tempo |
>
> **Gatilho:** "padrões mudam", "comportamento recente", "sazonal" → **eventos em tempo real**. → [[10 - Amazon Personalize|Amazon Personalize]]

> [!example] #17 · Tipos de viés: de onde ele vem
> | Tipo | Origem | Exemplo |
> |---|---|---|
> | **Viés humano** (cognitivo) | **Julgamento de uma pessoa** durante o projeto | Escolher atributos "porque eu acho importante" |
> | **Viés histórico / algorítmico** | **Dados do passado** com decisões injustas | Contratações antigas favoreciam homens → o modelo repete |
> | **Viés de amostragem / representação** | Grupo **pouco representado** no dataset | Poucos pacientes de minorias (#63) |
> | **Data skew / drift** | O dado **muda** por fator externo | Sazonalidade |
>
> **A pegadinha:** o cenário descrevia viés **histórico**, mas a pergunta pedia o exemplo de viés **humano**, "de forma distinta de outras questões relacionadas a viés". Responda **o que a pergunta pede**, não o que o cenário descreve. → [[01 - IA Responsável - Conceitos e Riscos#3. Características de um bom dataset|Características de um bom dataset]]

> [!example] #20 · As 4 formas de adaptar um FM no Bedrock
> | Técnica | Muda os pesos? | Dado usado |
> |---|---|---|
> | Prompt engineering | ❌ | Instruções e exemplos no prompt |
> | **RAG / Knowledge Bases** | ❌ | Documentos buscados **na hora da consulta** |
> | **Fine-tuning** | ✅ | **Rotulado** (pares prompt → resposta) |
> | Pré-treino contínuo | ✅ | **Não rotulado** do domínio |
>
> Provisioned Throughput é **capacidade de inferência**, não personalização. → [[02 - Foundation Models|Foundation Models]] · [[05 - Bedrock RAG - Knowledge Bases|Bedrock RAG - Knowledge Bases]]

> [!example] #33 · Métrica automática x avaliação humana
> | A pergunta pede... | Resposta |
> |---|---|
> | "**Métrica** automática para resumo" | **ROUGE** |
> | "**Métrica** automática para tradução" | **BLEU** |
> | "Avaliar a **qualidade**, **coerência**, **fluência**, **legibilidade** do texto" | **Avaliação humana** |
> | "Avaliar a **acurácia** de um classificador de imagens" | **Dataset de benchmark** (#4) |
>
> ROUGE e BLEU são **rápidas e escaláveis**, mas só contam **palavras em comum** com o gabarito. Um resumo pode ter ROUGE alto e ser confuso. → [[03 - Métricas de Avaliação - Resumo, Tradução e Transcrição|Métricas de Avaliação]]

> [!example] #63 · Qual princípio foi violado?
> | Sintoma no enunciado | Princípio |
> |---|---|
> | Resultado **desigual entre grupos** | **Justiça (fairness)** |
> | Desempenho **cai em um subconjunto** ou em condições diferentes | **Robustez** |
> | Ninguém consegue **explicar** a previsão | **Transparência / explicabilidade** |
> | Não há **dono** das decisões nem **trilha de auditoria** | **Responsabilização (accountability)** |
> | Dados vazados ou expostos | **Privacidade e segurança** |
>
> Neste cenário o mesmo problema fere **dois** princípios: é **injusto** (grupos diferentes) **e** pouco **robusto** (o modelo falha justamente nos dados sub-representados). → [[01 - IA Responsável - Conceitos e Riscos#1. As dimensões de IA responsável|As dimensões de IA responsável]]

## 🏷️ As 13 questões marcadas que você acertou: por que estão certas

> [!tip] Como usar
> Você acertou essas, mas marcou porque ficou em dúvida. Leia o **gatilho** de cada uma: é a palavra do enunciado que já entrega a resposta. Na prova, ao achar o gatilho, você não precisa ficar em dúvida.

### #4 · Avaliar a acurácia de um FM de classificação de imagens → **Dataset de benchmark** (D3)
- **Por que está certa:** um benchmark (ImageNet, CIFAR-10) é um conjunto **rotulado, padronizado e que o modelo nunca viu**. Com ele a acurácia é **objetiva e comparável**.
- **Por que as outras caem:** dados de **treino** dão nota otimista (o modelo já viu), **produção** é tarde demais e **imagens aleatórias** não têm consistência.
- **Gatilho:** "**acurácia**" + tarefa com resposta certa (classificação) → **benchmark**. Compare com o #33: "**qualidade**" de texto → **humano**.

### #6 · Objetivo dos modelos de difusão → **Gerar amostras de alta qualidade a partir de ruído** (D2)
- **Por que está certa:** no treino, o modelo **adiciona ruído** à imagem até virar ruído puro e aprende a **desfazer** isso passo a passo. Para gerar, começa do ruído e vai **limpando** até sair uma imagem nova. Exemplo: **Stable Diffusion**.
- **Por que as outras caem:** classificar imagens é tarefa de **CNN**. Detectar anomalias é tarefa **estatística** ou **não supervisionada**. Traduzir é tarefa de **transformer**.
- **Gatilho:** "difusão" = **ruído → imagem**.

### #7 · Analisar avaliações **no momento em que chegam** → **API em tempo real (síncrona) do Comprehend** (D1)
- **Por que está certa:** a API síncrona recebe **um texto por vez** e devolve na hora sentimento, frases-chave e entidades.
- **Por que as outras caem:** **S3 + Athena** é consulta **em lote**, depois. **Comprehend Medical** é só para texto **clínico**. **Lex** é para **chatbot**, não para analisar texto.
- **Gatilho:** "no momento em que são enviadas", "sem demora" → **tempo real**. "Milhares de documentos de uma vez" seria **job assíncrono**. → [[01 - Amazon Comprehend|Amazon Comprehend]]

### #15 · VAE x GAN → **VAE amostra de uma distribuição aprendida. GAN usa duas redes que competem** (D2)
- **Por que está certa:**
  - **VAE** = **codificador** (comprime a entrada num espaço latente probabilístico) + **decodificador** (sorteia um ponto desse espaço e gera dado novo).
  - **GAN** = **gerador** (cria falsificações) x **discriminador** (tenta descobrir o falso). Os dois treinam um contra o outro.
- **Por que as outras caem:** a opção C **inverte** os componentes. Os dois são **generativos**, nenhum é classificador. "Tempo real x lote" não define nenhum dos dois.
- **Macete:** **V**AE = **V**ariação de uma distribuição (codificador → decodificador). **G**AN = **G**ato e rato (gerador x discriminador).

### #19 · Descrições **criativas** e não repetitivas → **Temperatura alta + Top-P alto** (D3)
- **Por que está certa:** a temperatura alta aumenta a **aleatoriedade** na escolha da palavra. O Top-P alto deixa **mais candidatas** no sorteio. Os dois juntos dão **variedade**.
- **Por que as outras caem:** qualquer opção com **temperatura baixa** ou **top-p/top-k baixo** **restringe** o modelo às palavras mais prováveis, e o texto fica repetitivo. "Top-K alto + Top-P baixo" **anula** o ganho: o Top-P baixo corta de novo.
- **Gatilho:** "criativo", "variado", "evitar repetição" → **tudo alto**. "Consistente", "factual", "determinístico" → **tudo baixo**. → [[05 - Parâmetros de Inferência|Parâmetros de Inferência]]

### #22 · Recursos do SageMaker JumpStart → **Avaliar/comparar FMs com métricas prontas** + **modelos pré-treinados personalizáveis com seus dados** (D3)
- **Por que está certa:** o JumpStart é um **hub de modelos pré-treinados** (públicos **e** proprietários), com templates de solução. Ele permite **comparar FMs** por métricas de qualidade e responsabilidade e fazer **fine-tuning** com os seus dados.
- **Por que as outras caem:** "interface visual **sem código**" é o **SageMaker Canvas**. "Só modelos públicos" é falso. "Seus dados treinam o modelo base" é falso: os dados **não** treinam o modelo base.
- **Gatilho:** "começar rápido com modelos **pré-construídos**" → **JumpStart**. "**Sem código**" → **Canvas**. → [[05 - SageMaker - IA Generativa|SageMaker - IA Generativa]]

### #24 · O que **NÃO** é tarefa de um agente de IA → **Codificar manualmente regras para cada tarefa** (D2)
- **Por que está certa:** o agente usa o **FM para raciocinar** e decidir os passos, e chama APIs e bancos de dados sozinho. Escrever regras à mão para cada tarefa é o oposto disso: é **automação tradicional**, baseada em regras.
- **Por que as outras caem:** ajustar configurações, atualizar estoque e consultar banco de dados são exatamente o que um agente faz: **age** em sistemas por meio de *action groups*.
- **Gatilho:** pergunta com "**NÃO**" → procure a opção **manual** ou **fixa**. → [[06 - Bedrock Agents|Bedrock Agents]]

### #25 · Amazon Q x Amazon Bedrock → **Q é assistente pronto; Bedrock é o ambiente para construir com FMs** + **só o Bedrock deixa escolher o FM** (D3)
- **Por que está certa:**
  - **Amazon Q** = assistente **pronto para usar** (Q Business para funcionários, Q Developer para código). O modelo por trás é **fixo**.
  - **Amazon Bedrock** = **plataforma** para **construir** apps: você **escolhe o FM** (Anthropic, Meta, Mistral, Amazon...) e pode usar fine-tuning, RAG e agentes.
- **Por que as outras caem:** três opções **invertem** os papéis, e uma diz que os dois são assistentes.
- **Macete:** **Q** = **Q**uero usar pronto. **Bedrock** = **B**uild (construir). → [[16 - Amazon Q|Amazon Q]] · [[01 - Amazon Bedrock|Amazon Bedrock]]

### #28 · Few-shot para reconhecer **intenção** → **Exemplos de entrada do usuário + intenção correta** (D3)
- **Por que está certa:** a tarefa é **classificar**. Então cada exemplo precisa mostrar **a entrada e o rótulo** que se espera: `"Quero meu dinheiro de volta" → reembolso`. O modelo aprende o **padrão entrada → categoria**.
- **Por que as outras caem:** "entrada + **resposta** do modelo" ensina a **responder**, não a **classificar**. A opção sem a **entrada do usuário** não tem o que mapear.
- **Regra:** no few-shot, o exemplo tem o **mesmo formato da saída** que você quer. Quer um rótulo? O exemplo termina em **rótulo**. → [[03 - Tipos de Prompt|Tipos de Prompt]]

### #30 · Auditores precisam **entender** como o sistema decide → **Transparência + Explicabilidade** (D4)
- **Por que está certa:**
  - **Transparência** = o **processo** fica aberto para revisão: dados usados, lógica, como o sistema foi feito.
  - **Explicabilidade** = cada **decisão** vem com o **motivo** (quais fatores pesaram nesta transação).
- **Por que as outras caem:** segurança evita **dano**, escalabilidade é **volume**, viés e variância tratam de **precisão e justiça**. Nenhuma delas torna a decisão **compreensível**.
- **Gatilho:** "rastrear como chegou à conclusão", "compreensível para auditores" → **transparência + explicabilidade**. → [[02 - IA Responsável - Transparência e Explicabilidade|IA Responsável - Transparência e Explicabilidade]]

### #45 · Prever falhas com **precisão** e ainda ser **interpretável** → **Interpretabilidade x desempenho** (D4)
- **Por que está certa:** modelos mais complexos (deep learning, ensembles) costumam ser **mais precisos** e **mais difíceis de explicar**. Modelos simples (regressão, árvore) são **fáceis de explicar** e às vezes **menos precisos**. O cenário pede **os dois**, e por isso esse é o trade-off.
- **Por que as outras caem:** **viés x variância** é sobre **generalizar** (overfitting x underfitting). **Segurança x transparência** é sobre **evitar dano** x expor a lógica. **Controlabilidade** é sobre **ajustar** o modelo.
- **Gatilho:** "preciso" + "entender e confiar" no mesmo enunciado → **interpretabilidade x desempenho**. → [[02 - IA Responsável - Transparência e Explicabilidade#3. Os trade-offs|Os trade-offs]]

### #49 · Gerar **imagens a partir de texto** no Bedrock → **Stable Diffusion** (D2)
- **Por que está certa:** o Stable Diffusion (Stability AI) é um **modelo de difusão** de **texto → imagem** disponível no Bedrock (veja o #6).
- **Por que as outras caem:** **Jurassic** (AI21), **Llama** (Meta) e **Claude** (Anthropic) **geram texto**. O Claude até **analisa** imagens, mas não **cria** imagens.
- **Também vale:** **Amazon Nova Canvas** (e o antigo Titan Image Generator) gera imagens. Se aparecer como opção, também é texto → imagem. → [[14 - Amazon Nova|Amazon Nova]]

### #50 · Residência de dados x registro de dados → **Residência = onde o dado fica fisicamente. Registro = rastrear acesso e alterações ao longo do tempo** (D5)
- **Por que está certa:**
  - **Residência (data residency)** = **onde** (país ou região) o dado é armazenado. Serve para cumprir lei regional (LGPD, GDPR). Na AWS, você escolhe a **Região**.
  - **Registro (data logging)** = **quem fez o quê e quando** com o dado. Na AWS: **CloudTrail**, CloudWatch Logs.
- **Por que as outras caem:** uma opção **inverte** os conceitos. As outras misturam com **criptografia**, **ciclo de vida** e **transformação**, que são outros controles.
- **Macete:** **Resid**ência = onde o dado **reside**. **Log** = **diário** do dado. Era ponto fraco no S4 e agora você acertou. → [[06 - Domínio 5 - Segurança, Compliance e Governança]]

## 🔁 Reforço: 8 questões nos pontos fracos

**R1.** Um e-commerce usa Amazon Personalize e quer que as recomendações reflitam **o que o cliente clicou há 2 minutos**. O que fazer?

> [!success]- Resposta
> **Rastreamento de eventos em tempo real** (event tracker + **PutEvents**). Retreinar ou usar batch não reage em minutos.

**R2.** O mesmo e-commerce lança **500 produtos novos** que ainda não têm interações. Qual configuração ajuda esses itens a aparecer?

> [!success]- Resposta
> **Exploration weight** mais alto (mais descoberta de itens novos ou com pouca interação).

**R3.** Classifique o viés: (a) o engenheiro tira o atributo "bairro" porque **acha** que não importa; (b) o modelo de crédito repete **décadas** de negações a um grupo; (c) o dataset tem **2%** de pacientes idosos.

> [!success]- Resposta
> (a) **Viés humano** · (b) **viés histórico/algorítmico** · (c) **viés de amostragem/representação**.

**R4.** Uma empresa quer que o FM no Bedrock adote **o jargão jurídico interno**, e tem **5 mil pares pergunta → resposta** revisados. Qual técnica usar, e ela muda os pesos?

> [!success]- Resposta
> **Fine-tuning**: dado **rotulado**, **muda os pesos**. Se os dados fossem documentos sem rótulo, seria **pré-treino contínuo**. Se fosse só para consultar documentos atuais, seria **RAG** (sem mudar pesos).

**R5.** O time quer uma **métrica automática e escalável** para comparar 3 modelos de **resumo** em 10 mil documentos. E se quisesse saber se os resumos são **claros e coerentes** para o cliente?

> [!success]- Resposta
> Métrica automática → **ROUGE**. Clareza e coerência → **avaliação humana** (no Bedrock: Model Evaluation com **avaliadores humanos**).

**R6.** Um modelo de visão funciona bem com fotos diurnas e erra muito com **fotos noturnas**, que eram raras no treino. Qual princípio de IA responsável está mais em jogo?

> [!success]- Resposta
> **Robustez**: o desempenho cai em **condições diferentes** ou **pouco representadas**.

**R7.** Após um erro grave, ninguém na empresa sabe **quem aprovou** o modelo para produção e não há registro das decisões. Qual princípio falhou?

> [!success]- Resposta
> **Responsabilização (accountability)**: falta **dono** e **trilha de auditoria**. Ferramentas: SageMaker Model Registry (aprovação), Model Cards, CloudTrail.

**R8.** Verdadeiro ou falso: "Para reduzir alucinações de um chatbot sobre políticas internas, o melhor é fazer fine-tuning semanal".

> [!success]- Resposta
> **Falso.** Dados que mudam com frequência e precisam de fonte → **RAG / Knowledge Bases**. Fine-tuning é caro, não cita fonte e fica desatualizado.

## Plano até a prova

| Dia | Foco | Notas |
|---|---|---|
| 1 | **Tipos de viés** (humano x histórico x amostragem) + **princípio violado por sintoma** (tabela do #63) + R3, R6, R7 | [[01 - IA Responsável - Conceitos e Riscos\|IA Responsável - Conceitos e Riscos]] · [[04 - IA Responsável - Formulário de Respostas\|IA Responsável - Formulário de Respostas]] |
| 2 | **Prompt x RAG x fine-tuning x pré-treino** + **métrica automática x avaliação humana x benchmark** + R4, R5, R8 | [[02 - Foundation Models\|Foundation Models]] · [[03 - Métricas de Avaliação - Resumo, Tradução e Transcrição\|Métricas de Avaliação]] |
| 3 | Revisar os **gatilhos** das 13 marcadas acima + Personalize (R1, R2) | [[10 - Amazon Personalize\|Amazon Personalize]] |
| 4 | **Simulado 6**, com meta de **85%+** e **D4 acima de 80%** | — |

## Histórico de simulados

| Data | Simulado | Tentativa | Nota | Pior domínio |
|---|---|---|---|---|
| 2026-11-12 | Udemy Simulado 1 | 2 | 44/65 (68%) | Segurança (44%) · Fundamentos IA/ML (54%) |
| 2026-11-12 | Udemy Simulado 2 | 1 | 50/65 (76%) ✅ | IA Responsável (67%) · Aplicações de FMs (72%) |
| 2026-11-13 | Udemy Simulado 3 | 1 | 56/65 (86%) ✅ | Fundamentos IA/ML (77%) · IA Responsável (78%) |
| 2026-11-14 | Udemy Simulado 4 | 1 | 46/65 (70%) ⚠️ | Segurança (44%) · IA Responsável (44%) |
| 2026-11-16 | Udemy Simulado 5 | 1 | **60/65 (92%)** ✅ | IA Responsável (78%) · Aplicações de FMs (89%) |

---
Anterior: [[04 - Udemy Simulado 4 - Tentativa 1 - Análise e Reforço|Udemy Simulado 4 - Tentativa 1 - Análise e Reforço]] · Início: [[00 - Início - Guia do Exame]] · Checklist: [[09 - Checklist de Estudo]]
