---
title: sqlps-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1082bd587d9c3455733d611a676d901b62741859
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161601"
---
# <a name="sqlps-utility"></a>sqlps (Hilfsprogramm)
  Das Hilfsprogramm `sqlps` startet eine Windows PowerShell 2.0-Sitzung mit geladenem und registriertem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-PowerShell-Anbieter sowie geladenen und registrierten Cmdlets. Sie können PowerShell-Befehle oder -Skripts eingeben, die die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -PowerShell-Komponenten verwenden, sodass Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und ihre Objekte verwendet werden können.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen das `sqlps`-PowerShell-Modul. Weitere Informationen zu den `sqlps` -Modul finden Sie unter [Importieren des SQLPS-Moduls](../database-engine/import-the-sqlps-module.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -argsargument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a>Argumente  
 **-NoLogo**  
 Gibt an, dass beim Start des Hilfsprogramms `sqlps` die Copyrightinformationen ausgeblendet werden.  
  
 **-NoExit**  
 Gibt an, dass das Hilfsprogramm `sqlps` weiter ausgeführt wird, nachdem die Startbefehle abgeschlossen wurden.  
  
 **-NoProfile**  
 Gibt an, dass das Hilfsprogramm `sqlps` kein Benutzerprofil lädt. In Benutzerprofilen werden häufig verwendete Aliase, Funktionen und Variablen zur Verwendung in mehreren PowerShell-Sitzungen aufgezeichnet.  
  
 **-OutPutFormat** { **Text** | **XML** }  
 Gibt an, dass die `sqlps` Ausgabe des Hilfsprogramms formatiert werden entweder als Textzeichenfolgen (**Text**) oder in einem serialisierten CLIXML-Format (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Gibt an, die Eingabe in die `sqlps` Hilfsprogramm formatiert ist entweder als Textzeichenfolgen (**Text**) oder in einem serialisierten CLIXML-Format (**XML**).  
  
 **-Command**  
 Gibt den Befehl an, der vom Hilfsprogramm `sqlps` ausgeführt werden soll. Die `sqlps` Hilfsprogramm ausgeführt wird, den Befehl und dann beendet, es sei denn, **- NoExit** ist ebenfalls angegeben. Geben Sie nach **-Command**keine anderen Schalter an, denn diese werden als Befehlsparameter gelesen.  
  
 **-**  
 **-Command-** gibt an, dass die `sqlps` Hilfsprogramm, um die Eingabe aus der Standardeingabe lesen.  
  
 *script_block* [ **-args***argument_array* ]  
 Gibt einen Block von PowerShell-Befehlen an, die ausgeführt werden sollen. Der Block muss in geschweifte Klammern ({}) eingeschlossen werden. *Script_block* kann nur angegeben werden, wenn die `sqlps` Hilfsprogramm heißt entweder **PowerShell** oder einem anderen `sqlps` Sitzung des Hilfsprogramms. *Argument_array* ist ein Array von PowerShell-Variablen, das die Argumente für die PowerShell-Befehle in *script_block*enthält.  
  
 *string* [ *command_parameters* ]  
 Gibt eine Zeichenfolge an, die die auszuführenden PowerShell-Befehle enthält. Verwenden Sie das Format **"& {*`command`*}"**. Die Anführungszeichen geben eine Zeichenfolge an, und der Aufrufoperator (&) bewirkt, dass das Hilfsprogramm `sqlps` den Befehl ausführt.  
  
 [ **-?** | **-Help** ]  
 Zeigt eine Syntaxzusammenfassung der Optionen des Hilfsprogramms `sqlps` an.  
  
## <a name="remarks"></a>Hinweise  
 Die `sqlps` Dienstprogramm startet die PowerShell-Umgebung (PowerShell.exe) und lädt die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Modul. Das Modul, das auch mit dem Namen `sqlps`, lädt und registriert diese [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Snap-ins:  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Implementiert den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -PowerShell-Anbieter und zugeordnete Cmdlets, z. B. **Encode-SqlName** und **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Implementiert die Cmdlets **Invoke-Sqlcmd** und **Invoke-PolicyEvaluation** .  
  
 Das Hilfsprogramm `sqlps` kann für die folgenden Tasks verwendet werden:  
  
-   Interaktives Ausführen von PowerShell-Befehlen  
  
-   Ausführen von PowerShell-Skriptdateien  
  
-   Ausführen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Cmdlets  
  
-   Verwenden Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieterpfade, um durch die Hierarchie der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte zu navigieren.  
  
 In der Standardeinstellung die `sqlps` Hilfsprogramm ausgeführt wird, mit die Skriptausführungsrichtlinie auf **Restricted**. Dadurch wird die Ausführung von PowerShell-Skripts verhindert. Mit dem Cmdlet **Set-ExecutionPolicy** können Sie die Ausführung signierter Skripts oder beliebiger anderer Skripts ermöglichen. Führen Sie nur Skripts aus vertrauenswürdigen Quellen aus, und sichern Sie alle Eingabe- und Ausgabedateien, indem Sie die geeigneten NTFS-Berechtigungen verwenden. Weitere Informationen zum Aktivieren von PowerShell-Skripts finden Sie unter [Ausführen der Windows PowerShell-Skripts](http://go.microsoft.com/fwlink/?LinkId=103166).  
  
 Die Version der `sqlps` -Hilfsprogramm [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] und [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] wurde als eine Windows PowerShell 1.0-Mini-Shell implementiert. Mini-Shells weisen bestimmte Einschränkungen auf; Benutzer können beispielsweise keine anderen als die von der Mini-Shell geladenen Snap-Ins laden. Diese Einschränkungen gelten nicht für die [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Version und höhere Versionen des Hilfsprogramms, die dahingehend geändert wurden, dass sie das `sqlps`-Modul verwenden.  
  
## <a name="examples"></a>Beispiele  
 **A. Ausführen des sqlps-Hilfsprogramms im interaktiven Standardmodus ohne Copyrightinformationen**  
  
```  
sqlps -NoLogo  
```  
  
 **B. Ausführen eines SQL Server PowerShell-Skripts über die Eingabeaufforderung**  
  
```  
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
 **C. Ausführen eines SQL Server PowerShell-Skripts über die Eingabeaufforderung und weitere Ausführung nach Abschluss des Skripts**  
  
```  
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server-PowerShell](../powershell/sql-server-powershell.md)  
  
  
