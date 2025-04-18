# Lab 02: Use Azure OpenAI with your own data

In this lab, you will be using your own data with Azure OpenAI Large Language Models (LLM), which will be made searchable using Azure AI Search . You will be using the Porche Owner's Manual pdf provided under the `C:\Users\Public\Desktop\Data\Lab 2` folder.

### Lab Objectives

In this lab, you will complete the following tasks:

* Task 1: Navigate to Azure OpenAI Playground
* Task 2: Upload your own data
* Task 3: Interact with Azure OpenAI ChatGPT LLM using your own data

### Task 1: Navigate to Azure OpenAI Playground

1. Navigate back to the Resource groups and select the resource group **business-process-<inject key="Deployment ID" enableCopy="false"/>**.

   ![OpenAI](images/rgg.png)

2. On the Resource group, search, and select the **Azure OpenAI** resource type with the name similar to **oaibpa{suffix}**.

   ![OpenAI](images/pg3-task1-2.png)

3. On the **Azure OpenAI** page, click on **Go to Azure OpenAI Studio**.

   ![OpenAI Studio](images/pg3-task1-3.png)

4. On the **Azure OpenAI Studio**, In **Home** scroll down and click on **Bring your own data**.

   ![Azure OpenAI Studio](images/pg3-task1-4.png)

### Task 2: Upload your own data

In this step, we will be using Porche's owner manual for Taycan, Panamera, and Cayenne models.

1. You will be redirected **Chat** under **Playgrounds**. Click on **Add a data source** and fill the following details: 
   ![Azure OpenAI Studio](images/pg3-task2-1.png)
    
    - Select data source: **Upload files (preview)** **(1)**

    - Subscription: Select your subscription from the drop-down section **(2)**

    - Select Azure Blob storage resource: Choose the already created storage account **formrecognizer<inject key="Deployment ID">** **(3)**. 
      
      - **Note**: If asked for turn on CORS, click on **Turn on CORS**.

         ![](images/cors.png)

    - Select Azure AI Search  resource: Select the search service used in the previous lab from the drop-down **(4)**.

    - Enter the index name: Give an index name as **aoaiworkshop** **(5)**.
    - Click on **Next** **(6).**

      ![add-data](images/uploadfiles.png) 

2. On the **Data Management**, click on **Browse for a file** **(1)** enter the following `C:\Users\Public\Desktop\Data\Lab 2` **(2)** path and hit enter, select the **Panamera-from-2021-Porsche-Connect-Good-to-know-Owner-s-Manual** **(3)** pdf  file and click on **Open** **(4)** files.

   ![data-management](images/data-management.png)

3. It will redirect to **Data management**, click on **Upload files** **(1)**, and click on **Next** **(2)**.

   ![data-management](images/data-management-upload.png)

4. On the **Data Management** page, from the drop-down select **keyword (1)** as Search type and click on **Next (2)**.

   ![keyword](images/uploadfiles1.png)

5. On the **Data Connection** page, Under Azure resorce authentication type, select **API Key**.

   <img width="539" alt="image" src="https://github.com/user-attachments/assets/34f72831-1a33-47c8-9d8f-5200b51be35d">

6. On the **Review and finish** page, click on **Save and close**.

   ![image](https://github.com/user-attachments/assets/57bfec0e-a3e6-4791-af51-cceb44003c51)


### Task 3: Interact with Azure OpenAI ChatGPT LLM using your own data

1. Under the **Setup** pane, wait until your data upload is finished.

   ![upload-data](images/pg3-task3-1.png)

   ![upload-data](images/pg3-task3-1.1.png)

2. Under the **Chat Session** pane, you can start testing out your prompts by entering the query like this.

    ```
    how to operate Android Auto in Porche Taycan? give step-by-step instructions
    ```

      ![chat-session-one](images/pg3-task3-2.png)

3. You can also configure the responses of your bot by selecting the system message under **Setup**, replace the value under the **Give the model instructions and context**
 with `Your name is Alice. You are an AI assistant that helps people find information about Porche cars. Your responses should not contain any harmful information` **(1)** and click on **Apply changes** **(2)**. Here we have edited the default system message.

   ![assistant-setup-system-message](images/pg3-task3-3.png)

4. On **Update system message?** pop-up, click on **Continue**.

   ![Alt text](images/pg3-task3-4.png)

5. Under the **Chat Session** pane, you can start testing out your prompts by entering the query like this.

    ```
     What is your name
    ```
   
   ![chat-session-two](images/pg3-task3-5.png)

6. In the **Configuration** pane, click on **Parameters**. You can try and experiment with different parameter configurations to see how they change the behavior of the model.

    ![Alt text](images/parameters.png)

    > **Note**-If you didn't find **Configuration** click on **show panels** on top right corner.and Make sure check in the **setup** and **parameter** and **save** it.

    ![image](https://github.com/user-attachments/assets/4a9ca595-f5b4-46c2-9412-53af9bdc30ce)

## Summary 

In this hands-on lab, you will use your own data with Azure OpenAI Large Language Models (LLM) and make it searchable using Azure AI Search. The steps involve configuring and integrating these services to enhance data accessibility and searchability.

## You have successfully completed this lab.

