---
title: Verwenden Sie Sparklyr von RStudio
titleSuffix: SQL Server big data clusters
description: Verbinden Sie mit big Data-Cluster mithilfe von Sparklyr von RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 30b8ddccd01c0e8d9a4eac34f2f504b0d8971af6
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860191"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Verwenden Sie Sparklyr in SQL Server-big Data-cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr bietet eine R-Schnittstelle für Apache Spark. Sparklyr ist die gewünschte Methode für die R-Entwicklern mit Spark. Dieser Artikel beschreibt, wie Sie Sparklyr in einer SQL Server-2019 big Data-Cluster (Vorschau) mit RStudio verwenden.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Bereitstellen einen SQL Server-2019 big Data-Cluster](quickstart-big-data-cluster-deploy.md).
- [Installieren von RStudio](https://www.rstudio.com/)

## <a name="connect-to-spark-in-ss19-big-data-cluster"></a>Herstellen einer Verbindung mit spark in SS19 Big Data-cluster

In RStudio eine RScript erstellen und eine Verbindung mit dem Spark wie folgt. Big Data-Cluster Spark eine Verbindung herstellt, über Livy, die mit erreicht werden kann die [HDFS/Spark-Gateway](connect-to-big-data-cluster.md#hdfs). Verwenden Sie zur Authentifizierung des Benutzernamens und Kennworts, die Sie während der Bereitstellung festlegen.

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "***root***", password = "****")

httr::set_config(httr::config(ssl_verifypeer = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Ausführen von Sparklyr-Abfragen

Nach dem Herstellen einer Verbindung mit Spark, können Sie Sparklyr ausführen. Im folgenden Beispiel wird eine Abfrage auf Iris-Dataset Sparklyr verwenden:

``` r
copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).