# Water sustainability in the context of climate change 

This solution starter was created by at the United Nations Human Rights Office in Geneva, Switzerland on February 27-28, 2020. It features contributions by technologists from XXX, YYY, IBM, and Red Hat. 

## Authors

* Jane Jones - RBS
* Janet Jones - IBM

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
The global climate crisis is inextricably linked to water. Higher temperatures and more extreme weather events are projected to affect the availability and distribution of rainfall, snowmelt, river flows, and groundwater, and further deteriorate water quality. Low-income communities, already the most vulnerable to any threats to water supply, are likely to be the worst affected.

Read the [UN policy on climate change and water](https://www.unwater.org/publications/un-water-policy-brief-on-climate-change-and-water/) and understand how you can make a difference.

### How can technology help?
Whether it's third-party open source projects or IBM Cloud services, technologies like data analytics, Internet of Things, artificial intelligence, and blockchain can help address global environmental challenges such as water quantity and quality. Using water more efficiently will reduce greenhouse gases from treatment systems. 

## Video

[![Call for Code Solution Starter: Water sustainability in the context of climate change ](https://img.youtube.com/vi/hC2b-iP6Rxc/0.jpg)](https://www.youtube.com/watch?v=hC2b-iP6Rxc)

## The idea

The team tackled the challenges that come in the process of rebuilding after the impact of a disaster. Research has shown that rapid yet well-informed and well-orchestrated rebuilding measures can help to massively reduce the negative impact of disasters on the life, well-being, and health of individuals. An effective and efficient system of accessing information and contributing feedback in a way that can improve the foundation of future decisions is key to this cycle.

In order to leverage the benefits of such a system it must be designed to allow for simple ingestion of information, data, images along with a user-friendly way of drawing insights from it. The team created a platform-based solution that aggregates and analyzes historical and current data related to infrastructure, agriculture, weather, utility and more. It can then be used to derive key insights for future response and reconstruction plans. 

## How it works

The goal of this solution is to provide a better feedback loop that empowers local municipalities, small business owners, and members of the community, especially the most vulnerable. The team approached this problem by looking how a solution could benefit three potential end users who need access to information about the current situation, resources available to them, and how to better prepare next time:

1. A disaster victim, who seeks information on how to improve her community by best matching her skills to volunteer opportunities.
1. A small business owner who needs to open her shop as soon as possible to restart cash flow.
1. A local elected government official, who needs to generate damage assessments and rebuilding recommendations quickly.

By combining cloud-native infrastructure with event-driven data processing and intelligent modeling, this solution could help predict when and where a disaster may strike next and extrapolate the impact. Furthermore, it could allow stakeholders to derive the most promising course of action with the greatest improvement to plans and processes possible.

## Diagrams

![Challenge 1 Architecture](/images/Challenge_1_Architecture.png?raw=true "Challenge 1 Architecture")

This solution starter idea combines machine learning models with real-time information to get users the information they need to take action quickly.

1. By managing a collection of models about how better to restore infrastructure, the system could store historical data, use that to predict trends, and therefore provide recommendations in the form of an assessment.
1. These models could then be referenced by various applications to collect information about the current situation and provide end users with the assessments.
1. By rating the success of the recommendation, users can provide information that will help others in turn during future situations to build back better.

## Documents

- [Terminology on disaster risk reduction](https://www.unisdr.org/we/inform/terminology)
- [Using global indicators to measure progress](https://www.unisdr.org/files/54970_techguidancefdigitalhr.pdf)

## Datasets

- [Malawi Spatial Data Platform (MASDAP)](http://www.masdap.mw/)
- [Land Usage from MASDAP](http://www.masdap.mw/layers/osm:osm_landusages)
- [Malawi Disaster & Risk Profile](https://www.preventionweb.net/countries/mwi/data/)
- [Disparities in Cellphone Ownership Pose Challenges in Africa](https://news.gallup.com/poll/189269/disparities-cellphone-ownership-pose-challenges-africa.aspx)

## Technology

- [Generate insights from multiple data sources](https://developer.ibm.com/patterns/generate-insights-from-multiple-data-sources-using-watson-studio/)
- [Transform and load big data CSV files into a database](https://developer.ibm.com/patterns/transform-load-big-data-csv-files-db2-zos-database/)
- [2018 Finalist PD3R](https://developer.ibm.com/blogs/call-for-code-finalist-pd3r-uses-artificial-intelligence-for-retrofitting/)

## Getting started

### Prerequisite

You should have a basic understanding of the OpenWhisk programming model. If not, [try the action, trigger, and rule demo first](https://github.com/IBM/openwhisk-action-trigger-rule).

Also, you'll need an IBM Cloud account and the latest [OpenWhisk command line tool (`ibmcloud fn`) installed and on your PATH](https://github.com/IBM/openwhisk-action-trigger-rule/blob/master/docs/OPENWHISK.md).

As an alternative to this end-to-end example, you might also consider the more [basic "building block" version](https://github.com/IBM/openwhisk-rest-api-trigger) of this sample.

### Steps

1. [Provision MySQL](#1-provision-mysql)
2. [Create OpenWhisk actions and mappings](#2-create-openwhisk-actions-and-mappings)
3. [Test API endpoints](#3-test-api-endpoints)
4. [Delete actions and mappings](#4-delete-actions-and-mappings)
5. [Recreate deployment manually](#5-recreate-deployment-manually)

### 1. Provision MySQL

Log into the IBM Cloud and provision a [ClearDB](https://console.ng.bluemix.net/catalog/services/cleardb-mysql-database/) or a [Compose for MySQL](https://console.ng.bluemix.net/catalog/services/compose-for-mysql/) database instance. ClearDB has a free tier for simple testing, while Compose has tiers for larger workloads.

- For [ClearDB](https://console.ng.bluemix.net/catalog/services/cleardb-mysql-database/), log into the ClearDB dashboard, and select the default database created for you. Get the user, password and host information under "Endpoint Information".

- For [Compose](https://console.ng.bluemix.net/catalog/services/compose-for-mysql/), get the information from the `Service Credentials` tab in the IBM Cloud console.

Copy `template.local.env` to a new file named `local.env` and update the `MYSQL_HOSTNAME`, `MYSQL_USERNAME`, `MYSQL_PASSWORD` and `MYSQL_DATABASE` for your MySQL instance.

### 2. Create OpenWhisk actions and mappings

`deploy.sh` is a convenience script reads the environment variables from `local.env` and creates the OpenWhisk actions and API mappings on your behalf. Later you will run these commands yourself.

```bash
./deploy.sh --install
```

> **Note**: If you see any error messages, refer to the [Troubleshooting](#troubleshooting) section below. You can also explore [Alternative deployment methods](#alternative-deployment-methods).

### 3. Test API endpoints

There are four helper scripts that simulate HTTP API clients to create, get, update and delete entities against the `/v1/cat` endpoint.

```bash
# POST /v1/cat {"name": "Tarball", "color": "Black"}
client/cat-post.sh Tarball Black

# GET /v1/cat?id=1
client/cat-get.sh 1 # Or whatever integer ID was returned by the command above

# PUT /v1/cat {"id": 1, "name": "Tarball", "color": "Gray"}
client/cat-put.sh 1 Tarball Gray

# DELETE /v1/cat?id=1
client/cat-delete.sh 1
```

### 4. Delete actions and mappings

Use `deploy.sh` again to tear down the OpenWhisk actions and mappings. You will recreate them step-by-step in the next section.

```bash
./deploy.sh --uninstall
```

## Resources

- [Words into Action guidelines: Build back better in recovery, rehabilitation and reconstruction](https://www.unisdr.org/we/inform/publications/53213)
- [Sendai Framework Priority 4: Build Back Better](https://www.youtube.com/watch?v=mRTlS3ZfljM)
- [Building Back Better: How to Cut Natural Disaster Losses by a Third](https://www.worldbank.org/en/news/press-release/2018/06/18/building-back-better-how-to-cut-natural-disaster-losses-by-a-third)

## License

This solution starter is made available under the [Apache 2 License](LICENSE).
