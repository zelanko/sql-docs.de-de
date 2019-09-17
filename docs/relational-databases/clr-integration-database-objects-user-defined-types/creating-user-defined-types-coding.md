---
title: Codieren von benutzerdefinierten Typen | Microsoft-Dokumentation
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
ms.openlocfilehash: e94662043d3801cc7088533d7f0fbadd638bec5b
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874812"
---
# <a name="creating-user-defined-types---coding"></a>Erstellen benutzerdefinierter Typen: Codieren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Wenn Sie die Definition eines benutzerdefinierten Typs (UDT) schreiben, müssen Sie verschiedene Funktionen implementieren, abhängig davon, ob Sie den UDT als Klasse oder als Struktur implementieren, sowie abhängig von den von Ihnen gewählten Format- und Serialisierungsoptionen.  
  
 Das Beispiel in diesem Abschnitt veranschaulicht die Implementierung eines **Point** -UDT als Struktur **(oder** **Struktur** in Visual Basic). Der **Point** -UDT besteht aus X-und Y-Koordinaten, die als Eigenschaften Prozeduren implementiert werden  
  
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
  
 Der **Microsoft. SqlServer. Server** -Namespace enthält die Objekte, die für verschiedene Attribute des UDT erforderlich sind, und der **System. Data. SqlTypes** -Namespace enthält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Klassen, die System eigene Datentypen darstellen, die für das Stadtverordneten. Es kann natürlich zusätzliche Namespaces geben, die eine Assembly erfordert, um ordnungsgemäß zu funktionieren. Der **Point** -UDT verwendet auch den **System. Text** -Namespace für die Arbeit mit Zeichen folgen.  
  
> [!NOTE]  
>  Visual C++ Database-Objekte, z. b. UDTs, die mit **/clr: pure** kompiliert werden, werden für die Ausführung nicht unterstützt.  
  
## <a name="specifying-attributes"></a>Angeben von Attributen  
 Attribute bestimmen, wie die Serialisierung verwendet wird, um die Speicherdarstellung von UDTs zu erstellen und um UDTs durch Werte an den Client zu übertragen.  
  
 Das **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute-Attribut** ist erforderlich. Das **serialisierbare** Attribut ist optional. Sie können auch das **Microsoft. SqlServer. Server. sqlfaketattribute-Attribut** angeben, um Informationen über den Rückgabetyp eines UDT bereitzustellen. Weitere Informationen finden Sie unter [Benutzerdefinierte Attribute für CLR-Routinen](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md).  
  
### <a name="point-udt-attributes"></a>Attribute des Point-UDT  
 Das **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute-Attribut** legt das Speicherformat für den **Point** -UDT auf ' **native**' fest. **Isbyteguard** ist auf **true**festgelegt. Dadurch wird sichergestellt, dass die Ergebnisse von Vergleichen in SQL Server identisch sind, als wäre derselbe Vergleich in verwaltetem Code erfolgt. Der UDT implementiert die **System. Data. SqlTypes. INullable** -Schnittstelle, damit der UDT NULL-fähig ist.  
  
 Das folgende Code Fragment zeigt die Attribute für den **Point** -UDT.  
  
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
 Zusätzlich zum ordnungsgemäßen Angeben der Attribute für die Assemblys muss der UDT auch die NULL-Zulässigkeit unterstützen. UDTs, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in geladen werden, sind NULL-fähig, aber damit der UDT einen Nullwert erkennt, muss der UDT die **System. Data. SqlTypes. INullable** -Schnittstelle implementieren.  
  
 Sie müssen eine Eigenschaft mit dem Namen **IsNull**erstellen, die benötigt wird, um zu bestimmen, ob ein Wert innerhalb von CLR-Code NULL ist. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine NULL-Instanz eines UDTs findet, wird der UDT mit normalen Behandlungsmethoden für NULL-Werte persistent gespeichert. Der Server vergeudet keine Zeit mit dem Serialisieren oder Deserialisieren des UDTs, wenn dies nicht erforderlich ist, und er verschwendet keinen Platz zum Speichern des NULL-UDTs. Diese Überprüfung auf NULL wird jedes Mal durchgeführt, wenn ein UDT von der CLR übernommen wird. Das heißt, dass mit dem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Konstrukt immer überprüft werden kann, ob UDTs NULL sind. Die **IsNull** -Eigenschaft wird vom Server auch verwendet, um zu testen, ob eine Instanz NULL ist. Sobald der Server bestimmt, dass der UDT NULL ist, kann er seine systemeigene NULL-Behandlung verwenden.  
  
 Die " **get ()** "-Methode von " **IsNull** " ist in keiner Weise sondergeschrieben. Wenn eine **Punkt** Variable  **\@**  **pNULList,wirdp.IsNullstandardmäßigals"Null"ausgewertet,nichtals"1".\@** Dies liegt daran, dass das **SqlMethod (OnNullCall)** -Attribut der **IsNull get ()** -Methode standardmäßig auf false festgelegt ist. Da das-Objekt **null**ist und die-Eigenschaft angefordert wird, wird das Objekt nicht deserialisiert, die Methode wird nicht aufgerufen, und der Standardwert "Null" wird zurückgegeben.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel ist die `is_Null`-Variable privat und enthält für die Instanz des UDT den Status NULL. Im Code muss ein entsprechender Wert für `is_Null` verwaltet werden. Der UDT muss auch über eine statische Eigenschaft namens **null** verfügen, die eine Instanz des UDT mit einem NULL-Wert zurückgibt. Dadurch kann der UDT einen NULL-Wert zurückgeben, wenn die Instanz auch in der Datenbank tatsächlich NULL ist.  
  
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
  
