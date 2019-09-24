---
title: 'Tutorial: Bereitstellen eines Modells in python zum Kategorisieren von Kunden'
description: Im vierten Teil dieser vierteiligen tutorialreihe stellen Sie in Python ein Clustering-Modell mit SQL Server Machine Learning Services bereit.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/27/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: eef8a0f0f11e6d9085a1685145e4c6815979470d
ms.sourcegitcommit: 9221a693d4ab7ae0a7e2ddeb03bd0cf740628fd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71199356"
---
# <a name="tutorial-deploy-a-model-in-python-to-categorize-customers-with-sql-server-machine-learning-services"></a>Tutorial: Bereitstellen eines Modells in python zum Kategorisieren von Kunden mit SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im vierten Teil dieser vierteiligen tutorialreihe stellen Sie ein Clusteringmodell, das in Python entwickelt wurde, in einer SQL-Datenbank mithilfe SQL Server Machine Learning Services bereit.

Um Clustering regelmäßig durchzuführen, müssen Sie in der Lage sein, das Python-Skript von jeder App aus aufzurufen, wenn sich neue Kunden registrieren. Hierzu können Sie das Python-Skript in SQL Server bereitstellen, indem Sie das Python-Skript in einer gespeicherten SQL-Prozedur in der-Datenbank platzieren. Da das Modell in der SQL-Datenbank ausgeführt wird, kann es problemlos mit Daten trainiert werden, die in der Datenbank gespeichert sind.

In diesem Abschnitt verschieben Sie den Python-Code, den Sie soeben geschrieben haben, in SQL Server und stellen Clustering mithilfe von SQL Server Machine Learning Services bereit.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Erstellen einer gespeicherten Prozedur, die das Modell generiert
> * Clustering in SQL Server ausführen
> * Verwenden der Clustering-Informationen

In [Teil 1](python-clustering-model.md)haben Sie die erforderlichen Komponenten installiert und die Beispieldatenbank wieder hergestellt.

In [Teil 2](python-clustering-model-prepare-data.md)haben Sie gelernt, wie Sie die Daten aus einer SQL-Datenbank für die Durchführung von Clustering vorbereiten.

In [Teil 3](python-clustering-model-build.md)haben Sie gelernt, wie Sie ein K-Means-Clustering-Modell in python erstellen und trainieren.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Teil 4 dieser tutorialreihe geht davon aus, dass Sie die Voraussetzungen von [**Teil 1**](python-clustering-model.md)erfüllt haben, und hat die Schritte in [**Teil 2**](python-clustering-model-prepare-data.md) und [**Teil 3**](python-clustering-model-build.md)ausgeführt.

## <a name="create-a-stored-procedure-that-generates-the-model"></a>Erstellen einer gespeicherten Prozedur, die das Modell generiert

Führen Sie das folgende T-SQL-Skript aus, um die gespeicherte Prozedur zu erstellen. Mit dem Verfahren werden die Schritte neu erstellt, die Sie in den Teilen 1 und 2 dieser tutorialreihe entwickelt haben:

* Klassifizieren von Kunden basierend auf Ihrem Kauf-und Rückgabe Verlauf
* Generieren von vier Clustern von Kunden mithilfe eines K-Means-Algorithmus

