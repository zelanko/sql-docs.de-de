---
title: Mapping von CLR-Parameter Daten | Microsoft-Dokumentation
description: In diesem Artikel werden Microsoft SQL Server Datentypen, Entsprechungen in der CLR für SQL Server und systemeigene CLR-Entsprechungen im .NET Framework aufgelistet.
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
ms.openlocfilehash: 911b56023ea78ec75e605a39a39b705724101dee
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719938"
---
# <a name="mapping-clr-parameter-data"></a>Zuordnen von CLR-Parameterdaten
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In der folgenden Tabelle [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind die-Datentypen, ihre Entsprechungen in der Common Language Runtime (CLR) für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im **System. Data. SqlTypes** -Namespace und ihre systemeigenen CLR-Entsprechungen in der [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework aufgelistet.  
  
||||  
|-|-|-|  
|**SQL Server-Datentyp**|Typ (in System.Data.SqlTypes oder Microsoft.SqlServer.Types)|**CLR-Datentyp (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, NULL-Werte zulassen\<Int64>**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**bit**|**SqlBoolean**|**Boolescher Wert, NULL-Werte zulassen\<Boolean>**|  
|**char**|Keine|Keine|  
|**Cursor**|Keine|Keine|  
|**date**|**SqlDateTime**|**DateTime, NULL-Werte zulassen\<DateTime>**|  
|**datetime**|**SqlDateTime**|**DateTime, NULL-Werte zulassen\<DateTime>**|  
|**datetime2**|Keine|**DateTime, NULL-Werte zulassen\<DateTime>**|  
|**DateTimeOffset**|**None**|**DateTimeOffset, NULL-Werte zulassen\<DateTimeOffset>**|  
|**decimal**|**SqlDecimal**|**Decimal, NULL-Werte zulassen\<Decimal>**|  
|**float**|**SqlDouble**|**Double, NULL-Werte zulassen\<Double>**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** wird in Microsoft.SqlServer.Types.dll definiert, das mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** wird in Microsoft.SqlServer.Types.dll definiert, das mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** wird in Microsoft.SqlServer.Types.dll definiert, das mit SQL Server installiert wird und aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**Bild**|Keine|Keine|  
|**int**|**SqlInt32**|**Int32, NULL-Werte zulassen\<Int32>**|  
|**money**|**SqlMoney**|**Decimal, NULL-Werte zulassen\<Decimal>**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|Keine|Keine|  
|**numeric**|**SqlDecimal**|**Decimal, NULL-Werte zulassen\<Decimal>**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SqlChars** eignet sich besser für die Datenübertragung und den Zugriff, und **SqlString** ist eine bessere Entsprechung für die Durchführung von Zeichen folgen Vorgängen.|**String, Char[]**|  
|**nvarchar (1), nchar (1)**|**SqlChars, SqlString**|**Char, String, Char [], Nullable\<char>**|  
|**real**|**SqlSingle** (der Bereich von **SqlSingle**ist jedoch größer als **real**).|**Single, Nullable\<Single>**|  
|**rowversion**|Keine|**Byte []**|  
|**smallint**|**SqlInt16**|**Int16, NULL-Werte zulassen\<Int16>**|  
|**smallmoney**|**SqlMoney**|**Decimal, NULL-Werte zulassen\<Decimal>**|  
|**sql_variant**|Keine|**Objekt**|  
|**Tabelle**|Keine|Keine|  
|**text**|Keine|Keine|  
|**time**|Keine|**TimeSpan, Nullable\<TimeSpan>**|  
|**timestamp**|Keine|Keine|  
|**tinyint**|**SqlByte**|**Byte, NULL-Werte zulassen\<Byte>**|  
|**uniqueidentifier**|**SqlGuid**|**GUID, NULL-Werte zulassen\<Guid>**|  
|**Benutzerdefinierter Typ (User-Defined Type, UDT)**|Keine|Dieselbe Klasse, die in derselben Assembly oder einer abhängigen Assembly an den benutzerdefinierten Typ gebunden ist.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte []**|  
|**varbinary (1), binär (1)**|**SqlBytes, SqlBinary**|**Byte, Byte [], NULL-Werte zulassen\<byte>**|  
|**varchar**|Keine|Keine|  
|**xml**|**SQLXML**|Keine|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Automatische Datentypkonvertierung mit Out-Parametern  
 Eine CLR-Methode kann Informationen an den aufrufenden Code bzw. das aufrufende Programm zurückgeben, indem Sie einen Eingabeparameter mit dem **out** -Modifizierer (Microsoft Visual c#) oder ** \<Out()> ByRef** (Microsoft Visual Basic) kennzeichnet, wenn der Eingabeparameter ein CLR-Datentyp im **System ist. der Data. SqlTypes** -Namespace, und das aufrufende Programm gibt seinen äquivalenten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp als Eingabeparameter an. eine Typkonvertierung erfolgt automatisch, wenn die CLR-Methode den-Datentyp zurückgibt.  
  
 Beispielsweise verfügt die folgende gespeicherte CLR-Prozedur über einen Eingabeparameter des **SqlInt32** CLR-Datentyps, der mit **out** (c#) oder ** \<Out()> ByRef** (Visual Basic) gekennzeichnet ist:  
  
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
  
 Nachdem die Assembly erstellt und in der Datenbank erstellt wurde, wird die gespeicherte Prozedur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem folgenden Transact-SQL-Code erstellt, der den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp **int** als Ausgabeparameter angibt:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Wenn die gespeicherte CLR-Prozedur aufgerufen wird, wird der **SqlInt32** -Datentyp automatisch in einen **int** -Datentyp konvertiert und an das aufrufende Programm zurückgegeben.  
  
 Allerdings können nicht alle CLR-Datentypen automatisch durch einen Out-Parameter in ihre entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen konvertiert werden. In der folgenden Tabelle werden diese Ausnahmen aufgeführt.  
  
|||  
|-|-|  
|**CLR-Datentyp (SQL Server)**|**SQL Server-Datentyp**|  
|**Decimal**|SMALLMONEY|  
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
  
  
