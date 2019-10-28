---
title: Ändern von Daten mit umfangreichen Werten (max) in ADO.NET
description: Beschreibt das Arbeiten mit Datentypen mit umfangreichen Werten.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: fac55eb25f89ced173683d5ed5d4334c2fcde975
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452122"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Ändern von Daten mit umfangreichen Werten (max) in ADO.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Bei Large Object-Datentypen (LOB) übersteigt die Zeilengröße die maximal zulässige Zeilengröße von 8 KB. SQL Server  bietet einen `max`-Spezifizierer für die Datentypen `varchar`, `nvarchar` und `varbinary`, der das Speichern von 2^32 Bytes großen Werten ermöglicht. Tabellen Spalten und Transact-SQL-Variablen können `varchar(max)`-, `nvarchar(max)`-oder `varbinary(max)`-Datentypen angeben. In NET können die `max`-Datentypen durch einen `DataReader` abgerufen werden. Außerdem können sie ohne spezielle Behandlung sowohl als Eingabe- als auch als Ausgabeparameterwerte angegeben werden. Für große `varchar` Datentypen können Daten inkrementell abgerufen und aktualisiert werden.  
  
Die `max`-Datentypen können für Vergleiche, als Transact-SQL-Variablen und zum Verketten verwendet werden. Sie können auch in den unterschiedlichen Klauseln ORDER by, Group by einer SELECT-Anweisung sowie in Aggregaten, Joins und Unterabfragen verwendet werden.

