---
title: sqlps-Hilfsprogramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8ff96b99ee7982be89126e79687dbc8a2215f42f
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798138"
---
# <a name="sqlps-utility"></a>sqlps (Hilfsprogramm)
  Das Hilfsprogramm `sqlps` startet eine Windows PowerShell 2.0-Sitzung mit geladenem und registriertem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-PowerShell-Anbieter sowie geladenen und registrierten Cmdlets. Sie können PowerShell-Befehle oder -Skripts eingeben, die die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -PowerShell-Komponenten verwenden, sodass Instanzen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und ihre Objekte verwendet werden können.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen das `sqlps`-PowerShell-Modul. Weitere Informationen zum `sqlps`-Modul finden Sie unter [Importieren des sqlps-Moduls](../database-engine/import-the-sqlps-module.md).  
  
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
 Gibt an, dass die Ausgabe des `sqlps` Hilfsprogramms entweder als Text Zeichenfolgen (**Text**) oder in einem serialisierten CliXML-Format (**XML**) formatiert werden soll.  
  
 **-InPutFormat** { **Text** | **XML** }  
 Gibt an, dass die Eingabe für das `sqlps`-Hilfsprogramm entweder als Text Zeichenfolgen (**Text**) oder in einem serialisierten CliXML-Format (**XML**) formatiert ist.  
  
 **-Command**  
 Gibt den Befehl an, der vom Hilfsprogramm `sqlps` ausgeführt werden soll. Das Hilfsprogramm `sqlps` führt den Befehl aus und wird dann beendet, es sei denn, es ist auch " **-NoExit** " Geben Sie nach **-Command**keine anderen Schalter an, denn diese werden als Befehlsparameter gelesen.  
  
 **-**  
 **-Command-** gibt an, dass das `sqlps`-Hilfsprogramm die Eingabe aus der Standardeingabe gelesen hat.  
  
 *script_block* [ **-args**_argument_array_ ]  
 Gibt einen Block von PowerShell-Befehlen an, die ausgeführt werden sollen. Der Block muss in geschweifte Klammern ({}) eingeschlossen werden. *Script_block* können nur angegeben werden, wenn das `sqlps` Hilfsprogramm entweder von **PowerShell** oder einer anderen `sqlps` Utility-Sitzung aufgerufen wird. *Argument_array* ist ein Array von PowerShell-Variablen, das die Argumente für die PowerShell-Befehle in *script_block*enthält.  
  
 *string* [ *command_parameters* ]  
 Gibt eine Zeichenfolge an, die die auszuführenden PowerShell-Befehle enthält. Verwenden Sie das Format **"& { *`command`* }"** . Die Anführungszeichen geben eine Zeichenfolge an, und der Aufruf Operator (&) bewirkt, dass das Hilfsprogramm `sqlps` den Befehl ausführen.  
  
 [ **-?** |  **-Help** ]  
 Zeigt eine Syntaxzusammenfassung der Optionen des Hilfsprogramms `sqlps` an.  
  
## <a name="remarks"></a>Remarks  
 Das `sqlps`-Hilfsprogramm startet die PowerShell-Umgebung (PowerShell. exe) und lädt das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Modul. Das Modul, das auch `sqlps`benannt ist, lädt und registriert diese [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell-Snap-Ins:  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Implementiert den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -PowerShell-Anbieter und zugeordnete Cmdlets, z. B. **Encode-SqlName** und **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Implementiert die Cmdlets **Invoke-Sqlcmd** und **Invoke-PolicyEvaluation** .  
  
 Das Hilfsprogramm `sqlps` kann für die folgenden Tasks verwendet werden:  
  
-   Interaktives Ausführen von PowerShell-Befehlen  
  
-   Ausführen von PowerShell-Skriptdateien  
  
-   Ausführen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Cmdlets  
  
-   Verwenden Sie die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieterpfade, um durch die Hierarchie der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekte zu navigieren.  
  
 Standardmäßig wird das `sqlps`-Hilfsprogramm mit der Skript Ausführungs Richtlinie auf **restricted**festgelegt. Dadurch wird die Ausführung von PowerShell-Skripts verhindert. Mit dem Cmdlet **Set-ExecutionPolicy** können Sie die Ausführung signierter Skripts oder beliebiger anderer Skripts ermöglichen. Führen Sie nur Skripts aus vertrauenswürdigen Quellen aus, und sichern Sie alle Eingabe- und Ausgabedateien, indem Sie die geeigneten NTFS-Berechtigungen verwenden. Weitere Informationen zum Aktivieren von PowerShell-Skripts finden Sie unter [Ausführen der Windows PowerShell-Skripts](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/).  
  
 Die Version des Hilfsprogramms `sqlps` in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] und [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] wurde als Windows PowerShell 1.0-Mini-Shell implementiert. Mini-Shells weisen bestimmte Einschränkungen auf; Benutzer können beispielsweise keine anderen als die von der Mini-Shell geladenen Snap-Ins laden. Diese Einschränkungen gelten nicht für die [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Version und höhere Versionen des Hilfsprogramms, die dahingehend geändert wurden, dass sie das `sqlps`-Modul verwenden.  
  
## <a name="examples"></a>Beispiele  

### <a name="a-run-the-sqlps-utility-in-default-interactive-mode-without-the-copyright-banner"></a>A. Ausführen des Hilfsprogramms sqlps im interaktiven Standardmodus ohne Copyrightinformationen
  
```cmd
sqlps -NoLogo  
```  
  
### <a name="b-run-a-sql-server-powershell-script-from-the-command-prompt"></a>B. Ausführen eines SQL Server PowerShell-Skripts von der Eingabeaufforderung
  
```cmd
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
### <a name="c-run-a-sql-server-powershell-script-from-the-command-prompt-and-keep-running-after-the-script-completes"></a>C. Ausführen eines SQL Server PowerShell-Skripts von der Eingabeaufforderung und weitere Ausführung nach Abschluss des Skripts
  
```cmd
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren oder Deaktivieren eines Servernetzwerkprotokolls](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server-PowerShell](../powershell/sql-server-powershell.md)  
