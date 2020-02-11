---
title: Mapping von CLR-Parameter Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 17eeefbe125722c666f9f56394028da8c66a66b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75232282"
---
# <a name="mapping-clr-parameter-data"></a>Zuordnen von CLR-Parameterdaten
  In der folgenden Tabelle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind die-Datentypen, ihre Entsprechungen in der Common Language Runtime ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR `System.Data.SqlTypes` ) für im-Namespace und ihre systemeigenen CLR-Entsprechungen in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework aufgelistet.  
  
||||  
|-|-|-|  
|**SQL Server-Datentyp**|Typ (in System.Data.SqlTypes oder Microsoft.SqlServer.Types)|**CLR-Datentyp (.NET Framework)**|  
|`bigint`|`SqlInt64`|**Int64, Nullable\<Int64>**|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|**Boolescher Wert, auf\<NULL festleg barer boolescher>**|  
|`char`|Keine|Keine|  
|`cursor`|Keine|Keine|  
|`date`|`SqlDateTime`|**DateTime, auf NULL\<festleg Bare DateTime->**|  
|`datetime`|`SqlDateTime`|**DateTime, auf NULL\<festleg Bare DateTime->**|  
|`datetime2`|Keine|**DateTime, auf NULL\<festleg Bare DateTime->**|  
|`DATETIMEOFFSET`|`None`|**DateTimeOffset, auf NULL\<festleg Bare DateTimeOffset->**|  
|`decimal`|`SqlDecimal`|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|`float`|`SqlDouble`|**Double, auf NULL\<festleg Bare doppelte>**|  
|`geography`|`SqlGeography`<br /><br /> `SqlGeography`wird in der Datei Microsoft. SqlServer. types. dll definiert, die mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164)heruntergeladen werden kann.|Keine|  
|`geometry`|`SqlGeometry`<br /><br /> `SqlGeometry`wird in der Datei Microsoft. SqlServer. types. dll definiert, die mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164)heruntergeladen werden kann.|Keine|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> `SqlHierarchyId`wird in der Datei Microsoft. SqlServer. types. dll definiert, die mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=53164)heruntergeladen werden kann.|Keine|  
|`image`|Keine|Keine|  
|`int`|`SqlInt32`|**Int32, Nullable\<Int32>**|  
|`money`|`SqlMoney`|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|Keine|Keine|  
|`numeric`|`SqlDecimal`|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> 
  `SQLChars` bietet eine bessere Übereinstimmung für Datenübertragungen und Datenzugriff, und `SQLString` bietet eine bessere Übereinstimmung für die Durchführung von Zeichenfolgenvorgängen.|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|**Char, String, Char [], NULL-\<Werte zulassen char>**|  
|`real`|
  `SqlSingle` (der Bereich von `SqlSingle` ist jedoch größer als `real`)|**Single>, die\<NULL-Werte zulassen**|  
|`rowversion`|Keine|`Byte[]`|  
|`smallint`|`SqlInt16`|**Int16, Nullable\<Int16>**|  
|`smallmoney`|`SqlMoney`|**Decimal, NULL-\<Werte zulassen Dezimal>**|  
|`sql_variant`|Keine|`Object`|  
|`table`|Keine|Keine|  
|`text`|Keine|Keine|  
|`time`|Keine|**TimeSpan, Nullable\<TimeSpan>**|  
|`timestamp`|Keine|Keine|  
|`tinyint`|`SqlByte`|**Byte, NULL-\<Werte zulassen>**|  
|`uniqueidentifier`|`SqlGuid`|**GUID, auf NULL\<festleg Bare GUID>**|  
|`User-defined type(UDT)`|Keine|Dieselbe Klasse, die in derselben Assembly oder einer abhängigen Assembly an den benutzerdefinierten Typ gebunden ist.|  
|**varbinary**|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|**Byte, Byte [], auf NULL\<festleg Bare Byte>**|  
|`varchar`|Keine|Keine|  
|`xml`|`SqlXml`|Keine|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Automatische Datentypkonvertierung mit Out-Parametern  
 Eine CLR-Methode kann Informationen an den aufrufenden Code oder das aufrufende Programm zurückgeben, indem sie einen Eingabeparameter mit dem `out`-Modifizierer (Microsoft Visual C#) oder `<Out()> ByRef` (Microsoft Visual Basic) markiert. Wenn der Eingabeparameter ein CLR-Datentyp im `System.Data.SqlTypes`-Namespace ist und ein aufrufendes Programm seinen entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp als Eingabeparameter angibt, wird automatisch eine Typkonvertierung durchgeführt, wenn die CLR-Methode den Datentyp zurückgibt.  
  
 Beispielsweise verfügt die folgende CLR-gespeicherte Prozedur über einen Eingabeparameter von `SqlInt32` und einen CLR-Datentyp, der mit `out` (C#) oder `<Out()> ByRef` (Visual Basic) markiert ist:  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ ... }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
...  
End Sub  
```  
  
 Nachdem die Assembly in der Datenbank erstellt wurde, wird die gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem folgenden Transact-SQL erstellt, das einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp von `int` als einen OUTPUT-Parameter angibt:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Wenn die CLR-gespeicherte Prozedur aufgerufen wird, wird der `SqlInt32`-Datentyp automatisch in einen `int`-Datentyp konvertiert und an das aufrufende Programm zurückgegeben.  
  
 Allerdings können nicht alle CLR-Datentypen automatisch durch einen Out-Parameter in ihre entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen konvertiert werden. In der folgenden Tabelle werden diese Ausnahmen aufgeführt.  
  
|||  
|-|-|  
|**CLR-Datentyp (SQL Server)**|**SQL Server-Datentyp**|  
|`Decimal`|SMALLMONEY|  
|`SqlMoney`|SMALLMONEY|  
|`Decimal`|money|  
|`DateTime`|smalldatetime|  
|`SQLDateTime`|smalldatetime|  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Die `SqlGeography`-, `SqlGeometry`- und `SqlHierarchyId`-Typen wurden der Zuordnungstabelle hinzugefügt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Datentypen in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  
