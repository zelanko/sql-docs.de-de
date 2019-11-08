---
title: Versionshinweise zu SQL Server-Big Data-Clustern
titleSuffix: SQL Server big data clusters
description: In diesem Artikel werden die neuesten Updates und bekannten Probleme von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Preview) beschrieben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e868d5db99c3f0be141d28a881d8d8bc6f9c241e
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531626"
---
# <a name="sql-server-big-data-clusters-release-notes"></a>Versionshinweise zu SQL Server-Big Data-Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] erhalten Sie nahezu in Echtzeit Erkenntnisse aus all Ihren Daten. Dies erfolgt über eine vollständige Umgebung für die Arbeit mit umfangreichen Datasets, einschließlich maschinellen Lernens und künstlicher Intelligenz.

In diesem Artikel werden die Updates und bekannten Probleme für die neuesten Releases von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC) aufgeführt.

## <a id="rtm"></a> SQL Server 2019

Mit [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] wurden SQL Server-Big Data Cluster eingeführt.

Sie können SQL Server-Big Data-Cluster für Folgendes verwenden:

- [Bereitstellen skalierbarer Cluster](../big-data-cluster/deploy-get-started.md) aus SQL Server-, Spark- und HDFS-Containern, die auf Kubernetes ausgeführt werden 
- Lesen, Schreiben und Verarbeiten von Big Data von Transact-SQL oder Spark
- Einfaches Kombinieren und Analysieren hochwertiger relationaler Daten mit hohen Volumen von Big Data
- Abfragen externer Datenquellen
- Speichern von Big Data in von SQL Server verwaltetem HDFS
- Abfragen von Daten aus mehreren externen Datenquellen über den Cluster
- Verwenden der Daten für künstliche Intelligenz, maschinelles Lernen und andere Analyseaufgaben
- [Bereitstellen und Ausführen von Anwendungen](../big-data-cluster/concept-application-deployment.md) in [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)]
- Virtualisieren von Daten mit [PolyBase](../relational-databases/polybase/polybase-guide.md). Abfragen von Daten aus externen Datenquellen in SQL Server, Oracle, Teradata, MongoDB und ODBC mit externen Tabellen.
- Bereitstellen der Hochverfügbarkeit für die SQL Server-Masterinstanz und alle Datenbanken mithilfe von Always On-Verfügbarkeitsgruppen

## <a name="sql-server-version"></a>SQL Server-Version

Die aktuelle Version von SQL Server lautet `15.0.2070.34`.

## <a name="image-tags"></a>Imagetags

Das Imagetag für dieses Release ist `2019-GDR1-ubuntu-16.04`.

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="supportability"></a>Unterstützbarkeit

In diesem Abschnitt werden die Plattformen aufgeführt, die mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC) unterstützt werden.

### <a name="kubernetes-platforms"></a>Kubernetes-Plattformen

