---
title: CLR-Tabellenwert Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- Transact-SQL table-valued functions
- table-valued functions [CLR integration]
- TVFs [CLR integration]
ms.assetid: 9a6133ea-36e9-45bf-b572-1c0df3d6c194
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 7dfd3db3a8193e92f9670213c602d55dc45f5c7f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75232292"
---
# <a name="clr-table-valued-functions"></a>CLR-Tabellenwertfunktionen
  Eine Tabellenwertfunktion ist eine benutzerdefinierte Funktion, die eine Tabelle zurückgibt.  
  
 Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]verfügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über erweiterte Funktionalität für Tabellenwertfunktionen, sodass Sie eine Tabellenwertfunktion in jeder beliebigen verwalteten Sprache definieren können. Daten werden von einer Tabellenwertfunktion durch ein `IEnumerable`-Objekt oder `IEnumerator`-Objekt zurückgegeben.  
  
> [!NOTE]  
>  Bei Tabellenwertfunktionen können die Spalten des zurückgegebenen Tabellentyps keine timestamp-Spalten oder Spalten mit Nicht-Unicode-Zeichenfolgendatentypen enthalten (z. B. `char`, `varchar` und `text`). Die NOT NULL-Einschränkung wird nicht unterstützt  
  
## <a name="differences-between-transact-sql-and-clr-table-valued-functions"></a>Unterschiede zwischen Transact-SQL- und CLR-Tabellenwertfunktionen  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]-Tabellenwertfunktionen materialisieren die Ergebnisse des Funktionsaufrufs in einer Zwischentabelle. Da sie eine Zwischentabelle verwenden, können sie Einschränkungen und eindeutige Indizes der Ergebnisse unterstützen. Diese Funktionen können äußerst nützlich sein, wenn umfassende Ergebnisse zurückgegeben werden.  
  
 Im Gegensatz dazu stellen CLR-Tabellenwertfunktionen eine Streamingalternative dar. Es ist nicht erforderlich, das gesamte Resultset in einer einzigen Tabelle darzustellen. Das von der verwalteten Funktion zurückgegebene `IEnumerable`-Objekt wird direkt vom Ausführungsplan der Abfrage aufgerufen, die die Tabellenwertfunktion aufruft, und die Ergebnisse werden inkrementell verarbeitet. Beim Streamingmodell werden Ergebnisse sofort verarbeitet, sobald die erste Zeile verfügbar ist, und nicht erst, wenn die gesamte Tabelle aufgefüllt wurde. Dieses Modell ist auch eine gute Alternative, wenn eine sehr große Anzahl an Zeilen zurückgegeben wird, da diese nicht alle auf einmal im Speicher materialisiert werden müssen. Beispielsweise könnte eine verwaltete Tabellenwertfunktion verwendet werden, um eine Textdatei zu analysieren und jede Zeile als Tabellenzeile zurückzugeben.  
  
## <a name="implementing-table-valued-functions"></a>Implementieren von Tabellenwertfunktionen  
 Implementieren Sie Tabellenwertfunktionen als Methoden einer Klasse in einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework-Assembly. Der Code der Tabellenwertfunktion muss die `IEnumerable`-Schnittstelle implementieren. Die `IEnumerable`-Schnittstelle ist in .NET Framework definiert. Für Typen, die Arrays und Auflistungen in .NET Framework darstellen, ist die `IEnumerable`-Schnittstelle bereits implementiert. Dies vereinfacht das Schreiben von Tabellenwertfunktionen, die eine Auflistung oder ein Array in ein Resultset konvertieren.  
  
## <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Tabellenwertparameter sind benutzerdefinierte Tabellentypen, die an eine Prozedur oder Funktion übergeben werden, und bieten eine effiziente Methode zum Übergeben mehrerer Datenzeilen an den Server. Tabellenwertparameter verfügen über eine ähnliche Funktionalität wie Parameterarrays, bieten jedoch größere Flexibilität und engere Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)]. Außerdem verfügen sie auch über ein besseres Leistungspotenzial. Außerdem tragen Tabellenwertparameter dazu bei, die Anzahl von Roundtrips zum Server zu reduzieren. Anstatt mehrere Anforderungen an den Server zu senden, wie beispielsweise bei einer Liste von skalaren Parametern, können Daten als Tabellenwertparameter an den Server gesendet werden. Ein benutzerdefinierter Tabellentyp kann nicht als Tabellenwertparameter an eine verwaltete gespeicherte Prozedur oder Funktion übergeben werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess ausgeführt wird, oder von einer solchen Prozedur oder Funktion zurückgegeben werden. Weitere Informationen zu Tabellenwertparametern finden Sie unter [Use Table-Valued Parameters &#40;Database Engine&#41; (Verwenden von Tabellenwertparametern &#40;Datenbank-Engine&#41;)](../tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="output-parameters-and-table-valued-functions"></a>Ausgabeparameter und Tabellenwertfunktionen  
 Informationen können aus Tabellenwertfunktionen möglicherweise mit Ausgabeparametern zurückgegeben werden. Der entsprechende Parameter im Implementierungscode der Tabellenwertfunktion sollte einen als Verweis zu übergebenden Parameter als Argument verwenden. Beachten Sie, dass Visual Basic Ausgabeparameter nicht auf die gleiche Weise unterstützt wie Visual C#. Sie müssen den Parameter als Verweis angeben und das \<out ()->-Attribut zur Darstellung eines Ausgabe Parameters anwenden, wie im folgenden dargestellt:  
  
