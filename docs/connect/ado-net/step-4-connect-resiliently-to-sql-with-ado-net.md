---
title: 'Schritt 4: Herstellen einer resilientes Verbindung mit SQL mit ADO.net | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: 9b608b0b-6b38-42da-bb83-79df8c170cd7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7a080f68497829657c60bbd96238b71123b70d87
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957596"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Schritt 4: Herstellen stabiler SQL-Verbindungen mit ADO.NET

- Vorheriger Artikel: &nbsp;&nbsp;&nbsp;[Step 3: Proof of concept connecting to SQL using ADO.NET (Schritt 3: Proof of Concept für Verbindungen mit SQL über ADO.NET)](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
Dieses Thema enthält ein C# Codebeispiel, das eine benutzerdefinierte Wiederholungs Logik veranschaulicht. Die Wiederholungs Logik bietet Zuverlässigkeit. Die Wiederholungs Logik ist so konzipiert, dass temporäre Fehler oder *vorübergehende Fehler* ordnungsgemäß verarbeitet werden, die tendenziell entfernt werden, wenn das Programm mehrere Sekunden wartet und einen Wiederholungsversuch durchführt.  
  
Zu den Quellen vorübergehender Fehler gehören:  
  
- Ein kurzer Fehler bei dem Netzwerk, das das Internet unterstützt.  
- Ein cloudsystem ist möglicherweise ein Lastenausgleich seiner Ressourcen zu dem Zeitpunkt, zu dem die Abfrage gesendet wurde.  
  
  
Die ADO.NET-Klassen für das Herstellen einer Verbindung mit Ihrem lokalen Microsoft SQL Server können auch eine Verbindung mit Azure SQL-Datenbank herstellen. Allerdings können die ADO.NET-Klassen selbst nicht die erforderliche Stabilität und Zuverlässigkeit für den Produktionseinsatz bereitstellen. In Ihrem Client Programm können vorübergehende Fehler auftreten, von denen die Anwendung automatisch und ordnungsgemäß wieder hergestellt und fortgesetzt werden sollte.  
  
## <a name="step-1-identify-transient-errors"></a>Schritt 1: identifizieren vorübergehender Fehler  
  
Ihr Programm muss zwischen vorübergehenden Fehlern und permanenten Fehlern unterscheiden. Vorübergehende Fehler sind Fehlerzustände, die innerhalb eines kurzen Zeitraums, z. b. vorübergehender Netzwerkprobleme, gelöscht werden können.  Ein Beispiel für einen permanenten Fehler wäre, wenn das Programm eine falsche Schreibweise des Namens der Zieldatenbank aufweist. in diesem Fall würde der Fehler "keine solche Datenbank gefunden" beibehalten und kann innerhalb eines kurzen Zeitraums nicht gelöscht werden.  
  
Die Liste der Fehlernummern, die als vorübergehende Fehler kategorisiert sind, finden Sie unter [Fehlermeldungen für SQL-Datenbank-Client Anwendungen](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/) .  
  
## <a name="step-2-create-and-run-sample-application"></a>Schritt 2: Erstellen und Ausführen der Beispielanwendung  
  
In diesem Beispiel wird davon ausgegangen, dass .NET Framework 4.5.1 oder höher installiert ist.  Das C# Codebeispiel besteht aus einer Datei mit dem Namen Program.cs. Der Code wird im nächsten Abschnitt bereitgestellt.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Schritt 2. a: erfassen und Kompilieren des Code Beispiels  
  
Sie können das Beispiel mit den folgenden Schritten kompilieren:  
  
1. Erstellen Sie in der [kostenlosen Visual Studio Community-Edition](https://www.visualstudio.com/products/visual-studio-community-vs)ein neues Projekt C# aus der Konsolen Anwendungs Vorlage.  
    - Datei > Neues >-Projekt > > Vorlagen > Visual C# > Windows > Classic Desktop > Konsolenanwendung installiert  
    - Nennen Sie das Projekt **RetryAdo2**.  
2. Öffnen Sie den Bereich „Projektmappen-Explorer“.  
    - Sehen Sie sich den Namen des Projekts an.  
    - Sehen Sie sich den Namen der Program.cs-Datei an.  
3. Öffnen Sie die Datei Program.cs.  
4. Ersetzen Sie den Inhalt der Program.cs-Datei vollständig durch den Code im folgenden Codeblock.  
5. Klicken Sie auf das Menü Build > Projekt Mappe erstellen.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Schritt 2. b: Kopieren und Einfügen von Beispielcode  
  
Fügen Sie diesen Code in die **Program.cs** -Datei ein.  
  
Anschließend müssen Sie die Zeichen folgen für Servername, Kennwort usw. bearbeiten. Sie finden diese Zeichen folgen in der Methode mit dem Namen **gezqlconnectionstringbuilder**.  
  
Hinweis: die Verbindungs Zeichenfolge für den Servernamen ist auf die Azure SQL-Datenbank ausgerichtet, da Sie das vier-Zeichen-Präfix von **TCP:** enthält. Sie können jedoch die Server Zeichenfolge so anpassen, dass eine Verbindung mit Ihrer Microsoft SQL Server hergestellt wird  
  
  
```csharp
    using System;  // C#  
    using CG = System.Collections.Generic;  
    using QC = System.Data.SqlClient;  
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
  
###  <a name="step-2c-run-the-program"></a>Schritt 2. c: Ausführen des Programms  
  
  
Die ausführbare Datei **RetryAdo2. exe** gibt keine Parameter an. So führen Sie ". exe" aus:  
  
1. Öffnen Sie ein Konsolenfenster, in dem Sie die Binärdatei "RetryAdo2. exe" kompiliert haben.  
2. Führen Sie RetryAdo2. exe ohne Eingabeparameter aus.  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Schritt 3: Möglichkeiten zum Testen Ihrer Wiederholungs Logik  
  
Es gibt eine Vielzahl von Methoden, mit denen Sie einen vorübergehenden Fehler simulieren können, um Ihre Wiederholungs Logik zu testen.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Schritt 3. a: Auslösen einer Test Ausnahme  
  
Das Codebeispiel enthält Folgendes:  
  
- Eine kleine zweite Klasse mit dem Namen " **testsqlexception**" mit einer Eigenschaft namens " **Number**".  
- `//throw new TestSqlException(4060);`, für die Sie die Auskommentierung aufheben können.  
  
Wenn Sie die Auskommentierung der throw-Anweisung aufheben und die Kompilierung erneut durchführen, gibt die nächste **RetryAdo2. exe** -Datei eine Ausgabe ähnlich der folgenden aus.  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Schritt 3. b: erneerstes testen mit einem permanenten Fehler  
  
Um nachzuweisen, dass der Code persistente Fehler ordnungsgemäß behandelt, führen Sie den vorherigen Test erneut aus, sofern Sie nicht die Nummer eines echten vorübergehenden Fehlers wie 4060 verwenden. Verwenden Sie stattdessen die Unsinn-Nummer 7654321. Das Programm sollte dies als permanenten Fehler behandeln und alle Wiederholungen umgehen.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Schritt 3. c: Trennen der Verbindung mit dem Netzwerk  
  
1. Trennen Sie die Verbindung des Client Computers mit dem Netzwerk.  
    - Entfernen Sie für einen Desktop das Netzwerkkabel.  
    - Drücken Sie für einen Laptop die Funktions Kombination der Tasten, um den Netzwerkadapter zu deaktivieren.  
2. Starten Sie RetryAdo2. exe, und warten Sie, bis die Konsole den ersten vorübergehenden Fehler anzeigt, wahrscheinlich 11001.  
3. Stellen Sie erneut eine Verbindung mit dem Netzwerk her, während RetryAdo2. exe weiterhin ausgeführt wird.  
4. Überwachen Sie den Erfolg der Konsolen Berichte bei einem nachfolgenden Wiederholungsversuch.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Schritt 2. d: vorübergehendes fehl Schreiben des Server namens  
  
1. Fügen Sie **transienterrornumbers**vorübergehend 40615 als weitere Fehlernummer hinzu, und kompilieren Sie Sie neu.  
2. Legen Sie einen Haltepunkt in der Zeile `new QC.SqlConnectionStringBuilder()`fest:.  
3. Verwenden Sie die Funktion " *Bearbeiten und Fortfahren* ", um den Servernamen absichtlich falsch zu schreiben, ein paar Zeilen weiter unten.  
    - Führen Sie das Programm aus, und kehren Sie zum Breakpoint zurück.  
    - Der Fehler 40615 tritt auf.  
4. Korrigieren Sie die falsche Schreibweise.  
5. Lassen Sie das Programm erfolgreich ausführen und Fertigstellen.  
6. Entfernen Sie 40615, und kompilieren Sie neu.  
  
## <a name="next-steps"></a>Next Steps  
  
Weitere Best Practices und Entwurfs Richtlinien finden Sie unter Herstellen einer [Verbindung mit SQL-Datenbank: Verknüpfungen, bewährte Methoden und Entwurfs Richtlinien](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
