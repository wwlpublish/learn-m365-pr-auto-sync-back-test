Azure Synapse Analytics offers various machine learning capabilities. You may be familiar with how a typical data science process looks. It's a well-known process, which most machine learning projects follow. At a high level, the process contains the following steps:

## Data acquisition and understanding

Azure Data Factory, a natively integrated part of Azure Synapse, provides a powerful set of tools available for data ingestion and data orchestration pipelines. This integration allows you to easily build data pipelines to access and transform the data into a format that can be consumed for machine learning.

Depending on where the data is stored, Synapse offers a set of different tools to explore and prepare it for analytics and machine learning. One of the quickest ways to get started with data exploration is using Apache Spark or Synapse SQL serverless pools directly over data in the data lake.

## Modeling

In Azure Synapse, training machine learning models can be performed on the Apache Spark Pools with tools like PySpark/Python, Scala, or .NET. Another way to train machine learning models, that does not require much prior familiarity with machine learning, is to use AutoML. AutoML is a feature that automatically trains a set of machine learning models and allows the user to select the best model based on specific metrics. Thanks to a seamless integration with Azure Machine Learning from Azure Synapse Notebooks, users can easily leverage AutoML in Synapse with passthrough Azure Active Directory authentication.

## Model deployment and scoring

Models that have been trained either in Azure Synapse or outside Azure Synapse can easily be used for batch scoring. Currently in Synapse, there are two ways in which you can run batch scoring.

- You can use the TSQL PREDICT function in Synapse SQL pools to run your predictions right where your data lives. This powerful and scalable function allows you to enrich your data without moving any data out of your data warehouse. You can deploy an ONNX model from the Azure Machine Learning model registry in Synapse SQL Pools for batch scoring.

- Another option for batch scoring machine learning models in Azure Synapse is to leverage the Apache Spark Pools for Azure Synapse.

![Icon indicating play video](../media/video-icon.png) Watch this video to see an example of how to train an Azure Machine Learning model in an Azure Synapse workspace using Apache Spark and a Synapse Notebook.

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Hv0A]

 For more information on Azure Synapse Analytics and machine learning, see: [Machine Learning capabilities in Azure Synapse Analytics (workspaces preview)](/azure/synapse-analytics/machine-learning/what-is-machine-learning)

