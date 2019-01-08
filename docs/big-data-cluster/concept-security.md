---
title: Schlüsselbegriffe der Sicherheit
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt die Sicherheitskonzepte für SQL Server-2019 big Data-Cluster (Vorschau). Dies schließt ein, die die clusterendpunkte und die clusterauthentifizierung beschreibt.
author: nelgson
ms.author: negust
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: seodec18
ms.openlocfilehash: d4da38df828b2859de07a7676fc5070bcecf6329
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030574"
---
# <a name="security-concepts-for-sql-server-big-data-clusters"></a>Schlüsselbegriffe der Sicherheit für SQL Server-big Data-Cluster

Ein sichere big Data-Cluster bedeutet konsistenten und kohärenten-Unterstützung für Authentifizierung und Autorisierung Szenarien, in SQL Server und HDFS/Spark. Authentifizierung ist der Prozess der Überprüfung der Identität eines Benutzers oder der Dienst aus, und stellen Sie sicher, dass sie sind, die sie behauptet werden, dass sein. Autorisierung bezieht sich auf gewähren oder Verweigern des Zugriffs auf bestimmte Ressourcen, die basierend auf der Identität des anfordernden Benutzers. Dieser Schritt wird ausgeführt, nachdem ein Benutzer über die Authentifizierung identifiziert wurde.

Autorisierung in Big Data-Kontext erfolgt in der Regel über Zugriffssteuerungslisten (ACLs), die Zuordnen von Benutzeridentitäten mit bestimmten Berechtigungen. HDFS unterstützt Autorisierung, indem Sie Zugriff auf Dienst-APIs, die HDFS-Dateien und die Ausführung von Aufträgen beschränkt.

Dieser Artikel behandelt die wichtigsten sicherheitsbezogenen Konzepte in die big Data-Cluster.

## <a name="cluster-endpoints"></a>Cluster-Endpunkte

Es gibt drei Einstiegspunkte für die big Data-cluster

* HDFS/Spark (Knox)-Gateway – Dies ist eine HTTPS-basierte-Endpunkt. Andere Endpunkte werden über diesen Proxy. HDFS/Spark-Gateway wird verwendet, für den Zugriff auf Dienste wie WebHDFS und Livy. Wenn Sie Verweise auf Knox sehen, ist dies der Endpunkt an.

* Controllerendpunkt - big Data-Cluster Management-Dienst, der REST-APIs, die für die Verwaltung des Clusters verfügbar macht. Einige Tools, z.B. das Admin-Portal, über diesen Endpunkt auch zugegriffen werden.

* Masterinstanz - TDS-Endpunkts für die Datenbanktools und Anwendungen im Cluster eine Verbindung mit Master für SQL Server-Instanz.

![Cluster-Endpunkte](media/concept-security/cluster_endpoints.png)

Derzeit besteht keine Möglichkeit, Öffnung zusätzlicher Ports für den Zugriff auf den Cluster von außerhalb.

### <a name="how-endpoints-are-secured"></a>Wie Endpunkte gesichert werden

Sichern von Endpunkten in der big Data-Cluster erfolgt mit Kennwörtern, die sein können/aktualisiert entweder mithilfe von Umgebungsvariablen oder die CLI-Befehle. Alle internen Cluster-Kennwörter werden als Kubernetes-Geheimnisse gespeichert.  

## <a name="authentication"></a>Authentifizierung

Bei der Bereitstellung des Clusters an, eine Anzahl von Anmeldungen erstellt.

Einige diese Anmeldungen sind für Dienste miteinander kommunizieren, und andere sind für Endbenutzer auf den Cluster zugreifen.

### <a name="end-user-authentication"></a>Authentifizierung von Endbenutzern
Bei der Bereitstellung des Clusters, muss eine Anzahl von Kennwörtern für Endbenutzer über Umgebungsvariablen festgelegt werden. Dies sind Kennwörter, die SQL-Administratoren und Clusteradministratoren den Zugriff auf Dienste zu verwenden:

Controller-Benutzername:
 + CONTROLLER_USERNAME = < Controller_username >

Kennwort des Domänencontrollers:  
 + CONTROLLER_PASSWORD = < Controller_password >

SQL-Master-SA-Kennwort: 
 + MSSQL_SA_PASSWORD = < Controller_sa_password >

Kennwort für den Zugriff auf das HDFS/Spark-Endpunkt:
 + KNOX_PASSWORD = < Knox_password >

### <a name="intra-cluster-authentication"></a>Innerhalb des Clusters-Authentifizierung

Nach der Bereitstellung des Clusters sind eine Reihe von SQL-Anmeldungen erstellt:

* Eine spezielle SQL-Anmeldung wird in der Controller-SQL-Instanz erstellt, die vom System verwaltet, mit der Rolle "Sysadmin" ist. Das Kennwort für diese Anmeldung wird als geheimer Schlüssel K8s erfasst.

* Eine Sysadmin-Anmeldung wird in allen SQL-Instanzen im Cluster erstellt, die Controller besitzt und verwaltet. Es ist erforderlich für Controller, um administrative Aufgaben wie das HA-Installation oder Aktualisierung, auf diese Instanzen auszuführen. Diese Anmeldungen werden auch für die Kommunikation zwischen SQL-Instanzen, z. B. die master SQL-Instanz, die Kommunikation mit einem Datenpool innerhalb des Clusters verwendet.

> [!NOTE]
> In der aktuellen Version wird nur Standardauthentifizierung unterstützt. Differenzierte Zugriffssteuerung auf Objekte von HDFS und SQL big Data-Cluster COMPUTE- und Pools ist noch nicht verfügbar.

## <a name="intra-cluster-communication"></a>Kommunikation zwischen Clustern

Kommunikation mit nicht-SQL-Dienste in der big Data-Cluster, z.B. Livy Spark oder Spark für den Speicherpool wird mithilfe von Zertifikaten gesichert. Alle SQL Server auf SQL Server-Kommunikation wird mithilfe von SQL-Anmeldungen gesichert.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter den folgenden Artikeln:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
- [Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Kubernetes](quickstart-big-data-cluster-deploy.md)
