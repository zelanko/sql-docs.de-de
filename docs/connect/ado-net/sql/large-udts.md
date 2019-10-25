---
title: Große UDTs
description: Veranschaulicht das Abrufen von Daten aus großen Wert-UDTs, die in SQL Server 2008 eingeführt wurden.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 4ea2c0002ceb01606cdf51f04246abcdc74429e0
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452156"
---
# <a name="large-udts"></a>Große UDTs

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Benutzerdefinierte Typen (UDTs) gestatten Entwicklern, das Skalartypsystem durch das Speichern von CLR-Objekten (Common Language Runtime) in einer SQL Server-Datenbank zu erweitern. UDTs können mehrere Elemente enthalten und Verhalten aufweisen, die sich von den herkömmlichen Aliasdatentypen unterscheiden, die aus einem einzigen SQL Server-Systemdatentyp bestehen.  
  
Vorher waren UDTs auf eine Dateigröße von maximal 8 Kilobyte beschränkt. In SQL Server 2008 besteht diese Beschränkung für UDTs mit dem <xref:Microsoft.Data.SqlClient.Server.Format.UserDefined>-Format nicht mehr.  
  
Die komplette Dokumentation für benutzerdefinierte Typen finden Sie unter [benutzerdefinierte CLR-Typen](https://go.microsoft.com/fwlink/?LinkId=98366) aus SQL Server-Onlinedokumentation.
  
## <a name="retrieving-udt-schemas-using-getschema"></a>Abrufen von UDT-Schemas mithilfe von GetSchema  
Die <xref:Microsoft.Data.SqlClient.SqlConnection.GetSchema%2A>-Methode von <xref:Microsoft.Data.SqlClient.SqlConnection> gibt Datenbankschema Informationen in einem <xref:System.Data.DataTable> zurück.
  
### <a name="getschematable-column-values-for-udts"></a>Getschembare-Spaltenwerte für UDTs  
Die <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>-Methode einer <xref:Microsoft.Data.SqlClient.SqlDataReader> gibt eine <xref:System.Data.DataTable> zurück, die Spalten Metadaten beschreibt. In der folgenden Tabelle werden die Unterschiede in den Spalten Metadaten für große UDTs zwischen SQL Server 2005 und SQL Server 2008 beschrieben.  
  
|SqlDataReader-Spalte|SQL Server 2005|SQL Server 2008 und höher|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|Unterschiedlich|Unterschiedlich|  
|`NumericPrecision`|255|255|  
|`NumericScale`|255|255|  
|`DataType`|`Byte[]`|UDT-Instanz|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|UDT-Instanz|  
|`ProviderType`|21 (`SqlDbType.VarBinary`)|29 (`SqlDbType.Udt`)|  
|`NonVersionedProviderType`|29 (`SqlDbType.Udt`)|29 (`SqlDbType.Udt`)|  
|`DataTypeName`|`SqlDbType.VarBinary`|Der dreiteilige, als *Database.SchemaName.TypeName* angegebene Name.|  
|`IsLong`|Unterschiedlich|Unterschiedlich|  
  
## <a name="sqldatareader-considerations"></a>Überlegungen zu SqlDataReader  
Der <xref:Microsoft.Data.SqlClient.SqlDataReader> wurde beginnend in SQL Server 2008 erweitert und unterstützt nun das Abrufen großer UDT-Werte. Wie große UDT-Werte von einem <xref:Microsoft.Data.SqlClient.SqlDataReader> verarbeitet werden, hängt von der verwendeten Version von SQL Server sowie von der in der Verbindungs Zeichenfolge angegebenen `Type System Version` ab. Weitere Informationen finden Sie unter <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>ausgewertet wird.  
  
Die folgenden Methoden von <xref:Microsoft.Data.SqlClient.SqlDataReader> geben eine <xref:System.Data.SqlTypes.SqlBinary> anstelle eines UDT zurück, wenn die `Type System Version` auf SQL Server 2005 festgelegt ist:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
Die folgenden Methoden geben ein Array von `Byte[]` anstelle eines UDT zurück, wenn die `Type System Version` auf SQL Server 2005 festgelegt ist:  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
Beachten Sie, dass für die aktuelle Version von ADO.NET keine Konvertierungen vorgenommen werden.  
  
## <a name="specifying-sqlparameters"></a>Angeben von SQLPARAMETERS  
Die folgenden <xref:Microsoft.Data.SqlClient.SqlParameter> Eigenschaften wurden für große UDTs erweitert.  
  
|SqlParameter-Eigenschaft|und Beschreibung|  
|---------------------------|-----------------|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A>|Ruft ein Objekt ab, das den Wert des Parameters darstellt, oder legt dieses fest. Der Standardwert ist NULL. Die Eigenschaft kann `SqlBinary`, `Byte[]` oder ein verwaltetes Objekt sein.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.SqlValue%2A>|Ruft ein Objekt ab, das den Wert des Parameters darstellt, oder legt dieses fest. Der Standardwert ist NULL. Die Eigenschaft kann `SqlBinary`, `Byte[]` oder ein verwaltetes Objekt sein.|  
|<xref:Microsoft.Data.SqlClient.SqlParameter.Size%2A>|Ruft die Größe des aufzulösenden Parameter Werts ab oder legt diese fest. Der Standardwert ist 0. Die-Eigenschaft kann eine ganze Zahl sein, die die Größe des Parameter Werts darstellt. Bei großen UDTs kann es sich um die tatsächliche Größe des UDT handeln, bei unbekannter Größe lautet der Wert -1.|  
  
## <a name="retrieving-data-example"></a>Beispiel zum Abrufen von Daten  
Im folgenden Code Fragment wird veranschaulicht, wie große UDT-Daten abgerufen werden. Die `connectionString`-Variable setzt eine gültige Verbindung mit einer SQL Server-Datenbank voraus, und die `commandString`-Variable geht von einer gültigen SELECT-Anweisung aus, wobei die Primärschlüssel Spalte zuerst aufgelistet ist.  
  
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
