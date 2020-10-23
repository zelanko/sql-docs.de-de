---
title: Was ist eine Anwendungsbereitstellung?
titleSuffix: SQL Server Big Data Clusters
description: Erfahren Sie, wie eine Anwendungsbereitstellung Schnittstellen zum Erstellen, Verwalten und Ausführen von Anwendungen in einem Big Data-Cluster in SQL Server 2019 bereitstellt.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 65a7c0afc57cc29d8ec5df7beb4c3107470e2d31
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257260"
---
# <a name="what-is-application-deployment-on-a-big-data-cluster"></a>Was hat es mit der Anwendungsbereitstellung in Big Data-Cluster auf sich?

Es handelt sich hierbei um die Bereitstellung von Anwendungen in Big Data-Cluster durch die Bereitstellung von Schnittstellen zum Erstellen, Verwalten und Ausführen von Anwendungen. Anwendungen, die auf dem Big Data-Cluster bereitgestellt werden, profitieren von der Rechenleistung des Clusters und können auf die Daten zugreifen, die auf dem Cluster verfügbar sind. Dadurch wird die Skalierbarkeit und Leistung der Anwendungen erhöht, während die Anwendungen, in denen sich die Daten befinden, verwaltet werden. Die unterstützten Anwendungsruntimes für Big Data-Cluster in SQL Server sind R, Python, SSIS und MLeap.

In den folgenden Abschnitten werden die Architektur und die Funktionalität der Anwendungsbereitstellung beschrieben.

## <a name="application-deployment-architecture"></a>Architektur der Anwendungsbereitstellung

Die Anwendungsbereitstellung besteht aus einem Controller und App-Runtime-Handlern. Beim Erstellen einer Anwendung wird eine Spezifikationsdatei (`spec.yaml`) bereitgestellt. Diese `spec.yaml`-Datei enthält alles, was der Controller wissen muss, um die Anwendung erfolgreich bereitzustellen. Im Folgenden finden Sie ein Beispiel für den Inhalt für `spec.yaml`:

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

Der Controller überprüft die `runtime`, die in der `spec.yaml`-Datei angegeben ist, und ruft den entsprechenden Runtimehandler auf. Der Runtimehandler erstellt die Anwendung. Zuerst wird ein Kubernetes-ReplicaSet erstellt, das einen oder mehrere Pods enthält, von denen jeder die bereitzustellende Anwendung enthält. Die Anzahl von Pods wird durch den `replicas`-Parametersatz definiert, der in der `spec.yaml`-Datei für die Anwendung festgelegt ist. Jeder Pod kann über einen von mehreren Pools verfügen. Die Anzahl von Pools wird durch den `poolsize`-Parametersatz definiert, der in der `spec.yaml`-Datei festgelegt ist.

Diese Einstellungen wirken sich auf die Anzahl der Anforderungen aus, die die Bereitstellung parallel verarbeiten kann. Die maximale Anzahl von Anforderungen zu einem bestimmten Zeitpunkt entspricht dem Produkt aus `replicas` und `poolsize`. Wenn Sie über 5 Replikate und 2 Pools pro Replikat verfügen, kann die Bereitstellung 10 Anforderungen parallel verarbeiten. Das folgende Bild zeigt eine grafische Darstellung von `replicas` und `poolsize`:

![Poolgröße und Replikate](media/big-data-cluster-create-apps/poolsize-vs-replicas.png)

Nachdem das ReplicaSet erstellt und die Pods gestartet wurden, wird ein Cron-Auftrag erstellt, wenn ein `schedule` in der `spec.yaml`-Datei festgelegt wurde. Zum Schluss wird ein Kubernetes-Dienst erstellt, der zum Verwalten und Ausführen der Anwendung verwendet werden kann (siehe unten).

Wenn eine Anwendung ausgeführt wird, leitet der Kubernetes-Dienst für die Anwendung die Anforderungen an ein Replikat weiter und gibt die Ergebnisse zurück.

## <a name="security-considerations-for-applications-deployments-on-openshift"></a><a id="app-deploy-security"></a> Hinweise für Anwendungsbereitstellungen in OpenShift

SQL Server 2019 CU5 umfasst die Unterstützung für die Bereitstellung von Big Data-Cluster in Red Hat OpenShift sowie ein aktualisiertes Sicherheitsmodell für Big Data-Cluster, für das keine privilegierten Container mehr erforderlich sind. Zusätzlich zu nicht privilegierten Containern werden Container standardmäßig für alle neuen Bereitstellungen unter Verwendung von SQL Server 2019 CU5 nicht als Root-Benutzer ausgeführt.

Zum Zeitpunkt der Veröffentlichung von CU5 wird der Setupschritt der Anwendungen, die mit [App Deploy]()-Schnittstellen bereitgestellt wurden, weiterhin als *Root*-Benutzer ausgeführt. Dies ist erforderlich, da während des Setups zusätzliche, von der Anwendung verwendete Pakete installiert werden. Anderer Benutzercode, der als Teil der Anwendung bereitgestellt wird, wird als Benutzer mit niedrigen Berechtigungen ausgeführt. 

Außerdem steht die optionale Funktion **CAP_AUDIT_WRITE** zur Verfügung, die benötigt wird, um mithilfe von Cron-Aufträgen Zeitpläne für SSIS-Anwendungen zu erstellen. Wenn die YAML-Spezifikationsdatei der Anwendung einen Zeitplan vorgibt, wird die Anwendung über einen Cron-Auftrag ausgelöst. Dafür wird diese zusätzliche Funktion benötigt.  Alternativ kann die Anwendung nach Bedarf mit dem Befehl *azdata app run* über einen Webdienstaufruf ausgelöst werden. Hierfür wird die Funktion „CAP_AUDIT_WRITE“ nicht benötigt. 

> [!NOTE]
> Die benutzerdefinierte Sicherheitskontexteinschränkung (Security Context Constraint, SCC) im [Artikel zur OpenShift-Bereitstellung](deploy-openshift.md) umfasst diese Funktion nicht, da sie nicht für die Standardbereitstellung von Big Data-Cluster erforderlich ist. Sie können diese Funktion aktivieren, indem Sie zuerst die benutzerdefinierte SCC-YAML-Datei so aktualisieren, dass sie den Befehl „CAP_AUDIT_WRITE“ enthält. 

```yml
...
allowedCapabilities:
- SETUID
- SETGID
- CHOWN
- SYS_PTRACE
- AUDIT_WRITE
...
```

## <a name="how-to-work-with-application-deployment"></a>Vorgehensweise: Arbeiten mit der Anwendungsbereitstellung

Die zwei Hauptschnittstellen für die Anwendungsbereitstellung lauten wie folgt: 
- [Befehlszeilenschnittstelle[!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)]](app-create.md)
- [Visual Studio Code und Erweiterung Azure Data Studio](app-deployment-extension.md)

Es ist auch möglich, dass eine Anwendung mit einem RESTful-Webdienst ausgeführt wird. Weitere Informationen finden Sie unter [Nutzen von Anwendungen auf Big Data-Clustern](app-consume.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Erstellen und Ausführen von Anwendungen auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie unter:

- [Bereitstellen von Anwendungen mit „azdata“](app-create.md)
- [Vorgehensweise: Verwenden von Visual Studio Code zum Bereitstellen von Anwendungen für SQL Server-Big Data-Cluster](app-deployment-extension.md)
- [Verwenden von Anwendungen auf Big Data-Clustern](app-consume.md)

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in der folgenden Übersicht:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)