---
title: Active Directory-Objekte
titleSuffix: SQL Server Big Data Cluster
description: Hier erfahren Sie mehr über die Bereitstellung von SQL Server-Big Data-Clustern in der Active Directory-Domäne.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e4f8736beeac2e92d25092c60c3fe7e60127ea94
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942742"
---
# <a name="auto-generated-active-directory-objects"></a>Automatisch generierte Active Directory-Objekte

In diesem Artikel wird beschrieben, was die Active Directory-Konten (AD) und -Gruppen sind, die SQL Server während einer Big Data-Clusterbereitstellung (Big Data-Cluster, BDC) erstellt.

## <a name="accounts--groups"></a>Konten und Gruppen

Die Benutzerkonten und -Gruppen werden während der Clusterbereitstellung in der bereitgestellten [Organisationseinheit (Organisational Unit, OU)](/windows-server/identity/ad-ds/plan/reviewing-ou-design-concepts) generiert.

Jedes der Konten stellt einen Dienst in einem BDC dar. Die Konten besitzen die Dienstprinzipalnamen (SPNs), die für jeden Dienst erforderlich sind. Die SPNs im Besitz der einzelnen Konten können mit dem [setspn](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spn-setspn-syntax.aspx)-Befehl aufgelistet werden.

Die Bereitstellung generiert automatisch Konten- und Gruppennamen. Ab SQL Server 2019 CU5 ist das Konto- oder Gruppennamenpräfix der Name des Bereitstellungsnamespace (BDC-Clustername). Wenn der Clustername für die Elemente in diesem Artikel `bdc` ist, ersetzen Sie `<prefix>` durch `bdc`, um Ihre Konten zu identifizieren.

Das Podsuffix (-x) gibt unten eine variable Pod-ID an. Die unten aufgeführten Namen enthalten kein variables Präfix, das vom Benutzer während der Bereitstellung angegeben wird.

Der klassische Kontoname gilt für Bereitstellungen mithilfe von Versionen vor SQL Server 2019 CU5 sowie für Bereitstellungen, die mit der Option „useSubdomain“ durchgeführt werden, welche in der Sicherheitskonfiguration auf „false“ festgelegt wurde.

