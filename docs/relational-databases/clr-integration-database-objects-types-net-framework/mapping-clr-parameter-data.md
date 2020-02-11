---
title: Mapping von CLR-Parameter Daten | Microsoft-Dokumentation
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
ms.openlocfilehash: 530db4d31d3db4773713816f1b68404990997512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081313"
---
# <a name="mapping-clr-parameter-data"></a>Zuordnen von CLR-Parameterdaten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In der folgenden Tabelle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind die-Datentypen, ihre Entsprechungen in der Common Language Runtime ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR) für im **System. Data. SqlTypes** -Namespace und ihre systemeigenen CLR-Entsprechungen in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework aufgelistet.  
  
||||  
|-|-|-|  
|**SQL Server-Datentyp**|Typ (in System.Data.SqlTypes oder Microsoft.SqlServer.Types)|**CLR-Datentyp (.NET Framework)**|  
|**BIGINT**|**SqlInt64**|**Int64, Nullable\<Int64>**|  
|**BINARY**|**SqlBytes, SqlBinary**|**Byte []**|  
|**bit**|**SqlBoolean**|**Boolescher Wert, auf\<NULL festleg barer boolescher>**|  
|**Char**|Keine|Keine|  
|**Hand**|Keine|Keine|  
|**date**|**SqlDateTime**|**DateTime, auf NULL\<festleg Bare DateTime->**|  
|**datetime**|**SqlDateTime**|**DateTime, auf NULL\<festleg Bare DateTime->**|  
|**datetime2**|Keine|**DateTime, auf NULL\<festleg Bare DateTime->**|  
|**DATETIMEOFFSET**|**Keine**|**DateTimeOffset, auf NULL\<festleg Bare DateTimeOffset->**|  
|**Decimal**|**SqlDecimal**|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|**float**|**SqlDouble**|**Double, auf NULL\<festleg Bare doppelte>**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** wird in der Datei Microsoft. SqlServer. types. dll definiert, die mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**Geometrie**|**SqlGeometry**<br /><br /> **SqlGeometry** ist in der Datei Microsoft. SqlServer. types. dll definiert, die mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** ist in der Datei Microsoft. SqlServer. types. dll definiert, die mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**Klang**|Keine|Keine|  
|**int**|**SqlInt32**|**Int32, Nullable\<Int32>**|  
|**money**|**SqlMoney**|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|Keine|Keine|  
|**isch**|**SqlDecimal**|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SqlChars** eignet sich besser für die Datenübertragung und den Zugriff, und **SqlString** ist eine bessere Entsprechung für die Durchführung von Zeichen folgen Vorgängen.|**String, Char[]**|  
|**nvarchar (1), nchar (1)**|**SqlChars, SqlString**|**Char, String, Char [], NULL-\<Werte zulassen char>**|  
|**wirkliche**|**SqlSingle** (der Bereich von **SqlSingle**ist jedoch größer als **real**).|**Single>, die\<NULL-Werte zulassen**|  
|**rowversion**|Keine|**Byte []**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16>**|  
|**SMALLMONEY**|**SqlMoney**|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|**sql_variant**|Keine|**Object**|  
|**glaub**|Keine|Keine|  
|**text**|Keine|Keine|  
|**time**|Keine|**TimeSpan, Nullable\<TimeSpan>**|  
|**timestamp**|Keine|Keine|  
|**tinyint**|**SqlByte**|**Byte, NULL-\<Werte zulassen>**|  
|**uniqueidentifier**|**SqlGuid**|**GUID, auf NULL\<festleg Bare GUID>**|  
|**Benutzerdefinierter Typ (User-Defined Type, UDT)**|Keine|Dieselbe Klasse, die in derselben Assembly oder einer abhängigen Assembly an den benutzerdefinierten Typ gebunden ist.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**varbinary (1), binär (1)**|**SqlBytes, SqlBinary**|**Byte, Byte [], auf NULL\<festleg Bare Byte>**|  
|**varchar**|Keine|Keine|  
|**basi**|**SQLXML**|Keine|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Automatische Datentypkonvertierung mit Out-Parametern  
 Eine CLR-Methode kann Informationen an den aufrufenden Code bzw. das aufrufende Programm zurückgeben, indem Sie einen Eingabeparameter mit dem **out** -Modifizierer (Microsoft Visual c#) oder ** \<out () > ByRef** (Microsoft Visual Basic) kennzeichnet, wenn der Eingabeparameter ein CLR-Datentyp im **System ist. der Data. SqlTypes** -Namespace, und das aufrufende Programm gibt seinen äquivalenten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp als Eingabeparameter an. eine Typkonvertierung erfolgt automatisch, wenn die CLR-Methode den-Datentyp zurückgibt.  
  
 Beispielsweise verfügt die folgende gespeicherte CLR-Prozedur über einen Eingabeparameter des **SqlInt32** CLR-Datentyps, der mit **out** (c#) oder ** \<out () > ByRef** (Visual Basic) gekennzeichnet ist:  
  
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
  
 Nachdem die Assembly erstellt und in der Datenbank erstellt wurde, wird die gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem folgenden Transact-SQL-Code erstellt, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den Datentyp **int** als Ausgabeparameter angibt:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Wenn die gespeicherte CLR-Prozedur aufgerufen wird, wird der **SqlInt32** -Datentyp automatisch in einen **int** -Datentyp konvertiert und an das aufrufende Programm zurückgegeben.  
  
 Allerdings können nicht alle CLR-Datentypen automatisch durch einen Out-Parameter in ihre entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen konvertiert werden. In der folgenden Tabelle werden diese Ausnahmen aufgeführt.  
  
|||  
|-|-|  
|**CLR-Datentyp (SQL Server)**|**SQL Server-Datentyp**|  
|**Mierte**|SMALLMONEY|  
|**SqlMoney**|SMALLMONEY|  
|**Decimal**|money|  
|**DateTime**|smalldatetime|  
|**SQLDateTime**|smalldatetime|  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Der Zuordnungstabelle wurden die Typen **SqlGeography**, **SqlGeometry**und **SqlHierarchyId** hinzugefügt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
