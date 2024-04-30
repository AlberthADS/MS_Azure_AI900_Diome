Este tutorial irá demonstrar como realizar dois tipos de extração de dados a partir de linguagem de escrita e fala do Azure AI. Começaremos explorando o **Azure AI Speech**.

## 1. Explorar o Azure AI Speech

O **Azure AI Speech** é um recurso que transcreve falas em áudio para texto em tempo real. Com ele, é possível transcrever áudios de vídeo ou somente arquivos de áudio e ter uma saída em texto do que foi dito.

-  Criar um recurso no **Azure AI Speech**
	Antes de iniciar, precisamos um serviço de fala procurando para então iniciarmos os testes.
	
1. Abra o [Azure AI Speech Studio](https://speech.microsoft.com/), logando com sua conta da Microsoft.
    
2. Selecione a opção **Settings** e depois **Create a resource.** Configure com as seguintes configurações
    - **Name of new resource**: MicrosoftAISpeechStudio.
    - **Subscription**: Azure for Students _ou uma que esteja disponível_
    - **Region**: East US
    - **Pricing tier**: Standard S0.
    - **Resource group**: ETEC_Azure_ML _ou uma que esteja disponível_.
3. Selecione **Create resource** e aguarde alguns minutos até que o recurso esteja pronto.

## 2. Explorar o Fala em texto no Speech Studio

- Dentro deste repositório, baixe o áudio na pasta Inputs caso não tenha nenhum disponível.
    
- Em **Get started with Speech**, abaixo do _Speech to text_, encontre _Real-time speech to text_. Selecione **Try out Real-time speech to text**.
![[try-out-speech-to-text.png]]
- Sobre o _Choose audio files_, selecione **Browse files** e carregue o arquivo **WeAreGonna.m4a** ou algum outro de preferência.
![[use-with-your-resource.png]]

## 3. Analisando texto com o Language Studio

Nesta etapa, vamos agora realizar a análise de texto com o **Language Studio**. Com ele, podemos analisar o comportamento de comentários e detalhar como se comportam perante algum serviço que foi prestado, por exemplo. Muito útil em estabelecimentos que possuem campos de comentários dos clientes para melhorias de serviço.

Volte novamente para o portal do Azure e crie um novo recurso com as configurações abaixo:

- **Subscription**: Azure for Students _ou uma que esteja disponível._
- **Resource group**: ETEC_Azure_ML _ou uma que esteja disponível_.
- **Region**: East US.
- **Name**: AzureAILangStudio.
- **Pricing tier**: Free F0 _ou S se o Free F0 não estiver disponível_
- **By checking this box I acknowledge that I have read and understood all the terms below**: _Selecionado_.

## 4. ## Configure o recurso no Azure AI Language Studio

1. Acesse o **Language Studio** em [https://language.cognitive.azure.com](https://language.cognitive.azure.com?azure-portal=true) e logue com sua mesma conta Microsoft.
    
2. Quando uma tela dizendo **Select an Azure resource** aparecer, faça as seguintes configurações
    
    - **Azure directory**: _Default Directory, o diretório que você está usando_
    - **Azure subscription**: _Selecione a inscrição que esteja usando_
    - **Resource type**: Language
    - **Resource name**: _AzureAILangStudio_

## 5. Analisando críticas no Language Studio

- Na tela **Welcome to Language Studio**, selecione a aba **Classify text**, depois selecione **Analyze sentiment and mine opinions**.
    
- Abaixo do _Select text language_, selecione **English**.
    
- Sobre o _Select your Azure resource_, selecione o recurso.
    
- Sobre o _Enter your own text, upload a file, or use one of our sample texts_, copie o review abaixo:
	
```txt
Good pizza with slow service
Pizzeria Igarape, Sao Paulo, Brazil
05/13/2019
The service is excellent at the register and at the table. Deliveries are very fast and efficient, however I went to eat there and found it took a long time for my order to come out in the dining room, it wasn't busy and it took a long time.
We went to order from the menu too and there wasn't that option, I was a little disappointed as it was my first visit to the establishment.
```
	
- Confirme a caixa que está ciente que a _demo_ irá incluir usos que podem gerar custos e então selecione **Run**.
    
- Reveja a saída (_output_) e note que foi gerado um relatório sobre o comportamento do cliente com relação a pizzaria:
	
![[text-analize1.png]]
![[text-analyze2.png]]
	
```JSON
{
   "documents": [
       {
           "id": "id__647",
           "sentiment": "mixed",
           "confidenceScores": {
               "positive": 0.64,
               "neutral": 0.02,
               "negative": 0.34
           },
           "sentences": [
               {
                   "sentiment": "positive",
                   "confidenceScores": {
                       "positive": 0.99,
                       "neutral": 0.01,
                       "negative": 0
                   },
                   "offset": 0,
                   "length": 135,
                   "text": "Good pizza with slow service Pizzeria Igarape, Sao Paulo, Brazil 05/13/2019 The service is excellent at the register and at the table. ",
                   "targets": [
                       {
                           "sentiment": "positive",
                           "confidenceScores": {
                               "positive": 1,
                               "negative": 0
                           },
                           "offset": 5,
                           "length": 5,
                           "text": "pizza",
                           "relations": [
                               {
                                   "relationType": "assessment",
                                   "ref": "#/documents/0/sentences/0/assessments/0"
                               }
                           ]
                       },
                       {
                           "sentiment": "negative",
                           "confidenceScores": {
                               "positive": 0.07,
                               "negative": 0.93
                           },
                           "offset": 21,
                           "length": 7,
                           "text": "service",
                           "relations": [
                               {
                                   "relationType": "assessment",
                                   "ref": "#/documents/0/sentences/0/assessments/1"
                               }
                           ]
                       }
                   ],
                   "assessments": [
                       {
                           "sentiment": "positive",
                           "confidenceScores": {
                               "positive": 1,
                               "negative": 0
                           },
                           "offset": 0,
                           "length": 4,
                           "text": "Good",
                           "isNegated": false
                       },
                       {
                           "sentiment": "negative",
                           "confidenceScores": {
                               "positive": 0.07,
                               "negative": 0.93
                           },
                           "offset": 16,
                           "length": 4,
                           "text": "slow",
                           "isNegated": false
                       }
                   ]
               },
               {
                   "sentiment": "positive",
                   "confidenceScores": {
                       "positive": 0.94,
                       "neutral": 0.04,
                       "negative": 0.02
                   },
                   "offset": 135,
                   "length": 183,
                   "text": "Deliveries are very fast and efficient, however I went to eat there and found it took a long time for my order to come out in the dining room, it wasn't busy and it took a long time. ",
                   "targets": [
                       {
                           "sentiment": "positive",
                           "confidenceScores": {
                               "positive": 1,
                               "negative": 0
                           },
                           "offset": 135,
                           "length": 10,
                           "text": "Deliveries",
                           "relations": [
                               {
                                   "relationType": "assessment",
                                   "ref": "#/documents/0/sentences/1/assessments/0"
                               },
                               {
                                   "relationType": "assessment",
                                   "ref": "#/documents/0/sentences/1/assessments/1"
                               }
                           ]
                       },
                       {
                           "sentiment": "negative",
                           "confidenceScores": {
                               "positive": 0.19,
                               "negative": 0.81
                           },
                           "offset": 240,
                           "length": 5,
                           "text": "order",
                           "relations": [
                               {
                                   "relationType": "assessment",
                                   "ref": "#/documents/0/sentences/1/assessments/2"
                               }
                           ]
                       },
                       {
                           "sentiment": "negative",
                           "confidenceScores": {
                               "positive": 0.19,
                               "negative": 0.81
                           },
                           "offset": 265,
                           "length": 11,
                           "text": "dining room",
                           "relations": [
                               {
                                   "relationType": "assessment",
                                   "ref": "#/documents/0/sentences/1/assessments/2"
                               }
                           ]
                       }
                   ],
                   "assessments": [
                       {
                           "sentiment": "positive",
                           "confidenceScores": {
                               "positive": 1,
                               "negative": 0
                           },
                           "offset": 155,
                           "length": 4,
                           "text": "fast",
                           "isNegated": false
                       },
                       {
                           "sentiment": "positive",
                           "confidenceScores": {
                               "positive": 1,
                               "negative": 0
                           },
                           "offset": 164,
                           "length": 9,
                           "text": "efficient",
                           "isNegated": false
                       },
                       {
                           "sentiment": "negative",
                           "confidenceScores": {
                               "positive": 0.19,
                               "negative": 0.81
                           },
                           "offset": 288,
                           "length": 4,
                           "text": "busy",
                           "isNegated": true
                       }
                   ]
               },
               {
                   "sentiment": "negative",
                   "confidenceScores": {
                       "positive": 0,
                       "neutral": 0.01,
                       "negative": 0.99
                   },
                   "offset": 318,
                   "length": 139,
                   "text": "We went to order from the menu too and there wasn't that option, I was a little disappointed as it was my first visit to the establishment.",
                   "targets": [
                       {
                           "sentiment": "negative",
                           "confidenceScores": {
                               "positive": 0,
                               "negative": 1
                           },
                           "offset": 443,
                           "length": 13,
                           "text": "establishment",
                           "relations": [
                               {
                                   "relationType": "assessment",
                                   "ref": "#/documents/0/sentences/2/assessments/0"
                               }
                           ]
                       }
                   ],
                   "assessments": [
                       {
                           "sentiment": "negative",
                           "confidenceScores": {
                               "positive": 0,
                               "negative": 1
                           },
                           "offset": 398,
                           "length": 12,
                           "text": "disappointed",
                           "isNegated": false
                       }
                   ]
               }
           ],
           "warnings": []
       }
   ],
   "errors": [],
   "modelVersion": "2022-11-01"
}
```