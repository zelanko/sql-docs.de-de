---
title: Importieren des SQLPS-Moduls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 303d4cb75ad678ddd0c0f49e204566fc8a0d2c2c
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66064730"
---
# <a name="import-the-sqlps-module"></a>Importieren des SQLPS-Moduls
  Es wird empfohlen, zur Verwaltung von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] über PowerShell das `sqlps`-Modul in eine Windows PowerShell 2.0-Umgebung zu importieren. Das Modul lädt und registriert die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Snap-Ins und -Verwaltbarkeitsassemblys.  
  
1.  **Vorbereitungen:**  [Sicherheit](#Security)  
  
2.  **Das Modul zu laden:**  [Laden des Sqlps-Moduls](#LoadSqlps)  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Nach dem Importieren des `sqlps`-Moduls in Windows PowerShell stehen Ihnen folgende Möglichkeiten zur Verfügung:  
  
-   Interaktives Ausführen von Windows PowerShell-Befehlen  
  
-   Ausführen von Windows PowerShell-Skriptdateien  
  
-   Ausführen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Cmdlets  
  
-   Verwenden Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieterpfade, um durch die Hierarchie der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte zu navigieren.  
  
-   Verwenden Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Verwaltbarkeit-Objektmodelle (z. B. Microsoft.SqlServer.Management.Smo), um [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte zu verwalten.  
  
> [!NOTE]  
>  Die in den Namen von zwei SQL Server-Cmdlets (`Encode-Sqlname` und `Decode-Sqlname`) verwendeten Verben entsprechen nicht den genehmigten Verben für Windows PowerShell 2.0. Dies hat keine Auswirkungen auf den Vorgang, aber von Windows PowerShell wird eine Warnung ausgegeben, wenn das `sqlps`-Modul in eine Sitzung importiert wird.  
  
###  <a name="Security"></a> Sicherheit  
 Standardmäßig wird Windows PowerShell mit auf **Restricted**festgelegter Skriptausführungsrichtlinie ausgeführt. Dadurch wird die Ausführung von Windows PowerShell-Skripts verhindert. Zum Laden des `sqlps`-Moduls können Sie das `Set-ExecutionPolicy`-Cmdlet verwenden, um die Ausführung signierter Skripts oder beliebiger anderer Skripts zu ermöglichen. Führen Sie nur Skripts aus vertrauenswürdigen Quellen aus, und sichern Sie alle Eingabe- und Ausgabedateien, indem Sie die geeigneten NTFS-Berechtigungen verwenden. Weitere Informationen zum Aktivieren von Windows PowerShell-Skripts finden Sie unter [Ausführen der Windows PowerShell-Skripts](https://docs.microsoft.com/powershell/scripting/setup/starting-windows-powershell?view=powershell-6#how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows).  
  
##  <a name="LoadSqlps"></a> Laden des sqlps-Moduls  
 **So laden Sie das sqlps-Modul in Windows PowerShell**  
  
1.  Verwenden Sie das `Set-ExecutionPolicy`-Cmdlet, um die entsprechende Skriptausführungsrichtlinie festzulegen.  
  
2.  Verwenden der `Import-Module` -Cmdlet zum Importieren des Sqlps-Moduls. Geben Sie den `DisableNameChecking`-Parameter an, wenn Sie die Warnung zu `Encode-Sqlname` und `Decode-Sqlname` unterdrücken möchten.  
  
### <a name="example-powershell"></a>Beispiel (PowerShell)  
 In diesem Beispiel wird das `sqlps`-Modul bei deaktivierter Namensüberprüfung geladen.  
  
```  
## Import the SQL Server Module.  
  
Import-Module "sqlps" -DisableNameChecking  
  
```  
  

  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-PowerShell](../powershell/sql-server-powershell.md)   
 [SQL Server PowerShell-Anbieter](../powershell/sql-server-powershell-provider.md)   
 [Verwenden der Datenbank-Engine-Cmdlets](../../2014/database-engine/use-the-database-engine-cmdlets.md)  
  
  
