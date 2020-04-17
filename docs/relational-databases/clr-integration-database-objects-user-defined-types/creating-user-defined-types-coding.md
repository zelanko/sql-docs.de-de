---
title: Codieren benutzerdefinierter Typen | Microsoft Docs
description: In diesem Beispiel wird gezeigt, wie Sie eine UDT implementieren, die in einer SQL Server-Datenbank verwendet werden soll. Es implementiert die UDT als Struktur.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
author: rothja
ms.author: jroth
ms.openlocfilehash: a9d51cc0c33c8b656df176baa606a88a542ca4bc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486954"
---
# <a name="creating-user-defined-types---coding"></a>Erstellen benutzerdefinierter Typen: Codieren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn Sie die Definition eines benutzerdefinierten Typs (UDT) schreiben, müssen Sie verschiedene Funktionen implementieren, abhängig davon, ob Sie den UDT als Klasse oder als Struktur implementieren, sowie abhängig von den von Ihnen gewählten Format- und Serialisierungsoptionen.  
  
 Das Beispiel in diesem Abschnitt veranschaulicht das Implementieren eines **Punkt-UDT** als **Struktur** (oder **Struktur** in Visual Basic). Die **Point** Punkt-UDT besteht aus X- und Y-Koordinaten, die als Eigenschaftsverfahren implementiert sind.  
  
 Beim Definieren eines UDTs sind die folgenden Namespaces erforderlich:  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 Der **Namespace Microsoft.SqlServer.Server** enthält die Objekte, die für verschiedene Attribute Ihrer UDT erforderlich sind, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und der **Namespace System.Data.SqlTypes** enthält die Klassen, die systemeigene Datentypen darstellen, die für die Assembly verfügbar sind. Es kann natürlich zusätzliche Namespaces geben, die eine Assembly erfordert, um ordnungsgemäß zu funktionieren. Die **Point** UDT verwendet auch den **Namespace System.Text** für die Arbeit mit Zeichenfolgen.  
  
> [!NOTE]  
>  Visuelle C++-Datenbankobjekte, z. B. UDTs, die mit **/clr:pure** kompiliert werden, werden für die Ausführung nicht unterstützt.  
  
