---
title: Zuordnen von CLR-Parameterdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: clr
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SqlBinary data type
- SqlInt16 data type
- SqlMoney data type
- SqlString data type
- SqlSingle data type
- data types [CLR integration]
- SqlInt64 data type
- SqlDateTime data type
- SqlXml data type
- SqlBoolean data type
- SqlDecimal data type
- SqlBytes data type
- mapping data types [CLR integration]
- SqlChars data type
- SqlInt32 data type
ms.assetid: 89b43ee9-b9ad-4281-a4bf-c7c8d116daa2
caps.latest.revision: 71
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e17baf04677e0f87e24ed0f4bd891361f146acf5
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37357812"
---
# <a name="mapping-clr-parameter-data"></a>Zuordnen von CLR-Parameterdaten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die folgende Tabelle enthält [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen, deren Entsprechungen in der common Language Runtime (CLR) für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die **System.Data.SqlTypes** -Namespace und ihre systemeigenen CLR-Entsprechungen in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
||||  
|-|-|-|  
|**SQL Server-Datentyp**|Typ (in System.Data.SqlTypes oder Microsoft.SqlServer.Types)|**CLR-Datentyp ((.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, auf NULL festlegbare\<Int64 >**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**bit**|**Gibt den anbieterspezifischen Datentyp der Spalte auf der Grundlage der  **Schlüsselwort in der Verbindungszeichenfolge.**|**Boolesch, auf NULL festlegbare\<booleschen >**|  
|**char**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**Cursor**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**Datum**|**SqlDateTime**|**"DateTime", auf NULL festlegbare\<"DateTime" >**|  
|**datetime**|**SqlDateTime**|**"DateTime", auf NULL festlegbare\<"DateTime" >**|  
|**datetime2**|InclusionThresholdSetting|**"DateTime", auf NULL festlegbare\<"DateTime" >**|  
|**DATETIMEOFFSET**|**Keine**|**"DateTimeOffset", auf NULL festlegbare\<DateTimeOffset >**|  
|**decimal**|**SqlDecimal**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**float**|**SqlDouble**|**Doppelte, auf NULL festlegbar\<Double >**|  
|**geography**|**"Sqlgeography"**<br /><br /> **"Sqlgeography"** ist definiert in "Microsoft.SqlServer.Types.dll", die mit SQL Server installiert ist und heruntergeladen werden kann die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|InclusionThresholdSetting|  
|**Geometrie**|**"Sqlgeometry"**<br /><br /> **"Sqlgeometry"** ist definiert in "Microsoft.SqlServer.Types.dll", die mit SQL Server installiert ist und heruntergeladen werden kann die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|InclusionThresholdSetting|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** ist definiert in "Microsoft.SqlServer.Types.dll", die mit SQL Server installiert ist und heruntergeladen werden kann die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|InclusionThresholdSetting|  
|**image**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**int**|**SqlInt32**|**Int32, auf NULL festlegbare\<Int32 >**|  
|**money**|**Wenn die Spalte einen benutzerdefinierten Typ (UDT) ist, ist dies der qualifizierte Name UDTs-Assembly gemäß **.**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**numeric**|**SqlDecimal**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SQLChars** ist eine bessere Übereinstimmung für Datenübertragungen und Datenzugriff, und **SQLString** ist eine bessere Übereinstimmung für Zeichenfolge-Vorgänge.|**String, Char[]**|  
|**nvarchar(1), nchar(1)-Wert**|**SqlChars, SqlString**|**Char-Zeichen, String, Char [], Nullable\<Char >**|  
|**real**|**SqlSingle** (den Bereich der **SqlSingle**, jedoch ist größer als **echte**)|**Einzelne, auf NULL festlegbar\<einzelne >**|  
|**rowversion**|InclusionThresholdSetting|**Byte[]**|  
|**smallint**|**SqlInt16**|**Int16-Wert, auf NULL festlegbare\<Int16 >**|  
|**smallmoney**|**Wenn die Spalte einen benutzerdefinierten Typ (UDT) ist, ist dies der qualifizierte Name UDTs-Assembly gemäß **.**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**sql_variant**|InclusionThresholdSetting|**Objekt**|  
|**table**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**text**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**Uhrzeit**|InclusionThresholdSetting|**TimeSpan, auf NULL festlegbare\<TimeSpan >**|  
|**timestamp**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**tinyint**|**SqlByte**|**Byte, auf NULL festlegbare\<Byte >**|  
|**uniqueidentifier**|**SqlGuid**|**GUID, die NULL-Werte zulassen\<Guid >**|  
|**Eine benutzerdefinierte type(UDT)**|InclusionThresholdSetting|Dieselbe Klasse, die in derselben Assembly oder einer abhängigen Assembly an den benutzerdefinierten Typ gebunden ist.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**varbinary(1), binary(1)**|**SqlBytes, SqlBinary**|**Byte, Byte [], Nullable\<Byte >**|  
|**varchar**|InclusionThresholdSetting|InclusionThresholdSetting|  
|**xml**|**SqlXml**|InclusionThresholdSetting|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Automatische Datentypkonvertierung mit Out-Parametern  
 Eine CLR-Methode kann Zurückgeben von Informationen an den aufrufenden Code oder Programms markieren einen Eingabeparameter mit dem **out** Modifizierer (Microsoft Visual c#) oder  **\<Out() > ByRef** (Microsoft Visual Basic) Ist der Eingabeparameter ein CLR-Datentyp in der **System.Data.SqlTypes** -Namespace und das aufrufende Programm gibt an, dessen Entsprechung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp als Eingabeparameter, erfolgt automatisch, eine typkonvertierung Wenn die CLR-Methode für den Datentyp zurückgegeben.  
  
 Beispielsweise weist die folgende CLR-gespeicherte Prozedur einen Eingabeparameter des **SqlInt32** CLR-Datentyp, der mit markierten **out** (c#) oder  **\<Out() > ByRef** () Visual Basic):  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ … }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
…  
End Sub  
```  
  
 Nachdem die Assembly erstellt und in der Datenbank erstellt wird, wird die gespeicherte Prozedur erstellt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem folgenden Transact-SQL, die angibt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp **Int** als OUTPUT-Parameter:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Wenn die CLR-gespeicherte Prozedur wird aufgerufen, die **SqlInt32** Datentyp automatisch in konvertiert eine **Int** -Datentyp, und an das aufrufende Programm zurückgegeben.  
  
 Allerdings können nicht alle CLR-Datentypen automatisch durch einen Out-Parameter in ihre entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen konvertiert werden. In der folgenden Tabelle werden diese Ausnahmen aufgeführt.  
  
|||  
|-|-|  
|**CLR-Datentyp (SQL Server)**|**SQL Server-Datentyp**|  
|**Dezimalzahl**|SMALLMONEY|  
|**Wenn die Spalte einen benutzerdefinierten Typ (UDT) ist, ist dies der qualifizierte Name UDTs-Assembly gemäß **.**|SMALLMONEY|  
|**Dezimalzahl**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Hinzugefügt **"sqlgeography"**, **"sqlgeometry"**, und **SqlHierarchyId** Typen, um der Zuordnungstabelle.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
