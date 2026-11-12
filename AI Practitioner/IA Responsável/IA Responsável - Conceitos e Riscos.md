## Resumo

**Tarefa 4.1** do guia: o que torna um sistema de IA **responsável**, quais **riscos legais** a GenAI traz, como deve ser um **bom dataset**, o efeito de **viés e variância** e como escolher um modelo de forma **sustentável**.

> [!info] Ideia central
> Um sistema responsável trata **todos os grupos de forma justa**, **não causa dano**, **diz a verdade**, **aguenta entradas inesperadas** e pode ser **controlado e auditado**. Tudo começa nos **dados**.

---

## 1. As dimensões de IA responsável

A AWS define **8 dimensões** (o guia cita como exemplos: viés, justiça, inclusão, robustez, segurança e veracidade).

| Dimensão | Em uma linha | Exemplo de questão | Ferramenta AWS |
|---|---|---|---|
| **Justiça** (*fairness*) | Considerar o impacto em **diferentes grupos** de pessoas; evitar discriminação | "O modelo aprova menos crédito para mulheres" | Clarify, Model Monitor |
| **Explicabilidade** (*explainability*) | Entender e avaliar **por que** o sistema gerou a saída | "Explicar ao cliente o motivo da recusa" | Clarify (SHAP) |
| **Privacidade e segurança** | Dados e modelos **obtidos, usados e protegidos** corretamente | "Não expor CPF nas respostas" | Guardrails (PII), Macie, KMS |
| **Segurança** (*safety*) | **Prevenir saídas nocivas** e uso indevido | "Bloquear discurso de ódio" | Guardrails |
| **Controlabilidade** | Ter mecanismos para **monitorar e direcionar** o comportamento da IA | "Humano pode intervir/corrigir" | A2I, Model Monitor |
| **Veracidade e robustez** | Saída **correta**, mesmo com entradas **inesperadas ou adversárias** | "Modelo inventa fatos", "erra com erros de digitação" | Guardrails (grounding, automated reasoning), Bedrock Evaluations |
| **Governança** | Boas práticas em toda a **cadeia de IA** (fornecedores e quem implanta) | "Quem aprovou este modelo?" | Model Cards, Model Registry |
| **Transparência** | Dar às partes interessadas o que precisam para **decidir com informação** se usam o sistema | "Usuário sabe que fala com uma IA" | Model Cards, AI Service Cards |

Além dessas, o guia cita:
- **Viés** (*bias*): o modelo favorece/prejudica sistematicamente algum grupo.
- **Inclusão** (*inclusivity*): o sistema funciona para **todos**, incluindo minorias, idiomas, sotaques, pessoas com deficiência.

> [!tip] Dica para lembrar
> **"Justo, Explicável, Privado, Seguro, Controlável, Verdadeiro, Governado, Transparente."** Na prova, associe cada dimensão a um **sintoma** do cenário.

---

## 2. Riscos legais da IA generativa

| Risco (guia) | O que é | Exemplo | Como mitigar |
|---|---|---|---|
| **Violação de propriedade intelectual** | Saída copia ou se parece demais com obra protegida | Imagem gerada igual a um personagem famoso; código copiado com licença restritiva | Modelos com **indenização de PI** do fornecedor, filtros, revisão humana, verificar **licença** do modelo e dos dados |
| **Saídas enviesadas** | Respostas discriminatórias → processos e multas | Triagem de currículos que penaliza um gênero | Datasets balanceados, Clarify, análise por subgrupo |
| **Perda de confiança do cliente** | Erros ou respostas ofensivas destroem a reputação | Chatbot xinga cliente nas redes sociais | Guardrails, testes, transparência |
| **Risco ao usuário final** | A resposta causa **dano real** a quem confia nela | Conselho médico ou financeiro errado | Tópicos negados, avisos, **humano no loop** (A2I) |
| **Alucinações** | Resposta **confiante, mas falsa** | Advogado cita jurisprudência inventada pelo LLM | **RAG**, **contextual grounding check**, temperatura baixa, revisão humana |

Outros riscos que aparecem junto: **toxicidade**, **privacidade de dados** (vazamento de PII), **não determinismo** (mesma pergunta, respostas diferentes), **prompt injection / jailbreak** → [[Riscos e Segurança em Prompts]].

---

## 3. Características de um bom dataset

