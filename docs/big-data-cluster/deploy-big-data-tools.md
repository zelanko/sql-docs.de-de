---
title: Installieren von Big Data-Tools
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie die Tools installieren, die mit Big Data-Clustern unter SQL Server 2019 verwendet werden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e6571c92f68412a464b96964be4b02d22a106a0b
ms.sourcegitcommit: 3bd188e652102f3703812af53ba877cce94b44a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97489700"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Installieren von Big Data-Tools für SQL Server 2019

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel werden die Clienttools beschrieben, die zum Erstellen, Verwalten und Verwenden von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] installiert werden müssen. Der folgende Abschnitt enthält eine Liste der Tools und Links zu Installationsanweisungen. Bevor Sie einen Big Data-Cluster bereitstellen, konfigurieren Sie die Tools, die unter Windows oder Linux als erforderlich gekennzeichnet sind.

## <a name="big-data-cluster-tools"></a>Big Data-Cluster-Tools

In der folgenden Tabelle sind die allgemeinen Big Data-Cluster-Tools und deren Installation aufgeführt:

| Tool | Erforderlich | BESCHREIBUNG | Installation |
|---|---|---|---|
| `python` | Ja | Python ist eine interpretierte, objektorientierte Programmiersprache auf hoher Ebene mit dynamischer Semantik. Viele Teile von Big Data-Clustern für SQL Server verwenden Python. | [Installieren von Python](#python)|
| [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)] | Ja | Befehlszeilentool für die Installation und Verwaltung eines Big Data-Clusters. | [Installieren](../azdata/install/deploy-install-azdata.md) |
| `kubectl`<sup>1</sup> | Ja | Befehlszeilentool zum Überwachen des zugrunde liegenden Kubernetes-Clusters ([Weitere Informationen](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-using-native-package-management) |
| **Azure Data Studio** | Ja | Plattformübergreifendes grafisches Tool zum Abfragen von SQL Server. | [Installieren](../azure-data-studio/download-azure-data-studio.md) |
| **Datenvirtualisierungserweiterung** | Ja | Erweiterung für Azure Data Studio, die einen Datenvirtualisierungs-Assistenten bereitstellt. | [Installieren](../azure-data-studio/extensions/data-virtualization-extension.md) |
| **Azure CLI**<sup>2</sup> | Für AKS | Moderne Befehlszeilenschnittstelle zum Verwalten von Azure-Diensten. Wird mit AKS-Big Data-Cluster-Bereitstellungen verwendet ([Weitere Informationen](/cli/azure/)). | [Installieren](/cli/azure/install-azure-cli) |
| **mssql-cli** | Optional | Moderne Befehlszeilenschnittstelle zum Abfragen von SQL Server ([Weitere Informationen](../tools/mssql-cli.md)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Für einige Skripts | Legacybefehlszeilentool zum Abfragen von SQL Server ([Weitere Informationen](../tools/sqlcmd-utility.md)). Möglicherweise müssen Sie Microsoft ODBC Driver 11 für SQL Server installieren, bevor Sie das SQLCMD-Paket installieren. | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| `curl` <sup>3</sup> | Für einige Skripts | Befehlszeilentool zum Übertragen von Daten mit URLs. | [Windows](https://curl.haxx.se/windows/) \| Linux: Installieren von curl-Paket |
| `oc` | Für Red Hat OpenShift- und Azure Red Hat OpenShift-Bereitstellungen erforderlich |`oc` ist die OpenShift-Befehlszeilenschnittstelle. | [Installing the CLI](https://docs.openshift.com/container-platform/4.4/cli_reference/openshift_cli/getting-started-cli.html#installing-the-cli) (Installieren der Befehlszeilenschnittstelle)

<sup>1</sup> Sie müssen die `kubectl`-Version 1.13 oder höher verwenden. Außerdem sollte die Version von `kubectl` um eins höher oder niedriger als die Nebenversion Ihres Kubernetes-Clusters sein. Wenn Sie eine bestimmte Version auf dem `kubectl`-Client installieren möchten, finden Sie weitere Informationen unter [Installieren von `kubectl` mit curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (Verwenden Sie unter Windows 10 cmd.exe und nicht Windows PowerShell zum Ausführen von curl).

> [!TIP]
> Sie müssen den Clusterkontext mit dem folgenden Azure CLI-Befehl festlegen, um `kubectl` mit einem bereits bereitgestellten Cluster in Azure Kubernetes Service (AKS) zu verwenden:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Sie müssen die Azure CLI-Version 2.0.4 oder höher verwenden. Führen Sie bei Bedarf `az --version` aus, um die Version zu ermitteln.

<sup>3</sup> Bei Ausführung unter Windows 10 befindet sich `curl` bereits in Ihrem PATH, wenn Sie zur Ausführung eine Befehlseingabeaufforderung verwenden. Laden Sie für andere Versionen von Windows `curl` mithilfe des Links herunter, und platzieren Sie curl in Ihrem PATH.

## <a name="which-tools-are-required"></a>Welche Tools sind erforderlich?

Die vorherige Tabelle enthält alle gängigen Tools, die mit Big Data-Clustern verwendet werden. Welche Tools erforderlich sind, hängt von Ihrem Szenario ab. Im Allgemeinen sind die folgenden Tools besonders wichtig, um den Cluster zu verwalten, eine Verbindung mit ihm herzustellen und ihn abzufragen:

- [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)]
- `kubectl`
- **Azure Data Studio**
- **Datenvirtualisierungserweiterung**

Die verbleibenden Tools sind nur in bestimmten Szenarien erforderlich. **Azure CLI** kann zum Verwalten von Azure-Diensten verwendet werden, die mit AKS-Bereitstellungen verknüpft sind. **mssql-cli** ist ein optionales, aber nützliches Tool, das Ihnen ermöglicht, eine Verbindung mit der SQL Server-Masterinstanz im Cluster herzustellen und Abfragen von der Befehlszeile aus auszuführen. **sqlcmd** und `curl` sind erforderlich, wenn Sie die Installation von Beispieldaten mit dem GitHub-Skript planen.

### <a name="install-python-offline"></a><a id="python"></a> Offlineinstallation von Python

1. Laden Sie auf einem Computer mit Internetzugriff eine der folgenden komprimierten Dateien herunter, die Python enthalten:

   | Betriebssystem | Download |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Kopieren Sie die komprimierte Datei auf den Zielcomputer, und extrahieren Sie sie in einen Ordner Ihrer Wahl.

1. Führen Sie `installLocalPythonPackages.bat` nur unter Windows in diesem Ordner aus, und übergeben Sie den vollständigen Pfad zu demselben Ordner als Parameter.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="download-and-install-azure-data-studio"></a>Herunterladen und Installieren von Azure Data Studio

Azure Data Studio bietet Funktionen und Features speziell für SQL Server-Big Data-Cluster.

[Erwerben Sie die neueste Version von Azure Data Studio](../azure-data-studio/download-azure-data-studio.md).

Weitere Informationen über die neueste Version finden Sie in den [Versionshinweisen](./release-notes-big-data-cluster.md).

## <a name="next-steps"></a>Nächste Schritte

Stellen Sie nach dem Konfigurieren der Tools einen SQL Server 2019-Big Data-Cluster in der Cloud oder lokal für Kubernetes bereit. Weitere Informationen finden Sie in den folgenden Bereitstellungsartikeln:

- [Schnellstart: Verwenden eines Python-Skripts zum Bereitstellen eines SQL Server-Big Data-Clusters unter Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
- [Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in Kubernetes](deployment-guidance.md)

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)