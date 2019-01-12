---
title: Schnellstart für die Bereitstellung
titleSuffix: SQL Server 2019 big data clusters
description: Exemplarische Vorgehensweise eine Bereitstellung von SQL Server-2019 big Data-Cluster (Vorschau) in Azure Kubernetes Service (AKS).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/17/2018
ms.topic: quickstart
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 39c79c39c04d64656b83004425d476896cbc75db
ms.sourcegitcommit: 202ef5b24ed6765c7aaada9c2f4443372064bd60
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2019
ms.locfileid: "54241701"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Azure Kubernetes Service (AKS)

In diesem Schnellstart verwenden Sie ein Beispielskript für die Bereitstellung, um die SQL Server-2019 big Data-Cluster (Vorschau) zu Azure Kubernetes Service (AKS) bereitstellen. 

> [!TIP]
> ACS ist nur eine Option für das Hosten von Kubernetes für Ihre big Data-Cluster. Weitere Informationen zu anderen Bereitstellungsoptionen sowie wie die Optionen zum Anpassen der Bereitstellung finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md).

Die hier verwendete Standard big Data-Clusterbereitstellung besteht aus einer Instanz von SQL Master, einer Compute-poolinstanz, zwei Daten ressourcenpoolvorlage ressourcenpoolinstanzen und zwei Instanzen von Speicher-Pool. Daten werden beibehalten, über persistente Kubernetes-Volumes, die Speicher-Standardklassen AKS verwenden. Die Standardkonfiguration, die in diesem Schnellstart verwendete eignet sich für Entwicklungs-/testumgebungen.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Erforderliche Komponenten

- Ein Azure-Abonnement.
- [Big Data-Tools](deploy-big-data-tools.md):
   - **mssqlctl**
   - **"kubectl"**
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
   - **Azure-Befehlszeilenschnittstelle**

## <a name="log-in-to-your-azure-account"></a>Melden Sie sich bei Ihrem Azure-Konto

Das Skript verwendet die Azure-Befehlszeilenschnittstelle zum Automatisieren der Erstellung eines AKS-Clusters. Vor dem Ausführen des Skripts müssen Sie beim Azure-Konto mit Azure-Befehlszeilenschnittstelle mindestens einmal anmelden. Führen Sie den folgenden Befehl an einer Eingabeaufforderung aus.

```
az login
```

## <a name="download-the-deployment-script"></a>Laden Sie das Bereitstellungsskript

In dieser schnellstartanleitung wird die Erstellung der big Data-Cluster in AKS über ein Python-Skript automatisiert **bereitstellen – Sql-big-Data-aks.py**. Wenn Sie Python für bereits installiert **Mssqlctl**, Sie muss das Skript erfolgreich in dieser schnellstartanleitung ausführen können. 

Führen Sie in einer Windows PowerShell oder Linux-Bash-Eingabeaufforderung den folgenden Befehl aus, um das Bereitstellungsskript von GitHub herunterladen.

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>Ausführen des Bereitstellungsskripts

