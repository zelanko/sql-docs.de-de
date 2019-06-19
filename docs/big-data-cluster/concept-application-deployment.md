---
title: Was ist die Bereitstellung einer Anwendung?
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt die Bereitstellung einer Anwendung auf einem SQL Server-2019 big Data-Cluster (Vorschau).
author: jterh
ms.author: jroth
manager: jroth
ms.date: 03/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 1a6ba9caed2b01abc50e16e34d1a13413af2d0ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801855"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>Was ist die Bereitstellung einer Anwendung auf einem SQL Server-2019 big Data-Cluster?

Bereitstellung einer Anwendung ermöglicht die Bereitstellung von Anwendungen auf die big Data-Cluster durch die Bereitstellung von Schnittstellen zum Erstellen, verwalten und Ausführen von Anwendungen. Auf die big Data-Cluster bereitgestellte Anwendungen profitieren, die rechenleistung des Clusters, und es stehen die Daten, die im Cluster verfügbar ist. Dies erhöht die Skalierbarkeit und Leistung von Anwendungen, bei der Verwaltung von Anwendungen, in denen die Daten befinden.
Die folgenden Abschnitte beschreiben die Architektur und die Funktionalität der Anwendungsbereitstellung.

## <a name="application-deployment-architecture"></a>Anwendungsarchitektur für die Bereitstellung

Bereitstellung einer Anwendung besteht aus einem Controller und app-Runtime-Handler. Beim Erstellen einer Anwendung, eine Datei (`spec.yaml`) bereitgestellt wird. Dies `spec.yaml` Datei enthält alles, was der Controller, um die Anwendung erfolgreich bereitzustellen wissen muss. Folgendes ist ein Beispiel für die Inhalte für `spec.yaml`:

```yaml
#spec.yaml
name: add-app #name of your python script
version: v1  #version of the app
runtime: Python #the language this app uses (R or Python)
src: ./add.py #full path to the location of the app
entrypoint: add #the function that will be called upon execution
replicas: 1  #number of replicas needed
poolsize: 1  #the pool size that you need your app to scale
inputs:  #input parameters that the app expects and the type
  x: int
  y: int
output: #output parameter the app expects and the type
  result: int
```

Der Controller überprüft die `runtime` im angegebenen die `spec.yaml` Datei und den entsprechenden Common Language Runtime-Handler aufruft. Der Handler für die Laufzeit erstellt die Anwendung. Zuerst wird ein Kubernetes ReplicaSet erstellt mit einem oder mehreren Pods, von die jede die Anwendung bereitgestellt werden, enthält. Die Anzahl von Pods wird definiert, durch die `replicas` -Parametersatz in die `spec.yaml` Datei für die Anwendung. Jedem Pod kann es sich um eine weitere Pools aufweisen. Die Anzahl der Pools wird von definiert die `poolsize` -Parametersatz in die `spec.yaml` Datei.

Diese Einstellungen haben Auswirkungen auf die Menge der Anforderungen, die die Bereitstellung parallel verarbeiten kann. Die maximale Anzahl von Anforderungen zu einem bestimmten Zeitpunkt ist gleich `replicas` Zeiten `poolsize`. Wenn Sie über 5 Replikate und 2 Pools pro Replikat verfügen kann die Bereitstellung auf 10 Anforderungen parallel verarbeiten. Die Abbildung unten für eine grafische Darstellung der `replicas` und `poolsize`:

![Poolgröße und Replikate](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Nachdem die Replikatgruppe erstellt wurde, und die Pods gestartet haben, wird ein Cron-Auftrag erstellt, wenn eine `schedule` festgelegt wurde, der `spec.yaml` Datei. Schließlich eine Kubernetes Service wird erstellt, die zum Verwalten und Ausführen der Anwendung (siehe unten) verwendet werden können.

Wenn eine Anwendung ausgeführt wird, die Kubernetes-Dienst für die Anwendungsproxys die Anforderungen an ein Replikat und gibt die Ergebnisse zurück.

## <a name="how-to-work-with-application-deployment"></a>Arbeiten mit der Bereitstellung einer Anwendung

Die zwei wichtigsten Schnittstellen für die Anwendungsbereitstellung sind: 
- [Befehlszeilen-Schnittstelle `mssqlctl`](big-data-cluster-create-apps.md)
- [Visual Studio Code und Azure Data Studio-Erweiterung](app-deployment-extension.md)

Es ist auch möglich, eine Anwendung mit einer RESTful-Webdienst ausgeführt werden. Weitere Informationen finden Sie unter [Anwendungen für big Data-Cluster nutzen](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Erstellen und Ausführen von Anwendungen auf SQL Server-big Data-Clustern finden Sie unter den folgenden:

- [Deploy applications using mssqlctl (Bereitstellen von Anwendungen mit „mssqlctl“)](big-data-cluster-create-apps.md)
- [Bereitstellen von Anwendungen, die mit der Bereitstellung von App-Erweiterung](app-deployment-extension.md)
- [Nutzen Sie Anwendungen für big Data-Cluster](big-data-cluster-consume-apps.md)

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