### <a name="is-null-vs-isnull"></a>Ist NULL im Vergleich zu IsNull  
 Angenommen, eine Tabelle enthält die Schema Punkte (ID int, Location Point), wobei **Point** ein CLR-UDT ist, und die folgenden Abfragen:  
  
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
  
 Beide Abfragen geben die IDs von Punkten mit nicht-**null** -Speicherorten zurück. In Abfrage 1 wird die normale NULL-Behandlung verwendet, und dort ist keine Deserialisierung von UDTs erforderlich. Abfrage 2 hingegen muss jedes Objekt, das nicht**null** ist, deserialisieren und die CLR aufzurufen, um den Wert der **IsNull** -Eigenschaft zu erhalten. Die Verwendung von **is NULL** weist eine bessere Leistung auf, und es sollte nie ein Grund sein, die **IsNull** -Eigenschaft eines UDT [!INCLUDE[tsql](../../includes/tsql-md.md)] aus dem Code zu lesen.  
  
 Was ist also die Verwendung der **IsNull** -Eigenschaft? Zuerst muss im CLR-Code bestimmt werden, ob ein Wert **null** ist. Zweitens benötigt der Server eine Möglichkeit, um zu testen, ob eine Instanz **null**ist, sodass diese Eigenschaft vom Server verwendet wird. Nachdem festgelegt wurde, dass es **null**ist, kann es seine systemeigene NULL-Behandlung verwenden, um es zu verarbeiten.  
  
