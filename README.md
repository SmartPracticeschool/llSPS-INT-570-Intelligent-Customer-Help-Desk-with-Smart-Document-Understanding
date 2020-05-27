# Enhance customer helpdesks with Smart Document Understanding

In this code pattern, we walk you through a working example of a web app that utilizes multiple Watson services to create a better customer care experience.

Using the Watson Discovery Smart Document Understanding (SDU) feature, we will enhance the Discovery model so that queries will be better focused to only search the most relevant information found in a typical owner's manual.

Using Watson Assistant, we will use a standard customer care dialog to handle a typical conversation between a custmomer and a company representitive. When a customer question involves operation of a product, the Assistant dialog will communicate with the Discovery service using a webhook.

The webhook will be created by defining a `web action` using IBM Cloud Functions.

## What is SDU?

SDU trains Watson Discovery to extract custom fields in your documents. Customizing how your documents are indexed into Discovery will improve the answers returned from queries.

With SDU, you annotate fields within your documents to train custom conversion models. As you annotate, Watson is learning and will start predicting annotations. SDU models can also be exported and used on other collections.

Current document type support for SDU is based on your plan:

  * Lite plans: PDF, Word, PowerPoint, Excel, JSON, HTML
  * Advanced plans: PDF, Word, PowerPoint, Excel, PNG, TIFF, JPG, JSON, HTML

Here is a great video that provides an overview of the benefits of SDU, and a walk-through of how to apply it to your document:



## What is a webhook?

A webhook is a mechanism that allows you to call out to an external program based on something happening in your program. When used in a Watson Assistant dialog skill, a webhook is triggered when the Assistant processes a node that has a webhook enabled. The webhook collects data that you specify or that you collect from the user during the conversation and save in context variables, and sends the data to the Webhook request URL as an HTTP POST request. The URL that receives the webhook is the listener. It performs a predefined action using the information that is provided by the webhook as specified in the webhook definition, and can optionally return a response.

In our example, the webhook will communicate with an IBM Cloud Functions `web action`, which is connected to the Watson Discovery service.

> **Note**: Another method of integrating Watson Assistant with Watson Discovery is through the use of a new feature of Watson Assistant called a [search skill](https://cloud.ibm.com/docs/services/assistant?topic=assistant-skill-search-add). Click [here](https://github.com/IBM/watson-assistant-with-search-skill) to view a code pattern that showcases this feature.

## Flow

![architecture](doc/source/images/architecture.png)

1. The document is annotated using Watson Discovery SDU
1. The user interacts with the backend server via the app UI. The frontend app UI is a chatbot that engages the user in a conversation.
1. Dialog between the user and backend server is coordinated using a Watson Assistant dialog skill.
1. If the user asks a product operation question, a search query is passed to a predefined IBM Cloud Functions action.
1. The Cloud Functions action will query the Watson Discovery service and return the results.





Node-Red link:  https://intelligent-customer-help-desk-with-smart-document-sb26365.eu-gb.mybluemix.net/ui/#!/0?socketid=fO_T1rwl_m1pyrgnAAAM


# Lab4-Adding-Discovery-to-Chatbot

This is the source code for the lab and Capstone project for Building AI Applications with Watson APIs course on Coursera. 

Relevant Documentation:

- Watson Assistant Service Overview
  https://cloud.ibm.com/docs/services/assistant?topic=assistant-assistants
  
- Watson Discovery Service Overview
  https://cloud.ibm.com/docs/services/discovery?topic=discovery-about
 
- Watson Discovery How to Build Query
  https://cloud.ibm.com/docs/services/discovery?topic=discovery-query-concepts
  
- IBM Functions(Serverless Computing) Overview
  https://cloud.ibm.com/docs/openwhisk?topic=cloud-functions-getting-started
  
 - How to make a programming call from a dialog node
  https://cloud.ibm.com/docs/services/assistant?topic=assistant-dialog-webhooks
  
