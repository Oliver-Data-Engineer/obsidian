## Resumo

O **Amazon Comprehend Medical** é a versão do Comprehend **especializada em saúde**. Ele lê **textos clínicos não estruturados** (anotações médicas, resumos de alta, laudos, resultados de exames) e devolve as **informações médicas** que estão no texto: **condições, medicamentos com dosagem, exames, procedimentos, anatomia** e os **dados protegidos de saúde (PHI)**. Também liga essas informações a **códigos médicos padrão** (ICD-10-CM, RxNorm, SNOMED CT).

> [!info] Ideia central
> **Texto clínico → entidades médicas + PHI + códigos padronizados.** É o Comprehend que "fez medicina".
> 🔑 Palavras-chave na prova: "**anotações médicas / clínicas**", "**medicamentos e dosagens**", "**diagnósticos**", "**PHI**", "**HIPAA**", "**codificação médica (ICD-10)**", "**prontuário em texto**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Linguagem (NLP) para **saúde** |
| **Entrada** | **Texto** clínico em **inglês (EUA)** · arquivo único (tempo real) ou lote no **S3** |
| **Saída** | JSON com entidades, categoria, tipo, atributos, traços, posição no texto e **nível de confiança** |
| **Precisa saber ML?** | Não. Modelos **pré-treinados** prontos por API |
| **Customização** | Não tem treino personalizado (diferente do Comprehend comum) |
| **Compliance** | Serviço **elegível para HIPAA** · conexões via **TLS** · **não armazena** o conteúdo do cliente |
| **Preço** | Pago por **quantidade de texto analisado**, sem mínimo (tabela própria, diferente do Comprehend) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐ (aparece em cenários de saúde) |
| **Status 2026** | ✅ Disponível |

## Principais recursos (APIs)

| Recurso | O que faz | Exemplo |
|---|---|---|
| **DetectEntitiesV2** | Detecta **todas** as entidades médicas e suas relações | "ibuprofeno 200 mg, 2x ao dia" → medicamento + dosagem + frequência |
| **DetectPHI** | Detecta só os **dados protegidos de saúde** (para anonimizar) | Nome do paciente, idade, endereço, nº do prontuário |
| **InferICD10CM** | Liga **condições médicas** aos códigos **ICD-10-CM** (CID) | "pneumonia" → código ICD-10 | 
| **InferRxNorm** | Liga **medicamentos** aos códigos **RxNorm** | "Tylenol" → identificador RxNorm |
| **InferSNOMEDCT** | Liga condições, anatomia, exames e procedimentos ao **SNOMED CT** | "raio-X de tórax" → conceito SNOMED |

> **Ontology linking** = ligar o texto livre a um **vocabulário médico padrão**. É isso que permite **faturamento** e **codificação** automática.

### O que ele detecta (categorias do DetectEntitiesV2)

| Categoria | Exemplos |
|---|---|
| **MEDICAL_CONDITION** | Sinais, sintomas e diagnósticos ("dor crônica na perna esquerda") |
| **MEDICATION** | Nome comercial/genérico + **dosagem, frequência, via, duração, forma** |
| **TEST_TREATMENT_PROCEDURE** | Exames (com **valor e unidade**), tratamentos, procedimentos |
| **ANATOMY** | Partes e sistemas do corpo, direção (esquerda, superior...) |
| **PROTECTED_HEALTH_INFORMATION** | Nome, idade, endereço, e-mail, telefone, IDs, profissão |
| **BEHAVIORAL_ENVIRONMENTAL_SOCIAL** | Tabaco, álcool, drogas, **alergias**, gênero, etnia |
| **TIME_EXPRESSION** | "há três dias", "ontem" (quando ligado a uma entidade) |

**Traços** (*traits*) que ele entende pelo contexto: **NEGATION** ("paciente **nega** febre"), **SIGN** (relatado pelo médico), **SYMPTOM** (relatado pelo paciente), **DIAGNOSIS**, **HYPOTHETICAL**, **PAST_HISTORY**, **PERTAINS_TO_FAMILY** (é do **pai**, não do paciente).

### Exemplo

**Texto:** *"Paciente relata dor de cabeça há 3 dias. Nega febre. Prescrito ibuprofeno 400 mg via oral a cada 8 horas. Pai com histórico de diabetes."*

| Entidade | Categoria | Atributos / traços |
|---|---|---|
| dor de cabeça | MEDICAL_CONDITION | SYMPTOM · tempo: "há 3 dias" |
| febre | MEDICAL_CONDITION | **NEGATION** |
| ibuprofeno | MEDICATION | dosagem 400 mg · via oral · frequência a cada 8 h |
| diabetes | MEDICAL_CONDITION | **PERTAINS_TO_FAMILY** |

