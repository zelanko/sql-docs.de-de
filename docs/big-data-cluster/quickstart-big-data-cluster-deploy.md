---
title: Bereitstellungsskript
titleSuffix: SQL Server big data clusters
description: Exemplarische Vorgehensweise eine Bereitstellung von SQL Server-2019 big Data-Cluster (Vorschau) in Azure Kubernetes Service (AKS).
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0254b76b0845ff5f913d2d0ab69324ddd0072923
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728773"
---
# <a name="deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Bereitstellen von SQL Server-big Data-Cluster in Azure Kubernetes Service (AKS)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial verwenden Sie ein Beispielskript für die Bereitstellung, um die SQL Server-2019 big Data-Cluster (Vorschau) zu Azure Kubernetes Service (AKS) bereitstellen. 

> [!TIP]
> ACS ist nur eine Option für das Hosten von Kubernetes für Ihre big Data-Cluster. Weitere Informationen zu anderen Bereitstellungsoptionen sowie wie die Optionen zum Anpassen der Bereitstellung finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md).

Die hier verwendete Standard big Data-Clusterbereitstellung besteht aus einer Instanz von SQL Master, einer Compute-poolinstanz, zwei Daten ressourcenpoolvorlage ressourcenpoolinstanzen und zwei Instanzen von Speicher-Pool. Daten werden beibehalten, über persistente Kubernetes-Volumes, die Speicher-Standardklassen AKS verwenden. Die Standardkonfiguration, die in diesem Tutorial verwendete eignet sich für Entwicklungs-/testumgebungen.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Vorraussetzungen

- Ein Azure-Abonnement.
- [Big Data-Tools](deploy-big-data-tools.md):
   - **mssqlctl**
   - **kubectl**
   - **Azure Data Studio**
   - **SQL Server-2019-Erweiterung**
   - **Azure-Befehlszeilenschnittstelle**

## <a name="log-in-to-your-azure-account"></a>Melden Sie sich bei Ihrem Azure-Konto

Das Skript verwendet die Azure-Befehlszeilenschnittstelle zum Automatisieren der Erstellung eines AKS-Clusters. Vor dem Ausführen des Skripts müssen Sie beim Azure-Konto mit Azure-Befehlszeilenschnittstelle mindestens einmal anmelden. Führen Sie den folgenden Befehl an einer Eingabeaufforderung aus.

```
az login
```

## <a name="download-the-deployment-script"></a>Laden Sie das Bereitstellungsskript

In diesem Tutorial wird die Erstellung der big Data-Cluster in AKS über ein Python-Skript automatisiert **bereitstellen – Sql-big-Data-aks.py**. Wenn Sie Python für bereits installiert **Mssqlctl**, Sie muss das Skript erfolgreich in diesem Tutorial ausführen können. 

Führen Sie in einer Windows PowerShell oder Linux-Bash-Eingabeaufforderung den folgenden Befehl aus, um das Bereitstellungsskript von GitHub herunterladen.

```
curl -o deploy-sql-big-data-aks.py "https://raw.githubusercontent.com/Microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/aks/deploy-sql-big-data-aks.py"
```

## <a name="run-the-deployment-script"></a>Ausführen des Bereitstellungsskripts

