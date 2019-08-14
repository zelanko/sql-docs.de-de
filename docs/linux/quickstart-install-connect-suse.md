---
title: Erste Schritte mit SQL Server unter SUSE Linux Enterprise Server
titleSuffix: SQL Server
description: In dieser Schnellstartanleitung erfahren Sie, wie Sie SQL Server 2017 oder SQL Server 2019 unter SUSE Linux Enterprise Server installieren und anschließend mit sqlcmd eine Datenbank erstellen und abfragen.
author: VanMSFT
ms.author: vanto
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 31ddfb80-f75c-4f51-8540-de6213cb68b8
ms.openlocfilehash: b878e76546642ee9b9792ece31029c0640eb8864
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67910495"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-suse-linux-enterprise-server"></a>Schnellstart: Installieren von SQL Server und Erstellen einer Datenbank unter SUSE Linux Enterprise Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In dieser Schnellstartanleitung installieren Sie SQL Server 2017 oder SQL Server 2019 (Vorschau) unter SUSE Linux Enterprise Server (SLES) v12 SP2. Danach stellen Sie eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In dieser Schnellstartanleitung installieren Sie SQL Server 2019 (Vorschau) unter SUSE Linux Enterprise Server (SLES) v12 SP2. Danach stellen Sie eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

::: moniker-end

