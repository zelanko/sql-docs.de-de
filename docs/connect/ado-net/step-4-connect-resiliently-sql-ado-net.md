---
title: 'Schritt 4: Herstellen stabiler SQL-Verbindungen mit ADO.NET | Microsoft-Dokumentation'
description: In diesem Schritt wird beschrieben, wie Sie stabile Verbindungen zu SQL herstellen.
ms.custom: ''
ms.date: 08/15/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e0a042c6c5e937c08e5bcc6402caa8338f22b332
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78895834"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Schritt 4: Herstellen stabiler SQL-Verbindungen mit ADO.NET

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

- Vorheriger Artikel:&nbsp;&nbsp;&nbsp;[Schritt 3: Proof of Concept für Verbindungen mit SQL mithilfe von ADO.NET](step-3-connect-sql-ado-net.md)  

  
Dieses Thema enthält ein C#-Codebeispiel zur Veranschaulichung einer benutzerdefinierten Wiederholungslogik. Die Wiederholungslogik sorgt für Zuverlässigkeit. Die Wiederholungslogik dient zum ordnungsgemäßen Verarbeiten von *vorübergehenden Fehlern*, die meist nicht mehr vorhanden sind, wenn das Programm mehrere Sekunden wartet und es dann erneut versucht.  
  
Quellen vorübergehender Fehler sind u. a.:  
  
- Ein kurzer Ausfall des Netzwerks, das das Internet unterstützt.  
- Ein Cloudsystem kann zum Zeitpunkt des Absendens Ihrer Abfrage einen Lastenausgleich seiner Ressourcen vornehmen.  
  
  
ADO.NET-Klassen für die Verbindung mit Ihrem lokalen Microsoft SQL Server können auch Verbindungen mit Azure SQL-Datenbanken herstellen. Allerdings können die ADO.NET-Klassen allein nicht die ganze Stabilität und Zuverlässigkeit bieten, die für den Produktionseinsatz erforderlich sind. Ihr Clientprogramm kann auf vorübergehende Fehler stoßen, von denen es sich ohne Benutzereingriff ordnungsgemäß erholen sollte, um anschließend selbständig weiterzuarbeiten.  
  
## <a name="step-1-identify-transient-errors"></a>Schritt 1: Ermitteln vorübergehender Fehler  
  
Ihr Programm muss zwischen vorübergehenden Fehlern und beständigen Fehlern unterscheiden. Vorübergehende Fehler sind Fehlerbedingungen, die sich innerhalb kurzer Zeit auflösen können, wie z. B. zeitweilige Netzwerkprobleme.  Ein Beispiel eines dauerhaften Fehlers wäre, wenn in Ihrem Programm ein Schreibfehler im Namen der Zieldatenbank vorliegt. In diesem Fall würde der Fehler "Keine solche Datenbank gefunden" bestehen bleiben und keine Chance haben, sich innerhalb kurzer Zeit zu korrigieren.  
  
Die Liste der Fehlernummern, die als vorübergehende Fehler kategorisiert sind, finden Sie unter [Fehlermeldungen für SQL-Datenbank-Clientanwendungen](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/).  
  
## <a name="step-2-create-and-run-sample-application"></a>Schritt 2: Erstellen und Ausführen einer Beispielanwendung  
  
Bei dem Beispiel wird davon ausgegangen, dass .NET Framework 4.5.1 oder höher installiert ist.  Das C#-Codebeispiel besteht aus einer Datei mit dem Namen "Program.cs". Den Code dazu finden Sie im nächsten Abschnitt.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Schritt 2.a: Erfassen und Kompilieren des Codebeispiels  
  
Sie können das Beispiel mit den folgenden Schritten kompilieren:  
  
1. Erstellen Sie in der [kostenlosen Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)ein neues Projekt mit der Vorlage für die C#-Konsolenanwendung.  
    - "Datei" > "Neu" > Projekt" > "Installiert" > "Vorlagen" > "Visual C#" > "Windows" > "Klassischer Desktop" > "Konsolenanwendung"  
    - Geben Sie dem Projekt den Namen **RetryAdo2**.  
2. Öffnen Sie den Bereich „Projektmappen-Explorer“.  
    - Beachten Sie den Namen des Projekts.  
    - Beachten Sie den Namen der Datei "Program.cs".  
3. Öffnen Sie die Datei „Program.cs“.  
4. Ersetzen Sie den gesamten Inhalt der Datei "Program.cs" durch den Code im folgenden Codeblock.  
5. Klicken Sie auf das Menü "Build" > "Projektmappe erstellen".  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Schritt 2.b: Kopieren und Einfügen des Beispielcodes  
  
Fügen Sie diesen Code in die Datei **Program.cs** ein.  
  
Anschließend müssen Sie die Zeichenfolgen für Servername, Kennwort usw. bearbeiten. Sie finden diese Zeichenfolgen in der Methode namens **GetSqlConnectionStringBuilder**.  
  
