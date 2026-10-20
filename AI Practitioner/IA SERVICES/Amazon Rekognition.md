## Resumo

O **Amazon Rekognition** é o serviço de **visão computacional** da AWS. Ele analisa **imagens e vídeos** (gravados ou ao vivo) para detectar **objetos, cenas, rostos, texto e conteúdo impróprio**, sem que você precise construir modelos de ML ou infraestrutura. Escala para milhões de imagens e você paga só pelo que analisar.

> [!info] Ideia central
> **Imagem/vídeo → o que tem nela (rótulos, rostos, texto, moderação).** São os "olhos" da AWS.
> 🔑 Palavras-chave na prova: "**imagem**", "**vídeo**", "**reconhecimento facial**", "**detectar objetos**", "**moderação de conteúdo**", "**celebridades**", "**EPI**".

## Ficha rápida

| Item | Detalhe |
|---|---|
| **Categoria** | Visão computacional |
| **Entrada** | Imagens (JPEG/PNG) e vídeos (no S3 ou **streaming** via Kinesis Video Streams) |
| **Saída** | JSON com rótulos, coordenadas (*bounding boxes*) e **nível de confiança** |
| **Precisa saber ML?** | Não. APIs pré-treinadas |
| **Customização** | **Custom Labels**: treine com **suas imagens** para reconhecer seus objetos (ex.: seus produtos, defeitos de peça) |
| **Modos** | Imagem (síncrono) · Vídeo armazenado (assíncrono) · Vídeo ao vivo (streaming) |
| **Na prova** | Domínio 1 · Tarefa 1.2 · ⭐⭐⭐ |
| **Status 2026** | ✅ Disponível · ⚠️ *Streaming Events* e *moderação de imagens em lote* fechados para novos clientes (anúncio de 31/03/2026) |

## Principais recursos

| Recurso | O que faz | Exemplo |
|---|---|---|
| **Rótulos** (*labels*) | Detecta **objetos, cenas e atividades** | "carro", "praia", "pessoa correndo" |
| **Detecção e análise facial** | Encontra rostos e descreve **atributos**: faixa etária, **emoções**, **olhos abertos**, **sorriso**, óculos, barba | Foto de perfil válida? |
| **Comparação e busca de rostos** | Compara dois rostos ou procura um rosto em uma **coleção** | Verificação de identidade, controle de acesso |
| **Face Liveness** | Confirma que é uma **pessoa real** na câmera, não uma foto ou vídeo | Abertura de conta digital |
| **Reconhecimento de celebridades** | Identifica pessoas famosas | Catálogo de mídia |
| **Texto em imagem** (*DetectText*) | Lê textos **curtos** em cenas | Placas de carro, letreiros, camisetas |
| **Moderação de conteúdo** | Detecta conteúdo **impróprio** (nudez, violência…) | Moderação de fotos enviadas por usuários |
| **Detecção de EPI** | Verifica capacete, máscara e luvas | Segurança do trabalho |
| **Detecção de segmentos de vídeo** | Encontra cenas, créditos e telas pretas | Mídia e streaming |
| **Custom Labels** | Modelo **treinado com suas imagens** (poucas centenas bastam) | Detectar defeito em peça na linha de produção |

## Casos de uso

| Cenário | Como o Rekognition ajuda |
|---|---|
| **Verificação de identidade** | Compara a selfie com a foto do documento + Face Liveness |
| **Moderação de conteúdo** | Filtra imagens impróprias em redes sociais e marketplaces |
| **Busca em acervo de mídia** | Encontra fotos/vídeos por objeto, pessoa ou celebridade |
| **Segurança e acesso** | Reconhecimento facial na entrada de prédios |
| **Indústria** | Detectar defeitos com Custom Labels; verificar uso de EPI |

## Não confunda

| Serviço | Diferença |
|---|---|
| [[Amazon Textract]] | Para **documentos** (formulários, tabelas, notas fiscais), use o **Textract**. O Rekognition lê só textos **curtos em cenas** (placa, letreiro) |
| [[Amazon Augmented AI]] | Quando o Rekognition tem **baixa confiança** na moderação, o A2I manda a imagem para **revisão humana** |
| [[Amazon SageMaker]] | Para um modelo de visão **totalmente próprio**, use o SageMaker. Para algo **pronto** (ou Custom Labels), use o Rekognition |
| [[Amazon Bedrock]] | Modelos multimodais do Bedrock **descrevem** imagens livremente. O Rekognition dá saídas **estruturadas** e especializadas (rostos, moderação) |

> [!warning] Pegadinhas de prova
> - "Detectar **rostos**, **emoções** ou **celebridades**" → **Rekognition**.
> - "Moderar **imagens** enviadas por usuários" → **Rekognition** (moderação de conteúdo).
> - "Extrair dados de um **formulário escaneado**" → **Textract**, não Rekognition.
> - "Reconhecer **os produtos da minha empresa**" → **Rekognition Custom Labels**.

## Exemplo para Associação Mental

**O Segurança com Câmeras.** *Rekognition* = **reconhecer**. É o vigia na sala de monitoramento: olha as câmeras, reconhece **quem entrou** (rostos), percebe **se está sorrindo** (emoções), lê a **placa do carro** (texto) e dá o alarme se aparecer algo **impróprio** (moderação).

## 📝 Meu entendimento

> **Casos de uso:**
> - Detecção de usuarios e rostos
> - Análise de Face como Olhos Abertos Sorriso Sentimento
> - Detecção de textos em imagens, video texto

---
Resumo: [[Resumo]] · Anterior: [[Amazon Lex]] · Próximo: [[Amazon Textract]]

Fontes: [Amazon Rekognition](https://aws.amazon.com/pt/rekognition/) · [Classificação de imagens com Rekognition](https://docs.aws.amazon.com/pt_br/prescriptive-guidance/latest/image-classification/rekognition.html) · [Serviços em manutenção (AWS)](https://docs.aws.amazon.com/general/latest/gr/maintenance_services.html)
