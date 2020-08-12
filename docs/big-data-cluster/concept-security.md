---
title: Sicherheitskonzepte
titleSuffix: SQL Server big data clusters
description: In diesem Artikel werden Sicherheitskonzepte für Big Data-Cluster für SQL Server beschrieben. Dieser Artikel umfasst auch eine Beschreibung von Clusterendpunkten und der Clusterauthentifizierung.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f0d19589c057df0af9ffea711edd8963bc381e2d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730680"
---
# <a name="security-concepts-for-big-data-clusters-2019"></a>Sicherheitskonzepte für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel werden die wichtigsten sicherheitsbezogenen Konzepte in Big Data-Clustern erläutert.

[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] stellen eine kohärente und konsistente Autorisierung und Authentifizierung bereit. Ein Big Data-Cluster kann in Active Directory (AD) über eine vollständig automatisierte Bereitstellung integriert werden, die die AD-Integration für eine vorhandene Domäne einrichtet. Sobald ein Big Data-Cluster mit der AD-Integration konfiguriert ist, können Sie vorhandene Identitäten und Benutzergruppen für den einheitlichen Zugriff auf alle Endpunkte nutzen. Wenn Sie externe Tabellen in SQL Server erstellt haben, können Sie außerdem den Zugriff auf Datenquellen steuern, indem Sie den Benutzern und Gruppen von AD Zugriff auf externe Tabellen gewähren und so die Datenzugriffsrichtlinien an einem einzigen Ort zentralisieren.

In diesem 14-minütigen Video erhalten Sie einen Überblick über die Big Data-Clustersicherheit:

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Overview-Big-Data-Cluster-Security/player?WT.mc_id=dataexposed-c9-niner]


## <a name="authentication"></a>Authentifizierung

Die externen Clusterendpunkte unterstützen die AD-Authentifizierung. Verwenden Sie Ihre AD-Identität, um sich beim Big Data-Cluster zu authentifizieren.

### <a name="cluster-endpoints"></a>Clusterendpunkte

Es gibt fünf Einstiegspunkte für den Big Data-Cluster:

* Masterinstanz: TDS-Endpunkt für den Zugriff auf die SQL Server-Masterinstanz im Cluster mithilfe von Datenbanktools und Anwendungen wie SSMS oder Azure Data Studio. Wenn Sie HDFS- oder SQL Server-Befehle von azdata verwenden, stellt das Tool je nach Vorgang eine Verbindung mit den anderen Endpunkten her.

* Gateway für den Zugriff auf HDFS-Dateien, Spark (Knox): HTTPS-Endpunkt für den Zugriff auf Dienste wie webHDFS und Spark.

* (Controller-)Endpunkt für den Clusterverwaltungsdienst: Verwaltungsdienst für Big Data-Cluster, der REST-APIs für die Verwaltung des Clusters verfügbar macht. Das azdata-Tool erfordert eine Verbindung mit diesem Endpunkt.

* Verwaltungsproxy: Für den Zugriff auf das Dashboard für die Protokollsuche und das Metrikdashboard.

* Anwendungsproxy: Endpunkt zum Verwalten von Anwendungen, die im Big Data-Cluster bereitgestellt werden.

![Clusterendpunkte](media/concept-security/cluster_endpoints.png)

Derzeit gibt es keine Option, zusätzliche Ports zu öffnen, um von außen auf den Cluster zuzugreifen.

## <a name="authorization"></a>Authorization

Im gesamten Cluster lässt die integrierte Sicherheit zwischen verschiedenen Komponenten zu, dass die Identität des ursprünglichen Benutzers durch das Ausgeben von Abfragen von Spark und SQL Server bis hin zu HDFS übermittelt werden kann. Wie bereits erwähnt, unterstützen die verschiedenen externen Clusterendpunkte die AD-Authentifizierung.

Für die Verwaltung des Datenzugriffs gibt es im Cluster zwei Ebenen von Autorisierungsüberprüfungen. Die Autorisierung im Kontext von Big Data erfolgt in SQL Server mithilfe der herkömmlichen SQL Server-Berechtigungen für Objekte und in HDFS mit Steuerungslisten (ACLs), die Benutzeridentitäten bestimmten Berechtigungen zuordnen.

