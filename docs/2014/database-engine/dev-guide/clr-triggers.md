---
title: CLR-Trigger | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- inserted tables
- database objects [CLR integration], triggers
- common language runtime [SQL Server], triggers
- updated columns
- building database objects [CLR integration], triggers
- triggers [CLR integration]
- deleted tables
- EventData property
- SqlTriggerContext class
- transactions [CLR integration]
ms.assetid: 302a4e4a-3172-42b6-9cc0-4a971ab49c1c
caps.latest.revision: 67
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c6702a9a3851e7ce41862f8f314d9aebdb7a5745
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37160991"
---
# <a name="clr-triggers"></a>CLR-Trigger
  Aufgrund der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Integration mit der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR) können Sie jede beliebige [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Sprache verwenden, um CLR-Trigger zu erstellen. Dieser Abschnitt enthält spezifische Informationen zu Triggern, die mit CLR-Integration implementiert werden. Eine vollständige Erläuterung zu Triggern finden Sie unter [DDL-Trigger](../../relational-databases/triggers/ddl-triggers.md).  
  
## <a name="what-are-triggers"></a>Was sind Trigger?  
 Ein Trigger ist ein besonderer Typ einer gespeicherten Prozedur, die automatisch ausgeführt wird, wenn ein Sprachereignis ausgeführt wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält zwei allgemeine Typen von Triggern: DML-Trigger (Data Manipulation Language, Datenbearbeitungssprache) und DDL-Trigger (Data Definition Language, Datendefinitionssprache). DML-Trigger können verwendet werden, wenn die Anweisungen `INSERT`, `UPDATE` oder `DELETE` Daten in einer angegebenen Tabelle oder Sicht ändern. DDL-Trigger lösen gespeicherte Prozeduren als Reaktion auf verschiedene DDL-Anweisungen aus. Dies sind in erster Linie Anweisungen, die mit `CREATE`, `ALTER` und `DROP` beginnen. DDL-Trigger können für Verwaltungsaufgaben verwendet werden, z. B. zum Überwachen und Steuern von Datenbankvorgängen.  
  
## <a name="unique-capabilities-of-clr-triggers"></a>Spezifische Funktionen von CLR-Triggern  
 In [!INCLUDE[tsql](../../includes/tsql-md.md)] geschriebene Trigger können feststellen, welche Spalten der auslösenden Sicht oder Tabelle mit den Funktionen `UPDATE(column)` und `COLUMNS_UPDATED()` aktualisiert wurden.  
  
 In einer CLR-Sprache geschriebene Trigger unterscheiden sich in einigen bedeutenden Punkten von anderen CLR-Integrationsobjekten. CLR-Trigger bieten folgende Möglichkeiten:  
  
-   Verweisen auf Daten in den Tabellen `INSERTED` und `DELETED`  
  
-   Bestimmen, welche Spalten in Folge eines `UPDATE`-Vorgangs geändert wurden  
  
-   Zugreifen auf Informationen über Datenbankobjekte, die von der Ausführung von DDL-Anweisungen beeinflusst werden  
  
 Diese Funktionen werden grundsätzlich in der Abfragesprache oder durch die `SqlTriggerContext`-Klasse zur Verfügung gestellt. Weitere Informationen zu den Vorteilen von CLR-Integration "und" Auswählen zwischen verwaltetem Code und [!INCLUDE[tsql](../../includes/tsql-md.md)], finden Sie unter [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="using-the-sqltriggercontext-class"></a>Verwenden der SqlTriggerContext-Klasse  
 Die `SqlTriggerContext`-Klasse kann nicht öffentlich erstellt werden und kann nur durch Zugreifen auf die `SqlContext.TriggerContext`-Eigenschaft innerhalb des Texts eines CLR-Triggers abgerufen werden. Die `SqlTriggerContext`-Klasse kann vom aktiven `SqlContext` durch Aufrufen der `SqlContext.TriggerContext`-Eigenschaft abgerufen werden:  
  
 `SqlTriggerContext myTriggerContext = SqlContext.TriggerContext;`  
  
 Die `SqlTriggerContext` -Klasse stellt Kontextinformationen über den Trigger zur Verfügung. Diese Kontextinformationen umfassen den Typ der Aktion, die den Trigger ausgelöst hat, welche Spalten geändert wurden, in einer UPDATE-Vorgang, und im Falle eines DDL-Triggers, einer XML- `EventData` Struktur, die den auslösenden Vorgang beschreibt. Weitere Informationen finden Sie unter [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).  
  
### <a name="determining-the-trigger-action"></a>Bestimmen der Triggeraktion  
 Sobald Sie eine `SqlTriggerContext`-Klasse erhalten haben, können Sie damit den Typ der Aktion bestimmen, mit der der Trigger ausgelöst wurde. Diese Informationen stehen über die `TriggerAction`-Eigenschaft der `SqlTriggerContext`-Klasse zur Verfügung.  
  
 Für DML-Trigger kann die `TriggerAction`-Eigenschaft die folgenden Werte aufweisen:  
  
-   TriggerAction.Update (0x1)  
  
-   TriggerAction.Insert (0x2)  
  
-   TriggerAction.Delete (0x3)  
  
-   Für DDL-Trigger ist die Liste möglicher TriggerAction-Werte beachtlich länger. Weitere Informationen hierzu finden Sie im Abschnitt "TriggerAction Enumeration" in der .NET Framework-SDK-Dokumentation.  
  
### <a name="using-the-inserted-and-deleted-tables"></a>Verwenden der Tabellen 'inserted' und 'deleted'  
 Zwei besondere Tabellen werden in DML-triggeranweisungen verwendet: die **eingefügt** Tabelle und die **gelöscht** Tabelle. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erstellt und verwendet diese Tabellen automatisch. Sie können diese temporären Tabellen verwenden, um die Auswirkungen bestimmter Datenänderungen zu testen und Bedingungen für DML-Triggeraktionen festzulegen. Die Daten in den Tabellen können Sie jedoch nicht direkt ändern.  
  
 CLR-Trigger können Zugriff auf die **eingefügt** und **gelöscht** Tabellen durch der CLR-in-Process-Anbieter. Dazu wird ein `SqlCommand`-Objekt vom SqlContext-Objekt abgerufen. Zum Beispiel:  
  
 C#  
  
```  
SqlConnection connection = new SqlConnection ("context connection = true");  
connection.Open();  
SqlCommand command = connection.CreateCommand();  
command.CommandText = "SELECT * from " + "inserted";  
```  
  
 Visual Basic  
  
```  
Dim connection As New SqlConnection("context connection=true")  
Dim command As SqlCommand  
connection.Open()  
command = connection.CreateCommand()  
command.CommandText = "SELECT * FROM " + "inserted"  
```  
  
### <a name="determining-updated-columns"></a>Bestimmen aktualisierter Spalten  
 Sie können die Anzahl der vom UPDATE-Vorgang betroffenen Spalten bestimmen, indem Sie die `ColumnCount`-Eigenschaft des `SqlTriggerContext`-Objekts verwenden. Um zu bestimmen, ob die Spalte aktualisiert wurde, verwenden Sie die `IsUpdatedColumn`-Methode, mit der die Spaltenordnungszahl als Eingabeparameter übernommen wird. Der Wert `True` gibt an, dass die Spalte aktualisiert wurde.  
  
 Der folgende Codeausschnitt (aus dem EmailAudit-Trigger, der später in diesem Thema behandelt wird) führt beispielsweise alle aktualisierten Spalten auf:  
  
 C#  
  
```  
reader = command.ExecuteReader();  
reader.Read();  
for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
{  
   pipe.Send("Updated column "  
      + reader.GetName(columnNumber) + "? "  
   + triggContext.IsUpdatedColumn(columnNumber).ToString());  
 }  
  
 reader.Close();  
```  
  
 Visual Basic  
  
```  
reader = command.ExecuteReader()  
reader.Read()  
Dim columnNumber As Integer  
  
For columnNumber=0 To triggContext.ColumnCount-1  
  
   pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
   "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
Next  
  
reader.Close()  
```  
  
### <a name="accessing-eventdata-for-clr-ddl-triggers"></a>Zugreifen auf EventData für CLR DDL-Trigger  
 Wie normale Trigger lösen auch DDL-Trigger gespeicherte Prozeduren als Antwort auf Ereignisse aus. Aber im Gegensatz zu DML-Trigger, werden sie nicht als Reaktion auf aktualisieren, INSERT oder DELETE-Anweisungen für eine Tabelle oder Sicht ausgelöst. DDL-Trigger lösen stattdessen gespeicherte Prozeduren als Reaktion auf verschiedene DDL-Anweisungen aus. Dies sind in erster Linie Anweisungen, die mit CREATE, ALTER und DROP beginnen. DDL-Trigger können für Verwaltungsaufgaben verwendet werden, z. B. zum Überwachen von Datenbankvorgängen und Schemaänderungen.  
  
 Informationen über ein Ereignis, das einen DDL-Trigger auslöst, sind in der `EventData`-Eigenschaft der `SqlTriggerContext`-Klasse verfügbar. Diese Eigenschaft enthält einen `xml`-Wert. Das XML-Schema enthält folgende Informationen:  
  
-   Zeitpunkt des Ereignisses.  
  
-   Die SPID (System Process ID) der Verbindung, bei der der Trigger ausgeführt wurde.  
  
-   Der Typ des Ereignisses, die den Trigger ausgelöst haben.  
  
 Abhängig vom Ereignistyp schließt das Schema dann weitere Informationen ein, z. B. die Datenbank, in der das Ereignis aufgetreten ist, das Objekt, für das das Ereignis erfolgte, und den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehl des Ereignisses.  
  
 Im folgenden Beispiel gibt der DDL-Trigger die unformatierte `EventData`-Eigenschaft zurück.  
  
> [!NOTE]  
>  Das Senden von Ereignissen und Meldungen über das `SqlPipe`-Objekt wird hier nur zur Veranschaulichung gezeigt. Es wird jedoch für den Produktionscode beim Programmieren von CLR-Trigger nicht empfohlen. Weitere zurückgegebene Daten sind möglicherweise unerwartet und führen zu Anwendungsfehlern.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   public static void DropTableTrigger()  
   {  
       SqlTriggerContext triggContext = SqlContext.TriggerContext;             
  
       switch(triggContext.TriggerAction)  
       {  
           case TriggerAction.DropTable:  
           SqlContext.Pipe.Send("Table dropped! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
  
           default:  
           SqlContext.Pipe.Send("Something happened! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
       }  
   }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    Public Shared Sub DropTableTrigger()  
        Dim triggContext As SqlTriggerContext  
        triggContext = SqlContext.TriggerContext  
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.DropTable  
              SqlContext.Pipe.Send("Table dropped! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
           Case Else  
              SqlContext.Pipe.Send("Something else happened! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
        End Select  
    End Sub  
End Class     
```  
  
 Die folgende Beispielausgabe ist der `EventData`-Eigenschaftswert, nachdem ein DDL-Trigger von einem `CREATE TABLE`-Ereignis ausgelöst wurde:  
  
 `<EVENT_INSTANCE><PostTime>2004-04-16T21:17:16.160</PostTime><SPID>58</SPID><EventType>CREATE_TABLE</EventType><ServerName>MACHINENAME</ServerName><LoginName>MYDOMAIN\myname</LoginName><UserName>MYDOMAIN\myname</UserName><DatabaseName>AdventureWorks</DatabaseName><SchemaName>dbo</SchemaName><ObjectName>UserName</ObjectName><ObjectType>TABLE</ObjectType><TSQLCommand><SetOptions ANSI_NULLS="ON" ANSI_NULL_DEFAULT="ON" ANSI_PADDING="ON" QUOTED_IDENTIFIER="ON" ENCRYPTED="FALSE" /><CommandText>create table dbo.UserName  
(  
 UserName varchar(50),  
 RealName varchar(50)  
)  
</CommandText></TSQLCommand></EVENT_INSTANCE>`  
  
 Neben den Informationen, auf die über die `SqlTriggerContext`-Klasse zugegriffen werden kann, können Abfragen dennoch auf `COLUMNS_UPDATED` und auf inserted/deleted innerhalb des Texts eines prozessintern ausgeführten Befehls verweisen.  
  
## <a name="sample-clr-trigger"></a>Beispiel für einen CLR-Trigger  
 In diesem Beispiel wird das folgende Szenario veranschaulicht: Benutzer können eine beliebige ID auswählen. Sie möchten nun erfahren, welche Benutzer eine E-Mail-Adresse als ID eingegeben haben. Der folgende Trigger erkennt diese Informationen und protokolliert sie in einer Überwachungstabelle.  
  
> [!NOTE]  
>  Das Senden von Ereignissen und Meldungen über das `SqlPipe`-Objekt wird hier nur zur Veranschaulichung gezeigt. Es wird jedoch für den Produktionscode nicht empfohlen. Zusätzliche zurückgegebene Daten möglicherweise unerwartet und führen zu Anwendungsfehlern  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   [SqlTrigger(Name = @"EmailAudit", Target = "[dbo].[Users]", Event = "FOR INSERT, UPDATE, DELETE")]  
   public static void EmailAudit()  
   {  
      string userName;  
      string realName;  
      SqlCommand command;  
      SqlTriggerContext triggContext = SqlContext.TriggerContext;  
      SqlPipe pipe = SqlContext.Pipe;  
      SqlDataReader reader;  
  
      switch (triggContext.TriggerAction)  
      {  
         case TriggerAction.Insert:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
            reader.Close();  
  
            if (IsValidEMailAddress(userName))  
            {  
               command = new SqlCommand(  
                  @"INSERT [dbo].[UserNameAudit] VALUES ('"  
                  + userName + @"', '" + realName + @"');",  
                  connection);  
               pipe.Send(command.CommandText);  
               command.ExecuteNonQuery();  
               pipe.Send("You inserted: " + userName);  
            }  
         }  
  
         break;  
  
         case TriggerAction.Update:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
  
            pipe.Send(@"You updated: '" + userName + @"' - '"  
               + realName + @"'");  
  
            for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
            {  
               pipe.Send("Updated column "  
                  + reader.GetName(columnNumber) + "? "  
                  + triggContext.IsUpdatedColumn(columnNumber).ToString());  
            }  
  
            reader.Close();  
         }  
  
         break;  
  
         case TriggerAction.Delete:  
            using (SqlConnection connection  
               = new SqlConnection(@"context connection=true"))  
               {  
                  connection.Open();  
                  command = new SqlCommand(@"SELECT * FROM DELETED;",  
                     connection);  
                  reader = command.ExecuteReader();  
  
                  if (reader.HasRows)  
                  {  
                     pipe.Send(@"You deleted the following rows:");  
                     while (reader.Read())  
                     {  
                        pipe.Send(@"'" + reader.GetString(0)  
                        + @"', '" + reader.GetString(1) + @"'");  
                     }  
  
                     reader.Close();  
  
                     //alternately, to just send a tabular resultset back:  
                     //pipe.ExecuteAndSend(command);  
                  }  
                  else  
                  {  
                     pipe.Send("No rows affected.");  
                  }  
               }  
  
               break;  
            }  
        }  
  
     public static bool IsValidEMailAddress(string email)  
     {  
         return Regex.IsMatch(email, @"^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$");  
     }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Text.RegularExpressions  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    <SqlTrigger(Name:="EmailAudit", Target:="[dbo].[Users]", Event:="FOR INSERT, UPDATE, DELETE")> _  
    Public Shared Sub EmailAudit()  
        Dim userName As String  
        Dim realName As String  
        Dim command As SqlCommand  
        Dim triggContext As SqlTriggerContext  
        Dim pipe As SqlPipe  
        Dim reader As SqlDataReader    
  
        triggContext = SqlContext.TriggerContext      
        pipe = SqlContext.Pipe    
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.Insert  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 reader.Close()  
  
                 If IsValidEmailAddress(userName) Then  
                     command = New SqlCommand("INSERT [dbo].[UserNameAudit] VALUES ('" & _  
                       userName & "', '" & realName & "');", connection)  
  
                    pipe.Send(command.CommandText)  
                    command.ExecuteNonQuery()  
                    pipe.Send("You inserted: " & userName)  
  
                 End If  
              End Using  
  
           Case TriggerAction.Update  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 pipe.Send("You updated: " & userName & " - " & realName)  
  
                 Dim columnNumber As Integer  
  
                 For columnNumber=0 To triggContext.ColumnCount-1  
  
                    pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
                      "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
                 Next  
  
                 reader.Close()  
              End Using  
  
           Case TriggerAction.Delete  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM DELETED;", connection)  
  
                 reader = command.ExecuteReader()  
  
                 If reader.HasRows Then  
                    pipe.Send("You deleted the following rows:")  
  
                    While reader.Read()  
  
                       pipe.Send( reader.GetString(0) & ", " & reader.GetString(1) )  
  
                    End While   
  
                    reader.Close()  
  
                    ' Alternately, just send a tabular resultset back:  
                    ' pipe.ExecuteAndSend(command)  
  
                 Else  
                   pipe.Send("No rows affected.")  
                 End If  
  
              End Using   
        End Select  
    End Sub  
  
    Public Shared Function IsValidEMailAddress(emailAddress As String) As Boolean  
  
       return Regex.IsMatch(emailAddress, "^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$")  
    End Function      
End Class  
```  
  
 Angenommen, zwei Tabellen sind mit den folgenden Definitionen vorhanden:  
  
```  
CREATE TABLE Users  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
);  
GO CREATE TABLE UserNameAudit  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
)  
```  
  
 Die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung, den Trigger in erstellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lautet wie folgt aus, und geht davon aus Assembly **SQLCLRTest** ist bereits in der aktuellen registriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank.  
  
```  
CREATE TRIGGER EmailAudit  
ON Users  
FOR INSERT, UPDATE, DELETE  
AS  
EXTERNAL NAME SQLCLRTest.CLRTriggers.EmailAudit  
```  
  
## <a name="validating-and-canceling-invalid-transactions"></a>Überprüfen und Abbrechen von ungültigen Transaktionen  
 Trigger werden üblicherweise zur Überprüfung und zum Abbrechen von ungültigen INSERT-, UPDATE- oder DELETE-Transaktionen oder zum Verhindern von Änderungen in Ihrem Datenbankschema verwendet. Dies lässt sich erreichen, indem Validierungslogik in den Trigger integriert wird und anschließend ein Rollback zur aktuellen Transaktion durchgeführt wird, wenn die Aktion nicht den Validierungskriterien entspricht.  
  
 Beim Aufruf innerhalb eines Triggers löst die `Transaction.Rollback`-Methode oder ein SqlCommand-Befehl mit dem Befehlstext "TRANSACTION ROLLBACK" eine Ausnahme mit einer nicht eindeutigen Fehlermeldung aus und muss in einen try/catch-Block eingebunden werden. Die Fehlermeldung, die Sie sehen, ist ähnlich der folgenden:  
  
```  
Msg 6549, Level 16, State 1, Procedure trig_InsertValidator, Line 0  
A .NET Framework error occurred during execution of user defined routine or aggregate 'trig_InsertValidator':   
System.Data.SqlClient.SqlException: Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting… User transaction, if any, will be rolled back.  
```  
  
 Diese Ausnahme wird erwartet und der try/catch-Block ist notwendig, damit die Codeausführung fortgesetzt wird. Wenn der Triggercode die Ausführung beendet, wird eine andere Ausnahme ausgelöst.  
  
```  
Msg 3991, Level 16, State 1, Procedure trig_InsertValidator, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate "trig_InsertValidator" has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting.  
The statement has been terminated.  
```  
  
 Diese Ausnahme ist ebenfalls zu erwarten und ein try/catch-Block um die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung, die die den Trigger auslösenden Aktion ausführt, ist erforderlich, damit die Ausführung fortgesetzt wird. Trotz der zwei ausgelösten Ausnahmen wird ein Rollback für die Transaktion ausgeführt, und für die Änderungen in der Tabelle wird kein Commit ausgeführt. Einer der Hauptunterschiede zwischen CLR-Trigger und [!INCLUDE[tsql](../../includes/tsql-md.md)]-Trigger besteht darin, dass [!INCLUDE[tsql](../../includes/tsql-md.md)]-Trigger nach dem Rollback der Transaktion weiterhin mehr Verarbeitungsleistung übernehmen können.  
  
### <a name="example"></a>Beispiel  
 Der folgende Trigger führt eine einfache Überprüfung von INSERT-Anweisungen in einer Tabelle aus. Wenn der eingefügte Ganzzahlwert gleich 1 ist, wird ein Rollback der Transaktion durchgeführt und der Wert wird nicht in die Tabelle eingefügt. Alle anderen Ganzzahlwerte werden in die Tabelle eingefügt. Beachten Sie den try/catch-Block um die `Transaction.Rollback`-Methode. Das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Skript erstellt eine Testtabelle, Assembly und verwaltete gespeicherte Prozedur. Beachten Sie, dass die beiden INSERT-Anweisungen in einen try/catch-Block eingebunden sind, sodass die Ausnahme erfasst wird, die ausgelöst wird, wenn der Trigger die Ausführung beendet.  
  
 C#  
  
```  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class Triggers  
{  
    // Enter existing table or view for the target and uncomment the attribute line  
    // [Microsoft.SqlServer.Server.SqlTrigger (Name="trig_InsertValidator", Target="Table1", Event="FOR INSERT")]  
    public static void trig_InsertValidator()  
    {  
        using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
        {  
            SqlCommand command;  
            SqlDataReader reader;  
            int value;  
  
            // Open the connection.  
            connection.Open();  
  
            // Get the inserted value.  
            command = new SqlCommand(@"SELECT * FROM INSERTED", connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            value = (int)reader[0];  
            reader.Close();  
  
            // Rollback the transaction if a value of 1 was inserted.  
            if (1 == value)  
            {  
                try  
                {  
                    // Get the current transaction and roll it back.  
                    Transaction trans = Transaction.Current;  
                    trans.Rollback();                      
                }  
                catch (SqlException ex)  
                {  
                    // Catch the expected exception.                      
                }  
            }  
            else  
            {  
                // Perform other actions here.  
            }  
  
            // Close the connection.  
            connection.Close();              
        }  
    }  
}  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class Triggers  
' Enter existing table or view for the target and uncomment the attribute line  
' <Microsoft.SqlServer.Server.SqlTrigger(Name:="trig_InsertValidator", Target:="Table1", Event:="FOR INSERT")> _  
Public Shared Sub  trig_InsertValidator ()  
    Using connection As New SqlConnection("context connection=true")  
  
        Dim command As SqlCommand  
        Dim reader As SqlDataReader  
        Dim value As Integer  
  
        ' Open the connection.  
        connection.Open()  
  
        ' Get the inserted value.  
        command = New SqlCommand("SELECT * FROM INSERTED", connection)  
        reader = command.ExecuteReader()  
        reader.Read()  
        value = CType(reader(0), Integer)  
        reader.Close()  
  
        ' Rollback the transaction if a value of 1 was inserted.  
        If value = 1 Then  
  
            Try  
                ' Get the current transaction and roll it back.  
                Dim trans As Transaction  
                trans = Transaction.Current  
                trans.Rollback()  
  
            Catch ex As SqlException  
  
                ' Catch the exception.                      
            End Try  
        Else  
  
            ' Perform other actions here.  
        End If  
  
        ' Close the connection.  
        connection.Close()  
    End Using  
End Sub  
End Class  
```  
  
 Transact-SQL  
  
```  
-- Create the test table, assembly, and trigger.  
CREATE TABLE Table1(c1 int);  
go  
  
CREATE ASSEMBLY ValidationTriggers from 'E:\programming\ ValidationTriggers.dll';  
go  
  
CREATE TRIGGER trig_InsertValidator  
ON Table1  
FOR INSERT  
AS EXTERNAL NAME ValidationTriggers.Triggers.trig_InsertValidator;  
go  
  
-- Use a Try/Catch block to catch the expected exception  
BEGIN TRY  
   INSERT INTO Table1 VALUES(42)  
   INSERT INTO Table1 VALUES(1)  
END TRY  
BEGIN CATCH  
  SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
END CATCH;  
  
-- Clean up.  
DROP TRIGGER trig_InsertValidator;  
DROP ASSEMBLY ValidationTriggers;  
DROP TABLE Table1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql)   
 [DML-Trigger](../../relational-databases/triggers/dml-triggers.md)   
 [DDL-Trigger](../../relational-databases/triggers/ddl-triggers.md)   
 [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql)   
 [Erstellen von Datenbankobjekten mit Common Language Runtime &#40;CLR&#41; Integration](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