## <a name="implementing-the-parse-method"></a>Implementieren der Parse-Methode  
 Die **Methoden** "Analyse" und "zu **Zeichenfolge** " ermöglichen Konvertierungen in und aus Zeichen folgen Darstellungen des UDT. Mit **der Analyse** Methode kann eine Zeichenfolge in einen UDT konvertiert werden. Er muss als **statisch** deklariert werden (oder in Visual Basic frei **gegeben** werden) und einen Parameter vom Typ **System. Data. SqlTypes. SqlString**annehmen.  
  
 Der folgende Code implementiert die **Analysemethode für** den **Point** -UDT, der die X-und Y-Koordinaten trennt. Die **Parse** -Methode verfügt über ein einzelnes Argument vom Typ **System. Data. SqlTypes. SqlString**und geht davon aus, dass X-und Y-Werte als durch Trennzeichen getrennte Zeichenfolge angegeben werden. Wenn das Attribut **Microsoft. SqlServer. Server. SqlMethodAttribute. onnullcallauf** **false** festgelegt wird, wird verhindert, dass die **Analysemethode von** einer NULL-Instanz aus aufgerufen wird.  
  
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
 Die Methode " **destring** " konvertiert den **Point** -UDT in einen Zeichen folgen Wert. In diesem Fall wird die Zeichenfolge "Null" für eine NULL-Instanz des **Point** -Typs zurückgegeben. Die **ToString** -Methode kehrt die **Analysemethode mithilfe** von **System. Text. StringBuilder** um, um eine durch Kommas getrennte **System. String** zurückzugeben, die aus den X-und Y-Koordinaten Werten besteht. Da **InvokeIfReceiverIsNull** standardmäßig auf false festgelegt ist, ist die Überprüfung auf eine NULL-Instanz des **Punkts** nicht erforderlich.  
  
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
 Der **Point** -UDT macht X-und Y-Koordinaten verfügbar, die als öffentliche Lese-/Schreibeigenschaften vom Typ **System. Int32**implementiert werden.  
  
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
 Beim Verarbeiten von UDT-Daten konvertiert [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] automatisch Binärwerte in UDT-Werte. Im Rahmen dieses Konvertierungsprozesses muss überprüft werden, ob sich die Werte für das Serialisierungsformat des Typs eignen, und sichergestellt werden, dass die Werte ordnungsgemäß deserialisiert werden können. Dadurch wird sichergestellt, dass der Wert wieder in binäre Form konvertiert werden kann. Bei UDTs, deren Sortierreihenfolge eine Bytereihenfolge ist, wird dadurch auch sichergestellt, dass der resultierende Binärwert dem ursprünglichen Binärwert entspricht. So wird verhindert, dass ungültige Werte in der Datenbank persistent gespeichert werden. In einigen Fällen ist diese Art der Überprüfung möglicherweise unzulänglich. Eine zusätzliche Überprüfung kann erforderlich sein, wenn UDT-Werte in einer bestimmten Domäne oder einem Bereich liegen müssen. Ein UDT beispielsweise, der ein Datum implementiert, kann erfordern, dass der Wert für den Tag eine positive Zahl ist, die in einem bestimmten zulässigen Wertebereich liegt.  
  
 Mit der **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute. ValidationMethodName** -Eigenschaft von **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** können Sie den Namen einer Validierungsmethode angeben, die vom Server ausgeführt wird. Wenn Daten einem UDT zugewiesen oder in einen UDT konvertiert werden. **ValidationMethodName** wird auch während der Ausführung des Hilfsprogramms bcp, BULK INSERT, DBCC CHECKDB, DBCC Check File Group, DBCC CHECKTABLE, verteilte Abfrage und Tabular Data Stream (TDS) Remote Prozedur Aufruf (RPC) aufgerufen. Der Standardwert für **ValidationMethodName** ist NULL. Dies deutet darauf hin, dass keine Validierungsmethode vorhanden ist.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Code Fragment wird die Deklaration für die **Point** -Klasse gezeigt, die einen **ValidationMethodName** von **ValidatePoint**angibt.  
  
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
  
 Die Validierungsmethode kann einen beliebigen Bereich aufweisen und sollte **true** zurückgeben, wenn der Wert gültig ist, andernfalls **false** . Wenn die Methode **false** zurückgibt oder eine Ausnahme auslöst, wird der Wert als ungültig behandelt, und es wird ein Fehler ausgelöst.  
  
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
  
 Sie müssen die Validierungsmethode explizit aus den Eigenschaften Settern **und der Analyse** Methode abrufen, wenn Sie die Validierungsmethode in allen Situationen ausführen möchten. Dies ist keine Voraussetzung, und in einigen Fällen ist es möglicherweise nicht einmal wünschenswert.  
  
### <a name="parse-validation-example"></a>Beispiel für die Validierung in der Parse-Methode  
 Um sicherzustellen, dass die **ValidatePoint** -Methode in der **Point** -Klasse aufgerufen wird, müssen Sie Sie aus der **Analysemethode und aus den-** Eigenschaften Prozeduren aufrufen, die die X-und Y-Koordinaten Werte festlegen. Das folgende Code Fragment zeigt, wie die Validierungsmethode **ValidatePoint** von der Analyse **Funktion aufgerufen** wird.  
  
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
 Das folgende Code Fragment zeigt, wie die Validierungsmethode **ValidatePoint** von den Eigenschaften Prozeduren aufgerufen wird, die die X-und Y-Koordinaten festlegen.  
  
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
 Bei Codieren von UDT-Methoden müssen Sie berücksichtigen, ob sich der verwendete Algorithmus möglicherweise im Lauf der Zeit ändern könnte. Wenn dem so ist, sollten Sie erwägen, eine separate Klasse für die vom UDT verwendeten Methoden zu erstellen. Wenn sich der Algorithmus ändert, können Sie die Klasse mit dem neuen Code erneut kompilieren und die Assembly in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] laden, ohne den UDT dadurch zu beeinflussen. In vielen Fälle können UDTs mithilfe der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung ALTER ASSEMBLY erneut geladen werden, dies könnte jedoch potenziell zu Problemen mit vorhandenen Daten führen. Beispielsweise verwendet der **Currency** -UDT, der in der **AdventureWorks** -Beispieldatenbank enthalten ist, eine **ConvertCurrency** -Funktion zum Konvertieren von Währungswerten, die in einer separaten Klasse implementiert sind. Es ist möglich, dass sich die Konvertierungsalgorithmen in der Zukunft auf unvorhersehbare Weise ändern oder dass eine neue Funktionalität erforderlich wird. Das Trennen der **ConvertCurrency** -Funktion von der **Currency** UDT-Implementierung bietet mehr Flexibilität bei der Planung zukünftiger Änderungen.  
  