| Konto- oder Gruppenname|Weitere Informationen|
|----|---|
|`<prefix>-ctrl`|[Controllerdienstkonto](#controller-service-account)|
|`<prefix>-ngxm`|[Überwachen des Dienstkontos des Dienstproxys](#monitoring-service-proxy-service-account)|
|`<prefix>-ldap`|[LDAP-Benutzersuche](#ldap-lookup-user)|
|`<prefix>-sqc0-x/<prefix>-sqc0`|[SQL Server Benutzer für den Computepool](#compute-pool-sql-server-user)|
|`<prefix>-dmc0-x`|[Data Warehouse-DMS-Benutzer des Computepools](#compute-pool-data-warehouse-dms-user)|
|`<prefix>-dec0-x`|[Data Warehouse-Engine-Benutzer des Computepools](#compute-pool-data-warehouse-engine-user)|
|`<prefix>-sqd0`|[Datenpoolbenutzer in SQL Server](#data-pool-sql-server-user)|
|`<prefix>-sqs0`|[Speicherpoolbenutzer in SQL Server](#storage-pool-sql-server-user)|
|`<prefix>-ynt0-x`|[Benutzer des Speicherpools für den Yarn-Knotenverwaltungsdienst](#storage-pool-yarn-node-manager-service-user)|
|`<prefix>-htt0`|[Benutzer des Speicherpools für den HTTP-Dienst](#storage-pool-http-service-user)|
|`<prefix>-hdt0`|[Benutzer des Speicherpools für den HDFS-Datenknotendiensts](#storage-pool-hdfs-datanode-service-user)|
|`<prefix>-hdnn`|[Benutzer des HDFS-Namenknotendiensts](#hdfs-name-node-service-user)|
|`<prefix>-htnn`|[HTTP-Dienstbenutzer des HDFS-Namenknotens](#hdfs-name-node-http-service-user)|
|`<prefix>-kmnn-x`|[KMS-Dienstbenutzer des Namensknotens](#name-node-kms-service-user)|
|`<prefix>-jnzk-x`|[Zookeeper-JournalNode-Dienstbenutzer](#zookeeper-journalnode-service-users)|
|`<prefix>-htzk`|[Zookeeper-HTTP-Dienstbenutzer](#zookeeper-http-service-user)|
|`<prefix>-yrsh-x`|[Benutzer des Ressourcen-Manager-Diensts von Sparkhead-Yarn](#sparkhead-yarn-resource-manager-service-user)|
|`<prefix>-htsh`|[Sparkhead-HTTP-Benutzer](#sparkhead-http-user)|
|`<prefix>-shsh-x`|[Benutzer des Sparkhead-Spark-Verlaufsdiensts](#sparkhead-spark-history-service-user)|
|`<prefix>-lvsh-x`|[Sparkhead-Livy-Dienstbenutzer](#sparkhead-livy-service-user)|
|`<prefix>-hvsh-x`|[Sparkhead-Hive-Dienstbenutzer](#sparkhead-hive-service-user)|
|`<prefix>-yns0-x`|[Benutzer für den Yarn-Knotenverwaltungsdienst des Spark-Pools](#spark-pool-yarn-node-manager-service-user)|
|`<prefix>-hts0`|[HTTP-Benutzer der Yarn-Knotenverwaltung von Spark-Pool](#spark-pool-yarn-node-manager-http-user)|
|`<prefix>-knox-x`|[Knox-Gatewaybenutzer](#knox-gateway-user)|
|`<prefix>-htgw`|[HTTP-Benutzer für das Knox-Gateway](#knox-gateway-http-user)|
|`<prefix>-apst`|[Benutzer der App-Einrichtung](#app-setup-user)|
|`<prefix>-dmsvc`|[Data Warehouse-DMS-Dienstgruppe](#data-warehouse-dms-service-group)|
|`<prefix>-desvc`|[Dienstgruppe für Data Warehouse-Engine](#data-warehouse-engine-service-group)|

Im folgenden Abschnitt werden weitere Details zu jedem Konto erläutert. Weitere Informationen zu Gruppen finden Sie unter [Gruppen](#groups).

## <a name="controller-management--ldap-related-accounts"></a>Controller, Verwaltung und LDAP-bezogene Konten

### <a name="controller-service-account"></a>Controllerdienstkonto.

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`control`|
|Podname|`control-x`|
|Containername|`controller`|
|Dienstname|`controller`|
|Kontoname (ohne Präfix)| `ctrl`|
|Konto (mit Namespacepräfix)|`<prefix>-ctrl`|
|Klassischer Kontoname|`ctrl-controller`|

### <a name="monitoring-service-proxy-service-account"></a>Überwachen des Dienstproxy-Dienstkontos

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`mgmtproxy`|
|Podname|`mgmtproxy-x`|
|Containername|`service-proxy`|
|Dienstname|`nginx`|
|Konto (ohne Präfix)| `ngxm`|
|Konto (mit Namespacepräfix)|`<prefix>-ngxm`|
|Klassischer Kontoname|`nginx-mgmtproxy`|

### <a name="ldap-lookup-user"></a>LDAP-Benutzersuche

Wird von den Grafana- und Hadoop-Diensten verwendet, um Benutzer über LDAP zu suchen

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`metricsui`|
|Podname|`metricsui-x`|
|Containername|`grafana`|
|Dienstname|`grafana`|
|Kontoname (ohne Präfix)| `ldap`|
|Kontoname (mit Namespacepräfix)|`<prefix>-ldap`|
|Klassischer Kontoname|`ldap-user`|

## <a name="master-pool-accounts"></a>Masterpoolkonten

### <a name="master-pool-sql-server-user"></a>SQL Server-Benutzer des Masterpools

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`master`|
|Podname|`master-x`|
|Containername|`mssql-server`|
|Dienstname|`mssql`|
|Kontoname (ohne Präfix)| `sqmp-x/sqmp`|
|Kontoname (mit Namespacepräfix)|`<prefix>-sqmp-x/<prefix>-sqmp`|
|Klassischer Kontoname|`mssql-master-x`|

### <a name="master-pool-data-warehouse-dms-user"></a>Data Warehouse-DMS-Benutzer des Masterpools

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`master`|
|Podname|`master-x`|
|Containername|`mssql-server`|
|Dienstname|`dwdms`|
|Konto (ohne Präfix)| `dmmp-x`|
|Konto (mit Namespacepräfix)|`<prefix>-dmmp-x`|
|Klassischer Kontoname|`dwdms-master-x`|

### <a name="master-pool-data-warehouse-engine-user"></a>Data Warehouse-Engine-Benutzer des Masterpools

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`master`|
|Podname|`master-x`|
|Containername|`mssql-server`|
|Dienstname|`dweng`|
|Konto (ohne Präfix)| `demp`|
|Konto (mit Namespacepräfix)|`<prefix>-demp-x`|
|Klassischer Kontoname|`dweng-master-x`|

## <a name="compute-pool-accounts"></a>Computepoolkonten

### <a name="compute-pool-sql-server-user"></a>SQL Server-Benutzer des Computepools

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`compute-0`|
|Podname|`compute-0-x`|
|Containername|`mssql-server`|
|Dienstname|`mssql`|
|Konto (ohne Präfix)| `sqc0-x/sqlc0`|
|Konto (mit Namespacepräfix)|`<prefix>-sqc0-x/<prefix>-sqc0`|
|Klassischer Kontoname|`mssql-compute-0-x`|

### <a name="compute-pool-data-warehouse-dms-user"></a>Data Warehouse-DMS-Benutzer des Computepools

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`compute-0`|
|Podname|`compute-0-x`|
|Containername|`mssql-server`|
|Dienstname|`dwdms`|
|Konto (ohne Präfix)| `dmc0-x`|
|Konto (mit Namespacepräfix)|`<prefix>-dmc0-x`|
|Klassischer Kontoname|`dwdms-compute-0-x`|

### <a name="compute-pool-data-warehouse-engine-user"></a>Data Warehouse-Engine-Benutzer des Computepools

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`compute-0`|
|Podname|`compute-0-x`|
|Containername|`mssql-server`|
|Dienstname|`dweng`|
|Konto (ohne Präfix)| `dec0-x`|
|Konto (mit Namespacepräfix)|`<prefix>-dec0-x`|
|Klassischer Kontoname|`dweng-compute-0-x`|

## <a name="data-pool-accounts"></a>Datenpoolkonten

### <a name="data-pool-sql-server-user"></a>Datenpoolbenutzer in SQL Server

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`data-0`|
|Podname|`data-0-x`|
|Containername|`mssql-server`|
|Dienstname|`mssql`|
|Konto (ohne Präfix)| `sqd0`|
|Konto (mit Namespacepräfix)|`<prefix>-sqd0`|
|Klassischer Kontoname|`mssql-data-0`|

## <a name="storage-pool-accounts"></a>Speicherpoolkonten

### <a name="storage-pool-sql-server-user"></a>Speicherpoolbenutzer in SQL Server

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`storage-0`|
|Podname|`storage-0-x`|
|Containername|`mssql-server`|
|Dienstname|`mssql`|
|Konto (ohne Präfix)| `sqs0`|
|Konto (mit Namespacepräfix)|`<prefix>-sqs0`|
|Klassischer Kontoname|`mssql-storage-0`|

### <a name="storage-pool-yarn-node-manager-service-user"></a>Benutzer des Speicherpools für den Yarn-Knotenverwaltungsdienst

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`storage-0`|
|Podname|`storage-0-x`|
|Containername|`hadoop`|
|Dienstname|`Yarn Node Manager`|
|Konto (ohne Präfix)| `ynt0-x`|
|Konto (mit Namespacepräfix)|`<prefix>-ynt0-x`|
|Klassischer Kontoname|`yarnnm-storage-0-x`|

### <a name="storage-pool-http-service-user"></a>Benutzer des Speicherpools für den HTTP-Dienst

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`storage-0`|
|Podname|`storage-0-x`|
|Containername|`hadoop`|
|Dienstname|`HDFS Datanode`|
|Konto (ohne Präfix)| `hdt0`|
|Konto (mit Namespacepräfix)|`<prefix>-hdt0`|
|Klassischer Kontoname|`http-storage-0`|

### <a name="storage-pool-hdfs-datanode-service-user"></a>Benutzer des Speicherpools für den HDFS-Datenknotendiensts

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`storage-0`|
|Podname|`storage-0-x`|
|Containername|`hadoop`|
|Dienstname|`HDFS Datanode`|
|Konto (ohne Präfix)| `hdt0`|
|Konto (mit Namespacepräfix)|`<prefix>-hdt0`|
|Klassischer Kontoname|`hdfsdn-storage-0`|

## <a name="hdfs-accounts"></a>HDFS-Konten

### <a name="hdfs-name-node-service-user"></a>Benutzer des HDFS-Namenknotendiensts

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`nmnode-0`|
|Podname|`nmnode-0-x`|
|Containername|`hadoop`|
|Dienstname|`HDFS Namenode`|
|Konto (ohne Präfix)| `hdnn`|
|Konto (mit Namespacepräfix)|`<prefix>-hdnn`|
|Klassischer Kontoname|`hdfsnn-nmnode`|

### <a name="hdfs-name-node-http-service-user"></a>HTTP-Dienstbenutzer des HDFS-Namenknotens

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`nmnode-0`|
|Podname|`nmnode-0-x`|
|Containername|`hadoop`|
|Dienstname|`HDFS Namenode`|
|Konto (ohne Präfix)| `htnn`|
|Konto (mit Namespacepräfix)|`<prefix>-htnn`|
|Klassischer Kontoname|`http-nmnode`|

## <a name="kms-accounts"></a>KMS-Konten

### <a name="name-node-kms-service-user"></a>KMS-Dienstbenutzer des Namensknotens

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`nmnode-0`|
|Podname|`nmnode-0-x`|
|Containername|`hadoop`|
|Dienstname|`KMS`|
|Konto (ohne Präfix)| `kmnn-x`|
|Konto (mit Namespacepräfix)|`<prefix>-kmnn-x`|
|Klassischer Kontoname|`kms-nmnode-x`|

## <a name="zookeeper-accounts"></a>Zookeeper-Konten

### <a name="zookeeper-journalnode-service-users"></a>Zookeeper-JournalNode-Dienstbenutzer

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`zookeeper`|
|Podname|`zookeeper-x`|
|Containername|`zookeeper`|
|Dienstname|`Journal node`|
|Konto (ohne Präfix)| `jnzk-x`|
|Konto (mit Namespacepräfix)|`<prefix>-jnzk-x`|
|Klassischer Kontoname|`jn-zookeeper-x`|

### <a name="zookeeper-http-service-user"></a>Zookeeper-HTTP-Dienstbenutzer

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`zookeeper`|
|Podname|`zookeeper-x`|
|Containername|`zookeeper`|
|Dienstname|`Zookeeper`|
|Konto (ohne Präfix)| `htzk`|
|Konto (mit Namespacepräfix)|`<prefix>-htzk`|
|Klassischer Kontoname|`http-zookeeper`|

## <a name="spark-related-accounts"></a>Spark zugehörige Benutzer

### <a name="sparkhead-yarn-resource-manager-service-user"></a>Benutzer des Ressourcen-Manager-Diensts von Sparkhead-Yarn

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`sparkhead`|
|Podname|`sparkhead-x`|
|Containername|`hadoop-yarn-jobhistory`|
|Dienstname|`Yarn Resource Manager`|
|Konto (ohne Präfix)| `yrsh-x`|
|Konto (mit Namespacepräfix)|`<prefix>-yrsh-x`|
|Klassischer Kontoname|`yarnrm-sparkhead-x`|

### <a name="sparkhead-http-user"></a>Sparkhead-HTTP-Benutzer

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`sparkhead`|
|Podname|`sparkhead-x`|
|Containername|`*`|
|Dienstname|`*`|
|Konto (ohne Präfix)| `htsh`|
|Konto (mit Namespacepräfix)|`<prefix>-htsh`|
|Klassischer Kontoname|`http-sparkhead`|

### <a name="sparkhead-spark-history-service-user"></a>Benutzer des Sparkhead-Spark-Verlaufsdiensts

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`sparkhead`|
|Podname|`sparkhead-x`|
|Containername|`hadoop-livy-sparkhistory`|
|Dienstname|`Spark History Server`|
|Konto (ohne Präfix)| `shsh-x`|
|Konto (mit Namespacepräfix)|`<prefix>-shsh-x`|
|Klassischer Kontoname|`sph-sparkhead-x`|

### <a name="sparkhead-livy-service-user"></a>Sparkhead-Livy-Dienstbenutzer

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`sparkhead`|
|Podname|`sparkhead-x`|
|Containername|`hadoop-livy-sparkhistory`|
|Dienstname|`Livy`|
|Konto (ohne Präfix)| `lvsh-x`|
|Konto (mit Namespacepräfix)|`<prefix>-lvsh-x`|
|Klassischer Kontoname|`livy-sparkhead-x`|

### <a name="sparkhead-hive-service-user"></a>Sparkhead-Hive-Dienstbenutzer

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`sparkhead`|
|Podname|`sparkhead-x`|
|Containername|`hadoop-hivemetastore`|
|Dienstname|`Hive Metastore`|
|Konto (ohne Präfix)| `hvsh-x`|
|Konto (mit Namespacepräfix)|`<prefix>-hvsh-x`|
|Klassischer Kontoname|`hive-sparkhead-x`|

### <a name="spark-pool-yarn-node-manager-service-user"></a>Benutzer für den Yarn-Knotenverwaltungsdienst des Spark-Pools

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`spark-0`|
|Podname|`spark-0-x`|
|Containername|`hadoop`|
|Dienstname|`Yarn Node Manager`|
|Konto (ohne Präfix)| `yns0-x`|
|Konto (mit Namespacepräfix)|`<prefix>-yns0-x`|
|Klassischer Kontoname|`yarnnm-spark-0-x`|

### <a name="spark-pool-yarn-node-manager-http-user"></a>HTTP-Benutzer der Yarn-Knotenverwaltung von Spark-Pool

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`spark-0`|
|Podname|`spark-0-x`|
|Containername|`hadoop`|
|Dienstname|`Yarn Node Manager`|
|Konto (ohne Präfix)| `hts0`|
|Konto (mit Namespacepräfix)|`<prefix>-hts0`|
|Klassischer Kontoname|`http-spark-0`|

## <a name="knox-accounts"></a>Knox-Konten

### <a name="knox-gateway-user"></a>Knox-Gatewaybenutzer

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`gateway`|
|Podname|`gateway-x`|
|Containername|`knox`|
|Dienstname|`Knox`|
|Konto (ohne Präfix)| `knox-x`|
|Konto (mit Namespacepräfix)|`<prefix>-knox-x`|
|Klassischer Kontoname|`knox-gateway-x`|

### <a name="knox-gateway-http-user"></a>HTTP-Benutzer für das Knox-Gateway

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`gateway`|
|Podname|`gateway-x`|
|Containername|`knox`|
|Dienstname|`Knox`|
|Konto (ohne Präfix)| `htgw`|
|Konto (mit Namespacepräfix)|`<prefix>-htgw`|
|Klassischer Kontoname|`http-gateway`|

## <a name="app-accounts"></a>App-Konten

### <a name="app-setup-user"></a>Benutzer der App-Einrichtung

|Object|Kontoname|
|---|---|
|Skalierungsgruppenname|`appproxy`|
|Podname|`appproxy-x`|
|Containername|`App Service Proxy`|
|Dienstname|`nginx`|
|Konto (ohne Präfix)| `apst`|
|Konto (mit Namespacepräfix)|`<prefix>-apst`|
|Klassischer Kontoname|`app-setup`|

## <a name="groups"></a>Gruppen

Die folgenden Gruppen werden in der vom Benutzer bereitgestellten Organisationseinheit erstellt. Die Mitglieder der Gruppen sind die Benutzer, die oben für die entsprechenden Dienste erstellt wurden.

### <a name="data-warehouse-dms-service-group"></a>Data Warehouse-DMS-Dienstgruppe

|Object|Gruppenname|
|---|---|
|Skalierungsgruppenname|`master/compute-0`|
|Podname|`master-x/compute-0-x`|
|Containername|`mssql-server`|
|Dienstname|`dwdms`|
|Gruppe (ohne Präfix)| `dmsvc`|
|Konto (mit Namespacepräfix)|`<prefix>-dmsvc`|
|Klassischer Kontoname|`dwdms-service`|

### <a name="data-warehouse-engine-service-group"></a>Dienstgruppe für Data Warehouse-Engine

|Object|Gruppenname|
|---|---|
|Skalierungsgruppenname|`master/compute-0`|
|Podname|`master-x/compute-0-x`|
|Containername|`mssql-server`|
|Dienstname|`dweng`|
|Gruppe (ohne Präfix)| `desvc`|
|Konto (mit Namespacepräfix)|`<prefix>-desvc`|
|Klassischer Kontoname|`desvc`|

## <a name="next-steps"></a>Nächste Schritte

[Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] im Active Directory-Modus](deploy-active-directory.md)

[Bereitstellen mehrerer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in derselben Active Directory-Domäne](active-directory-deployment-background.md)
