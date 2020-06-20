---
title: Konvertieren von URNs in SQL Server-Anbieterpfade | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3160e5e6a70344d0340b0b14db822c7089b60680
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934571"
---
# <a name="convert-urns-to-sql-server-provider-paths"></a>Konvertieren von URNs in SQL Server-Anbieterpfade
  Das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Object-Modell (SMO-Modell) erstellt einheitliche Ressourcennamen (Uniform Resource Names, URN) für seine Objekte. Jeder URN identifiziert eindeutig ein SMO-Objekt und kann mit dem `Convert-UrnToPath`-Cmdlet in einen SQL Server PowerShell-Anbieterpfad konvertiert werden.  
  
## <a name="converting-urns-to-paths"></a>Konvertieren von URNs in Pfade  
 Jeder URN weist die gleichen Informationen wie einen Pfad zum Objekt auf, aber in einer anderen Form. Dies ist beispielsweise der Pfad zu einer Tabelle:  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 Und dies ist die URN zum gleichen Objekt:  
  
 Server [@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' und @Schema='Person']  
  
 Wenn Sie in einem PowerShell-Skript ein SMO-Objekt erstellt haben, können Sie auf die `Urn`-Eigenschaft verweisen, um den URN für das Objekt abzurufen. Anschließend können Sie das `Convert-UrnToPath`-Cmdlet verwenden, um die SMO-URN-Zeichenfolge in einen Windows PowerShell-Pfad zu konvertieren. Sie können dann mithilfe des Anbieters zu anderen Positionen im Pfad navigieren.  
  
 Wenn Knotennamen erweiterte Zeichen enthalten, die in Windows PowerShell-Pfadnamen nicht unterstützt werden, codiert `Convert-UrnToPath` sie in ihrer hexadezimalen Darstellung. Zum Beispiel wird "Meine:Tabelle" als "Meine%3ATabelle" zurückgegeben.  
  
 Führen Sie Folgendes aus, um Beispiele für die Verwendung des Cmdlet in Windows PowerShell zu erhalten:  
  
```powershell
Get-Help Convert-UrnToPath -Examples  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abfrage Ausdrücke und Uniform Resource Names](../powershell/query-expressions-and-uniform-resource-names.md)   
 [SQL Server PowerShell Anbieter](../powershell/sql-server-powershell-provider.md)   
 [SQL Server-PowerShell](../powershell/sql-server-powershell.md)  
