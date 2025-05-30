# Lab 01: Create and Deploy a Azure AI Document Intelligence Custom Model

In this lab, you will create (train) an Azure AI Document Intelligence custom model using a sample training dataset. Custom models extract and analyze distinct data and use cases from forms and documents specific to your business. To create a custom model, you label a dataset of documents with the values you want to extract and train the model on the labeled dataset. You only need five examples of the same form or document type to get started. For this lab, you will use the dataset provided at [Custom Model Sample Files](/SampleInvoices/Custom%20Model%20Sample/).

## Estimated Duration: 90 minutes

## Lab Objectives

In this lab, you will complete the following tasks:

* Task 1: Creating an Azure AI Document Intelligence Resource
* Task 2: Train and Label data
* Task 3: Build a new pipeline with the custom model module in BPA
* Task 4: Configure Azure AI Search 

### Task 1: Creating an Azure AI Document Intelligence Resource

1. Open a new tab and navigate to Document Intelligence Studio using `https://documentintelligence.ai.azure.com/studio`. 

2. When prompted, enter the following Email ID and Password.

    - **Email/Username**: <inject key="AzureAdUserEmail"></inject>
    - **Password**: <inject key="AzureAdUserPassword"></inject>

3. In Document Intelligence Studio, scroll down to Custom Models, under **Custom extraction model** choose **Get started**.

   ![Alt text](images/getstarted.png)

5. Under My Project, click on **+ Create a project**.

   ![Alt text](images/pg1-task1-4.png)

6. Enter the following details and click on **Continue**  **(3)**.
    
   - Project name: **testproject** **(1)**.
   - Description: **Custom model project** **(2)**.

     ![Alt text](images/enter-project-details.png)

7. Enter the following details **Configure service resource** and click on **Continue**.

   - Subscription: Select your **Default Subscription** **(1)**.
   - Resource group: **business-process-<inject key="Deployment ID" enableCopy="false"/>** **(2)**.
   - Document Intelligence or Cognitive Service Resource: Select the available Azure AI Search (Cognitive Service) **cogservicesbpass{suffix}** **(3)**.
   - API version: **2022-08-31 (3.0 General Availability)** **(4)**.

        ![storage account](images/Formai1.png)

8. Enter the following details **Connect training data source** and click on **Continue** **(8)**.

   - Subscription: Select your **Default Subscription** **(1)**.
   - Resource group: **business-process-<inject key="Deployment ID" enableCopy="false"/>** **(2)**.
   - Check the box to **Create new storage account** **(3)**
   - Storage account name: **formrecognizer<inject key="Deployment ID" enableCopy="false"/>** **(4)**.
   - Location: **East US** **(5)**.
   - Pricing tier: **Standard_LRS Standard** **(6)**.
   - Blob container name: **custommoduletext** **(7)**.
   
     ![](images/connect-training-data-source.png)

9. Validate the information and choose **Create project**.

     ![Alt text](images/create-project.png)

### Task 2: Train and Label data

In this step, you will upload 6 training documents to train the model.

1. Click on **Browse for files**.

     ![Browse for files](images/browse-for-files.png)

2.  On the file explorer, paste the following path `C:\Users\Public\Desktop\Data\Custom Model Sample` **(1)** hit **enter**, select all train JPEG files **train1 to train6** **(2)**, and hit **Open** **(3)**.

     ![train-upload](images/train-upload.png)

3. Once uploaded, choose **Run now** in the pop-up window under Run Layout.

     ![train-upload](images/run-now.png)

4. Click on **+ Add a field** **(1)**, select **Field** **(2)**, enter the field name as **Organization_sample** **(3)** and hit **enter**.

     ![run-now](images/add-field.png)

     ![run-now](images/add-field-name.png)

5. Label the new field added by selecting **CONTOSO LTD** in the top left of each document uploaded. Do this for all six documents.

     ![train-module](images/train-module.png)

6. Once all the documents are labeled, click on **Train** in the top right corner.

     ![Train](images/train-module1.png)

7. Specify the model ID as **customfrs** **(1)**, Model Description as **custom model** **(2)**, from the drop-down select **Template** **(3)** as Build Mode and click on **Train** **(4)**.

     ![Name](images/train-a-new-model.png)

8. Click on **Go to Models**. 

   ![Alt text](images/training-in-progress.png)

9. Wait till the model status shows **succeeded** **(1)**. Once the status Select the model **customfrs** **(2)** you created and choose **Test** **(3)**.

     ![select-models](images/select-models1.png)

10. On the Test model window, click on **Browse for files**. 

     ![select-models](images/test-upload.png)

11. On the file explorer, paste the following path `C:\Users\Public\Desktop\Data\Custom Model Sample` **(1)** hit **enter**, select all test JPEG files **test1 and test2** **(2)**, and hit **Open** **(3)**.

     ![test-file-upload](images/test-file-upload.png)