Verwenden Sie die folgenden Schritte aus, um das Ausführen des Bereitstellungsskripts. Dieses Skript ein AKS-Diensts in Azure erstellen und dann einen SQL Server-2019 big Data-Cluster in AKS bereitstellen. Sie können auch ändern, das Skript mit anderen [Umgebungsvariablen](deployment-guidance.md#configfile) zum Erstellen einer benutzerdefinierten Bereitstellung.

1. Führen Sie das Skript mit dem folgenden Befehl ein:

   ```
   python deploy-sql-big-data-aks.py
   ```

   > [!NOTE]
   > Wenn Sie sowohl für python3 python2 auf dem Client und im Pfad haben, müssen Sie python3 über den Befehl ausführen: `python3 deploy-sql-big-data-aks.py`.

1. Wenn Sie aufgefordert werden, geben Sie die folgenden Informationen an:

   | Wert | Beschreibung |
   |---|---|
   | **Azure-Abonnement-ID** | Die Azure-Abonnement-ID, der für AKS verwendet werden soll. Sie können alle Ihre Abonnements und die dazugehörigen IDs auflisten, indem Sie Ausführung `az account list` in einer anderen Befehlszeile. |
   | **Azure-Ressourcengruppe** | Der Gruppenname des Azure-Ressource für die AKS-Cluster zu erstellen. |
   | **Docker-Benutzername** | Der Docker-Benutzername, das Ihnen als Teil der begrenzten öffentlichen Vorschau bereitgestellt. |
   | **Docker-Kennwort** | Das Docker-Kennwort, das Ihnen als Teil der begrenzten öffentlichen Vorschau bereitgestellt. |
   | **Azure-region** | Der Azure-Region für den neuen AKS-Cluster (standardmäßig **Westus**). |
   | **VM-Größe** | Die [VM-Größe](https://docs.microsoft.com/azure/virtual-machines/windows/sizes) für Knoten im AKS-Cluster (standardmäßig **Standard_L8s**). |
   | **Workerknoten** | Die Anzahl der Worker-Knoten im AKS-Cluster (standardmäßig **1**). |
   | **Clustername** | Der Name des AKS-Clusters und der big Data-Cluster. Der Name des Ihrer big Data-Cluster muss nur alphanumerische Kleinbuchstaben und ohne Leerzeichen sein. (standardmäßig **Sqlbigdata**). |
   | **Kennwort** | Das Kennwort für den Controller, HDFS/Spark-Gateway und Masterinstanz (standardmäßig **MySQLBigData2019**). |
   | **Benutzerkonten** | Benutzername für den Controllerbenutzer (Standard: **Admin**). |

   > [!IMPORTANT]
   > Der Standardwert **Standard_L8s** Größe für den Computer möglicherweise nicht verfügbar in jeder Azure-Region. Wenn Sie eine andere computergröße auswählen, stellen Sie sicher, dass die Gesamtzahl von Datenträgern, die auf die Knoten im Cluster angefügt werden, kann größer als oder gleich 24. Jeder Anspruch persistentes Volume im Cluster erfordert einen angeschlossenen Datenträger. Big Data-Cluster erfordert derzeit 24 persistentes Volume Ansprüche. Z. B. die [Standard_L8s](https://docs.microsoft.com/azure/virtual-machines/windows/sizes-storage#lsv2-series) VM-Größe unterstützt 32 angefügte Datenträger aus, sodass Sie big Data-Cluster mit einem einzelnen Knoten der Größe des Computers bewerten können.

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
2018-11-15 15:50:50.0585 UTC | INFO | Controller Endpoint: https://111.111.111.111:30080
```

> [!IMPORTANT]
> Die gesamte Bereitstellung dauert sehr lange aufgrund der Zeitaufwand für die Container-Images für die Komponenten der big Data-Cluster herunterladen. Er sollte jedoch nicht mehrere Stunden dauern. Wenn Sie Probleme bei der Bereitstellung auftreten, finden Sie unter [Überwachung und Problembehandlung für SQL Server-big Data-Cluster](cluster-troubleshooting-commands.md).

## <a name="inspect-the-cluster"></a>Überprüfen Sie den cluster

Sie können jederzeit während der Bereitstellung verwenden **"kubectl"** oder **Mssqlctl** , den Status und die Details der Ausführung von big Data-Cluster zu überprüfen.

### <a name="use-kubectl"></a>Verwenden von kubectl

Öffnen Sie ein neues Befehlsfenster mit **"kubectl"** während der Bereitstellung.

1. Führen Sie den folgenden Befehl aus, um eine Zusammenfassung des Status des gesamten Clusters abzurufen:

   ```
   kubectl get all -n <your-big-data-cluster-name>
   ```

   > [!TIP]
   > Wenn Sie den Namen des big Data-Clusters nicht geändert haben, das Skript standardmäßig **Sqlbigdata**.

1. Überprüfen Sie die Kubernetes-Dienste und deren interne und externe Endpunkte mit den folgenden **"kubectl"** Befehl:

   ```
   kubectl get svc -n <your-big-data-cluster-name>
   ```

1. Sie können auch den Status der Kubernetes-Pods mithilfe des folgenden Befehls überprüfen:

   ```
   kubectl get pods -n <your-big-data-cluster-name>
   ```

1. Finden Sie weitere Informationen zu einem bestimmten Pod mit dem folgenden Befehl ein:

   ```
   kubectl describe pod <pod name> -n <your-big-data-cluster-name>
   ```

> [!TIP]
> Weitere Informationen zum Überwachen und Problembehandlung bei einer Bereitstellung finden Sie unter [Überwachung und Problembehandlung für SQL Server-big Data-Cluster](cluster-troubleshooting-commands.md).

## <a name="connect-to-the-cluster"></a>Verbinden mit dem cluster

Wenn das Bereitstellungsskript abgeschlossen ist, benachrichtigt die Ausgabe Sie Erfolg:

```output
2018-11-15 16:10:25.0583 UTC | INFO | Cluster state: Ready
2018-11-15 16:10:25.0583 UTC | INFO | Cluster deployed successfully.
```

Die SQL Server-big Data-Cluster wird nun in AKS bereitgestellt. Azure Data Studio können jetzt mit dem Cluster herstellen. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einer SQL Server big Data-cluster mit Azure Data Studio](connect-to-big-data-cluster.md).

## <a name="clean-up"></a>Bereinigen

Wenn Sie SQL Server-big Data-Cluster in Azure testen, sollten Sie die AKS-Cluster, Abschluss, um unerwartete Gebühren zu vermeiden löschen. Entfernen Sie den Cluster nicht, wenn Sie das Produkt weiterhin verwenden möchten.

> [!WARNING]
> Die folgenden Schritte aus, kurzzeitig von dem AKS-Cluster der SQL Server big Data-Cluster auch entfernt. Wenn Sie Datenbanken oder HDFS-Daten, die Sie beibehalten möchten, Sichern Sie die Daten vor dem Löschen des Clusters.

Führen Sie den folgenden Azure CLI-Befehl zum Entfernen der big Data-Cluster und AKS-Diensts in Azure (ersetzen Sie dies `<resource group name>` mit der **Azure-Ressourcengruppe** Sie im Bereitstellungsskript angegeben):

```azurecli
az group delete -n <resource group name>
```

## <a name="next-steps"></a>Nächste Schritte

Das Bereitstellungsskript konfiguriert Azure Kubernetes Service und auch einen SQL Server-2019 big Data-Cluster bereitgestellt. Sie können auch zukünftige Bereitstellungen über manuelle Agentinstallationen anpassen. Mehr wie big Data-Cluster sowie zum Anpassen von Bereitstellungen bereitgestellt sind, finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md).

Nun, dass der SQL Server-big Data-Cluster bereitgestellt wird, können Laden von Beispieldaten und die Tutorials erkunden:

> [!div class="nextstepaction"]
> [Tutorial: Laden Sie Beispieldaten in eine SQL Server-2019 big Data-cluster](tutorial-load-sample-data.md)