---
title: Installieren von Big Data-Tools
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie die Tools installieren, die mit SQL Server 2019 Big Data Cluster (Vorschauversion) verwendet werden.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 757209ff89fd40dcc737b65d3b19f2a7d4ef247b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419455"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Installieren von SQL Server 2019 Big Data Tools

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel werden die Client Tools beschrieben, die zum Erstellen, verwalten und Verwenden von SQL Server 2019 Big Data Clustern (Vorschauversion) installiert werden müssen. Der folgende Abschnitt enthält eine Liste der Tools und Links zu Installationsanweisungen. Bevor Sie einen Big Data Cluster bereitstellen, konfigurieren Sie die Tools, die unter Windows oder Linux als erforderlich gekennzeichnet sind.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Big Data-Cluster Tools

In der folgenden Tabelle sind die allgemeinen Big Data Cluster Tools und deren Installation aufgeführt:

| Tool | Erforderlich | Beschreibung | Installation |
|---|---|---|---|
| **Thon** | Ja | Python ist eine interpretiertes, objektorientierte Programmiersprache auf hoher Ebene mit dynamischer Semantik. Viele Teile von Big Data Clustern für SQL Server python verwenden. | [Installieren von python](#python)|
| **azdata** | Ja | Befehlszeilen Tool für die Installation und Verwaltung eines Big Data Clusters. | [Installieren](deploy-install-azdata.md) |
| **kubectl** <sup>1</sup> | Ja | Befehlszeilen Tool zum Überwachen des zugrunde liegenden kuberentes-Clusters ([Weitere Informationen](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-native-package-management) |
| **Azure Data Studio (Insider)** | Ja | Plattformübergreifendes grafisches Tool zum Abfragen von SQL Server ([Weitere Informationen](https://docs.microsoft.com/sql/azure-data-studio/what-is?view=sql-server-ver15)). | [Installieren](https://aka.ms/azdata-insiders) |
| **SQL Server 2019-Erweiterung** | Ja | Erweiterung für Azure Data Studio, die das Herstellen einer Verbindung mit dem Big Data Cluster unterstützt. Bietet auch einen datenvirtualisierungsassistenten. | [Installieren](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI** <sup>2</sup> | Für AKS | Moderne Befehlszeilenschnittstelle zum Verwalten von Azure-Diensten. Wird mit AKS Big Data Cluster Bereitstellungen verwendet ([Weitere Informationen](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Installieren](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Optional | Moderne Befehlszeilenschnittstelle zum Abfragen von SQL Server ([Weitere Informationen](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Für einige Skripts | Legacy-Befehlszeilen Tool zum Abfragen von SQL Server ([Weitere Informationen](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Für einige Skripts | Befehlszeilen Tool zum Übertragen von Daten mit URLs. | [Windows](https://curl.haxx.se/windows/) \| Linux: curl-Paket installieren |

<sup>1</sup> Sie müssen die kubectl-Version 1,10 oder höher verwenden. Außerdem sollte die Version von kubectl Plus oder minus einer neben Version Ihres Kubernetes-Clusters sein. Wenn Sie eine bestimmte Version auf dem kubectl-Client installieren möchten, finden Sie weitere Informationen unter [Installieren von kubectl Binary via curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (unter Windows 10, verwenden von "cmd. exe" und nicht von Windows PowerShell zum Ausführen von curl). 

> [!TIP]
> Um kubectl mit einem bereits bereitgestellten Cluster in Azure Kubernetes Service (AKS) zu verwenden, müssen Sie den Cluster Kontext mit dem folgenden Azure CLI Befehl festlegen:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Sie müssen Azure CLI Version 2.0.4 oder höher verwenden. Führen `az --version` Sie aus, um die Version bei Bedarf zu ermitteln.

<sup>3</sup> Wenn Sie unter Windows 10 ausführen, befindet sich **curl** bereits in Ihrem Pfad, wenn Sie von einer cmd-Eingabeaufforderung ausführen. Für andere Versionen von Windows können Sie **curl** mithilfe des Links herunterladen und in Ihrem Pfad platzieren.

## <a name="which-tools-are-required"></a>Welche Tools sind erforderlich?

Die vorherige Tabelle enthält alle gängigen Tools, die mit Big Data Clustern verwendet werden. Welche Tools erforderlich sind, hängt von Ihrem Szenario ab. Im Allgemeinen sind die folgenden Tools für das Verwalten, verbinden mit und Abfragen des Clusters besonders wichtig:

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **SQL Server 2019-Erweiterung**

Die verbleibenden Tools sind nur in bestimmten Szenarien erforderlich. **Azure CLI** können zum Verwalten von Azure-Diensten verwendet werden, die mit AKS-bereit Stellungen verknüpft sind. **MSSQL-CLI** ist ein optionales, aber nützliches Tool, das es Ihnen ermöglicht, eine Verbindung mit der SQL Server Master Instanz im Cluster herzustellen und Abfragen von der Befehlszeile aus auszuführen. Und **sqlcmd** und **curl** sind erforderlich, wenn Sie die Installation von Beispiel Daten mit dem GitHub-Skript planen.

### <a id="python"></a>Python Offline installieren

1. Laden Sie auf einem Computer mit Internet Zugriff eine der folgenden komprimierten Dateien herunter, die python enthalten:

   | Betriebssystem | Herunterladen |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Kopieren Sie die komprimierte Datei auf den Zielcomputer, und extrahieren Sie Sie in einen Ordner Ihrer Wahl.

1. Führen `installLocalPythonPackages.bat` Sie in diesem Ordner nur für Windows aus, und übergeben Sie den vollständigen Pfad an denselben Ordner wie einen-Parameter.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="next-steps"></a>Nächste Schritte

Stellen Sie nach dem Konfigurieren der Tools einen SQL Server 2019 Big Data-Cluster in der Cloud oder lokal bereit. Weitere Informationen finden Sie in den folgenden Bereitstellungs Artikeln:

- [Schnellstart: Bereitstellen von SQL Server Big Data-Cluster in Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
- [Bereitstellen von SQL Server Big Data Clustern auf Kubernetes](deployment-guidance.md)

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md).
