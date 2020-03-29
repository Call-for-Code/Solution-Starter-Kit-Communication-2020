# COVID 危機コミュニケーションスターターキット

このソリューションスターターは、IBMの技術者によって作成されました。

## 作成者

- [Donna Byron](https://developer.ibm.com/profiles/dkbyron/) - IBM
- [John Walicki](https://developer.ibm.com/profiles/walicki/) - IBM
- [Matt Price](https://developer.ibm.com/profiles/pricem/) - IBM
- [Mofizur Rahman](https://developer.ibm.com/profiles/mofizur.rahman) - IBM
- [Pooja Mistry](https://developer.ibm.com/profiles/pmistry/) - IBM
- [Upkar Lidder](https://developer.ibm.com/profiles/ulidder/) - IBM

## 目次

1. [概要](#概要)
2. [動画](#動画)
3. [解決案](#解決案)
4. [使い方](#使い方)
5. [構成図](#構成図)
6. [ドキュメント](#ドキュメント)
7. [データセット](#データセット)
8. [テクノロジー](#テクノロジー)
9. [始め方](#始め方)
10. [利用している情報源について](#利用している情報源について)  
11. [ライセンス](#license)

## 概要

### 現状課題
危機的状況では、通信システムは、検査、症状、コミュニティの対応、およびその他のリソースに関する基本的な情報を見つけようとする人々で埋め尽くされます。通信回線が詰まると、本当に助けが必要な人は乗り越えられません。チャットボットは、1日に数十、さらには数百、数千のメッセージに応答するのに役立ちます。

### テクノロジーがどのように役立つのか？

テキスト、電話、ウェブサイト、コミュニケーションアプリのいずれの場合でも、チャットボットや他のAI対応リソースとの会話は、コミュニティが重要な情報をすばやく理解し、カスタマーサービスリソースを解放してより高いレベルの問題に集中できるようにする上で重要な役割を果たすことができます。

IBM Watson Assistantサービスは、会話型対話を構築、トレーニング、および任意のアプリケーション、デバイス、またはチャネルにデプロイするのに役立ちます。 Watson Assistantを使用してチャットボットを作成すると、正確で関連性のある情報を収集する際にユーザーが直面する問題に対処できます。 Covid-19の最新ニュースを学ぶ場合でも、お住まいの地域でテストを実施している場合でも、チャットボットは、コミュニティが重要な情報をすばやく理解し、カスタマーサービスリソースを解放してより高いレベルの問題に集中できるようにする上で大きな役割を果たすことができます。 

## 動画
※ 英語の動画となります。英語が苦手な方は、YouTubeの設定から日本語自動翻訳機能を使って視聴してください。   
[![Call for Code Solution Starter: Water sustainability in the context of climate change ](https://img.youtube.com/vi/WzEj_m0hwF0/0.jpg)](https://www.youtube.com/watch?v=WzEj_m0hwF0)

## 解決案

COVID-19には、症状や検査サイト、学校、交通機関、その他の公共サービスの現状に関する回答を求める市民がいます。 Watson Assistantを使用して、この[Call for Code Starter Kit](https://developer.ibm.com/callforcode/getstarted/covid-19/community-cooperation/)は、COVID-19に関する一般的な質問を理解して応答し、Watson Discoveryを使用してCOVID-19ニュース記事をスキャンし、信頼できるソースからのデータを使用してCOVID統計情報の問い合わせに応答するようにプリロードされた仮想アシスタントを設計しました。

危機コミュニケーションスターターキットを搭載したこのWatson Assistantを使用すると、Slack統合を使用するか、Node-REDダッシュボードを介して、チャットボットをIBM CloudがホストするWebサーバーのCall for Codeソリューションに統合できます。

できること:
- 一貫性のある正確なCOVID-19情報を共有して対応する
- 市民が選択したチャネル（音声、テキスト、またはコラボレーションツール）を通じて最新情報にすばやく簡単にアクセスできる
- COVID-19の一般的な質問への回答を自動化することにより、貴重なリソースを解放する
- 最新の開発と推奨事項で情報を動的に更新する

皆さんにとっての課題は、このフレームワークから構築して、より完全なソリューションを作成することです。

## 使い方


## 構成図

### COVID-19 危機通信チャットボットとのウェブサイト統合

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Nodejs-WebServer.png)

1. ユーザーがCOVID-19チャットボットを使用してWebサイトにアクセスし、質問をします。
2. Node.js Webサーバーが、IBM CloudでホストされているWatson Assistantサービスを呼び出します。
3. Watson Assistantは、自然言語理解と機械学習を使用して、ユーザーの質問のエンティティーと意図を抽出します。
4.信頼できるCDCデータからCOVID-19 FAQ情報を入手します。
5. Watson Assistantは、OpenWhiskオープンソースのIBM Cloud Functionを呼び出します。
6. IBM Cloud Functionは、IBM Cloudで実行されているWatson Discoveryサービスを呼び出します。
7. Watson Discoveryはニュース記事をスキャンし、関連する記事で応答します。
8. Watson Assistantは、OpenWhiskオープンソースのIBM Cloud Functionを呼び出します。
9. IBM Cloud FunctionはCOVID-19 APIを呼び出して統計を取得します。
10. Watson Assistantがユーザーの問い合わせに応答します。
11. Node.js Webサーバーがチャットの回答をユーザーに表示します。

### COVID-19 危機通信チャットボットとのSlack統合

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Slack-Integration.png)

1. ユーザーはCOVID-19 Slack統合チャットボットアプリを呼び出して質問します。
2. Slackアプリが、IBM CloudでホストされているWatson Assistantサービスを呼び出します。
3. Watson Assistantは、自然言語理解と機械学習を使用して、ユーザーの質問のエンティティーと意図を抽出します。
4. 信頼できるCDCデータからCOVID-19 FAQ情報を入手します。
5. Watson Assistantは、OpenWhiskオープンソースのIBM Cloud Functionを呼び出します。
6. IBM Cloud Functionは、IBM Cloudで実行されているWatson Discoveryサービスを呼び出します。
7. Watson Discoveryはニュース記事をスキャンし、関連する記事で応答します。
8. Watson Assistantは、OpenWhiskオープンソースのIBM Cloud Functionを呼び出します。
9. IBM Cloud FunctionはCOVID-19 APIを呼び出して統計を取得します。
10. Watson AssistantがSlackアプリケーションに応答します。
11. Slackアプリがチャットの回答をユーザーに表示します。

### Node-REDを使用した音声対応COVID-19危機通信チャットボット

![Crisis Comms Architecture diagram](/images/Crisis-Comms-Architecture-Node-RED.png)

1. ユーザーは、COVID-19チャットボットを使用して音声対応のNode-RED Webサイトにアクセスし、質問をします。
2. Node-REDがスピーチwavファイルを記録し、IBM CloudでホストされているWatson Speech to Textサービスを呼び出します。
3. Watson Speech to Textは、機械学習を使用してユーザーの音声をデコードします。
4. Watson Speech to TextはCOVID-19質問の筆記録で応答し、Node-REDはIBM CloudでホストされているWatson Assistantサービスを呼び出します。
5. Watson Assistantは、自然言語理解と機械学習を使用して、ユーザーの質問のエンティティーと意図を抽出します。
6.信頼できるCDCデータからCOVID-19 FAQ情報を入手します。
7. Watson Assistantは、OpenWhiskオープンソースのIBM Cloud Functionを呼び出します。
8. IBM Cloud Functionは、IBM Cloudで実行されているWatson Discoveryサービスを呼び出します。
9. Watson Discoveryはニュース記事をスキャンし、関連する記事で応答します。
10. Watson Assistantは、OpenWhiskオープンソースのIBM Cloud Functionを呼び出します。
11. IBM Cloud FunctionはCOVID-19 APIを呼び出して統計を取得します。
12. Watson Assistantがユーザーの問い合わせに応答し、Node-REDがテキストのトランスクリプトをWatson Text to Speechに送信します。
13. Watson Text to Speechは、ユーザーの言語でメッセージをエンコードします。
14. Node-REDがチャット応答wavファイルをユーザーに再生します。
15.ユーザーはチャットの回答を聞きます。

## ドキュメント

### COVID-19に関する信頼できるソース
- [CDC COVID-19 FAQ](https://www.cdc.gov/coronavirus/2019-ncov/faq.html)

### チュートリアルとドキュメント:

- [How-to guides for chatbots(英語)](https://www.ibm.com/watson/how-to-build-a-chatbot)
- [Learning path: Getting started with Watson Assistant (英語)](https://developer.ibm.com/series/learning-path-watson-assistant/)
- [Chatbot with Watson Discovery - GitHub](https://github.com/IBM/watson-discovery-sdu-with-assistant)
- [Slackとの統合](https://cloud.ibm.com/docs/assistant?topic=assistant-deploy-slack)
- [Node-RED Slack Integration (英語)](https://www.ibm.com/cloud/blog/create-a-chatbot-on-ibm-cloud-and-integrate-with-slack-part-1)
- [Train a speech-to-text model (英語)](https://developer.ibm.com/patterns/customize-and-continuously-train-your-own-watson-speech-service/)
- [ダイアログ・ノードからのプログラマチック呼び出しの実行](https://cloud.ibm.com/docs/assistant?topic=assistant-dialog-webhooks)
- [IBM Cloud Voice Agent with Twilio (英語)](https://developer.ibm.com/recipes/tutorials/ibms-voice-agent-with-watson-and-twilio/)
- [Watson Assistant入門](https://cloud.ibm.com/docs/assistant?topic=assistant-getting-started)

## データセット

- [covid19api](https://covid19api.com/)

## テクノロジー

### IBM テクノロジー

- [IBM Watson Assistant](https://www.ibm.com/watson/jp-ja/developercloud/conversation.html)
- [Watson Discovery](https://www.ibm.com/jp-ja/cloud/watson-discovery)
- [Watson Speech to Text](https://www.ibm.com/jp-ja/cloud/watson-speech-to-text)
- [Watson Text to Speech](https://www.ibm.com/jp-ja/cloud/watson-text-to-speech)
- [IBM Cloud Functions](https://www.ibm.com/jp-ja/cloud/functions)

### オープンソーステクノロジー

- [Node.js](https://nodejs.org/en/)
- [Apache OpenWhisk](https://openwhisk.apache.org/)
- [Node-RED](https://nodered.org/)

## 始め方

### 前提条件

- [IBM Cloud](https://ibm.biz/BdzceS) アカウント登録

### Watson Assistantのインスタンスのセットアップ

IBM Cloudにログインし、Watson Assistantインスタンスをプロビジョニングします。

**Step 1.** [IBM Cloud カタログ](https://cloud.ibm.com/catalog/services/watson-assistant) から **Watson Assistant** のインスタンスを画面の流れに沿ってプロビジョニングします。
  ![Watson Assistant Catalog](/starter-kit/assistant/WA-Photo1-JP.png)

**Step 2.**  [Watson Assistantの起動]ボタンからサービスを起動します。

**Step 3.** **Create assistant** をクリックし、アシスタントを作成する方法についての [詳細な手順](https://cloud.ibm.com/docs/assistant?topic=assistant-assistant-add) に従います。
  ![Watson Assistant Photo2 ](/starter-kit/assistant/WA-Photo2.png)

**Step 4.** Watson Assistantインスタンスに **COVID Crisis Communication**という名前を付け、[Create assistant]ボタンで次に進みます。
  ![Watson Assistant Photo3 ](/starter-kit/assistant/WA-Photo3.png)

**Step 5.** **Add Dialog skill** ボタンをクリックしてアシスタントに追加します。操作に関して疑問な点がある場合には [ダイアログ・スキル作成に関するIBM Cloud資料](https://cloud.ibm.com/docs/assistant?topic=assistant-skill-dialog-add) を確認してください。
  ![Watson Assistant Photo4 ](/starter-kit/assistant/WA-Photo4.png)

**Step 6.** **Import skill > Choose JSON file** の順にクリックし、 [`skill-CDC-COVID-FAQ.json`](./starter-kit/assistant/skill-CDC-COVID-FAQ.json) ファイルを指定してから[Import]ボタンをクリックしてください。
  ![Watson Assistant Photo5 ](/starter-kit/assistant/WA-Photo5.png)

**Step 7.** 画面上の矢印からAssistantsページに戻ります。次にアクションメニュー ( **`⋮`** )をクリックして **Settings** を開きます。
  ![Watson Assistant Photo6 ](/starter-kit/assistant/WA-Photo6.png)

**Step 8.** 左側の **API Details** をクリックし、この後に使用するための `Assistant ID` と `Api Key` を書き留めておきます。
  ![Watson Assistant Photo7 ](/starter-kit/assistant/WA-Photo7.png)

**Step 9.**  画面上の[IBM Watson Assistant]から作成したSkillsに戻り、右横の **Preview Link** ボタンをクリックして、アシスタントをテストおよび確認するためのリンクをTry it out and share the linkから取得してアクセスします。
  ![Watson Assistant Photo9 ](/starter-kit/assistant/WA-Photo91.png)

**Step 10.** Watson AssistantチャットボットにCOVID-19について英語で質問します。
<p align="center">
<img width="50%" height="50%" src="https://raw.githubusercontent.com/Call-for-Code/Solution-Starter-Kit-Communication-2020/master/starter-kit/assistant/WA-Photo101.png">
</p>


### webhookを介してチャットボットをデータソースに接続する


Watson Assistant対応のチャットボットを作成したので、それをデータソースに接続する必要があります。 Watson Assistantでは、webhookを介してこれを行う必要があります。

webhookは、プログラムで発生したことに基づいて外部プログラムを呼び出すことができるメカニズムです。ダイアログスキルで使用すると、webhookが有効になっているノードをアシスタントが処理すると、webhookがトリガーされます。 webhookは、指定したデータ、または会話中にユーザーから収集したデータを収集し、コンテキスト変数に保存します。 webhook定義の一部として指定したURLにHTTP POSTリクエストの一部としてデータを送信します。 webhookを受け取るURLがリスナーです。 webhook定義で指定されたとおりに渡された情報を使用して、事前定義されたアクションを実行し、オプションで応答を返すことができます。

[次の手順に従って](./starter-kit/webhook/README_JP.md) プロビジョニングしたばかりのWatson AssistantチャットボットでWebhookをセットアップします。

### COVID-19チャットボットをSlackと統合する

機能しているWatson Assistantが用意できたので、それをSlackにデプロイしましょう。 Slackは、クラウドベースのメッセージングアプリケーションであり、人々が互いに協力するのに役立ちます。ダイアログスキルを設定してアシスタントに追加したら、アシスタントをSlackと統合できます。

統合すると、サポートするようにアシスタントを構成するイベントに応じて、アシスタントは、ダイレクトメッセージまたはアシスタントが直接言及されているチャネルで尋ねられている質問に応答できます。

COVID-19チャットボットをSlackと統合する方法については、[こちらの手順](/starter-kit/slack/README.md) をご覧ください。

![Slack Gif](/starter-kit/slack/readme_images/Slack.gif)

### COVID-19チャットボットをNode-REDと統合する

音声対応のチャットボットを作成したいと考えていますか？  [このチュートルアルではNode-RED](./starter-kit/node-red/README.md) とWatson Assistant、Watson Speech to Text、およびWatson Text to Speechノードを使用して、音声対応チャットボットを作成する方法について説明します。

### Node.js WebサイトにCOVID-19チャットボットを埋め込む

最後に、COVID-19危機通信チャットボットは、Node.jsウェブサイトに埋め込むことができます。

- 操作方法は、[COVID-Simple installation instructions](./starter-kit/covid-simple/README.md)に従ってください。

## 利用している情報源について

このWatson Assistantボットには、以下のリソースから供給されるデータが使用されています:

- 多くの静的応答は、CDCのCOVID FAQページにある情報を提供します: https://www.cdc.gov/coronavirus/2019-ncov/faq.html
- 感染および死亡数は、次のAPIを介してジョンズホプキンス大学から供給されます: https://www.covid19api.com/
- 動的なニュース記事は、IBM Watson Discoveryのニュースフィードから提供されます。サービスに関する追加情報はこちらです: https://www.ibm.com/watson/services/discovery-news/

## ライセンス

このソリューションスターターは、 [Apache 2 License](LICENSE) に基づいて提供されます。
