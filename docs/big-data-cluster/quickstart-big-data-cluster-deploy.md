---
title: Bereitstellungs Skript
titleSuffix: SQL Server big data clusters
description: 'Exemplarische Vorgehensweise: Bereitstellung von SQL Server 2019 Big Data Clustern (Vorschauversion) in Azure Kubernetes Service (AKS).'
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7ff1ec3672fbcf101d98ad30913742186dea574d
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419401"
---
# <a name="deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Bereitstellen von SQL Server Big Data-Cluster in Azure Kubernetes Service (AKS)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial verwenden Sie ein Beispielskript für die Bereitstellung von SQL Server 2019 Big Data Cluster (Vorschauversion) in Azure Kubernetes Service (AKS). 

> [!TIP]
> AKS ist nur eine Option zum Hosting von Kubernetes für Ihren Big Data Cluster. Weitere Informationen zu anderen Bereitstellungs Optionen und zum Anpassen von Bereitstellungs Optionen finden Sie unter Bereitstellen [von SQL Server Big Data Clustern auf Kubernetes](deployment-guidance.md).

Die hier verwendete standardmäßige Big Data Cluster Bereitstellung besteht aus einer SQL-Master Instanz, einer computepoolinstanz, zwei Daten Pool Instanzen und zwei Speicherpool Instanzen. Daten werden permanent mithilfe von Kubernetes permanenten Volumes verwendet, von denen die AKS-Standard Speicher Klassen verwendet werden. Die in diesem Tutorial verwendete Standardkonfiguration eignet sich für dev/Test-Umgebungen.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Vorraussetzungen

- Ein Azure-Abonnement.
- [Big Data-Tools](deploy-big-data-tools.md):
   - **azdata**
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server 2019-Erweiterung**
   - **Azure CLI**

## <a name="log-in-to-your-azure-account"></a>Melden Sie sich bei Ihrem Azure-Konto an.

Das Skript verwendet Azure CLI, um die Erstellung eines AKS-Clusters zu automatisieren. Vor dem Ausführen des Skripts müssen Sie sich mindestens einmal bei Ihrem Azure-Konto mit Azure CLI anmelden. Führen Sie den folgenden Befehl an einer Eingabeaufforderung aus.

```
az login
```

## <a name="download-the-deployment-script"></a>Herunterladen des Bereitstellungs Skripts

In diesem Tutorial wird die Erstellung des Big Data Clusters in AKS mithilfe eines python-Skripts **Deploy-SQL-Big-Data-AKS.py**automatisiert. Wenn Sie python für **azdata**bereits installiert haben, sollten Sie das Skript in diesem Tutorial erfolgreich ausführen können. 

Führen Sie in einer Windows PowerShell-oder Linux bash-Eingabeaufforderung den folgenden Befehl aus, um das Bereitstellungs Skript von GitHub herunterzuladen.

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>Ausführen des Bereitstellungs Skripts

