---
title: Was ist der Controller?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel beschreibt den Controller von einem SQL Server-2019 big Data-Cluster (Vorschau).
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 3084d9ecc80dcd8f283a52ca5559783626a7ca4e
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63472168"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>Was ist der Controller auf einem SQL Server-big Data-Cluster?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Den Controller hostet die grundlegende Logik für die Bereitstellung und Verwaltung von big Data-Cluster. Es übernimmt alle Interaktionen mit Kubernetes, SQL Server-Instanzen, die Teil des Clusters und andere Komponenten wie HDFS und Spark.

Der Controller-Dienst bietet die folgenden Kernfunktionen:

- Verwalten des clusterlebenszyklus: Cluster-Bootstrap & löschen, die Konfigurationen aktualisieren
- Verwalten der master-SQL Server-Instanzen
- Verwalten von Pools für Datenverarbeitung, Daten und Speicher
- Machen Sie Überwachungstools, um zu beobachten, die Zustand des Clusters
- Bereitstellen von Tools zur Problembehandlung, um zu erkennen und Reparieren unerwartete Probleme
- Verwalten von Clustersicherheit:
  - Stellen Sie sicher sichere Cluster-Endpunkte
  - Verwalten von Benutzern und Rollen
  - Konfigurieren von Anmeldeinformationen für die Kommunikation innerhalb des Clusters

## <a name="deploying-the-controller-service"></a>Bereitstellen des Controller-Diensts

Der Controller wird bereitgestellt und gehostet werden, in der gleichen Kubernetes-Namespace, in denen der Kunde möchte eine big Data-Cluster erstellen. Dieser Dienst wird von einem Kubernetes-Administrator während der Cluster-Bootstrap, mit dem Befehlszeilenprogramm Mssqlctl installiert:

```bash
mssqlctl cluster create --name <name of your cluster>
```

Der war-Workflow wird Layout auf Kubernetes eine voll funktionsfähige SQL Server-big Data-Cluster, der alle Komponenten, die in beschriebenen enthält die [Übersicht](big-data-cluster-overview.md) Artikel. Der bootstrap-Workflow erstellt zunächst den Controller-Dienst, und nachdem dieser bereitgestellt wurde, wird der Controller-Dienst koordiniert, die Installation und Konfiguration von Rest, der den Teil "Dienste" Master "," Compute "," Daten "und" Storage Pools.

## <a name="managing-the-cluster-through-the-controller-service"></a>Verwaltung des Clusters über den Controller-Dienst

Sie können den Cluster ausschließlich über den Controller-Dienst entweder verwalten `mssqlctl` -APIs oder das Verwaltungsportal für Cluster, die innerhalb des Clusters gehostet werden. Wenn Sie zusätzliche Kubernetes-Objekte, wie die Pods im gleichen Namespace bereitstellen, sind sie nicht verwaltet werden oder durch den Controller-Dienst überwacht.

Befinden sich in einem dedizierten Kubernetes-Namespace, der Controller und die Kubernetes-Objekte (zustandsbehaftete legt, Pods, Geheimnisse, usw.) für einen big Data-Cluster erstellt wurde. Der Controller-Dienst wird vom Administrator Kubernetes-Cluster zum Verwalten aller Ressourcen innerhalb dieses Namespace Berechtigung erteilt werden.  Die RBAC-Richtlinie für dieses Szenario wird automatisch als Teil der ersten Bereitstellung mithilfe konfiguriert `mssqlctl`. 

### <a name="mssqlctl"></a>mssqlctl

`mssqlctl` ein Befehlszeilen-Hilfsprogramm ist in Python geschrieben werden, mit dem können Clusteradministratoren für das Bootstrapping und Verwalten von big Data-Clustern über die REST-APIs, die von den Controller-Dienst verfügbar gemacht werden.

### <a name="cluster-administration-portal"></a>Cluster-Verwaltungsportal

Nach der Controllerdienst ausgeführt wird, kann die Clusterverwaltung verwenden die [Cluster-Verwaltungsportal](cluster-admin-portal.md) um den Fortschritt der Bereitstellung zu überwachen, erkennen und beheben Sie Probleme mit Diensten innerhalb des Clusters.

## <a name="controller-service-security"></a>Sicherheit des Domänencontrollers

Die gesamte Kommunikation mit dem Controllerdienst wird über eine REST-API über HTTPS durchgeführt. Ein selbstsigniertes Zertifikat wird automatisch für Sie bootstrap zum Zeitpunkt generiert werden. 

Der Controller-Dienstendpunkt-Authentifizierung basiert auf Benutzername und Kennwort. Diese Anmeldeinformationen werden bereitgestellt, bei der Verwendung der Eingabe für Umgebungsvariablen bootstrap Clusters `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD`.

> [!NOTE]
> Sie müssen angeben, ein Kennwort, ist unter Einhaltung [Anforderungen an SQL Server die Kennwortkomplexität](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter den folgenden Ressourcen:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server-big Data-Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
