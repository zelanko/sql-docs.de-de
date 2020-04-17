---
title: CLR Scalar-Bewertete Funktionen | Microsoft Docs
description: Eine Skalarwertfunktion gibt einen einzelnen Wert zurück. In der SQL Server CLR-Integration können Sie scalar-bewertete benutzerdefinierte Funktionen in verwalteten Code schreiben.
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
ms.openlocfilehash: a44187fc41409d149501c4cda7e99817be034a12
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488429"
---
# <a name="clr-scalar-valued-functions"></a>CLR-Skalarwertfunktionen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Eine Skalarwertfunktion (SVF) gibt einen einzelnen Wert zurück, z. B. eine Zeichenfolge, eine ganze Zahl oder einen Bitwert. Sie können benutzerdefinierte Funktionen mit skalarer Bewertung in verwaltetem Code mit einer beliebigen .NET Framework-Programmiersprache erstellen. Auf diese Funktionen kann über [!INCLUDE[tsql](../../includes/tsql-md.md)] oder anderen verwalteten Code zugegriffen werden. Informationen zu den Vorteilen der CLR-Integration [!INCLUDE[tsql](../../includes/tsql-md.md)]und der Auswahl zwischen verwaltetem Code und , finden Sie unter [Übersicht über CLR-Integration](../../relational-databases/clr-integration/clr-integration-overview.md).  
  
## <a name="requirements-for-clr-scalar-valued-functions"></a>Anforderungen für CLR-Skalarwertfunktionen  
 .NET Framework-Skalarwertfunktionen werden als Methoden einer Klasse in einer .NET Framework-Assembly implementiert. Die Eingabeparameter und der von einem SVF zurückgegebene Typ können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]alle skalaren Datentypen sein, die von unterstützt werden, mit Ausnahme von **varchar**, **char**, **rowversion**, **text**, **ntext**, **image**, **timestamp**, **table**, oder **cursor**. Skalarwertfunktionen müssen sicherstellen, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp und der Rückgabedatentyp der Implementierungsmethode übereinstimmen. Weitere Informationen zu Typkonvertierungen finden Sie unter [Zuordnen von CLR-Parameterdaten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md).  
  
 Beim Implementieren einer .NET Framework SVF in einer .NET Framework-Sprache kann das benutzerdefinierte **SqlFunction-Attribut** angegeben werden, um zusätzliche Informationen über die Funktion einzuschließen. Das **SqlFunction-Attribut** gibt an, ob die Funktion auf Daten zugreift oder diese ändert, ob sie deterministisch ist und ob die Funktion Gleitkommaoperationen umfasst.  
  
 Benutzerdefinierte Skalarwertfunktionen können deterministisch oder nicht deterministisch sein. Eine deterministische Funktion gibt immer dieselben Ergebnisse zurück, wenn sie mit einem bestimmten Satz an Eingabeparametern aufgerufen wird. Eine nicht deterministische Funktion kann unterschiedliche Ergebnisse zurückgeben, wenn sie mit einem bestimmten Satz an Eingabeparametern aufgerufen wird.  
  
> [!NOTE]  
>  Markieren Sie eine benutzerdefinierte Funktion nicht als deterministisch, wenn die Funktion bei denselben Eingabewerten und demselben Datenbankzustand nicht immer dieselben Ausgabewerte erzeugt. Das Markieren einer Funktion als deterministisch, wenn die Funktion nicht wirklich deterministisch ist, kann zu beschädigten indizierten Ansichten und berechneten Spalten führen. Sie markieren eine Funktion als deterministisch, indem Sie die **IsDeterministic-Eigenschaft** auf true festlegen.  
  
