---
title: Was ist der Controller?
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird der Controller eines SQL Server 2019 Big Data Cluster (Vorschau) beschrieben.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e984c3dced4bde713ac98d67c22481e54491cd68
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419536"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>Was ist der Controller in einem SQL Server Big Data Cluster?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der Controller hostet die Kernlogik für die Bereitstellung und Verwaltung eines Big Data Clusters. Es übernimmt alle Interaktionen mit Kubernetes, SQL Server Instanzen, die Teil des Clusters sind, und andere Komponenten wie HDFS und Spark.

Der Controller Dienst stellt die folgenden grundlegenden Funktionen bereit:

- Verwalten des Cluster Lebenszyklus: Cluster-Bootstrap & löschen, Update Konfigurationen
- Verwalten von Master SQL Server Instanzen
- Verwalten von COMPUTE-, Daten-und Speicherpools
- Machen Sie Überwachungstools verfügbar, um den Status des Clusters zu beobachten.
- Verfügbar machen von Problem Behandlungs Tools zum erkennen und reparieren unerwarteter Probleme
- Verwalten der Cluster Sicherheit:
  - Sicherstellen sicherer Cluster Endpunkte
  - Verwalten von Benutzern und Rollen
  - Konfigurieren von Anmelde Informationen für die Cluster interne Kommunikation

## <a name="deploying-the-controller-service"></a>Bereitstellen des Controller Dienstanbieter

Der Controller wird im gleichen Kubernetes-Namespace bereitgestellt und gehostet, in dem der Kunde einen Big Data Cluster erstellen möchte. Dieser Dienst wird von einem Kubernetes-Administrator während des Cluster-Bootstrap mit dem Befehlszeilenprogramm **azdata** installiert. Weitere Informationen finden Sie unter [Get Started with SQL Server Big Data Clusters](deploy-get-started.md).

Der Ausbau-Workflow wird auf Kubernetes ein voll funktionsfähiges SQL Server Big Data Cluster mit allen im [Übersichts](big-data-cluster-overview.md) Artikel beschriebenen Komponenten enthalten. Der Bootstrap-Workflow erstellt zunächst den Controller Dienst, und nach der Bereitstellung koordiniert der Controller Dienst die Installation und Konfiguration der restlichen Dienste von Master-, COMPUTE-, Daten-und Speicherpools.

## <a name="managing-the-cluster-through-the-controller-service"></a>Verwalten des Clusters über den Controller Dienst

Sie können den Cluster über den Controller Dienst mithilfe der **azdata** -Befehle verwalten. Wenn Sie zusätzliche Kubernetes-Objekte wie Pods im gleichen Namespace bereitstellen, werden Sie nicht vom Controller Dienst verwaltet oder überwacht. Sie können auch **kubectl** -Befehle verwenden, um den Cluster auf Kubernetes Ebene zu verwalten. Weitere Informationen finden Sie unter [Überwachung und Problembehandlung für SQL Server Big Data-Cluster](cluster-troubleshooting-commands.md).

Der Controller und die Kubernetes-Objekte (Zustands behaftete Sätze, Pods, Geheimnisse usw.), die für einen Big Data Cluster erstellt wurden, befinden sich in einem dedizierten Kubernetes-Namespace. Dem Controller Dienst wird vom Kubernetes-Cluster Administrator die Berechtigung zum Verwalten aller Ressourcen innerhalb dieses Namespace erteilt.  Die RBAC-Richtlinie für dieses Szenario wird automatisch als Teil der anfänglichen Cluster Bereitstellung mithilfe von **azdata**konfiguriert.

### <a name="azdata"></a>azdata

**azdata** ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm, mit dem Cluster Administratoren Big Data Cluster über die vom Controller Dienst verfügbar gemachten Rest-APIs Bootstrap und verwalten können.

## <a name="controller-service-security"></a>Sicherheit des Controller Diensts

Die gesamte Kommunikation mit dem Controller Dienst wird über eine Rest-API über HTTPS durchgeführt. Ein selbst signiertes Zertifikat wird automatisch zur Boots Trap Zeit für Sie generiert. 

Die Authentifizierung beim Controller Dienst Endpunkt basiert auf Benutzername und Kennwort. Diese Anmelde Informationen werden bei der Cluster-Bootstrap-Zeit mithilfe der Eingabe für die `CONTROLLER_USERNAME` Umgebungs `CONTROLLER_PASSWORD`Variablen und bereitgestellt.

> [!NOTE]
> Sie müssen ein Kennwort angeben, das den Anforderungen an die [Komplexität der SQL Server Kenn Wörter](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017)entspricht.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum SQL Server Big Data Clustern finden Sie in den folgenden Ressourcen:

- [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md)
- [Werkstatt Architektur von Microsoft SQL Server Big Data Clustern](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
