# Create and Deploy a Form Recognizer Custom Model

### Overview
In this lab, you will create (train) an Azure Form Recognizer custom model using a sample training dataset. Custom models extract and analyze distinct data and use cases from forms and documents specific to your business. To create a custom model, you label a dataset of documents with the values you want extracted and train the model on the labeled dataset. You only need five examples of the same form or document type to get started. For this lab, you will use the dataset provided at [Custom Model Sample Files](/SampleInvoices/Custom%20Model%20Sample/)..


### Goal
* Use a sample training data set to train a custom model in the Azure Form Recognizer Studio
* Label the training data documents with custom fields of interest 
* Test the trained model on test data, visualized results and confidence score in the Studio
* Use the custom model in the BPA pipeline


### Pre-requisites
* The accelerator is deployed and ready in the resource group
* You have an Azure subscription and permission to create a Form Recognizer Resource
* You have access to the sample invoices folder with the invoices to upload


### Instructions

### Step 1 Creating a Form Recognizer Resource

1. Go to the Resource group, search, and select the "**Azure AI services multi-service account**" resource type

   ![Alt text](images/select-multi-service.png)

2. Click on the Document Intelligence tab and select "**Go to Studio**"

   ![Alt text](images/select-document-intelligence.png)

3. In Document Intelligence Studio, scroll down to Custom Models and choose **Create new**.

   ![Alt text](images/custom-models.png)

4. Under My Project click on  **+ Create a project**

   ![Alt text](images/create-a-project.png)

5. Fill in project details and click on **Continue**  **(3)**.
    
   - Project name : **testproject** **(1)**.
   - Description : **Custom model project** **(2)**.

     ![Alt text](images/enter-project-details.png)

6. Fill in details for configuring service resource and click on **Continue** **(5)**.

   - Subscription : **Default Subscription** **(1)**.
   - Resource group : **business-process-<inject key="Deployment ID" enableCopy="false"/>** **(2)**.
   - Form Recognizer or Cognitive Service Resource: Select the available Cognitive Service Form Recognizer name similar to **cogservicesbpass{suffic}** **(3)**.
   - API version : **2022-08-31 (3.0 General Availability)** **(4)**.

     ![configuring service resource](images/configure-service-resource.png)

7. Fill in details for Connect training data source and click on **Continue** **(8)**.

   - Subscription : **Default Subscription** **(1)**.
   - Resource group : **business-process-<inject key="Deployment ID" enableCopy="false"/>** **(2)**.
   - Check the box to **Create new storage account** **(3)**
   - Storage account name : formrecognizer<inject key="Deployment ID" enableCopy="false"/> **(4)**.
   - Location : **East US** **(5)**.
   - Pricing tier : **Standard_LRS Standard** **(6)**.
   - Blob container name : **custommoduletext** **(7)**.
   
        ![storage account](images/connect-training-data-source.png)

8. validate the information and choose **create project**

     ![Alt text](images/create-project.png)

### Step 2 Train and Label data
In this step, you will upload 6 training documents to train the model.

1. Click on **Browse for files** 

     ![Browse for files](images/browse-for-files.png)

2.  On the file explorer enter the following `C:\Users\Public\Desktop\Data\Custom Model Sample` path hit **enter**, select all train JPEG files **train1 thought train6**, and hit **open**.

     ![train-upload](images/train-upload.png)

3. Once uploaded, choose **Run now** in the pop-up window under Run Layout.

     ![train-upload](images/train-upload.png)

4. Click on **+ Add a field** **(1)**, select **Field** **(2)** , enter the field name as **Organization_sample** **(3)** and hit **enter**.

     ![run-now](images/add-field.png)

     ![run-now](images/add-field-name.png)

5. Label the new field added by selecting **CONTOSO LTD** in the top left of each document uploaded. Do this for all the six documents.

     ![train-module](images/train-module.png)

6. Once all the documents are labeled, click on **Train** in the top right corner

     ![Train](images/train-module1.png)

