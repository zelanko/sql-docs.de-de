---
title: Clusterstatus anzeigen
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie Sie den Status eines Big Data Clusters mithilfe der Befehle Azure Data Studio, Notebooks und azdata anzeigen.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c6dca94b8bd7547222394d7809cb003b9e936982
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419286"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Anzeigen des Status eines Big Data Clusters

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie auf die Dienst Endpunkte zugreifen und den Status einer SQL Server Big Data Cluster (Vorschau) anzeigen. Sie können sowohl Azure Data Studio als auch **azdata**verwenden, und in diesem Artikel werden beide Verfahren behandelt.

## <a id="datastudio"></a>Azure Data Studio verwenden

Nachdem Sie den neuesten **Insider-Build** von [Azure Data Studio](https://aka.ms/azdata-insiders)heruntergeladen haben, können Sie Dienst Endpunkte und den Status eines Big Data Clusters mit dem SQL Server Big Data Cluster-Dashboard anzeigen. Beachten Sie, dass einige der unten aufgeführten Features nur im Insider-Build Azure Data Studio verfügbar sind.

1. Erstellen Sie zuerst eine Verbindung mit Ihrem Big Data Cluster in Azure Data Studio. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem SQL Server Big Data Cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

1. Klicken Sie mit der rechten Maustaste auf den Big Data Cluster-Endpunkt, und klicken Sie auf **Verwalten**.

   ![Rechtsklick verwalten](media/view-cluster-status/right-click-manage.png)

1. Wählen Sie die SQL Server Registerkarte **Big Data-Cluster** aus, um auf das Dashboard des Big Data Clusters zuzugreifen

   ![Dashboard für Big Data-Cluster](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Dienst Endpunkte

Es ist wichtig, in der Lage zu sein, auf einfache Weise auf die verschiedenen Dienste innerhalb eines Big Data Clusters zuzugreifen. Das Big Data Cluster-Dashboard enthält eine Tabelle mit Dienst Endpunkten, mit der Sie die Dienst Endpunkte anzeigen und kopieren können.

![Dienst Endpunkte](media/view-cluster-status/service-endpoints.png)

Die ersten Zeilen machen die folgenden Dienste verfügbar:

- Anwendungs Proxy
- Cluster Verwaltungsdienst
- HDFS und Spark
- Verwaltungs Proxy

Diese Dienste Listen die Endpunkte auf, die kopiert und eingefügt werden können, wenn Sie den Endpunkt zum Herstellen einer Verbindung mit diesen Diensten benötigen. Beispielsweise können Sie auf das Kopier Symbol rechts neben dem Endpunkt klicken und es dann in ein Textfenster einfügen, das diesen Endpunkt anfordert. Der Cluster Verwaltungsdienst-Endpunkt ist erforderlich, um das [Cluster Status Notebook](#notebook)auszuführen.

### <a name="dashboards"></a>Dashboards

In der Tabelle "Service Endpunkte" sind auch mehrere Dashboards für die Überwachung verfügbar:

- Metriken (grafana)
- Protokolle (kibana)
- Spark-Auftrags Überwachung
- Spark-Ressourcenverwaltung

Sie können direkt auf diese Links klicken. Sie werden zweimal aufgefordert, Ihren Benutzernamen und Ihr Kennwort anzugeben, bevor Sie eine Verbindung mit dem Dienst herstellen.

### <a id="notebook"></a>Cluster Status Notebook

1. Sie können den Cluster Status des Big Data Clusters auch anzeigen, indem Sie das Notebook für den Cluster Status starten. Um das Notebook zu starten, klicken Sie auf den Task **Cluster Status** .

    ![Gestartet](media/view-cluster-status/cluster-status-launch.png)

2. Bevor Sie beginnen, benötigen Sie Folgendes:

    - Big Data-Cluster Name
    - Controller Benutzername
    - Controller Kennwort
    - Controller Endpunkte

    Der Standard Big Data Cluster Name lautet **MSSQL-Cluster** , es sei denn, Sie haben ihn während der Bereitstellung angepasst. Sie finden den Controller Endpunkt über das Big Data Cluster-Dashboard in der Tabelle Dienst Endpunkte. Der Endpunkt wird als **Cluster Verwaltungsdienst**aufgeführt. Wenn Sie die Anmelde Informationen nicht kennen, Fragen Sie den Administrator, der Ihren Cluster bereitgestellt hat.

3. Klicken Sie in der oberen Symbolleiste auf **Zellen ausführen** .

4. Befolgen Sie die Eingabeaufforderung für Ihre Anmelde Informationen. Drücken Sie die EINGABETASTE, nachdem Sie die Anmelde Informationen für den Big Data Cluster Namen, den Controller Benutzernamen und das Controller Kennwort eingegeben haben.

    > [!Note]
    > Wenn Sie nicht über eine Konfigurationsdatei mit Ihrem Big Data verfügen, werden Sie aufgefordert, den Controller Endpunkt zu verwenden. Geben oder fügen Sie Sie ein, und drücken Sie die EINGABETASTE, um fortzufahren.

5. Wenn Sie erfolgreich eine Verbindung hergestellt haben, zeigt der Rest des Notebooks die Ausgabe der einzelnen Komponenten des Big Data Clusters an. Wenn Sie eine bestimmte codezelle erneut ausführen möchten, zeigen Sie mit der Maus auf die codezelle, und klicken Sie auf das Symbol **Ausführen** .

## <a name="use-azdata"></a>Verwenden von azdata

Sie können auch [azdata](deploy-install-azdata.md) -Befehle verwenden, um sowohl Endpunkte als auch den Cluster Status anzuzeigen.

### <a name="service-endpoints"></a>Dienst Endpunkte

Mithilfe der folgenden Schritte können Sie die IP-Adressen der externen Endpunkte für den Big Data Cluster abrufen.

1. Suchen Sie die IP-Adresse des Controller Endpunkts, indem Sie die externe IP-Ausgabe des folgenden **kubectl** -Befehls überprüfen:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie den Standardnamen während der Bereitstellung nicht geändert haben `-n mssql-cluster` , verwenden Sie im vorherigen Befehl. **MSSQL-Cluster** ist der Standardname für den Big Data Cluster.

1. Melden Sie sich mit der [azdata-Anmeldung](reference-azdata.md)beim Big Data-Cluster an. Legen Sie den Parameter **--Controller-Endpoint** auf die externe IP-Adresse des Controller Endpunkts fest.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Geben Sie den Benutzernamen und das Kennwort für den Controller (CONTROLLER_USERNAME und CONTROLLER_PASSWORD) während der Bereitstellung an.

1. Führen Sie die [azdata BDC Endpoint List](reference-azdata-bdc-endpoint.md) aus, um eine Liste mit einer Beschreibung der einzelnen Endpunkte und ihrer entsprechenden IP-Adresse und Port Werte zu erhalten. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   Die folgende Liste zeigt die Beispielausgabe dieses Befehls:

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

Sie können den Status des Clusters mit dem Befehl [azdata BDC Status Show](reference-azdata-bdc-status.md) anzeigen.

```bash
azdata bdc status show -o table
```

> [!TIP]
> Zum Ausführen der Status Befehle müssen Sie sich zunächst mit dem **azdata-Anmelde** Befehl anmelden, der im Abschnitt vorherige Endpunkte angezeigt wurde.

Das folgende Beispiel zeigt die Ausgabe dieses Befehls:

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

### <a name="view-pool-status"></a>Anzeigen des Pool Status

Sie können den Status von Pools im Cluster mit dem Befehl [azdata BDC Pool Status Show](reference-azdata-bdc-pool-status.md) anzeigen. Wenn Sie diesen Befehl verwenden möchten, geben Sie den Pooltyp `--kind` mit dem Parameter an. Die pooltypen lauten wie folgt:

- Compute
- data
- master
- Kerze
- Speicher

Der folgende Befehl zeigt z. b. den Pool Status des Speicherpools an:

```bash
azdata bdc pool status show --kind storage
```

Es sollte ein Text angezeigt werden, der der folgenden Ausgabe ähnelt:

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

Der `logsUrl` Wert verknüpft mit einem kibana-Dashboard mit Protokollinformationen:

![Kibana-Dashboard](./media/view-cluster-status/kibana-dashboard.png)

Die `nodeMetricsUrl` Werte `sqlMetricsUrl` und sind mit einem grafana-Dashboard zum Überwachen der Knoten Integrität und SQL-Metriken verknüpft:

![Grafana-Dashboard](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Anzeigen des Controller Status

Sie können den Controller Status mit dem Befehl [azdata BDC Control Status Show](reference-azdata-bdc-control-status.md) anzeigen. Es stellt ähnliche Links zu den Überwachungs Dashboards bereit, die sich auf die Controller Knoten des Big Data Clusters beziehen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind SQL Server Big Data Cluster](big-data-cluster-overview.md).
