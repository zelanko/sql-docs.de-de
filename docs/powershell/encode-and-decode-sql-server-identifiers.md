---
title: Codierung und Decodierung von SQL Server-Bezeichnern | Microsoft-Dokumentation
description: Einige Zeichen können in den Begrenzungsbezeichnern von SQL Server enthalten sein, die in Windows PowerShell-Pfaden nicht unterstützt werden. Hier erfahren Sie, wie Sie diese einschließen, indem Sie sie mit ihren hexadezimalen Werten darstellen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: bb9fe0d3-e432-42d3-b324-64dc908b544a
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 54ecf5fc3205ce3648f4783f846dd5954df684e9
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919138"
---
# <a name="encode-and-decode-sql-server-identifiers"></a>Codierung und Decodierung von SQL Server-Bezeichnern
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Begrenzungsbezeichner von SQL Server können Zeichen enthalten, die in Windows PowerShell-Pfaden nicht unterstützt werden. Diese Zeichen können angegeben werden, indem ihre Hexadezimalwerte codiert werden.  

> [!NOTE]
> Es gibt zwei SQL Server PowerShell-Module: **SqlServer** und **SQLPS**. Das **SQLPS**-Modul ist zwar in der SQL Server-Installation (für die Abwärtskompatibilität) enthalten, wird jedoch nicht mehr aktualisiert. Das **SqlServer**-Modul ist das aktuellste PowerShell-Modul. Das **SqlServer**-Modul enthält aktualisierte Versionen der Cmdlets in **SQLPS** sowie neue Cmdlets zur Unterstützung der neuesten SQL-Funktionen.  
> Vorherige Versionen des **SqlServer**-Moduls *waren* in SQL Server Management Studio (SSMS) enthalten, allerdings nur in den Versionen 16.x. Das **SqlServer**-Modul muss über den PowerShell-Katalog installiert werden, damit PowerShell mit SSMS 17.0 und höher verwendet werden kann.
> Informationen zur Installation des **SqlServer**-Moduls finden Sie unter [Installieren von SQL Server PowerShell](download-sql-server-ps-module.md).
  
  
Zeichen, die nicht in Windows PowerShell-Pfadnamen unterstützt werden, können als "%"-Zeichen gefolgt vom Hexadezimalwert des Bitmusters, das das Zeichen darstellt, dargestellt oder codiert werden (Beispiel: **%** xx). Codierung kann immer zur Verarbeitung von Zeichen verwendet werden, die in Windows PowerShell-Pfaden nicht unterstützt werden.  
  
 Das Cmdlet **Encode-SqlName** verwendet als Eingabe einen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Bezeichner. Es gibt eine Zeichenfolge mit allen nicht von der Windows PowerShell-Sprache unterstützten Zeichen, die mit "%xx" codiert sind, aus. Das Cmdlet **Decode-SqlName** verwendet einen codierten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Bezeichner als Eingabe und gibt den ursprünglichen Bezeichner zurück.  
  
##  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Einschränkungen  
 Die Cmdlets **Encode-Sqlname** und **Decode-Sqlname** codieren oder decodieren nur die Zeichen, die in SQL Server-Begrenzungsbezeichnern zulässig sind, aber in PowerShell-Pfaden nicht unterstützt werden. Im Folgenden werden die Zeichen aufgeführt, die von **Encode-SqlName** codiert und von **Decode-SqlName** decodiert werden:  
  
|||||||||||||  
|-|-|-|-|-|-|-|-|-|-|-|-|  
|**Zeichen**|\ |/|:|%|\<|>|*|?|[|]|&#124;|  
|**Hexadezimale Codierung**|%5C|%2F|%3A|%25|%3C|%3E|%2A|%3F|%5B|%5D|%7C|  
  
##  <a name="encoding-an-identifier"></a><a name="EncodeIdent"></a> Codieren eines Bezeichners  
 **So codieren Sie einen SQL Server-Bezeichner in einem PowerShell-Pfad**  
  
-   Codieren Sie mithilfe einer der folgenden beiden Methoden einen SQL Server-Bezeichner:  
  
    -   Geben Sie den Hexadezimalcode für das nicht unterstützte Zeichen an, indem Sie die Syntax % XX verwenden, wobei XX der Hexadezimalcode ist.  
  
    -   Übergeben Sie den Bezeichner als Zeichenfolge in Anführungszeichen an das Cmdlet **Encode-Sqlname** .  
  
### <a name="examples-encoding"></a>Beispiele (Codierung)  
 In diesem Beispiel wird die codierte Version des Zeichens ":" (%3A) dargestellt:  
  
```  
Set-Location Table%3ATest  
```  
  
 Alternativ können Sie **Encode-SqlName** verwenden, um einen von Windows PowerShell unterstützten Namen zu erstellen:  
  
```  
Set-Location (Encode-SqlName "Table:Test")  
```  
  
##  <a name="decoding-an-identifier"></a><a name="DecodeIdent"></a> Decodieren eines Bezeichners  
 **So decodieren Sie einen SQL Server-Bezeichner aus einem PowerShell-Pfad**  
  
 Verwenden Sie das Cmdlet **Decode-Sqlname** , um die Hexadezimalcodierungen durch die von der Codierung dargestellten Zeichen zu ersetzen.  
  
### <a name="examples-decoding"></a>Beispiele (Decodierung)  
 Dieses Beispiel gibt „Table:Test“ zurück:  
  
```  
Decode-SqlName "Table%3ATest"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Bezeichnern in PowerShell](sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell-Anbieter](sql-server-powershell-provider.md)   
 [SQL Server-PowerShell](sql-server-powershell.md)  
  
  
