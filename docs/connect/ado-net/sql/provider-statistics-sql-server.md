---
title: Anbieterstatistiken für SQL Server
description: Beschreibt die Unterstützung für das Abrufen von SQL Server Lauf Zeit Statistiken.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 092cf63e62bce01e2a771ce4e5f7f46e1073e91a
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452064"
---
# <a name="provider-statistics-for-sql-server"></a>Anbieterstatistiken für SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Ab .NET Framework Version 2,0 und .net Core Version 1,0 unterstützt die Microsoft SqlClient-Datenanbieter für SQL Server Lauf Zeit Statistiken. Sie müssen die Statistik aktivieren, indem Sie die <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A>-Eigenschaft des <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts auf `True` festlegen, nachdem Sie ein gültiges Verbindungs Objekt erstellt haben. Nachdem die Statistik aktiviert wurde, können Sie Sie als "Momentaufnahme" in der Zeit überprüfen, indem Sie einen <xref:System.Collections.IDictionary> Verweis über die <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>-Methode des <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts abrufen. Die Liste wird als Satz von Name-Wert-Paar-Wörterbuch Einträgen aufgelistet. Diese Name-Wert-Paare sind nicht geordnet. Sie können jederzeit die <xref:Microsoft.Data.SqlClient.SqlConnection.ResetStatistics%2A>-Methode des <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts zum Zurücksetzen der Zähler abrufen. Wenn die Statistik Sammlung nicht aktiviert wurde, wird keine Ausnahme generiert. Wenn <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> zusätzlich aufgerufen wird, ohne dass <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> zuerst aufgerufen wurde, sind die abgerufenen Werte die Anfangswerte für jeden Eintrag. Wenn Sie Statistiken aktivieren, die Anwendung für eine Weile ausführen und dann die Statistik deaktivieren, entsprechen die abgerufenen Werte den Werten, die bis zu dem Zeitpunkt erfasst wurden, an dem die Statistik deaktiviert wurde. Alle gesammelten statistischen Werte sind pro Verbindung.  
  