| Característica | Significa | Se faltar... |
|---|---|---|
| **Inclusivo** | Representa **todos os grupos** que usarão o sistema | Modelo falha para quem ficou de fora |
| **Diverso** | Variedade de cenários, origens, idiomas, condições | Modelo não generaliza |
| **Fontes curadas** | Dados de **origem confiável**, verificada e com direito de uso | Lixo entra, lixo sai; risco de PI |
| **Balanceado** | Quantidade **proporcional** de exemplos por classe/grupo | Viés para o grupo majoritário |

Também conta: **rótulos de qualidade** (*label quality*), dados **atualizados**, **privacidade** respeitada (PII removida), **documentação** da origem (linhagem).

> [!example] Exemplo clássico
> Reconhecimento facial treinado com 90% de rostos de pele clara → erra muito mais com pele escura. Problema: dataset **não inclusivo/balanceado**. Solução: **coletar dados representativos**, medir com **análise por subgrupo**.

---

## 4. Viés x variância

| | **Alto viés** | **Alta variância** |
|---|---|---|
| Problema | **Underfitting** | **Overfitting** |
| Sintoma | Erra **no treino e no teste** | Ótimo no treino, **ruim em dados novos** |
| Causa | Modelo **simples demais**, poucas features | Modelo **complexo demais**, decorou o ruído |
| Solução | Modelo mais complexo, mais features, treinar mais | Mais dados, regularização, menos features, *early stopping*, validação cruzada |

> [!warning] Dois sentidos de "viés"
> - **Viés estatístico** (bias x variance): erro por modelo simples demais → underfitting.
> - **Viés de justiça** (*bias/fairness*): modelo trata **grupos demográficos** de forma diferente.
> Leia o contexto: se fala de **grupos de pessoas**, é justiça; se fala de **treino x teste**, é estatístico.

**Efeito em grupos demográficos:** um modelo pode ter **boa acurácia geral** e ser **muito pior para um subgrupo** (idosos, minorias). Por isso o guia pede **análise por subgrupo**: medir as métricas **separadas por grupo**, não só a média.

---

## 5. Escolha responsável do modelo (sustentabilidade)

O guia pede "considerações ambientais e de sustentabilidade" ao escolher o modelo.

| Prática | Por que é responsável |
|---|---|
| **Usar FM pré-treinado** em vez de treinar do zero | Treinar um LLM consome energia enorme |
| Escolher o **menor modelo que atende** ao caso de uso | Menos computação por requisição |
| **Prompt engineering / RAG** antes de fine-tuning, fine-tuning antes de pré-treino | Ordem crescente de custo e energia |
| **Destilação** de modelos | Modelo menor, mais barato e eficiente |
| Hardware eficiente: **AWS Inferentia** (inferência) e **AWS Trainium** (treino) | Melhor desempenho por watt |
| Serverless / desligar recursos ociosos; inferência **batch** quando possível | Não desperdiça recursos |
| Regiões com mais energia renovável; pilar **Sustentabilidade** do Well-Architected | Menor pegada de carbono |

Outros critérios de escolha responsável: **licença** do modelo, **documentação** (Model/Service Cards), resultado em **avaliações de viés e toxicidade**, idiomas suportados, **custo**, latência.

---

## Exemplo para Associação Mental

**O restaurante.** Os **ingredientes** são o dataset: precisam ser **variados, frescos, de fornecedor confiável e na proporção certa** (inclusivo, diverso, curado, balanceado). O **chef** é o modelo: se só sabe fazer arroz, erra tudo (**underfitting**); se decorou só o gosto de um cliente, erra com os outros (**overfitting**). A **vigilância sanitária** são os Guardrails e as auditorias. Servir um prato estragado é o **risco ao usuário final**; copiar a receita patenteada do vizinho é **violação de PI**; inventar que o prato é orgânico é **alucinação**. E não precisa ligar o forno industrial para fazer um ovo (**sustentabilidade**).

## 📝 Meu entendimento
> _Explique com suas palavras: por que um modelo com 95% de acurácia pode ser injusto?_

---
Voltar: [[Índice - IA Responsável]] · Próximo: [[IA Responsável - Transparência e Explicabilidade]]

Fontes: [AWS Responsible AI – dimensões](https://aws.amazon.com/ai/responsible-ai/) · [AIF-C01 Exam Guide – Domínio 4](https://docs.aws.amazon.com/aws-certification/latest/ai-practitioner-01/ai-practitioner-01-domain4.html) · [Well-Architected – Sustainability Pillar](https://docs.aws.amazon.com/wellarchitected/latest/sustainability-pillar/sustainability-pillar.html)