7. Specify the model ID as **customfrs** **(1)**, Model Description as **custom model** **(2)**, from the drop down select **Template** **(3)** as Build Mode, and click on **Train** **(4)**.

     ![Name](images/train-a-new-model.png)

8. Click on **Go to Models**. 

   ![Alt text](images/training-in-progress.png)

9. Wait till the model status shows **succeeded** **(1)**.Once the status  Select the model **customfrs** **(2)** you created and choose **Test** **(3)**.

     ![select-models](images/select-models1.png)

10. In the Test model window, click on **Browse for files**. 

     ![select-models](images/test-upload.png)

11. On the file explorer enter the following `C:\Users\Public\Desktop\Data\Custom Model Sample` path hit **enter**, select all test JPEG files **test1 and test2**, and hit **open**.

     ![test-file-upload](images/test-file-upload.png)

12. Once uploaded, select one test model and click on **Run analysis**, now you can see on the right-hand side, that the model was able to detect the field "Organization_sample" we created in the last step along with its confidence score

     ![Alt text](images/result.png)

### Step 3 Build a new pipeline with the custom model module in BPA

After you are satisfied with the custom model performance, you can retrieve the model ID and use it in a new BPA pipeline with the Custom Model module in the next step.

1. Navigate back to the Resource Group and select the resource group **business-process-<inject key="Deployment ID" enableCopy="false"/>**.

  ![Alt text](images/rg.png.png)

2. Select the static web app and click on the URL

   ![Alt text](<images/static web app.png>)

   ![Alt text](images/image-11.png)

3. Choose Create/Update/Delete Pipelines option and create a new pipeline by specifying a name

   ![Alt text](<images/launch bpa step 5.png>)

   ![Alt text](<images/bpa 2.png>)

4. Select PDF Document

   ![Alt text](images/image-12.png)

5. Select the Form Recognizer custom model (batch) option and specify the model ID you gave in Step 2. 

   ![Alt text](images/image-13.png)

   ![Alt text](images/image-14.png)

Click on Done

   ![Alt text](images/image-15.png)

6. Now you will be ingesting documents by going to the Home page of BPA and choosing the Ingest Documents option.

   ![Alt text](images/image-16.png)

7. From the Select a pipeline drop-down, select the pipeline you just created and click on upload under Upload a single document

   ![Alt text](images/image-17.png)

8. For documents, go to [Lab 1 Step 3.7](/SampleInvoices/Lab%201%20Step%203.7/) folder. You can upload multiple invoice one-by-one.


### Step 4 Configure Azure Cognitive Search 


#### 4.1 Fo back to the resource group window and select Search service

![Alt text](images/image-18.png)

#### 4.2 Click on Import data and select Azure Blog Storage for the Data source option

![Alt text](images/image-20.png)

For connection string, choose an existing connection and select the storage account which was created for you already. Within that, select the results container. For Blob folder, specify the name of the pipeline you created in Step 3 in BPA.

![Alt text](images/image-19.png)

#### 4.3 Click on Add congnitive skills and skip to customize target index. Make all fields Retrievable and Searchable. Expand the documents field and under it, expand fields to make the three fields facetable (type, valueString & content).

![Alt text](images/facetable.png)

#### 4.4 Provide a name for the indexer if not already given and select Submit. You will get a notification that the import is successfully configured

![Alt text](images/image-22.png)

### Step 5 Use Sample Search Application

#### 5.1 Now go back to the BPA webpage and select Sample Search Application

![Alt text](images/image-23.png)

You can now filter and search on items and other fields configured.

![Alt text](<images/sample search app.png>)



## More Resources  
Getting Started with Form Recognizer Studio - https://learn.microsoft.com/en-us/azure/applied-ai-services/form-recognizer/form-recognizer-studio-overview?view=form-recog-3.0.0  
Form Recognizer Documentation - https://learn.microsoft.com/en-us/azure/applied-ai-services/form-recognizer/concept-invoice?view=form-recog-3.0.0