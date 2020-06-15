# Adding Webhooks to Watson Assistant

You can query for dynamic data using webhooks in IBM Watson Assistant. Our crisis communication chatbot uses two different sources:

- [Watson Discovery](https://www.ibm.com/cloud/watson-discovery)
- [COVID-19 API](https://covid19api.com/)
- [Weather Company Data](https://weather.com/coronavirus)

## Prerequisites
- Create an [IBM Cloud Account](https://www.ibm.com/account/reg/us-en/signup?formid=urx-42793&eventid=cfc-2020?cm_mmc=OSocial_Blog-_-Audience+Developer_Developer+Conversation-_-WW_WW-_-cfc-2020-ghub-starterkit-communication_ov75914&cm_mmca1=000039JL&cm_mmca2=10008917).
- Create a Watson Assistant COVID-19 crisis communications chatbot. [Follow these instructions](/README.md#getting-started)
- Create a [Weather Company API Account](https://callforcode.weather.com/register/)

### Make use of Discovery to get news information

1. From your IBM Cloud account, go to Watson Discovery.

![Discover Service](./images/discovery-service.png)

2. Create a new lite service.

![Create Discover Service](./images/create-discovery-service.png)

3. Make note of the API key and the URL. You need that in the next steps.

![Credentials](./images/discovery-credentials.png)

4. Open the Watson Discovery NEWS service, which is a prepopulated discovery dataset updated and maintained by the Watson Discovery team. 

![Watson Discovery NEWS](./images/watson-discovery-news.png)

5. From the top right corner, open the API tab. Make note of the Collection ID and Environment ID.

![NEWS Api info](./images/news-api-info.png)

### Get a Weather Company API Key

1. Go to [https://callforcode.weather.com/register/](https://callforcode.weather.com/register/)

2. Signup with your info. Your API key will be emailed to you.

3. Save the API key for future use.

### Creating Cloud Functions

1. In the IBM Cloud catalog, go to [IBM Cloud Functions](https://cloud.ibm.com/functions/).

2. Click **Start Creating**.

![functions](./images/cloud-functions.png)

3. Select **Create Action**.

![create](./images/create-action.png)

4. Name your action. For the Runtime dropdown, select **Node.js 10**.

![environment](./images/create-action-env.png)

5. Replace the code with [action/covid-webhook.js](./action/covid-webhook.js)

![code](./images/code.png)

6. Our code has two main parts. We decide whether to call the COVID-19 API or Watson Discovery based on a parameter sent on the function call. If a query param of `type=api` is set, you call the COVID-19 API on the [summary endpoint](https://api.covid19api.com/summary). 

It returns the data in the following format:

```
{
  Countries: [
    {
      Country: "",
      Slug: "",
      NewConfirmed: 0,
      TotalConfirmed: 0,
      NewDeaths: 0,
      TotalDeaths: 0,
      NewRecovered: 0,
      TotalRecovered: 0
    },
    {
      Country: " Azerbaijan",
      Slug: "-azerbaijan",
      NewConfirmed: 0,
      TotalConfirmed: 0,
      NewDeaths: 0,
      TotalDeaths: 0,
      NewRecovered: 0,
      TotalRecovered: 0
    },
    ...
  ]
}
```

7. If there is specific location (Country/Country Code/US State) selected, you look for that location either using The Weather Company API or in the summary response and return the status for that location.

For example, the response for `type=api` and `location=United States of America` is shown below.

```
{
  "result": "Total Cases: 65778\nTotal Deaths: 942\nTotal Recovered: 361\n\nSource: Johns Hopkins CSSE"
}
```

8. If you want to make a call to the Discovery service, you need to set some parameters that let you call the IAM-enabled service. On the left, click on the **Parameters** tab. Add the following parameters in double quotes: 
    - `api_key` (Discovery API Key)
    - `twcApiKey` (API key from The Weather Company)
    - `url` (Discovery Service URL)
    - `collection_id`
    - `env_id`

![parameters](./images/parameter.png)

9. Enable the action as a web action. To do so, select the **Endpoints** tab on the left. Click the checkbox beside "Enable as Web Action."

![endpoint](./images/endpoint.png)

10. Make note of the HTTP URL. You will use this as the webhook for your assistant. You will have to add `.json` in the end of this url to make it work as a webhook.

![http endpoint](./images/http-endpoint.png)

### Integrate data sources via a Watson Assistant webhook

- For detailed instructions on how to do this, check out our documentation: [Making Programmatic Calls from Watson Assistant](https://cloud.ibm.com/docs/assistant?topic=assistant-dialog-webhooks).

1. Bring up the COVID-19 assistant you created earlier. Find it in your IBM Cloud account under services > IBM Watson Assistant. Open the dialog by clicking the `CDC COVID FAQ` Dialog.

![assistant](./images/assistant.png)

2. Click on **Options** on the left.

![options](./images/options.png)

3. Under Options > Webhooks, in the URL text box, paste the URL from the Cloud Funciton step. Make sure to add a `.json` at the end of the URL.

![url](./images/add-url.png)

4. Select **Dialog** on the left navigation.

![dialog](./images/dialog.png)

5. Open up any dialog node you want to add a webhook call for. 

6. After selecting the node, click **Customize**.

![customize](./images/customize.png)

7. Enable Webhooks by moving the toggle button to **On** in the Webhooks section. Click **Save**.

![webhooks](./images/enable-webhook.png)

8. Add any parameter your webhook needs. These will be sent as query parameters.

![webhook parameters](./images/webhook-parameter.png)

9. Test that your webhook integration is working by going to the Try It tab and initiating a dialog that calls the webhook.

![webhook test](./images/webhook-test.png)

You can easily use webhooks to give your Watson Assistant access to many external APIs and databases.
