---
title: Verwenden Sie Sparklyr von RStudio
titleSuffix: SQL Server 2019 big data clusters
description: Verbinden Sie mit Big Data-Cluster mithilfe von Sparklyr von RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 83980f9d08a3894b0fbf7871cf899483e06702c4
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018356"
---
# <a name="use-sparklyr-in-sql-server-2019-big-data-cluster"></a>Verwenden Sie Sparklyr in SQL Server 2019 Big Data-cluster

Sparklyr bietet eine R-Schnittstelle für Apache Spark. Sparklyr ist die gewünschte Methode für die R-Entwicklern mit Spark. Dieser Artikel beschreibt, wie Sie Sparklyr in einer SQL Server-2019 big Data-Cluster (Vorschau) mit RStudio verwenden.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Bereitstellen einen SQL Server-2019 big Data-Cluster](quickstart-big-data-cluster-deploy.md).
- [Installieren von RStudio](https://www.rstudio.com/)

## <a name="connect-to-spark-in-ss19-big-data-cluster"></a>Herstellen einer Verbindung mit spark in SS19 Big Data-cluster

In RStudio eine RScript erstellen und eine Verbindung mit dem Spark wie folgt. Spark-Big Data-Cluster eine Verbindung herstellt, über Livy, die mit erreicht werden kann die [HDFS/Spark-Gateway](connect-to-big-data-cluster.md#hdfs). Verwenden Sie zur Authentifizierung des Benutzernamens und Kennworts, die Sie während der Bereitstellung festlegen.

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