# Lab 02: Use Azure OpenAI with your own data

### Estimated Duration: 60 Minutes

In this lab, you will be using your own data with Azure OpenAI Large Language Models (LLM), which will be made searchable using Azure AI Search. You will be using the Porsche Owner's Manual PDF provided under the `C:\Users\Public\Desktop\Data\Lab 2` folder.

## Lab Objectives

In this lab, you will complete the following tasks:

* Task 1: Navigate to Azure OpenAI Playground
* Task 2: Upload your own data
* Task 3: Interact with Azure OpenAI ChatGPT LLM using your own data

## Task 1: Navigate to Azure OpenAI Playground

1. Navigate back to the **Resource groups** and select the resource group **business-process-<inject key="Deployment ID" enableCopy="false"/>**.

   ![OpenAI](images/rgg.png)

2. On the Resource group, search, and select the **Azure OpenAI** resource type with the name similar to **oaibpa{suffix}**.

   ![OpenAI](images/9-7-25-l2-1.png)

3. On the **Azure OpenAI Overview** page, click on **Explore Azure AI Foundry portal**.

   ![OpenAI Studio](images/9-7-25-l2-2.png)

4. On the **Azure AI Foundry | Azure OpenAI Service** page, in the **Home** section, scroll down and click on **Bring your own data**.

   ![Azure OpenAI Studio](images/pg3-task1-4.png)

## Task 2: Upload your own data

In this step, we will be using Porsche's owner manual for the Taycan, Panamera, and Cayenne models.

1. On the **Chat playground** page, select **Chat** under **Playgrounds** **(1)**. Expand **Add your data** **(2)**, then click on **+ Add a data source** **(3)** and fill the following details:

   ![Azure OpenAI Studio](images/9-7-25-l2-3.png)
    
    - Select data source: **Upload files (preview)** **(1)**

    - Subscription: Select your subscription from the drop-down section **(2)**

    - Select Azure Blob storage resource: Choose the already created storage account **formrecognizer<inject key="Deployment ID">** **(3)**. 
      
      - **Note:** If prompted with a CORS permission warning,, click on **Turn on CORS**.

         ![](images/cors.png)

    - Select Azure AI Search  resource: Select the search service used in the previous lab from the drop-down **(4)**.

    - Enter the index name: Enter the index name as **aoaiworkshop** **(5)**.
    
    - Click on **Next** **(6)**.

      ![add-data](images/uploadfilesnew.png) 

2. On the **Upload files** page, click on **Browse for a file** **(1)** enter the following `C:\Users\Public\Desktop\Data\Lab 2` **(2)** path and hit enter, select the **Panamera-from-2021-Porsche-Connect-Good-to-know-Owner-s-Manual** **(3)** pdf  file and click on **Open** **(4)**.

   ![data-management](images/data-managementnew.png)

3. Click on **Upload files** **(1)**, and click on **Next** **(2)**.

   ![data-management](images/data-management-uploadnew.png)

4. On the **Data Management** page, select **Keyword** **(1)** from the **Search type** dropdown and click on **Next (2)**.

   ![keyword](images/uploadfiles1new.png)

5. On the **Data Connection** page, Under Azure resorce authentication type, select **API Key** and click on **Next**.

   ![keyword](images/E2-T2-S5.png)

6. On the **Review and finish** page, click on **Save and close**.

   ![image](images/9-7-25-l2-4.png)

## Task 3: Interact with Azure OpenAI ChatGPT LLM using your own data

1. Under the **Setup** pane, wait until your data upload is finished.

   ![upload-data](images/pg3-task3-1.png)

   ![upload-data](images/pg3-task3-1.1.png)

2. Under the **Chat Session** pane, you can start testing out your prompts by entering the query like this.

    ```
    How to operate Android Auto in the Porsche Taycan? give step-by-step instructions
    ```

      ![chat-session-one](images/pg3-task3-2.png)

3. You can also configure the responses of your bot by selecting the system message under **Setup**, replacing the value under the **Give the model instructions and context** with `Your name is Alice. You are an AI assistant that helps people find information about Porsche cars. Your responses should not contain any harmful information` **(1)** and click on **Apply changes** **(2)**. Here we have edited the default system message.

   ![assistant-setup-system-message](images/pg3-task3-3.png)

4. On **Update system message?** pop-up, click on **Continue**.

   ![Alt text](images/update-new.png)

5. Under the **Chat Session** pane, you can start testing out your prompts by entering the query like this.

    ```
    What are the available functions in the Discover menu item?
    ```
   
    ![chat-session-two](images/pg3-task3-5new.png)

6. Expand **> Parameters** from the left column. You can experiment with different parameter configurations to see how they affect the model's behavior.

    ![Alt text](images/E2-T2-S6.png)

7. You can try the following query after adjusting the parameters session

   - How can one navigate lists via voice control?
   - What are the settings that can be adjusted under the Settings menu item?
   - How can one report a theft using the Theft Reporting function?
   - What information can be viewed or edited in the My Garage section?
   - What does the Real-time Traffic service provide in the Navigation Plus feature?
   - How can real-time traffic messages be accessed and viewed?
   - What are the general guidelines for using voice control effectively?
   - How can the Charging Planner route be created and customized?
   - What are the available options for interacting with the multimodal map feature during navigation?

## Summary 

This hands-on lab demonstrates how to use your own data with Azure OpenAI’s Large Language Models (LLMs) and make it searchable using Azure AI Search. You’ll configure and integrate these services to improve data accessibility and enable intelligent search capabilities.

## You have successfully completed this Hands-on lab.
