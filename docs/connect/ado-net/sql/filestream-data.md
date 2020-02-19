---
title: FILESTREAM-Daten
description: Beschreibt, wie Sie mit Daten mit großen Werten arbeiten, die in SQL Server 2008 mit dem FILESTREAM-Attribut gespeichert sind.
ms.date: 08/15/2019
ms.assetid: bd8b845c-0f09-4295-b466-97ef106eefa8
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 602dfe9c96c1e8713b90c607806dd09ed16a37b6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75247760"
---
# <a name="filestream-data"></a>FILESTREAM-Daten

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Das FILESTREAM-Speicherattribut ist für binäre (Blob-)Daten vorgesehen, die in einer Spalte des Typs „varbinary(max)“ gespeichert sind. Vor FILESTREAM erforderte das Speichern von Binärdaten eine spezielle Verarbeitung. Unstrukturierte Daten, wie z. B. Textdokumente, Bilder und Videos, werden oft außerhalb der Datenbank gespeichert und sind daher schwierig zu verwalten.

> [!NOTE]
> Sie müssen .NET Framework 3.5 SP1 (oder höher) oder .NET Core installieren, um mithilfe von SqlClient mit FILESTREAM-Daten arbeiten zu können.

Wenn das FILESTREAM-Attribut für eine varbinary(max)-Spalte festgelegt ist, werden die Daten von SQL Server im lokalen NTFS-Dateisystem und nicht in der Datenbankdatei gespeichert. Obwohl die Speicherung separat erfolgt, können dieselben Transact-SQL-Anweisungen verwendet werden, die für das Arbeiten mit in der Datenbank gespeicherten varbinary(max)-Daten unterstützt werden.

## <a name="sqlclient-support-for-filestream"></a>SqlClient-Unterstützung für FILESTREAM

Der Microsoft-SqlClient-Datenanbieter für SQL Server, <xref:Microsoft.Data.SqlClient>, unterstützt das Lesen und Schreiben von FILESTREAM-Daten mithilfe der im <xref:System.Data.SqlTypes>-Namespace definierten <xref:Microsoft.Data.SqlTypes.SqlFileStream>-Klasse. `SqlFileStream` erbt von der <xref:System.IO.Stream>-Klasse, die Methoden zum Lesen und Schreiben von Datenströmen zur Verfügung stellt. Beim Lesen aus einem Datenstrom werden Daten aus dem Datenstrom in eine Datenstruktur, z. B. ein Array von Bytes, übertragen. Beim Schreiben werden die Daten aus der Datenstruktur in einen Datenstrom übertragen.

### <a name="creating-the-sql-server-table"></a>Erstellen der SQL Server-Tabelle

Mit den folgenden Transact-SQL-Anweisungen wird eine Tabelle mit dem Namen „employees“ erstellt und eine Datenzeile eingefügt. Sobald Sie die FILESTREAM-Speicherung aktiviert haben, können Sie diese Tabelle in Verbindung mit den folgenden Codebeispielen verwenden. Die Links zu den Ressourcen in der SQL Server-Onlinedokumentation finden Sie am Ende dieses Themas.

```sql
CREATE TABLE employees
(
  EmployeeId INT  NOT NULL  PRIMARY KEY,
  Photo VARBINARY(MAX) FILESTREAM  NULL,
  RowGuid UNIQUEIDENTIFIER  NOT NULL  ROWGUIDCOL
  UNIQUE DEFAULT NEWID()
)
GO
Insert into employees
Values(1, 0x00, default)
GO
```

### <a name="example-reading-overwriting-and-inserting-filestream-data"></a>Beispiel: Lesen, Überschreiben und Einfügen von FILESTREAM-Daten

Das folgende Beispiel veranschaulicht, wie Daten aus einem FILESTREAM gelesen werden können. Der Code ruft den logischen Pfad zur Datei ab, wobei `FileAccess` auf `Read` und `FileOptions` auf `SequentialScan` festgelegt wird. Der Code liest dann die Bytes aus dem SqlFileStream in den Puffer ein. Die Bytes werden anschließend in das Konsolenfenster geschrieben.

Das Beispiel veranschaulicht auch, wie Daten in einen FILESTREAM geschrieben werden, wobei alle vorhandenen Daten überschrieben werden. Der Code ruft den logischen Pfad zur Datei ab und erstellt `SqlFileStream`, wobei `FileAccess` auf `Write` und `FileOptions` auf `SequentialScan` festgelegt wird. Ein einzelnes Byte wird in `SqlFileStream`geschrieben, wobei alle Daten in der Datei ersetzt werden.

