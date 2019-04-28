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
ms.openlocfilehash: e0a7393a3b0547d37c5f69f4e75915f8706acf12
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62705620"
---
# <a name="use-the-powershell-provider-for-extended-events"></a>Verwenden des PowerShell-Anbieters für erweiterte Ereignisse
  Erweiterte Ereignisse von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Anbieters verwalten. Der Unterordner XEvent ist auf dem SQLSERVER-Laufwerk verfügbar. Auf diesen Ordner können Sie mit einer der folgenden Methoden zugreifen:  
  
-   Geben Sie an der Eingabeaufforderung `sqlps` ein, und drücken Sie dann die EINGABETASTE. Geben Sie `cd xevent` ein, und drücken Sie dann die EINGABETASTE. Von dort aus können Sie die **cd** und `dir` Befehle (oder **Set-Location** und **Get-Childitem** Cmdlets) zum Servernamen und Instanznamen wechseln.  
  
-   Erweitern Sie im Objekt-Explorer den Instanznamen, erweitern Sie **Verwaltung**, klicken Sie mit der rechten Maustaste auf **Erweiterte Ereignisse**, und klicken Sie anschließend auf **PowerShell starten**. Damit wird PowerShell unter dem folgenden Pfad gestartet:  
  
     PS SQLSERVER:\XEvent\\*Servername*\\*Instanzname*>  
  
    > [!NOTE]  
    >  PowerShell können Sie unter **Erweiterte Ereignisse**von jedem Knoten aus starten. Sie können z.B. mit der rechten Maustaste auf **Sitzungen**klicken und anschließend auf **PowerShell starten**klicken. Damit starten Sie PowerShell eine Ebene tiefer, mit dem Ordner Sitzungen.  
  
 Sie können die Struktur des Ordners "XEvent" nach vorhandenen Sitzungen für erweiterte Ereignisse und deren zugeordneten Ereignissen, Zielen und Prädikaten durchsuchen. Z. B. von der PS SQLServer: \xevent\\*ServerName*\\*InstanceName*> Pfad, falls das eingegebene `cd sessions`, EINGABETASTE drücken, `dir`, und klicken Sie dann die EINGABETASTE drücken, sehen Sie die Liste der in dieser Instanz gespeicherten Sitzungen. Sie können auch anzeigen, ob die Sitzung ausgeführt wird (und wenn dies der Fall ist, die bisherige Sitzungsdauer), sowie ob die Sitzung für den Start bei Instanzstart konfiguriert ist.  
  
 Wenn Sie die Ereignisse, deren Prädikate und die einer Sitzung zugeordneten Ziele anzeigen möchten, können Sie Verzeichnisse in den Sitzungsnamen ändern und dann den Ereignis- oder den Zielordner anzeigen. Beispielsweise, um anzuzeigen, die Ereignisse und deren Prädikate, die mit der Standard-systemintegritätssitzung, aus der PS SQLServer: \xevent verknüpft sind\\*ServerName*\\*InstanceName*\Sessions > Pfad, den Typ `cd system_health\events,` EINGABETASTE drücken, `dir`, und drücken Sie dann die EINGABETASTE.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -PowerShell-Anbieter ist ein leistungsstarkes Tool, mit dem Sie Sitzungen für erweiterte Ereignisse erstellen, ändern und verwalten können. Der folgende Abschnitt enthält einige einfache Beispiele für die Verwendung von PowerShell-Skripts mit erweiterten Ereignissen.  
  
## <a name="examples"></a>Beispiele  
 Achten Sie in den folgenden Beispielen auf Folgendes:  
  
-   Die Skripts ausgeführt werden müssen, von PS SQLSERVER:\\> Eingabeaufforderung (verfügbar `sqlps` an einer Eingabeaufforderung).  
  
-   Die Skripts verwenden die Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Die Skripts müssen mit der Erweiterung .ps1 gespeichert werden.  
  
-   In der PowerShell-Ausführungsrichtlinie muss das auszuführende Skript zugelassen sein. Verwenden Sie das Cmdlet **Set-Executionpolicy** , um die Ausführungsrichtlinie festzulegen. (Weitere Informationen erhalten Sie durch Eingabe von `get-help set-executionpolicy -detailed` und Drücken der EINGABETASTE.)  
  
 Mit dem folgenden Skript erstellen Sie die neue Sitzung "TestSession".  
  
```  
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = new-object Microsoft.SqlServer.Management.XEvent.Session -argumentlist $store, "TestSession"  
$event = $session.AddEvent("sqlserver.file_written")  
$event.AddAction("package0.callstack")  
$session.Create()  
```  
  
 Das folgende Skript fügt der im vorherigen Beispiel erstellten Sitzung das Ringpufferziel hinzu. (In diesem Beispiel wird die Verwendung der `Alter`-Methode veranschaulicht. Sie können das Ziel beim Erstellen der Sitzung hinzufügen.)  
  
```  
#Script to alter a session.  
cd XEvent  
$h = hostname  
cd $h  
cd DEFAULT\Sessions  
  
#Used to find the specified session.  
$session = dir|where {$_.Name -eq 'TestSession'}  
  
#Add the ring buffer target and call the Alter method.  
$session.AddTarget("package0.ring_buffer")  
$session.Alter()  
```  
  
 Mit dem folgenden Skript erstellen Sie eine neue Sitzung, in der ein Prädikatausdruck verwendet wird. In diesem Fall werden in der Sitzung Informationen gesammelt, die in die Datei „c:\temp.log“ geschrieben werden (über das Ereignis „sqlserver.file_written“).  
  
```  
#Script for creating a session.  
cd XEvent  
$h = hostname  
cd $h  
  
#Use the default instance.  
$store = dir | where {$_.DisplayName -ieq 'default'}  
$session = new-object Microsoft.SqlServer.Management.XEvent.Session -argumentlist $store, "TestSession2"  
$event = $session.AddEvent("sqlserver.file_written")  
  
#Construct a predicate "equal_i_unicode_string(path, N'c:\temp.log')".  
$column = $store.SqlServerPackage.EventInfoSet["file_written"].DataEventColumnInfoSet["path"]  
$operand = new-object Microsoft.SqlServer.Management.XEvent.PredOperand -argumentlist $column  
$value = new-object Microsoft.SqlServer.Management.XEvent.PredValue -argumentlist "c:\temp.log"  
$compare = $store.Package0Package.PredCompareInfoSet["equal_i_unicode_string"]  
$predicate = new-object Microsoft.SqlServer.Management.XEvent.PredFunctionExpr -argumentlist $compare, $operand, $value  
$event.SetPredicate($predicate)  
$session.Create()  
```  
  
## <a name="security"></a>Sicherheit  
 Zum Erstellen, Ändern oder Löschen einer Sitzung für erweiterte Ereignisse müssen Sie über die ALTER ANY EVENT SESSION-Berechtigung verfügen.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-PowerShell](../../powershell/sql-server-powershell.md)   
 [Verwenden der system_health-Sitzung](use-the-ssms-xe-profiler.md)   
 [Tools für erweiterte Ereignisse](extended-events-tools.md)  
  
  