## <a name="specifying-attributes"></a>Angeben von Attributen  
 Attribute bestimmen, wie die Serialisierung verwendet wird, um die Speicherdarstellung von UDTs zu erstellen und um UDTs durch Werte an den Client zu übertragen.  
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** ist erforderlich. Das **Serialisierbare** Attribut ist optional. Sie können auch **Microsoft.SqlServer.Server.SqlFacetAttribute** angeben, um Informationen über den Rückgabetyp einer UDT bereitzustellen. Weitere Informationen finden Sie unter [Benutzerdefinierte Attribute für CLR-Routinen](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Attribute des Point-UDT  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** legt das Speicherformat für den **Punkt** UDT auf **Native**fest. **IsByteOrdered** ist auf **true**festgelegt, was garantiert, dass die Vergleichsergebnisse in SQL Server identisch sind, als ob derselbe Vergleich im verwalteten Code stattgefunden hätte. Die UDT implementiert die **Schnittstelle System.Data.SqlTypes.INullable,** um die UDT-NULL zu beachten.  
  
 Das folgende Codefragment zeigt die **Point** Attribute für die Punkt-UDT.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a>Implementieren von NULL-Zulässigkeit  
 Zusätzlich zum ordnungsgemäßen Angeben der Attribute für die Assemblys muss der UDT auch die NULL-Zulässigkeit unterstützen. UdTs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die in geladen werden, sind null-fähig, aber damit die UDT einen NULL-Wert erkennen kann, muss die UDT die **Schnittstelle System.Data.SqlTypes.INullable** implementieren.  
  
 Sie müssen eine Eigenschaft mit dem Namen **IsNull**erstellen, die erforderlich ist, um zu bestimmen, ob ein Wert aus CLR-Code null ist. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine NULL-Instanz eines UDTs findet, wird der UDT mit normalen Behandlungsmethoden für NULL-Werte persistent gespeichert. Der Server vergeudet keine Zeit mit dem Serialisieren oder Deserialisieren des UDTs, wenn dies nicht erforderlich ist, und er verschwendet keinen Platz zum Speichern des NULL-UDTs. Diese Überprüfung auf NULL wird jedes Mal durchgeführt, wenn ein UDT von der CLR übernommen wird. Das heißt, dass mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Konstrukt immer überprüft werden kann, ob UDTs NULL sind. Die **IsNull-Eigenschaft** wird auch vom Server verwendet, um zu testen, ob eine Instanz null ist. Sobald der Server bestimmt, dass der UDT NULL ist, kann er seine systemeigene NULL-Behandlung verwenden.  
  
 Die **get()-Methode** von **IsNull** ist in keiner Weise besonders einfallsreichen Beispiel. Wenn eine ** \@** **Punktvariable** p **Null**ist, wird ** \@p.IsNull** standardmäßig zu "NULL" und nicht zu "1" ausgewertet. Dies liegt daran, dass das **SqlMethod(OnNullCall)-Attribut** der **IsNull get()-Methode** standardmäßig auf false festgelegt ist. Da das Objekt **Null**ist, wenn die Eigenschaft angefordert wird, wird das Objekt nicht deserialisiert, die Methode wird nicht aufgerufen, und der Standardwert "NULL" wird zurückgegeben.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel ist die `is_Null`-Variable privat und enthält für die Instanz des UDT den Status NULL. Im Code muss ein entsprechender Wert für `is_Null` verwaltet werden. Die UDT muss auch über eine statische Eigenschaft mit dem Namen **Null** verfügen, die eine NULL-Wertinstanz der UDT zurückgibt. Dadurch kann der UDT einen NULL-Wert zurückgeben, wenn die Instanz auch in der Datenbank tatsächlich NULL ist.  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a>IS NULL und IsNull  
 Betrachten Sie eine Tabelle, die das Schema Points (id int, Location Point), wobei **Point** eine CLR UDT ist, und die folgenden Abfragen enthält:  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 Beide Abfragen geben die IDs von Punkten mit**Nicht-Null-Positionen** zurück. In Abfrage 1 wird die normale NULL-Behandlung verwendet, und dort ist keine Deserialisierung von UDTs erforderlich. Abfrage 2 hingegen muss jedes**Nicht-Null-Objekt** deserialisieren und die CLR aufrufen, um den Wert der **IsNull-Eigenschaft** abzurufen. Die Verwendung von **IS NULL** wird eindeutig eine bessere Leistung aufweisen, und es sollte niemals einen Grund geben, die **IsNull-Eigenschaft** einer UDT aus [!INCLUDE[tsql](../../includes/tsql-md.md)] Code zu lesen.  
  
 Also, was ist die Verwendung der **IsNull-Eigenschaft?** Zunächst muss ermittelt werden, ob ein Wert **Null** innerhalb des CLR-Codes ist. Zweitens benötigt der Server eine Möglichkeit, zu testen, ob eine Instanz **Null**ist, sodass diese Eigenschaft vom Server verwendet wird. Nachdem es bestimmt, dass es **Null**ist, kann es seine systemeigene NULL-Handling verwenden, um es zu behandeln.  
  
## <a name="implementing-the-parse-method"></a>Implementieren der Parse-Methode  
 Die **Parse-** und **ToString-Methoden** ermöglichen Konvertierungen in und aus Zeichenfolgendarstellungen der UDT. Mit der **Parse-Methode** kann eine Zeichenfolge in eine UDT konvertiert werden. Sie muss als **statisch** (oder **freigegeben** in Visual Basic) deklariert werden und einen Parameter vom Typ **System.Data.SqlTypes.SqlString**annehmen.  
  
 Der folgende Code implementiert die **Parse-Methode** für die Punkt-UDT, die die X- und Y-Koordinaten trennt. **Point** Die **Parse-Methode** hat ein einzelnes Argument vom Typ **System.Data.SqlTypes.SqlString**und geht davon aus, dass X- und Y-Werte als durch Kommas getrennte Zeichenfolge angegeben werden. Durch Festlegen des **Attributs Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall** auf **false** wird verhindert, dass die **Parse-Methode** von einer Nullinstanz von Point aufgerufen wird.  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a>Implementieren der ToString-Methode  
 Die **ToString-Methode** konvertiert die **Point** UDT in einen Zeichenfolgenwert. In diesem Fall wird die Zeichenfolge "NULL" für **Point** eine Nullinstanz des Point-Typs zurückgegeben. Die **ToString-Methode** kehrt die **Parse-Methode** um, indem sie einen **System.Text.StringBuilder** verwendet, um einen durch Kommas getrennten **System.String** zurückzugeben, der aus den X- und Y-Koordinatenwerten besteht. Da **InvokeIfReceiverIsNull** standardmäßig false ist, ist die Überprüfung auf eine NULLinstanz von **Point** nicht erforderlich.  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a>Bereitstellen der UDT-Eigenschaften  
 Die **Point** Punkt-UDT macht X- und Y-Koordinaten verfügbar, die als öffentliche Lese-/Schreibeigenschaften vom Typ **System.Int32**implementiert werden.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a>Überprüfen von UDT-Werten  
 Beim Verarbeiten von UDT-Daten konvertiert [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatisch Binärwerte in UDT-Werte. Im Rahmen dieses Konvertierungsprozesses muss überprüft werden, ob sich die Werte für das Serialisierungsformat des Typs eignen, und sichergestellt werden, dass die Werte ordnungsgemäß deserialisiert werden können. Damit wird sichergestellt, dass der Wert in das binäre Format zurückkonvertiert werden kann. Bei UDTs, deren Sortierreihenfolge eine Bytereihenfolge ist, wird dadurch auch sichergestellt, dass der resultierende Binärwert dem ursprünglichen Binärwert entspricht. So wird verhindert, dass ungültige Werte in der Datenbank persistent gespeichert werden. In einigen Fällen ist diese Art der Überprüfung möglicherweise unzulänglich. Eine zusätzliche Überprüfung kann erforderlich sein, wenn UDT-Werte in einer bestimmten Domäne oder einem Bereich liegen müssen. Ein UDT beispielsweise, der ein Datum implementiert, kann erfordern, dass der Wert für den Tag eine positive Zahl ist, die in einem bestimmten zulässigen Wertebereich liegt.  
  
 Mit der **Microsoft.SqlServer.Server.SqlUserDefinedType.ValidationMethodName-Eigenschaft** der **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** können Sie den Namen einer Validierungsmethode angeben, die der Server ausführt, wenn Daten einer UDT zugewiesen oder in eine UDT konvertiert werden. **ValidationMethodName** wird auch während der Ausführung des bcp-Dienstprogramms, BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE, Distributed Query und TDS (TDS) Remote Prozeduraufruf (RPC) aufgerufen. Der Standardwert für **ValidationMethodName** ist null, was darauf hinweist, dass keine Validierungsmethode vorhanden ist.  
  
### <a name="example"></a>Beispiel  
 Das folgende Codefragment zeigt **Point** die Deklaration für die Point-Klasse, die einen **ValidationMethodName** von **ValidatePoint**angibt.  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 Wenn eine Validierungsmethode angegeben wird, muss diese eine Signatur aufweisen, die etwa folgendem Codefragment entspricht:  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 Die Validierungsmethode kann einen beliebigen Bereich haben und sollte **true** zurückgeben, wenn der Wert gültig ist, und andernfalls **false.** Wenn die Methode **false** zurückgibt oder eine Ausnahme auslöst, wird der Wert als ungültig behandelt, und es wird ein Fehler ausgelöst.  
  
 Im nachstehenden Beispiel lässt der Code für die X- und Y-Koordinaten nur Werte zu, die größer oder gleich Null sind.  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a>Einschränkungen von Validierungsmethoden  
 Der Server ruft die Validierungsmethode auf, wenn er Konvertierungen durchführt, nicht wenn Daten durch das Festlegen einzelner Eigenschaften oder mithilfe der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung INSERT eingefügt werden.  
  
 Sie müssen die Validierungsmethode explizit von Eigenschaftssettern und die **Parse-Methode** aufrufen, wenn die Validierungsmethode in allen Situationen ausgeführt werden soll. Dies ist keine Voraussetzung, und in einigen Fällen ist es möglicherweise nicht einmal wünschenswert.  
  
### <a name="parse-validation-example"></a>Beispiel für die Validierung in der Parse-Methode  
 Um sicherzustellen, dass die **ValidatePoint-Methode** in der **Point-Klasse** aufgerufen wird, müssen Sie sie von der **Parse-Methode** und von den Eigenschaftenprozeduren aufrufen, die die X- und Y-Koordinatenwerte festlegen. Das folgende Codefragment zeigt, **ValidatePoint** wie die ValidatePoint-Validierungsmethode aus der **Parse-Funktion** aufruft.  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a>Beispiel für die Validierung von Eigenschaften  
 Das folgende Codefragment zeigt, **ValidatePoint** wie die ValidatePoint-Validierungsmethode aus den Eigenschaftenprozeduren aufrufen wird, die die X- und Y-Koordinaten festlegen.  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a>Codieren von UDT-Methoden  
 Bei Codieren von UDT-Methoden müssen Sie berücksichtigen, ob sich der verwendete Algorithmus möglicherweise im Lauf der Zeit ändern könnte. Wenn dem so ist, sollten Sie erwägen, eine separate Klasse für die vom UDT verwendeten Methoden zu erstellen. Wenn sich der Algorithmus ändert, können Sie die Klasse mit dem neuen Code erneut kompilieren und die Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] laden, ohne den UDT dadurch zu beeinflussen. In vielen Fälle können UDTs mithilfe der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung ALTER ASSEMBLY erneut geladen werden, dies könnte jedoch potenziell zu Problemen mit vorhandenen Daten führen. Beispielsweise verwendet die in der **AdventureWorks-Beispieldatenbank** enthaltene **Währung** UDT eine **ConvertCurrency-Funktion,** um Währungswerte zu konvertieren, die in einer separaten Klasse implementiert ist. Es ist möglich, dass sich die Konvertierungsalgorithmen in der Zukunft auf unvorhersehbare Weise ändern oder dass eine neue Funktionalität erforderlich wird. Das Trennen der **ConvertCurrency-Funktion** von der **Currency** UDT-Implementierung bietet mehr Flexibilität bei der Planung zukünftiger Änderungen.  
  
### <a name="example"></a>Beispiel  
 Die **Punktklasse** enthält drei einfache Methoden zum Berechnen der Entfernung: **Entfernung**, **Entfernung von** und **EntfernungVon XY**. Jeder gibt eine **doppelte** Berechnung des Abstands von **Punkt** zu Null, den Abstand von einem angegebenen Punkt zu **Punkt**und den Abstand von den angegebenen X- und Y-Koordinaten zu **Punkt**zurück. **Entfernung** und **EntfernungVon** jedem Aufruf **DistanceFromXY**, und zeigen, wie unterschiedliche Argumente für jede Methode verwendet werden.  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a>Verwenden von SqlMethod-Attributen  
 Die **Microsoft.SqlServer.Server.SqlMethodAttribute-Klasse** stellt benutzerdefinierte Attribute bereit, die zum Markieren von Methodendefinitionen verwendet werden können, um Determinismus bei Nullaufrufverhalten anzugeben und anzugeben, ob eine Methode ein Mutator ist. Bei diesen Eigenschaften werden die Standardwerte vorausgesetzt, und das benutzerdefinierte Attribut wird nur verwendet, wenn ein anderer Wert als der Standardwert erforderlich ist.  
  
> [!NOTE]  
>  Die **SqlMethodAttribute-Klasse** erbt von der **SqlFunctionAttribute-Klasse,** sodass **SqlMethodAttribute** die Felder **FillRowMethodName** und **TableDefinition** von **SqlFunctionAttribute**erbt. Dies impliziert, dass es möglich ist, eine Tabellenwertmethode zu schreiben. Dies ist jedoch nicht der Fall. Die Methode kompiliert und die Assembly wird bereitgestellt, aber ein Fehler über den **IEnumerable-Rückgabetyp** wird\<zur Laufzeit mit\<der folgenden Meldung\<ausgelöst: "Methode, Eigenschaft oder Feld 'Name>' in Klasse 'Klasse>' in Assembly 'Assembly>' hat ungültigen Rückgabetyp."  
  
 In der folgenden Tabelle werden einige der relevanten **Microsoft.SqlServer.Server.SqlMethodAttribute-Eigenschaften** beschrieben, die in UDT-Methoden verwendet werden können, und ihre Standardwerte aufgelistet.  
  
 DataAccess  
 Gibt an, ob die Funktion auf die in der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherten Benutzerdaten zugreift. Standard ist **DataAccessKind**. **Keine**.  
  
 IsDeterministic  
 Gibt an, ob die Funktion bei denselben Eingabewerten und demselben Datenbankzustand auch immer dieselben Ausgabewerte erzeugt. Die Standardeinstellung lautet **false**.  
  
 IsMutator  
 Gibt an, ob die Methode eine Statusänderung in der UDT-Instanz verursacht. Die Standardeinstellung lautet **false**.  
  
 IsPrecise  
 Gibt an, ob die Funktion ungenaue Berechnungen beinhaltet, z. B. Gleitkommaoperationen. Die Standardeinstellung lautet **false**.  
  
 OnNullCall  
 Gibt an, ob die Methode aufgerufen wird, wenn als Eingabeargumente NULL-Verweise angegeben werden. Der Standardwert ist **true**.  
  
### <a name="example"></a>Beispiel  
 Mit der **Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator-Eigenschaft** können Sie eine Methode markieren, die eine Änderung des Status einer Instanz einer UDT zulässt. Mit [!INCLUDE[tsql](../../includes/tsql-md.md)] ist es nicht möglich, zwei UDT-Eigenschaften in der SET-Klausel einer UPDATE-Anweisung festzulegen. Sie können jedoch eine Methode als Mutator markieren, die zwei Elemente ändert.  
  
> [!NOTE]  
>  In Abfragen sind Mutatormethoden nicht zulässig. Sie können nur in Zuweisungsanweisungen oder Datenänderungsanweisungen aufgerufen werden. Wenn eine als Mutator markierte Methode nicht **void** zurückgibt (oder kein **Sub** in Visual Basic ist), schlägt CREATE TYPE mit einem Fehler fehl.  
  
 Die folgende Anweisung geht von der Existenz einer **Triangles-UDT** mit einer **Rotate-Methode** aus. Die [!INCLUDE[tsql](../../includes/tsql-md.md)] folgende update-Anweisung ruft die **Rotate-Methode** auf:  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 Die **Rotate-Methode** wird mit der **SqlMethod-Attributeinstellung** **IsMutator** auf **true** versehen, sodass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Methode als Mutatormethode markiert werden kann. Der Code legt **onNullCall** auch auf **false**fest, was dem Server angibt, dass die Methode einen Nullverweis **(Nichts** in Visual Basic) zurückgibt, wenn einer der Eingabeparameter NULL-Referenzen ist.  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a>Implementieren eines UDTs mit einem benutzerdefinierten Format  
 Beim Implementieren einer UDT mit einem benutzerdefinierten Format müssen Sie **Read-** und **Write-Methoden** implementieren, die die Microsoft.SqlServer.Server.IBinarySerialize-Schnittstelle implementieren, um die Serialisierung und Deserialisierung von UDT-Daten zu verarbeiten. Sie müssen auch die **MaxByteSize-Eigenschaft** der **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**angeben.  
  
### <a name="the-currency-udt"></a>Der UDT Currency  
 Die **Währung** UDT ist in den CLR-Beispielen enthalten, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert werden können, beginnend mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
 Die **Währung** UDT unterstützt den Umgang mit Geldbeträgen im Währungssystem einer bestimmten Kultur. Sie müssen zwei Felder definieren: eine **Zeichenfolge** für **CultureInfo**, die angibt, wer die Währung ausgegeben hat (z. B. en-us) und eine **Dezimalzahl** für **CurrencyValue**, den Geldbetrag.  
  
 Obwohl es vom Server nicht für Vergleiche verwendet wird, implementiert die **Currency** UDT die **System.IComparable-Schnittstelle,** die eine einzelne Methode verfügbar macht, **System.IComparable.CompareTo**. Diese Methode wird auf Clientseite in Situationen verwendet, in denen Currency-Werte genau verglichen oder geordnet werden sollen.  
  
 Im Code, der in der CLR ausgeführt wird, wird die Länderangabe getrennt vom Währungswert verglichen. Im [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code bestimmen die folgenden Aktionen den Vergleich:  
  
1.  Legen Sie das **IsByteOrdered-Attribut** auf true fest, das angibt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die persistente binäre Darstellung auf dem Datenträger für Vergleiche zu verwenden.  
  
2.  Verwenden Sie die **Write-Methode** für die **Währung** UDT, um zu bestimmen, wie die [!INCLUDE[tsql](../../includes/tsql-md.md)] UDT auf dem Datenträger beibehalten wird und daher, wie UDT-Werte verglichen und für Vorgänge sortiert werden.  
  
3.  Speichern Sie die **Währung** UDT im folgenden Binärformat:  

    1.  Speichern Sie die Länderangabe als UTF-16-codierte Zeichenfolge für die Bytes 0 bis 19, wobei die Zeichenfolge rechts mit NULL-Zeichen aufgefüllt werden soll.  
  
    2.  Verwenden Sie Bytes 20 und nachfolgende Bytes zum Speichern des Dezimalwerts der Währungsbetrags.  
  
 Durch die Auffüllung wird gewährleistet, dass die Länderangabe vollständig vom Währungsbetrag getrennt ist, sodass beim Vergleich zweier UDT-Werte im [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code jeweils die Bytes mit den Länderangaben und die Bytes mit den Währungsbeträgen miteinander verglichen werden.  
  
 Für die vollständige Codeliste für die **Währung** UDT befolgen Sie die Anweisungen für die Installation der CLR-Beispiele in [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Currency-Attribute  
 Die **Währung** UDT wird mit den folgenden Attributen definiert.  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a>Erstellen von Read- und Write-Methoden mit IBinarySerialize  
 Wenn Sie das UserDefined-Serialisierungsformat auswählen, müssen Sie auch die **IBinarySerialize-Schnittstelle** implementieren und eigene **Lese-** und **Schreibmethoden** erstellen. **UserDefined** Die folgenden Prozeduren aus der **Währung** UDT verwenden die **System.IO.BinaryReader** und **System.IO.BinaryWriter,** um aus der UDT zu lesen und zu schreiben.  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 Die vollständige Codeliste für die **Währung** UDT finden Sie unter [SQL Server Database Engine Samples](https://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