Führen Sie die folgenden Schritte aus, um das Bereitstellungs Skript auszuführen. Mit diesem Skript wird ein AKS-Dienst in Azure erstellt und dann ein SQL Server 2019 Big Data-Cluster für AKS bereitgestellt. Sie können das Skript auch mit anderen [Umgebungsvariablen](deployment-guidance.md#configfile) ändern, um eine benutzerdefinierte Bereitstellung zu erstellen.

1. Führen Sie das Skript mit dem folgenden Befehl aus:

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Wenn Sie sowohl python3 als auch python2 auf dem Client Computer und im Pfad haben, müssen Sie den Befehl mit python3 `python3 deploy-sql-big-data-aks.py`ausführen.

1. Wenn Sie dazu aufgefordert werden, geben Sie folgende Informationen ein:

   | Wert | Beschreibung |
   |---|---|
   | **Azure-Abonnement-ID** | Die Azure-Abonnement-ID, die für AKS verwendet werden soll. Sie können alle Ihre Abonnements und deren IDs auflisten, indem Sie `az account list` von einer anderen Befehlszeile ausführen. |
   | **Azure-Ressourcengruppe** | Der Name der Azure-Ressourcengruppe, die für den AKS-Cluster erstellt werden soll. |
   | **Azure-Region** | Die Azure-Region für den neuen AKS-Cluster (Standard- **USA, Westen**). |
   | **Computer Größe** | Die für Knoten im AKS-Cluster zu verwendende [Computer Größe](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) (Standard **Standard_L8s**). |
   | **Workerknoten** | Die Anzahl der workerknoten im AKS-Cluster (Standardwert: **1**). |
   | **Cluster Name** | Der Name des AKS-Clusters und des Big Data Clusters. Der Name des Big Data Clusters darf nur alphanumerische Zeichen in Kleinbuchstaben und keine Leerzeichen enthalten. (Standard **sqlbigdata**). |
   | **Kennwort** | Kennwort für den Controller, das HDFS/Spark-Gateway und die Master Instanz (Standard **MySQLBigData2019**). |
   | **Controller Benutzer** | Benutzername für den Controller Benutzer (Standard: **Admin**). |

Die folgenden Parameter sind für die Teilnehmer am SQL Server 2019 Big Data Cluster Early Adopter-Programm erforderlich: **Docker-Benutzername**und **docker-Kennwort**. Ab CTP 3,2 sind Sie nicht mehr erforderlich.

   > [!IMPORTANT]
   > Die standardmäßige **Standard_L8s** -Computer Größe ist möglicherweise nicht in jeder Azure-Region verfügbar. Wenn Sie eine andere Computer Größe auswählen, stellen Sie sicher, dass die Gesamtanzahl der Datenträger, die über die Knoten im Cluster angefügt werden können, größer oder gleich 24 ist. Jeder persistente volumenforderungs im Cluster erfordert einen angefügten Datenträger. Derzeit sind für Big Data Cluster 24 persistente volumenforderungen erforderlich. Beispielsweise unterstützt die [Standard_L8s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#lsv2-series) -Computer Größe 32 angefügte Datenträger, sodass Sie Big Data Cluster mit einem einzelnen Knoten dieser Computer Größe auswerten können.

   > [!NOTE]
   > Das `sa` Konto ist ein Systemadministrator auf der SQL Server Master Instanz, die während des Setups erstellt wird. Nach dem Erstellen der bereit `MSSQL_SA_PASSWORD` Stellung kann die Umgebungsvariable durch Ausführen `echo $MSSQL_SA_PASSWORD` von im masterstanzcontainer erkannt werden. Ändern Sie `sa` aus Sicherheitsgründen das Kennwort für die Master Instanz nach der Bereitstellung. Weitere Informationen finden Sie unter [Ändern des SA](../linux/quickstart-install-connect-docker.md#sapassword)-Kennworts.

1. Das Skript erstellt zunächst einen AKS-Cluster mithilfe der Parameter, die Sie angegeben haben. Dieser Schritt dauert einige Minuten.

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>Überwachen des Status

Nachdem das Skript den AKS-Cluster erstellt hat, werden die erforderlichen Umgebungsvariablen mit den Einstellungen festgelegt, die Sie zuvor angegeben haben. Anschließend werden **azdata** aufgerufen, um den Big Data Cluster in AKS bereitzustellen.

Das Client Befehlsfenster gibt den Bereitstellungs Status aus. Während des Bereitstellungs Prozesses sollte eine Reihe von Nachrichten angezeigt werden, die auf den Controller Pod warten:

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Nach 10 bis 20 Minuten sollten Sie benachrichtigt werden, dass der Controller Pod ausgeführt wird:

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> Die gesamte Bereitstellung kann aufgrund der Zeit, die zum Herunterladen der Container Images für die Komponenten des Big Data Clusters erforderlich ist, viel Zeit in Anspruch nehmen. Es sollte jedoch nicht mehrere Stunden dauern. Wenn Sie Probleme mit der Bereitstellung haben, finden Sie weitere Informationen unter [Überwachung und Problembehandlung SQL Server Big Data Cluster](cluster-troubleshooting-commands.md).

## <a name="inspect-the-cluster"></a>Überprüfen des Clusters

Sie können während der Bereitstellung jederzeit den Status und die Details zum laufenden Big Data Cluster mithilfe von **kubectl** oder **azdata** überprüfen.

### <a name="use-kubectl"></a>Verwenden von kubectl

Öffnen Sie ein neues Befehlsfenster, um **kubectl** während des Bereitstellungs Prozesses zu verwenden.

1. Führen Sie den folgenden Befehl aus, um eine Zusammenfassung des Status für den gesamten Cluster zu erhalten:

   ```
   kubectl get all -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie den Namen des Big Data Clusters nicht geändert haben, wird das Skript standardmäßig auf **sqlbigdata**festgelegt.

1. Überprüfen Sie die kubernetes-Dienste und ihre internen und externen Endpunkte mit dem folgenden **kubectl** -Befehl:

   ```
   kubectl get svc -n <your-big-data-cluster-name>
   ```

1. Sie können den Status der kubernetes Pods auch mit dem folgenden Befehl überprüfen:

   ```
   kubectl get pods -n <your-big-data-cluster-name>
   ```

1. Weitere Informationen zu einem bestimmten Pod finden Sie unter dem folgenden Befehl:

   ```
   kubectl describe pod <pod name> -n <your-big-data-cluster-name>
   ```

> [!TIP]
> Weitere Informationen zum Überwachen und behandeln von Problemen bei einer Bereitstellung finden Sie unter Überwachung und Problembehandlung für [SQL Server Big Data-Cluster](cluster-troubleshooting-commands.md).

## <a name="connect-to-the-cluster"></a>Herstellen einer Verbindung mit dem Cluster

Wenn das Bereitstellungs Skript abgeschlossen ist, werden Sie von der Ausgabe über Erfolg benachrichtigt:

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

Der SQL Server Big Data-Cluster ist jetzt auf AKS bereitgestellt. Nun können Sie Azure Data Studio verwenden, um eine Verbindung mit dem Cluster herzustellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem SQL Server Big Data Cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="clean-up"></a>Bereinigen

Wenn Sie SQL Server Big Data-Cluster in Azure testen, sollten Sie den AKS-Cluster löschen, wenn Sie fertig sind, um unerwartete Gebühren zu vermeiden. Entfernen Sie den Cluster nicht, wenn Sie ihn weiter verwenden möchten.

> [!WARNING]
> Die folgenden Schritte unterbrechen den AKS-Cluster, der die SQL Server Big Data Cluster entfernt. Wenn Sie über Datenbanken oder HDFS-Daten verfügen, die Sie beibehalten möchten, sichern Sie diese Daten, bevor Sie den Cluster löschen.

Führen Sie den folgenden Azure CLI Befehl aus, um den Big Data Cluster und den AKS-Dienst in `<resource group name>` Azure zu entfernen (ersetzen Sie durch die **Azure-Ressourcengruppe** , die Sie im Bereitstellungs Skript angegeben haben):

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>Nächste Schritte

Das Bereitstellungs Skript hat den Azure Kubernetes-Dienst konfiguriert und außerdem einen SQL Server 2019 Big Data Cluster bereitgestellt. Sie können auch zukünftige bereit Stellungen über manuelle Installationen anpassen. Weitere Informationen zur Bereitstellung von Big Data Clustern und zum Anpassen von bereit Stellungen finden Sie unter Bereitstellen [SQL Server Big Data Clustern auf Kubernetes](deployment-guidance.md).

Nachdem der SQL Server Big Data-Cluster bereitgestellt wurde, können Sie Beispiel Daten laden und die Tutorials durchsuchen:

> [!div class="nextstepaction"]
> [Tutorial: Laden von Beispiel Daten in einen SQL Server 2019 Big Data-Cluster](tutorial-load-sample-data.md)