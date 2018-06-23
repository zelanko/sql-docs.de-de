---
title: Zuordnen von CLR-Parameterdaten | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
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
caps.latest.revision: 69
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6a7c442f3bf102c668f0889f008b8a87205b2257
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161839"
---
# <a name="mapping-clr-parameter-data"></a>Zuordnen von CLR-Parameterdaten
  In der folgenden Tabelle sind die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen, ihre Entsprechungen in CLR (Common Language Runtime) für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im `System.Data.SqlTypes`-Namespace und ihre systemeigenen CLR-Entsprechungen in [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework aufgeführt.  
  
||||  
|-|-|-|  
|**SQL Server-Datentyp**|Typ (in System.Data.SqlTypes oder Microsoft.SqlServer.Types)|**CLR-Datentyp ((.NET Framework)**|  
|`bigint`|`SqlInt64`|**Int64, NULL-Werte zulassen\<Int64 >**|  
|`binary`|`SqlBytes, SqlBinary`|`Byte[]`|  
|`bit`|`SqlBoolean`|**Boolean "," NULL-Werte zulassen\<booleschen >**|  
|`char`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`cursor`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`date`|`SqlDateTime`|**"DateTime", NULL-Werte zulassen\<"DateTime" >**|  
|`datetime`|`SqlDateTime`|**"DateTime", NULL-Werte zulassen\<"DateTime" >**|  
|`datetime2`|InclusionThresholdSetting|**"DateTime", NULL-Werte zulassen\<"DateTime" >**|  
|`DATETIMEOFFSET`|`None`|**"DateTimeOffset", NULL-Werte zulassen\<"DateTimeOffset" >**|  
|`decimal`|`SqlDecimal`|**Decimal, NULL-Werte zulassen\<Decimal >**|  
|`float`|`SqlDouble`|**Double, NULL-Werte zulassen\<doppelte >**|  
|`geography`|`SqlGeography`<br /><br /> `SqlGeography` wird in Microsoft.SqlServer.Types.dll wird mit SQL Server installiert und kann von heruntergeladen werden definiert die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](http://go.microsoft.com/fwlink/?LinkId=131220).|InclusionThresholdSetting|  
|`geometry`|`SqlGeometry`<br /><br /> `SqlGeometry` wird in Microsoft.SqlServer.Types.dll wird mit SQL Server installiert und kann von heruntergeladen werden definiert die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](http://go.microsoft.com/fwlink/?LinkId=131220).|InclusionThresholdSetting|  
|`hierarchyid`|`SqlHierarchyId`<br /><br /> `SqlHierarchyId` wird in Microsoft.SqlServer.Types.dll wird mit SQL Server installiert und kann von heruntergeladen werden definiert die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [-feature Pack](http://go.microsoft.com/fwlink/?LinkId=131220).|InclusionThresholdSetting|  
|`image`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`int`|`SqlInt32`|**Int32, NULL-Werte zulassen\<Int32 >**|  
|`money`|`SqlMoney`|**Decimal, NULL-Werte zulassen\<Decimal >**|  
|`nchar`|`SqlChars, SqlString`|`String, Char[]`|  
|`ntext`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`numeric`|`SqlDecimal`|**Decimal, NULL-Werte zulassen\<Decimal >**|  
|`nvarchar`|`SqlChars, SqlString`<br /><br /> `SQLChars` bietet eine bessere Übereinstimmung für Datenübertragungen und Datenzugriff, und `SQLString` bietet eine bessere Übereinstimmung für die Durchführung von Zeichenfolgenvorgängen.|`String, Char[]`|  
|`nvarchar(1), nchar(1)`|`SqlChars, SqlString`|**Char, String, Char [], Nullable\<Char >**|  
|`real`|`SqlSingle` (der Bereich von `SqlSingle` ist jedoch größer als `real`)|**Einzelne, NULL-Werte zulassen\<einzelne >**|  
|`rowversion`|InclusionThresholdSetting|`Byte[]`|  
|`smallint`|`SqlInt16`|**Int16, NULL-Werte zulassen\<Int16 >**|  
|`smallmoney`|`SqlMoney`|**Decimal, NULL-Werte zulassen\<Decimal >**|  
|`sql_variant`|InclusionThresholdSetting|`Object`|  
|`table`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`text`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`time`|InclusionThresholdSetting|**Zeitspanne, die NULL-Werte zulassen\<TimeSpan >**|  
|`timestamp`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`tinyint`|`SqlByte`|**Byte, NULL-Werte zulassen\<Byte >**|  
|`uniqueidentifier`|`SqlGuid`|**GUID, die NULL-Werte zulassen\<Guid >**|  
|`User-defined type(UDT)`|InclusionThresholdSetting|Dieselbe Klasse, die in derselben Assembly oder einer abhängigen Assembly an den benutzerdefinierten Typ gebunden ist.|  
|**varbinary**|`SqlBytes, SqlBinary`|`Byte[]`|  
|`varbinary(1), binary(1)`|`SqlBytes, SqlBinary`|**Byte, Byte [], Nullable\<Byte >**|  
|`varchar`|InclusionThresholdSetting|InclusionThresholdSetting|  
|`xml`|`SqlXml`|InclusionThresholdSetting|  
  
## <a name="automatic-data-type-conversion-with-out-parameters"></a>Automatische Datentypkonvertierung mit Out-Parametern  
 Eine CLR-Methode kann Informationen an den aufrufenden Code oder das aufrufende Programm zurückgeben, indem sie einen Eingabeparameter mit dem `out`-Modifizierer (Microsoft Visual C#) oder `<Out()> ByRef` (Microsoft Visual Basic) markiert. Wenn der Eingabeparameter ein CLR-Datentyp im `System.Data.SqlTypes`-Namespace ist und ein aufrufendes Programm seinen entsprechenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp als Eingabeparameter angibt, wird automatisch eine Typkonvertierung durchgeführt, wenn die CLR-Methode den Datentyp zurückgibt.  
  
 Beispielsweise verfügt die folgende CLR-gespeicherte Prozedur über einen Eingabeparameter von `SqlInt32` und einen CLR-Datentyp, der mit `out` (C#) oder `<Out()> ByRef` (Visual Basic) markiert ist:  
  
```csharp  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void PriceSum(out SqlInt32 value)  
{ … }  
```  
  
```vb  
<Microsoft.SqlServer.Server.SqlProcedure> _  
Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
…  
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
|**CLR-Datentyp (SQL Server)**|**SQL Server-Datentyp**|  
|`Decimal`|SMALLMONEY|  
|`SqlMoney`|SMALLMONEY|  
|`Decimal`|money|  
|`DateTime`|smalldatetime|  
|`SQLDateTime`|smalldatetime|  
  
## <a name="change-history"></a>Änderungsverlauf  
  
|Aktualisierter Inhalt|  
|---------------------|  
|Die `SqlGeography`-, `SqlGeometry`- und `SqlHierarchyId`-Typen wurden der Zuordnungstabelle hinzugefügt.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  