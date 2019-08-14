---
title: Clusterstatus anzeigen
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie Sie den Status eines Big-Data-Clusters mithilfe von Azure Data Studio, Notebooks und „azdata“-Befehlen anzeigen.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c6dca94b8bd7547222394d7809cb003b9e936982
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419286"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Anzeigen des Status eines Big-Data-Clusters

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie auf die Dienstendpunkte zugreifen und den Status eines Big-Data-Clusters für SQL Server (Vorschauversion) anzeigen. Sie können sowohl Azure Data Studio als auch **azdata** verwenden. Beide Verfahren werden in diesem Artikel erläutert.

## <a id="datastudio"></a> Verwenden von Azure Data Studio

Nachdem Sie den neuesten **Insider-Build** von [Azure Data Studio](https://aka.ms/azdata-insiders) heruntergeladen haben, können Sie mithilfe des Dashboards des Big-Data-Clusters für SQL Server Dienstendpunkte sowie den Status eines Big-Data-Clusters anzeigen. Beachten Sie, dass einige der unten aufgeführten Features erstmals im Insider-Build von Azure Data Studio verfügbar sind.

1. Stellen Sie zunächst eine Verbindung mit Ihrem Big-Data-Cluster in Azure Data Studio her. Weitere Informationen finden Sie unter [Connect to a SQL Server big data cluster with Azure Data Studio (Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server mithilfe von Azure Data Studio)](connect-to-big-data-cluster.md).

1. Klicken Sie mit der rechten Maustaste auf den Endpunkt des Big-Data-Clusters, und klicken Sie auf **Verwalten**.

   ![Rechtsklick auf „Verwalten“](media/view-cluster-status/right-click-manage.png)

1. Klicken Sie auf die Registerkarte **SQL Server Big Data Cluster** (Big-Data-Cluster für SQL Server), um auf das Dashboard des Big-Data-Clusters zuzugreifen.

   ![Dashboard des Big-Data-Clusters](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Dienstendpunkte

Es ist wichtig, einfach auf die verschiedenen Dienste innerhalb eines Big-Data-Clusters zugreifen zu können. Das Dashboard des Big-Data-Clusters stellt eine Dienstendpunkttabelle bereit, in der die Dienstendpunkte angezeigt werden und aus der diese kopiert werden können.

![Dienstendpunkte](media/view-cluster-status/service-endpoints.png)

Die ersten paar Zeilen umfassen folgende Dienste:

- Anwendungsproxy
- Clusterverwaltungsdienst
- HDFS und Spark
- Verwaltungsproxy

Diese Dienste listen die Endpunkte auf, die Sie kopieren und einfügen können, wenn Sie den Endpunkt für die Verbindung mit diesen Diensten benötigen. Sie können beispielsweise auf das Kopiersymbol rechts neben dem Endpunkt klicken und diesen dann in ein Textfenster einfügen, in dem er angefordert wird. Der Endpunkt des Clusterverwaltungsdiensts wird zum Ausführen des [Notebooks für den Clusterstatus](#notebook) benötigt.

### <a name="dashboards"></a>Dashboards

In der Dienstendpunkttabelle werden auch mehrere Dashboards für die Überwachung offengelegt:

- Metriken (Grafana)
- Protokolle (Kibana)
- Spark-Auftragsüberwachung
- Spark-Ressourcenverwaltung

Sie können direkt auf diese Links klicken. Sie werden zweimal aufgefordert, Ihren Benutzernamen und Ihr Kennwort anzugeben, bevor eine Verbindung mit dem Dienst hergestellt wird.

### <a id="notebook"></a> Notebook für den Clusterstatus

1. Sie können auch den Clusterstatus des Big-Data-Clusters anzeigen, indem Sie das Notebook für den Clusterstatus starten. Klicken Sie auf die Aufgabe **Clusterstatus**, um das Notebook zu starten.

    ![Starten](media/view-cluster-status/cluster-status-launch.png)

2. Bevor Sie beginnen, benötigen Sie folgende Elemente:

    - Name des Big-Data-Clusters
    - Benutzername des Controllers
    - Kennwort des Controllers
    - Endpunkte des Controllers

    Der Standardname des Big-Data-Clusters ist **mssql-cluster**, sofern Sie diesen nicht im Laufe der Bereitstellung angepasst haben. Sie finden den Endpunkt des Controllers in der Dienstendpunkttabelle im Dashboard des Big-Data-Clusters. Der Endpunkt wird als **Clusterverwaltungsdienst** aufgeführt. Wenn Sie die Anmeldeinformationen nicht kennen, fragen Sie den Administrator, der Ihren Cluster bereitgestellt hat.

3. Klicken Sie in der oberen Symbolleiste auf **Run Cells** (Zellen ausführen).

4. Befolgen Sie die Aufforderung zur Eingabe Ihrer Anmeldeinformationen. Nachdem Sie die Anmeldeinformationen für den Namen des Big-Data-Clusters, den Benutzernamen sowie das Kennwort des Controllers eingegeben haben, drücken Sie die EINGABETASTE.

    > [!Note]
    > Wenn Sie keine Konfigurationsdatei für Ihre Big Data eingerichtet haben, werden Sie nach dem Endpunkt des Controllers gefragt. Geben oder fügen Sie ihn ein, und drücken Sie dann die EINGABETASTE, um fortzufahren.

5. Wenn Sie erfolgreich eine Verbindung hergestellt haben, zeigt der Rest des Notebooks die Ausgabe der einzelnen Komponenten des Big-Data-Clusters an. Wenn Sie eine bestimmte Codezelle erneut ausführen möchten, zeigen Sie mit der Maus auf die Codezelle, und klicken Sie auf das Symbol zum **Ausführen**.

## <a name="use-azdata"></a>Verwenden von azdata

Sie können auch [azdata](deploy-install-azdata.md)-Befehle zum Anzeigen beider Endpunkte sowie des Clusterstatus verwenden.

### <a name="service-endpoints"></a>Dienstendpunkte

Mithilfe der folgenden Schritte können Sie die IP-Adressen der externen Endpunkte für den Big-Data-Cluster abrufen.

1. Suchen Sie die IP-Adresse des Controller-Endpunkts in der Ausgabe der externen IP des folgenden **kubectl**-Befehls:

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie den Standardnamen während der Bereitstellung nicht geändert haben, verwenden Sie im vorherigen Befehl `-n mssql-cluster`. **mssql-cluster** ist der Standardname für den Big-Data-Cluster.

1. Melden Sie sich beim Big-Data-Cluster mit [azdata login](reference-azdata.md) an. Legen Sie den Parameter **--controller-endpoint** auf die externe IP-Adresse des Controllerendpunkts fest.

   ```bash
   azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
   ```

   Geben Sie den Benutzernamen und das Kennwort an (CONTROLLER_USERNAME und CONTROLLER_PASSWORD), die Sie während der Bereitstellung für den Controller konfiguriert haben.

1. Führen Sie [azdata bdc endpoint list](reference-azdata-bdc-endpoint.md) aus, um eine Liste mit Beschreibungen jedes Endpunkts sowie deren entsprechende IP-Adressen und Portwerte abzurufen. 

   ```bash
   azdata bdc endpoint list -o table
   ```

   Die folgende Liste zeigt eine Beispielausgabe dieses Befehls an:

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

Sie können den Status des Clusters mit dem Befehl [azdata bdc status show](reference-azdata-bdc-status.md) anzeigen.

```bash
azdata bdc status show -o table
```

> [!TIP]
> Zum Ausführen der Statusbefehle müssen Sie sich zunächst mit dem Befehl **azdata login** anmelden, der im vorangegangenen Abschnitt zu Endpunkten gezeigt wurde.

Im Folgenden wird eine Beispielausgabe dieses Befehls angezeigt:

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

### <a name="view-pool-status"></a>Anzeigen des Poolstatus

Sie können den Status von Pools im Cluster mit dem Befehl [azdata bdc pool status show](reference-azdata-bdc-pool-status.md) anzeigen. Geben Sie den Typ von Pool mit dem Parameter `--kind` an, um diesen Befehl zu verwenden. Die Pooltypen sind folgende:

- compute
- data
- master
- spark
- storage

Der folgende Befehl zeigt z. B. den Poolstatus des Speicherpools an:

```bash
azdata bdc pool status show --kind storage
```

Der Text sollte etwa wie die folgende Ausgabe aussehen:

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

Der `logsUrl`-Wert verweist auf ein Kibana-Dashboard mit Protokollinformationen:

![Kibana-Dashboard](./media/view-cluster-status/kibana-dashboard.png)

Die Werte `nodeMetricsUrl` und `sqlMetricsUrl` verweisen auf ein Grafana-Dashboard für die Überwachung der Knotenintegrität sowie von SQL-Metriken:

![Grafana-Dashboard](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Anzeigen des Controllerstatus

Sie können den Status des Controllers mit dem Befehl [azdata bdc control status show](reference-azdata-bdc-control-status.md) anzeigen. Dieser stellt ähnliche Links zu den Dashboards für die Überwachung bereit, die im Zusammenhang mit den Controllerknoten des Big-Data-Clusters stehen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [What are SQL Server big data clusters? (Was sind Big Data-Cluster für SQL Server?)](big-data-cluster-overview.md).
