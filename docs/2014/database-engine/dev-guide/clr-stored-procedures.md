---
title: CLR-gespeicherte Prozeduren | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
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
- database objects [CLR integration], stored procedures
- stored procedures [CLR integration]
- common language runtime [SQL Server], stored procedures
- building database objects [CLR integration], stored procedures
- output parameters [CLR integration]
- tabular results
ms.assetid: bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33
caps.latest.revision: 74
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7f90cbc5e45a095225f5937864d87d336a9c95da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148181"
---
# <a name="clr-stored-procedures"></a>CLR-gespeicherte Prozeduren
  Gespeicherte Prozeduren sind Routinen, die nicht in Skalarausdrücken verwendet werden können. Im Gegensatz zu Skalarfunktionen können sie tabellarische Ergebnisse und Meldungen an den Client zurückgeben, Anweisungen in Datendefinitionssprache (DDL, Data Definition Language) und in Datenbearbeitungssprache (DML, Data Manipulation Language) aufrufen und Ausgabeparameter zurückgeben. Weitere Informationen zu den Vorteilen von CLR-Integration und Auswählen zwischen verwaltetem Code und [!INCLUDE[tsql](../../includes/tsql-md.md)], finden Sie unter [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-stored-procedures"></a>Anforderungen für gespeicherte CLR-Prozeduren  
 In der common Language Runtime (CLR) werden gespeicherte Prozeduren implementiert, als öffentliche statische Methoden einer Klasse in einer [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Assembly. Die statische Methode kann entweder als ungültig deklariert werden oder gibt einen ganzzahligen Wert zurück. Wenn sie einen ganzzahligen Wert zurückgibt, wird die ganze Zahl von der Prozedur als Rückgabecode behandelt. Zum Beispiel:  
  
 `EXECUTE @return_status = procedure_name`  
  
 Die @return_status Variable wird den von der Methode zurückgegebenen Wert enthalten. Wenn die Methode als ungültig deklariert wird, ist der Rückgabecode 0.  
  
 Wenn die Methode Parameter verwendet, sollte die Anzahl der Parameter in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Implementierung mit der Anzahl der Parameter in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Deklaration der gespeicherten Prozedur übereinstimmen.  
  
 Bei den an eine gespeicherte CLR-Prozedur weitergegebenen Parametern kann es sich um einen beliebigen der systemeigenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typen handeln, die über eine Entsprechung im verwalteten Code verfügen. Damit die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Syntax die Prozedur erstellen kann, sollten diese Typen mit dem am besten passenden systemeigenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typ angegeben werden. Weitere Informationen zu typkonvertierungen finden Sie unter [Zuordnen von CLR-Parameterdaten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
### <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Tabellenwertparameter (Table Valued Parameters, TVPs), benutzerdefinierte Tabellentypen, die an eine Prozedur oder Funktion übergeben werden, bieten eine effiziente Methode zum Übergeben mehrerer Datenzeilen an den Server. TVPs verfügen über eine ähnliche Funktionalität wie Parameterarrays, bieten aber größere Flexibilität und engere Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)]. Außerdem verfügen sie auch über ein besseres Leistungspotenzial. TVPs helfen auch, die Anzahl von Roundtrips zum Server zu reduzieren. Anstatt mehrere Anforderungen an den Server zu senden, z. B. mit einer Liste von skalaren Parametern, können Daten als TVP an den Server gesendet werden. Ein benutzerdefinierter Tabellentyp kann nicht als Tabellenwertparameter an eine verwaltete gespeicherte Prozedur oder Funktion übergeben werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozess ausgeführt wird, oder von einer solchen Prozedur oder Funktion zurückgegeben werden. Weitere Informationen zu TVPs finden Sie unter [Tabellenwertparametern &#40;Datenbankmodul&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="returning-results-from-clr-stored-procedures"></a>Zurückgeben von Ergebnissen von gespeicherten CLR-Prozeduren  
 Informationen werden möglicherweise auf mehrere Weisen in gespeicherten [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Prozeduren zurückgegeben. Dies schließt Ausgabeparameter, Tabellenergebnisse und Meldungen ein.  
  
### <a name="output-parameters-and-clr-stored-procedures"></a>OUTPUT-Parameter und gespeicherte CLR-Prozeduren  
 Wie bei gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren werden Informationen möglicherweise mit OUTPUT-Parametern in gespeicherten [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Prozeduren zurückgegeben. Die [!INCLUDE[tsql](../../includes/tsql-md.md)]-DML-Syntax, die zum Erstellen von gespeicherten [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Prozeduren verwendet wird, ist mit der Syntax identisch, die zum Erstellen gespeicherter Prozeduren, die in [!INCLUDE[tsql](../../includes/tsql-md.md)] geschrieben werden, verwendet werden. Der entsprechende Parameter im Implementierungscode der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Klasse sollte einen als Verweis zu übergebenden Parameter als Argument verwenden. Beachten Sie, dass Visual Basic Ausgabeparameter nicht auf die gleiche Weise unterstützt wie Visual C#. Müssen Sie den Parameter als Verweis angeben und Anwenden der \<Out() >-Attribut ein OUTPUT-Parameter, wie im folgenden dargestellt:  
  
```  
Imports System.Runtime.InteropServices  
…  
Public Shared Sub PriceSum ( <Out()> ByRef value As SqlInt32)  
```  
  
 Das folgende Beispiel zeigt eine gespeicherte Prozedur, die Informationen über einen OUTPUT-Parameter zurückgibt.  
  
 C#  
  
```  
using System;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void PriceSum(out SqlInt32 value)  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         value = 0;  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT Price FROM Products", connection);  
         SqlDataReader reader = command.ExecuteReader();  
  
         using (reader)  
         {  
            while( reader.Read() )  
            {  
               value += reader.GetSqlInt32(0);  
            }  
         }           
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
Imports System.Runtime.InteropServices  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Executes a query and iterates over the results to perform a summation.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub PriceSum( <Out()> ByRef value As SqlInt32)  
  
        Using connection As New SqlConnection("context connection=true")  
           value = 0  
           Connection.Open()  
           Dim command As New SqlCommand("SELECT Price FROM Products", connection)  
           Dim reader As SqlDataReader  
           reader = command.ExecuteReader()  
  
           Using reader  
              While reader.Read()  
                 value += reader.GetSqlInt32(0)  
              End While  
           End Using  
        End Using          
    End Sub  
End Class  
```  
  
 Sobald die Assembly mit den oben genannten CLR-gespeicherte Prozedur erstellt und wurde erstellt, auf dem Server die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] wird verwendet, um die Prozedur in der Datenbank zu erstellen, und gibt *Summe* als OUTPUT-Parameter.  
  
```  
CREATE PROCEDURE PriceSum (@sum int OUTPUT)  
AS EXTERNAL NAME TestStoredProc.StoredProcedures.PriceSum  
-- if StoredProcedures class was inside a namespace, called MyNS,  
-- you would use:  
-- AS EXTERNAL NAME TestStoredProc.[MyNS.StoredProcedures].PriceSum  
```  
  
 Beachten Sie, dass *Summe* ist als deklariert ein `int` SQL Server-Datentyp, und dass der *Wert* in der CLR-gespeicherte Prozedur definierten Parameter wird angegeben, wie eine `SqlInt32` CLR-Datentyp. Wenn ein aufrufendes Programm die CLR-gespeicherte Prozedur ausführt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatisch konvertiert, dass die `SqlInt32` CLR-Datentyp in einen `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp.  Weitere Informationen dazu, welche CLR-Datentypen und können nicht konvertiert werden kann, finden Sie unter [Zuordnen von CLR-Parameterdaten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
### <a name="returning-tabular-results-and-messages"></a>Zurückgeben von Tabellenergebnissen und Meldungen  
 Das Zurückgeben von tabellarischen Ergebnissen und Meldungen an den Client erfolgt durch das `SqlPipe`-Objekt, das mithilfe der `Pipe`-Eigenschaft der `SqlContext`-Klasse abgerufen wird. Das `SqlPipe`-Objekt verfügt über eine `Send`-Methode. Durch das Aufrufen der `Send`-Methode können Sie Daten durch die Pipe zur aufrufenden Anwendung senden.  
  
 Dies sind verschiedene Überladungen der `SqlPipe.Send`-Methode, darunter eine, die `SqlDataReader` sendet und eine andere, die einfach eine Textzeichenfolge sendet.  
  
###### <a name="returning-messages"></a>Zurückgeben von Meldungen  
 Verwenden Sie `SqlPipe.Send(string)`, um Meldungen an die Clientanwendung zu senden. Der Text der Meldung ist auf 8000 Zeichen beschränkt. Wenn die Meldung 8000 Zeichen überschreitet, wird sie abgeschnitten.  
  
###### <a name="returning-tabular-results"></a>Zurückgeben von tabellarischen Ergebnissen  
 Um die Ergebnisse einer Abfrage direkt an den Client zu senden, verwenden Sie eine Überladung der `Execute`-Methode des `SqlPipe`-Objekts. Dies ist die effizienteste Methode zum Zurückgeben von Ergebnissen an den Client, da die Daten zu den Netzwerkpuffern übertragen werden, ohne in den verwalteten Arbeitsspeicher kopiert zu werden. Zum Beispiel:  
  
 [C#]  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the results to the client directly.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void ExecuteToClient()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version", connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub ExecuteToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 Um eine zuvor ausgeführte Abfrage über den prozessinternen Anbieter zu senden (oder um die Daten mithilfe einer benutzerdefinierten Implementierung von `SqlDataReader` vorab zu verarbeiten), verwenden Sie die Überladung der `Send`-Methode, die `SqlDataReader` verwendet. Diese Methode ist etwas langsamer als die zuvor beschriebene direkte Methode, bietet aber größere Flexibilität zum Ändern der Daten, bevor sie an den Client gesendet werden.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Execute a command and send the resulting reader to the client  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendReaderToClient()  
   {  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("select @@version", connection);  
         SqlDataReader r = command.ExecuteReader();  
         SqlContext.Pipe.Send(r);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendReaderToClient()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class  
```  
  
 Um ein dynamisches Resultset zu erstellen, füllen Sie es, und senden Sie es an den Client. Sie können Datensätze aus der aktuellen Verbindung erstellen und sie mithilfe von `SqlPipe.Send` senden.  
  
```csharp  
using System.Data;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
using System.Data.SqlTypes;  
  
public class StoredProcedures   
{  
   /// <summary>  
   /// Create a result set on the fly and send it to the client.  
   /// </summary>  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void SendTransientResultSet()  
   {  
      // Create a record object that represents an individual row, including it's metadata.  
      SqlDataRecord record = new SqlDataRecord(new SqlMetaData("stringcol", SqlDbType.NVarChar, 128));  
  
      // Populate the record.  
      record.SetSqlString(0, "Hello World!");  
  
      // Send the record to the client.  
      SqlContext.Pipe.Send(record);  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub SendTransientResultSet()  
        ' Create a record object that represents an individual row, including it's metadata.  
        Dim record As New SqlDataRecord(New SqlMetaData("stringcol", SqlDbType.NVarChar, 128) )  
  
        ' Populate the record.  
        record.SetSqlString(0, "Hello World!")  
  
        ' Send the record to the client.  
        SqlContext.Pipe.Send(record)          
    End Sub  
End Class   
```  
  
 Hier ist ein Beispiel für das Senden eines tabellarischen Ergebnisses und einer Meldung durch `SqlPipe`.  
  
```csharp  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void HelloWorld()  
   {  
      SqlContext.Pipe.Send("Hello world! It's now " + System.DateTime.Now.ToString()+"\n");  
      using(SqlConnection connection = new SqlConnection("context connection=true"))   
      {  
         connection.Open();  
         SqlCommand command = new SqlCommand("SELECT ProductNumber FROM ProductMaster", connection);  
         SqlDataReader reader = command.ExecuteReader();  
         SqlContext.Pipe.Send(reader);  
      }  
   }  
}  
```  
  
 [Visual Basic]  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class StoredProcedures   
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub HelloWorld()  
        SqlContext.Pipe.Send("Hello world! It's now " & System.DateTime.Now.ToString() & "\n")  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT ProductNumber FROM ProductMaster", connection)  
            Dim reader As SqlDataReader  
            reader = command.ExecuteReader()  
            SqlContext.Pipe.Send(reader)  
        End Using  
    End Sub  
End Class   
```  
  
 Das erste `Send` sendet eine Meldung an den Client, während das zweite ein tabellarisches Ergebnis mithilfe von `SqlDataReader` sendet.  
  
 Beachten Sie, dass diese Beispiele lediglich zu Illustrationszwecken dienen. CLR-Funktionen sind für berechnungsintensive Anwendungen geeigneter als einfache [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen. Eine fast identische gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozedur zum vorherigen Beispiel ist:  
  
```  
CREATE PROCEDURE HelloWorld() AS  
BEGIN  
PRINT('Hello world!')  
SELECT ProductNumber FROM ProductMaster  
END;  
```  
  
> [!NOTE]  
>  Meldungen und Resultsets werden in der Clientanwendung anders abgerufen. Z. B. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Resultsets in den **Ergebnisse** angezeigt, und Meldungen angezeigt, der **Nachrichten** Bereich.  
  
 Wenn der oben erwähnte Visual C#-Code in einer Datei MyFirstUdp.cs gespeichert und mit Folgendem kompiliert wird:  
  
```  
csc /t:library /out:MyFirstUdp.dll MyFirstUdp.cs   
```  
  
 Oder wenn der oben erwähnte Visual Basic-Code in einer Datei MyFirstUdp.vb gespeichert und mit Folgendem kompiliert wird:  
  
```  
vbc /t:library /out:MyFirstUdp.dll MyFirstUdp.vb   
```  
  
> [!NOTE]  
>  Ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] werden Visual C++-Datenbankobjekte (z. B. gespeicherte Prozeduren), die mit `/clr:pure` kompiliert werden, nicht für die Ausführung unterstützt.  
  
 Die resultierende Assembly kann mit folgender DLL registriert und der Einstiegspunkt aufgerufen werden:  
  
```  
CREATE ASSEMBLY MyFirstUdp FROM 'C:\Programming\MyFirstUdp.dll';  
CREATE PROCEDURE HelloWorld  
AS EXTERNAL NAME MyFirstUdp.StoredProcedures.HelloWorld;  
EXEC HelloWorld;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-benutzerdefinierte Funktionen](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [Benutzerdefinierte CLR-Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR-Trigger](../../../2014/database-engine/dev-guide/clr-triggers.md)  
  
  