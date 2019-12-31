---
title: Codieren von benutzerdefinierten Typen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 7427de92691a2d5c0a92aac55ac16f47dd2ef6b1
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75232241"
---
# <a name="coding-user-defined-types"></a>Programmieren benutzerdefinierter Typen
  Wenn Sie die Definition eines benutzerdefinierten Typs (UDT) schreiben, müssen Sie verschiedene Funktionen implementieren, abhängig davon, ob Sie den UDT als Klasse oder als Struktur implementieren, sowie abhängig von den von Ihnen gewählten Format- und Serialisierungsoptionen.  
  
 Das Codebeispiel in diesem Abschnitt veranschaulicht die Implementierung eines UDT namens `Point` als `struct` (bzw. `Structure` in Visual Basic). Der UDT `Point` besteht aus X- und Y-Koordinaten, die als Eigenschaftenprozeduren implementiert werden.  
  
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
  
 Der `Microsoft.SqlServer.Server`-Namespace enthält die Objekte, die für verschiedene Attribute des UDT erforderlich sind, und der `System.Data.SqlTypes`-Namespace enthält die Klassen, die systemeigenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen, die für die Assembly verfügbar sind. Es kann natürlich zusätzliche Namespaces geben, die eine Assembly erfordert, um ordnungsgemäß zu funktionieren. Der `Point`-UDT verwendet überdies den `System.Text`-Namespace zum Arbeiten mit Zeichenfolgen.  
  
> [!NOTE]  
>  Visual C++-Datenbankobjekte wie UDTs, die mit `/clr:pure` kompiliert wurden, werden nicht für die Ausführung unterstützt.  
  