12. Once uploaded, select **test2.jpeg (1)** model, and click on **Run analysis** **(2)**, Now you can see on the right-hand side that the model was able to detect the field **Organization_sample** **(3)** we created in the last step along with its confidence score.

     ![Alt text](images/result.png)

### Task 3: Build a new pipeline with the custom model module in BPA

After you are satisfied with the custom model performance, you can retrieve the model ID and use it in a new BPA pipeline with the Custom Model module in the next step.

1. On the Azure Portal, Navigate to the Resource groups and select the resource group **business-process -<inject key="Deployment ID" enableCopy="false"/>**.

    ![Alt text](images/rgg.png)

2. Go to the Resource group, search, and select the **Static Web App** resource type with the name similar to **webappbpa{suffix}**.

   ![webappbpa](images/static-web-page.png)

3. On the **Static Web App** page, click on **View app in browser**.

      ![webappbpa](images/formm.png)

4. Once the **Business Process Automation Accelerator** page loaded successfully, click on the **Create/Update/Delete Pipelines**. 

   ![Web APP](images/select-create-pipeline.png)

5. On the **Create Or Select A Pipeline** page, enter New Pipeline Name as **workshop** **(1)**, and click on the **Create Custom Pipeline** **(2)**. 

   ![workshop](images/create-pipeline.png)

6. On the **Select a document type to get started** page, select **PDF Document**

   ![workshop](images/image-document.png)

7. On the **Select a stage to add it to your pipeline configuration** page, search and select for **Form Recognizer Custom Model (Batch)**.

   ![workshop](images/E1-T3-S7.png)

8. On the pop-up, enter the Model ID as **customfrs** **(1)** and click on **Submit** **(2)**. 

   ![Model ID](images/pipeline-model-id.png)

9. On the **Select a stage to add it to your pipeline configuration** page, scroll down to review the **Pipeline Preview**, and click on **Done**.

   ![Pipeline Preview](images/done-pipeline.png)

10. On the **Piplelines workshop** page, click on **Home**. 

      ![home-pipeline](images/home-pipeline.png)

11. On the **Business Process Automation Accelerator** page, click on **Ingest Documents**.

      ![ingest-documents](images/ingest-documents.png)

12. On the **Upload a document to Blob Storage** page, from the drop-down select a Pipeline with the name **workshop** **(1)**, and click on **Upload or drop a file right here**.

      ![Upload a document](images/recogniserlab1-1.png)

13. For documents, paste the following path `C:\Users\Public\Desktop\Data\Lab 1 Step 3.7` **(1)** and hit enter. You can upload multiple invoices one by one.

      ![Upload a document](images/pipeline-folder.png)

### Task 4: Configure Azure AI Search 

1. Navigate back to the resource group window, search, and select **Search Service** with a name similar to **bpa{suffix}**.

   ![search service](images/rg3.png)

2. On the **Search service** page, click on **Import data**.

   ![Data source](images/BPAA1.png)

3. Enter the following details for **Connect to your data**.

   - Data Source: Select **Azure Blob Storage** **(1)**
   - Data Source Name: Enter **workshop** **(2)**.
   - Parsing mode: Select **JSON** **(3)**.
   - Subscription: Select the default Subscription. **(4)**
   - Click on **Choose an existing connection** **(5)** under Connection string.
  
     ![Connection to your data](images/fill-details.png)

4. On the **Storage accounts** page, select the storage account named similar to **bpass{suffix}**. 

     ![Storage account](images/stoarge-account.png)

5. Select **results** **(1)** container from the **Containers** page and click on **Select** **(2)**. It will redirect back to **Connection to your data** page.

     ![Storage account](images/continers.png)   
  
6. On the **Connect to your data** page, enter the **workshop** **(1)** as **Blob folder** and click on **Next : Add cognitive skills (Optional) (2)**.

   ![Connection](images/fill-details1.png)

7. On the **Add cognitive skills (Optional)** click on **Skip to : Customize target index**.

8. On the **Customize target index**, enter Index name as **azureblob-index** **(1)**, make all fields **Retrievable** **(2)**, and **Searchable** **(3)**.

      ![Connection](images/retrievable-searchable.png)

9. Expand the **aggregatedResults** **(1)** > **customFormRec** **(2)** > **documents** **(3)** > **fields** **(4)** under it, expand **Organization_sample (5)**. Make the three fields Facetable **(type, valueString & content)** **(6)** and click on **Next: Create an indexer** **(7)**.

      ![import-data](images/BPA5.png)

7. On the **Create an indexer** page, enter the name as **azureblob-indexer** **(1)** and click on **Submit** **(2)**.
   
   ![Create an indexer](images/create-an-indexer.png)

## Summary

In this hands-on lab, you will create a custom model with Azure AI Document Intelligence using a sample training dataset.

## You have successfully completed this lab.
