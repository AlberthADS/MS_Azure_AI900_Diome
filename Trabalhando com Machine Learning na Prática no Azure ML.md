## 1. ## Use automated machine learning to train a model

- No [Azure Machine Learning studio](https://ml.azure.com?azure-portal=true), clicar na opção **Automated ML** (dentro da guia **Authoring**).
    
- Após isso, seguir o passo-a-passo usando as opções abaixo:
    
    **Configurações básicas**:
    
    - **Job name**: mslearn-diabetes-automl
    - **New experiment name**: mslearn-diabetes-pred
    - **Description**: Automated machine learning for diabetes' people.
    - **Tags**: _none_
    
    **Tipo de Tarefa & Data**:
    
    - **Selecionar tipo de tarefa**: Regression
        
    - **Select dataset**: Cria um novo conjunto de dados com as seguintes configurações:
        
        - **Data type**:
            - **Name**: diabetes-pred
            - **Description**: Prediction about diabetes people
            - **Type**: Tabular
        - **Data source**:
            - Selecionar **From web files**
        - **Web URL**:
            - **Web URL**: `https://raw.githubusercontent.com/AlberthADS/MS_Azure_AI900_Diome/main/diabete_prediction.csv`
            - **Skip data validation**: _do not select_
        - **Settings**:
            - **File format**: Delimited
            - **Delimiter**: Comma
            - **Encoding**: UTF-8
            - **Column headers**: Only first file has headers
            - **Skip rows**: None
            - **Dataset contains multi-line data**: _do not select_
        - **Schema**:
            - Include all columns other than **Path**
            - Review the automatically detected types
        
        Selecionar **Create**. Depois que o conjunto de doados for criado, selecione o conjunto de dados **diabetes-pred** para continuar e iniciar a automação de trabalho do ML.
        
    
    **Configurações de tarefas**:
    
    - **Task type**: Regression
    - **Dataset**: bike-rentals
    - **Target column**: Rentals (integer)
    - **Additional configuration settings**:
        - **Primary metric**: Normalized root mean squared error
        - **Explain best model**: _Unselected_
        - **Use all supported models**: Não selecionado.
        - **Allowed models**: _Selecionar somente o **RandomForest** e **LightGBM**._
    - **Limits**: _Expandir a sessão_
        - **Max trials**: 3
        - **Max concurrent trials**: 3
        - **Max nodes**: 3
        - **Metric score threshold**: 0.085
        - **Timeout**: 15
        - **Iteration timeout**: 15
        - **Enable early termination**: _Selected_
    - **Validation and test**:
        - **Validation type**: Train-validation split
        - **Percentage of validation data**: 10
        - **Test dataset**: None
    
    **Computação**:
    
    - **Select compute type**: Serverless
    - **Virtual machine type**: CPU
    - **Virtual machine tier**: Dedicated
    - **Virtual machine size**: Standard_DS3_V2*
    - **Number of instances**: 1

## 2. Implantar o modelo e endpoint

Depois de iniciado a instância, começaremos agora a criar o modelo e o _endpoint_ do projeto.

- No [Azure Machine Learning studio](https://ml.azure.com?azure-portal=true), clicar na opção **Models** (dentro da guia **Assets**).
	
    **Configurações básicas do Modelo**:
    
    Selecionar a opção **Register** e depois **From a Job output**.
	
	- **Select Job**: mslearn-diabetes-automl
	
	**Select Output**
	- **Model Type:** MLflow
	- **Job Output:** best_model

	**Model Settings**
	**Name:** Diabetes_Predicion_ML
	**Description:** Prediction model for Diabetes' prediction
	**Version:** 1
	
	Revise as opções e finalize para que o modelo seja criado com base no aprendizado já criado.

	**Configurações básicas do endpoint**:

	Selecionar a opção **Register** e depois selecione o modelo **Diabetes_Predicion_ML**.

	Implantar o **Diabetes_Predicion_ML:1**
	
	- **Virtual machine**: Standard_DS1_v2
	- **Instance count**: 3
	- **Endpoint**: New
	- Endpoint name: etec-azure-ml-lab-xcgdc
	- **Deployment name**: diabetes-predicion-ml-1
	- **Inferencing data collection**: Disabled
	- **Package Model**: Disabled

	Aguarde entre 15 minutos para que o endpoint tenha finalizado.

## 3. ## Testando o serviço implementado

Vamos agora testar o nosso serviço implementado.

1. No Azure Machine Learning studio, selecione novamente o **Endpoints** abra o endpoint criado **etec-azure-ml-lab-xcgdc**.
    
2. Dentro do **Endpoint**, selecione a aba **Test** e na opção **Deployment**, selecione **diabetes-predicion-ml-1**.
    
3. Dentro da aba de testes, colamos o código abaixo e clicamos depois em "**Test**":
```json
{
  "input_data": {
    "columns": [
      "PatientID",
      "Pregnancies",
      "DiastolicBloodPressure",
      "TricepsThickness",
      "SerumInsulin",
      "BMI",
      "DiabetesPedigree",
      "Age"
    ],
    "index": [0, 1, 2],
    "data": [
      [1, 9, 51, 7, 24, 27.36983156, 1.350472047, 43],
      [2, 6, 61, 35, 24, 18.74367404, 1.074147566, 75],
      [3, 4, 50, 29, 243, 34.69215364, 0.741159926, 59]
    ]
  }
}
```
4. O resultado será apresentado igual a imagem abaixo:

![https://github.com/AlberthADS/MS_Azure_AI900_Diome/blob/main/prediction_result.png](https://raw.githubusercontent.com/AlberthADS/MS_Azure_AI900_Diome/main/prediction_result.png)