|Platform|Unterstützte Versionen|
|---------|---------|
|Kubernetes|BDC erfordert mindestens die Kubernetes-Version 1.13. Informationen zu Versionsunterstützungsrichtlinien finden Sie unter [Richtlinien zur Unterstützung von Kubernetes-Versionen und Versionsabweichungen](https://kubernetes.io/docs/setup/release/version-skew-policy/).|
|Azure Kubernetes Service (AKS)|BDC erfordert mindestens die AKS-Version 1.13.<br/>Informationen zu Versionsunterstützungsrichtlinien finden Sie unter [Unterstützte Kubernetes-Versionen in AKS](/azure/aks/supported-kubernetes-versions).|

### <a name="host-os-for-kubernetes"></a>Hostbetriebssystem für Kubernetes

|Platform|Unterstützte Versionen|
|---------|---------|
|Red Hat Enterprise Linux|7.3, 7.4, 7.5, 7.6|
|Ubuntu|16.04|

### <a name="tools"></a>Tools

|Platform|Unterstützte Versionen|
|---------|---------|
|`azdata`|Muss dieselbe Nebenversion wie der Server aufweisen (identisch mit der SQL Server-Masterinstanz).<br/>Führen Sie `azdata –-version` aus, um die Version zu überprüfen. Die aktuelle Version ist `15.0.2070`.|
|Azure Data Studio|Rufen Sie den neuesten Build von [Azure Data Studio](https://aka.ms/getazuredatastudio) ab.|

### <a name="sql-server-editions"></a>SQL Server-Editionen

|Edition|Hinweise|
|---------|---------|
|Enterprise<br/>Standard<br/>Entwickler| Die Edition von Big Data-Clustern wird von der Edition der SQL Server-Masterinstanz bestimmt. Zum Zeitpunkt der Bereitstellung wird standardmäßig die Developer Edition bereitgestellt. Sie können die Edition nach der Bereitstellung ändern. Informationen dazu finden Sie unter [Konfigurieren der SQL Server-Masterinstanz](../big-data-cluster/configure-sql-server-master-instance.md). |

## <a name="known-issues"></a>Bekannte Probleme

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>Die Übermittlung von Livy-Aufträgen von Azure Data Studio oder der curl-Befehl schlägt mit dem Fehler 500 fehl

**Problem und Kundenbeeinträchtigung:** In einer Hochverfügbarkeitskonfiguration werden freigegebene Spark-Ressourcen (Sparkhead) mit mehreren Replikaten konfiguriert. In diesem Fall können Fehler bei der Livy-Auftragsübermittlung von Azure Data Studio oder `curl` auftreten. Dies können Sie überprüfen, indem Sie `curl` auf einen beliebigen Sparkhead-Pod ausführen. Dies resultiert dann in einer abgelehnten Verbindung. Beispielsweise geben `curl https://sparkhead-0:8998/` oder `curl https://sparkhead-1:8998` den Fehler 500 zurück.

Dies geschieht in den folgenden Szenarios:

- Zookeeper-Pods oder Prozesse einzelner Zookeeper-Instanzen werden mehrmals neu gestartet.
- Wenn die Netzwerkkonnektivität zwischen Sparkhead- und Zookeeper-Pods unzuverlässig ist.

**Problemumgehung**: Beide Livy-Server müssen neu gestartet werden.

```bash
kubectl -n <clustername> exec sparkhead-0 -c hadoop-livy-sparkhistory supervisorctl restart livy
```

```bash
kubectl -n <clustername> exec sparkhead-1 -c hadoop-livy-sparkhistory supervisorctl restart livy
```

### <a name="create-memory-optimized-table-when-master-instance-in-an-availability-group"></a>Erstellen einer arbeitsspeicheroptimierten Tabelle, wenn die Masterinstanz sich in einer Verfügbarkeitsgruppe befindet

- **Problem und Kundenbeeinträchtigung:** Sie können den primären Endpunkt, der zum Herstellen einer Verbindung mit Datenbanken in Verfügbarkeitsgruppen (Listener) zur Verfügung gestellt wird, nicht zum Erstellen arbeitsspeicheroptimierter Tabellen verwenden.

- **Problemumgehung**: [Stellen Sie eine Verbindung mit der SQL Server-Instanz her](deployment-high-availability.md#instance-connect), stellen Sie einen Endpunkt zur Verfügung, stellen Sie eine Verbindung mit der SQL Server-Datenbank her, und erstellen Sie die arbeitsspeicheroptimierten Tabellen in der mit der neuen Verbindung erstellten Sitzung, um arbeitsspeicheroptimierte Tabellen zu erstellen, wenn die SQL Server-Masterinstanz sich in einer Verfügbarkeitsgruppe befindet.

### <a name="insert-to-external-tables-active-directory-authentication-mode"></a>Einfügen in externe Tabellen im Active Directory-Authentifizierungsmodus

- **Problem und Kundenbeeinträchtigung:** Wenn die SQL Server-Masterinstanz sich im Active Directory-Authentifizierungsmodus befindet, gibt eine Abfrage, die nur aus externen Tabellen auswählt, von denen sich mindestens eine in einem Speicherpool befindet, und in eine andere externe Tabelle einfügt, Folgendes zurück:

   ```
   Msg 7320, Level 16, State 102, Line 1
   Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "SQLNCLI11". Only domain logins can be used to query Kerberized storage pool.
   ```

- **Problemumgehung**: Passen Sie die Abfrage auf einer der folgenden Weisen an. Verknüpfen Sie die Speicherpooltabelle mit einer lokalen Tabelle, oder fügen Sie zunächst in die lokale Tabelle ein, und lesen Sie dann aus der lokalen Tabelle, um etwas in den Datenpool einzufügen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
