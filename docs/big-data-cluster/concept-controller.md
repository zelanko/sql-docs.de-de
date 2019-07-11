---
title: Was ist der Controller?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel beschreibt den Controller von einem SQL Server-2019 big Data-Cluster (Vorschau).
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 076cc40c09d4b086ae7a416ac1cc5ccbcc16a20a
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729175"
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

Der Controller wird bereitgestellt und gehostet werden, in der gleichen Kubernetes-Namespace, in denen der Kunde möchte eine big Data-Cluster erstellen. Dieser Dienst wird von einem Kubernetes-Administrator installiert, während der Cluster-bootstrap, mit der **Mssqlctl** Befehlszeilen-Hilfsprogramm. Weitere Informationen finden Sie unter [erste Schritte mit SQL Server-big Data-Cluster](deploy-get-started.md).

Der war-Workflow wird Layout auf Kubernetes eine voll funktionsfähige SQL Server-big Data-Cluster, der alle Komponenten, die in beschriebenen enthält die [Übersicht](big-data-cluster-overview.md) Artikel. Der bootstrap-Workflow erstellt zunächst den Controller-Dienst, und nachdem dieser bereitgestellt wurde, wird der Controller-Dienst koordiniert, die Installation und Konfiguration von Rest, der den Teil "Dienste" Master "," Compute "," Daten "und" Storage Pools.

## <a name="managing-the-cluster-through-the-controller-service"></a>Verwaltung des Clusters über den Controller-Dienst

Sie können den Cluster über den Controller-Dienst entweder verwalten **Mssqlctl** Befehle. Wenn Sie zusätzliche Kubernetes-Objekte, wie die Pods im gleichen Namespace bereitstellen, sind sie nicht verwaltet werden oder durch den Controller-Dienst überwacht. Sie können auch **"kubectl"** Befehle zum Verwalten des Clusters auf die Kubernetes-Ebene. Weitere Informationen finden Sie unter [Überwachung und Problembehandlung für SQL Server-big Data-Cluster](cluster-troubleshooting-commands.md).

Befinden sich in einem dedizierten Kubernetes-Namespace, der Controller und die Kubernetes-Objekte (zustandsbehaftete legt, Pods, Geheimnisse, usw.) für einen big Data-Cluster erstellt wurde. Der Controller-Dienst wird vom Administrator Kubernetes-Cluster zum Verwalten aller Ressourcen innerhalb dieses Namespace Berechtigung erteilt werden.  Die RBAC-Richtlinie für dieses Szenario wird automatisch als Teil der ersten Bereitstellung mithilfe konfiguriert **Mssqlctl**.

### <a name="mssqlctl"></a>mssqlctl

**Mssqlctl** ist ein Befehlszeilenprogramm, das in Python geschrieben wurde, ermöglicht das Clustern von Administratoren zum Starten und Verwalten von big Data-Clustern über die REST-APIs, die von den Controller-Dienst verfügbar gemacht werden.

## <a name="controller-service-security"></a>Sicherheit des Domänencontrollers

Die gesamte Kommunikation mit dem Controllerdienst wird über eine REST-API über HTTPS durchgeführt. Ein selbstsigniertes Zertifikat wird automatisch für Sie bootstrap zum Zeitpunkt generiert werden. 

Der Controller-Dienstendpunkt-Authentifizierung basiert auf Benutzername und Kennwort. Diese Anmeldeinformationen werden bereitgestellt, bei der Verwendung der Eingabe für Umgebungsvariablen bootstrap Clusters `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD`.

> [!NOTE]
> Sie müssen angeben, ein Kennwort, ist unter Einhaltung [Anforderungen an SQL Server die Kennwortkomplexität](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter den folgenden Ressourcen:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server-big Data-Cluster Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
