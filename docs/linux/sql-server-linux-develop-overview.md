---
title: Entwickeln von Anwendungen für SQL Server unter Linux | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 11/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.custom: sql-linux
ms.suite: sql
ms.technology: linux
ms.assetid: 758cb738-b018-465b-9ab0-59a24b892e66
ms.openlocfilehash: 317c2ea2064f7ffc286671a8fff7eef2f8149ee7
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084919"
---
# <a name="how-to-get-started-developing-applications-for-sql-server-on-linux"></a>Vorgehensweise zum Einstieg in die Entwicklung von Anwendungen für SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können Anwendungen erstellen, die Herstellen einer Verbindung mit und Verwenden von SQL Server 2017 unter Linux aus einer Vielzahl von Programmiersprachen, z. B. c#, Java, Node.js, PHP, Python, Ruby und C++. Sie können auch beliebte webframeworks und Frameworks der Object Relational Mapping (ORM) verwenden.

> [!VIDEO https://channel9.msdn.com/events/Connect/2017/T153/player]

> [!TIP]
> Diese gleichen Entwicklungsoptionen können Sie auch in SQL Server auf anderen Plattformen als Ziel. Anwendungen können Ziel-SQL-Server lokal oder in der Cloud unter Linux, Windows oder mit Docker unter MacOS. Oder Sie können als Ziel Azure SQL-Datenbank und Azure SQL Data Warehouse.

## <a name="try-the-tutorials"></a>Nutzen Sie die tutorials

Die beste Möglichkeit, erste Schritte aus, und Erstellen von Anwendungen mit SQL Server ist es selbst auszuprobieren.

- Navigieren Sie zu [erste Schritte-Tutorials](http://aka.ms/sqldev).
- Wählen Sie Ihre Plattform für Sprach- und Entwicklungstools.
- Wiederholen Sie die Codebeispiele aus.

> [!TIP]
> Wenn Sie für SQL Server 2017 unter Docker entwickeln möchten, sehen Sie sich die **MacOS** Tutorials.

## <a name="create-new-applications"></a>Erstellen Sie neue Anwendungen

Wenn Sie eine neue Anwendung erstellen, sehen Sie sich eine Liste mit den [verbindungsbibliotheken](sql-server-linux-develop-connectivity-libraries.md) eine Zusammenfassung der Connectors und beliebte Frameworks, die für verschiedene Programmiersprachen zur Verfügung.

## <a name="use-existing-applications"></a>Nutzen Sie bestehende Anwendungen

Wenn Sie eine vorhandene datenbankanwendung verfügen, können Sie einfach die Verbindungszeichenfolge in SQL Server 2017 unter Linux als Ziel ändern. Achten Sie darauf, die zum Lesen der [bekannte Probleme](sql-server-linux-release-notes.md) in SQL Server 2017 unter Linux.

## <a name="use-existing-sql-tools-on-windows-with-sql-server-on-linux"></a>Verwenden von vorhandenen SQL-Tools in Windows mit SQL Server unter Linux

Tools, die derzeit für Windows wie z. B. SSMS, SSDT und PowerShell, ausgeführt werden, funktionieren auch mit SQL Server 2017 unter Linux. Auch wenn ihnen nicht nativ unter Linux ausgeführt wird, können Sie remote SQL Server-Instanzen unter Linux noch verwalten. 

Finden Sie unter den folgenden Themen Weitere Informationen:

- [SQL Server Management Studio (SSMS)](sql-server-linux-manage-ssms.md)
- [SQL Server Data Tools (SSDT)](sql-server-linux-develop-use-ssdt.md)
- [SQL-PowerShell](sql-server-linux-manage-powershell.md)

> [!Note]
> Stellen Sie sicher, dass Sie für optimale Ergebnisse die neuesten Versionen dieser Tools verwenden.

## <a name="use-new-sql-tools-for-linux"></a>Verwenden Sie die neue SQL-Tools für Linux

Sie können die neue [Mssql-Erweiterung](https://aka.ms/mssql-marketplace) für [Visual Studio Code](https://code.visualstudio.com) unter Linux, MacOS und Windows. Eine schrittweise Anleitung finden Sie unter dem folgenden Tutorial:

- [Use Visual Studio Code (Verwenden von Visual Studio Code)](sql-server-linux-develop-use-vscode.md)

Sie können auch neue Befehlszeilentools verwenden, die native für Linux sind. Diese Tools umfassen Folgendes:

- [sqlcmd](../tools/sqlcmd-utility.md)
- [bcp](sql-server-linux-migrate-bcp.md)
- [mssql-conf](sql-server-linux-configure-mssql-conf.md)

## <a name="next-steps"></a>Nächste Schritte

Installieren von SQL Server unter Linux mit einer der folgenden schnellstartanleitungen zum Einstieg:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installieren unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-ubuntu.md)
