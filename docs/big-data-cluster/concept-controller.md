---
title: Was ist der Controller?
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt den Controller von einem SQL Server-2019 big Data-Cluster (Vorschau).
author: mihaelablendea
ms.author: mihaelab
manager: craigg
ms.date: 12/07/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: 954f3fa220d2bd379dc5d6666015b2be759aafc7
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "53206719"
---
# <a name="what-is-the-controller-on-a-sql-server-2019-big-data-cluster"></a>Was ist der Controller auf einem SQL Server-2019 big Data-Cluster?

Den Controller hostet die grundlegende Logik für die Bereitstellung und Verwaltung von big Data-Cluster. Es übernimmt alle Interaktionen mit Kubernetes, SQL Server-Instanzen, die Teil des Clusters und andere Komponenten wie HDFS und Spark. 

Der Controller-Dienst bietet die folgenden Kernfunktionen:

- Verwalten des clusterlebenszyklus: Cluster-Bootstrap & löschen, die Konfigurationen aktualisieren
- Verwalten der master-SQL Server-Instanzen
- Verwalten von Pools für Datenverarbeitung, Daten und Speicher
- Machen Sie Überwachungstools, um zu beobachten, die Zustand des Clusters
- Bereitstellen von Tools zur Problembehandlung, um zu erkennen und Reparieren unerwartete Probleme
- Verwalten von Clustersicherheit: sichere Cluster-Endpunkte stellen Sie sicher, Benutzern und Rollen verwalten, konfigurieren Sie Anmeldeinformationen für die Kommunikation innerhalb des Clusters
- Verwalten Sie den Workflow des Upgrades, damit sie problemlos implementiert werden (nicht verfügbar in der CTP-Version 2.2)
- Verwalten von hochverfügbarkeit und Notfallwiederherstellung für zustandsbehaftete Dienste im Cluster (nicht verfügbar in der CTP-Version 2.2)

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

Nach der Controllerdienst ausgeführt wird, kann die Clusterverwaltung verwenden die [Cluster-Verwaltungsportal](cluster-admin-portal.md) um den Fortschritt der Bereitstellung zu überwachen, erkennen und beheben Sie Probleme mit Diensten innerhalb des Clusters.

## <a name="controller-service-security"></a>Sicherheit des Domänencontrollers

Die gesamte Kommunikation mit dem Controllerdienst wird über eine REST-API über HTTPS durchgeführt. Ein selbstsigniertes Zertifikat wird automatisch für Sie bootstrap zum Zeitpunkt generiert werden. 

Der Controller-Dienstendpunkt-Authentifizierung basiert auf Benutzername und Kennwort. Diese Anmeldeinformationen werden bereitgestellt, bei der Verwendung der Eingabe für Umgebungsvariablen bootstrap Clusters `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD`.

> [!NOTE]
> Sie müssen angeben, ein Kennwort, ist unter Einhaltung [Anforderungen an SQL Server die Kennwortkomplexität](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
