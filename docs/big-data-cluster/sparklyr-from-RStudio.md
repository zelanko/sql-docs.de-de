---
title: Verwenden von sparklyr aus rstudio
titleSuffix: SQL Server big data clusters
description: Stellen Sie eine Verbindung mit Big Data Cluster mithilfe von sparklyr von rstudio her.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 04/08/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f346fed17e4c79214a7eba43f70767fc80b98a07
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/30/2019
ms.locfileid: "67728375"
---
# <a name="use-sparklyr-in-sql-server-big-data-cluster"></a>Verwenden von sparklyr in SQL Server Big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sparklyr stellt eine R-Schnittstelle für Apache Spark bereit. Sparklyr ist eine beliebte Methode für R-Entwickler, Spark zu verwenden. In diesem Artikel wird beschrieben, wie Sie sparklyr in einem SQL Server 2019 Big Data-Cluster (Vorschau) mithilfe von rstudio verwenden.

## <a name="prerequisites"></a>Vorraussetzungen

- Stellen Sie [eine SQL Server 2019 Big Data Cluster](quickstart-big-data-cluster-deploy.md)bereit.

### <a name="install-rstudio-desktop"></a>Installieren von rstudio Desktop

Installieren und konfigurieren Sie **rstudio Desktop** mit den folgenden Schritten:

1. Wenn Sie auf einem Windows-Client ausführen, müssen Sie [R 3.4.4 herunterladen und installieren](https://cran.rstudio.com/bin/windows/base/old/3.4.4).

1. [Laden Sie rstudio Desktop herunter, und installieren Sie](https://www.rstudio.com/products/rstudio/download/)es.

1. Nachdem die Installation abgeschlossen ist, führen Sie die folgenden Befehle in rstudio Desktop aus, um die erforderlichen Pakete zu installieren:

   ```RStudioDesktop
   install.packages("DBI", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("dplyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   install.packages("sparklyr", repos = "https://cran.microsoft.com/snapshot/2019-01-01")
   ```

## <a name="connect-to-spark-in-a-big-data-cluster"></a>Herstellen einer Verbindung mit Spark in einem Big Data Cluster

Mithilfe von Livy und dem HDFS-/Spark-Gateway können Sie mithilfe von sparklyr eine Verbindung zwischen einem Client und dem Big Data Cluster herstellen. 

Erstellen Sie in rstudio ein R-Skript, und stellen Sie eine Verbindung mit Spark her, wie im folgenden Beispiel gezeigt:

> [!TIP]
> Verwenden Sie `<USERNAME>` für `<PASSWORD>` die Werte und den Benutzernamen (z. b. root) und das Kennwort, die Sie während der Bereitstellung des Big Data Clusters festlegen. Informationen zu `<IP>` den `<PORT>` Werten und finden Sie in der Dokumentation zum [Herstellen einer Verbindung mit einem Big Data Cluster](connect-to-big-data-cluster.md).

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

## <a name="run-sparklyr-queries"></a>Ausführen von sparklyr-Abfragen

Nach dem Herstellen einer Verbindung mit Spark können Sie sparklyr ausführen. Im folgenden Beispiel wird eine Abfrage für das IRIS-DataSet mithilfe von sparklyr durchführt:

```r
iris_tbl <- copy_to(sc, iris)

iris_count <- dbGetQuery(sc, "SELECT COUNT(*) FROM iris")

iris_count
```

## <a name="distributed-r-computations"></a>Verteilte R-Berechnungen

Eine Funktion von sparklyr ist die Möglichkeit, [R-Berechnungen](https://spark.rstudio.com/guides/distributed-r/) mit [spark_apply](https://spark.rstudio.com/reference/spark_apply/)zu verteilen.

Da Big Data Cluster Livy-Verbindungen verwenden, müssen Sie `packages = FALSE` im **spark_apply**-Aufrufsatz festlegen. Weitere Informationen finden Sie im [Abschnitt "Livy](https://spark.rstudio.com/guides/distributed-r/#livy) " der sparklyr-Dokumentation zu verteilten R-Berechnungen. Mit dieser Einstellung können Sie nur die r-Pakete verwenden, die bereits in Ihrem Spark-Cluster in dem an **spark_apply**weiter gegebenen r-Code installiert sind. Diese Funktion wird im folgenden Beispiel veranschaulicht:

```r
iris_tbl %>% spark_apply(function(e) nrow(e), names = "nrow", group_by = "Species", packages = FALSE)
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster](big-data-cluster-overview.md).
