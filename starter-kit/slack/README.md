# Integrating with Slack 

This tutorial shows you step-by-step instructions for how to get your COVID Crisis Communication Assistant up and running with Slack. The end result will look something like this:

![Slack Gif](https://github.com/Call-for-Code/Solution-Starter-Kit-Communication-2020/blob/master/starter-kit/slack/readme_images/Slack.gif)

## Learning objectives

In this tutorial, you will:

- Learn about building a Slack App 
- Integrate your Slack App with Watson Assistant
- Build a Call for Code COVID-19 Crisis Communications Slack-enabled chatbot solution

## Prerequisites

To complete the steps in this tutorial you need:

- A Slack workspace with administrative rights. [Learn how to create your Slack workspace](https://slack.com/help/articles/206845317-Create-a-Slack-workspace).
- A [Watson Assistant COVID Crisis Communication Chatbot](https://github.com/Call-for-Code/Solution-Starter-Kit-Communication-2020#getting-started)

Now, I'll show you how to integrate your Slack workspace with your COVID-19 chatbot.

## Integrate Slack and your chatbot

### Step 1. 

Go to your COVID-19 Crisis Communications Assistant and click **Add Integration**.

![Slack Integration Photo1 ](/starter-kit/slack/readme_images/Slack-Photo1.png)

### Step 2.
In the Watson Assistant UI, scroll down to the section for "Third-party integration" and select **Slack**.

![Slack Integration Photo2 ](/starter-kit/slack/readme_images/Slack-Photo2.png)

### Step 3.
First, you need to create a [Slack App](https://api.slack.com/apps). Click on **Create New App**, name your application, and point to a Slack development workspace. Learn more about creating slack apps [here](https://api.slack.com/start).

![Slack Integration Photo3 ](/starter-kit/slack/readme_images/Slack-Photo3.png)

### Step 4.
On the Slack app Settings page, go to the **Basic Information** tab and find the **App Credentials** section. Copy your verification token from that section.

![Slack Integration Photo4 ](/starter-kit/slack/readme_images/Slack-Photo4.png)

Paste the verification token from step 4 and paste it into the appropriate area of Step 2 on Watson Assistant Slack integration page:

![Slack Integration Photo5 ](/starter-kit/slack/readme_images/Slack-Photo5.png)

(Optional): Upload an App Icon and App Name in the Display information section of the **Basic Information** tab:

![Slack Integration Photo- ](/starter-kit/slack/readme_images/Slack-Photo.png)

### Step 5.
Go to the **OAuth & Permissions tab**. In the **Bot Token Scopes** section, click **Add an Oauth Scope**, and then select the following scopes:`app_mentions:read` `chat:write` `im:history` `im:read` `im:write`.

![Slack Integration Photo6 ](/starter-kit/slack/readme_images/Slack-Photo6.png)

### Step 6.
On the **OAuth & Permissions** tab, click **Install App to Workspace**, and then click **Allow**. You should be redirected back to the OAuth & Permissions page.

![Slack Integration Photo7 ](/starter-kit/slack/readme_images/Slack-Photo7.png)

**Note** Make sure you copy your Bot User OAuth access token (`starts with xoxb`)  to both of the fields in **section 3** of Step 2 on Watson Assistant Slack integration page 
 
![Slack Integration Photo8 ](/starter-kit/slack/readme_images/Slack-Photo8.png)


### Step 7.
On the Slack app settings page, go to the **Event Subscriptions** tab. Switch the **Enable Events** toggle to the On position. Go to Step 3 of the Watson Assistant Slack Integration page, click **Generate Requestt URL**. Paste the requested URL and verify its accuracy on the **Enable Events** page.

![Slack Integration Photo9 ](/starter-kit/slack/readme_images/Slack-Photo9.png)

### Step 8.
On the Event Subscriptions tab, find the Subscribe to Bot Events section. Click **Add Bot User Event**, and then select the event types you want to subscribe to. You must select at least one of the following types: 

* `message.im`: Listens for message events that are posted in a direct message channel. 
* `app_mention`: Listens for only message events that mention your app or bot.

Make sure you save your changes.

![Slack Integration Photo10 ](/starter-kit/slack/readme_images/Slack-Photo10.png)

### Step 9.
On the **App Home** tab. Click **Edit** and enter a display name and default username for your virtual assistant. Click **Save**. Enable the **Always Show My Bot as Online** toggle:

![Slack Integration Photo11 ](/starter-kit/slack/readme_images/Slack-Photo11.png)

### Step 10.
On Watson Assistant Slack Integration page click **Save Changes**.

### Step 11.
Log into your Slack workspace and click on **Browse App**. Find the app you just created and add to your workspace:

![Slack Integration Photo12 ](/starter-kit/slack/readme_images/Slack-Photo12.png)

### Step 12.
Test your application by asking questions based on intents and entities in your dialog tree! If you recieve answers back you have successfully integrated your COVID Crisis Communication Assistant! Congratulations. 
