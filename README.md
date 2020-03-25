# COVID Crisis Communications Starter Kit

This solution starter was created by technologists from IBM.

## Authors

- Donna Byron - IBM
- [John Walicki](https://developer.ibm.com/profiles/walicki/) - IBM
- Matt Price - IBM
- Mofizur Rahman - IBM
- Pooja Mistry - IBM
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
10. [License](#license)

## Overview

### What's the problem?
In times of crisis, communications systems are one of the first systems to become overwhelmed. Chatbots help respond to tens, even hundreds, of thousands of messages a day. Whether via text, websites or communication apps like WhatsApp, being able to converse with chatbots and other resources can play a critical role in helping communities understand everything they need to know rapidly and free up customer service resources to focus on higher level issues. Whether that's correct hand washing procedure, how to properly detect symptoms, or local updates on quarantine, providing crisis communications digitally has a major role to play. 

### How can technology help?

Crisis communication, whether through a chatbot, SMS, or a website, can alleviate panic in communities and provide guidance on the best ways to protect yourself and your loved ones.  From guidance on good hygiene to how to properly detect symptoms or key contact information, technology like chatbots or messaging platforms can help deliver information quickly and precisely. This can save people hours compared to waiting to get through to a call center, and free up customer service representatives to focus on higher level issues. 

Watson Assistant is a service on IBM Cloud that allows us to build, train, and deploy conversational interactions into any application, device, or channel. Creating a chatbot using Watson Assistant can help address the issues that our users can face while trying to gather the right information. Whether that is trying to learn the latest news on Covid-19 or find out how to take the right precautions, a chatbot built with Watson Assistant can play a major role in helping communities quickly understand crucial information and free up customer service resources to focus on higher-level issues.

## Video

[![Call for Code Solution Starter: Water sustainability in the context of climate change ](https://img.youtube.com/vi/VnKmEgUnn34/0.jpg)](https://www.youtube.com/watch?v=VnKmEgUnn34)

## The idea


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

- Trusted sources for COVID-19
- [CDC COVID-19 FAQ](https://www.cdc.gov/coronavirus/2019-ncov/faq.html)

## Datasets

- [CDC COVID-19 FAQ](https://www.cdc.gov/coronavirus/2019-ncov/faq.html)

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

### Steps

1. [Set up an instance of Watson Assistant](#1-set-up-an-instance-of-watson-assistant).


### 1. Set up an instance of Watson Assistant
Log in to IBM Cloud and provision a Watson Assistant instance.

1. Provision an instance of **Watson Assistant** from the [IBM Cloud catalog](https://cloud.ibm.com/catalog/services/watson-assistant).
1. Launch the Watson Assistant service.
1. [Create an **Assistant**](https://cloud.ibm.com/docs/assistant?topic=assistant-assistant-add).
1. [Add a dialog skill](https://cloud.ibm.com/docs/assistant?topic=assistant-skill-dialog-add) to the **Assistant** by importing the [`starter-kit-flood-dialog-skill.json`](./starter-kit/assistant/starter-kit-flood-dialog-skill.json) file.
1. Go back to All Assistants page, open **Settings** from the action menu ( **`⋮`** ) and click on **API Details**.
1. Note the **Assistant ID** and **API Key**.
1. Go to **Preview Link** to get a link to test and verify the dialog skill.

## Resources

- [IBM Cloud](https://www.ibm.com/cloud)
- [Watson Assistant](https://cloud.ibm.com/docs/assistant?topic=assistant-getting-started)

## Resources


## License

This solution starter is made available under the [Apache 2 License](LICENSE).
