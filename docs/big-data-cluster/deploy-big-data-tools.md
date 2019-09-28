---
title: Installieren von Big Data-Tools
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie die mit [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Vorschau) verwendeten Tools installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: cbb34d5cd209281a5c97d819c7741503d234ad2d
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342023"
---
# <a name="install-sql-server-2019-big-data-tools"></a>Installieren von Big Data-Tools für SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel werden die Client Tools beschrieben, die zum Erstellen, verwalten und Verwenden von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Vorschau) installiert werden müssen. Der folgende Abschnitt enthält eine Liste der Tools und Links zu Installationsanweisungen. Bevor Sie einen Big Data-Cluster bereitstellen, konfigurieren Sie die Tools, die unter Windows oder Linux als erforderlich gekennzeichnet sind.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="big-data-cluster-tools"></a>Big Data-Cluster-Tools

In der folgenden Tabelle sind die allgemeinen Big Data-Cluster-Tools und deren Installation aufgeführt:

| Tool | Erforderlich | Beschreibung | Installation |
|---|---|---|---|
| **Python** | Ja | Python ist eine interpretierte, objektorientierte Programmiersprache auf hoher Ebene mit dynamischer Semantik. Viele Teile von Big Data-Clustern für SQL Server verwenden Python. | [Installieren von Python](#python)|
| **azdata** | Ja | Befehlszeilentool für die Installation und Verwaltung eines Big Data-Clusters. | [Installieren](deploy-install-azdata.md) |
| **kubectl**<sup>1</sup> | Ja | Befehlszeilentool zum Überwachen des zugrunde liegenden Kubernetes-Clusters ([Weitere Informationen](https://kubernetes.io/docs/tasks/tools/install-kubectl/)). | [Windows](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery) \| [Linux](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-using-native-package-management) |
| **Azure Data Studio-SQL Server 2019 Release Candidate (RC)** | Ja | Plattformübergreifendes grafisches Tool zum Abfragen von SQL Server. | [Installieren](#download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc) |
| **Erweiterung von SQL Server 2019** | Ja | Erweiterung für Azure Data Studio, die das Herstellen einer Verbindung mit dem Big Data-Cluster unterstützt. Bietet auch einen Datenvirtualisierungs-Assistenten. | [Installieren](../azure-data-studio/sql-server-2019-extension.md) |
| **Azure CLI**<sup>2</sup> | Für AKS | Moderne Befehlszeilenschnittstelle zum Verwalten von Azure-Diensten. Wird mit AKS-Big Data-Cluster-Bereitstellungen verwendet ([Weitere Informationen](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)). | [Installieren](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) |
| **mssql-cli** | Optional | Moderne Befehlszeilenschnittstelle zum Abfragen von SQL Server ([Weitere Informationen](https://github.com/dbcli/mssql-cli/blob/master/README.rst)). | [Windows](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/windows.md) \| [Linux](https://github.com/dbcli/mssql-cli/blob/master/doc/installation/linux.md) |
| **sqlcmd** | Für einige Skripts | Legacybefehlszeilentool zum Abfragen von SQL Server ([Weitere Informationen](https://docs.microsoft.com/sql/tools/sqlcmd-utility?view=sql-server-ver15)). | [Windows](https://www.microsoft.com/download/details.aspx?id=36433) \| [Linux](../linux/sql-server-linux-setup-tools.md) |
| **curl** <sup>3</sup> | Für einige Skripts | Befehlszeilentool zum Übertragen von Daten mit URLs. | [Windows](https://curl.haxx.se/windows/) \| Linux: curl-Paket installieren |

<sup>1</sup> Sie müssen die kubectl-Version 1,13 oder höher verwenden. Außerdem sollte die Version von kubectl um eins höher oder niedriger als die Nebenversion Ihres Kubernetes-Clusters sein. Wenn Sie eine bestimmte Version auf dem kubectl-Client installieren möchten, finden Sie weitere Informationen unter [Install and Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-binary-using-curl) (Installieren und Einrichten von kubectl). Verwenden Sie unter Windows 10 „cmd.exe“ und nicht Windows PowerShell zum Ausführen von curl.

> [!TIP]
> Um kubectl mit einem bereits bereitgestellten Cluster in Azure Kubernetes Service (AKS) zu verwenden, müssen Sie den Clusterkontext mit dem folgenden Azure CLI-Befehl festlegen:
>
>    ```azurecli
>    az aks get-credentials --name <aks_cluster_name> --resource-group <azure_resource_group_name>
>    ```

<sup>2</sup> Sie müssen die Azure CLI-Version 2.0.4 oder höher verwenden. Führen Sie bei Bedarf `az --version` aus, um die Version zu ermitteln.

<sup>3</sup> Bei Ausführung unter Windows 10 befindet **curl** sich bereits in Ihrem PATH, wenn Sie zur Ausführung eine Befehlseingabeaufforderung verwenden. Laden Sie für andere Versionen von Windows **curl** mithilfe des Links herunter, und platzieren Sie curl in Ihrem PATH.

## <a name="which-tools-are-required"></a>Welche Tools sind erforderlich?

Die vorherige Tabelle enthält alle gängigen Tools, die mit Big Data-Clustern verwendet werden. Welche Tools erforderlich sind, hängt von Ihrem Szenario ab. Im Allgemeinen sind die folgenden Tools besonders wichtig, um den Cluster zu verwalten, eine Verbindung mit ihm herzustellen und ihn abzufragen:

- **azdata**
- **kubectl**
- **Azure Data Studio**
- **Erweiterung von SQL Server 2019**

Die verbleibenden Tools sind nur in bestimmten Szenarien erforderlich. **Azure CLI** kann zum Verwalten von Azure-Diensten verwendet werden, die mit AKS-Bereitstellungen verknüpft sind. **mssql-cli** ist ein optionales, aber nützliches Tool, das Ihnen ermöglicht, eine Verbindung mit der SQL Server-Masterinstanz im Cluster herzustellen und Abfragen von der Befehlszeile aus auszuführen. **sqlcmd** und **curl** sind erforderlich, wenn Sie die Installation von Beispieldaten mit dem GitHub-Skript planen.

### <a id="python"></a> Offlineinstallation von Python

1. Laden Sie auf einem Computer mit Internetzugriff eine der folgenden komprimierten Dateien herunter, die Python enthalten:

   | Betriebssystem | Herunterladen |
   |---|---|
   | Windows | [https://go.microsoft.com/fwlink/?linkid=2074021](https://go.microsoft.com/fwlink/?linkid=2074021) |
   | Linux   | [https://go.microsoft.com/fwlink/?linkid=2065975](https://go.microsoft.com/fwlink/?linkid=2065975) |
   | OSX     | [https://go.microsoft.com/fwlink/?linkid=2065976](https://go.microsoft.com/fwlink/?linkid=2065976) |

1. Kopieren Sie die komprimierte Datei auf den Zielcomputer, und extrahieren Sie sie in einen Ordner Ihrer Wahl.

1. Führen Sie `installLocalPythonPackages.bat` nur unter Windows in diesem Ordner aus, und übergeben Sie den vollständigen Pfad zu demselben Ordner als Parameter.

   ```PowerShell
   installLocalPythonPackages.bat "C:\python-3.6.6-win-x64-0.0.1-offline\0.0.1"
   ```

## <a name="download-and-install-azure-data-studio-sql-server-2019-release-candidate-rc"></a>Herunterladen und Installieren von Azure Data Studio SQL Server 2019 Release Candidate (RC)

Azure Data Studio SQL Server 2019 RC bietet Funktionen und Features speziell für SQL Server 2019 RC.

Für normale Produktionsversionen von Azure Data Studio befolgen Sie die Anweisungen unter [herunterladen und Installieren von Azure Data Studio](../azure-data-studio/download.md).

|Platform|Herunterladen|Veröffentlichungsdatum| Version |
|:---|:---|:---|:---|
|Windows|[Benutzer-Installationsprogramm (empfohlen)](https://go.microsoft.com/fwlink/?linkid=2102435)<br>[System-Installationsprogramm](https://go.microsoft.com/fwlink/?linkid=2102523)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2102524)|27. August 2019 |RC 1.11.0-Insider|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2102436)|27. August 2019 |RC 1.11.0-Insider|
|Linux|[.deb](https://go.microsoft.com/fwlink/?linkid=2102526)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2102437)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2102525)|27. August 2019 |RC 1.11.0-Insider|

Weitere Informationen über die neueste Version finden Sie in den [Versionshinweisen](../big-data-cluster/release-notes-big-data-cluster.md).

### <a name="get-azure-data-studio-for-windows"></a>Azure Data Studio für Windows

Dieses Release von [!INCLUDE[name-sos](../includes/name-sos-short.md)] enthält das standardmäßige Windows-Installationsprogramm und eine ZIP-Datei.

Das *Benutzer-Installationsprogramm* wird empfohlen, da dafür keine Administratorrechte erforderlich sind, was Installation und Upgrades vereinfacht. Für das Benutzer-Installationsprogramm sind keine Administratorrechte erforderlich, da sich der Speicherort im lokalen Ordner „AppData“ (LOCALAPPDATA) des Benutzers befindet. Zudem bietet das Benutzer-Installationsprogramm eine einfachere Aktualisierung im Hintergrund. Weitere Informationen finden Sie unter [Benutzersetup für Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).

**Benutzer-Installationsprogramm** (empfohlen)

1. Laden Sie das [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-*Benutzer*-Installationsprogramm für Windows](https://go.microsoft.com/fwlink/?linkid=2102435) herunter, und führen Sie es aus.
2. Starten Sie die [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]-App.

**System-Installationsprogramm**

1. Laden Sie das [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-*System*-Installationsprogramm für Windows](https://go.microsoft.com/fwlink/?linkid=2102523) herunter, und führen Sie es aus.
2. Starten Sie die [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]-App.

**zip-Datei**

1. Laden Sie die [[!INCLUDE[name-sos](../includes/name-sos-short.md)]-ZIP-Datei für Windows](https://go.microsoft.com/fwlink/?linkid=2102524) herunter.
2. Navigieren Sie zur heruntergeladenen Datei, und extrahieren Sie sie.
3. Ausführen von `\azuredatastudio-windows\azuredatastudio.exe`

### <a name="get-azure-data-studio-for-macos"></a>Azure Data Studio für macOS

1. Laden Sie [[!INCLUDE[name-sos](../includes/name-sos-short.md)] für macOS](https://go.microsoft.com/fwlink/?linkid=2102436) herunter.
2. Doppelklicken Sie auf die ZIP-Datei, um die Inhalte zu erweitern.
3. Wenn Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] im *Launchpad* verfügbar machen wollen, können Sie *Azure Data Studio.app* in den Ordner *Programme* ziehen.

### <a name="get-azure-data-studio-for-linux"></a>Azure Data Studio für Linux

1. Laden Sie [!INCLUDE[name-sos](../includes/name-sos-short.md)] für Linux herunter, indem Sie eines der Installationsprogramme oder das Archiv „tar.gz“ verwenden:
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2102526)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2102437)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2102525)
1. Öffnen Sie ein neues Terminalfenster, und geben Sie die folgenden Befehle ein, um die Datei zu extrahieren und [!INCLUDE[name-sos](../includes/name-sos-short.md)] zu starten:

   **Debian-Installation:**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **rpm-Installation:**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **.tar.gz Installation:**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Bei Debian, Red hat und Ubuntu fehlen möglicherweise Abhängigkeiten. Verwenden Sie die folgenden Befehle, um diese Abhängigkeiten je nach Ihrer Linux-Version zu installieren:
   

   **Debian:** 
   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat:** 
   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu:** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```

### <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

[!INCLUDE[name-sos](../includes/name-sos-short.md)] kann unter Windows, macOS und Linux ausgeführt werden und wird auf den folgenden Plattformen unterstützt:

#### <a name="windows"></a>Windows

- Windows 10 (64-Bit)
- Windows 8.1 (64-Bit)
- Windows 8 (64-Bit)
- Windows 7 (SP1) (64-Bit) – Erfordert [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2 (64-Bit)
- Windows Server 2012 (64-Bit)
- Windows Server 2008 R2 (64-Bit)

#### <a name="macos"></a>macOS

- macOS 10.13 High Sierra
- macOS 10.12 Sierra

#### <a name="linux"></a>Linux

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="next-steps"></a>Nächste Schritte

Stellen Sie nach dem Konfigurieren der Tools einen SQL Server 2019-Big Data-Cluster in der Cloud oder lokal für Kubernetes bereit. Weitere Informationen finden Sie in den folgenden Bereitstellungsartikeln:

- [Schnellstart: Verwenden eines Python-Skripts zum Bereitstellen eines SQL Server-Big Data-Clusters unter Azure Kubernetes Service (AKS)](quickstart-big-data-cluster-deploy.md)
- [Bereitstellen auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Kubernetes](deployment-guidance.md)

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
