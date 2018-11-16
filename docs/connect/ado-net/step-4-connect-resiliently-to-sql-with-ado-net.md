---
title: 'Schritt 4: Herstellen robuster Verbindungen mit SQL mit ADO.NET | Microsoft-Dokumentation'
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
manager: craigg
ms.openlocfilehash: 483c7f84d171b34135d16fd6f392b6f5f180d217
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607100"
---
# <a name="step-4-connect-resiliently-to-sql-with-adonet"></a>Schritt 4: Herstellen stabiler SQL-Verbindungen mit ADO.NET

- Vorheriger Artikel: &nbsp;&nbsp;&nbsp;[Step 3: Proof of concept connecting to SQL using ADO.NET (Schritt 3: Proof of Concept für Verbindungen mit SQL über ADO.NET)](step-3-proof-of-concept-connecting-to-sql-using-ado-net.md)  

  
Dieses Thema enthält ein C#-Codebeispiel, das benutzerdefinierte Wiederholungslogik veranschaulicht wird. Die Wiederholungslogik sorgt für Zuverlässigkeit. Die Wiederholungslogik soll ordnungsgemäß verarbeiten von temporären Fehlern oder *vorübergehende Fehler* die tendenziell behoben sind, wenn das Programm mehrere Sekunden und Wiederholungen wartet.  
  
Quellen für vorübergehende Fehler sind:  
  
- Eine kurze Fehler der Netzwerkverbindung, die im Internet unterstützt.  
- Ein cloudsystem möglicherweise auf den Lastenausgleich von zugehörigen Ressourcen in dem Moment, die die Abfrage gesendet wurde.  
  
  
Die ADO.NET-Klassen zum Herstellen einer Verbindung mit Ihrem lokalen Microsoft SQL Server können auch mit Azure SQL-Datenbank verbinden. Die ADO.NET-Klassen können keine Klassen jedoch der Stabilität und Zuverlässigkeit erforderlich ist, in der Produktion verwendet bereitstellen. Ihr Clientprogramm kann vorübergehende Fehler auftreten, von denen er im Hintergrund und diskret wiederhergestellt und weiterhin, selbstständig sollten.  
  
## <a name="step-1-identify-transient-errors"></a>Schritt 1: Ermitteln von vorübergehenden Fehlern  
  
Das Programm muss zwischen vorübergehenden Fehlern und beständigen Fehlern unterscheiden. Vorübergehende Fehler sind fehlerbedingungen, die innerhalb kurzer Zeit, z. B. vorübergehende Netzwerkprobleme erholt können.  Ein Beispiel für ein beständiger Fehler wäre, wenn das Programm eine falsche Schreibweise für den Namen der Zieldatenbank hat: in diesem Fall der Fehler "Datenbank nicht gefunden" beibehalten werden sollen, und hat keine Chance, das Bereinigen von innerhalb kurzer Zeit.  
  
