---
title: Erste Schritte mit SQL Server unter SUSE Linux Enterprise Server
titleSuffix: SQL Server
description: Dieser Schnellstart veranschaulicht das Installieren von SQL Server 2017 oder SQL Server-2019 unter SUSE Linux Enterprise Server und klicken Sie dann zu erstellen und Abfragen einer Datenbank mit Sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: f5c0bb63ce7d188a2587d1a44d863a14308da273
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713575"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Schnellstart: Installieren von SQL Server, und erstellen Sie eine Datenbank unter SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In diesem Schnellstart installieren Sie SQL Server 2017 oder SQL Server-2019 Preview unter SUSE Linux Enterprise Server (SLES) v12 SP2. Verbinden Sie Sie dann mit **Sqlcmd** Erstellen Ihrer ersten Datenbank Abfragen und ausführen.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In dieser schnellstartanleitung installieren Sie SQL Server-2019 Preview unter SUSE Linux Enterprise Server (SLES) v12 SP2. Verbinden Sie Sie dann mit **Sqlcmd** Erstellen Ihrer ersten Datenbank Abfragen und ausführen.

::: moniker-end

> [!TIP]
> Dieses Lernprogramm erfordert eine Benutzereingabe und eine Internetverbindung besteht. Wenn Sie möchten die [unbeaufsichtigte](sql-server-linux-setup.md#unattended) oder [offline](sql-server-linux-setup.md#offline) Installationsverfahren, finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie benötigen einen Computer unter SLES v12 SP2 mit **mindestens 2 GB** des Arbeitsspeichers. Das Dateisystem muss **XFS** oder **EXT4**. Andere Dateisysteme, z. B. **BTRFS**, werden nicht unterstützt.

Wechseln Sie zu SUSE Linux Enterprise Server auf Ihrem eigenen Computer installieren, [ https://www.suse.com/products/server ](https://www.suse.com/products/server). Sie können auch virtuelle SLES-Computer in Azure erstellen. Finden Sie unter [erstellen und Verwalten von virtuellen Linux-Computern mit der Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm), und verwenden Sie `--image SLES` im Aufruf von `az vm create`.

Wenn Sie eine CTP-Version oder die RC-Version von SQL Server 2017 bereits installiert haben, müssen Sie zunächst das alte Repository entfernen, bevor Sie diese Schritte. Weitere Informationen finden Sie unter [Konfigurieren von Linux-Repositorys für SQL Server 2017 und 2019](sql-server-linux-change-repo.md).

> [!NOTE]
> Zu diesem Zeitpunkt die [Windows-Subsystem für Linux](https://msdn.microsoft.com/commandline/wsl/about) für Windows 10 als ein Installationsziel wird nicht unterstützt.

Weitere Informationen zu den Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server unter Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installieren von SQLServer

Führen Sie die folgenden Befehle in einem Terminal zu installieren, um SQL Server unter SLES konfigurieren zu können, die **Mssql-Server** Paket:

1. Laden Sie die Konfigurationsdatei des Microsoft SQL Server 2017-SLES-Repository herunter:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!TIP]
   > Wenn Sie SQL Server-2019 testen möchten, müssen Sie stattdessen Registrieren der **Preview (2019)** Repository. Verwenden Sie den folgenden Befehl für Installationen von SQL Server-2019:
   >
   > ```bash
   > sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   > ```

2. Aktualisieren Sie Ihre Repositorys.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Führen Sie die folgenden Befehle zum Installieren von SQL Server:

   ```bash
   sudo zypper install -y mssql-server
   ```

4. Nach der Paket-Installation abgeschlossen ist, führen Sie **Mssql-Conf Setup** , und befolgen Sie die aufforderungen, um das SA-Kennwort festgelegt, und wählen Sie die Version.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Die folgenden Editionen von SQL Server 2017 sind kostenlos lizenziert: Evaluation, Developer und Express.

   > [!NOTE]
   > Stellen Sie sicher, dass ein sicheres Kennwort für das SA-Konto (minimale Länge von 8-Zeichen, wie z. B. Groß- und Kleinbuchstaben, Basis 10-Ziffern und/oder nicht-alphanumerischen Zeichen) an.

5. Nachdem die Konfiguration abgeschlossen ist, stellen Sie sicher, dass der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

6. Wenn Sie eine Remoteverbindung herstellen möchten, müssen Sie möglicherweise auch die SQL Server-TCP-Port (Standardport: 1433) in Ihrer Firewall öffnen. Wenn Sie die SuSE-Firewall verwenden, müssen Sie so bearbeiten Sie die **/etc/sysconfig/SuSEfirewall2** Konfigurationsdatei. Ändern der **FW_SERVICES_EXT_TCP** einen Eintrag in die SQL Server-Portnummer einschließen.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

An diesem Punkt wird SQL Server auf dem SLES-Computer ausgeführt wird, und ist einsatzbereit!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installieren von SQLServer

Führen Sie die folgenden Befehle in einem Terminal zu installieren, um SQL Server unter SLES konfigurieren zu können, die **Mssql-Server** Paket:

1. Laden Sie die Konfigurationsdatei für Microsoft SQL Server-2019 Vorschau SLES-Repository herunter:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   ```

2. Aktualisieren Sie Ihre Repositorys.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Führen Sie die folgenden Befehle zum Installieren von SQL Server:

   ```bash
   sudo zypper install -y mssql-server
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

6. Wenn Sie eine Remoteverbindung herstellen möchten, müssen Sie möglicherweise auch die SQL Server-TCP-Port (Standardport: 1433) in Ihrer Firewall öffnen. Wenn Sie die SuSE-Firewall verwenden, müssen Sie so bearbeiten Sie die **/etc/sysconfig/SuSEfirewall2** Konfigurationsdatei. Ändern der **FW_SERVICES_EXT_TCP** einen Eintrag in die SQL Server-Portnummer einschließen.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

An diesem Punkt SQL Server-2019 Preview auf Ihrem SLES-Computer ausgeführt wird und ist einsatzbereit!

::: moniker-end


## <a id="tools"></a>Installieren der SQL Server-Befehlszeilentools

Um eine Datenbank erstellen zu können, müssen Sie die Verbindung mit einem Tool, das auf dem SQL Server Transact-SQL-Anweisungen ausgeführt werden kann. Die folgenden Schritte aus, Installieren der SQL Server-Befehlszeilentools: [Sqlcmd](../tools/sqlcmd-utility.md) und [Bcp](../tools/bcp-utility.md).

1. Die Microsoft SQL Server-Repository Zypper hinzufügen.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installieren Sie **Mssql-Tools** mit dem UnixODBC-Developer-Paket.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Fügen Sie der Einfachheit halber `/opt/mssql-tools/bin/` auf Ihre **Pfad** -Umgebungsvariablen angegeben. Dadurch können Sie die Tools ausführen, ohne den vollständigen Pfad anzugeben. Führen Sie die folgenden Befehle zum Ändern der **Pfad** sowohl für anmeldesitzungen als auch für interaktive/Sitzungen ohne Anmeldung:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