## <a name="statistical-values-available"></a>Verfügbare statistische Werte  
Zurzeit sind 18 verschiedene Elemente des Microsoft SQL Server Anbieters verfügbar. Die Anzahl der verfügbaren Elemente kann über die **Count**-Eigenschaft des <xref:System.Collections.IDictionary>-Schnittstellenverweises abgerufen werden, die von <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> zurückgegeben wird. Alle Zähler für Anbieterstatistiken verwenden den <xref:System.Int64>-CLR-Typ (Common Language Runtime) (**long** in C# und Visual Basic), der 64 Bit lang ist. Der maximale Wert des im Feld **int64.MaxValue** definierten **int64**-Datentyps beträgt ((2^63)-1)). Wenn die Werte für die Leistungsindikatoren diesen maximalen Wert erreichen, sollten Sie nicht mehr als genau angesehen werden. Das bedeutet, dass **int64.MaxValue**-1((2^63)-2) tatsächlich der größte gültige Wert für alle Statistiken ist.  
  
> [!NOTE]
>  Zum Zurückgeben von Anbieter Statistiken wird ein Wörterbuch verwendet, da sich die Anzahl, die Namen und die Reihenfolge der zurückgegebenen Statistiken in Zukunft ändern können. Anwendungen sollten sich nicht darauf verlassen, dass ein bestimmter Wert im Wörterbuch gefunden wird, sondern stattdessen überprüfen, ob der Wert vorhanden ist, und entsprechend verzweigen.  
  
In der folgenden Tabelle werden die verfügbaren aktuellen statistischen Werte beschrieben. Beachten Sie, dass die Schlüsselnamen für die einzelnen Werte nicht über regionale Versionen von Microsoft .NET Framework und .net Core lokalisiert werden.  
  
|Schlüsselname|und Beschreibung|  
|--------------|-----------------|  
|`BuffersReceived`|Gibt die Anzahl der TDS-Pakete (Tabular Data Stream) zurück, die vom Anbieter von SQL Server empfangen wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`BuffersSent`|Gibt die Anzahl der TDS-Pakete zurück, die vom Anbieter nach dem Aktivieren der Statistik an SQL Server gesendet wurden. Für große Befehle sind möglicherweise mehrere Puffer erforderlich. Wenn z. b. ein großer Befehl an den Server gesendet wird und sechs Pakete erforderlich sind, wird `ServerRoundtrips` um 1 erhöht, und `BuffersSent` wird um sechs erhöht.|  
|`BytesReceived`|Gibt die Anzahl der Daten Bytes in den TDS-Paketen zurück, die vom Anbieter von SQL Server empfangen wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`BytesSent`|Gibt die Anzahl der Daten Bytes zurück, die in TDS-Paketen an SQL Server gesendet werden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`ConnectionTime`|Die Zeitspanne (in Millisekunden), für die die Verbindung nach dem Aktivieren der Statistik geöffnet war (die Gesamtverbindungszeit, wenn die Statistik vor dem Öffnen der Verbindung aktiviert wurde).|  
|`CursorOpens`|Gibt an, wie oft ein Cursor über die Verbindung geöffnet wurde, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.<br /><br /> Beachten Sie, dass die schreibgeschützten/vorwärts gerichteten Ergebnisse, die von SELECT-Anweisungen zurückgegeben werden, nicht als Cursor angesehen werden und sich daher nicht auf diesen Wert auswirken.|  
|`ExecutionTime`|Gibt die Gesamtzeitspanne (in Millisekunden) zurück, die der Anbieter seit dem Aktivieren der Statistik mit der Verarbeitung verbracht hat, einschließlich der Zeit zum Warten auf Antworten vom Server und zum Ausführen von Code im Anbieter selbst.<br /><br /> Die Klassen, die Zeit Steuerungs Code enthalten, lauten:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Um die für die Leistung wichtigen Elemente so klein wie möglich zu halten, werden die folgenden Member nicht zeitlich zeitlich formatit:<br /><br /> SqlDataReader<br /><br /> this []-Operator (alle über Ladungen)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Gibt die Gesamtzahl der INSERT-, DELETE-und Update-Anweisungen zurück, die über die Verbindung ausgeführt wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`IduRows`|Gibt die Gesamtanzahl der Zeilen zurück, die von den INSERT-, DELETE-und Update-Anweisungen betroffen sind, die über die Verbindung ausgeführt wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`NetworkServerTime`|Gibt die kumulative Zeitspanne (in Millisekunden) zurück, die der Anbieter zum Warten auf Antworten vom Server verwendet hat, seitdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`PreparedExecs`|Gibt die Anzahl der vorbereiteten Befehle zurück, die über die Verbindung ausgeführt wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`Prepares`|Gibt die Anzahl der Anweisungen zurück, die über die Verbindung vorbereitet wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`SelectCount`|Gibt die Anzahl der SELECT-Anweisungen zurück, die über die Verbindung ausgeführt wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat. Dies umfasst FETCH-Anweisungen zum Abrufen von Zeilen aus Cursorn, und die Anzahl von SELECT-Anweisungen wird aktualisiert, wenn das Ende einer <xref:Microsoft.Data.SqlClient.SqlDataReader> erreicht wird.|  
|`SelectRows`|Gibt die Anzahl der ausgewählten Zeilen zurück, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat. Dieser Wert gibt alle Zeilen wieder, die von SQL-Anweisungen generiert wurden, auch solche, die nicht tatsächlich vom Aufrufer genutzt wurden. Beispielsweise würde das Schließen eines Daten Readers vor dem Lesen des gesamten Resultsets keine Auswirkung auf die Anzahl haben. Dies schließt die Zeilen ein, die von Cursorn durch Abruf Anweisungen abgerufen werden|  
|`ServerRoundtrips`|Gibt an, wie oft die Verbindung Befehle an den Server gesendet und eine Antwort erhalten hat, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`SumResultSets`|Gibt die Anzahl der Resultsets zurück, die verwendet wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat. Dies würde beispielsweise alle Resultsets einschließen, die an den Client zurückgegeben werden. Bei Cursorn wird jeder Abruf-oder Block Abruf Vorgang als unabhängiges Resultset betrachtet.|  
|`Transactions`|Gibt die Anzahl der Benutzer Transaktionen zurück, die gestartet werden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat, einschließlich Rollbacks. Wenn eine Verbindung mit Autocommit on ausgeführt wird, wird jeder Befehl als Transaktion behandelt.<br /><br /> Dieser Zähler erhöht die Transaktions Anzahl, sobald eine BEGIN TRAN-Anweisung ausgeführt wird, unabhängig davon, ob für die Transaktion ein Commit oder ein Rollback ausgeführt wird.|  
|`UnpreparedExecs`|Gibt die Anzahl der nicht vorbereiteten Anweisungen zurück, die über die Verbindung ausgeführt wurden, nachdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
  
### <a name="retrieving-a-value"></a>Abrufen eines Werts  
Die folgende Konsolenanwendung zeigt, wie Sie Statistiken für eine Verbindung aktivieren, vier einzelne Statistik Werte abrufen und Sie in das Konsolenfenster schreiben.  
  
> [!NOTE]
>  Im folgenden Beispiel wird die in SQL Server enthaltene **AdventureWorks**-Beispieldatenbank verwendet. Die im Beispielcode angegebene Verbindungs Zeichenfolge setzt voraus, dass die Datenbank auf dem lokalen Computer installiert und verfügbar ist. Ändern Sie die Verbindungs Zeichenfolge nach Bedarf für Ihre Umgebung.  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Abrufen aller Werte  
Die folgende Konsolenanwendung zeigt, wie Sie Statistiken für eine Verbindung aktivieren, alle verfügbaren Statistik Werte mithilfe des Enumerators abrufen und in das Konsolenfenster schreiben.  
  
> [!NOTE]
>  Im folgenden Beispiel wird die in SQL Server enthaltene **AdventureWorks**-Beispieldatenbank verwendet. Die im Beispielcode angegebene Verbindungs Zeichenfolge setzt voraus, dass die Datenbank auf dem lokalen Computer installiert und verfügbar ist. Ändern Sie die Verbindungs Zeichenfolge nach Bedarf für Ihre Umgebung.  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using Microsoft.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server und ADO.NET](index.md)
