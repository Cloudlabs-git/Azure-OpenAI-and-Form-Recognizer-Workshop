# Business Automation using Document Intelligence and Microsoft Foundry
 
### Overall Estimated Duration: 4 Hours

## 📘 Lab Scenario

Contoso Ltd. receives supplier and customer invoices in seven languages and layouts, from the US, Spain, Germany, France, Portugal, Italy and the Netherlands. Its finance team spends hours opening invoices one by one to answer simple questions such as "what is the total on invoice INV-2058?" or "what did we bill Müller & Partner?".
 
In this hands-on lab you act as a Cloud Consultant and build Contoso one end-to-end solution in two parts:
 
- **Lab 1** processes the invoices: a Document Intelligence model reads them, a Business Process Automation (BPA) pipeline runs them automatically, and Azure AI Search indexes the results.
- **Lab 2** puts an AI agent on top: a Microsoft Foundry agent uses the Lab 1 search index as its knowledge, so the finance team can ask questions about the invoices in plain language.
Lab 2 builds directly on Lab 1. Complete Lab 1 fully before you start Lab 2.

## 📋 Lab Overview

In this hands-on lab, you will explore how **Azure Document Intelligence**, **Azure AI Search**, and **Microsoft Foundry** can be used together to process and access business information. You train a custom Document Intelligence model, build a BPA pipeline that runs it on a batch of invoices, and index the extracted results in Azure AI Search. You then create a Foundry IQ knowledge base from that index, connect it to a Foundry agent, and chat with the agent about the invoices.

## 🎯 Lab Objectives

By the end of this lab you will be able to:
 
- **Process business documents with Document Intelligence (Lab 1):** create a custom extraction project, label and train a model, run it in a BPA pipeline, grant Azure AI Search secure access to storage with a managed identity, and index and query the extracted invoice data.
- **Ground an AI agent in your processed data (Lab 2):** create a knowledge base from the Lab 1 search index, connect it to a Foundry agent, and use the agent playground to answer questions about the invoices.

## ⚙️ Pre-requisites

- Basic familiarity with Azure AI services and Microsoft Foundry.
- A basic understanding of document processing and search concepts.

## 🏗️ Architecture

This architecture flow demonstrates how various Azure components work together to handle, process, analyze, and visualize data, providing a comprehensive and intelligent system tailored to business needs. In this lab, you'll first create custom models with Document Intelligence, focusing on extracting and analyzing specific data from business forms and documents. Next, you will leverage Azure's advanced data handling tools by using Microsoft Foundry Models in conjunction with Azure AI Search to make your data searchable and accessible. The architecture flow integrates these components to build intelligent systems that enhance productivity and deliver personalized experiences, demonstrating the powerful capabilities of Azure's AI and data analysis technologies tailored to your business needs.

## 🖼️ Architecture Diagram

 ![](./images/arch-diag-0110.png)

## 🔍 Explanation of Components

- **Data Sources:** Business documents such as PDFs, forms, and other files used for processing and analysis.
- **Azure Storage:** Stores the documents and related data used by the document processing workflow.
- **Azure Document Intelligence:** Custom model used to train and extract structured information from business documents (Lab 1).
- **BPA Custom Model Pipeline:** Processes documents using the trained Document Intelligence custom model (Lab 1).
- **Azure AI Search:** Indexes and makes processed document content searchable for efficient information retrieval (Lab 1).
- **Microsoft Foundry:** Provides the knowledge and agent capabilities used to work with business data (Lab 2).
- **Knowledge Source & Knowledge Base:** Organizes and provides business data as contextual knowledge for the Foundry Agent (Lab 2).
- **Foundry Agent:** Uses the configured knowledge to respond to natural-language queries and retrieve relevant information (Lab 2).
- **Foundry Agent Playground:** Provides an interactive interface for users to communicate with the Foundry Agent and explore information from their data (Lab 2).

# 🚀 Getting Started with the lab

We've prepared an immersive environment for you to explore how Azure Document Intelligence, Azure AI Search, and Microsoft Foundry work together to process business documents, make information searchable, and enable AI-powered interactions with your data. Let’s begin!

## Accessing Your Lab Environment
 
Once you're ready to dive in, your virtual machine and **Guide** will be right at your fingertips within your web browser.

 ![](./images/lab-guide-new.png)

## Virtual Machine & Lab Guide

Your virtual machine is your workhorse throughout the workshop. The lab guide is your roadmap to success.

## Exploring Your Lab Resources
 
To get the lab environment details, you can select the **Environment** tab. Additionally, the credentials will also be emailed to your registered email address.

 ![](./images/lab-env-new.png)
 
## Utilizing the Split Window Feature
 
For convenience, you can open the lab guide in a separate window by selecting the **Split Window** button from the Top right corner.
 
 ![](./images/lab-split-new.png)
 
## Managing Your Virtual Machine
 
Feel free to **Start, Stop, or Restart (2)** your virtual machine as needed from the **Resources (1)** tab. Your experience is in your hands!

   ![](./images/13062025(4).png)

## Lab Guide Zoom In/Zoom Out

To adjust the zoom level for the environment page, click the **A↕ : 100%** icon located next to the timer in the lab environment.

![Zoom In/Zoom Out](./images/size-new.png)  

## Resize the Virtual Machine View

Use the **slider (three vertical dots)** located between the **Virtual Machine** and the **Lab Guide** panes to adjust the display size, allowing you to customize the layout based on your preference.

![Zoom In/Zoom Out](./images/vm-resize.png)
 
## Let's Get Started with Azure Portal

1. On your virtual machine, click on the **Azure Portal** icon as shown below:
 
   ![](./images/new/vm.png)

1. On the **Sign in to Microsoft Azure** tab, you will see the login screen. Enter the following email/username, and click on **Next (2)**. 

   * **Email/Username:** <inject key="AzureAdUserEmail"></inject> **(1)**
   
      ![](./images/GS3.png)
     
1. Now enter the following temporary password and click on **Sign in (2)**.
   
   * **Temporary Access Pass:** <inject key="AzureAdUserPassword"></inject> **(1)**
   
      ![](./images/GS4.png "Enter Password")
   
1. If you see the pop-up **Stay signed in?**, select **No**.

   ![](./images/GS5.png)

1. Now you will see the Azure Portal Dashboard, click on **Resource groups** from the Navigate panel to see the resource groups.

   ![](./images/9-7-25-g5.png "Resource groups")
   
1. Confirm that you have the **business-process-<inject key="Deployment ID" enableCopy="false"/>** **(2)** resource group present as shown below.

   ![](./images/L1T3S1.png "Resource groups")
   
1. Verify the resources deployed in the resource group.

   ![](./images/new/GS8.png)
   
   
> **[!Tip]**
*For a smoother experience during the hands-on lab, it's important to thoroughly review both the instructions and the accompanying notes. This will help you navigate through the tasks with ease and confidence.*

## 📞 Support Contact
 
The **CloudLabs support team** is available 24/7, 365 days a year, via email and live chat to ensure seamless assistance at any time. We offer dedicated support channels tailored specifically for both learners and instructors, ensuring that all your needs are promptly and efficiently addressed.

Learner Support Contacts:
 
- Email Support: [cloudlabs-support@spektrasystems.com](mailto:cloudlabs-support@spektrasystems.com)
- Live Chat Support: https://cloudlabs.ai/labs-support

Now, click on **Next >>** from the lower right corner to move on to the next page.
 
![](./images/new/next.png)
   
### Happy Learning!!
