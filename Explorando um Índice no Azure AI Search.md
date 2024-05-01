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

## 3. Create a storage account

1. Retorne novamente para o portal do Azure e selecione novamente o botão **+ Create a resource**.
    
2. Procure por _storage account_, e crie um resurso de **Storage account** com as seguintes configurações:
    - **Subscription**: _Sua inscrição do Azure_.
    - **Resource group**: _Mesmo recurso do Azure AI Search e Azure AI services_.
    - **Storage account name**: etecazurestorage.
    - **Location**: East US.
    - **Performance**: Standard
    - **Redundancy**: Locally redundant storage (LRS)
3. Clique em **Review** e depois em **Create**. Aguarde até que deployment esteja completado e depois volte para a página do armazenamento criado.
	
    ![[azure-storage-account.png]]
4. No **Azure Storage** criado, no canto superior esquerdo da tela, selecione **Configuration** (abaixo do **Settings**).
5. Mude as configurações de _Allow Blob anonymous access_ para **Enabled** e depois selecione **Save**.
## 4. Carregar Documentos para o Azure Storage

1. No canto superior esquerdo da tela, selecione **Containers**.
2. Selecione **+ Container**. Uma página do canto superior direito irá abrir.
3. Digite as seguintes configurações e depois clique em **Create**:
    - **Name**: pizzariareviews
    - **Public access level**: Container (anonymous read access for containers and blobs)
    - **Advanced**: _sem mudanças_.
4. Acesse este repositório na pasta inputs e baixa o arquivo chamado _pizzarias.zip_.
5. No portal do Azure, selecione seu container _pizzaria-reviews_ criado. no container, selecione **Upload**.
	![[storage-blob.png]]
6. Na tela **Upload blob**, selecione **Select a file**.
    
7. Na janela Explorer, selecione **todos** os arquivos da pasta _reviews_, selecione **Open** e depois **Upload**.
	![[pizzaria-container2.png]]
8. Depois que oa arquivo tiverem sido carregados, você pode fechar a página **Upload blob**. Seus documentos agora estarão no armazenamento do container _pizzareviews_.
	
	![[pizzaria-container.png]]

## 5. Indexar os Documentos

Depois de termos criado o armazenamento, vamos usar o **Azure AI Search** para extrair insights e conteúdos dos documentos.

1. Na página do **Azure AI Search**, procure pelo seu recurso do **Azure AI Search**. Na página **Overview**, selecione **Import data**.
    
    [![Screenshot that shows the import data wizard.](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/media/create-cognitive-search-solution/azure-search-wizard-1.png)](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/media/create-cognitive-search-solution/azure-search-wizard-1.png)
    
2. Na página **Connect to your data**, na lista **Data Source**, selecione **Azure Blob Storage**. Complete os dados com as seguintes configurações abaixo:
    - **Data Source**: Azure Blob Storage
    - **Data source name**: pizzaria-customer-data
    - **Data to extract**: Content and metadata
    - **Parsing mode**: Default
    - **Connection string**: *Selecione **Choose an existing connection**. Selecione sua conta de armazenamento, selecione o container **pizzariareviews** e depois clique em **Select**.
    - **Managed identity authentication**: None
    - **Container name**: _esta configuração é auto-populada depois que você escolhe uma conexão existente_.
    - **Blob folder**: _Deixe este campo em branco_.
    - **Description**: Reviews for pizzaria employments.
3. Selecione **Next: Add cognitive skills (Optional)**.
    
4. Na sessão **Attach Cognitive Services**, selecione seu recurso de serviço do Azure AI.
    
5. Na sessão **Add enrichments**:
    - Altere o **Skillset name** para **pizza-skillset**.
    - Selecione a caixa **Enable OCR and merge all text into merged_content field**.
    - Certifique-se de que o **Source data field** está configurado para **merged_content**.
	- Mude o **Enrichment granularity level** para **Pages (5000 character chunks)**.
	- Não selecione _Enable incremental enrichment_
	- Selecione os seguintes campos de enriquecimento:
        
| Cognitive Skill               | Parameter | Field name   |
| ----------------------------- | --------- | ------------ |
| Extract location names        |           | locations    |
| Extract key phrases           |           | keyphrases   |
| Detect sentiment              |           | sentiment    |
| Generate tags from images     |           | imageTags    |
| Generate captions from images |           | imageCaption |
        
6. Sobre o **Save enrichments to a knowledge store**, selecione:
    - Image projections
    - Documents
    - Pages
    - Key phrases
    - Entities
    - Image details
    - Image references
    
	![[storage-import-data.png]]
	
7. Selecione **Azure blob projections: Document**. Uma configuração para o container auto-populado _Container name_ with the _knowledge-store_ aparecerá. **Não mude o nome do container!**
    
8. Selecione **Next: Customize target index**. Mude o **Index name** para **pizza-index**.
    
9. Certifique-se de que a **Key** está configurada para **metadata_storage_path**. Deixe o **Suggester name** em branco e **Search mode** auto-populado.
    
10. Revise o campo de configurações de campo de índice. Selecione **filterable** para todos os campos que já estão selecionados por padrão.
11. Select **Next: Create an indexer**.
    
12. Mude o **Indexer name** para **pizza-indexer**.
    
13. Deixe o **Schedule** configurado para **Once**.
    
14. Expanda o **Advanced options**. Certifique-se de que a opção **Base-64 Encode Keys** está selecionada, pois os codificadores de chaves podem tornar o índice mais eficiente.
    
15. Selecione **Submit** para criar um **data source**, **skillset**, **index**, e **indexer**. O **indexer** é rodado automaticamente e e roda indexando as pipelines que:
    - Extrai os campos de metadados dos documentos e conteúdos dos dados de origem.
    - Roda um conjunto de habilidades do **cognitive skills** para gerar mais campos de enriquecimento.
    - Mapeia os campos extraídos para o índice.
    
    ![[pizarria-index-search.png]]

## 6. Consultar os Índices

Use o **Search explorer** para escrever e testar consultas. Essa ferramente lhe fornece uma maneira fácil de validar a qualidade da sua pesquisa de índice.você pode realizar pesquisas utilizando linguagem **JSON**.

1. Na página de overview da pesquisa, selecione **Search explorer** no topo da tela.
	
	![[azure-search.png]]
	
2. Note que o índice selecionado é o _pizza-index_ que você criou. abaixo do índice selecionado, mude o _view_ para **JSON view**.
3. No campo **JSON query editor**, Copie e cole os seguintes códigos:
	
```JSON
{
 "search": "sentiment:'positive'",
 "count": true
}
```
	
```JSON
{
 "search": "sentiment:'negative'",
 "count": true
}
```
	
1. Uma página irá aparecer semelhante com a abaixo. A linha de código `@odata.count` é a responsável por retornar quantos índices foram encontrados na pesquisa:
	
	![[search-explorer.png]]

## 7. Conclusão

Podemos concluir que, diante do passo-a-passo demonstrado, o serviço de pesquisa cognitiva do **Azure** se mostrou muito preciso no seu propósito, se tornando uma ferramenta muito útil para estabelecimentos e empresas que precisam lidar com um grande volume de dados e, nele, a necessidade de aplicar alguns recursos que sejam de melhor valia (lanchonetes e pizzarias para determinar como se comporta as análises de clientes, por exemplo).
