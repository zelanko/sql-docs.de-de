---
title: Tabellenwertparameter
description: Beschreibt, wie mit Tabellenwert Parametern gearbeitet wird, die in SQL Server 2008 eingeführt wurden.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 370c16d5-db7b-43e3-945b-ccaab35b739b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: cb8eec87d0d36eb7deb8663e40407c0067967def
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451920"
---
# <a name="table-valued-parameters"></a>Tabellenwertparameter

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Tabellenwertparameter bieten eine einfache Möglichkeit zum Marshallen mehrerer Datenzeilen aus einer Clientanwendung nach SQL Server, ohne dass mehrere Roundtrips oder eine spezielle serverseitige Logik für die Verarbeitung der Daten erforderlich sind. Sie können Tabellenwertparameter verwenden, um Datenzeilen in einer Clientanwendung zu kapseln und die Daten in einem einzigen parametrisierten Befehl an den Server zu senden. Die eingehenden Datenzeilen werden in einer Tabellenvariablen gespeichert, die Sie dann mithilfe von Transact-SQL bearbeiten können.  
  
Für den Zugriff auf Spaltenwerte in Tabellenwertparametern können Standard-SELECT-Anweisungen in Transact-SQL verwendet werden. Tabellenwertparameter sind stark typisiert, und ihre Struktur wird automatisch validiert. Die Größe der Tabellenwert Parameter wird nur durch den Server Arbeitsspeicher beschränkt.  
  
> [!NOTE]
>  Sie können keine Daten in einem Tabellenwert Parameter zurückgeben. Tabellenwert Parameter sind nur Eingabewerte. das OUTPUT-Schlüsselwort wird nicht unterstützt.  
  
Weitere Informationen zu Tabellenwert Parametern finden Sie in den folgenden Ressourcen.  
  
