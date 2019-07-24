---
title: Was ist die Anwendungs Bereitstellung?
titleSuffix: SQL Server 2019 big data clusters
description: In diesem Artikel wird die Anwendungs Bereitstellung auf einem SQL Server 2019 Big Data-Cluster (Vorschauversion) beschrieben.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d8cc44862af21c54bdbd0e4adbb35db912c3f7c9
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419407"
---
# <a name="what-is-application-deployment-on-a-sql-server-2019-big-data-cluster"></a>Was ist die Anwendungs Bereitstellung auf einem SQL Server 2019 Big Data Cluster?

Die Anwendungs Bereitstellung ermöglicht die Bereitstellung von Anwendungen im Big Data Cluster durch die Bereitstellung von Schnittstellen zum Erstellen, verwalten und Ausführen von Anwendungen. Anwendungen, die auf dem Big Data Cluster bereitgestellt werden, profitieren von der Rechenleistung des Clusters und können auf die Daten zugreifen, die auf dem Cluster verfügbar sind. Dadurch wird die Skalierbarkeit und Leistung der Anwendungen erhöht, während die Anwendungen, in denen sich die Daten befinden, verwaltet werden.
In den folgenden Abschnitten werden die Architektur und die Funktionen der Anwendungs Bereitstellung beschrieben.

## <a name="application-deployment-architecture"></a>Architektur der Anwendungs Bereitstellung

Die Anwendungs Bereitstellung besteht aus einem Controller und App-Lauf Zeit Handlern. Beim Erstellen einer Anwendung wird eine Spezifikations Datei`spec.yaml`() bereitgestellt. Diese `spec.yaml` Datei enthält alles, was der Controller wissen muss, um die Anwendung erfolgreich bereitzustellen. Im folgenden finden Sie ein Beispiel für `spec.yaml`den Inhalt von:

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

Der Controller überprüft den `runtime` angegebenen in der `spec.yaml` Datei und ruft den entsprechenden Lauf Zeit Handler auf. Der Lauf Zeit Handler erstellt die Anwendung. Zuerst wird ein Kubernetes REPLICASET erstellt, das einen oder mehrere Pods enthält, von denen jede die bereit zustellende Anwendung enthält. Die Anzahl von Pods wird durch den `replicas` Parameter definiert, der in der `spec.yaml` Datei für die Anwendung festgelegt ist. Jeder Pod kann über einen der weiteren Pools verfügen. Die Anzahl der Pools wird durch den `poolsize` Parameter festgelegt, der in der `spec.yaml` Datei festgelegt ist.

Diese Einstellungen wirken sich auf die Anzahl der Anforderungen aus, die die Bereitstellung parallel verarbeiten kann. Die maximale Anzahl von Anforderungen zu einem bestimmten Zeitpunkt ist gleich `replicas` den Uhrzeiten. `poolsize` Wenn Sie über 5 Replikate und 2 Pools pro Replikat verfügen, kann die Bereitstellung 10 Anforderungen parallel verarbeiten. In der folgenden Abbildung finden Sie eine grafische Darstellung `replicas` von `poolsize`und:

![PoolSize und Replikate](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Nachdem das REPLICASET erstellt und die Pods gestartet wurden, wird ein Cron-Auftrag erstellt, wenn eine `schedule` in der `spec.yaml` Datei festgelegt wurde. Zum Schluss wird ein Kubernetes-Dienst erstellt, der zum Verwalten und Ausführen der Anwendung verwendet werden kann (siehe unten).

Wenn eine Anwendung ausgeführt wird, werden die Anforderungen vom Kubernetes-Dienst für die Anwendung an ein Replikat über gestellt, und die Ergebnisse werden zurückgegeben.

## <a name="how-to-work-with-application-deployment"></a>Arbeiten mit der Anwendungs Bereitstellung

Die zwei Haupt Schnittstellen für die Anwendungs Bereitstellung lauten wie folgt: 
- [Befehlszeilenschnittstelle`azdata`](big-data-cluster-create-apps.md)
- [Erweiterung für Visual Studio Code und Azure Data Studio](app-deployment-extension.md)

Es ist auch möglich, dass eine Anwendung mit einem Rest-Webdienst ausgeführt wird. Weitere Informationen finden Sie unter verwenden [von Anwendungen auf Big Data Clustern](big-data-cluster-consume-apps.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Erstellen und Ausführen von Anwendungen auf SQL Server Big Data Clustern finden Sie in den folgenden Bereichen:

- [Bereitstellen von Anwendungen mit azdata](big-data-cluster-create-apps.md)
- [Bereitstellen von Anwendungen mit der APP-Bereitstellungs Erweiterung](app-deployment-extension.md)
- [Verwenden von Anwendungen auf Big Data Clustern](big-data-cluster-consume-apps.md)

Weitere Informationen zum SQL Server Big Data Clustern finden Sie in der folgenden Übersicht:

- [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md)
