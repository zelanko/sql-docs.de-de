---
title: Erste Schritte mit SQL Server 2017 unter Red Hat Enterprise Linux | Microsoft-Dokumentation
description: Dieser Schnellstart veranschaulicht das Installieren von SQL Server 2017 auf Red Hat Enterprise Linux, und klicken Sie dann zu erstellen und Abfragen einer Datenbank mit Sqlcmd.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/22/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.assetid: 92503f59-96dc-4f6a-b1b0-d135c43e935e
ms.openlocfilehash: de149b0a75a550101e761baa109bc07dac062fcd
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020417"
---
# <a name="quickstart-install-sql-server-and-create-a-database-on-red-hat"></a>Schnellstart: Installieren von SQL Server, und erstellen Sie eine Datenbank auf Red Hat

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Schnellstart installieren Sie zunächst SQL Server 2017 auf die Red Hat Enterprise Linux (RHEL) 7.3 und höher. Stellen Sie anschließend eine Verbindung mit **sqlcmd** her, um Ihre erste Datenbank zu erstellen und Abfragen auszuführen.

> [!TIP]
> Dieses Lernprogramm erfordert eine Benutzereingabe und eine Internetverbindung besteht. Wenn Sie möchten die [unbeaufsichtigte](sql-server-linux-setup.md#unattended) oder [offline](sql-server-linux-setup.md#offline) Installationsverfahren, finden Sie unter [zur Installation von SQL Server unter Linux](sql-server-linux-setup.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie benötigen eine RHEL 7.3 oder 7.4 Computer mit **mindestens 2 GB** des Arbeitsspeichers.

Wechseln Sie zu Red Hat Enterprise Linux auf Ihrem eigenen Computer installieren, [ http://access.redhat.com/products/red-hat-enterprise-linux/evaluation ](http://access.redhat.com/products/red-hat-enterprise-linux/evaluation). Sie können auch RHEL-VMs in Azure erstellen. Finden Sie unter [erstellen und Verwalten von virtuellen Linux-Computern mit der Azure CLI](https://docs.microsoft.com/azure/virtual-machines/linux/tutorial-manage-vm), und verwenden Sie `--image RHEL` im Aufruf von `az vm create`.

Weitere Informationen zu den Systemanforderungen finden Sie unter [Systemanforderungen für SQL Server unter Linux](sql-server-linux-setup.md#system).

## <a id="install"></a>Installieren von SQLServer

Führen Sie die folgenden Befehle in einem Terminal zu installieren, um SQL Server unter RHEL konfigurieren zu können, die **Mssql-Server** Paket:

> [!IMPORTANT]
> Wenn Sie eine CTP-Version oder die RC-Version von SQL Server 2017 bereits installiert haben, müssen Sie zuerst die alte Repository entfernen, vor der Registrierung eines der GA-Repositorys. Weitere Informationen finden Sie unter [ändern Repositorys aus dem Repository für die Vorschau zu GA-Repositorys](sql-server-linux-change-repo.md).

1. Laden Sie die Konfigurationsdatei des Microsoft SQL Server-Red Hat-Repository herunter:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo
   ```

   > [!NOTE]
   > Dies ist das kumulative Update (CU)-Repository. Weitere Informationen zu Ihrem repositoryoptionen und ihre Unterschiede finden Sie unter [Repositorys für SQL Server unter Linux konfigurieren](sql-server-linux-change-repo.md).

1. Führen Sie die folgenden Befehle zum Installieren von SQL Server:

   ```bash
   sudo yum install -y mssql-server
   ```

1. Nach der Paket-Installation abgeschlossen ist, führen Sie **Mssql-Conf Setup** , und befolgen Sie die aufforderungen, um das SA-Kennwort festgelegt, und wählen Sie die Version.

   ```bash
   sudo /opt/mssql/bin/mssql-conf setup
   ```
   > [!TIP]
   > Wenn Sie SQL Server 2017 in diesem Tutorial versuchen, werden die folgenden Editionen kostenlos lizenziert: Evaluation, Developer und Express.

   > [!NOTE]
   > Stellen Sie sicher, dass ein sicheres Kennwort für das SA-Konto (minimale Länge von 8-Zeichen, wie z. B. Groß- und Kleinbuchstaben, Basis 10-Ziffern und/oder nicht-alphanumerischen Zeichen) an.

1. Nachdem die Konfiguration abgeschlossen ist, stellen Sie sicher, dass der Dienst ausgeführt wird:

   ```bash
   systemctl status mssql-server
   ```
   
1. Um Remoteverbindungen zuzulassen, öffnen Sie SQL Server-Port auf der Firewall in RHEL. Der SQL Server-Standardport ist TCP-Port 1433. Bei Verwendung von **FirewallD** für Ihre Firewall, können Sie die folgenden Befehle aus:

   ```bash
   sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
   sudo firewall-cmd --reload
   ```

An diesem Punkt wird SQL Server auf dem RHEL-Computer ausgeführt wird, und ist einsatzbereit!

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

> [!TIP]
> **Sqlcmd** ist nur ein Tool zum Herstellen einer Verbindung mit SQL Server zum Ausführen von Abfragen und Ausführen von Aufgaben für Verwaltungs- und Entwicklungstools. Andere Tools sind:
>
> * [SQL Server Operations Studio (Vorschauversion)](../sql-operations-studio/what-is.md)
> * [SQL Server Management Studio](sql-server-linux-manage-ssms.md)
> * [Visual Studio-Code](sql-server-linux-develop-use-vscode.md).
> * [mssql-cli (Vorschauversion)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/)

[!INCLUDE [Connect, create, and query data](../includes/sql-linux-quickstart-connect-query.md)]