Weitere Informationen zu Datentypen mit umfangreichen Werten finden [Sie unter Verwenden von Datentypen mit umfangreichen Werten](https://go.microsoft.com/fwlink/?LinkId=120498) SQL Server-Onlinedokumentation.
  
## <a name="large-value-type-restrictions"></a>Einschränkungen für große Werttypen  
Die folgenden Einschränkungen gelten für die `max`-Datentypen, die für kleinere Datentypen nicht vorhanden sind:  
  
- Eine `sql_variant` kann keinen großen `varchar` Datentyp enthalten.  
  
- Große `varchar` Spalten können nicht als Schlüssel Spalte in einem Index angegeben werden. Sie sind in einer inklusivspalte in einem nicht gruppierten Index zulässig.  
  
- Große `varchar` Spalten können nicht als Partitionierungsschlüssel Spalten verwendet werden.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Arbeiten mit großen Werttypen in Transact-SQL  
Die Transact-SQL-`OPENROWSET` Funktion ist eine einmalige Methode zum Herstellen einer Verbindung und zum Zugreifen auf Remote Daten. Auf `OPENROWSET` kann in der FROM-Klausel einer Abfrage so verwiesen werden, als ob es ein Tabellenname wäre. Darauf kann auch als Zieltabelle einer INSERT-, UPDATE- oder DELETE-Anweisung verwiesen werden.  
  
Die `OPENROWSET`-Funktion enthält den `BULK` Rowsetanbieter, mit dem Sie Daten direkt aus einer Datei lesen können, ohne die Daten in eine Ziel Tabelle zu laden. Auf diese Weise können Sie `OPENROWSET` in einer einfachen INSERT SELECT-Anweisung verwenden.  
  
Die Optionsargumente von `OPENROWSET BULK` ermöglichen die flexible Festlegung, wo mit dem Lesen von Daten angefangen und aufgehört werden soll, wie mit Fehlern umzugehen ist und wie Daten interpretiert werden. Beispielsweise können Sie angeben, dass die Datendatei als einzeiliges, einspaltiges Rowset vom Datentyp `varbinary`, `varchar` oder `nvarchar` gelesen wird. Die gesamte Syntax und die Optionen finden Sie unter SQL Server-Onlinedokumentation.  
  
Im folgenden Beispiel wird ein Foto in die ProductPhoto-Tabelle der AdventureWorks-Beispieldatenbank eingefügt. Wenn Sie den `BULK OPENROWSET`-Anbieter verwenden, müssen Sie die benannte Liste der Spalten auch dann angeben, wenn Sie nicht in jeder Spalte Werte einfügen. Der Primärschlüssel ist in diesem Fall als Identitäts Spalte definiert und kann in der Spaltenliste ausgelassen werden. Beachten Sie, dass Sie am Ende der `OPENROWSET`-Anweisung, die in diesem Fall thumbnailPhoto ist, auch einen Korrelations Namen angeben müssen. Dies korreliert mit der Spalte in der `ProductPhoto` Tabelle, in die die Datei geladen wird.  
  
```sql
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a>Aktualisieren von Daten mithilfe von UPDATE .WRITE  
Die Transact-SQL-Update-Anweisung verfügt über neue Schreib Syntax zum Ändern des Inhalts von `varchar(max)`-, `nvarchar(max)`-oder `varbinary(max)` Spalten. Dies ermöglicht es Ihnen, partielle Updates der Daten auszuführen. Das Update. Die Schreib Syntax wird hier in abgekürzten Form angezeigt:  
  
UPDATE  
  
{ *\<object>* }  
  
SET  
  
{ *column_name* = {. Write ( *Ausdruck* , @Offset @Length)}  
  
Die WRITE-Methode gibt an, dass ein Abschnitt des Werts von *colum_name* geändert wird. Der Ausdruck ist der Wert, der in *column_name* kopiert wird, `@Offset` ist der Anfangspunkt, ab dem der Ausdruck geschrieben wird, und das `@Length`-Argument gibt die Länge des Abschnitts in der Spalte an.  
  
|Wenn|Then|  
|--------|----------|  
|Der Ausdruck wird auf NULL festgelegt.|`@Length` wird ignoriert, und der Wert in *column_name* wird am angegebenen `@Offset` abgeschnitten.|  
|`@Offset` ist NULL|Beim Updatevorgang wird der Ausdruck am Ende des vorhandenen Werts *column_name* angefügt, und `@Length` wird ignoriert.|  
|`@Offset` ist größer als die Länge des column_name-Werts.|SQL Server gibt einen Fehler zurück.|  
|`@Length` ist NULL|Der Updatevorgang entfernt alle Daten aus `@Offset` bis zum Ende des `column_name`-Werts.|  
  
> [!NOTE]
>  Weder `@Offset` noch `@Length` kann eine negative Zahl sein.  
  
## <a name="example"></a>Beispiel  
Dieses Transact-SQL-Beispiel aktualisiert einen partiellen Wert in DocumentSummary, eine `nvarchar(max)` Spalte in der Document-Tabelle der AdventureWorks-Datenbank. Der Begriff „components“ wird durch den Begriff „features“ ersetzt, indem der Ersatzbegriff, die Anfangsposition (offset) des zu ersetzenden Begriffs in den vorhandenen Daten und die Anzahl der zu ersetzenden Zeichen (length) angegeben werden. Das Beispiel umfasst SELECT-Anweisungen vor und nach der Update-Anweisung, um die Ergebnisse zu vergleichen.  
  
```sql
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a>Arbeiten mit großen Werttypen in ADO.NET  
Sie können in ADO.NET mit großen Werttypen arbeiten, indem Sie große Werttypen als <xref:Microsoft.Data.SqlClient.SqlParameter>-Objekte in einem <xref:Microsoft.Data.SqlClient.SqlDataReader> angeben, damit ein Resultset zurückgegeben wird, oder indem Sie mithilfe eines <xref:Microsoft.Data.SqlClient.SqlDataAdapter> ein `DataSet`/ oder eine `DataTable` füllen. Es gibt keinen Unterschied zwischen dem Arbeiten mit einem großen Werttyp und dem zugehörigen, kleineren Wert Datentyp.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Verwenden von GE-qlbytes zum Abrufen von Daten  
Die `GetSqlBytes`-Methode des <xref:Microsoft.Data.SqlClient.SqlDataReader> kann zum Abrufen des Inhalts einer `varbinary(max)` Spalte verwendet werden. Im folgenden Code Fragment wird von einem <xref:Microsoft.Data.SqlClient.SqlCommand> Objekt mit dem Namen `cmd` ausgegangen, das `varbinary(max)` Daten aus einer Tabelle auswählt, und ein <xref:Microsoft.Data.SqlClient.SqlDataReader> Objekt mit dem Namen `reader`, das die Daten als <xref:System.Data.SqlTypes.SqlBytes> abruft.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Verwenden von gezaren qlchars zum Abrufen von Daten  
Die `GetSqlChars`-Methode des <xref:Microsoft.Data.SqlClient.SqlDataReader> kann zum Abrufen des Inhalts einer `varchar(max)` oder `nvarchar(max)` Spalte verwendet werden. Im folgenden Code Fragment wird von einem <xref:Microsoft.Data.SqlClient.SqlCommand> Objekt mit dem Namen `cmd` ausgegangen, das `nvarchar(max)` Daten aus einer Tabelle auswählt, und ein <xref:Microsoft.Data.SqlClient.SqlDataReader> Objekt mit dem Namen `reader`, das die Daten abruft.   
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Verwenden von geout qlbinary zum Abrufen von Daten  
Die `GetSqlBinary`-Methode einer <xref:Microsoft.Data.SqlClient.SqlDataReader> kann zum Abrufen des Inhalts einer `varbinary(max)` Spalte verwendet werden. Im folgenden Code Fragment wird von einem <xref:Microsoft.Data.SqlClient.SqlCommand> Objekt mit dem Namen `cmd` ausgegangen, das `varbinary(max)` Daten aus einer Tabelle auswählt, und ein <xref:Microsoft.Data.SqlClient.SqlDataReader> Objekt mit dem Namen `reader`, das die Daten als <xref:System.Data.SqlTypes.SqlBinary> Datenstrom abruft.  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a>Verwenden von GetBytes zum Abrufen von Daten  
Die `GetBytes`-Methode einer <xref:Microsoft.Data.SqlClient.SqlDataReader> liest einen Byte Datenstrom aus dem angegebenen Spalten Offset in ein Bytearray, beginnend am angegebenen Array Offset. Im folgenden Code Fragment wird von einem <xref:Microsoft.Data.SqlClient.SqlDataReader> Objekt mit dem Namen `reader` ausgegangen, das Bytes in ein Bytearray abruft. Beachten Sie, dass `GetBytes` im Gegensatz zu `GetSqlBytes` eine Größe für den Array Puffer erfordert.  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a>Verwenden von GetValue zum Abrufen von Daten  
Die `GetValue`-Methode einer <xref:Microsoft.Data.SqlClient.SqlDataReader> liest den Wert aus dem angegebenen Spalten Offset in ein Array. Im folgenden Code Fragment wird von einem <xref:Microsoft.Data.SqlClient.SqlDataReader> Objekt mit dem Namen `reader` ausgegangen, das binäre Daten aus dem ersten Spalten Offset abruft, und dann Zeichen folgen Daten aus dem zweiten Spalten Offset.  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Wandeln von großen Werttypen in CLR-Typen  
Sie können den Inhalt einer `varchar(max)` oder `nvarchar(max)` Spalte mit einer der Zeichen folgen Konvertierungs Methoden, z. b. `ToString`, konvertieren. Das folgende Code Fragment geht von einem <xref:Microsoft.Data.SqlClient.SqlDataReader> Objekt mit dem Namen `reader` aus, das die Daten abruft.  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a>Beispiel  
Der folgende Code Ruft den Namen und das `LargePhoto` Objekt aus der `ProductPhoto` Tabelle in der `AdventureWorks` Datenbank ab und speichert Sie in einer Datei. Die Assembly muss mit einem Verweis auf den <xref:System.Drawing> Namespace kompiliert werden.  Die <xref:Microsoft.Data.SqlClient.SqlDataReader.GetSqlBytes%2A>-Methode der <xref:Microsoft.Data.SqlClient.SqlDataReader> gibt ein <xref:System.Data.SqlTypes.SqlBytes> Objekt zurück, das eine `Stream` Eigenschaft verfügbar macht. Der Code verwendet diese, um ein neues `Bitmap`-Objekt zu erstellen, das dann im `ImageFormat` GIF gespeichert wird.  
  
[!code-csharp[DataWorks SqlBytes_Stream#1](~/../sqlclient/doc/samples/SqlBytes_Stream.cs#1)]
  
## <a name="using-large-value-type-parameters"></a>Verwenden von Parametern für den großen Wert  
Große Werttypen können in <xref:Microsoft.Data.SqlClient.SqlParameter> Objekten auf dieselbe Weise wie kleinere Werttypen in <xref:Microsoft.Data.SqlClient.SqlParameter> Objekten verwendet werden. Sie können große Werttypen als <xref:Microsoft.Data.SqlClient.SqlParameter>-Werte abrufen, wie im folgenden Beispiel dargestellt. Der Code geht davon aus, dass die folgende gespeicherte GetDocumentSummary-Prozedur in der AdventureWorks-Beispieldatenbank vorhanden ist. Die gespeicherte Prozedur verwendet einen Eingabeparameter mit dem Namen „@DocumentID“ und gibt den Inhalt der Spalte „DocumentSummary“ im @DocumentSummary-Ausgabeparameter zurück.  
  
```sql
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a>Beispiel  
Der ADO.NET-Code erstellt <xref:Microsoft.Data.SqlClient.SqlConnection> und <xref:Microsoft.Data.SqlClient.SqlCommand> Objekte, um die gespeicherte Prozedur GetDocumentSummary auszuführen und die Dokument Zusammenfassung abzurufen, die als großer Werttyp gespeichert wird. Der Code übergibt einen Wert für den @DocumentID-Eingabeparameter, und die im @DocumentSummary-Ausgabeparameter zurückgegebenen Ergebnisse werden im Konsolenfenster angezeigt.  
  
[!code-csharp[DataWorks SqlParameter_Value#1](~/../sqlclient/doc/samples/SqlParameter_Value.cs#1)]
  
## <a name="next-steps"></a>Nächste Schritte
- [Binäre Daten und Daten mit umfangreichen Werten in SQL Server](sql-server-binary-large-value-data.md)
- [SQL Server-Datenvorgänge in ADO.NET](sql-server-data-operations.md)
