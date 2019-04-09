---
title: Verwenden Sie Sparklyr von RStudio
titleSuffix: SQL Server big data clusters
description: Verbinden Sie mit big Data-Cluster mithilfe von Sparklyr von RStudio.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 148e4942babafb35af2efe33eb427f9462f0a47e
ms.sourcegitcommit: 2e7686443a61b1a2cf4ca47d9ab1010b9e9b5188
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59291580"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Verwenden Sie Sparklyr in SQL Server-big Data-cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr bietet eine R-Schnittstelle für Apache Spark. Sparklyr ist ein beliebtes Verfahren für die R-Entwicklern mit Spark. Dieser Artikel beschreibt, wie Sie Sparklyr in einer SQL Server-2019 big Data-Cluster (Vorschau) mit RStudio verwenden.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Bereitstellen einen SQL Server-2019 big Data-Cluster](quickstart-big-data-cluster-deploy.md).

### <a name="install-rstudio-desktop"></a>Installieren von RStudio Desktop

Installieren und Konfigurieren von **RStudio Desktop** mit den folgenden Schritten:

1. Wenn Sie auf einem Windows-Client ausführen [herunterladen und Installieren von R 3.4.4](https://cran.rstudio.com/bin/windows/base/old/3.4.4).

1. [Herunterladen und Installieren von RStudio Desktop](https://www.rstudio.com/products/rstudio/download/).

1. Nach Abschluss der Installation führen Sie die folgenden Befehle in RStudio Desktop, um die erforderlichen Pakete zu installieren:

   ```RStudio Desktop install.packages("DBI", repos = "https://cran.microsoft.com/snapshot/2019-01-01") install.packages("dplyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01") install.packages("sparklyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## Connect to Spark in a big data cluster

You can use sparklyr to connect from a client to the big data cluster using Livy and the HDFS/Spark gateway. 

In RStudio, create an R script and connect to Spark as in the following example:

> [!TIP]
> For the `<USERNAME>` and `<PASSWORD>` values, use the username (such as root) and password you set during the big data cluster deployment. For the `<IP>` and `<PORT>` values, see the documentation on the [HDFS/Spark gateway](connect-to-big-data-cluster.md#hdfs).

```r
library(sparklyr)
library(dplyr)
library(DBI)

#Specify the Knox username and password
config <- livy_config(user = "<username>", password = "<password>")

httr::set_config(httr::config(ssl_verifypeer = 0L, ssl_verifyhost = 0L))

sc <- spark_connect(master = "https://<IP>:<PORT>/gateway/default/livy/v1",
                    method = "livy",
                    config = config)
```

## <a name="run-sparklyr-queries"></a>Ausführen von Sparklyr-Abfragen

Nach dem Herstellen einer Verbindung mit Spark, können Sie Sparklyr ausführen. Im folgenden Beispiel wird eine Abfrage auf Iris-Dataset Sparklyr verwenden:

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>Verteilte R-Berechnungen

Eine Funktion von Sparklyr ist die Möglichkeit, [Verteilen von R-Berechnungen](https://spark.rstudio.com/guides/distributed-r/) mit [Spark_apply](https://spark.rstudio.com/reference/spark_apply/).

Da es sich bei big Data-Cluster Livy-Verbindungen verwenden, müssen Sie festlegen `packages = FALSE` im Aufruf von **Spark_apply**. Weitere Informationen finden Sie unter den [Livy-Abschnitt](https://spark.rstudio.com/guides/distributed-r/#livy) Sparklyr Dokumentation für verteilte R-Berechnungen. Mit dieser Einstellung können Sie nur die R-Pakete, die bereits auf Ihrem Spark-Cluster in der R-Code, der an übergebene installiert sind **Spark_apply**. Das folgende Beispiel veranschaulicht diese Funktionalität:

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [was SQL Server-2019 big Data-Cluster sind](big-data-cluster-overview.md).