```vb  
Imports System.Runtime.InteropServices  
...  
Public Shared Sub FillRow ( <Out()> ByRef value As SqlInt32)  
```  
  
### <a name="defining-a-table-valued-function-in-transact-sql"></a>Definieren einer Tabellenwertfunktion in Transact-SQL  
 Die Syntax zum Definieren einer CLR-Tabellenwertfunktion ähnelt der einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Tabellenwertfunktion, enthält jedoch zusätzlich die `EXTERNAL NAME`-Klausel. Beispiel:  
  
```  
CREATE FUNCTION GetEmpFirstLastNames()  
RETURNS TABLE (FirstName NVARCHAR(4000), LastName NVARCHAR(4000))  
EXTERNAL NAME MyDotNETAssembly.[MyNamespace.MyClassname]. GetEmpFirstLastNames;  
```  
  
 Tabellenwertfunktionen werden verwendet, um Daten in relationalem Format zur weiteren Verarbeitung in Abfragen darzustellen, z. B.:  
  
```  
select * from function();  
select * from tbl join function() f on tbl.col = f.col;  
select * from table t cross apply function(t.column);  
```  
  
 Tabellenwertfunktionen können in den folgenden Fällen eine Tabelle zurückgegeben:  
  
-   Wenn sie aus skalaren Eingabeargumenten erstellt wurde. Beispielsweise eine Tabellenwertfunktion, die eine durch Trennzeichen getrennte Zeichenfolge von Zahlen in einer Tabelle anordnet.  
  
