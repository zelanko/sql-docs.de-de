---
title: Bereitstellen von Big-Data-Clustern mit einem Python-Skript
titleSuffix: SQL Server Big Data Clusters
description: Hier erfahren Sie, wie Sie mit einem Skript Big Data-Cluster für SQL Server in Azure Kubernetes Service (AKS) bereitstellen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1b2a838f8ad386b8a236304401308d5be0f63ff1
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73706345"
---
# <a name="use-a-python-script-to-deploy-a-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Verwenden eines Python-Skripts zum Bereitstellen eines Big-Data-Clusters für SQL Server in Azure Kubernetes Service (AKS)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial verwenden Sie ein Python-Beispielskript, um [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] in Azure Kubernetes Service (AKS) bereitzustellen.

> [!TIP]
> Sie können Big-Data-Cluster nicht nur mit AKS in Kubernetes hosten. Informationen zu anderen Bereitstellungsoptionen und zum Anpassen dieser Optionen finden Sie unter [Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in Kubernetes](deployment-guidance.md).

Die hier verwendete Standardbereitstellung für Big-Data-Cluster besteht aus einer SQL-Masterinstanz, einer Computepoolinstanz, zwei Datenpoolinstanzen und zwei Speicherpoolinstanzen. Daten werden dauerhaft mit persistenten Kubernetes-Volumes gespeichert, die die Standardspeicherklassen von AKS verwenden. Die Standardkonfiguration, die in diesem Tutorial verwendet wird, eignet sich für Entwicklungs- und Testumgebungen.

## <a name="prerequisites"></a>Voraussetzungen

- ein Azure-Abonnement
- [Big-Data-Tools:](deploy-big-data-tools.md)
   - **azdata**
   - **kubectl**
   - **Azure Data Studio**
   - **Erweiterung für SQL Server 2019**
   - **Azure CLI**

## <a name="log-in-to-your-azure-account"></a>Anmelden bei Ihrem Azure-Konto

Das Skript verwendet die Azure CLI, um die Erstellung eines AKS-Clusters zu automatisieren. Sie müssen sich mindestens einmal bei Ihrem Azure-Konto mit der Azure CLI anmelden, bevor Sie das Skript ausführen. Geben Sie über eine Eingabeaufforderung den folgenden Befehl ein:

```
az login
```

## <a name="download-the-deployment-script"></a>Herunterladen des Bereitstellungsskripts

In diesem Tutorial wird die Erstellung des Big-Data-Clusters in AKS mit dem Python-Skript **deploy-sql-big-data-aks.py** automatisiert. Wenn Sie Python für **azdata**bereits installiert haben, sollten Sie das Skript in diesem Tutorial problemlos ausführen können. 

Führen Sie in PowerShell unter Windows oder Bash unter Linux den folgenden Befehl aus, um das Bereitstellungsskript von GitHub herunterzuladen.

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>Ausführen des Bereitstellungsskripts

