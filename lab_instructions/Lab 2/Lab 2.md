# Use Azure OpenAI with your own data

### Overview
In this lab, you will be using your own data with Azure OpenAI Large Language Models (LLM), which will be made searchable using Azure Cognitive Search. You will be using the Porche Owner's Manual pdf provided under the [Lab 2](/SampleInvoices/Lab%202/) folder.

### Goal
* How to leverage the ChatGPT LLM to extract a concise summary from your own document repository using OpenAI.

### Pre-requisites
* Access to Azure OpenAI chat playground.
* Sample data to test with OpenAI.

### Instructions

### Task 1: Navigate to Azure OpenAI Playground

Access the Azure OpenAI Studio and navigate to the "Bring your own data" section.

1. Navigate back to the Resource groups and select the resource group **business-process-<inject key="Deployment ID" enableCopy="false"/>**.

   ![OpenAI](images/rgg.png)

2. On the Resource group, search, and select the **Azure OpenAI (1)** resource type with a name similar to **Copilot-OpenAI-<inject key="Deployment ID" enableCopy="false"/> (2)**.

   ![OpenAI](images/03-07-2024.png)

3. On the **Azure OpenAI** page, click on **Go to Azure OpenAI Studio**.

   ![OpenAI Studio](images/open-studiolink.png)

4. On the **Azure OpenAI Studio**, scroll down click on **Bring your own data**.

   ![Azure OpenAI Studio](images/byod.png)

### Task 2: Upload your own data

In this task, we will be using Porche's owner manual for the Taycan, Panamera, and Cayenne models.

1. Fill the following details in **Add a data source** under **Add your data** tab and click on **Next** **(6)**.
    
    - Select data source: **Upload files (preview)** **(1)**

    - Subscription: Select your subscription from the drop-down section **(2)**

    - Select Azure Blob storage resource: Choose the already created storage account from the drop-down **copilotstorage<inject key="Deployment ID" enableCopy="false"/>** **(3)**. If asked, enable CORS.

    - Select Azure Cognitive Search resource: Select the search service from the drop-down **acs-<inject key="Deployment ID" enableCopy="false"/>** **(4)**.

    - Enter the index name: Give an index name as **aoaiworkshop** **(5)**
  
      ![add-data source](images/add-datasrc.png)

      ![add-data](images/bring-your-owndata-datasource.png) 

2. On the **Data Management**, click on **Browse for a file** **(1)** enter the following `C:\Users\Public\Desktop\Data\Lab 2` **(2)** path and hit enter, select the **Panamera-from-2021-Porsche-Connect-Good-to-know-Owner-s-Manual** **(3)** pdf  file and click on **Open** **(4)** files.

   ![data-management](images/data-management.png)

3. It will redirect to **Data management**, click on **Upload files** **(1)**, and click on **Next** **(2)**.

   ![data-management](images/bring-your-owndata-upload.png)

4. On the **Data Management** page, from the drop-down select **keyword (1)** as Search type and click on **Next (2)**.

   ![keyword](images/bring-your-owndata-datamanagment.png)

5. In the **Data connection** page, select **API Key** **(1)** and click on **Next (2)**.

   ![Data-Connection](images/bring-your-owndata-dataconnection.png)

6. On the **Review and finish** page, click on **Save and close**.

   ![Save and close](images/bring-your-owndata-save.png)

   <validation step="8f37ff68-c140-4a17-8af7-92838fba1d91" />

### Task 3: Interact with Azure OpenAI ChatGPT LLM using your own data

Test and interact with the ChatGPT model using your uploaded data to generate relevant responses.

1. Under the **Assistant Setup** pane, wait until your data upload is finished.

   ![upload-data](images/ingestion-progress.png)

   ![upload-data](images/data-ingested.png)

2. In the chat pane, you can start testing out your prompts by entering the query like this.

    ```
    how to operate Android Auto in Porche Taycan? give step-by-step instructions
    ```

      ![chat-session-one](images/first-chay.png)

3. You can also configure the responses of your bot by selecting the system message under **System Message**, and clicking on the field to replace the value under the system message with `Your name is Alice. You are an AI assistant that helps people find information about Porche cars.` Your responses should not contain any harmful information and click on **Save**. Here we have edited the default system message.

   ![assistant-setup-system-message](images/model-setup.png)

4. On **Update system message?** pop-up, click on **Continue**.

   ![Alt text](images/newfor4.png)

5. Under the **Chat Session** pane, you can start testing out your prompts by entering the query like this.

    ```
     What is your name
    ```
   
   ![chat-session-two](images/model-chat2.png)

6. In the **Configuration** pane, click on **Parameters**. You can try and experiment with different parameter configurations to see how they change the behavior of the model.

    ![Alt text](images/chat-parameters.png)

## Review

In this lab, you have accomplished the following:

* How to leverage the ChatGPT LLM to extract a concise summary from your own document repository using OpenAI.

## Summary

  In this lab, you will learn to navigate the Azure OpenAI Playground, upload and configure a Porsche Owner's Manual PDF in Azure OpenAI Studio, and interact with the ChatGPT model using your own data to generate and test responses to queries about Porsche cars.

## You have successfully completed the lab.