Verwenden Sie die folgenden Schritte aus, um das Ausführen des Bereitstellungsskripts. Dieses Skript ein AKS-Diensts in Azure erstellen und dann einen SQL Server-2019 big Data-Cluster in AKS bereitstellen. Sie können auch ändern, das Skript mit anderen [Umgebungsvariablen](deployment-guidance.md#env) zum Erstellen einer benutzerdefinierten Bereitstellung.

1. Führen Sie das Skript mit dem folgenden Befehl ein:

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Wenn Sie sowohl für python3 python2 auf dem Client und im Pfad haben, müssen Sie python3 über den Befehl ausführen: `python3 deploy-sql-big-data-aks.py`.

1. Wenn Sie aufgefordert werden, geben Sie die folgenden Informationen an:

   | Wert | Description |
   |---|---|
   | **Azure-Abonnement-ID** | Die Azure-Abonnement-ID, der für AKS verwendet werden soll. Sie können alle Ihre Abonnements und die dazugehörigen IDs auflisten, indem Sie Ausführung `az account list` in einer anderen Befehlszeile. |
   | **Azure-Ressourcengruppe** | Der Gruppenname des Azure-Ressource für die AKS-Cluster zu erstellen. |
   | **Docker-Benutzername** | Der Docker-Benutzername, das Ihnen als Teil der begrenzten öffentlichen Vorschau bereitgestellt. |
   | **Docker-Kennwort** | Das Docker-Kennwort, das Ihnen als Teil der begrenzten öffentlichen Vorschau bereitgestellt. |
   | **Azure-region** | Der Azure-Region für den neuen AKS-Cluster (standardmäßig **Westus**). |
   | **VM-Größe** | Die [VM-Größe](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) für Knoten im AKS-Cluster (standardmäßig **Standard_L4s**). |
   | **Workerknoten** | Die Anzahl der Worker-Knoten im AKS-Cluster (standardmäßig **3**). |
   | **Clustername** | Der Name des AKS-Clusters und der big Data-Cluster. Der Name Ihres Clusters muss nur alphanumerische Kleinbuchstaben und ohne Leerzeichen sein. (standardmäßig **Sqlbigdata**). |
   | **Kennwort** | Das Kennwort für den Controller, HDFS/Spark-Gateway und Masterinstanz (standardmäßig **MySQLBigData2019**). |
   | **Benutzerkonten** | Benutzername für den Controllerbenutzer (Standard: **Admin**). |

   > [!IMPORTANT]
   > Jeder Anspruch persistentes Volume im Cluster erfordert einen angeschlossenen Datenträger. Big Data-Cluster erfordert derzeit 21 persistentes Volume Ansprüche. Wenn Sie ein Azure-VM-Größe und Anzahl der Knoten auswählen, stellen Sie sicher, dass die Gesamtzahl von Datenträgern, die auf allen Knoten angefügt werden, können größer als oder gleich 21 ist. Z. B. die [Standard_L4s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#ls-series) VM-Größe unterstützt 16 angefügte Datenträgern, damit die drei Knoten bedeutet, dass 48 Datenträger angefügt werden können.

   > [!NOTE]
   > Die `sa` Konto ist ein Systemadministrator für die master SQL Server-Instanz, die während des Setups erstellt wird. Nach dem Erstellen der Bereitstellung der `MSSQL_SA_PASSWORD` Umgebungsvariable ist mit sichtbaren `echo $MSSQL_SA_PASSWORD` im Container Masterinstanz. Aus Sicherheitsgründen ändern Ihre `sa` Kennwort für die master-Instanz nach der Bereitstellung. Weitere Informationen finden Sie unter [Ändern des Systemadministratorkennworts](../linux/quickstart-install-connect-docker.md#sapassword).

1. Das Skript wird gestartet, durch das Erstellen eines AKS-Clusters mit den Parametern, die Sie angegeben haben. Dieser Schritt dauert einige Minuten.

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>Überwachen des status

Nachdem das Skript im AKS-Cluster erstellt wurde, wird er zum Festlegen von erforderlichen Umgebungsvariablen mit den Einstellungen, die Sie zuvor angegeben fortgesetzt. Es ruft dann **Mssqlctl** der big Data-Cluster in AKS bereitstellen.

Das Befehlsfenster der Client gibt den Bereitstellungsstatus. Während der Bereitstellung sehen Sie eine Reihe von Nachrichten, in dem sie den Pod Controller wartet:

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Nach 10 bis 20 Minuten sollten Sie eine Benachrichtigung über der Pod Controller ausgeführt wird:

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.222.222.222:30080
```

> [!IMPORTANT]
> Die gesamte Bereitstellung dauert sehr lange aufgrund der Zeitaufwand für die Container-Images für die Komponenten der big Data-Cluster herunterladen. Er sollte jedoch nicht mehrere Stunden dauern. Wenn Sie Probleme bei der Bereitstellung auftreten, finden Sie unter den [Problembehandlung bei der Bereitstellung](deployment-guidance.md#troubleshoot) Abschnitt im Artikel für die Bereitstellung.

## <a name="inspect-the-cluster"></a>Überprüfen Sie den cluster

Jederzeit während der Bereitstellung können Sie "kubectl" oder das Verwaltungsportal für den Cluster verwenden, um den Status und die Details der Ausführung von big Data-Cluster zu überprüfen.

### <a name="use-kubectl"></a>Verwenden von kubectl

Öffnen Sie ein neues Befehlsfenster mit **"kubectl"** während der Bereitstellung.

1. Führen Sie den folgenden Befehl aus, um eine Zusammenfassung des Status des gesamten Clusters abzurufen:

   ```
   kubectl get all -n <your-cluster-name>
   ```

1. Überprüfen Sie die Kubernetes-Dienste und deren interne und externe Endpunkte mit den folgenden **"kubectl"** Befehl:

   ```
   kubectl get svc -n <your-cluster-name>
   ```

1. Sie können auch den Status der Kubernetes-Pods mithilfe des folgenden Befehls überprüfen:

   ```
   kubectl get pods -n <your-cluster-name>
   ```

1. Finden Sie weitere Informationen zu einem bestimmten Pod mit dem folgenden Befehl ein:

   ```
   kubectl describe pod <pod name> -n <your-cluster-name>
   ```

> [!TIP]
> Weitere Informationen zum Überwachen und Problembehandlung bei einer Bereitstellung finden Sie unter den [Problembehandlung bei der Bereitstellung](deployment-guidance.md#troubleshoot) Abschnitt im Artikel für die Bereitstellung.

### <a name="use-the-cluster-administration-portal"></a>Verwenden Sie das Cluster-Verwaltungsportal

Sobald der Controller-Pod ausgeführt wird, können Sie auch das Verwaltungsportal für den Cluster zum Überwachen der Bereitstellung verwenden. Sie können den Portalzugriff mithilfe der externen IP-Adresse und den Port für die `service-proxy-lb` (z. B.: **https://\<Ip-Adresse\>: 30777/Portal**). Die Anmeldeinformationen verwendet, um sich beim Portal anmelden, entsprechen die Werte für **Controllerbenutzer** und **Kennwort** , die Sie im Bereitstellungsskript angegeben.

Erhalten Sie die IP-Adresse der **-Dienst-Proxy-lb** Dienst mit dem folgenden Befehl in einem nachfolgenden bash- oder Cmd-Fenster:

```bash
kubectl get svc service-proxy-lb -n <your-cluster-name>
```

> [!NOTE]
> In der CTP-Version 2.2 sehen eine sicherheitswarnung Sie beim Zugreifen auf die Webseite, da es sich bei big Data-Cluster derzeit automatisch generierte SSL-Zertifikate verwendet. In CTP-Version 2.2, ist es auch nicht den Status der SQL Server-Masterinstanz angezeigt.

## <a name="connect-to-the-cluster"></a>Verbinden mit dem cluster

Wenn das Bereitstellungsskript abgeschlossen ist, benachrichtigt die Ausgabe Sie Erfolg:

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

Die SQL Server-big Data-Cluster wird nun in AKS bereitgestellt. Sie können jetzt Studio für Azure Data verwenden, für die Verbindung für die master SQL Server-Instanz und die Verwendung von Azure Data Studio HDFS/Spark-Endpunkte.

### <a id="master"></a> Master-Instanz

Master SQL Server-Instanz ist eine herkömmliche SQL Server-Instanz, die mit der relationalen SQL Server-Datenbanken. Die folgenden Schritte beschreiben, Herstellen einer Verbindung mit der Verwendung von Azure Data Studio Masterinstanz.

1. Suchen Sie über die Befehlszeile die IP-Adresse Ihrer master-Instanz mit dem folgenden Befehl aus:

   ```
   kubectl get svc endpoint-master-pool -n <your-cluster-name>
   ```

1. Drücken Sie in Azure Data Studio **F1** > **neue Verbindung**.

1. In **Verbindungstyp**Option **Microsoft SQL Server**.

1. Geben Sie die IP-Adresse in der SQL Server-Masterinstanz **Servernamen** (z. B.: **\<IP-Adresse\>, 31433**).

1. Geben Sie einen SQL-Anmeldenamen **Benutzernamen** (`SA`) und **Kennwort** (das Kennwort, das Sie im Bereitstellungsskript eingegeben haben).

1. Ändern Sie das Ziel **Datenbanknamen** eines relationalen Datenbanken.

   ![Verbinden Sie mit der master-Instanz](./media/quickstart-big-data-cluster-deploy/connect-to-cluster.png)

1. Drücken Sie **Connect**, und die **Serverdashboard** sollte angezeigt werden.

### <a id="hdfs"></a> HDFS/Spark-gateway

Die **HDFS/Spark-Gateway** ermöglicht es Ihnen, für die Arbeit mit dem HDFS-Speicher-Pool und zum Ausführen von Spark-Aufträgen zu verbinden. Die folgenden Schritte beschreiben, wie eine Verbindung mit Azure Data Studio herstellen.

1. Finden Sie über die Befehlszeile die IP-Adresse Ihres HDFS/Spark-Gateways mit dem folgenden Befehl aus:

   ```
   kubectl get svc service-security-lb -n <your-cluster-name>
   ```
 
1. Drücken Sie in Azure Data Studio **F1** > **neue Verbindung**.

1. In **Verbindungstyp**Option **SQL Server-big Data-Cluster**.
   
   > [!TIP]
   > Wenn Sie nicht sehen die **SQL Server-big Data-Cluster** Verbindung geben, stellen Sie sicher, dass Sie installiert haben die [2019 für SQL Server-Erweiterung](../azure-data-studio/sql-server-2019-extension.md) und dass Sie Azure Data Studio nach der Erweiterung abgeschlossen neu gestartet installieren.

1. Geben Sie die IP-Adresse der big Data-Cluster in **Servernamen** (einen Port nicht angegeben).

1. Geben Sie `root` für die **Benutzer** , und geben Sie die **Kennwort** auf Ihre big Data-Cluster, die Sie im Bereitstellungsskript eingegeben haben.

   ![Verbinden Sie mit HDFS/Spark-gateway](./media/quickstart-big-data-cluster-deploy/connect-to-cluster-hdfs-spark.png)

1. Drücken Sie **Connect**, und die **Serverdashboard** sollte angezeigt werden.

## <a name="clean-up"></a>Bereinigen

Wenn Sie SQL Server-big Data-Cluster in Azure testen, sollten Sie die AKS-Cluster, Abschluss, um unerwartete Gebühren zu vermeiden löschen. Entfernen Sie den Cluster nicht, wenn Sie das Produkt weiterhin verwenden möchten.

> [!WARNING]
> Die folgenden Schritte aus, kurzzeitig von dem AKS-Cluster der SQL Server big Data-Cluster auch entfernt. Wenn Sie Datenbanken oder HDFS-Daten, die Sie beibehalten möchten, Sichern Sie die Daten vor dem Löschen des Clusters.

Führen Sie den folgenden Azure CLI-Befehl zum Entfernen der big Data-Cluster und AKS-Diensts in Azure (ersetzen Sie dies `<resource group name>` mit der **Azure-Ressourcengruppe** Sie im Bereitstellungsskript angegeben):

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>Nächste Schritte

Nun, dass der SQL Server-big Data-Cluster bereitgestellt wird, können Laden von Beispieldaten und die Tutorials erkunden:

> [!div class="nextstepaction"]
> [Tutorial: Laden Sie Beispieldaten in eine SQL Server-2019 big Data-cluster](tutorial-load-sample-data.md)