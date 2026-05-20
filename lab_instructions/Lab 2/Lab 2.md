# Use Azure OpenAI with your own data

### Overview
In this lab, you will be using your own data with Azure OpenAI Large Language Models (LLM), which will be made searchable using Azure AI Search. You will be using the Porche Owner's Manual pdf provided to you.

### Goal
How to leverage the ChatGPT LLM to extract a concise summary from your own document repository using OpenAI.

### Pre-requisites
* Access to Azure OpenAI chat playground.
* Sample data to test with OpenAI.

### Instructions

### Task 1: Navigate to Azure OpenAI Playground

Access the Azure OpenAI Studio and navigate to the "Bring your own data" section.

1. Navigate to the Resource groups and select the resource group **business-process-<inject key="Deployment ID" enableCopy="false"/>**.

   ![OpenAI](images/rgg.png)

2. On the Resource group, search, and select the **Azure OpenAI (1)** resource with the name prefix **(oai)** that was already created.

   ![OpenAI](images/change3.png)

3. On the **Azure OpenAI** page, click on **Go to Foundry Portal**.

   ![OpenAI Studio](images/change1.png)

4. On the **Microsoft Foundry Portal**, click **Chat** under the Playgrounds section on the left to see the Chat Playground service.

   ![Azure OpenAI Studio](../Lab%202/images/change2.png)

5. On **Chat playground** pane, select **Add your data (1)** tab and click on **+ Add a data source (2)**.

   ![](images/L2T1S5.png)

### Task 2: Upload your own data

In this task, we will use Porsche's owner manuals for the Taycan, Panamera, and Cayenne models.

1. Fill the following details in **Select or add data source** and click on **Next** **(6)**.
    
    - Select data source: **Upload files (preview)** **(1)**

    - Subscription: Select your subscription from the drop-down section **(2)**

    - Select Azure Blob storage resource: Choose the already created storage account from the drop-down with prefix as **(bpa)** **(3)**. If asked, enable CORS.

    - Select Azure AI Search resource: Select the search service from the drop-down with prefix as **(bpa)** **(4)**.

    - Enter the index name: Give an index name as **aoaiworkshop** **(5)**

      ![add-data](images/change4.png) 

2. On the **Data Management**, click on **Browse for a file** **(1)** enter the following `C:\LabFiles\Azure-OpenAI-and-Form-Recognizer-Workshop\SampleInvoices\Lab 2` **(2)** path and hit enter, select the **Panamera-from-2021-Porsche-Connect-Good-to-know-Owner-s-Manual** **(3)** pdf  file and click on **Open** **(4)** files.

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

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help

### Task 3: Interact with Azure OpenAI ChatGPT LLM using your own data

Test and interact with the ChatGPT model using your uploaded data to generate relevant responses.

1. Under the **Assistant Setup** pane, wait until your data upload is finished.

   ![upload-data](images/upload-data.png)

   ![upload-data](images/L2T3S1-ii.png)

2. Under the **Chat Session** pane, you can start testing out your prompts by entering the query like this.

    ```
    how to operate Android Auto in Porche Taycan? give step-by-step instructions
    ```

      ![chat-session-one](images/newfor2.png)

3. You can also configure the responses of your bot by selecting the **Give the model instructions and context** under **Setup**, replace the value with `Your name is Alice. You are an AI assistant that helps people find information about Porche cars. Your responses should not contain any harmful information` and click on **Apply Changes**. Here we have edited the default system message.

   ![assistant-setup-system-message](images/L2T3S3.png)

4. On **Update system message?** pop-up, click on **Continue**.

   ![Alt text](images/newfor4.png)

5. Under the **Chat Session** pane, you can start testing out your prompts by entering the query like this.

    ```
     What is your name
    ```
   
   ![chat-session-two](images/eyhackday3img6.png)

6. In the **Configuration** pane, click on **Parameters**. You can try and experiment with different parameter configurations to see how they change the behavior of the model.

    ![Alt text](images/L2T3S6.png)

## Review

In this lab, you have accomplished the following:

* How to leverage the ChatGPT LLM to extract a concise summary from your own document repository using OpenAI.

## Summary

  In this lab, you will learn to navigate the Azure OpenAI Playground, upload and configure a Porsche Owner's Manual PDF in Azure OpenAI Studio, and interact with the ChatGPT model using your own data to generate and test responses to queries about Porsche cars.

## You have successfully completed the lab.