HINWEIS:  Die Verbindungszeichenfolge für den Servernamen ist auf Azure SQL-Datenbank ausgerichtet, da sie das vier Zeichen lange Präfix **tcp:** enthält. Sie können jedoch die Serverzeichenfolge für die Verbindung mit Ihrer Microsoft SQL Server-Instanz anpassen.  
  
  
```csharp
using System;  // C#  
using CG = System.Collections.Generic;  
using QC = Microsoft.Data.SqlClient;  
using TD = System.Threading;  
    
namespace RetryAdo2  
{  
  public class Program  
  {  
    static public int Main(string[] args)  
    {  
      bool succeeded = false;  
      int totalNumberOfTimesToTry = 4;  
      int retryIntervalSeconds = 10;  
    
      for (int tries = 1;  
        tries <= totalNumberOfTimesToTry;  
        tries++)  
      {  
        try  
        {  
          if (tries > 1)  
          {  
            Console.WriteLine  
              ("Transient error encountered. Will begin attempt number {0} of {1} max...",  
              tries, totalNumberOfTimesToTry  
              );  
            TD.Thread.Sleep(1000 * retryIntervalSeconds);  
            retryIntervalSeconds = Convert.ToInt32  
              (retryIntervalSeconds * 1.5);  
          }  
          AccessDatabase();  
          succeeded = true;  
          break;  
        }  
    
        catch (QC.SqlException sqlExc)  
        {  
          if (TransientErrorNumbers.Contains  
            (sqlExc.Number) == true)  
          {  
            Console.WriteLine("{0}: transient occurred.", sqlExc.Number);  
            continue;  
          }  
          else  
          {  
            Console.WriteLine(sqlExc);  
            succeeded = false;  
            break;  
          }  
        }  
    
        catch (TestSqlException sqlExc)  
        {  
          if (TransientErrorNumbers.Contains  
            (sqlExc.Number) == true)  
          {  
            Console.WriteLine("{0}: transient occurred. (TESTING.)", sqlExc.Number);  
            continue;  
          }  
          else  
          {  
            Console.WriteLine(sqlExc);  
            succeeded = false;  
            break;  
          }  
        }  
    
        catch (Exception Exc)  
        {  
          Console.WriteLine(Exc);  
          succeeded = false;  
          break;  
        }  
      }  
    
      if (succeeded == true)  
      {  
        return 0;  
      }  
      else  
      {  
        Console.WriteLine("ERROR: Unable to access the database!");  
        return 1;  
      }  
    }  
    
    /// <summary>  
    /// Connects to the database, reads,  
    /// prints results to the console.  
    /// </summary>  
    static public void AccessDatabase()  
    {  
      //throw new TestSqlException(4060); //(7654321);  // Uncomment for testing.  
    
      using (var sqlConnection = new QC.SqlConnection  
          (GetSqlConnectionString()))  
      {  
        using (var dbCommand = sqlConnection.CreateCommand())  
        {  
          dbCommand.CommandText = @"  
SELECT TOP 3  
    ob.name,  
    CAST(ob.object_id as nvarchar(32)) as [object_id]  
  FROM sys.objects as ob  
  WHERE ob.type='IT'  
  ORDER BY ob.name;";  
    
          sqlConnection.Open();  
          var dataReader = dbCommand.ExecuteReader();  
    
          while (dataReader.Read())  
          {  
            Console.WriteLine("{0}\t{1}",  
              dataReader.GetString(0),  
              dataReader.GetString(1));  
          }  
        }  
      }  
    }  
    
    /// <summary>  
    /// You must edit the four 'my' string values.  
    /// </summary>  
    /// <returns>An ADO.NET connection string.</returns>  
    static private string GetSqlConnectionString()  
    {  
      // Prepare the connection string to Azure SQL Database.  
      var sqlConnectionSB = new QC.SqlConnectionStringBuilder();  
    
      // Change these values to your values.  
      sqlConnectionSB.DataSource = "tcp:myazuresqldbserver.database.windows.net,1433"; //["Server"]  
      sqlConnectionSB.InitialCatalog = "MyDatabase"; //["Database"]  
    
      sqlConnectionSB.UserID = "MyLogin";  // "@yourservername"  as suffix sometimes.  
      sqlConnectionSB.Password = "MyPassword";  
      sqlConnectionSB.IntegratedSecurity = false;  
    
      // Adjust these values if you like. (ADO.NET 4.5.1 or later.)  
      sqlConnectionSB.ConnectRetryCount = 3;  
      sqlConnectionSB.ConnectRetryInterval = 10;  // Seconds.  
    
      // Leave these values as they are.  
      sqlConnectionSB.IntegratedSecurity = false;  
      sqlConnectionSB.Encrypt = true;  
      sqlConnectionSB.ConnectTimeout = 30;  
    
      return sqlConnectionSB.ToString();  
    }  
    
    static public CG.List<int> TransientErrorNumbers =  
      new CG.List<int> { 4060, 40197, 40501, 40613,  
      49918, 49919, 49920, 11001 };  
  }  
    
  /// <summary>  
  /// For testing retry logic, you can have method  
  /// AccessDatabase start by throwing a new  
  /// TestSqlException with a Number that does  
  /// or does not match a transient error number  
  /// present in TransientErrorNumbers.  
  /// </summary>  
  internal class TestSqlException : ApplicationException  
  {  
    internal TestSqlException(int testErrorNumber)  
    { this.Number = testErrorNumber; }  
    
    internal int Number  
    { get; set; }  
  }  
}  
```  
  
