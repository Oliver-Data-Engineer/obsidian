Processamento de linguagem natural
Extração de insights de texto e documentos

Associação Compreender algo (Comprehend)

O Amazon Comprehend é um serviço de processamento de linguagem natural (PLN) que usa machine learning (ML) para descobrir insights no texto. O Amazon Comprehend fornece reconhecimento personalizado de entidades, classificação personalizada, extração de frases-chave, análise de sentimento, reconhecimento de entidades e mais APIs para facilitar a integração do NLP às aplicações. Basta chamar as APIs do Amazon Comprehend em sua aplicação e fornecer a localização do documento ou texto de origem. As APIs emitem uma saída com entidades, frases-chave, sentimentos e idioma em um formato JSON, que pode ser usada em sua aplicação.

**Exemplo:** uma seguradora deseja analisar documentos de texto em busca de entidades específicas para sua linha de negócios, número de apólices.

**Texto de exemplo:** Olá, meu nome é Sam Ford e preciso acionar o seguro devido a um acidente de carro. O código da minha apólice é 456-YQT.

## Exemplo

|Entidade|Categoria|Contagem|Confiança|
|---|---|---|---|
|456-YQT|ID da Apólice|1|0.95|


Link todos os atributos e funções: https://aws.amazon.com/pt/comprehend/features/


Meu entendimento:
	O Amazon Comprehend é um serviço para facilitar a integração de modelos de NLP, facilitando assim trabalhos como analise de sentimento, classificação, categorização, cenários onde seriam necessários trinar um modelo complexo de NPL para extrair informações de texto o Amazon Comprehend faz, podendo analisar diretamente documento ou texto de diferentes formas e com N objetivos, como analise de sentimento, identificação de localidade, identificação de pernoas e identidades