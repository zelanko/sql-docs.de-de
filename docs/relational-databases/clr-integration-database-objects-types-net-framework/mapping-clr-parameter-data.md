---
title: Zuordnung von CLR-Parameterdaten | Microsoft Docs
description: In diesem Artikel werden Microsoft SQL Server-Datentypen, Entsprechungen in der CLR für SQL Server und systemeigene CLR-Äquivalente in .NET Framework aufgeführt.
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
ms.openlocfilehash: 360a94229b107e9f24bb2a769157c75cdeb3c143
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488458"
---
# <a name="mapping-clr-parameter-data"></a>Zuordnen von CLR-Parameterdaten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] folgenden Tabelle sind Datentypen, deren Äquivalente in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Common Language Runtime (CLR) für im **Namespace System.Data.SqlTypes** und ihre systemeigenen CLR-Äquivalente im [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework aufgeführt.  
  
||||  
|-|-|-|  
|**SQL Server-Datentyp**|Typ (in System.Data.SqlTypes oder Microsoft.SqlServer.Types)|**CLR-Datentyp (.NET Framework)**|  
|**bigint**|**SqlInt64**|**Int64, Nullable\<Int64>**|  
|**binary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**bit**|**SqlBoolean**|**Boolesche,\<nullbare boolesche>**|  
|**char**|Keine|Keine|  
|**Cursor**|Keine|Keine|  
|**date**|**Sqldatetime**|**DateTime, Nullable\<DateTime>**|  
|**datetime**|**Sqldatetime**|**DateTime, Nullable\<DateTime>**|  
|**datetime2**|Keine|**DateTime, Nullable\<DateTime>**|  
|**Datetimeoffset**|**None**|**DateTimeOffset, nicht\<zulässige DateTimeOffset>**|  
|**decimal**|**Sqldecimal**|**Dezimal, Nullable\<Decimal>**|  
|**float**|**Sqldouble**|**Doppelte, nullable\<Doppel->**|  
|**geography**|**SqlGeography**<br /><br /> **SqlGeography** ist in Microsoft.SqlServer.Types.dll definiert, das mit SQL Server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installiert ist und aus dem [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**geometry**|**SqlGeometry**<br /><br /> **SqlGeometry** ist in Microsoft.SqlServer.Types.dll definiert, das mit SQL Server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installiert ist und aus dem [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**hierarchyid**|**SqlHierarchyId**<br /><br /> **SqlHierarchyId** ist in Microsoft.SqlServer.Types.dll definiert, das mit SQL Server [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installiert ist und aus dem [Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676)heruntergeladen werden kann.|Keine|  
|**image**|Keine|Keine|  
|**int**|**SqlInt32**|**Int32, Nullable\<Int32>**|  
|**money**|**Sqlmoney**|**Dezimal, Nullable\<Decimal>**|  
|**nchar**|**SqlChars, SqlString**|**String, Char[]**|  
|**ntext**|Keine|Keine|  
|**numeric**|**Sqldecimal**|**Dezimal, Nullable\<Decimal>**|  
|**nvarchar**|**SqlChars, SqlString**<br /><br /> **SQLChars** ist eine bessere Übereinstimmung für die Datenübertragung und den Zugriff, und **SQLString** ist eine bessere Übereinstimmung für die Ausführung von String-Vorgängen.|**String, Char[]**|  
|**nvarchar(1), nchar(1)**|**SqlChars, SqlString**|**Char, String, Char[],\<Nullable char>**|  
|**real**|**SqlSingle** (der Bereich von **SqlSingle**ist jedoch größer als **real)**|**Einzelne, nicht\<zu>**|  
|**rowversion**|Keine|**Byte[]**|  
|**smallint**|**SqlInt16**|**Int16, Nullable\<Int16>**|  
|**smallmoney**|**Sqlmoney**|**Dezimal, Nullable\<Decimal>**|  
|**sql_variant**|Keine|**Objekt**|  
|**Tabelle**|Keine|Keine|  
|**text**|Keine|Keine|  
|**time**|Keine|**TimeSpan, Nullable\<TimeSpan>**|  
|**timestamp**|Keine|Keine|  
|**tinyint**|**SqlByte**|**Byte, Nullable\<Byte>**|  
|**uniqueidentifier**|**Sqlguid**|**Guid, Nullable\<Guid>**|  
|**Benutzerdefinierter Typ (UDT)**|Keine|Dieselbe Klasse, die in derselben Assembly oder einer abhängigen Assembly an den benutzerdefinierten Typ gebunden ist.|  
|**varbinary**|**SqlBytes, SqlBinary**|**Byte[]**|  
|**varbinary(1), binär(1)**|**SqlBytes, SqlBinary**|**Byte, Byte[],\<Nullable byte>**|  
|**varchar**|Keine|Keine|  
|**xml**|**Sqlxml**|Keine|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Automatische Datentypkonvertierung mit Out-Parametern  
 Eine CLR-Methode kann Informationen an den aufrufenden Code oder das Programm zurückgeben, indem sie einen Eingabeparameter mit dem Out-Modifikator (Microsoft Visual **out** C)- oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ** \<Out()> ByRef** (Microsoft Visual Basic) markiert. Wenn der Eingabeparameter ein CLR-Datentyp im **Namespace System.Data.SqlTypes** ist und das aufrufende Programm seinen entsprechenden Datentyp als Eingabeparameter angibt, erfolgt automatisch eine Typkonvertierung, wenn die CLR-Methode den Datentyp zurückgibt.  
  
 Die folgende gespeicherte CLR-Prozedur verfügt beispielsweise über einen Eingabeparameter des **SQLInt32** CLR-Datentyps, der mit **out** (C-) oder ** \<Out()> ByRef** (Visual Basic) gekennzeichnet ist:  
  
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
  
 Nachdem die Assembly in der Datenbank erstellt und erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde, wird die gespeicherte Prozedur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit dem folgenden Transact-SQL erstellt, das einen Datentyp von **int** als OUTPUT-Parameter angibt:  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
```  
  
 Wenn die gespeicherte CLR-Prozedur aufgerufen wird, wird der **SqlInt32-Datentyp** automatisch in einen **int-Datentyp** konvertiert und an das aufrufende Programm zurückgegeben.  
  
 Allerdings können nicht alle CLR-Datentypen automatisch durch einen Out-Parameter in ihre entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen konvertiert werden. In der folgenden Tabelle werden diese Ausnahmen aufgeführt.  
  
|||  
|-|-|  
|**CLR-Datentyp (SQL Server)**|**SQL Server-Datentyp**|  
|**Decimal**|SMALLMONEY|  
|**Sqlmoney**|SMALLMONEY|  
|**Decimal**|money|  
|**Datetime**|smalldatetime|  
|**Sqldatetime**|smalldatetime|  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|**SqlGeography**- **SqlGeometry**und **SqlHierarchyId-Typen** wurden der Zuordnungstabelle hinzugefügt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Datentypen in .NET Framework](../../relational-databases/clr-integration-database-objects-types-net-framework/sql-server-data-types-in-the-net-framework.md)  
  
  