Die Liste der Fehlernummern, die als vorübergehende Fehler kategorisiert werden finden Sie unter [Fehlermeldungen für SQL-Datenbank-Clientanwendungen](https://docs.microsoft.com/azure/sql-database/sql-database-develop-error-messages/)  
  
## <a name="step-2-create-and-run-sample-application"></a>Schritt 2: Erstellen Sie und führen Sie der beispielanwendung aus  
  
In diesem Beispiel geht davon aus .NET Framework 4.5.1 oder höher installiert ist.  Das C#-Codebeispiel besteht aus einer Datei, die mit dem Namen "Program.cs". Der Code wird im nächsten Abschnitt bereitgestellt.  
  
### <a name="step-2a-capture-and-compile-the-code-sample"></a>Schritt-2.a: erfassen und Kompilieren des Codebeispiels  
  
Sie können das Beispiel mit den folgenden Schritten kompilieren:  
  
1. In der [kostenlose Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs), erstellen Sie ein neues Projekt aus der Vorlage für die C#-Konsolenanwendung.  
    - Datei > Neu > Projekt > installiert > Vorlagen > Visual c# > Windows > Klassischer Desktop > Konsolenanwendung  
    - Nennen Sie das Projekt **RetryAdo2**.  
2. Öffnen Sie den Bereich „Projektmappen-Explorer“.  
    - Der Name des Projekts angezeigt.  
    - Der Name der Datei "Program.cs" angezeigt.  
3. Öffnen Sie die Datei "Program.cs" ein.  
4. Ersetzen Sie den Inhalt der Datei "Program.cs" vollständig durch den Code in den folgenden Codeblock.  
5. Klicken Sie auf das Menü "erstellen > Projektmappe erstellen.  
  
### <a name="step-2b-copy-and-paste-sample-code"></a>Schritt 2.b: Beispielcode kopieren und einfügen  
  
Fügen Sie diesen Code in Ihre **"Program.cs"** Datei.  
  
Dann müssen Sie die Zeichenfolgen für die Servername, Kennwort und So weiter bearbeiten. Diese Zeichenfolgen finden Sie in der Methode, die mit dem Namen **GetSqlConnectionStringBuilder**.  
  
Hinweis: Die Verbindungszeichenfolge für den Servernamen ist zugeschnitten Azure SQL-Datenbank, da sie das Präfix aus vier Zeichen des enthält **Tcp:**. Aber Sie können anpassen, dass die serverzeichenfolge, die mit Microsoft SQL Server herstellen.  
  
  
```CSharp  
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
  
###  <a name="step-2c-run-the-program"></a>Schritt-2.c: Führen Sie das Programm  
  
  
Die **RetryAdo2.exe** ausführbare Datei gibt keine Parameter. So führen Sie die .exe aus:  
  
1. Öffnen Sie ein Konsolenfenster, in dem Sie die Binärdatei RetryAdo2.exe kompiliert haben.  
2. Führen Sie RetryAdo2.exe ohne Eingabeparameter aus.  
  
  
  
```  
    database_firewall_rules_table   245575913  
    filestream_tombstone_2073058421 2073058421  
    filetable_updates_2105058535    2105058535  
```  
  
  
  
## <a name="step-3-ways-to-test-your-retry-logic"></a>Schritt 3: Methoden, um Ihre Wiederholungslogik zu testen.  
  
Es gibt verschiedene Möglichkeiten können Sie simulieren, einen vorübergehenden Fehler, um Ihre Wiederholungslogik zu testen.  
  
  
###  <a name="step-3a-throw-a-test-exception"></a>Schritt 3.a: Auslösen eine testausnahme  
  
Das Codebeispiel enthält:  
  
- Eine kleine Sekunde-Klasse, die mit dem Namen **TestSqlException**, mit einer Eigenschaft mit dem Namen **Anzahl**.  
- `//throw new TestSqlException(4060);` , die Sie die auskommentierung aufheben können.  
  
Wenn Sie die auskommentierung der Throw-Anweisung und Neukompilieren aufheben, die nächste Ausführung von **RetryAdo2.exe** in etwa Folgendes ausgegeben.  
  
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
  
###  <a name="step-3b-retest-with-a-persistent-error"></a>Schritt 3.b: Testen mit einem beständigen Fehler  
  
Um nachzuweisen, dass den Code verwenden Sie Handles, auf die persistente Fehler ordnungsgemäß mit Ausnahme des vorherigen Tests erneut ausführen nicht die Anzahl der echten vorübergehender Fehler wie 4060. Verwenden Sie die Anzahl der unsinnige 7654321 ein. Das Programm dies als ein beständiger Fehler behandeln soll, und Sie sollten alle Wiederholungsversuche zu umgehen.  
  
###  <a name="step-3c-disconnect-from-the-network"></a>Schritt-3.c: Trennen der Netzwerkverbindung  
  
1. Trennen Sie den Clientcomputer vom Netzwerk aus.  
    - Trennen Sie für Desktop die Netzwerkkabel.  
    - Drücken Sie bei einem Laptop die mit den Schlüsseln für den Netzwerkadapter deaktivieren.  
2. Starten Sie RetryAdo2.exe und warten Sie auf der Konsole den ersten vorübergehenden Fehler, wahrscheinlich 11001 angezeigt.  
3. Verbinden Sie mit dem Netzwerk, während RetryAdo2.exe weiterhin ausgeführt.  
4. Sehen Sie sich die Konsole den Erfolg berichtet bei einem erneuten Versuch.  
  
  
###  <a name="step-2d-temporarily-misspell-the-server-name"></a>Schritt 2.d: falsch vorübergehend auf den Namen des Servers  
  
1. Temporär 40615 als weitere Fehlernummer hinzu hinzufügen **TransientErrorNumbers**, und kompilieren Sie erneut.  
2. Legen Sie einen Haltepunkt in der Zeile: `new QC.SqlConnectionStringBuilder()`.  
3. Verwenden der *bearbeiten und Fortfahren* Feature auf den Servernamen ein, die ein paar Zeilen, die folgenden absichtlich falsch zu schreiben.  
    - Lassen Sie das Programm laufen und kehren Sie zu Ihrem Haltepunkt zurück.  
    - Der Fehler "40615" tritt auf.  
4. Beheben Sie den Rechtschreibfehler.  
5. Lassen Sie das Programm laufen und erfolgreich abgeschlossen.  
6. 40615 entfernen und neu kompilieren.  
  
## <a name="next-steps"></a>Next Steps  
  
Um andere bewährte Practicies und Richtlinien für den Entwurf zu untersuchen, finden Sie unter [Herstellen einer Verbindung mit SQL-Datenbank: Links, Best Practices und Entwurfsrichtlinien](https://azure.microsoft.com/documentation/articles/sql-database-connect-central-recommendations/)  
