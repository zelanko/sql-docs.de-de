---
title: CLR-Skalarwertfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
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
ms.openlocfilehash: ac063fa59d22308cb90206816555eea8474acca6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68009773"
---
# <a name="clr-scalar-valued-functions"></a>CLR-Skalarwertfunktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Eine Skalarwertfunktion gibt einen einzelnen Wert wie eine Zeichenfolge, eine ganze Zahl oder einen Bitwert zurück. Außerdem können Sie mithilfe einer beliebigen .NET Framework-Programmiersprache benutzerdefinierte Skalarwertfunktionen in verwaltetem Code erstellen. Auf diese Funktionen kann über [!INCLUDE[tsql](../../includes/tsql-md.md)] oder anderen verwalteten Code zugegriffen werden. Informationen zu den Vorteilen der CLR-Integration und zur Auswahl zwischen verwaltetem [!INCLUDE[tsql](../../includes/tsql-md.md)]Code und finden Sie unter [Übersicht über die CLR-Integration](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>Anforderungen für CLR-Skalarwertfunktionen  
 .NET Framework-Skalarwertfunktionen werden als Methoden einer Klasse in einer .NET Framework-Assembly implementiert. Die Eingabeparameter und der von einem SVF zurückgegebene Typ können einer der skalaren Datentypen sein, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von unterstützt werden, mit Ausnahme von **varchar**, **char**, **rowversion**, **Text**, **ntext**, **Image**, **Zeitstempel**, **Table**oder **Cursor**. Skalarwertfunktionen müssen sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp und der Rückgabedatentyp der Implementierungsmethode übereinstimmen. Weitere Informationen zu Typkonvertierungen finden Sie unter [Mapping von CLR-Parameter Daten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
 Beim Implementieren eines .NET Framework SVF in einer .NET Framework Sprache kann das benutzerdefinierte **SqlFunction** -Attribut angegeben werden, um zusätzliche Informationen über die Funktion einzuschließen. Das **SqlFunction** -Attribut gibt an, ob die Funktion auf Daten zugreift oder diese ändert, ob Sie deterministisch ist und ob die Funktion Gleit Komma Vorgänge einschließt.  
  
 Benutzerdefinierte Skalarwertfunktionen können deterministisch oder nicht deterministisch sein. Eine deterministische Funktion gibt immer dieselben Ergebnisse zurück, wenn sie mit einem bestimmten Satz an Eingabeparametern aufgerufen wird. Eine nicht deterministische Funktion kann unterschiedliche Ergebnisse zurückgeben, wenn sie mit einem bestimmten Satz an Eingabeparametern aufgerufen wird.  
  
> [!NOTE]  
>  Markieren Sie eine benutzerdefinierte Funktion nicht als deterministisch, wenn die Funktion bei denselben Eingabewerten und demselben Datenbankzustand nicht immer dieselben Ausgabewerte erzeugt. Das Markieren einer Funktion als deterministisch, wenn die Funktion nicht wirklich deterministisch ist, kann zu beschädigten indizierten Sichten und berechneten Spalten führen. Sie markieren eine Funktion als deterministisch, indem Sie die **IsDeterministic** -Eigenschaft auf "true" festlegen.  
  
### <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Tabellenwertparameter (Table Valued Parameters, TVPs), benutzerdefinierte Tabellentypen, die an eine Prozedur oder Funktion übergeben werden, bieten eine effiziente Methode zum Übergeben mehrerer Datenzeilen an den Server. TVPs verfügen über eine ähnliche Funktionalität wie Parameterarrays, bieten aber größere Flexibilität und engere Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)]. Außerdem verfügen sie auch über ein besseres Leistungspotenzial. TVPs helfen auch, die Anzahl von Roundtrips zum Server zu reduzieren. Anstatt mehrere Anforderungen an den Server zu senden, z. B. mit einer Liste von skalaren Parametern, können Daten als TVP an den Server gesendet werden. Ein benutzerdefinierter Tabellentyp kann nicht als Tabellenwertparameter an eine verwaltete gespeicherte Prozedur oder Funktion übergeben werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess ausgeführt wird, oder von einer solchen Prozedur oder Funktion zurückgegeben werden. Weitere Informationen zu TVPs finden Sie unter [Verwenden von Tabellenwert Parametern &#40;Datenbank-Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
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
  
 Die erste Codezeile verweist auf **Microsoft. SqlServer. Server** , um auf Attribute und **System. Data. SqlClient** zuzugreifen, um auf den ADO.NET-Namespace zuzugreifen. (Dieser Namespace enthält **SqlClient**, den .NET Framework Datenanbieter für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)  
  
 Als nächstes empfängt die Funktion das benutzerdefinierte **SqlFunction** -Attribut, das im **Microsoft. SqlServer. Server** -Namespace enthalten ist. Das benutzerdefinierte Attribut gibt an, ob die benutzerdefinierte Funktion (UDF) den prozessinternen Anbieter verwendet, um Daten im Server zu lesen. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt nicht zu, dass UDFs Daten aktualisieren, einfügen oder löschen. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die Ausführung einer UDF optimieren, die den prozessinternen Anbieter nicht verwendet. Dies wird durch Festlegen von **DataAccessKind** auf **DataAccessKind. None**angegeben. Die Zielmethode in der nächsten Zeile ist eine öffentliche statische Methode (shared in Visual Basic .NET).  
  
 Die **SqlContext** -Klasse, die sich im **Microsoft. SqlServer. Server** -Namespace befindet, kann dann auf ein **SqlCommand** -Objekt mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einer Verbindung mit der Instanz zugreifen, die bereits eingerichtet ist. Obwohl Sie hier nicht verwendet wird, ist der aktuelle Transaktionskontext auch über die **System. Transactions** -API (Application Programming Interface) verfügbar.  
  
 Die meisten Codezeilen im Funktions Rumpf sollten Entwicklern vertraut sein, die Client Anwendungen geschrieben haben, die die im **System. Data. SqlClient** -Namespace gefundenen Typen verwenden.  
  
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
  
 Der entsprechende Befehls Text wird durch Initialisieren des **SqlCommand** -Objekts angegeben. Im vorherigen Beispiel wird die Anzahl der Zeilen in der **SalesOrderHeader**-Tabelle gezählt. Als nächstes wird die **ExecuteScalar** -Methode des **cmd** -Objekts aufgerufen. Dadurch wird ein Wert vom Typ " **int** " basierend auf der Abfrage zurückgegeben. Abschließend wird die Anzahl der Bestellungen an den Aufrufer zurückgegeben.  
  
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
>  
  `/t:library` gibt an, dass eine Bibliothek und keine ausführbare Datei erzeugt werden soll. Ausführbare Dateien können nicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] registriert werden.  
  
> [!NOTE]  
>  Visual C++ Datenbankobjekte, die mit **/clr: pure** kompiliert werden, werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]für die Ausführung unter nicht unterstützt. Zu solchen Datenbankobjekten gehören beispielsweise Skalarwertfunktionen.  
  
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
 [Mapping von CLR-Parameter Daten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [Übersicht über benutzerdefinierte Attribute der CLR-Integration](https://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)   
 [Benutzerdefinierte Funktionen](../../relational-databases/user-defined-functions/user-defined-functions.md)   
 [Data Access from CLR Database Objects](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
