---
title: Erste Schritte mit SQL Server unter Red Hat Enterprise Linux
titleSuffix: SQL Server
description: Dieser Schnellstart veranschaulicht das Installieren von SQL Server 2017 oder SQL Server-2019 auf Red Hat Enterprise Linux, und klicken Sie dann zu erstellen und Abfragen einer Datenbank mit Sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/16/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.custom: sql-linux, seodec18
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: dce4418dee10ff356d5c922350cd2fda29b44795
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58277307"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Schnellstart: Installieren von SQL Server, und erstellen Sie eine Datenbank auf Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

In dieser schnellstartanleitung installieren Sie SQL Server 2017 oder SQL Server-2019 an, zu auf Red Hat Enterprise Linux (RHEL). Verbinden Sie Sie dann mit **Sqlcmd** Erstellen Ihrer ersten Datenbank Abfragen und ausführen.

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

In dieser schnellstartanleitung installieren Sie SQL Server-2019 Vorschau auf die Red Hat Enterprise Linux (RHEL) 7.3 und höher. Verbinden Sie Sie dann mit **Sqlcmd** Erstellen Ihrer ersten Datenbank Abfragen und ausführen.

::: moniker-end

> [!TIP]
> Dieses Lernprogramm erfordert eine Benutzereingabe und eine Internetverbindung besteht. Wenn Sie möchten die [unbeaufsichtigte](sql-server-linux-setup.md#unattended) oder [offline](sql-server-linux-setup.md#offline) Installationsverfahren, finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie benötigen einen Computer RHEL 7.3, 7.4, 7.5 oder 7.6 mit **mindestens 2 GB** des Arbeitsspeichers.

Wechseln Sie zu Red Hat Enterprise Linux auf Ihrem eigenen Computer installieren, [ https://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](https://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Sie können auch RHEL-VMs in Azure erstellen. Finden Sie unter [erstellen und Verwalten von virtuellen Linux-Computern mit der Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm), und verwenden Sie `--image RHEL` im Aufruf von `az vm create`.

Wenn Sie eine CTP-Version oder die RC-Version von SQL Server 2017 bereits installiert haben, müssen Sie zunächst das alte Repository entfernen, bevor Sie diese Schritte. Weitere Informationen finden Sie unter [Konfigurieren von Linux-Repositorys für SQL Server 2017 und 2019](sql-server-linux-change-repo.md).

Weitere Informationen zu den Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server unter Linux](sql-server-linux-setup.md#system).

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

## <a id="install"></a>Installieren von SQLServer

Führen Sie die folgenden Befehle in einem Terminal zu installieren, um SQL Server unter RHEL konfigurieren zu können, die **Mssql-Server** Paket:

1. Laden Sie die Konfigurationsdatei des Microsoft SQL Server 2017 Red Hat-Repository herunter:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!TIP]
   > Wenn Sie SQL Server-2019 testen möchten, müssen Sie stattdessen Registrieren der **Preview (2019)** Repository. Verwenden Sie den folgenden Befehl für Installationen von SQL Server-2019:
   >
   > ```bash
   > sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   > ```

2. Führen Sie die folgenden Befehle zum Installieren von SQL Server:

   ```bash
   sudo yum install -y mssql-server
   ```

3. Nach der Paket-Installation abgeschlossen ist, führen Sie **Mssql-Conf Setup** , und befolgen Sie die aufforderungen, um das SA-Kennwort festgelegt, und wählen Sie die Version.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!TIP]
   > Die folgenden Editionen von SQL Server 2017 sind kostenlos lizenziert: Evaluation, Developer und Express.

   > [!NOTE]
   > Stellen Sie sicher, dass ein sicheres Kennwort für das SA-Konto (minimale Länge von 8-Zeichen, wie z. B. Groß- und Kleinbuchstaben, Basis 10-Ziffern und/oder nicht-alphanumerischen Zeichen) an.

4. Nachdem die Konfiguration abgeschlossen ist, stellen Sie sicher, dass der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

5. Um Remoteverbindungen zuzulassen, öffnen Sie SQL Server-Port auf der Firewall in RHEL. Der SQL Server-Standardport ist TCP-Port 1433. Bei Verwendung von **FirewallD** für Ihre Firewall, können Sie die folgenden Befehle aus:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

An diesem Punkt wird SQL Server auf dem RHEL-Computer ausgeführt wird, und ist einsatzbereit!

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions"

## <a id="install"></a>Installieren von SQLServer

Führen Sie die folgenden Befehle in einem Terminal zu installieren, um SQL Server unter RHEL konfigurieren zu können, die **Mssql-Server** Paket:

1. Laden Sie die Vorschau für Microsoft SQL Server-2019 Red Hat-Repository-Konfigurationsdatei herunter:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo
   ```

2. Führen Sie die folgenden Befehle zum Installieren von SQL Server:

   ```bash
   sudo yum install -y mssql-server
   ```

3. Nach der Paket-Installation abgeschlossen ist, führen Sie **Mssql-Conf Setup** , und befolgen Sie die aufforderungen, um das SA-Kennwort festgelegt, und wählen Sie die Version.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```

   > [!NOTE]
   > Stellen Sie sicher, dass ein sicheres Kennwort für das SA-Konto (minimale Länge von 8-Zeichen, wie z. B. Groß- und Kleinbuchstaben, Basis 10-Ziffern und/oder nicht-alphanumerischen Zeichen) an.

4. Nachdem die Konfiguration abgeschlossen ist, stellen Sie sicher, dass der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```

5. Um Remoteverbindungen zuzulassen, öffnen Sie SQL Server-Port auf der Firewall in RHEL. Der SQL Server-Standardport ist TCP-Port 1433. Bei Verwendung von **FirewallD** für Ihre Firewall, können Sie die folgenden Befehle aus:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

An diesem Punkt 2019 für SQL Server-Vorschau ist auf dem RHEL-Computer ausgeführt und ist einsatzbereit!

::: moniker-end

## <a id="tools"></a>Installieren der SQL Server-Befehlszeilentools

Um eine Datenbank erstellen zu können, müssen Sie die Verbindung mit einem Tool, das auf dem SQL Server Transact-SQL-Anweisungen ausgeführt werden kann. Die folgenden Schritte aus, Installieren der SQL Server-Befehlszeilentools: [Sqlcmd](../tools/sqlcmd-utility.md) und [Bcp](../tools/bcp-utility.md).

1. Laden Sie die Konfigurationsdatei des Microsoft Red Hat-Repository herunter.

   ```bash
   sudo curl -o /etc/yum.repos.d/msprod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```

1. Wenn Sie eine frühere Version von hatten **Mssql-Tools** installiert haben, entfernen Sie alle älteren UnixODBC-Pakete.

   ```bash
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel
   ```

1. Führen Sie die folgenden Befehle zum Installieren **Mssql-Tools** mit dem UnixODBC-Developer-Paket.

   ```bash
   sudo yum install -y mssql-tools unixODBC-devel
   ```

1. Fügen Sie der Einfachheit halber `/opt/mssql-tools/bin/` auf Ihre **Pfad** -Umgebungsvariablen angegeben. Dadurch können Sie die Tools ausführen, ohne den vollständigen Pfad anzugeben. Führen Sie die folgenden Befehle zum Ändern der **Pfad** sowohl für anmeldesitzungen als auch für interaktive/Sitzungen ohne Anmeldung:

   ```bash
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