## <a name="specifying-attributes"></a>Angeben von Attributen  
 Attribute bestimmen, wie die Serialisierung verwendet wird, um die Speicherdarstellung von UDTs zu erstellen und um UDTs durch Werte an den Client zu übertragen.  
  
 
  `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` ist erforderlich. Das `Serializable`-Attribut ist optional. Sie können auch das `Microsoft.SqlServer.Server.SqlFacetAttribute`-Attribut angeben, um Informationen über den Rückgabetyp eines UDTs bereitzustellen. Weitere Informationen finden Sie unter [Benutzerdefinierte Attribute für CLR-Routinen](../clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Attribute des Point-UDT  
 
  `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` legt das Speicherformat für den `Point`-UDT auf `Native` fest. 
  `IsByteOrdered` wird auf `true` festgelegt. Dies garantiert, dass Vergleiche in SQL Server dieselben Ergebnisse liefern wie Vergleiche in verwaltetem Code. Der UDT implementiert die `System.Data.SqlTypes.INullable`-Schnittstelle, damit der UDT NULL erkennt.  
  
 Das folgende Codefragment zeigt die Attribute für den `Point`-UDT.  
  
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
 Zusätzlich zum ordnungsgemäßen Angeben der Attribute für die Assemblys muss der UDT auch die NULL-Zulässigkeit unterstützen. UDTs, die in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladen werden, erkennen Nullwerte, aber damit der UDT einen Nullwert erkennt, muss der UDT die `System.Data.SqlTypes.INullable`-Schnittstelle implementieren.  
  
 Sie müssen eine Eigenschaft namens `IsNull` erstellen, mit der im CLR-Code bestimmt werden kann, ob ein Wert NULL ist. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine NULL-Instanz eines UDTs findet, wird der UDT mit normalen Behandlungsmethoden für NULL-Werte persistent gespeichert. Der Server vergeudet keine Zeit mit dem Serialisieren oder Deserialisieren des UDTs, wenn dies nicht erforderlich ist, und er verschwendet keinen Platz zum Speichern des NULL-UDTs. Diese Überprüfung auf NULL wird jedes Mal durchgeführt, wenn ein UDT von der CLR übernommen wird. Das heißt, dass mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Konstrukt immer überprüft werden kann, ob UDTs NULL sind. Die `IsNull`-Eigenschaft wird auch vom Server verwendet, um zu testen, ob eine Instanz NULL ist. Sobald der Server bestimmt, dass der UDT NULL ist, kann er seine systemeigene NULL-Behandlung verwenden.  
  
 Die `get()`-Methode von `IsNull` stellt in keiner Weise einen Sonderfall dar. Wenn eine `Point`-Variable `@p` gleich `Null` ist, dann ergibt `@p.IsNull` standardmäßig "NULL", nicht "1". Dies ist so, weil das `SqlMethod(OnNullCall)`-Attribut der `IsNull get()`-Methode den Standardwert false hat. Weil das Objekt `Null` ist, wird es nicht deserialisiert, wenn die Eigenschaft angefordert wird, die Methode wird nicht aufgerufen, und der Standardwert "NULL" wird zurückgegeben.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel ist die `is_Null`-Variable privat und enthält für die Instanz des UDT den Status NULL. Im Code muss ein entsprechender Wert für `is_Null` verwaltet werden. Der UDT muss auch über eine statische Eigenschaft namens `Null` verfügen, welche die NULL-Wertinstanz des UDTs zurückgibt. Dadurch kann der UDT einen NULL-Wert zurückgeben, wenn die Instanz auch in der Datenbank tatsächlich NULL ist.  
  
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
 Betrachten Sie eine Tabelle, die das Schema Points(id int, location Point), wobei `Point` ein CLR UDT ist, und die folgenden Abfragen enthält:  
  
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
  
 Beide Abfragen geben die IDs von Punkten mit Positionen ungleich `Null` zurück. In Abfrage 1 wird die normale NULL-Behandlung verwendet, und dort ist keine Deserialisierung von UDTs erforderlich. In Abfrage 2 dagegen muss jedes Objekt, das nicht `Null` ist, deserialisiert und die CLR aufgerufen werden, um den Wert der `IsNull`-Eigenschaft zu erhalten. Der Einsatz von `IS NULL` zeigt eindeutig ein besseres Leistungsverhalten, und es sollte nie notwendig sein, die `IsNull`-Eigenschaft eines UDT über [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code abzurufen.  
  
 Wozu dient also die `IsNull`-Eigenschaft? Erstens wird sie benötigt, damit im CLR-Code bestimmt werden kann, ob ein Wert `Null` ist. Zweitens muss der Server prüfen können, ob eine Instanz `Null` ist, und hierzu wird diese Eigenschaft vom Server verwendet. Sobald der Server bestimmt hat, dass die Instanz UDT `Null` ist, kann er seine systemeigene NULL-Behandlung verwenden.  
  
## <a name="implementing-the-parse-method"></a>Implementieren der Parse-Methode  
 Die `Parse`-Methode und die `ToString`-Methode ermöglichen die Konvertierung des UDT in Zeichenfolgendarstellungen und umgekehrt von Zeichenfolgen in den UDT. Die `Parse`-Methode lässt das Konvertieren einer Zeichenfolge in einen UDT zu. Die Zeichenfolge muss als `static` (oder `Shared` in Visual Basic) deklariert werden und einen Parameter vom Typ `System.Data.SqlTypes.SqlString` verwenden.  
  
 Im folgenden Code wird die `Parse`-Methode für den `Point`-UDT implementiert, welche die X- und Y-Koordinaten einer Instanz einzeln ausgibt. Die `Parse`-Methode verfügt über nur ein Argument des Typs `System.Data.SqlTypes.SqlString` und setzt voraus, dass die X- und Y-Werte in einer durch Komma begrenzten Zeichenfolge übergeben werden. Durch die Festlegung des `Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall`-Attributs auf `false` wird verhindert, dass die `Parse`-Methode für eine NULL-Instanz von Point aufgerufen wird.  
  
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
 Die `ToString`-Methode konvertiert den `Point`-UDT in einen Zeichenfolgenwert. In diesem Fall wird die Zeichenfolge "NULL" für eine NULL-Instanz des `Point`-Typs zurückgegeben. Die `ToString`-Methode kehrt das Ergebnis der `Parse`-Methode mithilfe eines `System.Text.StringBuilder` um und gibt eine durch Kommas begrenzte `System.String`-Instanz zurück, die aus den Koordinatenwerten X und Y besteht. Da **InvokeIfReceiverIsNull** standardmäßig auf false festgelegt ist, `Point` ist die Überprüfung auf eine NULL-Instanz nicht erforderlich.  
  
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
 Der UDT `Point` macht die X- und Y-Koordinaten verfügbar, die als öffentliche Eigenschaften des `System.Int32`-Typs mit Lese-/Schreibzugriff implementiert werden.  
  
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
  
 In der `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName`-Eigenschaft von `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` können Sie den Namen einer Überprüfungsmethode angeben, die der Server ausführt, wenn Daten einem UDT zugewiesen oder in einen UDT konvertiert werden. 
  `ValidationMethodName` wird auch beim Ausführen des bcp-Hilfsprogramms, bei BULK INSERT, DBCC CHECKDB, DBCC CHECKFILEGROUP, DBCC CHECKTABLE und verteilten Abfragen sowie bei TDS-Vorgängen (Tabular Data Stream) und Remoteprozeduraufrufen (Remote Procedure Call, RPC) aufgerufen. Der Standardwert für `ValidationMethodName` lautet NULL, womit angegeben wird, dass keine Validierungsmethode festgelegt ist.  
  
### <a name="example"></a>Beispiel  
 Das folgende Codefragment zeigt die Deklaration für die `Point`-Klasse, die mit `ValidationMethodName` als Validierungsmethode `ValidatePoint` angibt.  
  
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
  
 Die Validierungsmethode kann einen beliebigen Gültigkeitsbereich haben und sollte `true` zurückgeben, wenn der Wert zulässig ist, und andernfalls `false`. Wenn die Methode `false` zurückgibt oder eine Ausnahme auslöst, wird der Wert als nicht zulässig behandelt, und es wird ein Fehler generiert.  
  
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
  
 Sie müssen die Validierungsmethode explizit aus den Eigenschaften Settern und der `Parse` -Methode aufzurufen, wenn Sie die Validierungsmethode in allen Situationen ausführen möchten. Dies ist keine Voraussetzung, und in einigen Fällen ist es möglicherweise nicht einmal wünschenswert.  
  
### <a name="parse-validation-example"></a>Beispiel für die Validierung in der Parse-Methode  
 Um sicherzustellen, `ValidatePoint` dass die-Methode in `Point` der-Klasse aufgerufen wird, müssen Sie `Parse` Sie aus der-Methode und aus den-Eigenschaften Prozeduren aufrufen, die die X-und Y-Koordinaten Werte festlegen. Das folgende Code Fragment zeigt, wie die `ValidatePoint` Validierungsmethode von der `Parse` -Funktion aufgerufen wird.  
  
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
 Das folgende Code Fragment zeigt, wie die `ValidatePoint` Validierungsmethode aus den Eigenschaften Prozeduren aufgerufen wird, die die X-und Y-Koordinaten festlegen.  
  
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
 Bei Codieren von UDT-Methoden müssen Sie berücksichtigen, ob sich der verwendete Algorithmus möglicherweise im Lauf der Zeit ändern könnte. Wenn dem so ist, sollten Sie erwägen, eine separate Klasse für die vom UDT verwendeten Methoden zu erstellen. Wenn sich der Algorithmus ändert, können Sie die Klasse mit dem neuen Code erneut kompilieren und die Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] laden, ohne den UDT dadurch zu beeinflussen. In vielen Fälle können UDTs mithilfe der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung ALTER ASSEMBLY erneut geladen werden, dies könnte jedoch potenziell zu Problemen mit vorhandenen Daten führen. Beispielsweise verwendet der `Currency` UDT, der in der **AdventureWorks** -Beispieldatenbank enthalten ist, eine **ConvertCurrency** -Funktion zum Konvertieren von Währungswerten, die in einer separaten Klasse implementiert sind. Es ist möglich, dass sich die Konvertierungsalgorithmen in der Zukunft auf unvorhersehbare Weise ändern oder dass eine neue Funktionalität erforderlich wird. Das Trennen der **ConvertCurrency** -Funktion `Currency` von der UDT-Implementierung bietet mehr Flexibilität bei der Planung zukünftiger Änderungen.  
  
### <a name="example"></a>Beispiel  
 Die `Point` -Klasse enthält drei einfache Methoden zum Berechnen der Entfernung: **Distance**, **DistanceFrom** und **DistanceFromXY**. Jede dieser Methoden gibt einen Wert vom Typ `double` zurück, wobei die Entfernung von `Point` zum Nullpunkt, die Entfernung von einem angegebenen Punkt zu `Point` und die Entfernung von den angegebenen X- und Y-Koordinaten zu `Point` berechnet wird **Distance** und **DistanceFrom** alle Aufrufe von **DistanceFromXY**und veranschaulichen, wie für jede Methode verschiedene Argumente verwendet werden.  
  
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
 Die `Microsoft.SqlServer.Server.SqlMethodAttribute`-Klasse stellt benutzerdefinierte Attribute zur Verfügung, mit denen Methodendefinitionen markiert werden können, um einen Determinismus anzugeben, das Verhalten beim Aufruf für NULL-Werte festzulegen und anzugeben, ob eine Methode eine Mutatormethode ist. Bei diesen Eigenschaften werden die Standardwerte vorausgesetzt, und das benutzerdefinierte Attribut wird nur verwendet, wenn ein anderer Wert als der Standardwert erforderlich ist.  
  
> [!NOTE]  
>  Die `SqlMethodAttribute`-Klasse erbt von der `SqlFunctionAttribute`-Klasse, daher erbt die `SqlMethodAttribute`-Klasse die Felder `FillRowMethodName` und `TableDefinition` von `SqlFunctionAttribute`. Dies impliziert, dass es möglich ist, eine Tabellenwertmethode zu schreiben. Dies ist jedoch nicht der Fall. Die-Methode wird kompiliert, und die Assembly wird bereitgestellt, aber es `IEnumerable` wird ein Fehler über den Rückgabetyp zur Laufzeit mit der folgenden Meldung ausgelöst: "die\<Methode, die Eigenschaft oder das\<Feld ' Name> ' in\<der Klasse ' class> ' in der Assembly '> ' weist einen ungültigen Rückgabetyp auf."  
  
 In der folgenden Tabelle werden einige der relevanten `Microsoft.SqlServer.Server.SqlMethodAttribute`-Eigenschaften beschrieben, die in UDT-Methoden verwendet werden können, und die zugehörigen Standardwerte aufgeführt.  
  
 DataAccess  
 Gibt an, ob die Funktion auf die in der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherten Benutzerdaten zugreift. Der Standardwert lautet `DataAccessKind``None`.  
  
 IsDeterministic  
 Gibt an, ob die Funktion bei denselben Eingabewerten und demselben Datenbankzustand auch immer dieselben Ausgabewerte erzeugt. Der Standardwert ist `false`.  
  
 IsMutator  
 Gibt an, ob die Methode eine Statusänderung in der UDT-Instanz verursacht. Der Standardwert ist `false`.  
  
 IsPrecise  
 Gibt an, ob die Funktion ungenaue Berechnungen beinhaltet, z. B. Gleitkommaoperationen. Der Standardwert ist `false`.  
  
 OnNullCall  
 Gibt an, ob die Methode aufgerufen wird, wenn als Eingabeargumente NULL-Verweise angegeben werden. Der Standardwert ist `true`.  
  
### <a name="example"></a>Beispiel  
 Mit der `Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator`-Eigenschaft können Sie eine Methode markieren, die eine Änderung des Status einer Instanz eines UDTs gestattet. Mit [!INCLUDE[tsql](../../includes/tsql-md.md)] ist es nicht möglich, zwei UDT-Eigenschaften in der SET-Klausel einer UPDATE-Anweisung festzulegen. Sie können jedoch eine Methode als Mutator markieren, die zwei Elemente ändert.  
  
> [!NOTE]  
>  In Abfragen sind Mutatormethoden nicht zulässig. Sie können nur in Zuweisungsanweisungen oder Datenänderungsanweisungen aufgerufen werden. Wenn eine als Mutatormethode gekennzeichnete Methode nicht `void` zurückgibt (oder kein `Sub` in Visual Basic ist), führt CREATE TYPE zu einem Fehler.  
  
 Die folgende Anweisung setzt die Existenz des UDTs `Triangles` voraus, der über die `Rotate`-Methode verfügt. In der folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung UPDATE wird die `Rotate`-Methode aufgerufen:  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 Die `Rotate`-Methode ist mit dem `SqlMethod`-Attribut ausgezeichnet, mit dem `IsMutator` auf `true` festgelegt wird, sodass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Methode als Mutatormethode markieren kann. Im Code wird zudem `OnNullCall` auf `false` festgelegt. Dem Server wird damit angegeben, dass die Methode einen NULL-Verweis (`Nothing` in Visual Basic) zurückgibt, wenn einer der Eingabeparameter einen NULL-Verweis enthält.  
  
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
 Zur Implementierung eines UDTs mit einem benutzerdefinierten Format müssen Sie die `Read`-Methode und die `Write`-Methode implementieren. Diese Methoden implementieren die Microsoft.SqlServer.Server.IBinarySerialize-Schnittstelle zur Serialisierung und Deserialisierung der UDT-Daten. Sie müssen zudem die `MaxByteSize`-Eigenschaft des `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`-Attributs angeben.  
  
### <a name="the-currency-udt"></a>Der UDT Currency  
 Der UDT `Currency` ist seit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in den CLR-Beispielen enthalten, die zusammen mit [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] installiert werden können.  
  
 Der UDT `Currency` kann Währungsbeträge im Währungssystem eines bestimmten Lands verarbeiten. Sie müssen zwei Felder definieren: ein `string`-Feld für `CultureInfo`, das angibt, welches Land die Währung ausgegeben hat (beispielsweise en-us) und ein `decimal`-Feld für `CurrencyValue`, den Währungsbetrag.  
  
 Obwohl sie vom Server nicht zum Durchführen von Vergleichen verwendet wird, implementiert der UDT `Currency` die `System.IComparable`-Schnittstelle, die nur eine Methode namens `System.IComparable.CompareTo` bereitstellt. Diese Methode wird auf Clientseite in Situationen verwendet, in denen Currency-Werte genau verglichen oder geordnet werden sollen.  
  
 Im Code, der in der CLR ausgeführt wird, wird die Länderangabe getrennt vom Währungswert verglichen. Im [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code bestimmen die folgenden Aktionen den Vergleich:  
  
1.  Legen Sie das `IsByteOrdered`-Attribut auf true fest, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] anzuweisen, die auf dem Datenträger persistent gespeicherte binäre Darstellung für Vergleiche zu verwenden.  
  
2.  Bestimmen Sie mithilfe der `Write`-Methode für den UDT `Currency`, wie der UDT auf dem Datenträger persistent gespeichert wird und wie die UDT-Werte infolgedessen in [!INCLUDE[tsql](../../includes/tsql-md.md)]-Vorgängen verglichen und angeordnet werden.  
  
3.  Speichern Sie den UDT `Currency` im folgenden binären Format:  
  
    1.  Speichern Sie die Länderangabe als UTF-16-codierte Zeichenfolge für die Bytes 0 bis 19, wobei die Zeichenfolge rechts mit NULL-Zeichen aufgefüllt werden soll.  
  
    2.  Verwenden Sie Bytes 20 und nachfolgende Bytes zum Speichern des Dezimalwerts der Währungsbetrags.  
  
 Durch die Auffüllung wird gewährleistet, dass die Länderangabe vollständig vom Währungsbetrag getrennt ist, sodass beim Vergleich zweier UDT-Werte im [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code jeweils die Bytes mit den Länderangaben und die Bytes mit den Währungsbeträgen miteinander verglichen werden.  
  
 Die komplette Code Auflistung für den `Currency` UDT finden Sie in den Anweisungen zum Installieren der CLR-Beispiele in [SQL Server Datenbank-Engine Beispiele](https://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Currency-Attribute  
 Der UDT `Currency` wurde mit den folgenden Attributen definiert.  
  
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
 Wenn Sie das Serialisierungsformat `UserDefined` wählen, müssen Sie auch die `IBinarySerialize`-Schnittstelle implementieren und eigene `Read`- und `Write`-Methoden schreiben. In den folgenden Prozeduren aus dem UDT `Currency` werden `System.IO.BinaryReader` und `System.IO.BinaryWriter` zum Lesen bzw. zum Schreiben von UDT-Werten verwendet.  
  
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
  
 Das komplette Codelisting für den `Currency` UDT finden Sie unter [SQL Server Datenbank-Engine Beispiele](https://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen eines benutzerdefinierten Typs](creating-user-defined-types.md)  
  