### <a name="example"></a>Beispiel  
 Die **Point** -Klasse enthält drei einfache Methoden zum Berechnen der Entfernung: **Distance**, **DistanceFrom** und **DistanceFromXY**. Jede gibt einen **Double** -Wert zurück, der den Abstand zwischen **Punkt** und 0 (null), den Abstand von einem angegebenen Punkt zu **Punkt**und den Abstand zwischen den angegebenen X-und Y-Koordinaten und dem **Punkt**berechnet. **Distance** und **DistanceFrom** alle Aufrufe von **DistanceFromXY**und veranschaulichen, wie für jede Methode verschiedene Argumente verwendet werden.  
  
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
 Die **Microsoft. SqlServer. Server. SqlMethodAttribute** -Klasse stellt benutzerdefinierte Attribute bereit, die verwendet werden können, um Methoden Definitionen zu markieren, um Determinismus, das Verhalten von NULL-anrufen anzugeben und anzugeben, ob eine Methode ein Mutator ist. Bei diesen Eigenschaften werden die Standardwerte vorausgesetzt, und das benutzerdefinierte Attribut wird nur verwendet, wenn ein anderer Wert als der Standardwert erforderlich ist.  
  
> [!NOTE]  
>  Die **SqlMethodAttribute** -Klasse erbt von der **SqlFunctionAttribute** -Klasse, sodass **SqlMethodAttribute** die **FillRowMethodName** -und **TableDefinition** -Felder von **SqlFunctionAttribute**erbt. Dies impliziert, dass es möglich ist, eine Tabellenwertmethode zu schreiben. Dies ist jedoch nicht der Fall. Die-Methode wird kompiliert, und die Assembly wird bereitgestellt, aber es wird ein Fehler über den **IEnumerable** -Rückgabetyp zur Laufzeit mit der folgenden Meldung ausgelöst: "Die Methode, die Eigenschaft oder das\<Feld ' Name > ' in\<der Klasse ' class > '\<in der Assembly ' > ' weist einen ungültigen Rückgabetyp auf."  
  
 In der folgenden Tabelle werden einige der relevanten **Microsoft. SqlServer. Server. SqlMethodAttribute** -Eigenschaften beschrieben, die in UDT-Methoden verwendet werden können, und ihre Standardwerte werden aufgelistet.  
  
 DataAccess  
 Gibt an, ob die Funktion auf die in der lokalen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeicherten Benutzerdaten zugreift. Der Standardwert ist **DataAccessKind**. **Keine**.  
  
 IsDeterministic  
 Gibt an, ob die Funktion bei denselben Eingabewerten und demselben Datenbankzustand auch immer dieselben Ausgabewerte erzeugt. Der Standardwert ist **false**.  
  
 IsMutator  
 Gibt an, ob die Methode eine Statusänderung in der UDT-Instanz verursacht. Der Standardwert ist **false**.  
  
 IsPrecise  
 Gibt an, ob die Funktion ungenaue Berechnungen beinhaltet, z. B. Gleitkommaoperationen. Der Standardwert ist **false**.  
  
 OnNullCall  
 Gibt an, ob die Methode aufgerufen wird, wenn als Eingabeargumente NULL-Verweise angegeben werden. Der Standardwert ist **true**.  
  
### <a name="example"></a>Beispiel  
 Mit der **Microsoft. SqlServer. Server. SqlMethodAttribute. IsMutator** -Eigenschaft können Sie eine Methode markieren, die eine Änderung des Zustands einer UDT-Instanz zulässt. Mit [!INCLUDE[tsql](../../includes/tsql-md.md)] ist es nicht möglich, zwei UDT-Eigenschaften in der SET-Klausel einer UPDATE-Anweisung festzulegen. Sie können jedoch eine Methode als Mutator markieren, die zwei Elemente ändert.  
  
