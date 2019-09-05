---
title: 'Tutorial: Vorbereiten von Daten zum Kategorisieren von Kunden in python'
description: Im Teil 2 dieser vierteiligen tutorialreihe bereiten Sie die Daten aus einer SQL Server Datenbank vor, um das Clustering in Python mit SQL Server Machine Learning Services durchzuführen.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/30/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d91f3b9f1e3d1abe53d677d9f9058058d321d985
ms.sourcegitcommit: 26715b4dbef95d99abf2ab7198a00e6e2c550243
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294345"
---
# <a name="tutorial-prepare-data-to-categorize-customers-in-python-with-sql-server-machine-learning-services"></a>Tutorial: Vorbereiten von Daten zum Kategorisieren von Kunden in Python mit SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Im Teil 2 dieser vierteiligen tutorialreihe stellen Sie die Daten aus einer SQL-Datenbank mithilfe von python wieder her. Später in dieser Reihe verwenden Sie diese Daten zum trainieren und Bereitstellen eines Clusteringmodells in Python mit SQL Server Machine Learning Services.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Trennen von Kunden in verschiedenen Dimensionen mithilfe von python
> * Laden der Daten aus der SQL-Datenbank in einen python-Datenrahmen

In [Teil 1](python-clustering-model.md)haben Sie die erforderlichen Komponenten installiert und die Beispieldatenbank wieder hergestellt.

In [Teil 3](python-clustering-model-build.md)erfahren Sie, wie Sie ein K-Means-Clustering-Modell in python erstellen und trainieren.

In [Teil 4](python-clustering-model-deploy.md)erfahren Sie, wie Sie eine gespeicherte Prozedur in einer SQL-Datenbank erstellen, die basierend auf neuen Daten Clustering in python durchführen kann.

## <a name="prerequisites"></a>Erforderliche Komponenten

* In Teil 2 dieses Tutorials wird davon ausgegangen, dass Sie die Voraussetzungen von [**Teil 1**](python-clustering-model.md)erfüllt haben.

## <a name="separate-customers"></a>Getrennte Kunden

Um sich auf Clustering-Kunden vorzubereiten, trennen Sie die Kunden zuerst in den folgenden Dimensionen:

* **orderratio** = Verhältnis der Rückgabe Reihenfolge (Gesamtzahl der Bestellungen, die teilweise oder vollständig zurückgegeben wurden, und die Gesamtzahl der
* **itemsratio** = Verhältnis von Rückgabe Elementen (Gesamtzahl der zurückgegebenen Elemente im Vergleich zur Anzahl erworbener Elemente)
* **monetaryratio** = Verhältnis der Rückgabe Menge (Gesamtbetrag der zurückgegebenen Elemente im Vergleich zum erworbenen Betrag)
* **Frequency** = Rückgabe Häufigkeit

Öffnen Sie ein neues Notebook in Azure Data Studio, und geben Sie das folgende Skript ein.

Ersetzen Sie in der Verbindungs Zeichenfolge die Verbindungsdetails nach Bedarf.

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

## <a name="load-the-data-into-a-data-frame"></a>Laden der Daten in einen Datenrahmen

Die Ergebnisse der Abfrage werden mithilfe der revoscalepy **rxsqlserverdata** -Funktion an python zurückgegeben. Im Rahmen des Prozesses verwenden Sie die Spalten Informationen, die Sie im vorherigen Skript definiert haben.

```python
data_source = revoscale.RxSqlServerData(sql_query=input_query, column_Info=column_info,
                                        connection_string=conn_str)
revoscale.RxInSqlServer(connection_string=conn_str, num_tasks=1, auto_cleanup=False)
# import data source and convert to pandas dataframe.
customer_data = pd.DataFrame(revoscale.rx_import(data_source))
```

Zeigen Sie nun den Anfang des Daten Rahmens an, um zu überprüfen, ob er korrekt aussieht.

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

Wenn Sie dieses Tutorial nicht fortsetzen möchten, löschen Sie die tpcxbb_1gb-Datenbank aus SQL Server.

## <a name="next-steps"></a>Nächste Schritte

Im Teil 2 dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Trennen von Kunden in verschiedenen Dimensionen mithilfe von python
* Laden der Daten aus der SQL-Datenbank in einen python-Datenrahmen

Um ein Machine Learning-Modell zu erstellen, das diese Kundendaten verwendet, befolgen Sie die folgenden drei Schritte:

> [!div class="nextstepaction"]
> [Tutorial: Erstellen eines Vorhersagemodells in Python mit SQL Server Machine Learning Services](python-clustering-model-build.md)
