---
title: Anbieterstatistiken für SQL Server
description: Informationen zur Unterstützung des Abrufens von SQL Server-Laufzeitstatistiken.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 9a736eedf98d5e654f34423af8893cecda5a106f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925491"
---
# <a name="provider-statistics-for-sql-server"></a>Anbieterstatistiken für SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Ab . NET Framework 2.0 und .NET Core 1.0 unterstützt der Microsoft SqlClient-Datenanbieter für SQL Server Laufzeitstatistiken. Sie müssen Statistiken aktivieren, indem Sie die Eigenschaft <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> des <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts auf `True` festlegen, nachdem Sie ein gültiges Verbindungsobjekt erstellt haben. Nachdem Statistiken aktiviert wurden, können Sie sie als Momentaufnahme überprüfen, indem Sie einen <xref:System.Collections.IDictionary>-Verweis über die <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>-Methode des <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts abrufen. Sie zählen die Liste als eine Reihe von Wörterbucheinträgen in Form von Name-Wert-Paaren durch. Diese Name-Wert-Paare sind nicht geordnet. Sie können jederzeit die <xref:Microsoft.Data.SqlClient.SqlConnection.ResetStatistics%2A>-Methode des <xref:Microsoft.Data.SqlClient.SqlConnection>-Objekts zum Zurücksetzen der Zähler aufrufen. Wenn die Statistikerfassung nicht aktiviert ist, wird keine Ausnahme generiert. Wenn außerdem <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> aufgerufen wird, ohne dass zuvor <xref:Microsoft.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> aufgerufen wurde, sind die abgerufenen Werte die Anfangswerte jedes Eintrags. Wenn Sie Statistiken aktivieren, Ihre Anwendung eine Weile ausführen und Statistiken dann deaktivieren, spiegeln die abgerufenen Werte die Werte wider, die bis zu dem Punkt erfasst wurden, an dem Statistiken deaktiviert wurden. Alle erfassten statistischen Werte gelten verbindungsbezogen.  
  
