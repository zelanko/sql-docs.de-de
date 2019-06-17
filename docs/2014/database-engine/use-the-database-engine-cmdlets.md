---
title: Verwenden des Datenbank-Engine-Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Convert-UrnToPath cmdlet
- PowerShell [SQL Server], cmdlets
- Cmdlets [SQL Server]
- PowerShell [SQL Server], Convert-UrnToPath
- Cmdlets [SQL Server], Convert-UrnToPath
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 720aa982-09ae-41a3-b603-a91004cfbe3e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 190b8f0ec6ac647ee45a07181af1bd7094199dcb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66088683"
---
# <a name="use-the-database-engine-cmdlets"></a>Verwenden der Datenbank-Engine-Cmdlets
  Windows PowerShell-Cmdlets sind Einzelfunktionsbefehle, für die i. d. R. eine Verb-Substantiv-Namenskonvention gilt, z. B. **Get-Help** oder **Set-MachineName**. Der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anbieter für Windows PowerShell bietet für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]spezifische Cmdlets.  
  
## <a name="database-engine-cmdlets"></a>Datenbank-Engine-Cmdlets  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] implementiert eine kleine Anzahl von Cmdlets für [!INCLUDE[ssDE](../includes/ssde-md.md)]. Diese Cmdlets werden hauptsächlich zum Ausführen vorhandener Transact-SQL-Skripts aus neuen PowerShell-Skripts, Auswerten richtlinienbasierter Verwaltungsrichtlinien und Unterstützen beim Angeben von SQL Server-Bezeichnern in SQL Server-Anbieterpfaden verwendet.  
  
 Bei den meisten Windows PowerShell-Skripts wird [!INCLUDE[ssDE](../includes/ssde-md.md)] genutzt. Hierbei kommen der SQL Server PowerShell-Anbieter und SQL Server-Verwaltbarkeits-Objektmodelle zum Einsatz. Weitere Informationen finden Sie unter [SQL Server PowerShell](../powershell/sql-server-powershell.md).  
  
### <a name="get-cmdlet-help"></a>Get-Help-Cmdlet  
 In der Windows PowerShell-Umgebung stellt das **Get-Help** -Cmdlet Hilfeinformationen für jedes Cmdlet bereit. **Get-Help** gibt Informationen wie Syntax, Parameterdefinitionen, Eingabe- und Ausgabetypen und eine Beschreibung der vom Cmdlet durchgeführten Aktion zurück. Weitere Informationen finden Sie unter [Get Help SQL Server PowerShell](../../2014/database-engine/get-help-sql-server-powershell.md).  
  
### <a name="partial-parameter-names"></a>Partielle Parameternamen  
 Sie müssen nicht den ganzen Namen eines Cmdlet-Parameters angeben. Sie müssen nur so viele Zeichen des Namens eingeben, dass dieser eindeutig von den anderen Parametern unterschieden werden kann, die von dem Cmdlet unterstützt werden. In diesen Beispielen werden drei Methoden zum Angeben des Parameters **Invoke-Sqlcmd-QueryTimeout** veranschaulicht:  
  
```  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTimeout 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryTime 3  
Invoke-Sqlcmd -Query "SELECT @@VERSION;" -QueryT 3  
```  
  
## <a name="database-engine-cmdlet-tasks"></a>Cmdlet-Tasks der Datenbank-Engine  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt die Verwendung von **Invoke-Sqlcmd** zum Ausführen von **sqlcmd** -Skripts oder -Befehlen, die [!INCLUDE[tsql](../includes/tsql-md.md)] - oder XQuery-Anweisungen enthalten. Die **sqlcmd** -Eingabe wird entweder als Zeichenfolgen-Eingabeparameter oder als Name einer zu öffnenden Skriptdatei akzeptiert.|[Invoke-Sqlcmd-Cmdlet](../../2014/database-engine/invoke-sqlcmd-cmdlet.md)|  
|Beschreibt die Verwendung von **Invoke-PolicyEvaluation** zum Melden, ob ein Zielsatz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Objekten den in richtlinienbasierten Verwaltungsrichtlinien definierten Bedingungen entspricht. Optional können mit dem Cmdlet alle festlegbaren Optionen in den Zielobjekten neu konfiguriert werden, die den Richtlinienbedingungen nicht entsprechen.|[Invoke-PolicyEvaluation-Cmdlet](../../2014/database-engine/invoke-policyevaluation-cmdlet.md)|  
|Beschreibt die Verwendung von `Encode-Sqlname` und `Decode-Sqlname` zum Verarbeiten von SQL Server-Bezeichnern, die in Windows PowerShell-Pfaden nicht unterstützte Zeichen enthalten.|[Codierung und Decodierung von SQL Server-Bezeichnern](../powershell/encode-and-decode-sql-server-identifiers.md)|  
|Beschreibt die Verwendung von `Convert-UrnToPath` zum Konvertieren eines URN (Uniform Resource Name, einheitlicher Name für Ressourcen) für SQL Server-Verwaltbarkeitsobjekte in den entsprechenden Pfad des SQL Server-Anbieters.|[Konvertieren von URNs in SQL Server-Anbieterpfade](../../2014/database-engine/convert-urns-to-sql-server-provider-paths.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server PowerShell-Anbieter](../powershell/sql-server-powershell-provider.md)   
 [SQL Server-PowerShell](../powershell/sql-server-powershell.md)   
 [Übersicht über die PowerShell-Cmdlets für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](availability-groups/windows/overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  
