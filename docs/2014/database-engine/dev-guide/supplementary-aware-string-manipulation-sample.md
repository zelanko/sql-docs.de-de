---
title: Beispiel für eine ergänzende Zeichen folgen Bearbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 343a1cd6-94e9-4200-9d17-11cef0d73f73
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2df5fa785f715dbf63c7682148c20bbaf971d0c1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "76928096"
---
# <a name="supplementary-aware-string-manipulation-sample"></a>Beispiel für Zeichenfolgendarstellung mit ergänzenden Zeichen
  Dieses Beispiel für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] veranschaulicht Zeichenfolgenbearbeitungen mit ergänzenden Zeichen. Dieses Beispiel zeigt die Implementierung von fünf Transact-SQL-Zeichenfolgenfunktionen, die dieselben Bearbeitungsfunktionen für Zeichenfolgen bereitstellen wie die integrierten Funktionen, jedoch zusätzliche Funktionen für ergänzende Zeichen bieten, um sowohl Unicode- als auch Sonderzeichenfolgen bearbeiten zu können. Die fünf Funktionen sind "Lens () `lefts(), rights(), subs()` " `replace_s()` und die den integrierten Funktionen `LEN(), LEFT(), RIGHT(), SUBSTRING()` und `REPLACE()` Zeichen folgen Funktionen entsprechen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Zum Erstellen und Ausführen dieses Projekts muss die folgende Software installiert sein:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express erhalten Sie kostenlos auf der [Website](https://www.microsoft.com/sql-server/sql-server-editions-express) mit der Dokumentation und den Beispielen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.  
  
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
  
-   Wenn Sie keine Administratorrechte für die von Ihnen verwendete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz besitzen, müssen Sie sich von einem Administrator die **CreateAssembly**-Berechtigung erteilen lassen, damit Sie die Installation ausführen können.  
  
## <a name="building-the-sample"></a>Erstellen des Beispiels  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a>Verwenden Sie die folgenden Anweisungen, um das Beispiel zu erstellen und auszuführen:  
  
1.  Wechseln Sie zu einer Visual Studio- oder .NET Framework-Eingabeaufforderung.  
  
2.  Erstellen Sie ggf. ein Verzeichnis für das Beispiel. Für dieses Beispiel wird C:\MySample verwendet.  
  
3.  Da dieses Beispiel eine signierte Assembly erfordert, erstellen Sie einen asymmetrischen Schlüssel, indem Sie folgenden Befehl eingeben:  
  
     `sn -k SampleKey.snk`  
  
4.  Kompilieren Sie an der Eingabeaufforderung den Beispielcode, indem Sie je nach gewählter Sprache eine der folgenden Anweisungen ausführen.  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll  /keyfile:Key.snk  /target:library SurrogateStringFunction.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll  /keyfile:Key.snk /target:library SurrogateStringFunction.cs`  
  
5.  Kopieren Sie den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Installationscode in eine Datei, und speichern Sie sie als `Install.sql` im Beispielverzeichnis.  
  
6.  Stellen Sie die Assembly und die gespeicherte Prozedur bereit, indem Sie die folgende Anweisung ausführen:  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  Kopieren [!INCLUDE[tsql](../../includes/tsql-md.md)] Sie das Test Befehls Skript in eine Datei, und `test.sql` speichern Sie Sie als im Beispiel Verzeichnis.  
  
8.  Führen Sie das Testskript mit dem folgenden Befehl aus:  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. Kopieren Sie das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Bereinigungsskript in eine Datei, und speichern Sie diese als `cleanup.sql` im Beispielverzeichnis.  
  
10. Führen Sie das Skript mit dem folgenden Befehl aus:  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a>Beispielcode  
 Die Codelistings für dieses Beispiel lauten wie folgt.  
  
 C#  
  
```  
using System;  
using System.Globalization;  
using System.Text;  
  
/// <summary>  
/// Include several string functions for T-SQL to manipulate surrogate characters.  
/// </summary>  
public sealed class SurrogateStringFunction  
{  
/// <summary>  
///  
/// </summary>  
private SurrogateStringFunction()  
{}  
  
/// <summary>  
/// LenS is equal to T-SQL string function LEN() which returns the number  
/// of characters, rather than the number of bytes, of the given string expression.  
/// </summary>  
/// <param name="value">The input string.</param>  
/// <returns>The number of characters in the string.</returns>  
public static long LenS(String value)  
{  
if (value == null) throw new ArgumentNullException("value");  
  
int[] myIndex;  
// Remove trailing spaces for situations when the Transact-SQL variable or table column  
// uses a fixed length datatype such as nchar(50).  
// If the trailing spaces are not excluded, this function will return 50 which is not  
// correct or expected.  
myIndex = StringInfo.ParseCombiningCharacters(value.TrimEnd());  
return (null != myIndex) ? myIndex.Length : 0;  
}  
  
/// <summary>  
/// SubS only support character expression of T-SQL funciton SUBSTRING()  
/// which returns part of a string.  
/// </summary>  
/// <param name="value">The input string.</param>  
/// <param name="start">The position of the first character that will be returned.</param>  
/// <param name="length">The number of characters to return.</param>  
/// <returns>The string found at the starting position for the specified  
/// number characters.</returns>  
  
public static String SubS(String value, int start, int length)  
{  
if (value == null) throw new ArgumentNullException("value");  
if (length < 0)  
                throw new ArgumentException("Invalid length parameter passed to the substring function.");  
  
// In Transact-SQL, the substring method initializes to 1. So, start should be initialized to at least 1.  
// Length also has to be at least 1 or the Transact-SQL result would be an empty string.  
            if ((start + length) <= 1)  
                return (String.Empty);  
  
// The 2 if statements below guarantee that the result will match the substring function in   
// Transact-SQL which will initialize start to 1 by subtracting from the length.  
            if (start <= 0 && length > 0)  
                length--;  
  
            if ((start <= 0))  
            {  
                length = length + start;  
                start = 1;  
            }  
  
            int[] myIndex;  
myIndex = StringInfo.ParseCombiningCharacters(value);  
int NumOfIndexes = (null != myIndex) ? myIndex.Length : 0;  
  
            start--;  
            if ((0 <= start) && (start < NumOfIndexes))  
{  
int lastIndex = start + length;  
  
// if we are past the last char, then we get the string  
// up to the last char   
if (lastIndex > (NumOfIndexes - 1))  
{  
return value.Substring(myIndex[start]);  
}  
else  
{  
return value.Substring(myIndex[start], myIndex[lastIndex] - myIndex[start]);  
}  
}  
else  
{  
return String.Empty;  
}  
}  
  
//   
//      
/// <summary>  
/// LeftS is equal to T-SQL string function LEFT() which returns the left  
/// part of a character string with the specified number of characters.  
/// </summary>  
/// <param name="value">The input string.</param>  
/// <param name="start">The position of the first character that will be returned.</param>  
/// <param name="length">The number of characters to return.</param>  
/// <returns>The string found at the starting position for n-length.</returns>  
  
public static String LeftS(String value, int length )  
{  
if (length < 0)  
throw new ArgumentException("length must be a positive integer");  
  
return SubS(value, 1, length);  
}  
  
// RightS is equal to T-SQL string function RIGHT() which returns the right  
//    part of a character string with the specified number of characters.  
  
public static String RightS(String value, int length)  
{  
if (length < 0)  
throw new NotSupportedException("length must be a positive integer");  
if (value == null) throw new ArgumentNullException("value");  
  
int[] myIndex;  
  
myIndex = StringInfo.ParseCombiningCharacters(value);  
int numOfIndexes = (null != myIndex) ? myIndex.Length : 0;  
  
if (numOfIndexes <= length)  
return value;  
  
if (length == 0) return String.Empty;  
  
int virtualStartIndex = numOfIndexes - length;  
int physicalStartIndex = myIndex[virtualStartIndex];  
return value.Substring(physicalStartIndex);  
  
}  
  
//  
// ReplaceS is equal to T-SQL string function REPLACE() which replaces all  
// occurrences of the second given string expression in the first string expression  
// with a third expression.  
//  
public static String ReplaceS(String value, String replaceValue, String newValue)  
{  
StringBuilder result = new StringBuilder(value.Length);  
int[] myIndex;  
int i = 0;  
String upperValue = value.ToUpper(CultureInfo.CurrentUICulture);  
String upperReplaceValue = replaceValue.ToUpper(CultureInfo.CurrentUICulture);  
  
myIndex = StringInfo.ParseCombiningCharacters(upperValue);  
while (i < value.Length)  
{  
int possibleMatch = upperValue.IndexOf(upperReplaceValue, i);  
if (possibleMatch < 0)  
{  
result.Append(value.Substring(i));  
break;  
}  
else  
{  
//Ensure we're not matching a partial surrogate  
int surrogateIndex = Array.IndexOf<int>(myIndex, possibleMatch);  
if (surrogateIndex < 0)  
{  
//We've matched in the middle of a surrogate, skip this match  
//as it is not valid.  
int nextStart = possibleMatch + 1;  
result.Append(value.Substring(i, nextStart-i));  
i = nextStart;  
}  
else  
{  
//This is a valid match.  Make the substitution.  
result.Append(value.Substring(i, possibleMatch - i));  
result.Append(newValue);  
i = possibleMatch + replaceValue.Length;  
}  
}  
}  
return result.ToString();  
}  
}  
```  
  
 Visual Basic  
  
```  
Imports Microsoft.VisualBasic  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Diagnostics  
Imports System.Globalization  
Imports System.Text  
''' <summary>  
''' Include several string functions for T-SQL to manipulate surrogate characters.  
''' </summary>  
  
Public NotInheritable Class SurrogateStringFunction  
    ''' <summary>  
    ''' Empty default constructor  
    ''' </summary>  
    Private Sub New()  
    End Sub  
  
    ''' <summary>  
    ''' LenS is equal to T-SQL string function LEN() which returns the number  
    ''' of characters, rather than the number of bytes, of the given string expression.  
    ''' </summary>  
    ''' <param name="value">The input string.</param>  
    ''' <returns>The number of characters in the string.</returns>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function LenS(ByVal value As String) As Long  
        If value Is Nothing Then  
            Throw New ArgumentNullException("value")  
        End If  
  
        Dim myIndex() As Integer  
        ' Remove trailing spaces for situations when the Transact-SQL variable or table column  
        ' uses a fixed length datatype such as nchar(50).  
        ' If the trailing spaces are not excluded, this function will return 50 which is not  
        ' correct or expected.  
        myIndex = StringInfo.ParseCombiningCharacters(value.TrimEnd())  
  
        If (myIndex IsNot Nothing) Then  
            Return myIndex.Length  
        Else  
            Return 0  
        End If  
    End Function  
  
    ''' <summary>  
    ''' SubS only support character expression of T-SQL funciton SUBSTRING()  
    ''' which returns part of a string.  
    ''' </summary>  
    ''' <param name="value">The input string.</param>  
    ''' <param name="start">The position of the first character that will be returned.</param>  
    ''' <param name="length">The number of characters to return.</param>  
    ''' <returns>The string found at the starting position for the specified  
    ''' number characters.</returns>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function SubS(ByVal value As String, ByVal start As Integer, ByVal length As Integer) As String  
        If value Is Nothing Then  
            Throw New ArgumentNullException("value")  
        End If  
  
        If length < 0 Then  
            Throw New ArgumentException("Invalid length parameter passed to the substring function.")  
        End If  
  
        ' In Transact-SQL, the substring method initializes to 1. So, start should be initialized to at least 1.  
        ' Length also has to be at least 1 or the Transact-SQL result would be an empty string.  
        If start + length <= 1 Then  
            Return String.Empty  
        End If  
  
        ' The 2 if statements below guarantee that the result will match the substring function in   
        ' Transact-SQL which will initialize start to 1 by subtracting from the length.  
        If start <= 0 AndAlso length > 0 Then  
            length -= 1  
        End If  
  
        If start <= 0 Then  
            length = length + start  
            start = 1  
        End If  
  
        Dim myIndex() As Integer  
        myIndex = StringInfo.ParseCombiningCharacters(value)  
  
        Dim NumOfIndexes As Integer  
        If (myIndex IsNot Nothing) Then  
            NumOfIndexes = myIndex.Length  
        Else  
            NumOfIndexes = 0  
        End If  
  
        start -= 1  
        If 0 <= start AndAlso start < NumOfIndexes Then  
            Dim lastIndex As Integer = start + length  
  
            ' if we are past the last char, then we get the string  
            ' up to the last char   
            If lastIndex > NumOfIndexes - 1 Then  
                Return value.Substring(myIndex(start))  
            Else  
                Return value.Substring(myIndex(start), myIndex(lastIndex) - myIndex(start))  
            End If  
        Else  
            Return String.Empty  
        End If  
    End Function  
  
    ''' <summary>  
    ''' LeftS is equal to T-SQL string function LEFT() which returns the left  
    ''' part of a character string with the specified number of characters.  
    ''' </summary>  
    ''' <param name="value">The input string.</param>  
    ''' <param name="length">The number of characters to return.</param>  
    ''' <returns>The string found at the starting position for n-length.</returns>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function LeftS(ByVal value As String, ByVal length As Integer) As String  
        If length < 0 Then  
            Throw New ArgumentException("Length must be a positive integer")  
        End If  
  
        Return SubS(value, 1, length)  
    End Function  
  
    ' RightS is equal to T-SQL string function RIGHT() which returns the right  
    '    part of a character string with the specified number of characters.  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function RightS(ByVal value As String, ByVal length As Integer) As String  
        If value Is Nothing Then  
            Throw New ArgumentNullException("value")  
        End If  
  
        If length < 0 Then  
            Throw New NotSupportedException("Length must be a positive integer")  
        End If  
  
        Dim myIndex() As Integer  
  
        myIndex = StringInfo.ParseCombiningCharacters(value)  
        Dim NumOfIndexes As Integer  
        If (myIndex IsNot Nothing) Then  
            NumOfIndexes = myIndex.Length  
        Else  
            NumOfIndexes = 0  
        End If  
  
        If NumOfIndexes <= length Then  
            Return value  
        End If  
  
        If length = 0 Then  
            Return String.Empty  
        End If  
  
        Dim virtualStartIndex As Integer = NumOfIndexes - length  
        Dim physicalStartIndex As Integer = myIndex(virtualStartIndex)  
  
        Return value.Substring(physicalStartIndex)  
    End Function  
  
    ''' <summary>  
    ''' ReplaceS is equal to T-SQL string function REPLACE() which replaces all  
    ''' occurrences of the second given string expression in the first string expression  
    ''' with a third expression.  
    ''' </summary>  
    ''' <param name="value"></param>  
    ''' <param name="replaceValue"></param>  
    ''' <param name="newValue"></param>  
    ''' <returns></returns>  
    ''' <remarks></remarks>  
    <Microsoft.SqlServer.Server.SqlFunction()> _  
    Public Shared Function ReplaceS(ByVal value As String, ByVal replaceValue As String, ByVal newValue As String) As String  
        Dim result As New StringBuilder(value.Length)  
        Dim myIndex() As Integer  
        Dim i As Integer = 0  
        Dim upperValue As String = value.ToUpper(CultureInfo.CurrentUICulture)  
        Dim upperReplaceValue As String = replaceValue.ToUpper(CultureInfo.CurrentUICulture)  
  
        myIndex = StringInfo.ParseCombiningCharacters(upperValue)  
  
        While i < value.Length  
            Dim possibleMatch As Integer = upperValue.IndexOf(upperReplaceValue, i)  
            If possibleMatch < 0 Then  
                result.Append(value.Substring(i))  
                Exit While  
            Else  
                'Ensure we're not matching a partial surrogate  
                Dim surrogateIndex As Integer = Array.IndexOf(Of Integer)(myIndex, possibleMatch)  
                If surrogateIndex < 0 Then  
                    'We've matched in the middle of a surrogate, skip this match  
                    'as it is not valid.  
                    Dim nextStart As Integer = possibleMatch + 1  
                    result.Append(value.Substring(i, nextStart - i))  
                    i = nextStart  
                Else  
                    'This is a valid match.  Make the substitution.  
                    result.Append(value.Substring(i, possibleMatch - i))  
                    result.Append(newValue)  
                    i = possibleMatch + replaceValue.Length  
                End If  
            End If  
        End While  
  
        Return result.ToString()  
    End Function  
End Class  
```  
  
 Dies ist das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Installationsskript (`Install.sql`), das die Assembly bereitstellt und die Funktionen mit ergänzenden Funktionen in der Datenbank erstellt.  
  
```  
Use [AdventureWorks]  
Go  
  
IF OBJECT_ID('[dbo].[len_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[len_s];  
  
IF OBJECT_ID('[dbo].[sub_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[sub_s];  
  
IF OBJECT_ID('[dbo].[left_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[left_s];  
  
IF OBJECT_ID('[dbo].[right_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[right_s];  
  
IF OBJECT_ID('[dbo].[replace_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[replace_s];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies  
             WHERE [name] = 'SurrogateStringFunction')  
  DROP ASSEMBLY SurrogateStringFunction;  
GO  
  
USE master  
GO  
  
IF EXISTS (SELECT * FROM sys.server_principals WHERE [name] = 'ExternalSample_Login')  
DROP LOGIN ExternalSample_Login;  
GO  
  
IF EXISTS (SELECT * FROM sys.asymmetric_keys WHERE [name] = 'ExternalSample_Key')  
DROP ASYMMETRIC KEY ExternalSample_Key;  
GO  
  
--Before we register the assembly to SQL Server, we must arrange for the appropriate permissions.  
--Assemblies with unsafe or external_access permissions can only be registered and operate correctly  
--if either the database trustworthy bit is set or if the assembly is signed with a key,  
--that key is registered with SQL Server, a server principal is created from that key,  
--and that principal is granted the external access or unsafe assembly permission.  We choose  
--the latter approach as it is more granular, and therefore safer.  You should never  
--register an assembly with SQL Server (especially with external_access or unsafe permissions) without  
--thoroughly reviewing the source code of the assembly to make sure that its actions   
--do not pose an operational or security risk for your site.  
  
DECLARE @SamplesPath nvarchar(1024);  
  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
set @SamplesPath = N'C:\MySample\'  
  
EXEC('CREATE ASYMMETRIC KEY ExternalSample_Key FROM EXECUTABLE FILE = ''' + @SamplesPath   
    + 'SurrogateStringFunction.dll'';');  
CREATE LOGIN ExternalSample_Login FROM ASYMMETRIC KEY ExternalSample_Key  
GRANT EXTERNAL ACCESS ASSEMBLY TO ExternalSample_Login;  
GO  
  
USE AdventureWorks;  
GO  
  
--  
-- Create assembly to register class methods for create functions  
--   
DECLARE @SamplesPath nvarchar(1024);  
-- You may need to modify the value of the this variable if you have installed the sample someplace other than the default location.  
  
set @SamplesPath = N'C:\MySample\'  
  
CREATE ASSEMBLY [SurrogateStringFunction]  
FROM @SamplesPath + 'SurrogateStringFunction.dll'  
WITH PERMISSION_SET = EXTERNAL_ACCESS;  
GO  
  
CREATE FUNCTION [dbo].[len_s] (@str nvarchar(4000))  
RETURNS bigint  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[LenS];  
GO  
  
CREATE FUNCTION [dbo].[sub_s](@str nvarchar(4000), @pos int, @cont int)  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[SubS];  
GO  
  
CREATE FUNCTION [dbo].[left_s](@str nvarchar(4000), @cont int)  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[LeftS];  
GO  
  
CREATE FUNCTION [dbo].[right_s](@str nvarchar(4000), @cont int)  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[RightS];  
GO  
  
CREATE FUNCTION [dbo].[replace_s](@str nvarchar(4000), @str1 nvarchar(4000), @str2 nvarchar(4000))  
RETURNS nvarchar(4000)  
AS EXTERNAL NAME [SurrogateStringFunction].[SurrogateStringFunction].[ReplaceS];  
GO  
```  
  
 Dies ist die Datei `test.sql`, die das Beispiel durch das Ausführen der Funktionen testet.  
  
```  
Use [AdventureWorks]  
Go  
  
-- left_s  VS  Left  
print ('***** left_s VS Left *****');  
select [dbo].[left_s](N'𠱷𠱸123',2);  
print(N'Should Return 𠱷𠱸');  
go  
select Left(N'𠱷𠱸123',2);  
print(N'Will Return 𠱷');  
go  
  
-- right_s VS Right  
print ('***** right_s VS Right *****')  
select [dbo].[right_s](N'𠱷𠱸123',5);  
print(N'Should Return 𠱷𠱸123');  
go  
select Right(N'𠱷𠱸123',5);  
print(N'Will Return 𠱸123');  
go  
  
-- len_s  VS Len  
print('***** len_s VS Len *****');  
select [dbo].[len_s](N'𠆾𠇀𠇃12');  
print(N'Should Return 5');  
go  
select Len(N'𠆾𠇀𠇃12');  
print(N'Will Return 8');  
go  
  
-- sub_s VS Substring  
print('***** sub_s VS Subscription *****');  
select [dbo].[sub_s] (N'𢙢𢙣𢙤𢙥𢙦𢙧𢙨𢙩𢙪𢙫𢙬𢙭𢙮𢙯𢙰𢙱𢙲𢙳',3,5);  
print(N'Should Return 𢙤𢙥𢙦𢙧𢙨');  
go  
select substring(N'𢙢𢙣𢙤𢙥𢙦𢙧𢙨𢙩𢙪𢙫𢙬𢙭𢙮𢙯𢙰𢙱𢙲𢙳',3,5);  
print(N'Will Return 𢙣𢙤');  
go  
  
-- replace_s VS Replace  
print('***** replace_s VS Replace *****');  
select [dbo].[replace_s](N'𡥕𡥖𡥗𡥙𡥚𡥛𡥕𡥖𡥗𡥙𡥚𡥛',N'𡥗𡥙𡥚',N'𡦼');  
print(N'Should Return 𡥖𡦼𡥛𡥕𡥖𡦼𡥛');  
go  
select replace(N'𡥕𡥖𡥗𡥙𡥚𡥛𡥕𡥖𡥗𡥙𡥚𡥛',N'𡥗𡥙𡥚',N'𡦼');  
print(N'Will Return 𡦼');  
go  
```  
  
 Im folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code werden die Assembly und die Funktionen aus der Datenbank entfernt.  
  
```  
-- Drop assemblies and functions if they exist.  
USE [AdventureWorks]  
GO  
  
IF OBJECT_ID('[dbo].[len_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[len_s];  
  
IF OBJECT_ID('[dbo].[sub_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[sub_s];  
  
IF OBJECT_ID('[dbo].[left_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[left_s];  
  
IF OBJECT_ID('[dbo].[right_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[right_s];  
  
IF OBJECT_ID('[dbo].[replace_s]') IS NOT NULL  
  DROP FUNCTION [dbo].[replace_s];  
GO  
  
IF EXISTS (SELECT [name] FROM sys.assemblies  
             WHERE [name] = 'SurrogateStringFunction')  
  DROP ASSEMBLY SurrogateStringFunction;  
GO  
  
USE master  
GO  
  
IF EXISTS (SELECT * FROM sys.server_principals WHERE [name] = 'ExternalSample_Login')  
DROP LOGIN ExternalSample_Login;  
GO  
  
IF EXISTS (SELECT * FROM sys.asymmetric_keys WHERE [name] = 'ExternalSample_Key')  
DROP ASYMMETRIC KEY ExternalSample_Key;  
GO  
  
USE [AdventureWorks]  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwendungsszenarios und Beispiele für Common Language Runtime-Integration &#40;CLR&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
