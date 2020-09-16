---
title: SQL Server PowerShell
description: Hier erfahren Sie mehr über die beiden SQL Server PowerShell-Module „SqlServer“ und „SQLPS“, die PowerShell-Anbieter und Cmdlets umfassen.
ms.prod: sql
ms.technology: sql-server-powershell
ms.topic: conceptual
ms.assetid: 89b70725-bbe7-4ffe-a27d-2a40005a97e7
author: markingmyname
ms.author: maghan
ms.reviewer: matteot
ms.custom: ''
ms.date: 06/11/2020
ms.openlocfilehash: e320408fd569cbf747c9f9ada68f51dd2bea8a41
ms.sourcegitcommit: a9f16d7819ed0e2b7ad8f4a7d4d2397437b2bbb2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714328"
---
# <a name="sql-server-powershell"></a>SQL Server PowerShell

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

**[Installieren von SQL Server PowerShell](download-sql-server-ps-module.md)**

Es gibt zwei SQL Server PowerShell-Module: **SqlServer** und **SQLPS**. Das **SQLPS**-Modul ist zwar in der SQL Server-Installation (für die Abwärtskompatibilität) enthalten, wird jedoch nicht mehr aktualisiert. Das **SqlServer**-Modul ist das aktuellste PowerShell-Modul. Das **SqlServer**-Modul enthält aktualisierte Versionen der Cmdlets in **SQLPS** sowie neue Cmdlets zur Unterstützung der neuesten SQL-Funktionen.  

Vorherige Versionen des **SqlServer**-Moduls waren im SQL Server Management Studio (SSMS) enthalten, allerdings nur in den Versionen 16.x.

Das **SqlServer**-Modul muss über den PowerShell-Katalog installiert werden, damit PowerShell mit SSMS 17.0 und höher verwendet werden kann.

Informationen zur Installation des **SqlServer**-Moduls finden Sie unter [Installieren von SQL Server PowerShell](download-sql-server-ps-module.md).

**Warum wurde das Modul von „SQLPS“ in „SqlServer“ geändert?**

Zur Freigabe von SQL PowerShell-Updates mussten die Identitäten des SQL PowerShell-Moduls und des Wrappers *SQLPS.exe* geändert werden. Aufgrund dieser Änderung gibt es jetzt zwei SQL PowerShell-Module: das **SqlServer**-Modul und das **SQLPS**-Modul.  

**Aktualisieren Sie Ihre PowerShell-Skripts, wenn Sie das SQLPS-Modul importieren.**

Wenn Sie über PowerShell-Skripts verfügen, die `Import-Module -Name SQLPS` ausführen, und Sie die Vorteile der neuen Anbieterfunktionen und Cmdlets nutzen möchten, müssen Sie diese in `Import-Module -Name SqlServer` ändern. Das neue Modul wird im Ordner `%ProgramFiles%\WindowsPowerShell\Modules\SqlServer` installiert. Daher müssen Sie die Variable „$env:PSModulePath“ nicht aktualisieren. Wenn Sie über Skripts verfügen, die eine Community-Version oder eine Version eines Drittanbieters eines Moduls mit dem Namen **SqlServer** verwenden, verwenden Sie den Parameter „Prefix“, um Konflikte mit den Namen zu vermeiden.

Es wird empfohlen, das Skript mit *Import-Module SQLServer* zu starten, um parallele Probleme zu vermeiden, wenn das SQLPS-Modul auf demselben Computer installiert ist.

