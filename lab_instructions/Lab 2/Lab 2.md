# Lab 02: Use Azure OpenAI with your own data

### Overview
In this lab, you will be using your own data with Azure OpenAI Large Language Models (LLM), which will be made searchable using Azure AI Search. You will be using the Porsche Owner's Manual pdf provided to you.

### Goal
How to leverage the ChatGPT LLM to extract a concise summary from your own document repository using OpenAI.

### Pre-requisites
* Access to Microsoft Foundry portal.
* Sample data to test with OpenAI.

### Task 1: Navigate to Microsoft Foundry Playground

Access the Microsoft Foundry portal and upgrade the pre-deployed Azure OpenAI resource.

1. Navigate to **Resource groups**, and then select the **business-process-<inject key="Deployment ID" enableCopy="false"/>** resource group.

   ![OpenAI](images/rgg.png)

1. On the **Resource group** page, search for and select the **Azure OpenAI** resource with the name prefix **oaibpa** that was provisioned during the deployment.

   ![OpenAI](images/change3.png)

1. In the left pane, select **Identity (1)**. Under **System assigned**, toggle the status to **On (2)**, and select **Save (3)**.

   ![OpenAI](images/image-121.png)

1. On the confirmation prompt, select **Yes**.

1. Navigate back to the **Overview** page of the resource. If the page does not immediately reflect the change, refresh the browser and wait a minute for the update to propagate.

1. On the **Overview** page, locate the banner **"Want to try the latest industry models and Agents?"** and select **Get started**.

   ![Azure OpenAI Studio](../Lab%202/images/banner.png)

1. Review the upgrade details, and select **Next** to proceed.

1. Confirm the upgrade by selecting **Upgrade** (or **Confirm**, depending on the current dialog).

1. Wait for the upgrade process to complete. Once finished, you'll be redirected to a new Foundry project associated with this resource.

1. Navigate to the **Microsoft Foundry portal** and ensure the **New Foundry** toggle (top right) is switched **On**.

1. On the top navigation menu, ensure that you are in the **proj-default** project **(1)**. Then, on the same page, select **Test in playground** **(2)**.

   ![Azure OpenAI Studio](../Lab%202/images/image-122.png)

   >**Note:** On the **All set. Let's build your agents.** pop-up, select **Let's go**. Close all other pop-ups.

1. Select your deployed chat model from the **Deployment** dropdown. Ensure that **gpt-5.4-mini** is selected as the deployed model.

   ![](images/image-123.png)

### Task 2: Upload your own data

In this task, we will use Porsche's owner manuals for the Taycan, Panamera, and Cayenne models.

1. On the **gpt-5.4-mini** playground page, select **Save as agent** (top right).

   ![](images/image-124.png)

1. In the **Create an agent** dialog, enter the agent name as **PorscheManualsAssistant (1)**, and select **Create and open playground (2)**.

   ![](images/image-125.png)

1. Before building the knowledge source, upload the manual to Blob Storage so it can be picked up by the indexing pipeline:

    a. In the **Azure Portal**, navigate to your storage account with prefix **bpa**.

      ![](images/image-130.png)

    b. Select **Containers (1)** from the left pane, and select a container to hold the manuals that is **documents (2)**.

      ![](images/image-131.png)

    c. Open the container, select **Upload**, and browse to `C:\LabFiles\Azure-OpenAI-and-Form-Recognizer-Workshop\SampleInvoices\Lab 2` on the JumpVM.

    d. Select **Panamera-from-2021-Porsche-Connect-Good-to-know-Owner-s-Manual.pdf**, and select **Upload**.

1. Navigate to your **bpa**-prefixed **Search service** resource, and select **Import data** from the top menu.

   ![](images/image-132.png)

1. On the **Choose a data source** page, select **Azure Blob Storage**.

   ![](images/image-133.png)

1. On **What scenario are you targeting?**, select **RAG**.