## <a name="statistical-values-available"></a>Verfügbare statistische Werte  
Gegenwärtig bietet der Microsoft SQL Server-Anbieter 18 Elemente. Die Anzahl der verfügbaren Elemente kann über die **Count**-Eigenschaft des <xref:System.Collections.IDictionary>-Schnittstellenverweises abgerufen werden, die von <xref:Microsoft.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> zurückgegeben wird. Alle Zähler für Anbieterstatistiken verwenden den <xref:System.Int64>-CLR-Typ (Common Language Runtime) (**long** in C# und Visual Basic), der 64 Bit lang ist. Der maximale Wert des im Feld **int64.MaxValue** definierten **int64**-Datentyps beträgt ((2^63)-1)). Wenn die Werte für die Zähler diesen Maximalwert erreichen, dürfen sie nicht mehr als genau betrachtet werden. Das bedeutet, dass **int64.MaxValue**-1((2^63)-2) tatsächlich der größte gültige Wert für alle Statistiken ist.  
  
> [!NOTE]
>  Ein Wörterbuch wird für die Rückgabe von Anbieterstatistiken verwendet, da sich Anzahl, Namen und Reihenfolge der zurückgegebenen Statistiken in Zukunft ändern können. Anwendungen dürfen sich nicht darauf verlassen, dass ein bestimmter Wert im Wörterbuch zu finden ist, sondern müssen prüfen, ob der Wert vorhanden ist und entsprechend verzweigen.  
  
In der folgenden Tabelle werden die aktuell verfügbaren statistischen Werte beschrieben. Beachten Sie, dass die Schlüsselnamen für die einzelnen Werte in den regionalen Versionen von Microsoft .NET Framework und .NET Core nicht lokalisiert sind.  
  
|Schlüsselname|BESCHREIBUNG|  
|--------------|-----------------|  
|`BuffersReceived`|Gibt die Anzahl der TDS-Pakete (Tabular Data Stream) zurück, die der Anbieter von SQL Server empfangen hat, nachdem die Anwendung die Nutzung des Anbieters gestartet und Statistiken aktiviert hat.|  
|`BuffersSent`|Gibt die Anzahl der TDS-Pakete zurück, die vom Anbieter nach Aktivieren von Statistiken an SQL Server gesendet wurden. Für große Befehle sind möglicherweise mehrere Puffer erforderlich. Wenn z. B. ein großer Befehl an den Server gesendet wird und er sechs Pakete erfordert, wird `ServerRoundtrips` um 1 und `BuffersSent` um 6 erhöht.|  
|`BytesReceived`|Gibt die Anzahl der Datenbytes in den TDS-Paketen zurück, die der Anbieter von SQL Server empfangen hat, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.|  
|`BytesSent`|Gibt die Anzahl der Datenbytes zurück, die in TDS-Paketen an SQL Server gesendet wurden, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.|  
|`ConnectionTime`|Die Zeitspanne (in Millisekunden), für die die Verbindung nach dem Aktivieren der Statistik geöffnet war (die Gesamtverbindungszeit, wenn die Statistik vor dem Öffnen der Verbindung aktiviert wurde).|  
|`CursorOpens`|Gibt zurück, wie oft ein Cursor über die Verbindung geöffnet wurde, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.<br /><br /> Beachten Sie, dass schreibgeschützte/vorwärtsgerichtete Ergebnisse, die von SELECT-Anweisungen zurückgegeben werden, nicht als Cursor betrachtet werden und daher diesen Zähler nicht beeinflussen.|  
|`ExecutionTime`|Gibt die Gesamtzeitspanne (in Millisekunden) zurück, die der Anbieter seit dem Aktivieren der Statistik mit der Verarbeitung verbracht hat, einschließlich der Zeit zum Warten auf Antworten vom Server und zum Ausführen von Code im Anbieter selbst.<br /><br /> Die Klassen, die Zeitsteuerungscode enthalten, lauten:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Um leistungskritische Member so klein wie möglich zu halten, werden die folgenden Member nicht zeitgesteuert:<br /><br /> SqlDataReader<br /><br /> this []-Operator (alle Überladungen)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Gibt die Gesamtanzahl der über die Verbindung ausgeführten INSERT-, DELETE- und UPDATE-Anweisungen zurück, sobald die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.|  
|`IduRows`|Gibt die Gesamtanzahl der Zeilen zurück, die von INSERT-, DELETE- und UPDATE-Anweisungen betroffen sind, die über die Verbindung ausgeführt wurden, sobald die Anwendung mit der Verwendung des Anbieters begonnen und Statistiken aktiviert hat.|  
|`NetworkServerTime`|Gibt die kumulative Zeitspanne (in Millisekunden) zurück, die der Anbieter zum Warten auf Antworten vom Server verwendet hat, seitdem die Anwendung den Anbieter verwendet und die Statistik aktiviert hat.|  
|`PreparedExecs`|Gibt die Anzahl vorbereiteter Befehle zurück, die über die Verbindung ausgeführt wurden, sobald die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.|  
|`Prepares`|Gibt die Anzahl der über die Verbindung vorbereiteten Anweisungen zurück, sobald die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.|  
|`SelectCount`|Gibt die Anzahl der über die Verbindung ausgeführten SELECT-Anweisungen zurück, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat. Dazu gehören FETCH-Anweisungen zum Abrufen von Zeilen aus Cursorn. Der Zähler für SELECT-Anweisungen wird aktualisiert, wenn das Ende von <xref:Microsoft.Data.SqlClient.SqlDataReader> erreicht ist.|  
|`SelectRows`|Gibt die Anzahl der ausgewählten Zeilen zurück, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat. Dieser Zähler spiegelt alle von SQL-Anweisungen erstellten Zeilen wider, auch solche, die vom Aufrufer nicht wirklich genutzt wurden. Beispielsweise würde das Schließen eines Datenlesers vor dem Lesen des gesamten Resultsets die Anzahl nicht beeinflussen. Dies schließt die Zeilen ein, die von den Cursorn über FETCH-Anweisungen abgerufen werden.|  
|`ServerRoundtrips`|Gibt zurück, wie oft die Verbindung Befehle an den Server gesendet und eine Antwort erhalten hat, sobald die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.|  
|`SumResultSets`|Gibt die Anzahl der Resultsets zurück, die verwendet wurden, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat. Dies würde z. B. jedes an den Client zurückgegebene Resultset umfassen. Bei Cursorn wird jeder Abruf oder Blockabruf als unabhängiges Resultset betrachtet.|  
|`Transactions`|Gibt die Anzahl der Benutzertransaktionen zurück, die gestartet wurden, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken, einschließlich Rollbacks, aktiviert hat. Wenn eine Verbindung mit aktiviertem Autocommit ausgeführt wird, gilt jeder Befehl als Transaktion.<br /><br /> Dieser Zähler erhöht den Transaktionszähler, sobald eine BEGIN TRAN-Anweisung ausgeführt wird, unabhängig davon, ob die Transaktion committet oder später rückgängig gemacht wird.|  
|`UnpreparedExecs`|Gibt die Anzahl der über die Verbindung ausgeführten unvorbereiteten Anweisungen zurück, nachdem die Anwendung mit der Nutzung des Anbieters begonnen und Statistiken aktiviert hat.|  
  
### <a name="retrieving-a-value"></a>Abrufen eines Werts  
Die folgende Konsolenanwendung zeigt, wie Statistiken über eine Verbindung aktiviert, vier einzelne Statistikwerte abgerufen und in das Konsolenfenster geschrieben werden können.  
  
> [!NOTE]
>  Im folgenden Beispiel wird die in SQL Server enthaltene **AdventureWorks**-Beispieldatenbank verwendet. In der im Beispielcode bereitgestellten Verbindungszeichenfolge wird davon ausgegangen, dass die Datenbank auf dem lokalen Computer installiert und verfügbar ist. Ändern Sie die Verbindungszeichenfolge nach Bedarf für Ihre Umgebung.  
  
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
Die folgende Konsolenanwendung zeigt, wie Statistiken über eine Verbindung aktiviert, alle verfügbaren Statistikwerte mit dem Enumerator abgerufen und in das Konsolenfenster geschrieben werden können.  
  
> [!NOTE]
>  Im folgenden Beispiel wird die in SQL Server enthaltene **AdventureWorks**-Beispieldatenbank verwendet. In der im Beispielcode bereitgestellten Verbindungszeichenfolge wird davon ausgegangen, dass die Datenbank auf dem lokalen Computer installiert und verfügbar ist. Ändern Sie die Verbindungszeichenfolge nach Bedarf für Ihre Umgebung.  
  
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
