---
title: Verwalten von SQL Server für Linux
description: Dieser Artikel enthält Links zu allgemeinen Verwaltungsaufgaben und Tools für SQL Server, die unter Linux ausgeführt werden.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 6bd8eb0b-593d-467e-87ea-ab1c4dbcd1ea
ms.openlocfilehash: 51feab9c5cc38f1e9b67b3de68ce29c597cdb83a
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85883907"
---
# <a name="choose-the-right-tool-to-manage-sql-server-on-linux"></a>Auswählen des richtigen Tools zum Verwalten von SQL Server für Linux

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Es gibt mehrere Möglichkeiten, SQL Server für Linux zu verwalten. Der folgende Abschnitt enthält eine kurze Übersicht über verschiedene Verwaltungstools und -techniken mit Verweisen auf weitere Ressourcen.

## <a name="mssql-conf"></a>mssql-conf 

Mit dem **mssql-conf**-Tool wird SQL Server für Linux konfiguriert. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server für Linux mithilfe von mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="transact-sql"></a>Transact-SQL

Fast alle Aktionen, die Sie in einem Clienttool ausführen können, können auch mit Transact-SQL-Anweisungen ausgeführt werden. SQL Server stellt [dynamische Verwaltungssichten](../relational-databases/system-dynamic-management-views/system-dynamic-management-views.md) (Dynamic Management Views, DMVs) bereit, mit denen der Status und die Konfiguration von SQL Server abgefragt werden können. Außerdem gibt es [Transact-SQL-Befehle](../t-sql/language-reference.md) für Datenbankverwaltungsaufgaben. Sie können diese Befehle in jedem Clienttool ausführen, das Herstellen von Verbindungen mit SQL Server und Ausführen von Transact-SQL-Abfragen unterstützt, etwa [sqlcmd](sql-server-linux-setup-tools.md) oder [Visual Studio Code](sql-server-linux-develop-use-vscode.md).

## <a name="azure-data-studio"></a>Azure Data Studio

Das neue Azure Data Studio ist ein plattformübergreifendes Tool zum Verwalten von SQL Server. Weitere Informationen finden Sie unter [Azure Data Studio](../azure-data-studio/what-is.md).

## <a name="sql-server-management-studio-on-windows"></a>SQL Server Management Studio unter Windows

SQL Server Management Studio (SSMS) ist eine Windows-Anwendung, die eine grafische Benutzeroberfläche zum Verwalten von SQL Server bereitstellt. Obwohl die Anwendung zurzeit nur unter Windows ausgeführt wird, können Sie sie verwenden, um Remoteverbindungen mit Ihren Linux SQL Server-Instanzen herzustellen. Weitere Informationen zum Verwenden von SSMS, um SQL Server zu verwalten, finden Sie unter [Verwenden von SSMS zum Verwalten von SQL Server für Linux](sql-server-linux-manage-ssms.md).

## <a name="mssql-cli-preview"></a>mssql-cli (Vorschauversion)

Microsoft hat ein neues plattformübergreifendes Skripterstellungstool für SQL Server, [mssql-cli](https://blogs.technet.microsoft.com/dataplatforminsider/2017/12/12/try-mssql-cli-a-new-interactive-command-line-tool-for-sql-server/), veröffentlicht. Dieses Tool befindet sich zurzeit in der Vorschau.

## <a name="powershell"></a>PowerShell

PowerShell stellt eine leistungsstarke Befehlszeilenumgebung zum Verwalten von SQL Server für Linux bereit. Weitere Informationen finden Sie unter [Verwenden von PowerShell unter Windows zum Verwalten von SQL Server für Linux](sql-server-linux-manage-powershell.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server für Linux finden Sie unter [SQL Server für Linux](sql-server-linux-overview.md).