###  <a name="step-2c-run-the-program"></a>Schritt 2.c: Ausführen des Programms  
  
  
Die ausführbare Datei **RetryAdo2.exe** gibt keine Parameter ein. So führen Sie die EXE-Datei aus:  
  
1. Öffnen Sie ein Konsolenfenster, wohin Sie die Binärdatei RetryAdo2.exe kompiliert haben.  
2. Führen Sie RetryAdo2.exe ohne Eingabeparameter aus.  
  
  
  
```  
database_firewall_rules_table   245575913  
filestream_tombstone_2073058421 2073058421  
filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Schritt 3: Möglichkeiten um Ihre Wiederholungslogik zu testen  
  
Es gibt verschiedene Wege, wie Sie einen vorübergehenden Fehler simulieren können, um Ihre Wiederholungslogik zu testen.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Schritt 3.a: Auslösen einer Testausnahme  
  
Das Codebeispiel beinhaltet:  
  
- Eine kleine zweite Klasse namens **TestSqlException** mit einer Eigenschaft namens **Number**.  
- `//throw new TestSqlException(4060);` , wofür Sie die Auskommentierung aufheben können.  
  
Falls Sie die Auskommentierung für die Auslösungsanweisung aufheben und neu kompilieren, gibt die nächste Ausführung von **RetryAdo2.exe** etwas aus, was dem Folgenden ähnelt.  
  
```  
[C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
>> RetryAdo2.exe  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 2 of 4 max...  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 3 of 4 max...  
4060: transient occurred. (TESTING.)  
Transient error encountered. Will begin attempt number 4 of 4 max...  
4060: transient occurred. (TESTING.)  
ERROR: Unable to access the database!  
  
[C:\VS15\RetryAdo2\RetryAdo2\bin\Debug\]  
>>  
```  
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Schritt 3.b: Erneutes Testen mit einem beständigen Fehler  
  
Um zu beweisen, dass der Code dauerhafte Fehler ordnungsgemäß behandelt, führen Sie den vorigen Test erneut durch, wobei Sie jedoch nicht die Nummer eines echten vorübergehenden Fehlers wie 4060 verwenden dürfen. Verwenden Sie stattdessen die unsinnige Nummer 7654321. Das Programm sollte diesen als dauerhaften Fehler behandeln und jede Wiederholung ausschließen.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Schritt 3.c: Trennen vom Netzwerk  
  
1. Trennen Sie den Clientcomputer vom Netzwerk.  
    - Bei einem Desktop-Computer stecken Sie das Netzwerkkabel aus.  
    - Bei einem Laptop drücken Sie die Tastenkombination um den Netzwerkadapter auszuschalten.  
2. Starten Sie RetryAdo2.exe und warten Sie, bis die Konsole den ersten vorübergehenden Fehler, wahrscheinlich „11001“, anzeigt.  
3. Verbinden Sie sich wieder mit dem Netzwerk, während RetryAdo2.exe weiterhin ausgeführt wird.  
4. Beobachten Sie in einem späteren erneuten Versuch, wie die Konsole den Erfolg berichtet.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Schritt 2.d: Temporäres Falschschreiben des Servernamens  
  
1. Fügen Sie **TransientErrorNumbers**temporär 40615 als weitere Fehlernummer hinzu und kompilieren Sie neu.  
2. Setzen Sie einen Haltepunkt in der Zeile: `new QC.SqlConnectionStringBuilder()`.  
3. Verwenden Sie die Funktion *Bearbeiten und fortfahren*, um einige Zeilen tiefer den Servernamen absichtlich falsch zu schreiben.  
    - Lassen Sie das Programm laufen und kehren Sie zu Ihrem Haltepunkt zurück.  
    - Der Fehler „40615“ tritt auf.  
4. Beheben Sie den Rechtschreibfehler.  
5. Lassen Sie das Programm laufen und erfolgreich abschließen.  
6. Entfernen Sie „40615“ und kompilieren Sie erneut.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
Informationen zu anderen bewährten Methoden und Entwurfsrichtlinien finden Sie unter [Verbindungsherstellung mit SQL-Datenbank: Links, bewährte Methoden und Entwurfsrichtlinien](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
