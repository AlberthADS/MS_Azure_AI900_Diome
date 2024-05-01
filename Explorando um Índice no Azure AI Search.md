Neste tutorial, vamos aprender a como utilizar o mecanismo de pesquisa cognitiva do **Azure AI**. Ela é essencial para quando se é preciso lidar com grandes quantidades de documentos que foram digitalizados e que necessitam ser pesquisados. Além, também, de colher resultados de sentimentos e leituras de imagens utilizando o **Optical Character Recognition**.

Vamos precisar acessar apenas o [portal do Azure](https://portal.azure.com/#home) para utilizar os recursos deste tutorial.

## 1. Criando um recurso do Azure AI Search

1. Logue no [portal do Azure](https://portal.azure.com/learn.docs.microsoft.com?azure-portal=true).
    
2. Clique no botão **+ Create a resource**, procure por _Azure AI Search_, e crie um recurso **Azure AI Search** com as seguintes configuraçõs:
    
    - **Subscription**: _Sua inscrição do Azure_.
    - **Resource group**: ETEC_Azure_AI900 _ou alguma outra de interesse que seja única_.
    - **Service name**: etecazureaisearch.
    - **Location**: East US.
    - **Pricing tier**: Basic
3. Selecione **Review + create**, e depois verá uma resposta de validação escrita **Validation Success**, selecione **Create**.
    
4. Depois, vá em **Go to resource**. Na página de overview do Azure AI Search, você pode adicionar índices, importar dados, e procurar por índices de buscas já criadas.
	
	![[azure-search-service.png]]

## 2. Criando um recurso de serviço do Azure AI

Você irá precisar providenciar um resurso do **Azure AI services** que esteja na mesma localização do seu recurso do Azure AI Search criado anteriormente.

1. Retorne para a página principal do Azure portal. Clique no botão **＋Create a resource** e procure por _Azure AI services_. Selecione o plano **create an Azure AI services**. Você será levado para uma página para criar um serviço do recurso do Azure AI . Faça as seguintes configurações:
    - **Subscription**: _Sua inscrição do Azure_.
    - **Resource group**: _Mesmo grupo criado no Azure AI Resources_.
    - **Region**: _Mesma localização do Azure AI Resources_.
    - **Name**: etecazureservice.
    - **Pricing tier**: Standard S0
    - **By checking this box I acknowledge that I have read and understood all the terms below**: Selecionado.
2. Selecione **Review + create**. depois de passar pela validação, selecione **Create**.
    
3. Aguarde até que o deployment seja terminado.
	
	![[azure-ai-services.png]]


![[azure-storage-account.png]]![[storage-import-data.png]]

![[search-explorer.png]]![[pizzaria-container.png]]

![[pizzaria-container2.png]]![[pizarria-index-search.png]]

![[azure-search.png]]

