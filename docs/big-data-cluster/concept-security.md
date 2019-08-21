---
title: Sicherheitskonzepte
titleSuffix: SQL Server big data clusters
description: In diesem Artikel werden die Sicherheits [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]Konzepte für beschrieben. Der Artikel umfasst auch eine Beschreibung von Clusterendpunkten und Clusterauthentifizierung.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4e4441f0cc4f19d4784019408bfc5309a5734285
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69652254"
---
# <a name="security-concepts-for-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Sicherheitskonzepte für[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Ein sicherer Big Data-Cluster impliziert konsistente und kohärente Unterstützung für Authentifizierung- und Autorisierungsszenarien sowohl für SQL Server als auch für HDFS/Spark. Authentifizierung ist der Prozess, mit dem die Identität eines Benutzers oder Diensts überprüft und sichergestellt wird, dass der Benutzer oder Dienst das ist, was er zu sein vorgibt. Autorisierung bezieht sich auf das Gewähren oder Verweigern des Zugriffs auf bestimmte Ressourcen basierend auf der Identität des Benutzers, der den Zugriff anfordert. Dieser Schritt wird ausgeführt, nachdem ein Benutzer per Authentifizierung identifiziert wurde.

Im Big Data-Kontext erfolgt die Autorisierung in der Regel über Zugriffssteuerungslisten (Access Control Lists, ACLs), die Benutzeridentitäten bestimmte Berechtigungen zuordnen. HDFS unterstützt die Autorisierung durch Einschränken des Zugriffs auf Dienst-APIs, HDFS-Dateien und Auftragsausführung.

In diesem Artikel werden die wichtigsten sicherheitsbezogenen Konzepte in Big Data-Clustern erläutert.

## <a name="cluster-endpoints"></a>Clusterendpunkte

Es gibt drei Einstiegspunkte für den Big Data-Cluster:

* HDFS/Spark-Gateway (Knox): Dies ist ein HTTPS-basierter Endpunkt. Andere Endpunkte werden per Proxy über diesen Endpunkt geleitet. Ein HDFS/Spark-Gateway wird für den Zugriff auf Dienste wie webHDFS und Livy verwendet. Wenn Sie Verweise auf Knox sehen – dies ist der Endpunkt.

* Controllerendpunkt: Verwaltungsdienst für Big Data-Cluster, der REST-APIs für die Verwaltung des Clusters verfügbar macht. Über diesen Endpunkt wird auch auf einige Tools zugegriffen.

* Masterinstanz: TDS-Endpunkt für Datenbanktools und Anwendungen zum Herstellen einer Verbindung mit der SQL Server-Masterinstanz im Cluster.

![Clusterendpunkte](media/concept-security/cluster_endpoints.png)

Derzeit gibt es keine Option, zusätzliche Ports zu öffnen, um von außen auf den Cluster zuzugreifen.

### <a name="how-endpoints-are-secured"></a>Sichern von Endpunkten

Endpunkte im Big Data-Cluster werden über Kennwörter gesichert, die mithilfe von Umgebungsvariablen oder CLI-Befehlen festgelegt oder aktualisiert werden können. Alle internen Clusterkennwörter werden als Kubernetes-Geheimnisse gespeichert.  

## <a name="authentication"></a>Authentifizierung

Beim Bereitstellen des Clusters wird eine Reihe von Anmeldungen erstellt.

Einige dieser Anmeldungen dienen dazu, dass Dienste miteinander kommunizieren können, andere werden von Endbenutzern für den Zugriff auf den Cluster verwendet.

### <a name="end-user-authentication"></a>Authentifizierung von Endbenutzern
Beim Bereitstellen des Clusters muss mithilfe von Umgebungsvariablen eine Reihe von Kennwörtern für Endbenutzer festgelegt werden. Dies sind Kennwörter, die SQL-Administratoren und Clusteradministratoren für den Zugriff auf Dienste verwenden:

Benutzername des Controllers:
 + CONTROLLER_USERNAME=<Benutzername_des_Controllers>

Kennwort des Controllers:  
 + CONTROLLER_PASSWORD=<Kennwort_des_Controllers>

Systemadministratorkennwort für SQL Master: 
 + MSSQL_SA_PASSWORD=<SA_Kennwort_des_Controllers>

Kennwort für den Zugriff auf den HDFS/Spark-Endpunkt:
 + KNOX_PASSWORD=<KNOX_Kennwort>

### <a name="intra-cluster-authentication"></a>Clusterinterne Authentifizierung

Beim Bereitstellen des Clusters wird eine Reihe von SQL-Anmeldungen erstellt:

* In der vom System verwalteten SQL-Controllerinstanz wird eine spezielle SQL-Anmeldung mit der Systemadministratorrolle erstellt. Das Kennwort für diese Anmeldung wird als K8s-Geheimnis aufgezeichnet.

* Eine Systemadministratoranmeldung wird in allen SQL-Instanzen in dem Cluster erstellt, die der Controller besitzt und verwaltet. Diese Anmeldung ist erforderlich, damit der Controller auf diesen Instanzen Verwaltungsaufgaben wie das Setup oder Upgrade von Hochverfügbarkeit ausführen kann. Diese Anmeldungen werden auch für die clusterinterne Kommunikation zwischen SQL-Instanzen verwendet, beispielsweise für die Kommunikation der SQL-Masterinstanz mit einem Datenpool.

> [!NOTE]
> Im aktuellen Release wird nur die Standardauthentifizierung unterstützt. Eine differenzierte Steuerung des Zugriffs auf HDFS-Objekte und Compute- und Datenpools für SQL-Big Data-Cluster ist noch nicht verfügbar.

## <a name="intra-cluster-communication"></a>Clusterinterne Kommunikation

Die Kommunikation mit Nicht-SQL-Diensten innerhalb des Big Data-Clusters wie z.B. zwischen Livy und Spark oder zwischen Spark und dem Speicherpool wird mithilfe von Zertifikaten gesichert. Die gesamte Kommunikation zwischen SQL Server-Instanzen wird mithilfe von SQL-Anmeldungen gesichert.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]zu finden Sie in den folgenden Ressourcen:

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] -Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
