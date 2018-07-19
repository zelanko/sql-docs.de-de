---
title: Hello World-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: fed6c358-f5ee-4d4c-9ad6-089778383ba7
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75ac8eafd490dc3a9b7501f7c653bc8aaf99cde4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37269926"
---
# <a name="hello-world-sample"></a>Beispiel "Hello World"
  Das Hello World-Beispiel veranschaulicht die grundlegenden Vorgänge, die beim Erstellen, Bereitstellen und Testen einer einfachen gespeicherten Prozedur, die auf einer CLR (Common Language Runtime)-Integration basiert, ausgeführt werden müssen. Diese Beispiel zeigt außerdem, wie Sie Daten über einen Datensatz, der dynamisch von der gespeicherten Prozedur erstellt und an den Aufrufer zurückgegeben wird, zurückgeben können.  
  
 Die `HelloWorld` gespeicherte Prozedur gibt die Zeichenfolge "Hello World!" in einem Resultset aus einer Zeile besteht. Dieses Beispiel veranschaulicht einige Verwendungsmöglichkeiten für die Klassen [Microsoft.SqlServer.Server.SqlMetaData](http://go.microsoft.com/fwlink/?LinkID=193572), [Microsoft.SqlServer.Server.SqlDataRecord](http://go.microsoft.com/fwlink/?LinkID=193573) und [ Microsoft.SqlServer.Server.Pipe](http://go.microsoft.com/fwlink/?LinkID=193571).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Erstellen und Ausführen dieses Projekts muss die folgende Software installiert sein:  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express erhalten Sie kostenlos auf der [Website](http://go.microsoft.com/fwlink/?LinkId=31046) mit der Dokumentation und den Beispielen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.  
  
-   Die AdventureWorks-Datenbank, die auf der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer-[Website](http://go.microsoft.com/fwlink/?linkid=62796) zur Verfügung gestellt wird.  
  
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
    >  Um CLR zu aktivieren, benötigen Sie `ALTER SETTINGS` Serverberechtigung, die implizit Mitglieder erhalten die `sysadmin` und `serveradmin` festen Serverrollen.  
  
-   Die AdventureWorks-Datenbank muss in der von Ihnen verwendeten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz installiert sein.  
  
-   Wenn Sie nicht-Administrator sind die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz, die Sie verwenden, benötigen Sie einen Administrator, die Sie gewähren **CreateAssembly** Berechtigung, um die Installation abzuschließen.  
  
## <a name="building-the-sample"></a>Erstellen des Beispiels  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a>Verwenden Sie die folgenden Anweisungen, um das Beispiel zu erstellen und auszuführen:  
  
1.  Wechseln Sie zu einer Visual Studio- oder .NET Framework-Eingabeaufforderung.  
  
2.  Erstellen Sie ggf. ein Verzeichnis für das Beispiel. Für dieses Beispiel wird C:\MySample verwendet.  
  
3.  Erstellen Sie in c:\MySample die Datei `HelloWorld.vb` (für das Visual Basic-Beispiel) oder `HelloWorld.cs` (für das C#-Beispiel), und kopieren Sie den entsprechenden Visual Basic- oder C#-Beispielcode (unten) in die Datei.  
  
4.  Kompilieren Sie an der Eingabeaufforderung den Beispielcode, indem Sie je nach gewählter Sprache eine der folgenden Anweisungen ausführen.  
  
    -   `vbc C:HelloWorld.vb /target:library`  
  
    -   `csc /target:library HelloWorld.cs`  
  
5.  Kopieren Sie den [!INCLUDE[tsql](../../includes/tsql-md.md)]-Installationscode in eine Datei, und speichern Sie sie als `Install.sql` im Beispielverzeichnis.  
  
6.  Stellen Sie die Assembly und die gespeicherte Prozedur bereit, indem Sie die folgende Anweisung ausführen:  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  Kopie [!INCLUDE[tsql](../../includes/tsql-md.md)] -testbefehlsskript in eine Datei, und speichern Sie ihn `test.sql` im Beispielverzeichnis.  
  
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
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
public partial class StoredProcedures  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld()  
    {  
        Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 12);  
        SqlDataRecord greetingRecord  
            = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
        greetingRecord.SetString(0, "Hello world!");  
        SqlContext.Pipe.Send(greetingRecord);  
    }  
};  
  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public NotInheritable Class StoredProcedures  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorld()  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 12)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, "Hello World!")  
        SqlContext.Pipe.Send(greetingRecord)  
    End Sub  
End Class  
```  
  
 Dies ist das [!INCLUDE[tsql](../../includes/tsql-md.md)]-Installationsskript (`Install.sql`), das die Assembly bereitstellt und die gespeicherte Prozedur in der Datenbank erstellt.  
  
```  
USE AdventureWorks  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
set @SamplesPath = '$(root)'  
CREATE ASSEMBLY HelloWorld   
FROM @SamplesPath + 'HelloWorld.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorld  
--(  
--    @Greeting nvarchar(12) OUTPUT  
--)  
AS EXTERNAL NAME HelloWorld.[StoredProcedures].HelloWorld;  
GO  
```  
  
 Dies ist die Datei `test.sql`, die das Beispiel durch das Ausführen der gespeicherten Prozedur testet.  
  
```  
use AdventureWorks  
go  
execute usp_HelloWorld  
  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
```  
  
 Im folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code werden die Assembly und die gespeicherte Prozedur aus der Datenbank entfernt.  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwendungsszenarios und Beispiele für Common Language Runtime-Integration &#40;CLR&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
