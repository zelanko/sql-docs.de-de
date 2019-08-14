---
title: Was ist der Controller?
titleSuffix: SQL Server big data clusters
description: Dieser Artikel enthält die Beschreibung des Controllers in einem Big Data-Cluster für SQL Server 2019 (Vorschau).
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e984c3dced4bde713ac98d67c22481e54491cd68
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419536"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>Was ist der Controller in einem SQL Server-Big Data Cluster?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

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

Der Controller wird im gleichen Kubernetes-Namespace bereitgestellt und gehostet, in dem der Kunde einen Big Data-Cluster erstellen möchte. Dieser Dienst wird von einem Kubernetes-Administrator während des Clusterbootstraps mit dem Befehlszeilen-Hilfsprogramm **azdata** installiert. Weitere Informationen finden Sie unter [Einstieg in SQL Server-Big Data-Cluster](deploy-get-started.md).

Der Erstellungsworkflow errichtet auf der Basis von Kubernetes einen voll funktionsfähigen SQL Server-Big Data-Cluster mit allen im Artikel [Übersicht](big-data-cluster-overview.md) beschriebenen Komponenten. Der Bootstrapworkflow erstellt zunächst den Controllerdienst und koordiniert nach dessen Bereitstellung die Installation und Konfiguration der übrigen Dienste, die Teil der Master-, Compute-, Daten- und Speicherpools sind.

## <a name="managing-the-cluster-through-the-controller-service"></a>Verwalten des Clusters über den Controllerdienst

Sie können den Cluster mithilfe der **azdata**-Befehle über den Controllerdienst verwalten. Wenn Sie zusätzliche Kubernetes-Objekte wie Pods im gleichen Namespace bereitstellen, werden sie nicht vom Controllerdienst verwaltet oder überwacht. Sie können auch **kubectl**-Befehle verwenden, um den Cluster auf Kubernetes-Ebene zu verwalten. Weitere Informationen finden Sie unter [Überwachen und Behandeln von Problemen eines Big Data-Clusters für SQL Server](cluster-troubleshooting-commands.md).

Der Controller und die Kubernetes-Objekte (zustandsbehaftete Sätze, Pods, Geheimnisse usw.), die für einen Big Data-Cluster erstellt wurden, befinden sich in einem dedizierten Kubernetes-Namespace. Dem Controllerdienst wird vom Administrator des Kubernetes-Clusters die Berechtigung zum Verwalten aller Ressourcen innerhalb dieses Namespace erteilt.  Die RBAC-Richtlinie für dieses Szenario wird automatisch als Teil der anfänglichen Clusterbereitstellung mithilfe von **azdata** konfiguriert.

### <a name="azdata"></a>azdata

**azdata** ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, das Clusteradministratoren ermöglicht, Big Data-Cluster über die vom Controllerdienst verfügbar gemachten REST-APIs zu starten und zu verwalten.

## <a name="controller-service-security"></a>Controllerdienstsicherheit

Die gesamte Kommunikation mit dem Controllerdienst wird mittels einer Rest-API über HTTPS durchgeführt. Ein selbstsigniertes Zertifikat wird automatisch zur Bootstrapzeit für Sie generiert. 

Die Authentifizierung beim Controllerdienstendpunkt basiert auf Benutzername und Kennwort. Diese Anmeldeinformationen werden zur Clusterbootstrapzeit mithilfe der Eingabe für die Umgebungsvariablen `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD` bereitgestellt.

> [!NOTE]
> Sie müssen ein Kennwort angeben, das der [Kennwortrichtlinie für die Komplexität von SQL Server-Kennwörtern](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017) entspricht.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie weitere Informationen zu den Big Data-Clustern für SQL Server:

- [Was sind Big Data-Cluster für SQL Server 2019?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server big data clusters Architecture](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters) (Workshop: Architektur von Big Data-Clustern für SQL Server)
