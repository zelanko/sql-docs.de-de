---
title: Importieren des SQLPS-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e687fd8c7fcd7c21f8aac9b546492a8f9bd4a644
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48077240"
---
# <a name="import-the-sqlps-module"></a>Importieren des SQLPS-Moduls
  Es wird empfohlen, zur Verwaltung von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] über PowerShell das `sqlps`-Modul in eine Windows PowerShell 2.0-Umgebung zu importieren. Das Modul lädt und registriert die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Snap-Ins und -Verwaltbarkeitsassemblys.  
  
1.  **Vorbereitungen:** [Sicherheit](#Security)  
  
2.  **So laden Sie das Modul:**  [Laden des sqlps-Moduls](#LoadSqlps)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Nach dem Importieren des `sqlps`-Moduls in Windows PowerShell stehen Ihnen folgende Möglichkeiten zur Verfügung:  
  
-   Interaktives Ausführen von Windows PowerShell-Befehlen  
  
-   Ausführen von Windows PowerShell-Skriptdateien  
  
-   Ausführen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Cmdlets  
  
-   Verwenden Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieterpfade, um durch die Hierarchie der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte zu navigieren.  
  
-   Verwenden Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Verwaltbarkeit-Objektmodelle (z. B. Microsoft.SqlServer.Management.Smo), um [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte zu verwalten.  
  
> [!NOTE]  
>  Die in den Namen von zwei SQL Server-Cmdlets (`Encode-Sqlname` und `Decode-Sqlname`) verwendeten Verben entsprechen nicht den genehmigten Verben für Windows PowerShell 2.0. Dies hat keine Auswirkungen auf den Vorgang, aber Windows PowerShell gibt eine Warnung bei der `sqlps` -Modul in eine Sitzung importiert wird.  
  
###  <a name="Security"></a> Sicherheit  
 Standardmäßig wird Windows PowerShell mit auf **Restricted**festgelegter Skriptausführungsrichtlinie ausgeführt. Dadurch wird die Ausführung von Windows PowerShell-Skripts verhindert. Zum Laden des `sqlps`-Moduls können Sie das `Set-ExecutionPolicy`-Cmdlet verwenden, um die Ausführung signierter Skripts oder beliebiger anderer Skripts zu ermöglichen. Führen Sie nur Skripts aus vertrauenswürdigen Quellen aus, und sichern Sie alle Eingabe- und Ausgabedateien, indem Sie die geeigneten NTFS-Berechtigungen verwenden. Weitere Informationen zum Aktivieren von Windows PowerShell-Skripts finden Sie unter [Ausführen der Windows PowerShell-Skripts](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx).  
  
##  <a name="LoadSqlps"></a> Laden des sqlps-Moduls  
 **So laden Sie das sqlps-Modul in Windows PowerShell**  
  
1.  Verwenden der `Set-ExecutionPolicy` Cmdlet, um die entsprechende Skriptausführungsrichtlinie festzulegen.  
  
2.  Verwenden der `Import-Module` -Cmdlet zum Importieren des Sqlps-Moduls. Geben Sie die `DisableNameChecking` -Parameters, wenn Sie die Warnung zu unterdrücken möchten `Encode-Sqlname` und `Decode-Sqlname`.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 In diesem Beispiel wird das `sqlps`-Modul bei deaktivierter Namensüberprüfung geladen.  
  
```  
## Import the SQL Server Module.  
  
Import-Module “sqlps” -DisableNameChecking  
  
```  
  

  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-PowerShell](../powershell/sql-server-powershell.md)   
 [SQL Server PowerShell-Anbieter](../powershell/sql-server-powershell-provider.md)   
 [Verwenden der Datenbank-Engine-Cmdlets](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
  
  
