---
title: Was ist der SQL Server-big Data-Cluster-Controller? | Microsoft-Dokumentation
description: ''
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 6b3a8f01170fecf21fd85dbb2d85d228430fc100
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796033"
---
# <a name="what-is-the-sql-server-big-data-clusters-controller"></a>Was ist der SQL Server-big Data-Cluster-Controller?

Den Controller hostet die grundlegende Logik für die Bereitstellung und Verwaltung von big Data-Cluster. Es übernimmt alle Interaktionen mit Kubernetes, SQL Server-Instanzen, die Teil des Clusters und andere Komponenten wie HDFS und Spark. 

Der Controller-Dienst bietet die folgenden Kernfunktionen:

- Verwalten des clusterlebenszyklus: Cluster-Bootstrap & löschen, die Konfigurationen aktualisieren
- Verwalten der master-SQL Server-Instanzen
- Verwalten von Pools für Compute, Daten und Speicher
- Machen Sie Überwachungstools, um zu beobachten, die Zustand des Clusters
- Bereitstellen von Tools zur Problembehandlung, um zu erkennen und Reparieren unerwartete Probleme
- Verwalten von Clustersicherheit: sichere Cluster-Endpunkte stellen Sie sicher, Benutzern und Rollen verwalten, konfigurieren Sie Anmeldeinformationen für die Kommunikation innerhalb des Clusters
- Verwalten Sie den Workflow des Upgrades, damit sie problemlos implementiert werden (in CTP 2.0 nicht verfügbar)
- Verwalten von hochverfügbarkeit und Notfallwiederherstellung für zustandsbehaftete Dienste im Cluster (in CTP 2.0 nicht verfügbar)

## <a name="deploying-the-controller-service"></a>Bereitstellen des Controller-Diensts

Der Controller wird bereitgestellt und gehostet werden, in der gleichen Kubernetes-Namespace, in denen der Kunde möchte eine big Data-Cluster erstellen. Dieser Dienst wird von einem Kubernetes-Administrator während der Cluster-Bootstrap, mit dem Befehlszeilenprogramm Mssqlctl installiert:

```bash
mssqlctl create cluster <name of your cluster>
```

Der war-Workflow wird Layout auf Kubernetes eine voll funktionsfähige SQL Server-big Data-Cluster, der alle Komponenten, die in beschriebenen enthält die [Übersicht](big-data-cluster-overview.md) Artikel. Der bootstrap-Workflow erstellt zunächst den Controller-Dienst, und nachdem dieser bereitgestellt wurde, wird der Controller-Dienst koordiniert, die Installation und Konfiguration von Rest, der den Teil "Dienste" Master "," Compute "," Daten "und" Storage Pools.

## <a name="managing-the-cluster-through-the-controller-service"></a>Verwaltung des Clusters über den Controller-Dienst
Sie können den Cluster ausschließlich über den Controller-Dienst entweder verwalten `mssqlctl` -APIs oder das Verwaltungsportal für Cluster, die innerhalb des Clusters gehostet werden. Wenn Sie zusätzliche Kubernetes-Objekte, wie die Pods im gleichen Namespace bereitstellen, sind sie nicht verwaltet werden oder durch den Controller-Dienst überwacht.

Befinden sich in einem dedizierten Kubernetes-Namespace, der Controller und die Kubernetes-Objekte (zustandsbehaftete legt, Pods, Geheimnisse, usw.) für einen big Data-Cluster erstellt wurde. Der Controller-Dienst wird vom Administrator Kubernetes-Cluster zum Verwalten aller Ressourcen innerhalb dieses Namespace Berechtigung erteilt werden.  Die RBAC-Richtlinie für dieses Szenario wird automatisch als Teil der ersten Bereitstellung mithilfe konfiguriert `mssqlctl`. 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` ein Befehlszeilen-Hilfsprogramm ist in Python geschrieben werden, mit dem können Clusteradministratoren für das Bootstrapping und Verwalten von big Data-Clustern über die REST-APIs, die von den Controller-Dienst verfügbar gemacht werden.

### <a name="cluster-administration-portal"></a>Cluster-Verwaltungsportal

Nach der Controller-Dienst ausgeführt wird, kann Clusteradministrator das Cluster-Verwaltungsportal verwenden, um den Fortschritt der Bereitstellung überwachen, erkennen und beheben Sie Probleme mit Diensten innerhalb des Clusters. 

## <a name="monitoring-and-troubleshooting-the-controller-service"></a>Überwachung und Problembehandlung für den Controller-Dienst

Demnächst...

## <a name="controller-service-security"></a>Sicherheit des Domänencontrollers
Die gesamte Kommunikation mit dem Controllerdienst wird über eine REST-API über HTTPS durchgeführt. Ein selbstsigniertes Zertifikat wird automatisch für Sie bootstrap zum Zeitpunkt generiert werden. 

Der Controller-Dienstendpunkt-Authentifizierung basiert auf Benutzername und Kennwort. Diese Anmeldeinformationen werden bereitgestellt, bei der Verwendung der Eingabe für Umgebungsvariablen bootstrap Clusters `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD`.
```

> [!NOTE]
> You must provide a password that is in compliance with [SQL Server password complexity requirements](https://docs.microsoft.com/en-us/sql/relational-databases/security/password-policy?view=sql-server-2017).

## Next steps

To learn more about the SQL Server big data clusters, see the following overview:

- [What is SQL Server 2019 big data clusters?](big-data-cluster-overview.md)
