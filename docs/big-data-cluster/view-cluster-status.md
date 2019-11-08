---
title: Clusterstatus anzeigen
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird erläutert, wie Sie den Status eines Big-Data-Clusters mithilfe von Azure Data Studio, Notebooks und „azdata“-Befehlen anzeigen.
author: yualan
ms.author: alayu
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 45cf5461b9154d397ee5365fd275d2545a3cc376
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531589"
---
# <a name="how-to-view-the-status-of-a-big-data-cluster"></a>Anzeigen des Status eines Big-Data-Clusters 

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie auf die Dienstendpunkte zugreifen und den Status von Big Data-Clusterkomponenten für SQL Server anzeigen. Sie können sowohl Azure Data Studio als auch **azdata** verwenden. Beide Verfahren werden in diesem Artikel erläutert.

## <a id="datastudio"></a> Verwenden von Azure Data Studio

Nachdem Sie den neuesten **Insider-Build** von [Azure Data Studio](https://aka.ms/getazuredatastudio) heruntergeladen haben, können Sie mithilfe des Dashboards des Big-Data-Clusters für SQL Server Dienstendpunkte sowie den Status eines Big-Data-Clusters anzeigen. Einige der unten aufgeführten Features sind erstmals im Insider-Build von Azure Data Studio verfügbar.

1. Stellen Sie zunächst eine Verbindung mit Ihrem Big-Data-Cluster in Azure Data Studio her. Weitere Informationen finden Sie unter [Connect to a SQL Server big data cluster with Azure Data Studio (Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server mithilfe von Azure Data Studio)](connect-to-big-data-cluster.md).

1. Klicken Sie mit der rechten Maustaste auf den Endpunkt des Big-Data-Clusters, und klicken Sie auf **Verwalten**.

   ![Rechtsklick auf „Verwalten“](media/view-cluster-status/right-click-manage.png)

1. Klicken Sie auf die Registerkarte **SQL Server Big Data Cluster** (Big-Data-Cluster für SQL Server), um auf das Dashboard des Big-Data-Clusters zuzugreifen.

   ![Dashboard des Big-Data-Clusters](media/view-cluster-status/bdc-dashboard.png)

### <a name="service-endpoints"></a>Dienstendpunkte

Es ist wichtig, einfach auf die verschiedenen Dienste innerhalb eines Big-Data-Clusters zugreifen zu können. Das Dashboard des Big-Data-Clusters stellt eine Dienstendpunkttabelle bereit, in der die Dienstendpunkte angezeigt werden und aus der diese kopiert werden können.

![Dienstendpunkte](media/view-cluster-status/service-endpoints.png)

Diese Dienste listen die Endpunkte auf, die Sie kopieren und einfügen können, wenn Sie den Endpunkt für die Verbindung mit diesen Diensten benötigen. Sie können beispielsweise auf das Kopiersymbol rechts neben dem Endpunkt klicken und diesen dann in ein Textfenster einfügen, in dem er angefordert wird. Der Endpunkt des Clusterverwaltungsdiensts wird zum Ausführen des [Notebooks für den Clusterstatus](#notebook) benötigt.

### <a name="dashboards"></a>Dashboards

In der Dienstendpunkttabelle werden auch mehrere Dashboards für die Überwachung offengelegt:

- Metriken (Grafana)
- Protokolle (Kibana)
- Spark-Auftragsüberwachung
- Spark-Ressourcenverwaltung

Sie können direkt auf diese Links klicken. Sie müssen sich beim Zugriff auf diese Dashboards authentifizieren. Geben Sie für die Dashboards „Metriken“ und „Protokolle“ die Controller-Administratoranmeldeinformationen an, die Sie zum Zeitpunkt der Bereitstellung mithilfe der Umgebungsvariablen **AZDATA_USERNAME** und **AZDATA_PASSWORD** festlegen. Spark-Dashboards verwenden Gateway-Anmeldeinformationen (Knox): entweder AD-Identität in einem Cluster, der in AD oder **Root**-Benutzer integriert ist, und **AZDATA_PASSWORD**, wenn die Standardauthentifizierung in Ihrem Cluster verwendet wird. 

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

1. Melden Sie sich beim Big-Data-Cluster mit [azdata login](reference-azdata.md) an. Legen Sie den Parameter **--controller-endpoint** auf die externe IP-Adresse des Controllerendpunkts fest.

   ```bash
   azdata login --endpoint https://<ip-address-of-controller-svc-external>:30080 --username <user-name>
   ```

   Geben Sie den Benutzernamen und das Kennwort an (AZDATA_USERNAME und AZDATA_PASSWORD), die Sie während der Bereitstellung für den Controller konfiguriert haben. 
   Für die AD-Authentifizierung lautet der Befehl wie folgt:

  ```bash
   azdata login --endpoint https://<control_domain_name>:30080 --auth ad
   ```

1. Führen Sie [`azdata bdc endpoint list`](reference-azdata-bdc-endpoint.md) aus, um eine Liste mit Beschreibungen jedes Endpunkts sowie deren entsprechende IP-Adressen und Portwerte abzurufen. 

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

Sie können den Status des Clusters mit dem Befehl [`azdata bdc status show`](reference-azdata-bdc-status.md) anzeigen.

```bash
azdata bdc status show
```

> [!TIP]
> Zum Ausführen der Statusbefehle müssen Sie sich zunächst mit dem Befehl **azdata login** anmelden, der im vorangegangenen Abschnitt zu Endpunkten gezeigt wurde.

Im Folgenden wird eine Beispielausgabe dieses Befehls angezeigt:

```output
 Bdc: ready                                                                                                                                                                                                          Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Services: ready                                                                                                                                                                                                     Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Servicename    State    Healthstatus    Details

 spark          ready    healthy         -
 sql            ready    healthy         -
 hdfs           ready    healthy         -
 control        ready    healthy         -
 gateway        ready    healthy         -
 app            ready    healthy         -


 Spark Services: ready                                                                                                                                                                                               Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 sparkhead       ready    healthy         StatefulSet sparkhead is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Sql Services: ready                                                                                                                                                                                                 Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 master          ready    healthy         StatefulSet master is healthy
 compute-0       ready    healthy         StatefulSet compute-0 is healthy
 data-0          ready    healthy         StatefulSet data-0 is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Hdfs Services: ready                                                                                                                                                                                                Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 nmnode-0        ready    healthy         StatefulSet nmnode-0 is healthy
 zookeeper       ready    healthy         StatefulSet zookeeper is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy
 sparkhead       ready    healthy         StatefulSet sparkhead is healthy


 Control Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 controldb       ready    healthy         StatefulSet controldb is healthy
 control         ready    healthy         ReplicaSet control is healthy
 metricsdc       ready    healthy         DaemonSet metricsdc is healthy
 metricsui       ready    healthy         ReplicaSet metricsui is healthy
 metricsdb       ready    healthy         StatefulSet metricsdb is healthy
 logsui          ready    healthy         ReplicaSet logsui is healthy
 logsdb          ready    healthy         StatefulSet logsdb is healthy
 mgmtproxy       ready    healthy         ReplicaSet mgmtproxy is healthy
 controlwd       ready    healthy         ReplicaSet controlwd is healthy


 Gateway Services: ready                                                                                                                                                                                             Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 gateway         ready    healthy         StatefulSet gateway is healthy


 App Services: ready                                                                                                                                                                                                 Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 appproxy        ready    healthy         ReplicaSet appproxy is healthy
```

### <a name="view-specific-resource-status"></a>Anzeigen des Status einer bestimmten Ressource

Sie können den Status einer bestimmten Ressource im Cluster mit dem Befehl [azdata bdc status show](reference-azdata-bdc-status.md) anzeigen. Wenn Sie diesen Befehl verwenden, können Sie mit dem `--resource`-Parameter filtern. Beispiele für `--resource`-Parametereingaben

- master
- Steuerung
- compute-0
- storage-0
- gateway

Der folgende Befehl zeigt z. B. den Status des Speicherpools an:

```bash
azdata bdc status show --all --resource storage-0
```

Wenn Sie den Status aller Komponenten anzeigen möchten, die einen bestimmten Dienst ausführen, müssen Sie die entsprechende `azdata bdc <serviceName> status show`-Befehlsgruppe verwenden. Beispiel:

- azdata bdc sql status show –-alle
- azdata bdc hdfs status show –-alle
- azdata bdc spark status show –-alle

Nachfolgend sehen Sie eine Beispielausgabe:

```output
  Storage-0: ready                                                                                                                                                                                                    Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Instances: running                                                                                                                                                                                                  Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 storage-0-0     running  healthy         Pod storage-0-0 is healthy
 storage-0-1     running  healthy         Pod storage-0-1 is healthy


 Dashboards
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Name            Url

 nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/nodemetrics/ui
 sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/sqlmetrics/ui
 logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/logs/ui
 ```

> [!TIP]
> Führen Sie den Befehl "Status" mit `--all`-Parametern für weitere Integritätsdetails aus, einschließlich Links zu den Dashboards „Metriken“ und „Protokolle“, die der jeweiligen Instanz entsprechen. Im Folgenden sehen Sie eine Beispielausgabe unter Verwendung der `--all`-Parameter:

```output
 Spark: ready                                                                                                                                                                                                        Health Status:  healthy
 ===========================================================================================================================================================================================================================================
 Resources: ready                                                                                                                                                                                                    Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Resourcename    State    Healthstatus    Details

 sparkhead       ready    healthy         StatefulSet sparkhead is healthy
 storage-0       ready    healthy         StatefulSet storage-0 is healthy


 Sparkhead Resources: running                                                                                                                                                                                        Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 sparkhead-0     running  healthy         Pod sparkhead-0 is healthy
 sparkhead-1     running  healthy         Pod sparkhead-1 is healthy


      Dashboards
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      Name            Url

      nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/nodemetrics/ui
      sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/sqlmetrics/ui
      logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/sparkhead-1/status/logs/ui


 Storage-0 Resources: running                                                                                                                                                                                        Health Status:  healthy
 -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 Instancename    State    Healthstatus    Details

 storage-0-0     running  healthy         Pod storage-0-0 is healthy
 storage-0-1     running  healthy         Pod storage-0-1 is healthy


      Dashboards
      --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      Name            Url

      nodeMetricsUrl  https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/nodemetrics/ui
      sqlMetricsUrl   https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/sqlmetrics/ui
      logsUrl         https://13.91.50.9:30777/api/v1/bdc/instances/storage-0-1/status/logs/ui
```

Der `logsUrl`-Wert verweist auf ein Kibana-Dashboard:

![Kibana-Dashboard](./media/view-cluster-status/kibana-dashboard.png)

> [!NOTE]
> Der (alte) Microsoft Edge-Browser ist nicht mit Kibana kompatibel. Sie müssen den Chromium-basierten Browser verwenden, damit das Dashboard korrekt angezeigt wird. Wenn Sie die Dashboards mit einem nicht unterstützten Browser laden, wird eine leere Seite angezeigt. Klicken Sie hier, um unterstützte Browser für Kibana anzuzeigen.

Die Werte für `nodeMetricsUrl` und `sqlMetricsUrl` verweisen auf ein Grafana-Dashboard zur Überwachung von Kubernetes-Knotenmetriken und Big Data-Cluster-Dienstmetriken:

![Grafana-Dashboard](./media/view-cluster-status/grafana-dashboard.png)

![SQL](./media/view-cluster-status/grafana-sql-status.png)

### <a name="view-controller-status"></a>Anzeigen des Controllerstatus

Sie können den Controllerstatus mit dem Befehl [`azdata bdc control status show`](reference-azdata-bdc-control-status.md) anzeigen. Dieser stellt ähnliche Links zu den Dashboards für die Überwachung bereit, die im Zusammenhang mit den Controllerkomponenten des Big Data-Clusters stehen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]?](big-data-cluster-overview.md).
