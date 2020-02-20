---
title: Machine Learning Services (Python, R)
titleSuffix: SQL Server Big Data Clusters
description: Hier erfahren Sie, wie Sie Python- und R-Skripts auf der Masterinstanz eines SQL Server-Big Data-Clusters mit Machine Learning Services ausführen können.
author: dphansen
ms.author: davidph
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
ms.openlocfilehash: e16304765e5f4a51feed4d3d59e790505baa740d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75252025"
---
# <a name="run-python-and-r-scripts-with-machine-learning-services-on-sql-server-big-data-clusters"></a>Ausführen von Python- und R-Skripts mit Machine Learning Services auf SQL Server-Big Data-Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Sie können Python- und R-Skripts auf der Masterinstanz eines [SQL Server-Big Data-Clusters](big-data-cluster-overview.md) mit [Machine Learning Services](../advanced-analytics/index.yml) ausführen.

> [!NOTE]
> Sie können mit den [SQL Server-Spracherweiterungen](../language-extensions/language-extensions-overview.md) auch Java-Code auf der Masterinstanz ausführen. Wenn Sie die folgenden Schritte befolgen, werden auch die Spracherweiterungen aktiviert.

## <a name="enable-machine-learning-services"></a>Aktivieren von Machine Learning Services

Machine Learning Services wird standardmäßig in Big Data-Clustern installiert und erfordert keine separate Installation.

Führen Sie diese Anweisung auf der Masterinstanz aus, um Machine Learning Services zu aktivieren:

```sql
EXEC sp_configure 'external scripts enabled', 1
RECONFIGURE WITH OVERRIDE
GO
```

## <a name="enable-always-on-availability-groups"></a>Aktivieren von AlwaysOn-Verfügbarkeitsgruppen

Wenn Sie SQL Server-Big Data-Cluster mit [Always On-Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) verwenden, sind für die Aktivierung von Machine Learning Services zusätzliche Schritte erforderlich.

1. Stellen Sie eine Verbindung mit der Masterinstanz her, und führen Sie diese Anweisung aus:

    ```sql
    SELECT @@SERVERNAME
    ```

    Notieren Sie sich den Servernamen. In diesem Beispiel lautet der Servername der Masterinstanz **master-2**.

1. Führen Sie für jedes Replikat in der Always On-Verfügbarkeitsgruppe im Big Data-Cluster diese `kubectl`-Befehle aus:

    ```
    kubectl -n bdc expose pod master-0 --port=1533 --name=mymaster-0 --type=LoadBalancer

    kubectl -n bdc expose pod master-1 --port=1533 --name=mymaster-1 --type=LoadBalancer

    kubectl -n bdc expose pod master-2 --port=1533 --name=mymaster-2 --type=LoadBalancer
    ```

    Daraufhin sollte eine Ausgabe ähnlich der folgenden angezeigt werden:
    
    ```
    service/mymaster-0 exposed

    service/mymaster-1 exposed

    service/mymaster-2 exposed
    ```

1. Stellen Sie eine Verbindung mit jedem Masterreplikatendpunkt her, und aktivieren Sie die Skriptausführung.

    Führen Sie diese Anweisung aus:

    ```sql
    EXEC sp_configure 'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    GO
    ```

Sie können nun Python- und R-Skripts auf der Masterinstanz von Big Data-Clustern ausführen. In den folgenden Schnellstarts erfahren Sie, wie Sie das erste Skript ausführen können.

## <a name="next-steps"></a>Nächste Schritte

+ [Schnellstart: Erstellen und Ausführen einfacher Python-Skripts mit SQL Server-Machine Learning Services](../advanced-analytics/tutorials/quickstart-python-create-script.md)
+ [Schnellstart: Erstellen und Bewerten eines Vorhersagemodells in Python mit SQL Server Machine Learning Services](../advanced-analytics/tutorials/quickstart-python-train-score-model.md)
+ [Schnellstart: Erstellen und Ausführen einfacher R-Skripts mit SQL Server-Machine Learning Services](../advanced-analytics/tutorials/quickstart-r-create-script.md)
+ [Schnellstart: Erstellen und Bewerten eines Vorhersagemodells in R mit SQL Server-Machine Learning Services](../advanced-analytics/tutorials/quickstart-r-train-score-model.md)