Im Beispiel wird außerdem dargestellt, wie Daten unter Verwendung der „Seek“-Methode in einen FILESTREAM geschrieben werden, wobei die Daten ans Ende der Datei angehängt werden. Der Code ruft den logischen Pfad zur Datei ab und erstellt `SqlFileStream`, wobei `FileAccess` auf `ReadWrite` und `FileOptions` auf `SequentialScan` festgelegt wird. Der Code verwendet die Seek-Methode, um das Ende der Datei zu suchen, wobei ein einzelnes Byte an die vorhandene Datei angefügt wird.

```csharp
using System;
using Microsoft.Data.SqlClient;
using System.Data.SqlTypes;
using System.Data;
using System.IO;

namespace FileStreamTest
{
    class Program
    {
        static void Main(string[] args)
        {
            SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder("server=(local);integrated security=true;database=myDB");
            ReadFileStream(builder);
            OverwriteFileStream(builder);
            InsertFileStream(builder);

            Console.WriteLine("Done");
        }

        private static void ReadFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();
                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for the file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Read, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Read the contents as bytes and write them to the console
                            for (long index = 0; index < fileStream.Length; index++)
                            {
                                Console.WriteLine(fileStream.ReadByte());
                            }
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void OverwriteFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        // Create the SqlFileStream
                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.Write, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Write a single byte to the file. This will
                            // replace any data in the file.
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }
        }

        private static void InsertFileStream(SqlConnectionStringBuilder connStringBuilder)
        {
            using (SqlConnection connection = new SqlConnection(connStringBuilder.ToString()))
            {
                connection.Open();

                SqlCommand command = new SqlCommand("SELECT TOP(1) Photo.PathName(), GET_FILESTREAM_TRANSACTION_CONTEXT() FROM employees", connection);

                SqlTransaction tran = connection.BeginTransaction(IsolationLevel.ReadCommitted);
                command.Transaction = tran;

                using (SqlDataReader reader = command.ExecuteReader())
                {
                    while (reader.Read())
                    {
                        // Get the pointer for file
                        string path = reader.GetString(0);
                        byte[] transactionContext = reader.GetSqlBytes(1).Buffer;

                        using (Stream fileStream = new SqlFileStream(path, transactionContext, FileAccess.ReadWrite, FileOptions.SequentialScan, allocationSize: 0))
                        {
                            // Seek to the end of the file
                            fileStream.Seek(0, SeekOrigin.End);

                            // Append a single byte
                            fileStream.WriteByte(0x01);
                        }
                    }
                }
                tran.Commit();
            }

        }
    }
}
```

Ein weiteres Beispiel finden Sie unter [Speichern und Abrufen von Binärdaten in einer FILESTREAM-Spalte](https://www.codeproject.com/Articles/32216/How-to-store-and-fetch-binary-data-into-a-file-str).

## <a name="resources-in-sql-server-books-online"></a>Ressourcen in der SQL Server-Onlinedokumentation

Die vollständige Dokumentation für FILESTREAM finden Sie in den folgenden Abschnitten der SQL Server-Onlinedokumentation.

|Thema|Beschreibung|
|-----------|-----------------|
|[FILESTREAM (SQL Server)](../../../relational-databases/blob/filestream-sql-server.md)|Beschreibt, wann FILESTREAM-Speicher verwendet wird und wie dieser die SQL Server-Datenbank-Engine in ein NTFS-Dateisystem integriert.|
|[Erstellen von Clientanwendungen für FILESTREAM-Daten](../../../relational-databases/blob/create-client-applications-for-filestream-data.md)|Beschreibt die Windows-API-Funktionen für das Arbeiten mit FILESTREAM-Daten.|
|[FILESTREAM und andere SQL Server-Funktionen](../../../relational-databases/blob/filestream-compatibility-with-other-sql-server-features.md)|Enthält Überlegungen, Leitlinien und Einschränkungen für die Verwendung von FILESTREAM-Daten mit anderen Features von SQL Server.|

## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Datentypen und ADO.NET](sql-server-data-types.md)
- [Binäre Daten und Daten mit umfangreichen Werten in SQL Server](sql-server-binary-large-value-data.md)
