Neste capítulo, vamos aprender a como utilizar o reconhecimento de imagens do Azure AI Vision.

## 1. Detecção de faces no Vision Studio

O serviço de detecção de imagens do Azure permite que você consiga detectar pessoas através da ferramenta Vision AI Studio. Abaixo, o passo-a-passo de como realizar as configurações:

1. Acesse o [https://portal.azure.com](https://portal.azure.com?azure-portal=true), logando com sua conta Azure da Microsoft.
    
2. Clique em **＋Create a resource** e procure por _Azure AI services_. Selecione **create** para iniciar a criação da assinatura. Configure-a com os seguintes pontos:
    - **Subscription**: _ETEC_Azure_ML_ (ou sua assinatura do Azure).
    - **Resource group**: ETEC_Azure_ML
    - **Region**: East US.
    - **Name**: Azure-AI-Vision-ETEC
    - **Pricing tier**: _Standard S0._
    - **By checking this box I acknowledge that I have read and understood all the terms below**: _Selecionado_.
3. Selecione **Review + create** e depois em **Create** para aguardar que o recurso seja criado

## 2. Conectando seu recurso do Azure AI service ao Vision Studio

Agora, vamos nos conectar em outro portal do Azure para iniciarmos os procedimentos dos recursos do **Vision AI Studio**. Nesta etapa, vamos começar iniciando o processo de detecção de faces no **Vision Studio**.

1. Acesse o **Vision Studio** em [https://portal.vision.cognitive.azure.com](https://portal.vision.cognitive.azure.com?azure-portal=true).
    
2. Logue com a mesma conta que você criou o recurso no portal do Azure.
	
3. Com o Vision Studio aberto, clique em **View all resources** abaixo do cabeçalho **Getting started with Vision**.
![[vision-resources.png]]
4. Com a página dos recursos aberta, selecione o recurso que foi criado anteriormente e clique em **Select as default resource**.
![[Pasted image 20240430023722.png]]
5. Volte para a página anterior e selecione a aba **Face** e clique em **Detect Faces in an image**.
    
6. Selecione a opção **Browse for a file** e selecione uma imagem de preferência. O resultado (dependendo da imagem) será igual ao abaixo:
![[face_recognition.png]]
```JSON
[
    {
        "Face": 1,
        "Face mask": "no"
    },
    {
        "recognitionModel": "recognition_01",
        "faceRectangle": {
            "width": 113,
            "height": 144,
            "left": 317,
            "top": 93
        },
        "faceLandmarks": {
            "pupilLeft": {
                "x": 365.1,
                "y": 153.9
            },
            "pupilRight": {
                "x": 411.2,
                "y": 152.5
            },
            "noseTip": {
                "x": 400,
                "y": 188.1
            },
            "mouthLeft": {
                "x": 355.3,
                "y": 196.4
            },
            "mouthRight": {
                "x": 405.2,
                "y": 195.9
            },
            "eyebrowLeftOuter": {
                "x": 344.6,
                "y": 147.1
            },
            "eyebrowLeftInner": {
                "x": 384.3,
                "y": 147.5
            },
            "eyeLeftOuter": {
                "x": 356.9,
                "y": 154.1
            },
            "eyeLeftTop": {
                "x": 365.5,
                "y": 152.1
            },
            "eyeLeftBottom": {
                "x": 365.5,
                "y": 155.6
            },
            "eyeLeftInner": {
                "x": 372.6,
                "y": 153.7
           },
           "eyebrowRightInner": {
               "x": 405.7,
               "y": 146.9
           },
           "eyebrowRightOuter": {
               "x": 426.5,
               "y": 141.5
           },
           "eyeRightInner": {
               "x": 404.1,
               "y": 153.2
           },
           "eyeRightTop": {
               "x": 411.5,
               "y": 150.6
           },
           "eyeRightBottom": {
               "x": 411.5,
               "y": 154
           },
           "eyeRightOuter": {
               "x": 417.8,
               "y": 152.1
           },
           "noseRootLeft": {
               "x": 385.9,
               "y": 156.7
           },
           "noseRootRight": {
               "x": 400.4,
               "y": 157.1
           },
           "noseLeftAlarTop": {
               "x": 381.7,
               "y": 174.5
           },
           "noseRightAlarTop": {
               "x": 405,
               "y": 173.6
           },
           "noseLeftAlarOutTip": {
               "x": 374.5,
               "y": 182.5
           },
           "noseRightAlarOutTip": {
               "x": 407.8,
               "y": 181.6
           },
           "upperLipTop": {
               "x": 390.5,
               "y": 198.7
           },
           "upperLipBottom": {
               "x": 389.1,
               "y": 202.5
           },
            "underLipTop": {
               "x": 387.7,
               "y": 210.8
           },
           "underLipBottom": {
               "x": 386.6,
               "y": 217.5
           }
       },
       "faceAttributes": {
           "mask": {
               "type": "noMask",
               "noseAndMouthCovered": false
           }
       }
   }
]
```

## 3. ## Extrair textos de imagens no Vision Studio

Agora vamos realizar a extração de textos dentro de imagens com o **Vision AI Studio**.

1. Volte para a página anterior, selecione a aba **Opticam Character Recognition**.
    
2. Clique novamente em **Browse for a File** para carregar uma imagem e aguarde até o sistema terminar. Uma mensagem similar a abaixo será apresentada:

![Diga não as drogas](https://github.com/AlberthADS/MS_Azure_AI900_Diome/blob/main/Inputs/img-22.jpg?raw=true)

```JSON
[
   {
       "DROGAS EU TÔ FORA,PEGO MINHA
       BIKE
       E VOU EMBORA
       SEJA DIFERENTE,DROGASN ÃO
       AhNegão.com.br"
   },
   {
       "lines": [
           {
               "text": "DROGAS EU TÔ FORA, PEGO MINHA",
               "boundingPolygon": [
                   {
                       "x": 42,
                       "y": 124
                   },
                   {
                       "x": 467,
                       "y": 114
                   },
                   {
                       "x": 469,
                       "y": 175
                   },
                   {
                       "x": 45,
                       "y": 186
                   }
               ],
               "words": [
                   {
                       "text": "DROGAS",
                       "boundingPolygon": [
                           {
                               "x": 43,
                               "y": 133
                           },
                           {
                               "x": 130,
                               "y": 125
                           },
                           {
                               "x": 134,
                               "y": 186
                           },
                           {
                               "x": 47,
                               "y": 185
                           }
                       ],
                       "confidence": 0.99
                   },
                   {
                       "text": "EU",
                       "boundingPolygon": [
                           {
                               "x": 142,
                               "y": 124
                           },
                           {
                               "x": 170,
                               "y": 121
                           },
                           {
                               "x": 174,
                               "y": 186
                           },
                           {
                               "x": 146,
                               "y": 186
                           }
                       ],
                       "confidence": 0.989
                   },
                   {
                       "text": "TÔ",
                       "boundingPolygon": [
                           {
                               "x": 182,
                               "y": 121
                           },
                           {
                               "x": 206,
                               "y": 119
                           },
                           {
                               "x": 209,
                               "y": 186
                           },
                           {
                               "x": 186,
                               "y": 186
                           }
                       ],
                       "confidence": 0.877
                   },
                   {
                       "text": "FORA,",
                       "boundingPolygon": [
                           {
                               "x": 218,
                               "y": 118
                           },
                           {
                               "x": 290,
                               "y": 116
                           },
                           {
                               "x": 293,
                               "y": 183
                           },
                           {
                               "x": 221,
                               "y": 186
                           }
                       ],
                       "confidence": 0.95
                   },
                   {
                       "text": "PEGO",
                       "boundingPolygon": [
                           {
                               "x": 302,
                               "y": 116
                           },
                           {
                               "x": 362,
                               "y": 115
                           },
                           {
                               "x": 365,
                               "y": 178
                           },
                            {
                               "x": 305,
                               "y": 182
                           }
                       ],
                       "confidence": 0.986
                   },
                   {
                       "text": "MINHA",
                       "boundingPolygon": [
                           {
                               "x": 374,
                               "y": 115
                           },
                           {
                               "x": 466,
                               "y": 118
                           },

                           {
                               "x": 468,
                               "y": 169
                           },
                           {
                               "x": 376,
                               "y": 177
                           }
                       ],
                       "confidence": 0.994
                   }
               ]
           },
           {
               "text": "BIKE",
               "boundingPolygon": [
                   {
                       "x": 47,
                       "y": 202
                   },
                   {
                       "x": 138,
                       "y": 197
                   },
                   {
                       "x": 141,
                       "y": 236
                   },
                   {
                       "x": 49,
                       "y": 242
                   }
               ],
               "words": [
                   {
                       "text": "BIKE",
                       "boundingPolygon": [
                           {
                               "x": 47,
                               "y": 202
                           },
                           {
                               "x": 134,
                               "y": 197
                           },
                           {
                               "x": 136,
                               "y": 237
                           },
                           {
                               "x": 49,
                               "y": 242
                           }
                       ],
                       "confidence": 0.988
                   }
               ]
           },
           {
               "text": "E VOU EMBORA",
               "boundingPolygon": [
                   {
                       "x": 221,
                       "y": 191
                   },
                   {
                       "x": 467,
                       "y": 181
                   },
                   {
                       "x": 469,
                       "y": 223
                   },
                   {
                       "x": 221,
                       "y": 233
                   }
               ],
               "words": [
                   {
                       "text": "E",
                       "boundingPolygon": [
                           {
                               "x": 221,
                               "y": 192
                           },
                           {
                               "x": 240,
                               "y": 191
                           },
                           {
                               "x": 241,
                               "y": 233
                           },
                           {
                               "x": 222,
                               "y": 233
                           }
                       ],
                       "confidence": 0.994
                   },
                   {
                       "text": "VOU",
                       "boundingPolygon": [
                           {
                               "x": 249,
                               "y": 190
                           },
                           {
                               "x": 314,
                               "y": 187
                           },
                           {
                               "x": 316,
                               "y": 231
                           },
                           {
                               "x": 250,
                               "y": 233
                           }
                       ],
                       "confidence": 0.998
                   },
                   {
                       "text": "EMBORA",
                       "boundingPolygon": [
                           {
                               "x": 329,
                               "y": 187
                           },
                           {
                               "x": 466,
                               "y": 181
                           },
                           {
                               "x": 469,
                               "y": 220
                           },
                           {
                               "x": 330,
                               "y": 231
                           }
                       ],
                       "confidence": 0.995
                   }
               ]
           },
           {
               "text": "SEJA DIFERENTE, DROGAS NÃO",
               "boundingPolygon": [
                   {
                       "x": 261,
                       "y": 249
                   },
                   {
                       "x": 466,
                       "y": 239
                   },
                   {
                       "x": 467,
                       "y": 254
                   },
                   {
                       "x": 262,
                       "y": 263
                   }
               ],
               "words": [
                   {
                       "text": "SEJA",
                       "boundingPolygon": [
                           {
                               "x": 263,
                               "y": 249
                           },
                           {
                               "x": 293,
                               "y": 249
                           },
                           {
                               "x": 294,
                               "y": 262
                           },
                           {
                               "x": 263,
                               "y": 263
                           }
                       ],
                       "confidence": 0.989
                   },
                   {
                       "text": "DIFERENTE,",
                       "boundingPolygon": [
                           {
                               "x": 298,
                               "y": 248
                           },
                           {
                               "x": 377,
                               "y": 245
                           },
                           {
                               "x": 377,
                               "y": 258
                           },
                           {
                               "x": 299,
                               "y": 261
                           }
                       ],
                       "confidence": 0.99
                   },
                   {
                       "text": "DROGAS",
                       "boundingPolygon": [
                           {
                               "x": 380,
                               "y": 245
                           },
                           {
                               "x": 433,
                               "y": 242
                           },
                           {
                               "x": 433,
                               "y": 256
                           },
                           {
                               "x": 380,
                               "y": 258
                           }
                       ],
                       "confidence": 0.994
                   },
                   {
                       "text": "NÃO",
                       "boundingPolygon": [
                           {
                               "x": 437,
                               "y": 242
                           },
                           {
                               "x": 463,
                               "y": 240
                           },
                           {
                               "x": 463,
                               "y": 255
                           },
                           {
                               "x": 438,
                               "y": 256
                           }
                       ],
                       "confidence": 0.979
                   }
               ]
           },
           {
               "text": "AhNegão.com.br",
               "boundingPolygon": [
                   {
                       "x": 390,
                       "y": 345
                   },
                   {
                       "x": 492,
                       "y": 345
                   },
                   {
                       "x": 493,
                       "y": 360
                   },
                   {
                       "x": 390,
                       "y": 360
                   }
               ],
               "words": [
                   {
                       "text": "AhNegão.com.br",
                       "boundingPolygon": [
                           {
                               "x": 392,
                               "y": 345
                           },
                           {
                               "x": 493,
                               "y": 345
                           },
                           {
                               "x": 492,
                               "y": 360
                           },
                           {
                               "x": 392,
                               "y": 361
                           }
                       ],
                       "confidence": 0.989
                   }
               ]
           }
       ]
   }
]
```

## 4. # Analisar imagens no Vision Studio

Por último, iremos utilizar o recurso de análise de contexto de imagens do **Vision AI Studio**. Com ele, é possível extrairmos o que possivelmente uma imagem está "dizendo".

Volte para a página anterior, selecione a aba **Image Analysis** e selecione a opção **Add Captions to Images**.
    
2. Clique novamente em **Browse for a File** para carregar uma imagem e aguarde até o sistema terminar. Uma mensagem similar a abaixo será apresentada:

![Homem-aranha no violão](https://github.com/AlberthADS/MS_Azure_AI900_Diome/blob/main/Inputs/6-1.jpg?raw=true)

```JSON
[
   {
       "a man in a garment playing a guitar"
   },
   {
       "apim-request-id": "a51503e3-91b5-46f9-840e-42d5d83bfe4e",
       "content-length": "162",
       "content-type": "application/json; charset=utf-8",
       "modelVersion": "2023-10-01",
       "captionResult": {
           "text": "a man in a garment playing a guitar",
           "confidence": 0.8545867800712585
       },
       "metadata": {
           "width": 450,
           "height": 600
       }
   }
]
```

## 5. Resultados

Podemos concluir que as ferramentas de detecção de imagens da Microsoft se mostraram muito assertivas com relação a cada conteúdo inserido nela. A taxa de acerto do muito próxima aos 100% e demonstra como ela possui mais margens para melhorias.
