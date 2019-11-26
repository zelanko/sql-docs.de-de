---
title: Verwenden des PowerShell-Anbieters für erweiterte Ereignisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- PowerShell [SQL Server], xevent
- extended events [SQL Server], PowerShell
- PowerShell [SQL Server], extended events
ms.assetid: 0b10016f-a479-4444-a484-46cb4677cf64
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ea4432b07007ce1bbc4ec5b944594b204a7ad808
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72782905"
---
# <a name="use-the-powershell-provider-for-extended-events"></a>Verwenden des PowerShell-Anbieters für erweiterte Ereignisse
  Erweiterte Ereignisse von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Anbieters verwalten. Der Unterordner XEvent ist auf dem SQLSERVER-Laufwerk verfügbar. Auf diesen Ordner können Sie mit einer der folgenden Methoden zugreifen:  
  
-   Geben Sie an der Eingabeaufforderung `sqlps` ein, und drücken Sie dann die EINGABETASTE. Geben Sie `cd xevent` ein, und drücken Sie dann die EINGABETASTE. Von dort aus können Sie die Befehle " **CD** " und "`dir`" (oder die Cmdlets " **Set-Location** " und " **Get-ChildItem** ") verwenden, um zum Servernamen und Instanznamen zu navigieren.  
  
-   Erweitern Sie im Objekt-Explorer den Instanznamen, erweitern Sie **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Erweiterte Ereignisse**, und klicken Sie anschließend auf **PowerShell starten**. Damit wird PowerShell unter dem folgenden Pfad gestartet:  
  
     PS SQLSERVER:\XEvent\\*Servername*\\*Instanzname*>  
  
    > [!NOTE]  
    >  PowerShell können Sie unter **Erweiterte Ereignisse**von jedem Knoten aus starten. Sie können z.B. mit der rechten Maustaste auf **Sitzungen**klicken und anschließend auf **PowerShell starten**klicken. Damit starten Sie PowerShell eine Ebene tiefer, mit dem Ordner Sitzungen.  
  
 Sie können die Struktur des Ordners "XEvent" nach vorhandenen Sitzungen für erweiterte Ereignisse und deren zugeordneten Ereignissen, Zielen und Prädikaten durchsuchen. Wenn Sie z. b. von der Datei PS SQLServer: \ XEvent\\*Servername*\\*instanceName*> Pfad eingeben `cd sessions`, drücken Sie die EINGABETASTE, geben Sie `dir`ein, und drücken Sie dann die EINGABETASTE, um die Liste der Sitzungen anzuzeigen, die auf dieser Instanz gespeichert sind. Sie können auch anzeigen, ob die Sitzung ausgeführt wird (und wenn dies der Fall ist, die bisherige Sitzungsdauer), sowie ob die Sitzung für den Start bei Instanzstart konfiguriert ist.  
  
 Wenn Sie die Ereignisse, deren Prädikate und die einer Sitzung zugeordneten Ziele anzeigen möchten, können Sie Verzeichnisse in den Sitzungsnamen ändern und dann den Ereignis- oder den Zielordner anzeigen. Um z. b. die Ereignisse und deren Prädikate anzuzeigen, die der standardmäßigen System Integritäts Sitzung zugeordnet sind, geben Sie im Verzeichnis PS SQLServer: \ XEvent\\*Servername*\\*instanceName*\sessions > Pfad `cd system_health\events,` drücken Sie die EINGABETASTE, geben Sie `dir`ein, und drücken Sie dann die EINGABETASTE.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Anbieter ist ein leistungsstarkes Tool, mit dem Sie Sitzungen für erweiterte Ereignisse erstellen, ändern und verwalten können. Der folgende Abschnitt enthält einige einfache Beispiele für die Verwendung von PowerShell-Skripts mit erweiterten Ereignissen.  
  
## <a name="examples"></a>Beispiele  
 Achten Sie in den folgenden Beispielen auf Folgendes:  
  
-   Die Skripts müssen über die Eingabeaufforderung von PS SQLServer:\\> ausgeführt werden (verfügbar, wenn Sie an einer Eingabeaufforderung `sqlps` eingeben).  
  
-   Die Skripts verwenden die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Die Skripts müssen mit der Erweiterung .ps1 gespeichert werden.  
  
-   In der PowerShell-Ausführungsrichtlinie muss das auszuführende Skript zugelassen sein. Verwenden Sie das Cmdlet **Set-Executionpolicy** , um die Ausführungsrichtlinie festzulegen. (Weitere Informationen erhalten Sie durch Eingabe von `get-help set-executionpolicy -detailed` und Drücken der EINGABETASTE.)  
  
 Mit dem folgenden Skript erstellen Sie die neue Sitzung "TestSession".  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession"  
$event = $session.AddEvent("sqlserver.file_written")  
$event.AddAction("package0.callstack")  
$session.Create()  
```  
  
 Das folgende Skript fügt der im vorherigen Beispiel erstellten Sitzung das Ringpufferziel hinzu. (In diesem Beispiel wird die Verwendung der `Alter`-Methode veranschaulicht. Sie können das Ziel beim Erstellen der Sitzung hinzufügen.)  
  
```powershell
#Script to alter a session.  
cd XEvent  
$h = hostname  
cd $h  
cd DEFAULT\Sessions  
  
#Used to find the specified session.  
$session = dir | where {$_.Name -eq 'TestSession'}  
  
#Add the ring buffer target and call the Alter method.  
$session.AddTarget("package0.ring_buffer")  
$session.Alter()  
```  
  
 Mit dem folgenden Skript erstellen Sie eine neue Sitzung, in der ein Prädikatausdruck verwendet wird. In diesem Fall werden in der Sitzung Informationen gesammelt, die in die Datei „c:\temp.log“ geschrieben werden (über das Ereignis „sqlserver.file_written“).  
  
```powershell
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = New-Object Microsoft.SqlServer.Management.XEvent.Session -ArgumentList $store, "TestSession2"  
$event = $session.AddEvent("sqlserver.file_written")  
  
#Construct a predicate "equal_i_unicode_string(path, N'c:\temp.log')".  
$column = $store.SqlServerPackage.EventInfoSet["file_written"].DataEventColumnInfoSet["path"]  
$operand = new-object Microsoft.SqlServer.Management.XEvent.PredOperand -argumentlist $column  
$value = new-object Microsoft.SqlServer.Management.XEvent.PredValue -argumentlist "c:\temp.log"  
$compare = $store.Package0Package.PredCompareInfoSet["equal_i_unicode_string"]  
$predicate = new-object Microsoft.SqlServer.Management.XEvent.PredFunctionExpr -ArgumentList $compare, $operand, $value  
$event.SetPredicate($predicate)  
$session.Create()  
```  
  
## <a name="security"></a>Security  
 Zum Erstellen, Ändern oder Löschen einer Sitzung für erweiterte Ereignisse müssen Sie über die ALTER ANY EVENT SESSION-Berechtigung verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)   
 [Verwenden der system_health-Sitzung](use-the-ssms-xe-profiler.md)   
 [Tools für erweiterte Ereignisse](extended-events-tools.md)  