|Ressource|und Beschreibung|  
|--------------|-----------------|  
|[Tabellenwertparameter (Datenbankmodul)](https://go.microsoft.com/fwlink/?LinkId=98363) in der SQL Server-Onlinedokumentation|Beschreibt das Erstellen und Verwenden von Tabellenwert Parametern.|  
|[Benutzerdefinierte Tabellentypen](https://go.microsoft.com/fwlink/?LinkId=98364) in SQL Server-Onlinedokumentation|Beschreibt die benutzerdefinierten Tabellentypen, die zum Deklarieren von Tabellenwertparametern verwendet werden.|  
  
## <a name="passing-multiple-rows-in-previous-versions-of-sql-server"></a>Übergeben mehrerer Zeilen in früheren Versionen von SQL Server  
Vor der Einführung von Tabellenwertparametern in SQL Server 2008 bestanden nur eingeschränkte Möglichkeiten zum Übergeben mehrerer Datenzeilen an eine gespeicherte Prozedur oder einen parametrisierten SQL-Befehl. Ein Entwickler kann aus den folgenden Optionen auswählen, um mehrere Zeilen an den Server zu übergeben:  
  
- Verwenden Sie eine Reihe einzelner Parameter, um die Werte in mehreren Spalten und Zeilen der Daten darzustellen. Die Menge der Daten, die mit dieser Methode übermittelt werden kann, ist durch die zulässige Anzahl von Parametern beschränkt. SQL Server-Prozeduren können höchstens über 2100 Parameter verfügen. Server seitige Logik ist erforderlich, um diese einzelnen Werte für die Verarbeitung in einer Tabellen Variablen oder einer temporären Tabelle zusammenzufassen.  
  
- Bündeln Sie mehrere Datenwerte in durch Trennzeichen getrennte Zeichen folgen oder XML-Dokumente, und übergeben Sie diese Text Werte dann an eine Prozedur oder Anweisung. Hierfür ist es erforderlich, dass die Prozedur oder die Anweisung die erforderliche Logik zum Überprüfen der Datenstrukturen und zur Entflechtung der Werte einschließt.  
  
- Erstellen Sie eine Reihe von einzelnen SQL-Anweisungen für Datenänderungen, die sich auf mehrere Zeilen auswirken, z. b. solche, die durch Aufrufen der `Update`-Methode einer <xref:Microsoft.Data.SqlClient.SqlDataAdapter> erstellt werden. Änderungen können einzeln an den Server übermittelt oder in Gruppen zusammengefasst werden. Auch wenn Sie in Batches übermittelt werden, die mehrere-Anweisungen enthalten, wird jede-Anweisung separat auf dem Server ausgeführt.  
  
- Verwenden Sie das Hilfsprogramm `bcp` oder das <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Objekt, um viele Daten Zeilen in eine Tabelle zu laden. Obwohl dieses Verfahren sehr effizient ist, wird die serverseitige Verarbeitung nur dann unterstützt, wenn die Daten in eine temporäre Tabelle oder Tabellen Variable geladen werden.  
  
## <a name="creating-table-valued-parameter-types"></a>Erstellen von Tabellenwert Parameter-Typen  
Tabellenwertparameter basieren auf stark typisierten Tabellenstrukturen, die mit CREATE TYPE-Anweisungen in Transact-SQL definiert werden. Sie müssen einen Tabellentyp erstellen und die Struktur in SQL Server definieren, bevor Sie Tabellenwertparameter in Ihren Clientanwendungen verwenden können. Weitere Informationen über das Erstellen von Tabellentypen finden Sie unter [Benutzerdefinierte Tabellentypen](https://go.microsoft.com/fwlink/?LinkID=98364) in der SQL Server-Onlinedokumentation.  
  
Die folgende Anweisung erstellt einen Tabellentyp namens "CategoryTableType", der aus den Spalten "CategoryID" und "CategoryName" besteht:  
  
```sql
CREATE TYPE dbo.CategoryTableType AS TABLE  
    ( CategoryID int, CategoryName nvarchar(50) )  
```  
  
Nachdem Sie einen Tabellentyp erstellt haben, können Sie Tabellenwert Parameter basierend auf diesem Typ deklarieren. Das folgende Transact-SQL-Fragment veranschaulicht, wie ein Tabellenwertparameter in der Definition einer gespeicherten Prozedur deklariert wird. Beachten Sie, dass das Schlüsselwort "schreibgeschützt" erforderlich ist, um einen Tabellenwert Parameter zu deklarieren.  
  
```sql
CREATE PROCEDURE usp_UpdateCategories   
    (@tvpNewCategories dbo.CategoryTableType READONLY)  
```  
  
## <a name="modifying-data-with-table-valued-parameters-transact-sql"></a>Ändern von Daten mit Tabellenwert Parametern (Transact-SQL)  
Tabellenwert Parameter können in Satz basierten Datenänderungen verwendet werden, die sich auf mehrere Zeilen auswirken, indem eine einzige Anweisung ausgeführt wird. Beispielsweise können Sie alle Zeilen in einem Tabellenwert Parameter auswählen und in eine Datenbanktabelle einfügen, oder Sie können eine Update-Anweisung erstellen, indem Sie einen Tabellenwert Parameter mit der Tabelle verbinden, die Sie aktualisieren möchten.  
  
Mit der folgenden UPDATE-Anweisung in Transact-SQL wird veranschaulicht, wie ein Tabellenwertparameter durch einen Join mit der Categories-Tabelle verwendet wird. Wenn Sie einen Tabellenwert Parameter mit einem Join in einer from-Klausel verwenden, müssen Sie diesen ebenfalls als Alias angeben, wie hier gezeigt, wobei der Tabellenwert Parameter als "EC" Alias verwendet wird:  
  
```sql
UPDATE dbo.Categories  
    SET Categories.CategoryName = ec.CategoryName  
    FROM dbo.Categories INNER JOIN @tvpEditedCategories AS ec  
    ON dbo.Categories.CategoryID = ec.CategoryID;  
```  
  
Dieses Transact-SQL-Beispiel veranschaulicht, wie Zeilen aus einem Tabellenwertparameter ausgewählt werden, um einen INSERT-Vorgang in einem einzelnen mengenbasierten Vorgang auszuführen.  
  
```sql
INSERT INTO dbo.Categories (CategoryID, CategoryName)  
    SELECT nc.CategoryID, nc.CategoryName FROM @tvpNewCategories AS nc;  
```  
  
## <a name="limitations-of-table-valued-parameters"></a>Einschränkungen von Tabellenwert Parametern  
Es gibt mehrere Einschränkungen für Tabellenwert Parameter:  
  
- Tabellenwertparameter können nicht an [benutzerdefinierte CLR-Funktionen](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) übergeben werden.  
  
- Tabellenwert Parameter können nur indiziert werden, um Unique-oder PRIMARY KEY-Einschränkungen zu unterstützen. SQL Server verwaltet keine Statistiken für Tabellenwertparameter.  
  
- Tabellenwertparameter sind in Transact-SQL-Code schreibgeschützt. Sie können die Spaltenwerte in den Zeilen eines Tabellenwert Parameters nicht aktualisieren, und Sie können keine Zeilen einfügen oder löschen. Um die Daten zu ändern, die an eine gespeicherte Prozedur oder eine parametrisierte Anweisung in einem Tabellenwert Parameter übergeben werden, müssen Sie die Daten in eine temporäre Tabelle oder in eine Tabellen Variable einfügen.  
  
- ALTER TABLE-Anweisungen können nicht zum Ändern des Entwurfs von Tabellenwert Parametern verwendet werden.  
  
## <a name="configuring-a-sqlparameter-example"></a>Konfigurieren eines SqlParameter-Beispiels  
<xref:Microsoft.Data.SqlClient> unterstützt das Auffüllen von Tabellenwertparametern aus <xref:System.Data.DataTable>-, <xref:System.Data.Common.DbDataReader>- und <xref:System.Collections.Generic.IEnumerable%601> \ <xref:Microsoft.Data.SqlClient.Server.SqlDataRecord>-Objekten. Sie müssen mit der <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A>-Eigenschaft eines <xref:Microsoft.Data.SqlClient.SqlParameter> einen Typnamen für den Tabellenwertparameter angeben. Der `TypeName` muss dem Namen eines kompatiblen Typs entsprechen, der zuvor auf dem Server erstellt wurde. Im folgenden Code Fragment wird veranschaulicht, wie <xref:Microsoft.Data.SqlClient.SqlParameter> zum Einfügen von Daten konfiguriert wird.  
 
Im folgenden Beispiel enthält die Variable `addedCategories` eine <xref:System.Data.DataTable>. Informationen zum Füllen der Variablen finden Sie in den Beispielen im nächsten Abschnitt [übergeben eines Tabellenwert Parameters an eine gespeicherte Prozedur](#passing).

```csharp  
// Configure the command and parameter.  
SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
tvpParam.SqlDbType = SqlDbType.Structured;  
tvpParam.TypeName = "dbo.CategoryTableType";  
```   
  
Sie können auch jedes von <xref:System.Data.Common.DbDataReader> abgeleitete Objekt verwenden, um Datenzeilen per Streaming in einen Tabellenwertparameter zu übertragen, wie im folgenden Fragment dargestellt:  
  
```csharp  
// Configure the SqlCommand and table-valued parameter.  
SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
insertCommand.CommandType = CommandType.StoredProcedure;  
SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", dataReader);  
tvpParam.SqlDbType = SqlDbType.Structured;  
```  
  
## <a name="passing"></a> Übergeben eines Tabellenwertparameters an eine gespeicherte Prozedur  
In diesem Beispiel wird veranschaulicht, wie Tabellenwert Parameter-Daten an eine gespeicherte Prozedur übergeben werden. Der Code extrahiert hinzugefügte Zeilen in eine neue <xref:System.Data.DataTable> mithilfe der <xref:System.Data.DataTable.GetChanges%2A>-Methode. Im Code wird dann eine <xref:Microsoft.Data.SqlClient.SqlCommand> definiert, wobei die Eigenschaft <xref:Microsoft.Data.SqlClient.SqlCommand.CommandType%2A> auf <xref:System.Data.CommandType.StoredProcedure> festgelegt wird. Die <xref:Microsoft.Data.SqlClient.SqlParameter> wird mit der <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A>-Methode aufgefüllt, und die <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A> wird auf `Structured` festgelegt. Der <xref:Microsoft.Data.SqlClient.SqlCommand> wird dann mit der <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>-Methode ausgeführt.  
  
```csharp  
// Assumes connection is an open SqlConnection object.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Configure the SqlCommand and SqlParameter.  
  SqlCommand insertCommand = new SqlCommand("usp_InsertCategories", connection);  
  insertCommand.CommandType = CommandType.StoredProcedure;  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
### <a name="passing-a-table-valued-parameter-to-a-parameterized-sql-statement"></a>Übergeben eines Tabellenwert Parameters an eine parametrisierte SQL-Anweisung  
 Im folgenden Beispiel wird veranschaulicht, wie Daten in den dbo eingefügt werden. Kategorien Tabelle mithilfe einer INSERT-Anweisung mit einer SELECT-Unterabfrage, die über einen Tabellenwert Parameter als Datenquelle verfügt. Wenn Sie einen Tabellenwert Parameter an eine parametrisierte SQL-Anweisung übergeben, müssen Sie einen Typnamen für den Tabellenwert Parameter angeben, indem Sie die neue <xref:Microsoft.Data.SqlClient.SqlParameter.TypeName%2A>-Eigenschaft einer <xref:Microsoft.Data.SqlClient.SqlParameter> verwenden. Diese `TypeName` muss dem Namen eines kompatiblen Typs entsprechen, der zuvor auf dem Server erstellt wurde. Der Code in diesem Beispiel verwendet die `TypeName`-Eigenschaft, um auf die in dbo definierte Typstruktur zu verweisen. CategoryTableType.  
  
> [!NOTE]
>  Wenn Sie einen Wert für eine Identitäts Spalte in einem Tabellenwert Parameter angeben, müssen Sie die SET IDENTITY_INSERT-Anweisung für die Sitzung ausgeben.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
using (connection)  
{  
  // Create a DataTable with the modified rows.  
  DataTable addedCategories = CategoriesDataTable.GetChanges(DataRowState.Added);  

  // Define the INSERT-SELECT statement.  
  string sqlInsert =   
      "INSERT INTO dbo.Categories (CategoryID, CategoryName)"  
      + " SELECT nc.CategoryID, nc.CategoryName"  
      + " FROM @tvpNewCategories AS nc;"  

  // Configure the command and parameter.  
  SqlCommand insertCommand = new SqlCommand(sqlInsert, connection);  
  SqlParameter tvpParam = insertCommand.Parameters.AddWithValue("@tvpNewCategories", addedCategories);  
  tvpParam.SqlDbType = SqlDbType.Structured;  
  tvpParam.TypeName = "dbo.CategoryTableType";  

  // Execute the command.  
  insertCommand.ExecuteNonQuery();  
}  
```  
  
## <a name="streaming-rows-with-a-datareader"></a>Streamen von Zeilen mit einem DataReader  
Sie können auch jedes von <xref:System.Data.Common.DbDataReader> abgeleitete Objekt verwenden, um Datenzeilen per Streaming in einen Tabellenwertparameter zu übertragen. Das folgende Code Fragment veranschaulicht das Abrufen von Daten aus einer Oracle-Datenbank mithilfe einer <xref:System.Data.OracleClient.OracleCommand> und einer <xref:System.Data.OracleClient.OracleDataReader>. Der Code konfiguriert dann eine <xref:Microsoft.Data.SqlClient.SqlCommand>, um eine gespeicherte Prozedur mit einem einzelnen Eingabeparameter aufzurufen. Die <xref:Microsoft.Data.SqlClient.SqlParameter.SqlDbType%2A>-Eigenschaft der <xref:Microsoft.Data.SqlClient.SqlParameter> ist auf `Structured` festgelegt. Der <xref:Microsoft.Data.SqlClient.SqlParameterCollection.AddWithValue%2A> übergibt das `OracleDataReader` Resultset als Tabellenwert Parameter an die gespeicherte Prozedur.  
  
```csharp  
// Assumes connection is an open SqlConnection.  
// Retrieve data from Oracle.  
OracleCommand selectCommand = new OracleCommand(  
   "Select CategoryID, CategoryName FROM Categories;",  
   oracleConnection);  
OracleDataReader oracleReader = selectCommand.ExecuteReader(  
   CommandBehavior.CloseConnection);  
  
 // Configure the SqlCommand and table-valued parameter.  
 SqlCommand insertCommand = new SqlCommand(  
   "usp_InsertCategories", connection);  
 insertCommand.CommandType = CommandType.StoredProcedure;  
 SqlParameter tvpParam =  
    insertCommand.Parameters.AddWithValue(  
    "@tvpNewCategories", oracleReader);  
 tvpParam.SqlDbType = SqlDbType.Structured;  
  
 // Execute the command.  
 insertCommand.ExecuteNonQuery();  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datenvorgänge in ADO.NET](sql-server-data-operations.md)