## Casos de uso

| Cenário | Como ajuda |
|---|---|
| **Gestão de casos de pacientes** | Organiza informações que estão em texto livre; triagem precoce |
| **Pesquisa clínica** | Selecionar pacientes para **ensaios clínicos**; **farmacovigilância** (efeitos adversos de remédios) |
| **Faturamento médico / seguros** | Extrair diagnósticos e gerar **códigos ICD-10** para cobrança e sinistros |
| **Anonimização** | **DetectPHI** para remover dados do paciente antes de compartilhar/analisar |
| **Saúde populacional** | Achar lacunas de cuidado analisando milhares de prontuários |

## Combinações comuns

| Fluxo | Serviços |
|---|---|
| **Consulta gravada → entidades médicas** | **Transcribe Medical** (fala → texto) → **Comprehend Medical** |
| **Laudo escaneado / PDF → entidades** | **Textract** (extrai o texto) → **Comprehend Medical** |
| **Resultados de baixa confiança → médico revisa** | Comprehend Medical → **A2I** (humano no loop) |
| **Dados de saúde estruturados (FHIR) em escala** | **AWS HealthLake** (usa NLP médico integrado) |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[01 - Amazon Comprehend\|Amazon Comprehend]] | NLP **geral**: **sentimento**, frases-chave, idioma, PII, classificação **personalizada**. O Medical **não faz** análise de sentimento nem treino personalizado: é focado em **entidades médicas** |
| **Transcribe Medical** ([[04 - Amazon Transcribe\|Amazon Transcribe]]) | Converte **fala médica em texto**. O Comprehend Medical **analisa o texto** |
| [[08 - Amazon Textract\|Amazon Textract]] | **Extrai** texto de documentos e imagens. O Comprehend Medical **entende** o texto clínico |
| **Amazon Macie** | Encontra PII em **buckets S3**. O Comprehend Medical encontra **PHI dentro de um texto clínico** |
| **AWS HealthLake** | **Armazena e consulta** dados de saúde no padrão FHIR. O Comprehend Medical é só a **análise de texto** |

> [!warning] Pegadinhas de prova
> - "Extrair **medicamentos, dosagens e diagnósticos** de anotações médicas" → **Comprehend Medical** (não Comprehend comum, não SageMaker).
> - "Identificar **PHI** em prontuários para **HIPAA**" → **Comprehend Medical (DetectPHI)**.
> - "Gerar **códigos ICD-10** a partir do texto" → **Comprehend Medical (InferICD10CM)**.
> - "**Gravação** de consulta médica" → primeiro **Transcribe Medical**, depois Comprehend Medical.
> - Cenário de saúde que pede **sentimento + entidades médicas** (como a questão #41 do simulado) → a resposta esperada é **Comprehend Medical**, mesmo que o sentimento venha do Comprehend comum. O que define é o **texto clínico**.
> - Não substitui o médico: a AWS recomenda **revisão humana** em decisões de cuidado ao paciente.

## Exemplo para Associação Mental

**O Residente de Medicina.** O [[01 - Amazon Comprehend|Amazon Comprehend]] é o **leitor atento** com canetas coloridas. O **Comprehend Medical** é o **residente**: lê a letra do médico no prontuário, sublinha **doenças, remédios e doses**, percebe quando o paciente **nega** um sintoma ou quando a doença é do **pai**, cobre com tarja os **dados do paciente** (PHI) e anota ao lado o **código CID** de cada diagnóstico para o faturamento. Mas quem decide o tratamento continua sendo o médico.

## 📝 Meu entendimento

> _Explique com suas palavras: quando usar o Comprehend Medical em vez do Comprehend comum?_

---
Resumo: [[00 - Resumo - Serviços de IA|Resumo - Serviços de IA]] · Relacionado: [[01 - Amazon Comprehend|Amazon Comprehend]] · [[04 - Amazon Transcribe|Amazon Transcribe]] · [[08 - Amazon Textract|Amazon Textract]]

Fontes: [What is Amazon Comprehend Medical](https://docs.aws.amazon.com/comprehend-medical/latest/dev/comprehendmedical-welcome.html) · [Detect entities (Version 2)](https://docs.aws.amazon.com/comprehend-medical/latest/dev/textanalysis-entitiesv2.html) · [Amazon Comprehend Medical](https://aws.amazon.com/comprehend/medical/)
