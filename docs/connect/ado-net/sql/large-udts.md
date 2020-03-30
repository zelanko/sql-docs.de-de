---
title: Große UDTs
description: Veranschaulicht, wie Sie Daten aus UDTs mit großen Werten abrufen, die mit SQL Server 2008 eingeführt wurden.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e572b8fcf1550562c7a9f1841eec1c311f18c3f8
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896706"
---
# <a name="large-udts"></a>Große UDTs

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Benutzerdefinierte Typen (UDTs) gestatten Entwicklern, das Skalartypsystem durch das Speichern von CLR-Objekten (Common Language Runtime) in einer SQL Server-Datenbank zu erweitern. UDTs können mehrere Elemente enthalten und Verhalten aufweisen, die sich von den herkömmlichen Aliasdatentypen unterscheiden, die aus einem einzigen SQL Server-Systemdatentyp bestehen.  
  
Vorher waren UDTs auf eine Dateigröße von maximal 8 Kilobyte beschränkt. In SQL Server 2008 besteht diese Beschränkung für UDTs mit dem <xref:Microsoft.Data.SqlClient.Server.Format.UserDefined>-Format nicht mehr.  
  
Die vollständige Dokumentation zu benutzerdefinierten Typen finden Sie in der SQL Server-Onlinedokumentation unter [Benutzerdefinierte CLR-Typen](https://go.microsoft.com/fwlink/?LinkId=98366).
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Abrufen von UDT-Schemas mithilfe von GetSchema  
Die <xref:Microsoft.Data.SqlClient.SqlConnection.GetSchema%2A>-Methode von <xref:Microsoft.Data.SqlClient.SqlConnection> gibt in einer <xref:System.Data.DataTable>Informationen zum Datenbankschema zurück.
  
### <a name="getschematable-column-values-for-udts"></a>Werte in der Spalte GetSchemaTable für UDTs  
Die <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>-Methode von <xref:Microsoft.Data.SqlClient.SqlDataReader> gibt eine <xref:System.Data.DataTable> zurück, die Spaltenmetadaten beschreibt. In der folgenden Tabelle werden die Unterschiede bei SQL Server 2005 und SQL Server 2008 bei den Spaltenmetadaten für große UDTs beschrieben.  
  
|Spalte SqlDataReader|SQL Server 2005|SQL Server 2008 und höher|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Varies|Varies|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT-Instanz|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT-Instanz|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Der dreiteilige, als *Database.SchemaName.TypeName* angegebene Name.|  
|`IsLong`|Varies|Varies|  
  
## <a name="sqldatareader-considerations"></a>Aspekte bei der Spalte SqlDataReader  
Der <xref:Microsoft.Data.SqlClient.SqlDataReader> wurde beginnend in SQL Server 2008 erweitert und unterstützt nun das Abrufen großer UDT-Werte. Wie große UDT-Werte von <xref:Microsoft.Data.SqlClient.SqlDataReader> verarbeitet werden, hängt von der verwendeten SQL Server-Version sowie von der in der Verbindungszeichenfolge angegebenen `Type System Version` ab. Weitere Informationen finden Sie unter <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
Die folgenden Methoden von <xref:Microsoft.Data.SqlClient.SqlDataReader> geben <xref:System.Data.SqlTypes.SqlBinary> anstelle eines UDT zurück, wenn `Type System Version` auf SQL Server 2005 festgelegt ist:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
Die folgenden Methoden geben eine Array von `Byte[]` anstelle eines UDT zurück, wenn `Type System Version` auf SQL Server 2005 festgelegt ist:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
Beachten Sie, dass für die aktuelle Version von ADO.NET keine Konvertierungen erfolgen.  
  
## <a name="specifying-sqlparameters"></a>Angeben von SqlParameters  
Die folgenden <xref:Microsoft.Data.SqlClient.SqlParameter>-Eigenschaften wurden für das Arbeiten mit großen UDTs erweitert.  
  
|SqlParameter-Eigenschaft|BESCHREIBUNG|  
|---------------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Ruft ein Objekt ab oder legt es fest, das den Wert des Parameters darstellt. Der Standardwert ist NULL. Die Eigenschaft kann `SqlBinary`, `Byte[]` oder ein verwaltetes Objekt sein.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Ruft ein Objekt ab oder legt es fest, das den Wert des Parameters darstellt. Der Standardwert ist NULL. Die Eigenschaft kann `SqlBinary`, `Byte[]` oder ein verwaltetes Objekt sein.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Ruft die Größe des aufzulösenden Parameterwerts ab oder legt sie fest. Der Standardwert ist 0. Die Eigenschaft kann eine ganze Zahl sein, die die Größe des Parameterwerts darstellt. Bei großen UDTs kann es sich um die tatsächliche Größe des UDT handeln, bei unbekannter Größe lautet der Wert -1.|  
  
## <a name="retrieving-data-example"></a>Beispiel des Abrufens von Daten  
Das folgende Codefragment zeigt, wie große UDT-Daten abgerufen werden können. Die Variable `connectionString` setzt eine gültige Verbindung mit einer SQL Server-Datenbank voraus. Die Variable `commandString` setzt eine gültige SELECT-Anweisung mit an erster Stelle aufgeführter Primärschlüsselspalte voraus.  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Binäre Daten und Daten mit umfangreichen Werten in SQL Server](sql-server-binary-large-value-data.md)
 