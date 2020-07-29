---
title: Was ist der Controller?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung des Controllers in einem Big Data-Cluster für SQL Server.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5a294bf705e4caf4a79c0f67ce925187e24c0f00
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730700"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>Was ist der Controller in einem SQL Server-Big Data Cluster?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Der Controller hostet die Kernlogik für die Bereitstellung und Verwaltung eines Big Data-Clusters. Er übernimmt alle Interaktionen mit Kubernetes, SQL Server-Instanzen, die Teil des Clusters sind, und anderen Komponenten wie HDFS und Spark.

Der Controllerdienst stellt die folgenden grundlegenden Funktionen bereit:

- Verwalten des Lebenszyklus des Clusters: Bootstrap und Löschen des Clusters, Aktualisieren von Konfigurationen
- Verwalten von SQL Server-Masterinstanzen
- Verwalten von Compute-, Daten- und Speicherpools
- Verfügbarmachen von Überwachungstools, um den Status des Clusters zu beobachten
- Verfügbarmachen von Problembehandlungstools zum Erkennen und Beheben unerwarteter Probleme
- Verwalten der Clustersicherheit:
  - Sicherstellen sicherer Clusterendpunkte
  - Verwalten von Benutzern und Rollen
  - Konfigurieren von Anmeldeinformationen für die interne Kommunikation des Clusters

## <a name="deploying-the-controller-service"></a>Bereitstellen des Controllerdiensts

Der Controller wird im gleichen Kubernetes-Namespace bereitgestellt und gehostet, in dem der Kunde einen Big Data-Cluster erstellen möchte. Dieser Dienst wird von einem Kubernetes-Administrator während des Clusterbootstraps mit dem Befehlszeilen-Hilfsprogramm **azdata** installiert. Weitere Informationen finden Sie unter [Erste Schritte mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deploy-get-started.md).

Der Erstellungsworkflow errichtet auf der Basis von Kubernetes einen voll funktionsfähigen SQL Server-Big Data-Cluster mit allen im Artikel [Übersicht](big-data-cluster-overview.md) beschriebenen Komponenten. Der Bootstrapworkflow erstellt zunächst den Controllerdienst und koordiniert nach dessen Bereitstellung die Installation und Konfiguration der übrigen Dienste, die Teil der Master-, Compute-, Daten- und Speicherpools sind.

## <a name="managing-the-cluster-through-the-controller-service"></a>Verwalten des Clusters über den Controllerdienst

Sie können den Cluster mithilfe der **azdata**-Befehle über den Controllerdienst verwalten. Wenn Sie zusätzliche Kubernetes-Objekte wie Pods im gleichen Namespace bereitstellen, werden sie nicht vom Controllerdienst verwaltet oder überwacht. Sie können auch **kubectl**-Befehle verwenden, um den Cluster auf Kubernetes-Ebene zu verwalten. Weitere Informationen finden Sie unter [Überwachen und Behandeln von Problemen eines [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](cluster-troubleshooting-commands.md).

Der Controller und die Kubernetes-Objekte (zustandsbehaftete Sätze, Pods, Geheimnisse usw.), die für einen Big Data-Cluster erstellt wurden, befinden sich in einem dedizierten Kubernetes-Namespace. Dem Controllerdienst wird vom Administrator des Kubernetes-Clusters die Berechtigung zum Verwalten aller Ressourcen innerhalb dieses Namespace erteilt.  Die RBAC-Richtlinie für dieses Szenario wird automatisch als Teil der anfänglichen Clusterbereitstellung mithilfe von **azdata** konfiguriert.

### <a name="azdata"></a>azdata

**azdata** ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, das Clusteradministratoren ermöglicht, Big Data-Cluster über die vom Controllerdienst verfügbar gemachten REST-APIs zu starten und zu verwalten.

## <a name="controller-service-security"></a>Controllerdienstsicherheit

Die gesamte Kommunikation mit dem Controllerdienst wird mittels einer Rest-API über HTTPS durchgeführt. Ein selbstsigniertes Zertifikat wird automatisch zur Bootstrapzeit für Sie generiert. 

Für die Authentifizierung beim Controllerdienstendpunkt wird entweder eine Active Directory-Identität verwendet, oder sie basiert auf Benutzername und Kennwort. Diese Anmeldeinformationen werden zur Clusterbootstrapzeit mithilfe der Eingabe für die Umgebungsvariablen `AZDATA_USERNAME` und `AZDATA_PASSWORD` bereitgestellt.

> [!NOTE]
> Sie müssen ein Kennwort angeben, das der [Kennwortrichtlinie für die Komplexität von SQL Server-Kennwörtern](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017) entspricht.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Architektur](https://github.com/microsoft/sqlworkshops-bdc)
