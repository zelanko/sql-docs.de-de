---
title: Erste Schritte mit SQL Server unter Ubuntu | Microsoft-Dokumentation
description: Dieser Schnellstart veranschaulicht das Installieren von SQL Server 2017 oder SQL Server-2019 unter Ubuntu und klicken Sie dann zu erstellen und Abfragen einer Datenbank mit Sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 0741669f8a35125ad1a7312c4a014f1fba0c291a
ms.sourcegitcommit: b7fd118a70a5da9bff25719a3d520ce993ea9def
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "46712332"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-ubuntu"></a>Schnellstart: Installieren von SQL Server, und erstellen Sie eine Datenbank unter Ubuntu

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In diesem Schnellstart installieren Sie SQL Server 2017 oder SQL Server 2019 CTP 2.0 auf Ubuntu 16.04. Verbinden Sie Sie dann mit **Sqlcmd** Erstellen Ihrer ersten Datenbank Abfragen und ausführen.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In diesem Schnellstart installieren Sie SQL Server 2019 CTP 2.0 auf Ubuntu 16.04 an. Verbinden Sie Sie dann mit **Sqlcmd** Erstellen Ihrer ersten Datenbank Abfragen und ausführen.

::: moniker-end

> [!TIP]
> Dieses Lernprogramm erfordert eine Benutzereingabe und eine Internetverbindung besteht. Wenn Sie möchten die [unbeaufsichtigte](sql-server-linux-setup.md#unattended) oder [offline](sql-server-linux-setup.md#offline) Installationsverfahren, finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie benötigen einen Ubuntu 16.04-Computer mit **mindestens 2 GB** des Arbeitsspeichers.

Um Ubuntu auf Ihrem eigenen Computer zu installieren, wechseln Sie zu [ http://www.ubuntu.com/download/server ](http://www.ubuntu.com/download/server). Sie können auch den virtuellen Ubuntu-Computern in Azure erstellen. Finden Sie unter [erstellen und Verwalten von Linux-VMs mit der Azure-Befehlszeilenschnittstelle](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm).

> [!NOTE]
> Zu diesem Zeitpunkt die [Windows-Subsystem für Linux](https://msdn.microsoft.com/commandline/wsl/about) für Windows 10 als ein Installationsziel wird nicht unterstützt.

Weitere Informationen zu den Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server unter Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installieren von SQLServer

Führen Sie die folgenden Befehle in einem Terminal zu installieren, um SQL Server unter Ubuntu konfigurieren zu können, die **Mssql-Server** Paket.

1. Importieren Sie die öffentlichen Repository GPG-Schlüssel:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Registrieren Sie das Microsoft SQL Server-Ubuntu-Repository:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"
   ```

   > [!TIP]
   > Wenn Sie SQL Server-2019 testen möchten, müssen Sie stattdessen Registrieren der **Preview (2019)** Repository. Verwenden Sie den folgenden Befehl für Installationen von SQL Server-2019:
   >
   > ```bash
   > sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
   > ```

3. Führen Sie die folgenden Befehle zum Installieren von SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Nach der Paket-Installation abgeschlossen ist, führen Sie **Mssql-Conf Setup** , und befolgen Sie die aufforderungen, um das SA-Kennwort festgelegt, und wählen Sie die Version.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Die folgenden Editionen von SQL Server 2017 kostenlos lizenziert sind: Evaluation, Developer und Express.

   > [!NOTE]
   > Stellen Sie sicher, dass ein sicheres Kennwort für das SA-Konto (minimale Länge von 8-Zeichen, wie z. B. Groß- und Kleinbuchstaben, Basis 10-Ziffern und/oder nicht-alphanumerischen Zeichen) an.

5. Nachdem die Konfiguration abgeschlossen ist, stellen Sie sicher, dass der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

6. Wenn Sie eine Remoteverbindung herstellen möchten, müssen Sie möglicherweise auch die SQL Server-TCP-Port (Standardport: 1433) in Ihrer Firewall öffnen.

An diesem Punkt wird SQL Server auf Ihrem Ubuntu-Computer ausgeführt wird, und ist einsatzbereit!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installieren von SQLServer

Führen Sie die folgenden Befehle in einem Terminal zu installieren, um SQL Server unter Ubuntu konfigurieren zu können, die **Mssql-Server** Paket.

1. Importieren Sie die öffentlichen Repository GPG-Schlüssel:

   ```bash
   wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. Das Microsoft SQL Server-Ubuntu-Repository für SQL Server-2019 Vorschau zu registrieren:

   ```bash
   sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
   ```

3. Führen Sie die folgenden Befehle zum Installieren von SQL Server:

   ```bash
   sudo apt-get update
   sudo apt-get install -y mssql-server
   ```

4. Nach der Paket-Installation abgeschlossen ist, führen Sie **Mssql-Conf Setup** , und befolgen Sie die aufforderungen, um das SA-Kennwort festgelegt, und wählen Sie die Version.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Stellen Sie sicher, dass ein sicheres Kennwort für das SA-Konto (minimale Länge von 8-Zeichen, wie z. B. Groß- und Kleinbuchstaben, Basis 10-Ziffern und/oder nicht-alphanumerischen Zeichen) an.

5. Nachdem die Konfiguration abgeschlossen ist, stellen Sie sicher, dass der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

6. Wenn Sie eine Remoteverbindung herstellen möchten, müssen Sie möglicherweise auch die SQL Server-TCP-Port (Standardport: 1433) in Ihrer Firewall öffnen.

An diesem Punkt wird SQL Server 2019 CTP 2.0 auf Ihrem Ubuntu-Computer ausgeführt wird, und ist einsatzbereit!

::: moniker-end

## <a id="tools"></a>Installieren der SQL Server-Befehlszeilentools

Um eine Datenbank erstellen zu können, müssen Sie die Verbindung mit einem Tool, das auf dem SQL Server Transact-SQL-Anweisungen ausgeführt werden kann. Die folgenden Schritte aus, Installieren der SQL Server-Befehlszeilentools: [Sqlcmd](../tools/sqlcmd-utility.md) und [Bcp](../tools/bcp-utility.md).

Verwenden Sie die folgenden Schritte aus, um das Installieren der **Mssql-Tools** unter Ubuntu. 

1. Importieren Sie die öffentlichen Repository GPG-Schlüssel.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

1. Registrieren Sie das Microsoft-Ubuntu-Repository.

   ```bash
   curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/msprod.list
   ```

1. Aktualisieren Sie die Liste der Datenquellen, und führen Sie den Installationsbefehl mit dem UnixODBC-Developer-Paket.

   ```bash
   sudo apt-get update 
   sudo apt-get install mssql-tools unixodbc-dev
   ```

   > [!Note] 
   > Aktualisieren Sie auf die neueste Version der **Mssql-Tools** führen Sie die folgenden Befehle:
   >    ```bash
   >   sudo apt-get update 
   >   sudo apt-get install mssql-tools 
   >   ```

1. **Optionale**: Hinzufügen `/opt/mssql-tools/bin/` auf Ihre **Pfad** in einer Bash-Shell-Umgebungsvariablen angegeben.

   Zu **Sqlcmd/Bcp** zugegriffen werden kann, in der Bash-Shell für und-anmeldesitzungen, ändern Ihre **Pfad** in die **~/.bash_profile** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   ```

   Vornehmen **Sqlcmd/Bcp-** zugegriffen werden kann, in der Bash-Shell für interaktive/Sitzungen ohne Anmeldung, ändern Sie die **Pfad** in die **~/.bashrc** -Datei mit den folgenden Befehl aus:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
