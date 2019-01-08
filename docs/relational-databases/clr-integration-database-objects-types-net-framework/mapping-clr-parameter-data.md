---
title: Zuordnen von CLR-Parameterdaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9c4697d2dcbad80d1da0fd8ed6c81750ac90695b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52534126"
---
# <a name="mapping-clr-parameter-data"></a>Zuordnen von CLR-Parameterdaten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die folgende Tabelle enthält [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen, deren Entsprechungen in der common Language Runtime (CLR) für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die **System.Data.SqlTypes** -Namespace und ihre systemeigenen CLR-Entsprechungen in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework.  
  
||||  
|-|-|-|  
|**SQL Server-Datentyp**|Typ (in System.Data.SqlTypes oder Microsoft.SqlServer.Types)|**CLR-Datentyp ((.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, auf NULL festlegbare\<Int64 >**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**bit**|**SqlBoolean**|**Boolesch, auf NULL festlegbare\<booleschen >**|  
|**char**|None|None|  
|**Cursor**|None|None|  
|**Datum**|**SqlDateTime**|**"DateTime", auf NULL festlegbare\<"DateTime" >**|  
|**datetime**|**SqlDateTime**|**"DateTime", auf NULL festlegbare\<"DateTime" >**|  
|**datetime2**|None|**"DateTime", auf NULL festlegbare\<"DateTime" >**|  
|**DATETIMEOFFSET**|**Keine**|**"DateTimeOffset", auf NULL festlegbare\<DateTimeOffset >**|  
|**decimal**|**SqlDecimal**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**float**|**SqlDouble**|**Doppelte, auf NULL festlegbar\<Double >**|  
|**geography**|**"Sqlgeography"**<br /><br /> **"Sqlgeography"** ist definiert in "Microsoft.SqlServer.Types.dll", die mit SQL Server installiert ist und heruntergeladen werden kann die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**Geometrie**|**"Sqlgeometry"**<br /><br /> **"Sqlgeometry"** ist definiert in "Microsoft.SqlServer.Types.dll", die mit SQL Server installiert ist und heruntergeladen werden kann die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** ist definiert in "Microsoft.SqlServer.Types.dll", die mit SQL Server installiert ist und heruntergeladen werden kann die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).|None|  
|**image**|None|None|  
|**int**|**SqlInt32**|**Int32, auf NULL festlegbare\<Int32 >**|  
|**money**|**SqlMoney**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|None|None|  
|**numeric**|**SqlDecimal**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SQLChars** ist eine bessere Übereinstimmung für Datenübertragungen und Datenzugriff, und **SQLString** ist eine bessere Übereinstimmung für Zeichenfolge-Vorgänge.|**String, Char[]**|  
|**nvarchar(1), nchar(1)-Wert**|**SqlChars, SqlString**|**Char-Zeichen, String, Char [], Nullable\<Char >**|  
|**real**|**SqlSingle** (den Bereich der **SqlSingle**, jedoch ist größer als **echte**)|**Einzelne, auf NULL festlegbar\<einzelne >**|  
|**rowversion**|None|**Byte[]**|  
|**smallint**|**SqlInt16**|**Int16-Wert, auf NULL festlegbare\<Int16 >**|  
|**smallmoney**|**SqlMoney**|**Decimal, auf NULL festlegbar\<Decimal >**|  
|**sql_variant**|None|**Objekt**|  
|**table**|None|None|  
|**text**|None|None|  
|**Uhrzeit**|None|**TimeSpan, auf NULL festlegbare\<TimeSpan >**|  
|**timestamp**|None|None|  
|**tinyint**|**SqlByte**|**Byte, auf NULL festlegbare\<Byte >**|  
|**uniqueidentifier**|**SqlGuid**|**GUID, die NULL-Werte zulassen\<Guid >**|  
|**Eine benutzerdefinierte type(UDT)**|None|Dieselbe Klasse, die in derselben Assembly oder einer abhängigen Assembly an den benutzerdefinierten Typ gebunden ist.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**varbinary(1), binary(1)**|**SqlBytes, SqlBinary**|**Byte, Byte [], Nullable\<Byte >**|  
|**varchar**|None|None|  
|**xml**|**SqlXml**|None|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Automatische Datentypkonvertierung mit Out-Parametern  
 Eine CLR-Methode kann Zurückgeben von Informationen an den aufrufenden Code oder Programms markieren einen Eingabeparameter mit dem **out** Modifizierer (Microsoft Visual c#) oder  **\<Out() > ByRef** (Microsoft Visual Basic) Ist der Eingabeparameter ein CLR-Datentyp in der **System.Data.SqlTypes** -Namespace und das aufrufende Programm gibt an, dessen Entsprechung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp als Eingabeparameter, erfolgt automatisch, eine typkonvertierung Wenn die CLR-Methode für den Datentyp zurückgegeben.  
  
 Beispielsweise weist die folgende CLR-gespeicherte Prozedur einen Eingabeparameter des **SqlInt32** CLR-Datentyp, der mit markierten **out** (c#) oder  **\<Out() > ByRef** () Visual Basic):  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
\<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( \<Out()> ByRef value As SqlInt32)  
...  
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
|**SqlMoney**|SMALLMONEY|  
|**Dezimalzahl**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Hinzugefügt **"sqlgeography"**, **"sqlgeometry"**, und **SqlHierarchyId** Typen, um der Zuordnungstabelle.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