-   Wenn sie aus externen Daten erstellt wurde. Beispielsweise eine Tabellenwertfunktion, die das Ereignisprotokoll liest und es als Tabelle bereitstellt.  
  
 **Hinweis** Eine Tabellenwert Funktion kann nur den Datenzugriff über eine [!INCLUDE[tsql](../../includes/tsql-md.md)] Abfrage in der `InitMethod` -Methode und nicht in der `FillRow` -Methode ausführen. Die `InitMethod`-Methode sollte mit der `SqlFunction.DataAccess.Read`-Attributeigenschaft gekennzeichnet werden, wenn eine [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfrage ausgeführt wird.  
  
## <a name="a-sample-table-valued-function"></a>Beispiel für eine Tabellenwertfunktion  
 Die folgende Tabellenwertfunktion gibt Informationen aus dem Systemereignisprotokoll zurück. Die Funktion liest ein einzelnes Zeichenfolgenargument, das den Namen des Ereignisprotokolls enthält.  
  
###### <a name="sample-code"></a>Beispielcode  
  
```csharp  
using System;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Collections;  
using System.Data.SqlTypes;  
using System.Diagnostics;  
  
public class TabularEventLog  
{  
    [SqlFunction(FillRowMethodName = "FillRow")]  
    public static IEnumerable InitMethod(String logname)  
    {  
        return new EventLog(logname).Entries;    }  
  
    public static void FillRow(Object obj, out SqlDateTime timeWritten, out SqlChars message, out SqlChars category, out long instanceId)  
    {  
        EventLogEntry eventLogEntry = (EventLogEntry)obj;  
        timeWritten = new SqlDateTime(eventLogEntry.TimeWritten);  
        message = new SqlChars(eventLogEntry.Message);  
        category = new SqlChars(eventLogEntry.Category);  
        instanceId = eventLogEntry.InstanceId;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data.Sql  
Imports Microsoft.SqlServer.Server  
Imports System.Collections  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Public Class TabularEventLog  
    <SqlFunction(FillRowMethodName:="FillRow")> _  
    Public Shared Function InitMethod(ByVal logname As String) As IEnumerable  
        Return New EventLog(logname).Entries  
    End Function  
  
    Public Shared Sub FillRow(ByVal obj As Object, <Out()> ByRef timeWritten As SqlDateTime, <Out()> ByRef message As SqlChars, <Out()> ByRef category As SqlChars, <Out()> ByRef instanceId As Long)  
        Dim eventLogEnTry As EventLogEntry = CType(obj, EventLogEntry)  
        timeWritten = New SqlDateTime(eventLogEnTry.TimeWritten)  
        message = New SqlChars(eventLogEnTry.Message)  
        category = New SqlChars(eventLogEnTry.Category)  
        instanceId = eventLogEnTry.InstanceId  
    End Sub  
End Class  
```  
  
###### <a name="declaring-and-using-the-sample-table-valued-function"></a>Deklarieren und Verwenden des Beispiels für eine Tabellenwertfunktion  
 Sobald das Beispiel für eine Tabellenwertfunktion kompiliert wurde, kann diese in [!INCLUDE[tsql](../../includes/tsql-md.md)] folgendermaßen deklariert werden:  
  
```  
use master;  
-- Replace SQL_Server_logon with your SQL Server user credentials.  
GRANT EXTERNAL ACCESS ASSEMBLY TO [SQL_Server_logon];   
-- Modify the following line to specify a different database.  
ALTER DATABASE master SET TRUSTWORTHY ON;  
  
-- Modify the next line to use the appropriate database.  
CREATE ASSEMBLY tvfEventLog   
FROM 'D:\assemblies\tvfEventLog\tvfeventlog.dll'   
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
CREATE FUNCTION ReadEventLog(@logname nvarchar(100))  
RETURNS TABLE   
(logTime datetime,Message nvarchar(4000),Category nvarchar(4000),InstanceId bigint)  
AS   
EXTERNAL NAME tvfEventLog.TabularEventLog.InitMethod;  
GO  
```  
  
 Visual C++-Datenbankobjekte, die mit /clr:pure kompiliert wurden, können nicht in [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ausgeführt werden. Zu solchen Datenbankobjekten gehören beispielsweise Tabellenwertfunktionen.  
  
 Führen Sie den folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code aus, um das Beispiel zu testen:  
  
```  
-- Select the top 100 events,  
SELECT TOP 100 *  
FROM dbo.ReadEventLog(N'Security') as T;  
go  
  
-- Select the last 10 login events.  
SELECT TOP 10 T.logTime, T.Message, T.InstanceId   
FROM dbo.ReadEventLog(N'Security') as T  
WHERE T.Category = N'Logon/Logoff';  
go  
```  
  
## <a name="sample-returning-the-results-of-a-sql-server-query"></a>Beispiel: Zurückgeben der Ergebnisse einer SQL Server-Abfrage  
 Im folgenden Beispiel wird eine Tabellenwertfunktion gezeigt, die eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank abfragt. In diesem Beispiel wird die AdventureWorks Datenbank Light aus [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]verwendet. Weitere [https://www.codeplex.com/sqlserversamples](https://go.microsoft.com/fwlink/?LinkId=87843) Informationen zum Herunterladen von AdventureWorks finden Sie unter.  
  
 Nennen Sie die Quellcodedatei FindInvalidEmails.cs bzw. FindInvalidEmails.vb.  
  
```csharp  
using System;  
using System.Collections;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
  
using Microsoft.SqlServer.Server;  
  
public partial class UserDefinedFunctions {  
   private class EmailResult {  
      public SqlInt32 CustomerId;  
      public SqlString EmailAdress;  
  
      public EmailResult(SqlInt32 customerId, SqlString emailAdress) {  
         CustomerId = customerId;  
         EmailAdress = emailAdress;  
      }  
   }  
  
   public static bool ValidateEmail(SqlString emailAddress) {  
      if (emailAddress.IsNull)  
         return false;  
  
      if (!emailAddress.Value.EndsWith("@adventure-works.com"))  
         return false;  
  
      // Validate the address. Put any more rules here.  
      return true;  
   }  
  
   [SqlFunction(  
       DataAccess = DataAccessKind.Read,  
       FillRowMethodName = "FindInvalidEmails_FillRow",  
       TableDefinition="CustomerId int, EmailAddress nvarchar(4000)")]  
   public static IEnumerable FindInvalidEmails(SqlDateTime modifiedSince) {  
      ArrayList resultCollection = new ArrayList();  
  
      using (SqlConnection connection = new SqlConnection("context connection=true")) {  
         connection.Open();  
  
         using (SqlCommand selectEmails = new SqlCommand(  
             "SELECT " +  
             "[CustomerID], [EmailAddress] " +  
             "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " +  
             "WHERE [ModifiedDate] >= @modifiedSince",  
             connection)) {  
            SqlParameter modifiedSinceParam = selectEmails.Parameters.Add(  
                "@modifiedSince",  
                SqlDbType.DateTime);  
            modifiedSinceParam.Value = modifiedSince;  
  
            using (SqlDataReader emailsReader = selectEmails.ExecuteReader()) {  
               while (emailsReader.Read()) {  
                  SqlString emailAddress = emailsReader.GetSqlString(1);  
                  if (ValidateEmail(emailAddress)) {  
                     resultCollection.Add(new EmailResult(  
                         emailsReader.GetSqlInt32(0),  
                         emailAddress));  
                  }  
               }  
            }  
         }  
      }  
  
      return resultCollection;  
   }  
  
   public static void FindInvalidEmails_FillRow(  
       object emailResultObj,  
       out SqlInt32 customerId,  
       out SqlString emailAdress) {  
      EmailResult emailResult = (EmailResult)emailResultObj;  
  
      customerId = emailResult.CustomerId;  
      emailAdress = emailResult.EmailAdress;  
   }  
};  
```  
  
```vb  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, ByRef customerId As SqlInt32, ByRef emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End ClassImports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Public Partial Class UserDefinedFunctions  
   Private Class EmailResult  
      Public CustomerId As SqlInt32  
      Public EmailAdress As SqlString  
  
      Public Sub New(customerId__1 As SqlInt32, emailAdress__2 As SqlString)  
         CustomerId = customerId__1  
         EmailAdress = emailAdress__2  
      End Sub  
   End Class  
  
   Public Shared Function ValidateEmail(emailAddress As SqlString) As Boolean  
      If emailAddress.IsNull Then  
         Return False  
      End If  
  
      If Not emailAddress.Value.EndsWith("@adventure-works.com") Then  
         Return False  
      End If  
  
      ' Validate the address. Put any more rules here.  
      Return True  
   End Function  
  
   <SqlFunction(DataAccess := DataAccessKind.Read, FillRowMethodName := "FindInvalidEmails_FillRow", TableDefinition := "CustomerId int, EmailAddress nvarchar(4000)")> _  
   Public Shared Function FindInvalidEmails(modifiedSince As SqlDateTime) As IEnumerable  
      Dim resultCollection As New ArrayList()  
  
      Using connection As New SqlConnection("context connection=true")  
         connection.Open()  
  
         Using selectEmails As New SqlCommand("SELECT " & "[CustomerID], [EmailAddress] " & "FROM [AdventureWorksLT2008].[SalesLT].[Customer] " & "WHERE [ModifiedDate] >= @modifiedSince", connection)  
            Dim modifiedSinceParam As SqlParameter = selectEmails.Parameters.Add("@modifiedSince", SqlDbType.DateTime)  
            modifiedSinceParam.Value = modifiedSince  
  
            Using emailsReader As SqlDataReader = selectEmails.ExecuteReader()  
               While emailsReader.Read()  
                  Dim emailAddress As SqlString = emailsReader.GetSqlString(1)  
                  If ValidateEmail(emailAddress) Then  
                     resultCollection.Add(New EmailResult(emailsReader.GetSqlInt32(0), emailAddress))  
                  End If  
               End While  
            End Using  
         End Using  
      End Using  
  
      Return resultCollection  
   End Function  
  
   Public Shared Sub FindInvalidEmails_FillRow(emailResultObj As Object, customerId As SqlInt32, emailAdress As SqlString)  
      Dim emailResult As EmailResult = DirectCast(emailResultObj, EmailResult)  
  
      customerId = emailResult.CustomerId  
      emailAdress = emailResult.EmailAdress  
   End Sub  
End Class  
```  
  
 Kompilieren Sie den Quellcode zu einer DLL, und kopieren Sie die DLL in das Stammverzeichnis von Laufwerk C:.  Führen Sie dann die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Abfrage aus.  
  
```  
use AdventureWorksLT2008;  
go  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'FindInvalidEmails')  
   DROP FUNCTION FindInvalidEmails;  
go  
  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'MyClrCode')  
   DROP ASSEMBLY MyClrCode;  
go  
  
CREATE ASSEMBLY MyClrCode FROM 'C:\FindInvalidEmails.dll'  
WITH PERMISSION_SET = SAFE -- EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION FindInvalidEmails(@ModifiedSince datetime)   
RETURNS TABLE (  
   CustomerId int,  
   EmailAddress nvarchar(4000)  
)  
AS EXTERNAL NAME MyClrCode.UserDefinedFunctions.[FindInvalidEmails];  
go  
  
SELECT * FROM FindInvalidEmails('2000-01-01');  
go  
```  
  