Dieser Abschnitt gilt für Skripts, die von PowerShell und nicht vom SQL-Agent ausgeführt werden. Das neue Modul kann mit SQL-Agent-Auftragsschritten mithilfe von [#NOSQLPS](#sql-server-agent) verwendet werden.

## <a name="sql-server-powershell-components"></a>SQL Server PowerShell-Komponenten

Das **SqlServer**-Modul umfasst Folgendes:

- [PowerShell-Anbieter](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers), was einen einfachen Navigationsmechanismus wie bei Dateisystempfaden ermöglicht. Sie können Dateisystempfaden ähnelnde Pfade erstellen, in denen das Laufwerk einem SQL Server-Management Object-Modell zugeordnet ist und deren Knoten auf Objektmodellklassen basieren. Sie können dann vertraute Befehle wie **cd** und **dir** verwenden, um auf den Pfaden zu navigieren, auf ähnliche Weise, wie Sie in einem Eingabeaufforderungsfenster in Ordnern navigieren. Mit anderen Befehlen, wie **ren** oder **del**, können Sie Aktionen für die Knoten im Pfad ausführen.

- mehrere Cmdlets, die Aktionen wie das Ausführen eines **sqlcmd**-Skripts unterstützen, das Transact-SQL- oder XQuery-Anweisungen enthält  

- AS-Anbieter und Cmdlets, die zuvor separat installiert wurden

## <a name="sql-server-versions"></a>SQL Server-Versionen

SQL PowerShell-Cmdlets können verwendet werden, um Instanzen von Azure SQL-Datenbank und Azure SQL Data Warehouse sowie alle [unterstützten SQL Server-Produkte](https://support.microsoft.com/lifecycle/search/1044) zu verwalten.

## <a name="sql-server-identifiers-that-contain-characters-not-supported-in-powershell-paths"></a>SQL Server-Bezeichner mit Zeichen, die in PowerShell-Pfaden nicht unterstützt werden.

Das **Encode-Sqlname** -Cmdlet und das **Decode-Sqlname** -Cmdlet helfen Ihnen, SQL Server-Bezeichner mit Zeichen anzugeben, die in PowerShell-Pfaden nicht unterstützt werden. Weitere Informationen finden Sie unter [SQL Server Identifiers in PowerShell](sql-server-identifiers-in-powershell.md).

Verwenden Sie das **Convert-UrnToPath**-Cmdlet, um einen eindeutigen Ressourcennamen (Unique Resource Name, URN) für ein Datenbank-Engine-Objekt in einen Pfad für den SQL Server PowerShell-Anbieter zu konvertieren. Weitere Informationen finden Sie unter [Convert URNs to SQL Server Provider Paths](https://docs.microsoft.com/powershell/module/sqlserver/Convert-UrnToPath).
  
## <a name="query-expressions-and-unique-resource-names"></a>Abfrageausdrücke und eindeutige Ressourcennamen  

Bei Abfrageausdrücken handelt es sich um Zeichenfolgen, die eine ähnliche Syntax wie XPath nutzen, um eine Gruppe von Kriterien angeben, mit der ein oder mehrere Objekte in einer Objektmodellhierarchie aufgezählt werden. Ein eindeutiger Ressourcenname (Unique Resource Name, URN) ist ein spezieller Typ einer Abfrageausdrucks-Zeichenfolge, der ein einzelnes Objekt eindeutig kennzeichnet. Weitere Informationen finden Sie unter [Query Expressions and Uniform Resource Names](query-expressions-and-uniform-resource-names.md).

## <a name="sql-server-agent"></a>SQL Server-Agent

Es wurden keine Änderungen an dem von SQL Server-Agent verwendeten Modul vorgenommen. Daher verwenden SQL Server-Agent-Aufträge, die über PowerShell-Auftragsschritte verfügen, das SQLPS-Modul. Weitere Informationen finden Sie im Artikel zum [Ausführen von PowerShell mit dem SQL Server-Agent](run-windows-powershell-steps-in-sql-server-agent.md). Ab SQL Server 2019 können Sie SQLPS jedoch deaktivieren. Fügen Sie hierzu in der ersten Zeile eines Auftragsschritts des PowerShell-Moduls `#NOSQLPS` hinzu, wodurch der SQL-Agent aufhört, das SQLPS-Modul automatisch zu laden. Wenn Sie dies tun, führt der SQL-Agent-Auftrag die auf dem Computer installierte PowerShell-Version aus. Sie können dann auch ein beliebiges anderes PowerShell-Modul verwenden.

Wenn Sie das **SqlServer**-Modul in Ihrem SQL-Agent-Auftragsschritt verwenden möchten, können Sie diesen Code in den ersten beiden Skriptzeilen platzieren.

```powershell
#NOSQLPS
Import-Module -Name SqlServer
```

## <a name="cmdlet-reference"></a>Cmdlet-Referenz

- [SqlServer-Cmdlets](https://docs.microsoft.com/powershell/module/sqlserver)
- [SQLPS-Cmdlets](https://docs.microsoft.com/powershell/module/sqlps)

## <a name="next-steps"></a>Nächste Schritte

[Herunterladen des SQL Server PowerShell-Moduls](download-sql-server-ps-module.md)