Führen Sie die folgenden Schritte aus, um das Bereitstellungsskript auszuführen. Dieses erstellt einen AKS-Dienst in Azure und stellt anschließend einen Big-Data-Cluster für SQL Server 2019 in AKS bereit. Sie können das Skript auch mit anderen [Umgebungsvariablen](deployment-guidance.md#configfile) anpassen, um eine benutzerdefinierte Bereitstellung zu erstellen.

1. Führen Sie das Skript mit dem folgenden Befehl aus:

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Wenn sowohl python3 als auch python2 auf dem Clientcomputer installiert sind und beide Versionen in den Suchpfad für Befehle eingebunden sind, müssen Sie den Befehl mit python3 ausführen: `python3 deploy-sql-big-data-aks.py`.

1. Geben Sie folgende Informationen ein, wenn Sie dazu aufgefordert werden:

   | value | und Beschreibung |
   |---|---|
   | **Azure-Abonnement-ID** | Die Azure-Abonnement-ID, die für AKS verwendet werden soll. Sie können Ihre Abonnements und deren IDs auflisten, indem Sie `az account list` über eine andere Befehlszeile ausführen. |
   | **Azure-Ressourcengruppe** | Der Name der Azure-Ressourcengruppe, die für den AKS-Cluster erstellt werden soll. |
   | **Azure-Region** | Die Azure-Region für den neuen AKS-Cluster (Standardwert: **westus** (USA, Westen)). |
   | **Größe des Computers** | Die [Größe des Computers](https://docs.microsoft.com/azure/virtual-machines/windows/sizes), die für Knoten im AKS-Cluster verwendet werden soll (Standardwert: **Standard_L8s**). |
   | **Workerknoten** | Die Anzahl der Workerknoten im AKS-Cluster (Standardwert: **1**). |
   | **Clustername** | Der Name des AKS-Clusters und des Big-Data-Clusters. Der Name Ihres Big-Data-Clusters darf nur alphanumerische Zeichen enthalten. Außerdem darf er nur aus Kleinbuchstaben bestehen und keine Leerzeichen enthalten (Standardwert: **sqlbigdata**). |
   | **Kennwort** | Das Kennwort für den Controller, das HDFS/Spark-Gateway und die Masterinstanz (Standardwert: **MySQLBigData2019**). |
   | **Benutzername** | Der Benutzername für den Controllerbenutzer (Standardwert: **admin**). |

   > [!IMPORTANT]
   > Die Standardgröße **Standard_L8s** für Computer ist möglicherweise nicht in allen Azure-Regionen verfügbar. Wenn Sie eine andere Größe auswählen, müssen Sie sicherstellen, dass die Gesamtzahl der Datenträger, die den Knoten im Cluster angefügt werden können, größer oder gleich 24 ist. Auf dem Cluster ist für jeden PersistentVolumeClaim ein angefügter Datenträger erforderlich. Aktuell sind für Big-Data-Cluster 24 PersistentVolumeClaims erforderlich. Für die Computergröße [Standard_L8s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#lsv2-series) werden beispielsweise 32 angefügte Datenträger unterstützt, sodass Sie Big-Data-Cluster mit einem einzelnen Knoten dieser Größe auswerten können.

   > [!NOTE]
   > Das SQL Server-Konto `sa` ist während der Bereitstellung eines Big Data-Clusters deaktiviert. In der SQL Server-Masterinstanz wird eine neue SysAdmin-Anmeldung bereitgestellt, die den gleichen Namen wie für die Eingabe **Benutzername** und das der Eingabe **Kennwort** entsprechende Kennwort verwendet. Die gleichen Werte für **Benutzername** und **Kennwort** werden zur Bereitstellung eines Controller-Administratorbenutzers verwendet. Der einzige für das Gateway (Knox) unterstützte Benutzer ist **root**, und das Kennwort ist das gleiche wie oben.

1. Das Skript erstellt zunächst einen AKS-Cluster mithilfe der Parameter, die Sie angegeben haben. Dieser Schritt dauert einige Minuten.

   <img src="./media/quickstart-big-data-cluster-deploy/script-parameters.png" width="800px" alt="Script parameters and AKS cluster creation"/>

## <a name="monitor-the-status"></a>Überwachen des Status

Nachdem das Skript den AKS-Cluster erstellt hat, werden die erforderlichen Umgebungsvariablen mit den Einstellungen festgelegt, die Sie zuvor angegeben haben. Anschließend wird **azdata** aufgerufen, um den Big-Data-Cluster in AKS bereitzustellen.

Der Bereitstellungsstatus wird im Befehlsfenster des Clients ausgegeben. Im Verlauf des Bereitstellungsprozesses sollten mehrere Wartemeldungen für den Controllerpod angezeigt werden:

```output
2018-11-15 15:42:02.0209 UTC | INFO | Waiting for controller pod to be up...
```

Nach 10 bis 20 Minuten sollten Sie benachrichtigt werden, dass der Controllerpod ausgeführt wird:

```output
2018-11-15 15:50:50.0300 UTC | INFO | Controller pod is running.
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> Die vollständige Bereitstellung kann einige Zeit in Anspruch nehmen, da die Containerimages für die Komponenten des Big-Data-Clusters heruntergeladen werden müssen. Der Vorgang sollte jedoch nicht mehrere Stunden dauern. Wenn Probleme bei der Bereitstellung auftreten, finden Sie weitere Informationen unter [Überwachung und Problembehandlung: [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](cluster-troubleshooting-commands.md).

## <a name="inspect-the-cluster"></a>Überprüfen des Clusters

Sie können während der Bereitstellung jederzeit mit **kubectl** oder **azdata** den Status des ausgeführten Big-Data-Clusters überprüfen und sich Details anzeigen lassen.

### <a name="use-kubectl"></a>Verwenden von kubectl

Öffnen Sie ein neues Befehlsfenster, um **kubectl** während des Bereitstellungsprozesses zu verwenden.

1. Führen Sie den folgenden Befehl aus, um eine Zusammenfassung des Status für den gesamten Cluster abzurufen:

   ```
   kubectl get all -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie den Namen des Big-Data-Clusters nicht geändert haben, verwendet das Skript den Standardnamen **sqlbigdata**.

1. Überprüfen Sie die Kubernetes-Dienste und ihre internen und externen Endpunkte mit dem folgenden**kubectl**-Befehl:

   ```
   kubectl get svc -n <your-big-data-cluster-name>
   ```

1. Sie können den Status der Kubernetes-Pods auch mit dem folgenden Befehl überprüfen:

   ```
   kubectl get pods -n <your-big-data-cluster-name>
   ```

1. Weitere Informationen zu einem bestimmten Pod können Sie mit dem folgenden Befehl abrufen:

   ```
   kubectl describe pod <pod name> -n <your-big-data-cluster-name>
   ```

> [!TIP]
> Weitere Informationen zum Überwachen und Behandeln von Problemen einer Bereitstellung finden Sie unter [Überwachung und Problembehandlung: [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](cluster-troubleshooting-commands.md).

## <a name="connect-to-the-cluster"></a>Herstellen einer Verbindung mit dem Cluster

Nachdem das Bereitstellungsskript erfolgreich ausgeführt wurde, wird die folgende Meldung ausgegeben:

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

Der Big-Data-Cluster für SQL Server wurde in AKS bereitgestellt. Nun können Sie Azure Data Studio verwenden, um eine Verbindung mit dem Cluster herzustellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem Big-Data-Cluster für SQL Server mithilfe von Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="clean-up"></a>Bereinigung

Wenn Sie [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in Azure testen, sollten Sie abschließend den AKS-Cluster löschen, um unerwartete Gebühren zu vermeiden. Entfernen Sie den Cluster nicht, wenn Sie ihn weiterhin verwenden möchten.

> [!WARNING]
> Wenn Sie die folgenden Schritte ausführen, werden der AKS-Cluster und die Big-Data-Cluster für SQL Server gelöscht. Wenn Sie über Datenbanken oder HDFS-Daten verfügen, die Sie beibehalten möchten, müssen Sie diese Daten sichern, bevor Sie den Cluster löschen.

Führen Sie den folgenden Azure CLI-Befehl aus, um den Big-Data-Cluster und den AKS-Dienst in Azure zu entfernen. Ersetzen Sie dabei `<resource group name>` durch die **Azure-Ressourcengruppe**, die Sie im Bereitstellungsskript angegeben haben:

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>Nächste Schritte

Durch das Bereitstellungsskript wurden Azure Kubernetes Service konfiguriert und ein Big-Data-Cluster für SQL Server 2019 bereitgestellt. Sie können zukünftige Bereitstellungen auch mithilfe manueller Installationen anpassen. Weitere Informationen darüber, wie Sie Big Data-Cluster bereitstellen und Bereitstellungen anpassen, finden Sie unter [Bereitstellen von ](deployment-guidance.md) in Kubernetes[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)].

Da der Big-Data-Cluster für SQL Server bereitgestellt wurde, können Sie nun Beispieldaten auf diesen hochladen und sich die zugehörigen Tutorials ansehen:

> [!div class="nextstepaction"]
> [Tutorial: Hochladen von Beispieldaten auf einen Big-Data-Cluster für SQL Server 2019](tutorial-load-sample-data.md)
