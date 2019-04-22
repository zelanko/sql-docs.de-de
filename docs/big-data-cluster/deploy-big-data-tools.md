---
title: Installieren von Big Data-Tools
titleSuffix: SQL Server big data clusters
description: Informationen Sie zum Installieren von Tools, die mit SQL Server-2019 big Data-Clustern (Vorschau) verwendet.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/17/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: dc53bdfb71efeafd55752686ff136355bc79bd34
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "58860481"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Installieren von SQL Server-2019 big datatools

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, die Clienttools, die zum Erstellen, verwalten, installiert werden soll, und Verwenden von SQL Server-2019 big Data-Cluster (Vorschau). Der folgende Abschnitt enthält eine Liste der Tools und Links zu Anweisungen zur Installation. Konfigurieren Sie vor der Bereitstellung von big Data-Cluster aus, die Tools, die gekennzeichnet werden, erforderlich für Windows oder Linux aus.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Big Data-Cluster-tools

Die folgende Tabelle enthält allgemeine big Data-Cluster-Tools und deren Installation:

| Tool | Erforderlich | Description | Installation |
|---|---|---|---|
| **mssqlctl** | Ja | Befehlszeilenprogramm zum Installieren und Verwalten von big Data-Cluster. | [Installieren](deploy-install-mssqlctl.md) |
| **kubectl**<sup>1</sup> | Ja | Befehlszeilentool für die Überwachung der zugrunde liegenden Clusters Kuberentes ([Informationen](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio** | Ja | Plattformübergreifende grafisches Tool zum Abfragen von SQL Server ([Informationen](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Installieren](../azure-data-studio/download.md) |
| **SQL Server-2019-Erweiterung** | Ja | Erweiterung für Azure Data Studio, das die Verbindung mit dem big Data-Cluster unterstützt. Stellt auch einen Assistenten Datenvirtualisierung bereit. | [Installieren](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure-Befehlszeilenschnittstelle**<sup>2</sup> | Für AKS | Moderne Befehlszeilenschnittstelle zum Verwalten von Azure-Dienste. Mit AKS big Data-Cluster-Bereitstellungen verwendet ([Informationen](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Installieren](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Optional | Moderne Befehlszeilenschnittstelle zum Abfragen von SQL Server ([Informationen](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Für einige Skripts | Legacy-Befehlszeilentool für Abfragen von SQL Server ([Informationen](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Für einige Skripts | Befehlszeilenprogramm zum Übertragen von Daten mit URLs. | [Windows](https://curl.haxx.se/windows/) \| Linux: Curl-Installationspaket |

<sup>1</sup> müssen Sie "kubectl", Version 1,10 oder höher verwenden. Darüber hinaus muss die Version des "kubectl" plus oder minus ein Nebenversion des Kubernetes-Clusters. Wenn Sie eine bestimmte Version auf "kubectl"-Client installieren möchten, finden Sie unter [Installieren von Kubectl über Curl binäre](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (unter Windows 10 verwenden cmd.exe und nicht die Windows PowerShell zum Ausführen von Curl). 

> [!TIP]
> Um "kubectl" mit einem bereits bereitgestellten Cluster auf Azure Kubernetes Service (AKS) verwenden zu können, müssen Sie den Clusterkontext mit dem folgenden Azure CLI-Befehl festlegen:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> müssen verwenden Sie Azure CLI-Version 2.0.4 oder höher. Führen Sie `az --version` auf die Version zu ermitteln, bei Bedarf.

<sup>3</sup> , wenn Sie auf Windows 10 ausführen **curl** ist bereits in Ihrem Pfad, wenn von einer Cmd-Eingabeaufforderung ausgeführt wird. Laden Sie für andere Versionen von Windows, **curl** verwenden Sie den Link, und platzieren Sie sie in Ihrem Pfad befindet.

## <a name="which-tools-are-required"></a>Welche Tools sind erforderlich?

Die vorherige Tabelle enthält alle allgemeinen Tools, die mit big Data-Cluster verwendet werden. Welche Tools erforderlich sind, hängt von Ihrem Szenario ab. Aber im Allgemeinen sind die folgenden Tools zum Verwalten, Herstellen einer Verbindung mit und Abfragen der wichtigsten:

- **mssqlctl**
- **kubectl**
- **Azure Data Studio**
- **SQL Server-2019-Erweiterung**

Die übrigen Tools sind nur in bestimmten Szenarien erforderlich. **Azure-Befehlszeilenschnittstelle** kann zum Verwalten von Azure-Dienste im Zusammenhang mit AKS-Bereitstellungen verwendet werden. **MSSQL-Cli** ist ein Tool, optional, aber hilfreich, mit dem Sie SQL Server-Instanz master im Cluster herstellen und Abfragen von der Befehlszeile aus ausführen. Und **Sqlcmd** und **curl** sind erforderlich, wenn Sie Daten mit dem GitHub-Skript installieren möchten.

## <a name="next-steps"></a>Nächste Schritte

Nach dem Konfigurieren der Tools, stellen Sie einen SQL Server-2019 big Data-Cluster für Kubernetes in der Cloud oder lokal bereit. Weitere Informationen finden Sie unter den folgenden bereitstellungsartikeln:

- [Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
- [Wie Sie SQL Server-big Data-Cluster in Kubernetes bereitstellen](deployment-guidance.md)

Weitere Informationen über big Data-Cluster finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
