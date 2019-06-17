---
title: In-Process Data Access-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 155be272-4f9a-4d86-9f4f-714c4f45b49a
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b9854218e66d3edfe10f4220a5ac662cccc6f481
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62781138"
---
# <a name="in-process-data-access-sample"></a>Beispiel für In-Process-Datenzugriff
  Das `InProcessDataAccess`-Beispiel enthält eine bestimmte Anzahl von einfachen Funktionen zur Demonstration verschiedener Funktionen des prozessinternen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-CLR-Datenzugriffsanbieters.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Erstellen und Ausführen dieses Projekts muss die folgende Software installiert sein:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express erhalten Sie kostenlos auf der [Website](https://go.microsoft.com/fwlink/?LinkId=31046) mit der Dokumentation und den Beispielen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.  
  
-   Die AdventureWorks-Datenbank, die auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer-[Website](https://go.microsoft.com/fwlink/?linkid=62796) zur Verfügung gestellt wird.  
  
-   .NET Framework SDK 2.0 oder höher oder Microsoft Visual Studio 2005 oder höher. Das .NET Framework SDK ist kostenlos erhältlich.  
  
-   Außerdem müssen die folgenden Bedingungen erfüllt sein:  
  
-   In der von Ihnen verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz muss die CLR-Integration aktiviert sein.  
  
-   Führen Sie zum Aktivieren der CLR-Integration die folgenden Schritte aus:  
  
    #### <a name="enabling-clr-integration"></a>Aktivieren der CLR-Integration  
  
    -   Führen Sie die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Befehle aus:  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  Um CLR zu aktivieren, benötigen Sie die `ALTER SETTINGS`-Serverberechtigung, die Mitglieder der festen Serverrollen `sysadmin` und `serveradmin` implizit erhalten.  
  
-   Die AdventureWorks-Datenbank muss in der von Ihnen verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz installiert sein.  
  
-   Wenn Sie nicht-Administrator sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz, die Sie verwenden, benötigen Sie einen Administrator, die Sie gewähren **CreateAssembly** Berechtigung, um die Installation abzuschließen.  
  
## <a name="building-the-sample"></a>Erstellen des Beispiels  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a>Verwenden Sie die folgenden Anweisungen, um das Beispiel zu erstellen und auszuführen:  
  
1.  Wechseln Sie zu einer Visual Studio- oder .NET Framework-Eingabeaufforderung.  
  
2.  Erstellen Sie ggf. ein Verzeichnis für das Beispiel. Für dieses Beispiel wird C:\MySample verwendet.  
  
3.  Erstellen Sie in c:\MySample die Datei `inprocda.vb` (für das Visual Basic-Beispiel) oder `inprocda.cs` (für das C#-Beispiel), und kopieren Sie den entsprechenden Visual Basic- oder C#-Beispielcode (unten) in die Datei.  
  
4.  Kompilieren Sie an der Eingabeaufforderung den Beispielcode in die erforderliche Assembly, indem Sie je nach gewählter Sprache eine der folgenden Anweisungen ausführen.  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /target:library InProcDA.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /target:library inprocda.cs`  
  
5.  Kopieren Sie den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Installationscode in eine Datei, und speichern Sie sie als `Install.sql` im Beispielverzeichnis.  
  
6.  Wenn das Beispiel in einem anderen Verzeichnis als `C:\MySample\` installiert ist, bearbeiten Sie die Datei `Install.sql`wie gezeigt, damit sie auf diesen Speicherort verweist.  
  
7.  Stellen Sie die Assembly, die gespeicherte Prozedur und die Funktionen bereit, indem Sie die folgende Anweisung ausführen:  
  
    -   `sqlcmd -E -I -i install.sql`  
  
8.  Kopieren Sie den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Installationscode in eine Datei, und speichern Sie sie als `test.sql` im Beispielverzeichnis.  
  
9. Testen Sie die Anwendung, indem Sie an der Eingabeaufforderung die folgende Zeile ausführen:  
  
    -   `sqlcmd -E -I -i test.sql`  
  
10. Kopieren Sie das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Bereinigungsskript in eine Datei, und speichern Sie diese als `cleanup.sql` im Beispielverzeichnis.  
  
11. Führen Sie das Skript mit dem folgenden Befehl aus:  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a>Beispielcode  
 Die Codelistings für dieses Beispiel lauten wie folgt.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
public sealed class DataAccessDemo  
{  
        private DataAccessDemo()  
        {  
        }  
  
        /// <summary>  
/// Simple example to send a message to the client.  
/// </summary>  
public static void SendMessage(string msg)  
{  
SqlContext.Pipe.Send("Message from server: " + msg);  
}  
  
/// <summary>  
/// Simple example of performing data access within  
/// a function  
/// </summary>  
/// <returns></returns>  
        [Microsoft.SqlServer.Server.SqlFunction(DataAccess = Microsoft.SqlServer.Server.DataAccessKind.Read)]  
public static string ReportSqlVersion()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                //create a command from the current context  
                SqlCommand cmd = conn.CreateCommand();  
  
                //execute something  
                cmd.CommandText = "select @@version";  
  
                conn.Open();  
                //return results as scalar  
                return (string)cmd.ExecuteScalar();  
            }  
}  
  
/// <summary>  
/// Create a result set on the fly and send it to the client.  
/// </summary>  
public static void SendTransientResultSet()  
{  
//create the metadata for the columns  
            Microsoft.SqlServer.Server.SqlMetaData[] columnSchema   
                = new Microsoft.SqlServer.Server.SqlMetaData[] {  
new Microsoft.SqlServer.Server.SqlMetaData("stringcol", SqlDbType.NVarChar, 128)  
};  
  
//create a record based on that metadata  
            SqlDataRecord newRecord = new SqlDataRecord(columnSchema);  
  
//populate it  
newRecord.SetString(0, "Hello World!");  
  
//send it  
SqlContext.Pipe.Send(newRecord);  
}  
  
/// <summary>  
/// Execute a command and send the results to the client directly.  
/// </summary>  
public static void ExecuteToClient()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                SqlCommand cmd = conn.CreateCommand();  
  
                cmd.CommandText = "select @@version";  
                conn.Open();  
                SqlContext.Pipe.ExecuteAndSend(cmd);  
            }  
}  
  
/// <summary>  
/// Execute a command and send the resultig reader to the client  
/// </summary>  
public static void SendReaderToClient()  
{  
            using (SqlConnection conn = new SqlConnection("context connection=true"))  
            {  
                SqlCommand cmd = conn.CreateCommand();  
  
                cmd.CommandText = "select @@version";  
                conn.Open();  
                SqlDataReader rdr = cmd.ExecuteReader();  
                try  
                {  
                    SqlContext.Pipe.Send(rdr);  
                }  
                finally  
                {  
                    rdr.Close();  
                }  
            }  
}  
  
};  
```  
  
 Visual Basic  
  
```  
Imports Microsoft.SqlServer.Server  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Diagnostics  
Partial Public NotInheritable Class DataAccessDemo  
    Private Sub New()  
    End Sub  
  
    ''' <summary>  
    ''' Simple example of performing data access within a function  
    ''' </summary>  
    ''' <returns></returns>  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReportSqlVersion() As SqlString  
        Using conn As New SqlConnection("context connection=true")  
            'create a command from the current context  
            Dim cmd As SqlCommand = conn.CreateCommand()  
  
            'execute something  
            cmd.CommandText = "SELECT @@VERSION"  
  
            conn.Open()  
  
            'return results as scalar  
            Return CType(cmd.ExecuteScalar(), String)  
        End Using  
    End Function  
  
    ''' <summary>  
    ''' Simple example to send a message to the client.  
    ''' </summary>  
    Public Shared Sub SendMessage(ByVal msg As String)  
        SqlContext.Pipe.Send(("Message from server: " & msg))  
    End Sub  
  
    ''' <summary>  
    ''' Create a result set on the fly and send it to the client.  
    ''' </summary>  
    Public Shared Sub SendTransientResultSet()  
        'create the metadata for the columns  
        Dim columnSchema() As Microsoft.SqlServer.Server.SqlMetaData _  
            = {New SqlMetaData("stringcol", SqlDbType.NVarChar, 128)}  
  
        'create a record based on that metadata  
        Dim newRecord As New SqlDataRecord(columnSchema)  
  
        'populate it  
        newRecord.SetString(0, "Hello World!")  
  
        'send it  
        SqlContext.Pipe.Send(newRecord)  
    End Sub  
  
    ''' <summary>  
    ''' Execute a command and send the results to the client directly.  
    ''' </summary>  
    Public Shared Sub ExecuteToClient()  
        Using conn As New SqlConnection("context connection=true")  
            Dim cmd As SqlCommand = conn.CreateCommand()  
  
            cmd.CommandText = "SELECT @@VERSION"  
            conn.Open()  
            SqlContext.Pipe.ExecuteAndSend(cmd)  
        End Using  
    End Sub  
  
    ''' <summary>  
    ''' Execute a command and send the resulting reader to the client  
    ''' </summary>  
    Public Shared Sub SendReaderToClient()  
        Using conn As New SqlConnection("context connection=true")  
            Dim cmd As SqlCommand = conn.CreateCommand()  
            cmd.CommandText = "SELECT @@VERSION"  
            conn.Open()  
            Dim rdr As SqlDataReader = cmd.ExecuteReader()  
            Try  
                SqlContext.Pipe.Send(rdr)  
            Finally  
                rdr.Close()  
            End Try  
        End Using  
    End Sub  
  
End Class  
  
```  
  
 Dies ist das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Installationsskript (`Install.sql`), das die Assembly bereitstellt und die gespeicherten Prozeduren sowie die Funktion erstellt, die in diesem Beispiel benötigt werden.  
  
```  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendMessage')  
DROP PROCEDURE SendMessage;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendTransientResultSet')  
DROP PROCEDURE SendTransientResultSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'ExecuteToClient')  
DROP PROCEDURE ExecuteToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendReaderToClient')  
DROP PROCEDURE SendReaderToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'ReportSqlVersion' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [ReportSqlVersion];  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'InProcDA') DROP ASSEMBLY InProcDA;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath = N'C:\MySample\'  
CREATE ASSEMBLY InProcDA FROM @SamplesPath + 'InProcDA.dll'  
WITH permission_set = SAFE;  
GO  
  
CREATE PROCEDURE [SendMessage] @msg nvarchar(4000)  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendMessage];  
GO  
  
CREATE FUNCTION [ReportSqlVersion]() RETURNS nvarchar(4000)  
AS EXTERNAL NAME [InProcDA].[DataAccessDemo].[ReportSqlVersion];  
GO  
  
CREATE PROCEDURE [SendTransientResultSet]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendTransientResultSet];  
GO  
  
CREATE PROCEDURE [ExecuteToClient]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[ExecuteToClient];  
GO  
  
CREATE PROCEDURE [SendReaderToClient]  
AS  
EXTERNAL NAME [InProcDA].[DataAccessDemo].[SendReaderToClient];  
GO  
```  
  
 Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] (`test.sql`) das Beispiel getestet, hierfür werden die gespeicherten Prozeduren und die Funktion, die in diesem Beispiel definiert.  
  
```  
USE AdventureWorks;  
GO  
  
-- send a message to the client  
EXEC SendMessage  N'This is a test message.';  
  
-- exec a function that does data access  
SELECT dbo.ReportSqlVersion();  
  
-- exec the proc that sends a result set to the client  
EXEC SendTransientResultSet;  
  
EXEC ExecuteToClient;  
  
EXEC SendReaderToClient;  
  
USE master;  
GO  
  
```  
  
 Im folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code werden die Assembly, die Funktion und die gespeicherten Prozeduren aus der Datenbank entfernt.  
  
```  
  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendMessage')  
DROP PROCEDURE SendMessage;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendTransientResultSet')  
DROP PROCEDURE SendTransientResultSet;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'ExecuteToClient')  
DROP PROCEDURE ExecuteToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE name = N'SendReaderToClient')  
DROP PROCEDURE SendReaderToClient;  
GO  
  
IF EXISTS (SELECT * FROM sys.objects WHERE name = N'ReportSqlVersion' and (type = 'FS' or type = 'FT'))    
DROP FUNCTION [ReportSqlVersion];  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE name = N'InProcDA') DROP ASSEMBLY InProcDA;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwendungsszenarios und Beispiele für Common Language Runtime-Integration &#40;CLR&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
