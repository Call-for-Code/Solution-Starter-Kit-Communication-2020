# COVID Crisis Communications Starter Kit

This solution starter was created by technologists from IBM.

## Authors

- [Donna Byron](https://developer.ibm.com/profiles/dkbyron/) - IBM
- [John Walicki](https://developer.ibm.com/profiles/walicki/) - IBM
- [Matt Price](https://developer.ibm.com/profiles/pricem/) - IBM
- [Mofizur Rahman](https://developer.ibm.com/profiles/mofizur.rahman) - IBM
- [Pooja Mistry](https://developer.ibm.com/profiles/pmistry/) - IBM
- [Upkar Lidder](https://developer.ibm.com/profiles/ulidder/) - IBM

## Contents

1. [Overview](#overview)
2. [Video](#video)
3. [The idea](#the-idea)
4. [How it works](#how-it-works)
5. [Diagrams](#diagrams)
6. [Documents](#documents)
7. [Datasets](#datasets)
8. [Technology](#technology)
9. [Getting started](#getting-started)
9. [Resources](#resources)
10.[License](#license)

## Overview

### What's the problem?
In times of crisis, communications systems are one of the first systems to become overwhelmed. Chatbots help respond to tens, even hundreds, of thousands of messages a day. Whether via text, websites or communication apps like WhatsApp, being able to converse with chatbots and other resources can play a critical role in helping communities understand everything they need to know rapidly and free up customer service resources to focus on higher level issues. Whether that's correct hand washing procedure, how to properly detect symptoms, or local updates on quarantine, providing crisis communications digitally has a major role to play. 

### How can technology help?

Crisis communication, whether through a chatbot, SMS, or a website, can alleviate panic in communities and provide guidance on the best ways to protect yourself and your loved ones.  From guidance on good hygiene to how to properly detect symptoms or key contact information, technology like chatbots or messaging platforms can help deliver information quickly and precisely. This can save people hours compared to waiting to get through to a call center, and free up customer service representatives to focus on higher level issues.

Watson Assistant is a service on IBM Cloud that allows us to build, train, and deploy conversational interactions into any application, device, or channel. Creating a chatbot using Watson Assistant can help address the issues that our users can face while trying to gather the right information. Whether that is trying to learn the latest news on Covid-19 or find out how to take the right precautions, a chatbot built with Watson Assistant can play a major role in helping communities quickly understand crucial information and free up customer service resources to focus on higher-level issues.

## Video

[![Call for Code Solution Starter: Water sustainability in the context of climate change ](https://img.youtube.com/vi/VnKmEgUnn34/0.jpg)](https://www.youtube.com/watch?v=VnKmEgUnn34)

## The idea

The idea for this starter kit stems from having an accurate source for communication and messaging during time of crisis. With communication systems being the first systems to be overwhelmed, the team thought that the best idea would be to use technology to create a chatbot that can help respond to a multiple inquiries a day and  can integrate with various technologies. In this pandemic , the team thought it would be best to create a chat bot using Watson Assistant that is  based on COVID-19 crisis management training data that would answer all basic inquires about the Coronavirus as well as any information regarding health and safety of individuals. This Watson Assistant based chatbot would also be integrated with to Watson Discovery news to get real time news articles around COVID-19 and would be used to  deployed to various different mediums such as Slack and Node-RED.

This starter kit shows how a user can integrate the COVID Crisis Communication Watson Assistant to various different technologies. With more and more individuals working from home and communicating via Slack  the team thought that having a Slack integration to the COVID Crisis Communication Bot would be a great use case for individuals to communicate. The other integration with Node-RED integration allows users to communicate with COVID Crisis Communication bot via speech to text api for any home automated assistant use cases. Along with these two integrations, this starter kit provided various resources and tutorials on how to integrate a Watson Assistant to a multitude of technologies. Overall the goal of this starter kit was to provide use examples on how to integrate the COVID Crisis Communication Bot and inspire everyone on how to get started with building your own version of these integrations.  

COVID-19 has citizens looking for answers about symptoms and testing sites as well as current status of schools, transportation and other public services. Using Watson Assistant, this Call for Code Starter Kit has designed a virtual assistant pre-loaded to understand and respond to common questions about COVID-19, scan COVID-19 news articles using Watson Discovery and respond to COVID statistics inquires with data from trusted sources.

With this Watson Assistant powered Crisis Communications Starter Kit you can integrate a chatbot into your Call for Code solution in a IBM Cloud hosted web server, using a Slack integration or via a Node-RED Dashboard.  It can:

- Respond by sharing consistent, accurate COVID-19 information
- Help citizens quickly and easily access the latest information through their channel of choice – voice, text or collaborative tool
- Free valuable resources by automating answers to common COVID-19 questions.
- Dynamically update information with the latest developments and recommendations


## How it works


## Diagrams

### Crisis Chatbot on a web site

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Nodejs-WebServer.png)

1. User visits a website with the COVID-19 chatbot and asks a question
2. Node.js web server calls Watson Assistant service hosted in IBM Cloud
3. Watson Assistant uses NLU and ML to extract entities and intents of the user question
4. Check external data sources for COVID information
5. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function
6. IBM Cloud Function calls Watson Discovery service running in IBM Cloud
7. Watson Discovery scans news articles and responds with relevant articles
8. Watson Assistant replies to the user inquiry
9. Node.js web server displays the chat answer to the user

### Crisis Chatbot integrated with Slack

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Slack-Integration.png)

1. User invokes a COVID-19 Slack integration chatbot app and asks a question
2. Slack app calls Watson Assistant service hosted in IBM Cloud
3. Watson Assistant uses NLU and ML to extract entities and intents of the user question
4. Check external data sources for COVID information
5. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function
6. IBM Cloud Function calls Watson Discovery service running in IBM Cloud
7. Watson Discovery scans news articles and responds with relevant articles
8. Watson Assistant replies to the Slack app
9. Slack app displays the chat answer to the user

### Voice enabled Crisis Chatbot using Node-RED

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Node-RED.png)

1. User visits a voice enabled Node-RED website with the COVID-19 chatbot and asks a question
2. Node-RED records the speech wav file and calls the Watson Speech to Text service hosted in IBM Cloud
3. Watson Speech to Text uses ML to decode the user's speech
4. Watson Speech to Text replies with a transcript of the COVID-19 question and Node-RED calls Watson Assistant service hosted in IBM Cloud
5. Watson Assistant uses NLU and ML to extract entities and intents of the user question
6. Check external data sources for COVID information
7. Watson Assistant invokes an OpenWhisk open source powered IBM Cloud Function
8. IBM Cloud Function calls Watson Discovery service running in IBM Cloud
9. Watson Discovery scans news articles and responds with relevant articles
10. Watson Assistant replies to the user inquiry and Node-RED sends the text transcript to Watson Text to Speech
11. Watson Text to Speech encodes the message in the user's language
12. Node-RED plays the chat answer wav file to the user
13. User listens to the chat answer


## Documents

- Trusted sources for COVID-19 information
 - [CDC COVID-19 FAQ](https://www.cdc.gov/coronavirus/2019-ncov/faq.html)

## Datasets

- [covid19api](https://covid19api.com/)

## Technology

- [Bot Asset Exchange](https://developer.ibm.com/code/exchanges/bots/)
- [IBM Watson Assistant](https://www.ibm.com/cloud/watson-assistant/)
- [How-to guides for chatbots](https://www.ibm.com/watson/how-to-build-a-chatbot)
- [Create a machine learning powered web app to answer questions](https://developer.ibm.com/patterns/create-a-machine-learning-powered-web-app-to-answer-questions-from-a-book/)
- [Learning path: Getting started with Watson Assistant](https://developer.ibm.com/series/learning-path-watson-assistant/)
- [Train a speech-to-text model](https://developer.ibm.com/patterns/customize-and-continuously-train-your-own-watson-speech-service/)
- [Chatbot with Watson Discovery](https://github.com/IBM/watson-discovery-sdu-with-assistant)
- [Chat Bot Slack Integration](https://developer.ibm.com/technologies/artificial-intelligence/videos/integrating-watson-assistant-with-slack-using-built-in-integrations/#)
- [Chat Bot Slack Deployment](https://cloud.ibm.com/docs/assistant?topic=assistant-deploy-slack)
- [Node-RED Slack Integration](https://www.ibm.com/cloud/blog/create-a-chatbot-on-ibm-cloud-and-integrate-with-slack-part-1)
- [Enhance customer helpdesks with Smart Document Understanding using webhooks in Watson Assistant](https://developer.ibm.com/patterns/enhance-customer-help-desk-with-smart-document-understanding/)
- [Watson Voice Agent](https://cloud.ibm.com/catalog/services/voice-agent-with-watson)
- [Getting Started with Watson Voice Agent](https://cloud.ibm.com/docs/services/voice-agent?topic=voice-agent-getting-started)
- [Making Programmatic Calls from Watson Assistant](https://cloud.ibm.com/docs/assistant?topic=assistant-dialog-webhooks)
- [IBM Cloud Voice Agent with Twilio](https://developer.ibm.com/recipes/tutorials/ibms-voice-agent-with-watson-and-twilio/)


## Getting started

### Prerequisite

- Register for an [IBM Cloud](https://www.ibm.com/account/reg/us-en/signup?formid=urx-42793&eventid=cfc-2020?cm_mmc=OSocial_Blog-_-Audience+Developer_Developer+Conversation-_-WW_WW-_-cfc-2020-ghub-starterkit-communication_ov75914&cm_mmca1=000039JL&cm_mmca2=10008917) account.

### Set up an instance of Watson Assistant
Log in to IBM Cloud and provision a Watson Assistant instance.

**Step 1.** Provision an instance of **Watson Assistant** from the [IBM Cloud catalog](https://cloud.ibm.com/catalog/services/watson-assistant).
![Watson Assistant Catalog](/starter-kit/assistant/WA-Photo1.png)

**Step 2.**  Launch the Watson Assistant service.

**Step 3.** [Create a  **Watson Assistant** service instance](https://cloud.ibm.com/docs/assistant?topic=assistant-assistant-add).
![Watson Assistant Photo2 ](/starter-kit/assistant/WA-Photo2.png)

**Step 4.** Name the Watson Assistant instance **COVID Crisis Communication**
![Watson Assistant Photo3 ](/starter-kit/assistant/WA-Photo3.png)

**Step 5.** Click on [Add dialog skill](https://cloud.ibm.com/docs/assistant?topic=assistant-skill-dialog-add)
![Watson Assistant Photo4 ](/starter-kit/assistant/WA-Photo4.png)

**Step 6.** Click on **Import skill** and upload the [`skill-CDC-COVID-FAQ.json`](./starter-kit/covid-simple/training/skill-CDC-COVID-FAQ.json) file.
![Watson Assistant Photo5 ](/starter-kit/assistant/WA-Photo5.png)

**Step 7.** Go back to All Assistants page, open **Settings** from the action menu ( **`⋮`** ) and click on **API Details**.
![Watson Assistant Photo6 ](/starter-kit/assistant/WA-Photo6.png)

**Step 8.**  Note the **Assistant ID** and **Api Key** for future use.
![Watson Assistant Photo7 ](/starter-kit/assistant/WA-Photo7.png)

**Step 9.**  Go back to your dialog skill and click on the  **Preview Link** button on the side to get a link to test and verify your assistant.
![Watson Assistant Photo9 ](/starter-kit/assistant/WA-Photo9.png)

**Step 10.** Ask the Watson Assistant chatbot some questions about COVID-19
![Watson Assistant Photo10 ](/starter-kit/assistant/WA-Photo10.png)

### Add a Webhook
To make a programmatic call, define a webhook that sends a POST request callout to an external application that performs a programmatic function. You can then invoke the webhook from one or more dialog nodes.

A webhook is a mechanism that allows you to call out to an external program based on something happening in your program. When used in a dialog skill, a webhook is triggered when the assistant processes a node that has a webhook enabled. The webhook collects data that you specify or that you collect from the user during the conversation and save in context variables. It sends the data as part of a HTTP POST request to the URL that you specify as part of your webhook definition. The URL that receives the webhook is the listener. It performs a predefined action using the information that you pass to it as specified in the webhook definition, and can optionally return a response.

[Instruction for setting up Webhook](./starter-kit/webhook/README.md)

### Integrate with Slack
Now that you have a functioning Watson Assistant, let’s deploy it to Slack. Slack is a cloud-based messaging application that helps people collaborate with one another. After you configure a dialog skill and add it to an assistant, you can integrate the assistant with Slack.

When integrated, depending on the events that you configure the assistant to support, your assistant can respond to questions that are asked in direct messages or in channels where the assistant is directly mentioned.

Follow this tutorial to learn how to [Integrate with Slack](/starter-kit/slack/README.md)

![Slack Gif](/starter-kit/slack/readme_images/Slack.gif)

### Integrate with Node-RED

This tutorial will teach you how to [create a voice enabled chatbot using Node-RED](./starter-kit/node-red/README.md) and the Watson Assistant, Watson Speech to Text, and Watson Text to Speech nodes.

### Integrate with a Node.js web site

- Fork of [Assistant-Simple](https://github.com/watson-developer-cloud/assistant-simple)
- Follow the [COVID-Simple installation instructions](./starter-kit/covid-simple/README.md)

## Resources

- [IBM Cloud](https://www.ibm.com/cloud)
- [Watson Assistant](https://cloud.ibm.com/docs/assistant?topic=assistant-getting-started)

## Resources


## License

This solution starter is made available under the [Apache 2 License](LICENSE).
