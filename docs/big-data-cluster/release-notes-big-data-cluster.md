---
title: Versionshinweise zu SQL Server-Big Data-Clustern
titleSuffix: SQL Server big data clusters
description: In diesem Artikel werden die neuesten Updates und bekannten Probleme von SQL Server-Big Data-Clustern beschrieben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 02/13/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 38a1e2381bb3b7730a06af09b807886e18a50d13
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78924705"
---
# <a name="sql-server-2019-big-data-clusters-release-notes"></a>Versionshinweise zu Big Data-Clustern für SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Die folgenden Versionshinweise gelten für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Dieser Artikel ist in Abschnitte für jedes einzelne Release unterteilt. Jede Version verfügt über einen Link zu einem Supportartikel, in dem die Änderungen der Kapazitätseinheit und Links zu herunterladbaren Linux-Paketen enthalten sind. In diesem Artikel werden zudem [bekannte Probleme](#known-issues) für die neuesten Releases von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC) aufgeführt.

## <a name="supported-platforms"></a>Unterstützte Plattformen

In diesem Abschnitt werden die Plattformen aufgeführt, die mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC) unterstützt werden.

### <a name="kubernetes-platforms"></a>Kubernetes-Plattformen

|Plattform|Unterstützte Versionen|
|---------|---------|
|Kubernetes|BDC erfordert mindestens die Kubernetes-Version 1.13. Informationen zu Versionsunterstützungsrichtlinien finden Sie unter [Richtlinien zur Unterstützung von Kubernetes-Versionen und Versionsabweichungen](https://kubernetes.io/docs/setup/release/version-skew-policy/).|
|Azure Kubernetes Service (AKS)|BDC erfordert mindestens die AKS-Version 1.13.<br/>Informationen zu Versionsunterstützungsrichtlinien finden Sie unter [Unterstützte Kubernetes-Versionen in AKS](/azure/aks/supported-kubernetes-versions).|

### <a name="host-os-for-kubernetes"></a>Hostbetriebssystem für Kubernetes

|Plattform|Unterstützte Versionen|
|---------|---------|
|Red Hat Enterprise Linux|7.3, 7.4, 7.5, 7.6|
|Ubuntu|16.04|

### <a name="sql-server-editions"></a>SQL Server-Editionen

|Edition|Notizen|
|---------|---------|
|Enterprise<br/>Standard<br/>Entwickler| Die Edition von Big Data-Clustern wird von der Edition der SQL Server-Masterinstanz bestimmt. Zum Zeitpunkt der Bereitstellung wird standardmäßig die Developer Edition bereitgestellt. Sie können die Edition nach der Bereitstellung ändern. Informationen dazu finden Sie unter [Konfigurieren der SQL Server-Masterinstanz](../big-data-cluster/configure-sql-server-master-instance.md). |

## <a name="tools"></a>Tools

|Plattform|Unterstützte Versionen|
|---------|---------|
|`azdata`|Muss dieselbe Nebenversion wie der Server aufweisen (identisch mit der SQL Server-Masterinstanz).<br/><br/>Führen Sie `azdata –-version` aus, um die Version zu überprüfen.<br/><br/>Ab SQL Server 2019 CU2 ist dies Version `15.0.4013`.|
|Azure Data Studio|Rufen Sie den neuesten Build von [Azure Data Studio](https://aka.ms/getazuredatastudio) ab.|

## <a name="release-history"></a>Releaseverlauf

In der folgenden Tabelle wird der Releaseverlauf von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] aufgelistet.

| Release               | Version       | Veröffentlichungsdatum |
|-----------------------|---------------|--------------|
| [CU2](#cu2)           | 15.0.4013.40    | 13.2.2020   |
| [CU1](#cu1)           | 15.0.4003.23   | 01.07.2020   |
| [GDR1](#rtm)            | 15.0.2070.34  | 2019-11-04   |

## <a name="how-to-install-updates"></a>Installieren von Updates

Informationen zum Installieren von Updates finden Sie unter [Upgraden von Big Data-Clustern für SQL Server [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deployment-upgrade.md).

## <a id="cu2"></a> CU2 (Februar 2020)

Kumulatives Update 2-Release (CU2) für SQL Server 2019 Die Version der SQL Server-Datenbank-Engine für dieses Release ist 15.0.4013.40.

|Paketversion | Imagetag |
|-----|-----|
|15.0.4013.40 |[2019-CU2-ubuntu-16.04]

## <a id="cu1"></a> Kumulatives Update 1 (Januar 2020)

Dies ist das CU1-Release für SQL Server 2019. Die Version der SQL Server-Datenbank-Engine für dieses Release ist 15.0.4003.23.

|Paketversion | Imagetag |
|-----|-----|
|15.0.4003.23|[2019-CU1-ubuntu-16.04]

## <a id="rtm"></a> Allgemeine Vertriebsversion 1 (November 2019)

Mit der allgemeinen Vertriebsversion 1 für SQL Server 2019 (GDR1) wird die allgemeine Verfügbarkeit für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-nover.md)] eingeführt. Die Version der SQL Server-Datenbank-Engine für dieses Release ist 15.0.2070.34.

|Paketversion | Imagetag |
|-----|-----|
|15.0.2070.34|[2019-GDR1-ubuntu-16.04]

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="known-issues"></a>Bekannte Probleme

### <a name="deployment-with-private-repository"></a>Bereitstellung mit privatem Repository

- **Problem und Kundenbeeinträchtigung:** Beim Upgrade aus einem privaten Repository müssen bestimmte Anforderungen erfüllt werden.

- **Problemumgehung**: Wenn Sie ein privates Repository verwenden, um die Images für die Bereitstellung oder das Upgrade eines BDC vorab abzurufen, stellen Sie sicher, dass sich die aktuellen Buildimages sowie die Zielbuildimages im privaten Repository befinden. Dadurch kann bei Bedarf ein Rollback durchgeführt werden. Wenn Sie die Anmeldeinformationen des privaten Repositorys seit der ursprünglichen Bereitstellung geändert haben, müssen Sie zudem den entsprechenden geheimen Schlüssel in Kubernetes aktualisieren, bevor Sie das Upgrade durchführen. `azdata` bietet keine Unterstützung für das Aktualisieren der Anmeldeinformationen über die Umgebungsvariablen `AZDATA_PASSWORD` und `AZDATA_USERNAME`. Aktualisieren Sie den geheimen Schlüssel mithilfe von [`kubectl edit secrets`](https://kubernetes.io/docs/concepts/configuration/secret/#editing-a-secret). 

Ein Upgrade unter Verwendung unterschiedlicher privater Repositorys für den aktuellen Build und den Zielbuild wird nicht unterstützt.

### <a name="upgrade-may-fail-due-to-timeout"></a>Beim Upgrade kann aufgrund eines Timeouts ein Fehler auftreten.

- **Problem und Kundenbeeinträchtigung:** Beim Upgrade kann aufgrund eines Timeouts ein Fehler auftreten.

   Der folgende Code zeigt, wie der Fehler aussehen könnte:

   ```
   >azdata.EXE bdc upgrade --name <mssql-cluster>
   Upgrading cluster to version 15.0.4003

   NOTE: Cluster upgrade can take a significant amount of time depending on
   configuration, network speed, and the number of nodes in the cluster.

   Upgrading Control Plane.
   Control plane upgrade failed. Failed to upgrade controller.
   ```

   Dieser Fehler tritt eher auf, wenn Sie das Upgrade des BDC in Azure Kubernetes Service (AKS) durchführen.

- **Problemumgehung**: Erhöhen Sie den Timeoutwert für das Upgrade. 

   Bearbeiten Sie die Konfigurationszuordnung für Upgrades, um die Timeoutwerte für Upgrades zu erhöhen. So bearbeiten Sie die Konfigurationszuordnung für Upgrades:

   1. Führen Sie den folgenden Befehl aus:

      ```bash
      kubectl edit configmap controller-upgrade-configmap
      ```

   2.   Bearbeiten Sie die unten aufgeführten Felder:

       **`controllerUpgradeTimeoutInMinutes`** Gibt die Wartezeit in Minuten an, bis der Controller oder die Controllerdatenbank das Upgrade abgeschlossen hat. Der Standardwert ist 5. Aktualisieren Sie diesen Wert auf mindestens 20.

       **`totalUpgradeTimeoutInMinutes`** : Gibt die kombinierte Zeitdauer an, bis der Controller und die Controllerdatenbank das Upgrade abgeschlossen haben (Upgrade von Controller und Controllerdatenbank). Der Standardwert ist 10. Aktualisieren Sie diesen Wert auf mindestens 40.

       **`componentUpgradeTimeoutInMinutes`** : Gibt die Zeitdauer an, in der jede nachfolgende Phase des Upgrades abgeschlossen sein muss.  Der Standardwert ist 30. Aktualisieren Sie diesen Wert auf 45.

   3.   Speichern Sie Ihre Angaben, und schließen Sie die Anwendung.

   Das unten gezeigte Python-Skript zeigt eine weitere Möglichkeit, um die Timeoutwerte festzulegen:

   ```python
   from kubernetes import client, config
   import json

   def set_upgrade_timeouts(namespace, controller_timeout=20, controller_total_timeout=40, component_timeout=45):
       """ Set the timeouts for upgrades

       The timeout settings are as follows

       controllerUpgradeTimeoutInMinutes: sets the max amount of time for the controller
           or controllerdb to finish upgrading

       totalUpgradeTimeoutInMinutes: sets the max amount of time to wait for both the
           controller and controllerdb to complete their upgrade

       componentUpgradeTimeoutInMinutes: sets the max amount of time allowed for
           subsequent phases of the upgrade to complete
       """
       config.load_kube_config()

       upgrade_config_map = client.CoreV1Api().read_namespaced_config_map("controller-upgrade-configmap", namespace)

       upgrade_config = json.loads(upgrade_config_map.data["controller-upgrade"])

       upgrade_config["controllerUpgradeTimeoutInMinutes"] = controller_timeout

       upgrade_config["totalUpgradeTimeoutInMinutes"] = controller_total_timeout

       upgrade_config["componentUpgradeTimeoutInMinutes"] = component_timeout

       upgrade_config_map.data["controller-upgrade"] = json.dumps(upgrade_config)

       client.CoreV1Api().patch_namespaced_config_map("controller-upgrade-configmap", namespace, upgrade_config_map)
   ```

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>Die Übermittlung von Livy-Aufträgen von Azure Data Studio oder der curl-Befehl schlägt mit dem Fehler 500 fehl

- **Problem und Kundenbeeinträchtigung:** In einer Hochverfügbarkeitskonfiguration werden freigegebene Spark-Ressourcen (`sparkhead`) mit mehreren Replikaten konfiguriert. In diesem Fall können Fehler bei der Livy-Auftragsübermittlung von Azure Data Studio oder `curl` auftreten. Dies können Sie überprüfen, indem Sie `curl` auf einen beliebigen `sparkhead`-Pod ausführen. Dies resultiert dann in einer abgelehnten Verbindung. Beispielsweise geben `curl https://sparkhead-0:8998/` oder `curl https://sparkhead-1:8998` den Fehler 500 zurück.

   Dies geschieht in den folgenden Szenarios:

   - Zookeeper-Pods oder Prozesse einzelner Zookeeper-Instanzen werden mehrmals neu gestartet.
   - Wenn die Netzwerkkonnektivität zwischen `sparkhead`- und Zookeeper-Pods unzuverlässig ist.

- **Problemumgehung**: Beide Livy-Server müssen neu gestartet werden.

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

### <a name="transparent-data-encryption-capabilities-can-not-be-used-with-databases-that-are-part-of-the-availability-group-in-the-sql-server-master-instance"></a>Transparent Data Encryption-Funktionen können nicht mit Datenbanken verwendet werden, die Teil der Verfügbarkeitsgruppe in der SQL Server-Masterinstanz sind.

- **Problem und Kundenbeeinträchtigung:** In Hochverfügbarkeitskonfigurationen können Datenbanken mit aktivierter Verschlüsselung nach einem Failover nicht verwendet werden, da sich die für die Verschlüsselung verwendeten Hauptschlüssel auf den einzelnen Replikaten unterscheiden. 

- **Problemumgehung**: Für dieses Szenario gibt es keine Problemumgehung. Es wird empfohlen, die Verschlüsselung in dieser Konfiguration erst zu aktivieren, wenn ein Fix vorhanden ist.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