> [!NOTE]  
>  In Abfragen sind Mutatormethoden nicht zulässig. Sie können nur in Zuweisungsanweisungen oder Datenänderungsanweisungen aufgerufen werden. Wenn eine Methode, die als Mutator markiert ist, nicht " **void** " zurückgibt (oder keine **Sub** in Visual Basic), schlägt CREATE Type mit einem Fehler fehl.  
  
 Die folgende Anweisung geht davon aus, dass ein **Dreiecke** -UDT vorhanden ist, der über eine **Rotation** -Methode verfügt Die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] Update-Anweisung ruft die **Rotation** -Methode auf:  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 Die **Rotation** -Methode wird mit der **SqlMethod** -Attribut Einstellung **IsMutator** auf **true** ergänzt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , damit die Methode als Mutatormethode markieren kann. Der Code legt auch **onnullcallauf** **false**fest, was dem Server anzeigt, dass die Methode einen NULL-Verweis (**Nothing** in Visual Basic) zurückgibt, wenn einer der Eingabeparameter NULL-Verweise ist.  
  
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
 Beim Implementieren eines UDT mit einem benutzerdefinierten Format müssen Sie **Lese** -und **Schreib** Methoden implementieren, die die Microsoft. SqlServer. Server. IBinarySerialize-Schnittstelle implementieren, um die Serialisierung und Deserialisierung von UDT-Daten zu verarbeiten. Sie müssen auch die **MaxByteSize** -Eigenschaft des **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute-Attributs**angeben.  
  
### <a name="the-currency-udt"></a>Der UDT Currency  
 Der **Currency** -UDT ist in den CLR-Beispielen enthalten, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert werden können [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], beginnend mit.  
  
 Der **Currency** -UDT unterstützt die Behandlung von Geldbeträgen im Währungssystem einer bestimmten Kultur. Sie müssen zwei Felder definieren: eine **Zeichenfolge** für **CultureInfo**, die angibt, wer die Währung ausgestellt hat (z. b. en-US), und ein **Decimal** für "Currency **value**", die Geld Menge.  
  
 Obwohl es nicht vom Server zum Durchführen von Vergleichen verwendet wird, implementiert der **Currency** UDT die **System. ivergleichbare** -Schnittstelle, die eine einzelne Methode ( **System. ivergleichbare. CompareTo**) verfügbar macht. Diese Methode wird auf Clientseite in Situationen verwendet, in denen Currency-Werte genau verglichen oder geordnet werden sollen.  
  
 Im Code, der in der CLR ausgeführt wird, wird die Länderangabe getrennt vom Währungswert verglichen. Im [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code bestimmen die folgenden Aktionen den Vergleich:  
  
1.  Legen Sie das Attribut " **isbyteorder** " auf " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] true" fest, um die persistente binäre Darstellung auf dem Datenträger für Vergleiche zu verwenden.  
  
2.  Verwenden Sie die **Write** -Methode für den **Currency** -UDT, um zu bestimmen, wie der UDT auf dem Datenträger gespeichert wird, und damit [!INCLUDE[tsql](../../includes/tsql-md.md)] , wie UDT-Werte verglichen und für Vorgänge angeordnet werden.  
  
3.  Speichern Sie den **Currency** -UDT in folgendem Binärformat:  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    1.  Speichern Sie die Länderangabe als UTF-16-codierte Zeichenfolge für die Bytes 0 bis 19, wobei die Zeichenfolge rechts mit NULL-Zeichen aufgefüllt werden soll.  
  
    2.  Verwenden Sie Bytes 20 und nachfolgende Bytes zum Speichern des Dezimalwerts der Währungsbetrags.  
  
 Durch die Auffüllung wird gewährleistet, dass die Länderangabe vollständig vom Währungsbetrag getrennt ist, sodass beim Vergleich zweier UDT-Werte im [!INCLUDE[tsql](../../includes/tsql-md.md)]-Code jeweils die Bytes mit den Länderangaben und die Bytes mit den Währungsbeträgen miteinander verglichen werden.  
  
 Die komplette Code Auflistung für den **Currency** -UDT finden Sie in den Anweisungen zum Installieren der CLR-Beispiele in [SQL Server Datenbank-Engine Beispiele](https://msftengprodsamples.codeplex.com/).  
  
### <a name="currency-attributes"></a>Currency-Attribute  
 Der **Currency** -UDT ist mit den folgenden Attributen definiert.  
  
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
 Wenn Sie ein **benutzerdefiniertes** Serialisierungsformat auswählen, müssen Sie auch die **IBinarySerialize** -Schnittstelle implementieren und eigene **Lese** -und **Schreib** Methoden erstellen. Die folgenden Prozeduren aus dem **Currency** UDT verwenden **System. IO. BinaryReader** und **System. IO. BinaryWriter** , um aus dem UDT zu lesen und in diesen zu schreiben.  
  
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
  
 Das komplette Codelisting für den **Currency** -UDT finden Sie unter [SQL Server Datenbank-Engine Beispiele](https://msftengprodsamples.codeplex.com/).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines benutzerdefinierten Typs](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