> [!TIP]
> Für dieses Tutorial sind Benutzereingaben und eine Internetverbindung erforderlich. Wenn Sie am [unbeaufsichtigten](sql-server-linux-setup.md#unattended) oder am [Offline](sql-server-linux-setup.md#offline)-Installationsverfahren interessiert sind, finden Sie weitere Informationen im [Leitfaden für die Installation von SQL Server für Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Voraussetzungen

Sie müssen über einen SLES v12 SP2-Computer mit **mindestens 2 GB** Arbeitsspeicher verfügen. Das Dateisystem muss **XFS** oder **EXT4** sein. Andere Dateisysteme wie z.B. **BTRFS** werden nicht unterstützt.

Um SUSE Linux Enterprise Server auf Ihrem eigenen Computer zu installieren, wechseln Sie zu [https://www.suse.com/products/server](https://www.suse.com/products/server). Sie können auch virtuelle SLES-Computer in Azure erstellen. Weitere Informationen finden Sie unter [Erstellen und Verwalten virtueller Linux-Computer mit der Azure-Befehlszeilenschnittstelle](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm). Verwenden Sie `--image SLES` im Aufruf von `az vm create`.

Wenn Sie bereits eine CTP- oder RC-Version von SQL Server 2017 installiert haben, müssen Sie zuerst das alte Repository entfernen, bevor Sie die folgenden Schritte ausführen. Weitere Informationen finden Sie unter [Konfigurieren von Linux-Repositorys für SQL Server 2017 und 2019](sql-server-linux-change-repo.md).

> [!NOTE]
> Zurzeit wird das [Windows-Subsystem für Linux](https://msdn.microsoft.com/commandline/wsl/about) für Windows 10 als Installationsziel nicht unterstützt.

Weitere Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server für Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installieren von SQL Server

Um SQL Server unter SLES zu konfigurieren, führen Sie in einem Terminal die folgenden Befehle aus, um das Paket **mssql-server** zu installieren:

1. Laden Sie die Konfigurationsdatei für das SLES-Repository für Microsoft SQL Server 2017 herunter:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
   ```

   > [!TIP]
   > Wenn Sie SQL Server 2019 testen möchten, müssen Sie stattdessen das Repository **Preview (2019)** registrieren. Verwenden Sie für Installationen von SQL Server 2019 den folgenden Befehl:
   >
   > ```bash
   > sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   > ```

2. Aktualisieren Sie Ihre Repositorys.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Führen Sie die folgenden Befehle aus, um SQL Server zu installieren:

   ```bash
   sudo zypper install -y mssql-server
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
   systemctl status mssql-server
   ```

6. Wenn Sie eine Remoteverbindung planen, müssen Sie möglicherweise auch den SQL Server-TCP-Port (standardmäßig 1433) in Ihrer Firewall öffnen. Wenn Sie die SuSE-Firewall verwenden, müssen Sie die Konfigurationsdatei **/etc/sysconfig/SuSEfirewall2** bearbeiten. Ändern Sie den Eintrag **FW_SERVICES_EXT_TCP** so, dass die SQL Server-Portnummer enthalten ist.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

Jetzt wird SQL Server auf Ihrem SLES-Computer ausgeführt und ist einsatzbereit!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installieren von SQL Server

Um SQL Server unter SLES zu konfigurieren, führen Sie in einem Terminal die folgenden Befehle aus, um das Paket **mssql-server** zu installieren:

1. Laden Sie die Konfigurationsdatei für das SLES-Repository für Microsoft SQL Server 2019 (Vorschauversion) herunter:

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo
   ```

2. Aktualisieren Sie Ihre Repositorys.

   ```bash
   sudo zypper --gpg-auto-import-keys refresh 
   ```
   
3. Führen Sie die folgenden Befehle aus, um SQL Server zu installieren:

   ```bash
   sudo zypper install -y mssql-server
   ```

4. Nachdem die Paketinstallation abgeschlossen ist, führen Sie **mssql-conf setup** aus, und befolgen Sie die Anweisungen, um das Systemadministratorkennwort festzulegen und Ihre Edition auszuwählen.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Stellen Sie sicher, dass Sie ein sicheres Kennwort für das Systemadministratorkonto angeben (minimale Länge von 8 Zeichen, Groß-und Kleinbuchstaben, Ziffern und/oder nicht-alphanumerische Symbole).

5. Nachdem die Konfiguration abgeschlossen ist, überprüfen Sie, ob der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

6. Wenn Sie eine Remoteverbindung planen, müssen Sie möglicherweise auch den SQL Server-TCP-Port (standardmäßig 1433) in Ihrer Firewall öffnen. Wenn Sie die SuSE-Firewall verwenden, müssen Sie die Konfigurationsdatei **/etc/sysconfig/SuSEfirewall2** bearbeiten. Ändern Sie den Eintrag **FW_SERVICES_EXT_TCP** so, dass die SQL Server-Portnummer enthalten ist.

   ```
   FW_SERVICES_EXT_TCP="1433"
   ```

Jetzt wird SQL Server 2019 (Vorschau) auf Ihrem SLES-Computer ausgeführt und ist einsatzbereit!

::: moniker-end


## <a id="tools"></a>Installieren der SQL Server-Befehlszeilentools

Um eine Datenbank zu erstellen, müssen Sie eine Verbindung mit einem Tool herstellen, das Transact-SQL-Anweisungen auf dem SQL Server-Computer ausführen kann. Mit den folgenden Schritten installieren Sie die SQL Server-Befehlszeilentools: [sqlcmd](../tools/sqlcmd-utility.md) und [bcp](../tools/bcp-utility.md).

1. Fügen Sie das Microsoft SQL Server-Repository zu Zypper hinzu.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo 
   sudo zypper --gpg-auto-import-keys refresh
   ```

1. Installieren Sie **mssql-tools** mit dem unixODBC-Entwicklerpaket.

   ```bash
   sudo zypper install -y mssql-tools unixODBC-devel
   ```

1. Fügen Sie für einfacheres Arbeiten `/opt/mssql-tools/bin/` zu Ihrer **PATH**-Umgebungsvariablen hinzu. Dadurch können Sie die Tools ausführen, ohne den vollständigen Pfad angeben zu müssen. Führen Sie die folgenden Befehle aus, um **PATH** sowohl für Anmeldesitzungen als auch für interaktive Sitzungen oder Sitzungen ohne Anmeldung zu ändern:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
