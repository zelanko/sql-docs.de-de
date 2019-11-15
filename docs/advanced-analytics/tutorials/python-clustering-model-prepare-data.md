---
title: 'Python-Tutorial: Vorbereiten von Clusterdaten'
description: Im zweiten Teil dieser vierteiligen Tutorialreihe bereiten Sie die Daten aus einer SQL Server-Datenbank-Instanz für das Clustering in Python mit SQL Server-Machine Learning Services vor.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 11c24d5403e6540da52ec3557c64e1dc8fa57c78
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727089"
---
# <a name="tutorial-prepare-data-to-categorize-customers-in-python-with-sql-server-machine-learning-services"></a>Lernprogramm: Vorbereiten von Daten zur Kategorisierung von Kunden in Python mit SQL Server-Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im zweiten Teil dieser vierteiligen Tutorialreihe stellen Sie Daten aus einer SQL-Datenbank mithilfe von Python wieder her und bereiten diese vor. Diese Daten verwenden Sie in einem späteren Teil dieser Reihe zum Trainieren und Bereitstellen eines linearen Clustermodells in Python mit SQL Server-Machine Learning Services.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Aufteilen von Kunden über verschiedene Dimensionen mit Python
> * Laden der Daten aus SQL-Datenbank in einen Python-Datenrahmen

In [Teil 1](python-clustering-model.md) haben Sie die Voraussetzungen installiert und die Beispieldatenbank wiederhergestellt.

In [Teil 3](python-clustering-model-build.md) erfahren Sie, wie Sie ein k-Means-Algorithmusmodell in Python erstellen und trainieren.

In [Teil 4](python-clustering-model-deploy.md) erfahren Sie, wie Sie eine gespeicherte Prozedur in einer SQL-Datenbank-Instanz erstellen, die in Python Clustering auf der Grundlage neuer Daten durchführen kann.

## <a name="prerequisites"></a>Voraussetzungen

* Teil 2 dieses Tutorials setzt voraus, dass Sie die Voraussetzungen von [**Teil 1**](python-clustering-model.md) erfüllt haben.

## <a name="separate-customers"></a>Aufteilen von Kunden

Sie werden zunächst Kunden nach den folgenden Dimensionen aufteilen, um sich auf das Clustering von Kunden vorzubereiten:

* **orderRatio** = Retourenauftragsquote (Gesamtzahl der teilweise oder vollständig zurückgegebenen Aufträge im Vergleich zur Gesamtzahl der Aufträge)
* **itemsRatio** = Retourenquote (Gesamtzahl der zurückgegebenen Artikel im Vergleich zur Anzahl der gekauften Artikel)
* **monetaryRatio** = Retourenbetragsquote (Gesamtbetrag der zurückgegebenen Artikel im Vergleich zum gekauften Betrag)
* **frequency** = Retourenfrequenz

Öffnen Sie ein neues Notebook in Azure Data Studio, und geben Sie das folgende Skript ein.

Ersetzen Sie bei Bedarf die Verbindungsdetails in der Verbindungszeichenfolge.

```python
# Load packages.
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import revoscalepy as revoscale
from scipy.spatial import distance as sci_distance
from sklearn import cluster as sk_cluster

################################################################################################

## Connect to DB and select data

################################################################################################

# Connection string to connect to SQL Server named instance.
conn_str = 'Driver=SQL Server;Server=localhost;Database=tpcxbb_1gb;Trusted_Connection=True;'

input_query = '''SELECT
ss_customer_sk AS customer,
ROUND(COALESCE(returns_count / NULLIF(1.0*orders_count, 0), 0), 7) AS orderRatio,
ROUND(COALESCE(returns_items / NULLIF(1.0*orders_items, 0), 0), 7) AS itemsRatio,
ROUND(COALESCE(returns_money / NULLIF(1.0*orders_money, 0), 0), 7) AS monetaryRatio,
COALESCE(returns_count, 0) AS frequency
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
GROUP BY sr_customer_sk ) returned ON ss_customer_sk=sr_customer_sk'''


# Define the columns we wish to import.
column_info = {
    "customer": {"type": "integer"},
    "orderRatio": {"type": "integer"},
    "itemsRatio": {"type": "integer"},
    "frequency": {"type": "integer"}
}
```

## <a name="load-the-data-into-a-data-frame"></a>Laden der Daten in einem neuen Datenrahmen

Die Ergebnisse der Abfrage werden mit der revoscalepy-Funktion **RxSqlServerData** an Python zurückgegeben. Als Teil des Prozesses verwenden Sie die Spalteninformationen, die Sie im vorherigen Skript definiert haben.

```python
data_source = revoscale.RxSqlServerData(sql_query=input_query, column_Info=column_info,
                                        connection_string=conn_str)
revoscale.RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)
# import data source and convert to pandas dataframe.
customer_data = pd.DataFrame(revoscale.rx_import(data_source))
```

Zeigen Sie nun den Anfang des Datenrahmens an, um sicherzustellen, dass er korrekt ist.

```python
print("Data frame:", customer_data.head(n=5))
```

```results
Rows Read: 37336, Total Rows Processed: 37336, Total Chunk Time: 0.172 seconds
Data frame:     customer  orderRatio  itemsRatio  monetaryRatio  frequency
0    29727.0    0.000000    0.000000       0.000000          0
1    97643.0    0.068182    0.078176       0.037034          3
2    57247.0    0.000000    0.000000       0.000000          0
3    32549.0    0.086957    0.068657       0.031281          4
4     2040.0    0.000000    0.000000       0.000000          0
```

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie mit diesem Tutorial nicht fortfahren möchten, löschen Sie die tpcxbb_1gb-Datenbank aus SQL Server.

## <a name="next-steps"></a>Nächste Schritte

In Teil 2 dieser Tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Aufteilen von Kunden über verschiedene Dimensionen mit Python
* Laden der Daten aus SQL-Datenbank in einen Python-Datenrahmen

Befolgen Sie Teil 3 dieser Tutorialreihe, um ein Machine Learning-Modell zu erstellen, das diese Kundendaten verwendet:

> [!div class="nextstepaction"]
> [Tutorial: Erstellen eines Modells in Python zum Kategorisieren von Kunden mit SQL Server-Machine Learning Services](python-clustering-model-build.md)
