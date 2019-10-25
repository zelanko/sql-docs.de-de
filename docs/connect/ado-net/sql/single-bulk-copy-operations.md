---
title: Einzelne Massenkopiervorgänge
description: Beschreibt das Ausführen eines einzelnen Massen Kopierens von Daten in eine Instanz von SQL Server mithilfe der SqlBulkCopy-Klasse und das Ausführen des Massen Kopiervorgangs mithilfe von Transact-SQL-Anweisungen und der SqlCommand-Klasse.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 792ebcb5a4365301c31362a748d786c17ddee42a
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452094"
---
# <a name="single-bulk-copy-operations"></a>Einzelne Massenkopiervorgänge

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Die einfachste Herangehensweise an einen SQL Server-Massenkopiervorgang ist das Durchführen eines einzelnen Vorgangs für eine Datenbank. Standardmäßig wird ein Massenkopiervorgang als isolierter Vorgang ausgeführt: Der Kopiervorgang erfolgt in nicht transaktionaler Weise, ohne Möglichkeit zum Rollback.  
  
> [!NOTE]
>  Wenn Sie für den Massenkopiervorgang beim Auftreten eines Fehlers einen teilweisen oder vollständigen Rollback ausführen müssen, können Sie entweder eine von <xref:Microsoft.Data.SqlClient.SqlBulkCopy> verwaltete Transaktion verwenden oder den Massenkopiervorgang innerhalb einer vorhandenen Transaktion ausführen. **SqlBulkCopy** funktioniert auch mit <xref:System.Transactions>, wenn die Verbindung (implizit oder explizit) in eine **System.Transactions**-Transaktion eingetragen wurde.  
>   
>  Weitere Informationen finden Sie unter [Transaktionen und Massenkopiervorgänge](transaction-bulk-copy-operations.md).  
  
Die allgemeinen Schritte zum Ausführen eines Massen Kopiervorgangs lauten wie folgt:  
  
1. Herstellen einer Verbindung mit dem Quellserver und Abrufen der zu kopierenden Daten. Daten können auch aus anderen Quellen stammen, wenn Sie von einem <xref:System.Data.IDataReader> oder <xref:System.Data.DataTable> Objekt abgerufen werden können.  
  
2. Stellen Sie eine Verbindung mit dem Zielserver her (sofern die Verbindung nicht von **SqlBulkCopy** hergestellt werden soll).  
  
3. Erstellen Sie ein <xref:Microsoft.Data.SqlClient.SqlBulkCopy> Objekt, und legen Sie alle erforderlichen Eigenschaften fest.  
  
4. Legen Sie die **DestinationTableName**-Eigenschaft fest, um die Zieltabelle für den Masseneinfügevorgang anzugeben.  
  
5. Rufen Sie eine der **WriteToServer**-Methoden auf.  
  
6. Optional können Sie Eigenschaften aktualisieren und **WriteToServer** bei Bedarf erneut aufrufen.  
  
7. Ruft <xref:Microsoft.Data.SqlClient.SqlBulkCopy.Close%2A> auf oder packt die Massen Kopiervorgänge innerhalb einer `Using` Anweisung.  
  
> [!CAUTION]
>  Wir empfehlen die Verwendung gleicher Datentypen für Quell- und Zielspalten. Wenn die Datentypen nicht übereinstimmen, versucht **SqlBulkCopy**, die einzelnen Quellwerte anhand der vom <xref:Microsoft.Data.SqlClient.SqlParameter.Value%2A> angewendeten Regeln in den Zieldatentyp zu konvertieren. Konvertierungen wirken sich negativ auf die Leistung aus und können außerdem zu unerwarteten Fehlern führen. Beispielsweise kann ein Datentyp `Double` in den meisten Fällen in den Datentyp `Decimal` konvertiert werden, aber nicht immer.  
  
## <a name="example"></a>Beispiel  
In der folgenden Konsolenanwendung wird veranschaulicht, wie Daten mithilfe der <xref:Microsoft.Data.SqlClient.SqlBulkCopy>-Klasse geladen werden. In diesem Beispiel werden in der SQL Server-Datenbank **AdventureWorks** unter Verwendung von <xref:Microsoft.Data.SqlClient.SqlDataReader> Daten aus der Tabelle **Production.Product** in eine ähnliche Tabelle derselben Datenbank kopiert.  
  
> [!IMPORTANT]
>  Dieses Beispiel wird nur ausgeführt, wenn Sie die Arbeitstabellen zuvor wie unter [Massenkopierbeispiel-Einrichtung](bulk-copy-example-setup.md) beschrieben erstellt haben. Der angegebene Code dient nur zur Demonstration der Syntax für die Verwendung von **SqlBulkCopy**. Wenn sich die Quell- und Zieltabellen in der gleichen SQL Server-Instanz befinden, ist die Verwendung einer Transact-SQL-Anweisung `INSERT … SELECT` zum Kopieren der Daten einfacher und schneller.  
  
[!code-csharp[DataWorks SqlBulkCopy_WriteToServer#1](~/../sqlclient/doc/samples/SqlBulkCopy_WriteToServer.cs#1)]
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a>Ausführen eines Massen Kopiervorgangs mithilfe von Transact-SQL und der Command-Klasse  
Das folgende Beispiel zeigt die Verwendung der Methode <xref:Microsoft.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> zum Ausführen der Anweisung BULK INSERT.  
  
> [!NOTE]
>  Der Dateipfad für die Datenquelle ist relativ zum Server. Der Serverprozess muss Zugriff auf diesen Pfad besitzen, damit der Massenkopiervorgang erfolgreich ausgeführt werden kann.  
  
```csharp  
using (SqlConnection connection = New SqlConnection(connectionString))  
{  
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +  
    "FROM 'f:\mydata\data.tbl' " +  
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";  
connection.Open();  
SqlCommand command = new SqlCommand(queryString, connection);  
  
command.ExecuteNonQuery();  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [Massenkopiervorgänge in SQL Server](bulk-copy-operations-sql-server.md)