Ein sicherer Big Data-Cluster impliziert konsistente und kohärente Unterstützung für Authentifizierung- und Autorisierungsszenarien sowohl für SQL Server als auch für HDFS/Spark. Authentifizierung ist der Prozess, mit dem die Identität eines Benutzers oder Diensts überprüft und sichergestellt wird, dass der Benutzer oder Dienst das ist, was er zu sein vorgibt. Autorisierung bezieht sich auf das Gewähren oder Verweigern des Zugriffs auf bestimmte Ressourcen basierend auf der Identität des Benutzers, der den Zugriff anfordert. Dieser Schritt wird ausgeführt, nachdem ein Benutzer per Authentifizierung identifiziert wurde.

Im Big Data-Kontext erfolgt die Autorisierung in der Regel über Zugriffssteuerungslisten (Access Control Lists, ACLs), die Benutzeridentitäten bestimmte Berechtigungen zuordnen. HDFS unterstützt die Autorisierung durch Einschränken des Zugriffs auf Dienst-APIs, HDFS-Dateien und die Auftragsausführung.

## <a name="encryption-and-other-security-mechanisms"></a>Verschlüsselung und andere Sicherheitsmechanismen

Die Verschlüsselung der Kommunikation zwischen Clients und externen Endpunkten sowie zwischen Komponenten innerhalb des Clusters wird mithilfe von Zertifikaten durch TLS/SSL gesichert.

Die gesamte Kommunikation zwischen SQL Server-Instanzen, wie z. B. die Kommunikation der SQL-Masterinstanz mit einem Datenpool, wird mithilfe von SQL-Anmeldungen gesichert.

> [!IMPORTANT]
>  Big Data-Cluster verwenden etcd zum Speichern von Anmeldeinformationen. Um Best Practices einzuhalten, müssen Sie sicherstellen, dass Ihr Kubernetes-Cluster so konfiguriert ist, dass etcd-Verschlüsselung für ruhende Daten verwendet wird. Standardmäßig werden Geheimnisse in etcd unverschlüsselt gespeichert. Weitere Informationen zu dieser Verwaltungsaufgabe finden Sie in der Kubernetes-Dokumentation unter https://kubernetes.io/docs/tasks/administer-cluster/kms-provider/ und https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/.


## <a name="basic-administrator-login"></a>Standardanmeldung für Administratoren

Sie können den Cluster entweder im AD-Modus oder nur mithilfe der Standardanmeldung für Administratoren bereitstellen. Für Administratorkontos nur eine Standardanmeldung zu verwenden, ist ein von der Produktion nicht unterstützter Sicherheitsmodus und für die Auswertung des Produkts vorgesehen.

Auch wenn Sie den Active Directory-Modus auswählen, werden Standardanmeldungen für den Clusteradministrator erstellt. Diese Funktion bietet alternativen Zugriff, falls die AD-Konnektivität unterbrochen wird.

Bei der Bereitstellung erhält diese Standardanmeldung Administratorberechtigungen im Cluster. Der Anmeldebenutzer ist Systemadministrator in der SQL Server-Masterinstanz und Administrator im Clustercontroller.
Hadoop-Komponenten unterstützen die Authentifizierung im gemischten Modus nicht. Dies bedeutet, dass für die Authentifizierung beim Gateway (Knox) keine Standardanmeldung für Administratoren verwendet werden kann.

Zu den Anmeldeinformationen, die Sie bei der Bereitstellung definieren müssen, gehört Folgendes:

Benutzername des Clusteradministrators:

 + `AZDATA_USERNAME=<username>`

Kennwort des Benutzeradministrators:  
 + `AZDATA_PASSWORD=<password>`

> [!NOTE]
> Beachten Sie, dass der Benutzername in einem anderen als dem AD-Modus für die Authentifizierung beim Gateway (Knox) für den Zugriff auf HDFS/Spark in Kombination mit dem oben aufgeführten Kennwort verwendet werden muss. In früheren Versionen als SQL Server 2019 CU5 lautete der Benutzername `root`.
> 
> [!INCLUDE [big-data-cluster-root-user](../includes/big-data-cluster-root-user.md)]

## <a name="next-steps"></a>Nächste Schritte

[Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)

[Workshop: Microsoft [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]-Architektur](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)

[Kubernetes RBAC](kubernetes-rbac.md)
