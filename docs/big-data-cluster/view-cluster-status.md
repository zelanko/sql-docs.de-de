---
title: Clusterstatus anzeigen
titleSuffix: SQL Server big data clusters
description: In diesem Artikel erläutert das Anzeigen des Status einer big Data-Cluster mithilfe von Azure Data Studio, Notebooks und Mssqlctl Befehle.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
manager: jroth
ms.date: 06/27/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b3cc78e36fe427966c7730533104c63aa3ed9332
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727331"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Gewusst wie: Anzeigen des Status einer big Data-cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt, wie Sie den Zugriff auf die Dienstendpunkte und Anzeigen des Status einer SQL Server-big Data-Cluster (Vorschau). Sie können beide Studio für Azure Data und **Mssqlctl**, und dieser Artikel deckt beide Verfahren.

## <a id="datastudio"></a> Verwenden von Azure Data Studio

Nach dem Herunterladen der neuesten **Insiders-build** von [Studio für Azure Data](https://aka.ms/azdata-insiders), können Sie Dienstendpunkte anzeigen und der Status einer big Data-cluster mit der SQL Server-big Data-Cluster-Dashboard. Beachten Sie, dass einige der nachstehend genannten Funktionen zunächst nur in den Insider-Build von Azure Data Studio verfügbar sind.

1. Erstellen Sie zunächst eine Verbindung mit Ihrer big Data-Cluster in Azure Data Studio. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer SQL Server big Data-cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

1. Mit der rechten Maustaste auf den Endpunkt der big Data-Cluster, und klicken Sie auf **verwalten**.

   ![Verwalten der rechten Maustaste auf](media/view-cluster-status/right-click-manage.png)

1. Wählen Sie die **SQL Server-Cluster für Big Data** Tab, um das big Data-Cluster-Dashboard zugreifen.

   ![Big Data-Cluster-dashboard](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Dienstendpunkte

Es ist wichtig, um problemlos die verschiedenen Dienste innerhalb einer big Data-Cluster zugreifen zu können. Das big Data-Cluster-Dashboard enthält eine Tabelle der Dienst-Endpunkte, mit dem Sie anzeigen und kopieren Sie die Dienstendpunkte.

![Dienstendpunkte](media/view-cluster-status/service-endpoints.png)

Die ersten Zeilen zur Verfügung, die folgenden Dienste:

- Anwendungsproxy
- Cluster-Management-Dienst
- HDFS und Spark
- Management-Proxy

Diese Dienste aufgelistet, die Endpunkte, die kopiert und eingefügt werden, wenn Sie den Endpunkt für die Verbindung mit diesen Diensten benötigen werden können. Sie können z. B. Klicken Sie auf das Symbol "Kopieren" rechts neben dem Endpunkt und fügen Sie ihn in einem Text-Fenster, das dieses Endpunkts anfordern. Der Cluster-Management-Dienst-Endpunkt ist zum Ausführen der [Cluster Status Notebook](#notebook).

### <a name="dashboards"></a>Dashboards

Die Tabelle im Dienst-Endpunkte verfügbar macht auch mehrere Dashboards für die Überwachung:

- Metrics (Grafana)
- Protokolle (Kibana)
- Spark-Auftrag überwachen
- Spark-Ressourcenverwaltung

Sie können direkt auf diese Links klicken. Sie werden aufgefordert, zweimal, um Ihren Benutzernamen und Kennwort angeben, bevor Sie die Verbindung mit dem Dienst.

### <a id="notebook"></a> Cluster-Status-notebook

1. Sie können auch Clusterstatus von big Data-Cluster anzeigen, indem Sie das Notebook Clusterstatus zu starten. Um das Notebook zu starten, klicken Sie auf die **Clusterstatus** Aufgabe.

    ![Starten](media/view-cluster-status/cluster-status-launch.png)

2. Bevor Sie beginnen, benötigen Sie Folgendes:

    - Big Data-Clusternamen
    - Controller-Benutzername
    - Kennwort des Domänencontrollers
    - Controller-Endpunkte

    Der Standardname für big Data-Cluster ist **Mssql-Cluster** es sei denn, Sie während der Bereitstellung angepasst. Den controllerendpunkt aus dem big Data-Cluster-Dashboard finden Sie in der Tabelle "Dienstendpunkte". Der Endpunkt wird als aufgeführt **Clusterverwaltungsdienst**. Wenn Sie nicht, dass die Anmeldeinformationen wissen, bitten Sie des Administrators, der den Cluster bereitgestellt.

3. Klicken Sie auf **führen Sie Zellen** in der oberen Symbolleiste.

4. Befolgen Sie die Aufforderung Ihre Anmeldeinformationen ein. Drücken Sie EINGABETASTE nach dem Geben Sie jeden Aspekt der Anmeldeinformationen für die big Data-Clustername, Controller-Benutzername und Kennwort des Domänencontrollers.

    > [!Note]
    > Wenn Sie eine Config-Datei-Installation nicht mit Ihrer big Data verfügen, werden für den controllerendpunkt aufgefordert. Geben Sie oder fügen Sie ihn, und drücken Sie dann die EINGABETASTE, um den Vorgang fortzusetzen.

5. Wenn Sie erfolgreich angemeldet haben, wird der Rest des Notebooks der Ausgabe der einzelnen Komponenten der big Data-Cluster angezeigt. Wenn Sie eine bestimmte codezelle erneut ausführen möchten, zeigen Sie auf der codezelle, und klicken Sie auf die **ausführen** Symbol.

## <a name="use-mssqlctl"></a>Verwenden von mssqlctl

Sie können auch [Mssqlctl](deploy-install-mssqlctl.md) Befehle aus, um sowohl Endpunkte als auch den Status des Clusters anzuzeigen.

### <a name="service-endpoints"></a>Dienstendpunkte

Sie können die IP-Adressen der externen Endpunkte für die big Data-Cluster mit den folgenden Schritten erhalten.

1. Finden Sie die IP-Adresse des Endpunkts Controller anhand der EXTERNEN IP-Ausgabe des folgenden **"kubectl"** Befehl:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie nicht den Standardnamen bei der Bereitstellung geändert haben, verwenden Sie `-n mssql-cluster` im vorherigen Befehl. **MSSQL-Cluster** ist der Standardname für die big Data-Cluster.

1. Melden Sie sich bei der big Data-Cluster mit [Mssqlctl Anmeldung](reference-mssqlctl.md). Legen Sie die **--controllerendpunkt** Parameter, um die externe IP-Adresse des Endpunkts Controller.

   ```bash
   mssqlctl login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Geben Sie Benutzername und Kennwort, die Sie für den Controller (CONTROLLER_USERNAME und CONTROLLER_PASSWORD) konfiguriert, während der Bereitstellung.

1. Führen Sie [Mssqlctl Bdc-Endpunktliste](reference-mssqlctl-bdc-endpoint.md) um eine Liste mit einer Beschreibung der einzelnen Endpunkten und ihre entsprechenden Werte für IP-Adresse und den Port abzurufen. 

   ```bash
   mssqlctl bdc endpoint list -o table
   ```

   Die folgende Liste enthält Beispiel für die Ausgabe dieses Befehls:

   ```output
   Description                                             Endpoint                                                   Ip              Name               Port    Protocol
   ------------------------------------------------------  ---------------------------------------------------------  --------------  -----------------  ------  ----------
   Gateway to access HDFS files, Spark                     https://11.111.111.111:30443                               11.111.111.111  gateway            30443   https
   Spark Jobs Management and Monitoring Dashboard          https://11.111.111.111:30443/gateway/default/sparkhistory  11.111.111.111  spark-history      30443   https
   Spark Diagnostics and Monitoring Dashboard              https://11.111.111.111:30443/gateway/default/yarn          11.111.111.111  yarn-ui            30443   https
   Application Proxy                                       https://11.111.111.111:30778                               11.111.111.111  app-proxy          30778   https
   Management Proxy                                        https://11.111.111.111:30777                               11.111.111.111  mgmtproxy          30777   https
   Log Search Dashboard                                    https://11.111.111.111:30777/kibana                        11.111.111.111  logsui             30777   https
   Metrics Dashboard                                       https://11.111.111.111:30777/grafana                       11.111.111.111  metricsui          30777   https
   Cluster Management Service                              https://11.111.111.111:30080                               11.111.111.111  controller         30080   https
   SQL Server Master Instance Front-End                    11.111.111.111,31433                                       11.111.111.111  sql-server-master  31433   tcp
   HDFS File System Proxy                                  https://11.111.111.111:30443/gateway/default/webhdfs/v1    11.111.111.111  webhdfs            30443   https
   Proxy for running Spark statements, jobs, applications  https://11.111.111.111:30443/gateway/default/livy/v1       11.111.111.111  livy               30443   https
   ```

### <a name="view-cluster-status"></a>Clusterstatus anzeigen

Sie können den Status des Clusters mit dem Anzeigen der [Mssqlctl BDC-Status anzeigen](reference-mssqlctl-bdc-status.md) Befehl.

```bash
mssqlctl bdc status show -o table
```

> [!TIP]
> Um die Status-Befehle auszuführen, muss zunächst der Anmeldung mit der **Mssqlctl Anmeldung** -Befehl, der im vorherigen Abschnitt "Endpoints" gezeigt wurde.

Das folgende Beispiel zeigt eine Beispielausgabe für diesen Befehl aus:

```output
Kind     Name           State
-------  -------------  -------
BDC      mssql-cluster  Ready
Control  default        Ready
Master   default        Ready
Compute  default        Ready
Data     default        Ready
Storage  default        Ready
```

### <a name="view-pool-status"></a>Pool-Anzeigestatus

Sie können den Status des Speicherpools innerhalb des Clusters mit Anzeigen der [Mssqlctl BDC-Pool-Status anzeigen](reference-mssqlctl-bdc-pool-status.md) Befehl. Um diesen Befehl verwenden, geben Sie den Typ der Pool mit den `--kind` Parameter. Die Pool-Typen sind:

- Compute
- data
- master
- Spark
- Speicher

Der folgende Befehl zeigt z. B. die Pool-Status des Speicherpools:

```bash
mssqlctl bdc pool status show --kind storage
```

Text wie die folgende Ausgabe sollte angezeigt werden:

```output
[
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/logs/ui",
    "name": "storage-0-0",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-0/sqlmetrics/ui",
    "state": "Running"
  },
  {
    "kind": "Pod",
    "logsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/logs/ui",
    "name": "storage-0-1",
    "nodeMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/nodemetrics/ui",
    "sqlMetricsUrl": "https://11.111.111.111:30080/clusters/mssql-cluster/pods/storage-0-1/sqlmetrics/ui",
    "state": "Running"
  }
]
```

Die `logsUrl` Wert Links, um ein Kibana-Dashboard mit Informationen:

![Kibana-dashboard](./media/view-cluster-status/kibana-dashboard.png)

Die `nodeMetricsUrl` und `sqlMetricsUrl` Werte zu verknüpfen, um einen Grafana-Dashboard zur Überwachung der Integrität von Knoten und SQL-Metriken:

![Grafana-dashboard](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Controller-Anzeigestatus

Sie können den Controllerstatus mit Anzeigen der [Mssqlctl BDC-Steuerelement Status anzeigen](reference-mssqlctl-bdc-control-status.md) Befehl. Es bietet ähnliche Links zu den überwachungsdashboards im Zusammenhang mit der der Controller-Knoten des Clusters big Data.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [wie SQL Server-big Data-Cluster sind](big-data-cluster-overview.md).
