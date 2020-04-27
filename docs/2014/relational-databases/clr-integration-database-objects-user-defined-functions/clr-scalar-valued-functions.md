---
title: CLR-Skalarwertfunktionen | Microsoft-Dokumentation
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
- SVF
- scalar-valued functions
ms.assetid: 20dcf802-c27d-4722-9cd3-206b1e77bee0
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: cf5c0b6c7004f458e424e58d738cce22e97afa2b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62919589"
---
# <a name="clr-scalar-valued-functions"></a>CLR-Skalarwertfunktionen
  Eine Skalarwertfunktion gibt einen einzelnen Wert wie eine Zeichenfolge, eine ganze Zahl oder einen Bitwert zurück. Außerdem können Sie mithilfe einer beliebigen .NET Framework-Programmiersprache benutzerdefinierte Skalarwertfunktionen in verwaltetem Code erstellen. Auf diese Funktionen kann über [!INCLUDE[tsql](../../includes/tsql-md.md)] oder anderen verwalteten Code zugegriffen werden. Informationen zu den Vorteilen der CLR-Integration und zur Auswahl zwischen verwaltetem [!INCLUDE[tsql](../../includes/tsql-md.md)]Code und finden Sie unter [Übersicht über die CLR-Integration](../clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>Anforderungen für CLR-Skalarwertfunktionen  
 .NET Framework-Skalarwertfunktionen werden als Methoden einer Klasse in einer .NET Framework-Assembly implementiert. Die Eingabeparameter und der von einem SVF zurückgegebene Typ können einer der skalaren Datentypen sein, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von unter `varchar`stützt `char`werden `rowversion`, `text`außer `ntext`, `image`, `timestamp`, `table`,, `cursor`,, oder. Skalarwertfunktionen müssen sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp und der Rückgabedatentyp der Implementierungsmethode übereinstimmen. Weitere Informationen zu Typkonvertierungen finden Sie unter [Mapping von CLR-Parameter Daten](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
 Zur Implementierung einer .NET Framework-Skalarwertfunktion in einer .NET Framework-Sprache kann das benutzerdefinierte `SqlFunction`-Attribut angegeben werden, um zusätzliche Informationen über die Funktion aufzunehmen. Das `SqlFunction`-Attribut gibt an, ob die Funktion auf Daten zugreift oder Daten verändert, ob sie deterministisch ist und ob die Funktion Gleitkommaberechnungen beinhaltet.  
  
 Benutzerdefinierte Skalarwertfunktionen können deterministisch oder nicht deterministisch sein. Eine deterministische Funktion gibt immer dieselben Ergebnisse zurück, wenn sie mit einem bestimmten Satz an Eingabeparametern aufgerufen wird. Eine nicht deterministische Funktion kann unterschiedliche Ergebnisse zurückgeben, wenn sie mit einem bestimmten Satz an Eingabeparametern aufgerufen wird.  
  
> [!NOTE]  
>  Markieren Sie eine benutzerdefinierte Funktion nicht als deterministisch, wenn die Funktion bei denselben Eingabewerten und demselben Datenbankzustand nicht immer dieselben Ausgabewerte erzeugt. Das Markieren einer Funktion als deterministisch, wenn die Funktion nicht wirklich deterministisch ist, kann zu beschädigten indizierten Sichten und berechneten Spalten führen. Sie markieren eine Funktion als deterministisch, indem Sie die `IsDeterministic`-Eigenschaft auf true festlegen.  
  
### <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Tabellenwertparameter (Table Valued Parameters, TVPs), benutzerdefinierte Tabellentypen, die an eine Prozedur oder Funktion übergeben werden, bieten eine effiziente Methode zum Übergeben mehrerer Datenzeilen an den Server. TVPs verfügen über eine ähnliche Funktionalität wie Parameterarrays, bieten aber größere Flexibilität und engere Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)]. Außerdem verfügen sie auch über ein besseres Leistungspotenzial. TVPs helfen auch, die Anzahl von Roundtrips zum Server zu reduzieren. Anstatt mehrere Anforderungen an den Server zu senden, z. B. mit einer Liste von skalaren Parametern, können Daten als TVP an den Server gesendet werden. Ein benutzerdefinierter Tabellentyp kann nicht als Tabellenwertparameter an eine verwaltete gespeicherte Prozedur oder Funktion übergeben werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess ausgeführt wird, oder von einer solchen Prozedur oder Funktion zurückgegeben werden. Weitere Informationen zu TVPs finden Sie unter [Verwenden von Tabellenwert Parametern &#40;Datenbank-Engine&#41;](../tables/use-table-valued-parameters-database-engine.md).  
  
## <a name="example-of-a-clr-scalar-valued-function"></a>Beispiel für eine CLR-Skalarwertfunktion  
 Es folgt eine einfache Skalarwertfunktion, die auf Daten zugreift und einen ganzzahligen Wert zurückgibt:  
  
```csharp  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public class T  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static int ReturnOrderCount()  
    {  
        using (SqlConnection conn   
            = new SqlConnection("context connection=true"))  
        {  
            conn.Open();  
            SqlCommand cmd = new SqlCommand(  
                "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
            return (int)cmd.ExecuteScalar();  
        }  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public Class T  
    <SqlFunction(DataAccess:=DataAccessKind.Read)> _  
    Public Shared Function ReturnOrderCount() As Integer  
        Using conn As New SqlConnection("context connection=true")  
            conn.Open()  
            Dim cmd As New SqlCommand("SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
            Return CType(cmd.ExecuteScalar(), Integer)  
        End Using  
    End Function  
End Class  
```  
  
 Die erste Codezeile verweist auf `Microsoft.SqlServer.Server`, um auf Attribute zuzugreifen, und auf `System.Data.SqlClient`, um auf den ADO.NET-Namespace zuzugreifen. (Dieser Namespace enthält `SqlClient`, den .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)  
  
 Danach empfängt die Funktion das benutzerdefinierte `SqlFunction`-Attribut, das im `Microsoft.SqlServer.Server`-Namespace enthalten ist. Das benutzerdefinierte Attribut gibt an, ob die benutzerdefinierte Funktion (UDF) den prozessinternen Anbieter verwendet, um Daten im Server zu lesen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt nicht zu, dass UDFs Daten aktualisieren, einfügen oder löschen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die Ausführung einer UDF optimieren, die den prozessinternen Anbieter nicht verwendet. Dies wird angegeben, indem `DataAccessKind` auf `DataAccessKind.None` festgelegt wird. Die Zielmethode in der nächsten Zeile ist eine öffentliche statische Methode (shared in Visual Basic .NET).  
  
 Die `SqlContext`-Klasse, die im `Microsoft.SqlServer.Server`-Namespace enthalten ist, kann dann über die bereits eingerichtete Verbindung mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz auf ein `SqlCommand`-Objekt zugreifen. Hier wird zwar kein Gebrauch davon gemacht, aber auch der aktuelle Transaktionskontext ist über die `System.Transactions`-Anwendungsprogrammierschnittstelle (API) verfügbar.  
  
 Die meisten Codezeilen im Funktionsrumpf sollten Entwicklern bekannt vorkommen, die bereits Clientanwendungen mit Typen aus dem `System.Data.SqlClient`-Namespace geschrieben haben.  
  
 [C#]  
  
```  
using(SqlConnection conn = new SqlConnection("context connection=true"))   
{  
   conn.Open();  
   SqlCommand cmd = new SqlCommand(  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn);  
   return (int) cmd.ExecuteScalar();  
}    
```  
  
 [Visual Basic]  
  
```  
Using conn As New SqlConnection("context connection=true")  
   conn.Open()  
   Dim cmd As New SqlCommand( _  
        "SELECT COUNT(*) AS 'Order Count' FROM SalesOrderHeader", conn)  
   Return CType(cmd.ExecuteScalar(), Integer)  
End Using  
```  
  
 Der entsprechende Befehlstext wird angegeben, indem das `SqlCommand`-Objekt initialisiert wird. Im vorherigen Beispiel wird die Anzahl der Zeilen in der Tabelle `SalesOrderHeader` gezählt. Als Nächstes wird die `ExecuteScalar`-Methode des `cmd`-Objekts aufgerufen. Daraufhin wird ein Wert des Typs `int` zurückgegeben, der auf der Abfrage basiert. Abschließend wird die Anzahl der Bestellungen an den Aufrufer zurückgegeben.  
  
 Wenn dieser Code in einer Datei namens FirstUdf.cs gespeichert wird, kann er wie folgt als Assembly kompiliert werden:  
  
 [C#]  
  
```  
csc.exe /t:library /out:FirstUdf.dll FirstUdf.cs   
```  
  
 [Visual Basic]  
  
```  
vbc.exe /t:library /out:FirstUdf.dll FirstUdf.vb  
```  
  
> [!NOTE]  
>  `/t:library` gibt an, dass eine Bibliothek und keine ausführbare Datei erzeugt werden soll. Ausführbare Dateien können nicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert werden.  
  
> [!NOTE]  
>  Visual C++-Datenbankobjekte, die mit `/clr:pure` kompiliert wurden, können nicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden. Zu solchen Datenbankobjekten gehören beispielsweise Skalarwertfunktionen.  
  
 Die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Abfrage und ein Beispielaufruf zum Registrieren der Assembly und der UDF folgen:  
  
```  
CREATE ASSEMBLY FirstUdf FROM 'FirstUdf.dll';  
GO  
  
CREATE FUNCTION CountSalesOrderHeader() RETURNS INT   
AS EXTERNAL NAME FirstUdf.T.ReturnOrderCount;   
GO  
  
SELECT dbo.CountSalesOrderHeader();  
GO  
  
```  
  
 Beachten Sie, dass der Funktionsname, der in [!INCLUDE[tsql](../../includes/tsql-md.md)] angegeben wird, nicht mit dem Namen der öffentlichen statischen Zielmethode übereinstimmen muss.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Mapping von CLR-Parameter Daten](../clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [Übersicht über benutzerdefinierte Attribute der CLR-Integration](../../database-engine/dev-guide/overview-of-clr-integration-custom-attributes.md)   
 [Benutzerdefinierte Funktionen](../user-defined-functions/user-defined-functions.md)   
 [Data Access from CLR Database Objects](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