```sql
USE [tpcxbb_1gb]
GO

CREATE procedure [dbo].[py_generate_customer_return_clusters]
AS

BEGIN
    DECLARE

-- Input query to generate the purchase history & return metrics
     @input_query NVARCHAR(MAX) = N'
SELECT
  ss_customer_sk AS customer,
  CAST( (ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) ) AS FLOAT) AS orderRatio,
  CAST( (ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) ) AS FLOAT) AS itemsRatio,
  CAST( (ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) ) AS FLOAT) AS monetaryRatio,
  CAST( (COALESCE(returns_count, 0)) AS FLOAT) AS frequency
FROM
  (
    SELECT
      ss_customer_sk,
      -- return order ratio
      COUNT(distinct(ss_ticket_number)) AS orders_count,
      -- return ss_item_sk ratio
      COUNT(ss_item_sk) AS orders_items,
      -- return monetary amount ratio
      SUM( ss_net_paid ) AS orders_money
    FROM store_sales s
    GROUP BY ss_customer_sk
  ) orders
  LEFT OUTER JOIN
  (
    SELECT
      sr_customer_sk,
      -- return order ratio
      count(distinct(sr_ticket_number)) as returns_count,
      -- return ss_item_sk ratio
      COUNT(sr_item_sk) as returns_items,
      -- return monetary amount ratio
      SUM( sr_return_amt ) AS returns_money
    FROM store_returns
    GROUP BY sr_customer_sk
  ) returned ON ss_customer_sk=sr_customer_sk
 '

EXEC sp_execute_external_script
      @language = N'Python'
    , @script = N'

import pandas as pd
from sklearn.cluster import KMeans

#get data from input query
customer_data = my_input_data

#We concluded in step 2 in the tutorial that 4 would be a good number of clusters
n_clusters = 4

#Perform clustering
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orderRatio","itemsRatio","monetaryRatio","frequency"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
    , @input_data_1 = @input_query
    , @input_data_1_name = N'my_input_data'
             with result sets (("Customer" int, "orderRatio" float,"itemsRatio" float,"monetaryRatio" float,"frequency" float,"cluster" float));
END;
GO
```

## <a name="perform-clustering-in-sql-database"></a>Ausführen von Clustering in SQL-Datenbank

Nachdem Sie die gespeicherte Prozedur erstellt haben, führen Sie das folgende Skript aus, um mithilfe des Verfahrens Clustering auszuführen.

```sql
--Create a table to store the predictions in

DROP TABLE IF EXISTS [dbo].[py_customer_clusters];
GO

CREATE TABLE [dbo].[py_customer_clusters] (
    [Customer] [bigint] NULL
  , [OrderRatio] [float] NULL
  , [itemsRatio] [float] NULL
  , [monetaryRatio] [float] NULL
  , [frequency] [float] NULL
  , [cluster] [int] NULL
  ,
    ) ON [PRIMARY]
GO

--Execute the clustering and insert results into table
INSERT INTO py_customer_clusters
EXEC [dbo].[py_generate_customer_return_clusters];

-- Select contents of the table to verify it works
SELECT * FROM py_customer_clusters;
```

## <a name="use-the-clustering-information"></a>Verwenden der Clustering-Informationen

Da Sie die Clustering-Prozedur in der-Datenbank gespeichert haben, können Sie das Clustering effizient für Kundendaten ausführen, die in derselben Datenbank gespeichert sind. Sie können die Prozedur immer dann ausführen, wenn Ihre Kundendaten aktualisiert werden und die aktualisierten Clustering-Informationen verwendet werden.

Angenommen, Sie möchten eine Werbe-e-Mail an Kunden in Cluster 0, der inaktiven Gruppe, senden (Sie können sehen, wie die vier Cluster in den [drei Teil](python-clustering-model-build.md#analyze-the-results) dieses Tutorials beschrieben wurden). Der folgende Code wählt die e-Mail-Adressen von Kunden in Cluster 0 aus.

```sql
USE [tpcxbb_1gb]
--Get email addresses of customers in cluster 0 for a promotion campaign
SELECT customer.[c_email_address], customer.c_customer_sk
  FROM dbo.customer
  JOIN
  [dbo].[py_customer_clusters] as c
  ON c.Customer = customer.c_customer_sk
  WHERE c.cluster = 0
```

Sie können den Wert von **c. Cluster** ändern, um e-Mail-Adressen für Kunden in anderen Clustern zurückzugeben.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie mit diesem Tutorial fertig sind, können Sie die tpcxbb_1gb-Datenbank aus SQL Server löschen.

## <a name="next-steps"></a>Nächste Schritte

Im vierten Teil dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Erstellen einer gespeicherten Prozedur, die das Modell generiert
* Clustering in SQL Server ausführen
* Verwenden der Clustering-Informationen

Weitere Informationen zur Verwendung von python in SQL Server Machine Learning Services finden Sie unter:

* [Schnellstart: Erstellen und Ausführen einfacher python-Skripts mit SQL Server Machine Learning Services](quickstart-python-create-script.md)
* [Weitere Python-Tutorials für SQL Server Machine Learning Services](sql-server-python-tutorials.md)
* [Installieren von Python-Paketen mit sqlmlutils](../package-management/install-additional-python-packages-on-sql-server.md)