### <a name="table-valued-parameters"></a>Tabellenwertparameter  
 Tabellenwertparameter (Table Valued Parameters, TVPs), benutzerdefinierte Tabellentypen, die an eine Prozedur oder Funktion übergeben werden, bieten eine effiziente Methode zum Übergeben mehrerer Datenzeilen an den Server. TVPs verfügen über eine ähnliche Funktionalität wie Parameterarrays, bieten aber größere Flexibilität und engere Integration mit [!INCLUDE[tsql](../../includes/tsql-md.md)]. Außerdem verfügen sie auch über ein besseres Leistungspotenzial. TVPs helfen auch, die Anzahl von Roundtrips zum Server zu reduzieren. Anstatt mehrere Anforderungen an den Server zu senden, z. B. mit einer Liste von skalaren Parametern, können Daten als TVP an den Server gesendet werden. Ein benutzerdefinierter Tabellentyp kann nicht als Tabellenwertparameter an eine verwaltete gespeicherte Prozedur oder Funktion übergeben werden, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozess ausgeführt wird, oder von einer solchen Prozedur oder Funktion zurückgegeben werden. Weitere Informationen zu TVPs finden Sie unter Verwenden von [Tabellenwertparametern &#40;Datenbankmodul&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md).  
  
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
  
 Die erste Codezeile verweist auf **Microsoft.SqlServer.Server,** um auf Attribute zuzugreifen, und **auf System.Data.SqlClient,** um auf den ADO.NET Namespace zuzugreifen. (Dieser Namespace enthält **SqlClient**, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].NET Framework-Datenanbieter für .)  
  
 Als Nächstes empfängt die Funktion das benutzerdefinierte **SqlFunction-Attribut,** das im **Microsoft.SqlServer.Server-Namespace** gefunden wird. Das benutzerdefinierte Attribut gibt an, ob die benutzerdefinierte Funktion (UDF) den prozessinternen Anbieter verwendet, um Daten im Server zu lesen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lässt nicht zu, dass UDFs Daten aktualisieren, einfügen oder löschen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die Ausführung einer UDF optimieren, die den prozessinternen Anbieter nicht verwendet. Dies wird durch Festlegen von **DataAccessKind** auf **DataAccessKind.None**angezeigt. Die Zielmethode in der nächsten Zeile ist eine öffentliche statische Methode (shared in Visual Basic .NET).  
  
 Die **SqlContext-Klasse,** die sich im **Microsoft.SqlServer.Server-Namespace** befindet, kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dann auf ein **SqlCommand-Objekt** mit einer Verbindung mit der Instanz zugreifen, die bereits eingerichtet ist. Obwohl hier nicht verwendet wird, ist der aktuelle Transaktionskontext auch über die **System.Transactions-Api** (Application Programming Interface) verfügbar.  
  
 Die meisten Codezeilen im Funktionstext sollten Entwicklern vertraut sein, die Clientanwendungen geschrieben haben, die die typen im **System.Data.SqlClient-Namespace** verwenden.  
  
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
  
 Der entsprechende Befehlstext wird durch Initialisieren des **SqlCommand-Objekts** angegeben. Im vorherigen Beispiel wird die Anzahl der Zeilen in der Tabelle **SalesOrderHeader**gezählt. Als Nächstes wird die **ExecuteScalar-Methode** des **cmd-Objekts** aufgerufen. Dadurch wird ein Wert vom Typ **int** basierend auf der Abfrage zurückgegeben. Abschließend wird die Anzahl der Bestellungen an den Aufrufer zurückgegeben.  
  
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
>  Visual C++-Datenbankobjekte, die mit **/clr:pure** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kompiliert wurden, werden für die Ausführung auf nicht unterstützt. Zu solchen Datenbankobjekten gehören beispielsweise Skalarwertfunktionen.  
  
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
 [Zuordnen von CLR-Parameterdaten](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)   
 [Übersicht über clR Integration Custom Attribute](https://msdn.microsoft.com/library/ecf5c097-0972-48e2-a9c0-b695b7dd2820)   
 [Benutzerdefinierte Funktionen](../../relational-databases/user-defined-functions/user-defined-functions.md)   
 [Data Access from CLR Database Objects](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
