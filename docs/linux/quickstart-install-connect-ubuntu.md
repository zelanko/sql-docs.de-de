---
title: Erste Schritte mit SQL Server unter Ubuntu
titleSuffix: SQL Server
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie SQL Server 2017 oder SQL Server 2019 unter Ubuntu installieren und anschließend mit sqlcmd eine Datenbank erstellen und abfragen.
author: VanMSFT
ms.author: vanto
ms.date: 05/28/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sqlfreshmay19
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: e21761c221ec83770be7c9aa19f8a4ec971617e2
ms.sourcegitcommit: 823d7bdfa01beee3cf984749a8c17888d4c04964
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2019
ms.locfileid: "70030316"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Schnellstart: Installieren von SQL Server und Erstellen einer Datenbank unter Ubuntu
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]


<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In dieser Schnellstartanleitung installieren Sie SQL Server 2017 oder SQL Server 2019 (Vorschau) unter Ubuntu 16.04. Danach stellen Sie eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In dieser Schnellstartanleitung installieren Sie SQL Server 2019 (Vorschau) unter Ubuntu 16.04. Danach stellen Sie eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

::: moniker-end

> [!TIP]
> Für dieses Tutorial sind Benutzereingaben und eine Internetverbindung erforderlich. Wenn Sie am unbeaufsichtigten oder am Offline-Installationsverfahren interessiert sind, finden Sie weitere Informationen im [Leitfaden für die Installation von SQL Server für Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen über einen Ubuntu 16.04-Computer mit **mindestens 2 GB** Arbeitsspeicher verfügen.

Um Ubuntu 16.04 auf Ihrem eigenen Computer zu installieren, wechseln Sie zu [http://releases.ubuntu.com/xenial/](http://releases.ubuntu.com/xenial/). Sie können auch virtuelle Ubuntu-Computer in Azure erstellen. Weitere Informationen finden Sie unter [Erstellen und Verwalten virtueller Linux-Computer mit der Azure-Befehlszeilenschnittstelle](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> Zurzeit wird das [Windows-Subsystem für Linux](https://msdn.microsoft.com/commandline/wsl/about) für Windows 10 als Installationsziel nicht unterstützt.

Weitere Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server für Linux](sql-server-linux-setup.md#system).

> [!NOTE]
> Ubuntu 18.04 wird noch nicht offiziell unterstützt. SQL Server kann aber bereits ausgeführt werden, wenn [Änderungen](https://blogs.msdn.microsoft.com/sql_server_team/installing-sql-server-2017-for-linux-on-ubuntu-18-04-lts/) vorgenommen werden.

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installieren von SQL Server

Um SQL Server unter Ubuntu zu konfigurieren, führen Sie in einem Terminal die folgenden Befehle aus, die das Paket **mssql-server** installieren.

1. Importieren Sie die öffentlichen GPG-Schlüssel des Repositorys:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Registrieren Sie das Microsoft SQL Server Ubuntu-Repository:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!TIP]
   > Wenn Sie SQL Server 2019 testen möchten, müssen Sie stattdessen das Repository **Preview (2019)** registrieren. Verwenden Sie für Installationen von SQL Server 2019 den folgenden Befehl:
   >
   > ```bash
   > sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
   > ```

3. Führen Sie die folgenden Befehle aus, um SQL Server zu installieren:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Nachdem die Paketinstallation abgeschlossen ist, führen Sie **mssql-conf setup** aus, und befolgen Sie die Anweisungen, um das Systemadministratorkennwort festzulegen und Ihre Edition auszuwählen.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Für die folgenden SQL Server 2017-Editionen sind kostenlose Lizenzen verfügbar: Evaluation, Developer und Express.

   > [!NOTE]
   > Stellen Sie sicher, dass Sie ein sicheres Kennwort für das Systemadministratorkonto angeben (minimale Länge von 8 Zeichen, Groß-und Kleinbuchstaben, Ziffern und/oder nicht-alphanumerische Symbole).

5. Nachdem die Konfiguration abgeschlossen ist, überprüfen Sie, ob der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. Wenn Sie eine Remoteverbindung planen, müssen Sie möglicherweise auch den SQL Server-TCP-Port (standardmäßig 1433) in Ihrer Firewall öffnen.

Jetzt wird SQL Server auf Ihrem Ubuntu-Computer ausgeführt und ist einsatzbereit!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installieren von SQL Server

Um SQL Server unter Ubuntu zu konfigurieren, führen Sie in einem Terminal die folgenden Befehle aus, die das Paket **mssql-server** installieren.

1. Importieren Sie die öffentlichen GPG-Schlüssel des Repositorys:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Registrieren Sie das Microsoft SQL Server Ubuntu-Repository für SQL Server 2019 (Vorschau):

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
   ```

3. Führen Sie die folgenden Befehle aus, um SQL Server zu installieren:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Nachdem die Paketinstallation abgeschlossen ist, führen Sie **mssql-conf setup** aus, und befolgen Sie die Anweisungen, um das Systemadministratorkennwort festzulegen und Ihre Edition auszuwählen.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Stellen Sie sicher, dass Sie ein sicheres Kennwort für das Systemadministratorkonto angeben (minimale Länge von 8 Zeichen, Groß-und Kleinbuchstaben, Ziffern und/oder nicht-alphanumerische Symbole).

5. Nachdem die Konfiguration abgeschlossen ist, überprüfen Sie, ob der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server --no-pager
   ```

6. Wenn Sie eine Remoteverbindung planen, müssen Sie möglicherweise auch den SQL Server-TCP-Port (standardmäßig 1433) in Ihrer Firewall öffnen.

Jetzt wird SQL Server 2019 auf Ihrem Ubuntu-Computer ausgeführt und ist einsatzbereit!

::: moniker-end

## <a id="tools"></a>Installieren der SQL Server-Befehlszeilentools

Um eine Datenbank zu erstellen, müssen Sie eine Verbindung mit einem Tool herstellen, das Transact-SQL-Anweisungen auf dem SQL Server-Computer ausführen kann. Mit den folgenden Schritten installieren Sie die SQL Server-Befehlszeilentools: [sqlcmd](../tools/sqlcmd-utility.md) und [bcp](../tools/bcp-utility.md).

Führen Sie zum Installieren von **mssql-tools** unter Ubuntu die folgenden Schritte aus. 

1. Importieren Sie die öffentlichen GPG-Schlüssel des Repositorys.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrieren Sie das Microsoft Ubuntu-Repository.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Aktualisieren Sie die Liste mit Quellen, und führen Sie den Installationsbefehl mit dem unixODBC-Entwicklerpaket aus.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Führen Sie die folgenden Befehle aus, um **mssql-tools** auf die neueste Version zu aktualisieren:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Optional**: Fügen Sie in einer Bash-Shell `/opt/mssql-tools/bin/` zu Ihrer **PATH**-Umgebungsvariablen hinzu.

   Ändern Sie **PATH** in der Datei **~/.bash_profile** mit dem folgenden Befehl, um **sqlcmd/bcp** von der Bash-Shell aus für Anmeldesitzungen zugänglich zu machen:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Ändern Sie **PATH** in der Datei **~/.bashrc** mit dem folgenden Befehl, um **sqlcmd/bcp** von der Bash-Shell aus für interaktive Sitzungen oder Sitzungen ohne Anmeldung zugänglich zu machen:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