1. On **Connect to your data**, configure the following, then select **Next**:

    - **Subscription (1)**: Your lab subscription

    - **Storage account (2)**: Your **bpa**-prefixed storage account

    - **Blob container (3)**: **documents**

    - **Parsing mode (4)**: **Default**

    - Select **Next (5)**
    
      ![](images/image-134.png)

1. On **Vectorize your text**, select an embedding model deployment (such as **text-embedding-ada-002**) from your Foundry resource, and select **Next**.

1. On **Vectorize and enrich your images**, leave this disabled/skipped (not needed for text-based manuals), and select **Next**.

1. On **Advanced settings**, enter the index name as **aoaiworkshop**, ensure semantic ranking/configuration is enabled, and select **Next**.

1. On **Review and create**, review the configuration, and select **Create**.

1. Wait for the indexer to finish running. You can check progress under **Indexers** in the left pane of the Search resource.

1. Return to the **Microsoft Foundry portal**, open your **PorscheManualsAssistant** agent, and in the left pane, select **Knowledge (1)**.

1. Scroll down on the **Knowledge (Foundry IQ)** page. For **Foundry IQ resource**, choose your Azure AI Search resource with prefix **bpa (2)** from the drop-down, and select **Connect (3)**.

   ![](images/image-126.png)

1. On the **Knowledge (Foundry IQ)** page, select **Create a knowledge base**.

   ![](images/image-127.png)

1. On the **Create a new knowledge base** page, keep the options as default. Scroll down to **Knowledge sources**, select the **Add sources (1)** drop-down, and select **Azure AI Search Index (2)**.

   ![](images/image-128.png)

1. In the **Create a knowledge source** dialog, enter a **Name** for the source (for example, **porsche-manuals-source**).

1. Under **Select search index**, select **aoaiworkshop** from the drop-down (it should now be listed, since the index was created with semantic configuration in the earlier steps).

1. Select **Create**.

1. Back on the **Create a new knowledge base** page, select **Create** to finish creating the knowledge base.

1. Back on the **PorscheManualsAssistant** agent's **Knowledge** section, confirm the knowledge base is listed and connected.

1. Select **Save**.

1. In the chat pane on the right, test the agent by asking a question about the uploaded manual, for example: *"What does the Panamera owner's manual say about Porsche Connect setup?"*

   Confirm the agent responds using content grounded in the uploaded document.

<validation step="8f37ff68-c140-4a17-8af7-92838fba1d91" />

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - Hit the Validate button for the corresponding task. If you receive a success message, you can proceed to the next task. 
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide.
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help

### Task 3: Interact with your agent using your own data

Test and interact with the **PorscheManualsAssistant** agent using your uploaded data to generate relevant responses.

1. In the agent's chat pane, enter the following query:

   ```
   how to operate Android Auto in Porsche Taycan? give step-by-step instructions
   ```

1. Confirm the response is grounded in the uploaded manual content.

1. You can also configure the agent's behavior by selecting the **Instructions** field in the agent's setup pane, and replacing the value with:

   ```
   Your name is Alice. You are an AI assistant that helps people find information about Porsche cars. Your responses should not contain any harmful information
   ```

1. Select **Save** to apply the updated instructions.

1. In the chat pane, test the updated behavior by entering the query:

   ```
   What is your name
   ```

1. Confirm the agent responds as "Alice."

1. In the setup pane, select the **sliders/parameters icon** next to the model dropdown to view generation parameters (such as temperature and max tokens). Experiment with different values to see how they change the model's behavior.

## Review

In this lab, you have accomplished the following:

* How to leverage the ChatGPT LLM to extract a concise summary from your own document repository using OpenAI.

## Summary

In this lab, you learned to navigate the Microsoft Foundry playground, upload a Porsche Owner's Manual PDF, index it using Azure AI Search's RAG import pipeline, connect it as a knowledge source to a Foundry agent, and interact with the agent using your own data to generate and test responses to queries about Porsche cars.

## You have successfully completed the lab.