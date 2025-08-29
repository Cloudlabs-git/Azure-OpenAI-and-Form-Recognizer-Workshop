# Lab 01: Create and Deploy an Azure AI Document Intelligence Custom Model

### Estimated Duration: 120 Minutes

In this lab, you will create (train) an Azure AI Document Intelligence custom model using a sample training dataset. Custom models extract and analyze distinct data and use cases from forms and documents specific to your business. To create a custom model, you label a dataset of documents with the values you want to extract and train the model on the labeled dataset. You only need five examples of the same form or document type to get started. For this lab, you will use the dataset provided at [Custom Model Sample Files](https://github.com/MSUSAzureAccelerators/Azure-OpenAI-and-Form-Recognizer-Workshop/tree/main/SampleInvoices/Custom%20Model%20Sample).

## Lab Objectives

In this lab, you will complete the following tasks:

* Task 1: Creating an Azure AI Document Intelligence Resource
* Task 2: Train and Label data
* Task 3: Build a new pipeline with the custom model module in BPA
* Task 4: Configure Azure AI Search 

## Task 1: Creating an Azure AI Document Intelligence Resource

In this task, you will create an Azure AI Document Intelligence project using Document Intelligence Studio. You’ll configure the project by selecting a Cognitive Services resource and creating a Storage Account to prepare the environment for custom model training.

1. Open a new tab and navigate to **Document Intelligence Studio** using [Document Intelligence](https://documentintelligence.ai.azure.com/studio). 

1. On the **Sign in to Microsoft Azure** tab, you will see the login screen. Enter the following email/username **(1)**, and click on **Next (2)**. 

   * **Email/Username:** <inject key="AzureAdUserEmail"></inject>

      ![Alt text](../images/9-7-25-g2.png)

1. Now enter the following password **(1)** and click on **Sign in (2)**.
   
   * **Password:** <inject key="AzureAdUserPassword"></inject>

      ![Alt text](../images/9-7-25-g3.png)

      >**Note:** If the sign in pop up does not come up, from the top right corner click on **SignIn** and then sign in.

      ![accounts](../images/1login.png)

1. In Document Intelligence Studio, scroll down to **Custom Models**, under **Custom extraction model**, choose **Get started**.

   ![Alt text](../images/13062025(6).png)

1. On the **Custom extraction model** page, click **+ Create a project** under **My Projects**.

   ![Alt text](images/9-7-25-l1-1.png)

1. On the **Custom extraction models** tab, under **Enter project details**, enter the following details and click on **Continue** **(3)**.
    
   - Project name: **testproject** **(1)**.

   - Description: **Custom model project** **(2)**.

     ![Alt text](images/9-7-25-l1-2.png)

1. On the **Configure service resource** tab, enter the following details and click on **Continue (5)**.

   - Subscription: Select your **Default Subscription** **(1)**.

   - Resource group: **business-process-<inject key="Deployment ID" enableCopy="false"/>** **(2)**.

   - Document Intelligence or Cognitive Service Resource: Select the available Azure AI Search (Cognitive Service) **cogservicesbpass{suffix}** **(3)**.

   - API version: **2024-11-30 (4.0 General Availability)** **(4)**.

        ![Alt text](images/9-7-25-l1-3.png)

1. On the **Connect training data source** tab, enter the following details and click on **Continue** **(8)**.

    - Subscription: Select your **Default Subscription** **(1)**.
   
    - Resource group: **business-process-<inject key="Deployment ID" enableCopy="false"/>** **(2)**.
   
    - Check the box to **Create new storage account** **(3)**
   
    - Storage account name: **formrecognizer<inject key="Deployment ID" enableCopy="false"/>** **(4)**.
   
    - Location: **East US** **(5)**.
   
    - Pricing tier: **Standard_LRS Standard** **(6)**.
   
    - Blob container name: **custommoduletext** **(7)**.
   
      ![](images/9-7-25-l1-4.png)

1. On the **Review and create** tab, validate the information and click **Create project**.

     ![Alt text](images/9-7-25-l1-5.png)
> **Congratulations** on completing the lab! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next  task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help

  <validation step="60c13090-77ec-4831-9df3-a8cf1c72a307" />

## Task 2: Train and Label data

In this task, you will upload and label six training documents to define a custom field for extraction. After labeling, you'll train the Document Intelligence model and validate its accuracy by testing it with sample documents.

1. On the **Label data** page of your custom extraction model project, click **Browse for files** to upload your sample documents.

     ![Browse for files](../images/browsefile.png)

1.  On the file explorer, paste the following path `C:\Users\Public\Desktop\Data\Custom Model Sample` **(1)** hit **enter**, select all train JPEG files **train1 to train6** **(2)**, and click **Open** **(3)**.

     ![train-upload](images/train-upload.png)

1. Once uploaded, in the **Start labeling now** pop-up, select **Run now** under the **Run layout** column.

     ![train-upload](images/run-now.png)

1. On the **Label data** page, click **+ Add a field** **(1)**, then select **Field** **(2)** from the dropdown. Enter the field name as `Organization_sample` **(3)** and press **Enter**.

     ![run-now](images/add-field.png)

     ![run-now](images/add-field-name.png)

1. On the **Label data** page, select the text **CONTOSO** **(1)** from the document preview. From the label dropdown, choose **Organization_sample** **(2)**. Repeat for all six documents.

     ![train-module](images/9-7-25-l1-6.png)

1. On the **Label data** page, after labeling all six documents, click on **Train** in the top right corner.

     ![Train](images/9-7-25-l1-7.png)

1. On the **Train a new model** page, specify the Model ID as **customfrs** **(1)**, Model description as **custom model** **(2)**, from the drop-down select **Template** **(3)** as Build Mode and click on **Train** **(4)**.

     ![Name](images/9-7-25-l1-8.png)

1. On the **Training in progress** dialog opens. click on **Go to Models**

   ![Alt text](images/9-7-25-l1-9.png)

1. On the **Models** page, wait until the **Status** of your model changes to **succeeded** **(1)**. Then, select the model **customfrs** **(2)** and click on **Test** **(3)** from the top menu.

     ![select-models](images/9-7-25-l1-10.png)

1. From the left-side menu, navigate to the **Test model** page and click **Browse for files**.

     ![select-models](images/test-upload.png)

1. On the file explorer, paste the following path `C:\Users\Public\Desktop\Data\Custom Model Sample` **(1)** hit **enter**, select all test JPEG files **test1 and test2** **(2)**, and click **Open** **(3)**.

   ![test-file-upload](./images/test-file-upload.png)

1. On the **Test model** page, Once uploaded, select **test2.jpeg (1)** model, and click on **Run analysis** **(2)**, Now you can see on the right-hand side that the model was able to detect the field **Organization_sample** **(3)** we created in the last step along with its confidence score(*may vary from screenshot)*.

     ![Alt text](../images/test.png)

## Task 3: Build a new pipeline with the custom model module in BPA

In this task, you will create a custom document processing pipeline using the Business Process Automation (BPA) Accelerator. You’ll integrate your trained custom model into the pipeline and upload documents for automated extraction and processing.

1. On the Azure Portal, navigate to the Resource groups and select the resource group **business-process-<inject key="Deployment ID" enableCopy="false"/>**.

    ![Alt text](images/rgg.png)

1. On the **Resource group** page, search, and select the **Static Web App** resource type with the name similar to **webappbpa{suffix}**.

   ![webappbpa](images/9-7-25-l1-11.png)

1. On the **Overview** page of **Static Web App** page, click on **View app in browser**.

      ![webappbpa](images/9-7-25-l1-12.png)

1. Once the **Business Process Automation Accelerator** page loads successfully, scroll down to the section titled **"What would you like to do?"** Under this section, click on the **Create/Update/Delete Pipelines**. 

   ![Web APP](images/9-7-25-l1-13.png)

1. On the **Create Or Select A Pipeline** page, Enter New Pipeline Name as **workshop** **(1)**, and click on the **Create Custom Pipeline** **(2)**. 

   ![workshop](images/9-7-25-l1-14.png)

1. On the **Select a document type to get started** page, select **PDF Document**

   ![workshop](images/image-document.png)

1. On the **Select a stage to add it to your pipeline configuration** page, click on **Form Recognizer Custom Model (Batch)**.

   ![workshop](images/E1-T3-S7.png)

1. On the **Model ID** pop-up. Enter the Form Recognizer Custom Model ID as **customfrs** in the **Model ID** field **(1)**, and then click on **Submit** **(2)**.

   ![Model ID](images/pipeline-model-id.png)

1. On the **Select a stage to add it to your pipeline configuration** page, scroll down to review the **Pipeline Preview**, and click on **Done**.

   ![Pipeline Preview](images/done-pipeline.png)

1. On the **Piplelines workshop** page, click on **Home**. 

     ![home-pipeline](images/9-7-25-l1-15.png)

1. On the **Business Process Automation Accelerator** page, scroll down to the **What would you like to do?** section, then click on **Ingest Documents**.

     ![ingest-documents](images/9-7-25-l1-16.png)

1. On the **Upload a document to Blob Storage** page, from the drop-down, **Select a Pipeline** with the name **workshop** **(1)**, and click on **Upload or drop a file right here (2)**.

     ![Upload a document](images/9-7-25-l1-17.png)

1. For documents, paste the following path `C:\Users\Public\Desktop\Data\Lab 1 Step 3.7` **(1)** and hit enter. Select the invoice files **(2)** and click **Open** **(3)** You can upload multiple invoices one by one.

     ![Upload a document](images/pipeline-folder.png)

## Task 4: Configure Azure AI Search 

In this task, you will configure Azure AI Search to index the extracted document data stored in Azure Blob Storage. You'll define a data source, customize indexing settings, and create an indexer to make the custom model output searchable.

1. Navigate back to the resource group page, select **Search service** with a name similar to **bpa{suffix}**.

   ![search service](images/rg3.png)

1. On the **Search service** page, click on **Import data**. From the **Data Source** dropdown, select **Azure Blob Storage**.

   ![Data source](images/BPAA1.png)

1. On the **Import data** page, under the **Connect to your data** tab, enter the following details:

   - Data Source: Select **Azure Blob Storage** **(1)**

   - Data source name: Enter **workshop** **(2)**.

   - Parsing mode: Select **JSON** **(3)**.

   - Subscription: Select the default Subscription. **(4)**

   - Click on **Choose an existing connection** **(5)** under Connection string.
  
     ![Connection to your data](images/fill-details.png)

1. On the **Storage accounts** page, select the storage account named similar to **bpass{suffix}**. 

     ![Storage account](images/stoarge-account.png)

1. Select **results** **(1)** container from the **Containers** page and click on **Select** **(2)**. It will redirect back to the **Connect to your data** page.

     ![Storage account](images/continers.png)   
  
1. On the **Connect to your data** page, enter the **workshop** **(1)** as **Blob folder** and click on **Next: Add cognitive skills (Optional) (2)**.

   ![Connection](images/fill-details1.png)

1. On the **Add cognitive skills (Optional)** page, leave all settings as default and click **Skip to: Customize target index**.

    ![Data source](images/9-7-25-l1-19.png)

1. On the **Import data** page, enter **Index name** as **azureblob-index** **(1)**, select the check box of all fields **Retrievable** **(2)**, and **Searchable** **(3)**.

      ![Connection](images/9-7-25-l1-20.png)

1. Expand the **aggregatedResult** **(1)** -> **customFormRec (2)** -> **documents** **(3)** -> **fields** **(4)** under it, expand **Organization_sample (5)**. Make the three fields Facetable **(type, valueString & content)** **(6)** and click on **Next: Create an indexer** **(7)**.

   ![import-data](../images/aggregatedresult.png)

1. On the **Create an indexer** page, enter the Name as **azureblob-indexer** **(1)** and click on **Submit** **(2)**.
   
   ![Create an indexer](images/create-an-indexer.png)

> **Congratulations** on completing the lab! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next  task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help

  <validation step="52b89379-3a35-4829-b65b-466fadb99e86" />

## Task 5: Use Sample Search Application [Read Only]

In this task, you will explore the Sample Search Application to verify the results indexed by Azure AI Search. This allows you to view and validate searchable content extracted by your custom model.

1. Navigate back to the **Business Process Automation Accelerator** home page, under the section **What would you like to do?**, click on **Sample Search Application**.

   ![Sample Search Applicationt](images/9-7-25-l1-22.png)

1. On the **Sample Search Application** page, in the search bar, enter **invoice1** **(1)** and click on **Search** **(2)** to view results.

   ![output](images/output.png)

## Summary

In this lab, you’ll build a custom model with Azure AI Document Intelligence by training it on a sample dataset, enabling automated document processing tailored to your data.

Now, click on **Next >>** from the lower right corner to move on to the next lab.

![](../images/next-new.png)
