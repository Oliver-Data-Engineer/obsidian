O que é o Amazon Translate?
	O Amazon Translate é um serviço de tradução de texto que usa tecnologias avançadas de machine learning para fornecer traduções de alta qualidade sob demanda. Você pode o Amazon Translate para traduzir documentos de texto não estruturado ou para criar aplicativos que funcionam em vários idiomas.

Como o Amazon Translate funciona ?


## Formatos compatíveis para o conteúdo de entrada

O Amazon Translate oferece suporte aos seguintes formatos para o conteúdo de entrada:

- Para traduções em tempo real:
    
    - **Texto de entrada** — Texto simples no formato UTF-8. O Amazon Translate fornece o conteúdo de saída como texto UTF-8.
        
    - **Um arquivo de entrada** — um arquivo contendo conteúdo de texto sem formatação (.txt), HTML (.html) ou Word (.docx). O Amazon Translate fornece o conteúdo de saída como um arquivo no mesmo formato do arquivo de entrada.
        
    
- Para trabalhos de tradução em lote:
    
    - **Coleção de arquivos de entrada** — Um ou mais arquivos que você carrega em um local do Amazon S3. Os formatos de arquivo compatíveis incluem texto sem formatação (.txt), HTML (.html), Word (.docx), Excel (.xlsx), (.pptx) e XLIFF 1.2 PowerPoint (.xlf). O Amazon Translate fornece o conteúdo de saída como arquivos. O formato de arquivo de cada arquivo de saída corresponde ao formato do arquivo de entrada.
## Como personalizar suas traduções

Você pode usar os seguintes recursos para personalizar as traduções que você produz com o Amazon Translate:

- **Do-not-translate tags** — usa tags de início e fim para especificar o conteúdo que você não deseja traduzir (em conteúdo HTML).
    
- **Terminologia personalizada**: define como você deseja que o Amazon Translate traduza termos específicos, como nomes de marcas.
    
- **Brevidade** — Reduz o tamanho da saída da tradução para a maioria das traduções (em comparação com a saída da tradução sem brevidade). O Brevity é compatível com traduções de texto em tempo real.
    
- **Profanidade** — mascara palavras e frases profanas em sua tradução.
    
- **Formalidade** — Define o nível de formalidade do idioma em sua saída de tradução.
    
- **Dados paralelos** — adapta a saída da tradução para refletir as opções de estilo, tom e palavra nos exemplos de tradução fornecidos por você.


Links de Referencia: 
	https://docs.aws.amazon.com/pt_br/translate/latest/dg/what-is.html
	https://aws.amazon.com/pt/translate/

Oque eu entendi:
	Basicamente um serviço tradutor, serve para traduzir textos não estruturados e pode ser configurada formas de traduzir exemplo de tradução não literal para nomes específicos podem ser configuradas  