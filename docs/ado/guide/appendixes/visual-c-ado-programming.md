---
description: Visual C++-ADO-Programmierung
title: Visual C++ ADO-Programmierung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO]
ms.assetid: 11233b96-e05c-4221-9aed-5f20944b0f1c
author: rothja
ms.author: jroth
ms.openlocfilehash: ae93db522b465b85feefe85cd94df4be3d29f062
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453952"
---
# <a name="visual-c-ado-programming"></a>Visual C++-ADO-Programmierung
Die ADO-API-Referenz beschreibt die Funktionalität der ADO-API (Application Programming Interface) mithilfe einer Syntax, die dem Microsoft-Visual Basic ähnelt. Obwohl es sich bei der Zielgruppe um alle Benutzer handelt, verwenden ADO-Programmierer verschiedene Sprachen, wie z. b. Visual Basic, Visual C++ (mit und ohne die **#Import** -Direktive) und Visual J++ (mit dem ADO/WFC-Klassen Paket).  

> [!NOTE]
> Microsoft beendete die Unterstützung für Visual J++ in 2004.

 Um dieser Vielfalt Rechnung zu tragen, bietet das [ADO für Visual C++-Syntax Indizes](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) Visual C++ sprachspezifische Syntax mit Links zu allgemeinen Beschreibungen von Funktionen, Parametern, Ausnahme Verhalten usw. in der API-Referenz.  
  
 ADO wird mit COM-Schnittstellen (Component Object Model) implementiert. Programmierer können jedoch einfacher mit com in bestimmten Programmiersprachen arbeiten als andere. Beispielsweise werden fast alle Details der Verwendung von com für Visual Basic Programmierer implizit behandelt, während Visual C++ Programmierer an diesen Details teilnehmen müssen.  
  
 In den folgenden Abschnitten werden Details für C-und C++-Programmierer zusammengefasst, die ADO und die **#Import** -Direktive Er konzentriert sich auf spezifische Datentypen für com (**Variant**, **BSTR**und **SAFEARRAY**) und die Fehlerbehandlung (_com_error).  
  
## <a name="using-the-import-compiler-directive"></a>Verwenden der #Import-Compilerdirektive  
 Die **#Import** Visual C++-Compilerdirektive vereinfacht das Arbeiten mit den ADO-Methoden und-Eigenschaften. Die-Direktive nimmt den Namen einer Datei an, die eine Typbibliothek enthält, wie z. b. ADO. dll (Msado15.dll), und generiert Header Dateien mit typedef-Deklarationen, intelligenten Zeigern für Schnittstellen und Enumerationskonstanten. Jede Schnittstelle ist in einer Klasse gekapselt oder umschließt.  
  
 Für jeden Vorgang innerhalb einer Klasse (d. h. eine Methode oder einen Eigenschafts Befehl) gibt es eine Deklaration, um den Vorgang direkt aufzurufen (d. h. die "RAW"-Form des Vorgangs), und eine Deklaration, um den Rohvorgang aufzurufen und einen com-Fehler auszulösen, wenn der Vorgang nicht erfolgreich ausgeführt werden kann. Wenn es sich bei dem Vorgang um eine Eigenschaft handelt, gibt es normalerweise eine Compilerdirektive, die eine alternative Syntax für den Vorgang erstellt, der Syntax wie Visual Basic hat.  
  
 Vorgänge, die den Wert einer Eigenschaft abrufen, haben Namen der Form " **Get**_Property_". Vorgänge, die den Wert einer Eigenschaft festlegen, haben Namen der Form, **Put**_Eigenschaft_"Put". Vorgänge, die den Wert einer Eigenschaft mit einem Zeiger auf ein ADO-Objekt festlegen, haben Namen der Form **PutRef**-_Eigenschaft_.  
  
 Sie können eine Eigenschaft mit Aufrufen dieser Formulare erhalten oder festlegen:  
  
```cpp
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```
  
## <a name="using-property-directives"></a>Verwenden von Eigenschafts Anweisungen  
 Die **__declspec (Property...)** -Compilerdirektive ist eine Microsoft-spezifische C-Spracherweiterung, die eine Funktion deklariert, die als Eigenschaft verwendet wird, um eine alternative Syntax zu erhalten. Daher können Sie Werte einer Eigenschaft ähnlich wie Visual Basic festlegen oder erhalten. Beispielsweise können Sie eine Eigenschaft wie folgt festlegen und erhalten:  
  
```cpp
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```
  
 Beachten Sie, dass Sie keinen Code ausführen müssen:  
  
```cpp
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```
  
 Der Compiler generiert den entsprechenden **Get** _-_ -, **Put**-oder **PutRef**-_Eigenschafts_ aufzurufen, je nachdem, welche Alternative Syntax deklariert wird und ob die Eigenschaft gelesen oder geschrieben wird.  
  
 Die **__declspec (Property...)** -Compilerdirektive kann nur die **Get**-, **Put**-oder **Get** -und **Put** -alternative Syntax für eine Funktion deklarieren. Schreibgeschützte Vorgänge verfügen nur über eine **Get** -Deklaration. schreibgeschützte Vorgänge verfügen nur über eine **Put** -Deklaration. sowohl Lese-als auch Schreibvorgänge verfügen über **Get** -und **Put** -Deklarationen.  
  
 Mit dieser Direktive sind nur zwei Deklarationen möglich. Allerdings kann jede Eigenschaft über drei Eigenschaften Funktionen verfügen: **Get**-_Eigenschaft_, **Put**-_Eigenschaft_und **PutRef**-_Eigenschaft_. In diesem Fall haben nur zwei Formen der-Eigenschaft die alternative Syntax.  
  
 Beispielsweise wird die **Befehls** Objekt- **ActiveConnection** -Eigenschaft mit einer alternativen Syntax für **Get**_ActiveConnection_ und **PutRef**_ActiveConnection_deklariert. Die **PutRef**-Syntax ist eine gute Wahl, da Sie in der Praxis normalerweise ein offenes **Verbindungs** Objekt (d. h. einen **Verbindungs** Objekt Zeiger) in dieser Eigenschaft platzieren möchten. Das **Recordset** -Objekt hingegen verfügt über **Get**-, **Put**-und **PutRef**_ActiveConnection_ -Vorgänge, aber keine alternative Syntax.  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>Auflistungen, die GetItem-Methode und die Item-Eigenschaft  

 ADO definiert mehrere Auflistungen, einschließlich **Felder**, **Parameter**, **Eigenschaften**und **Fehler**. In Visual C++ gibt die **GetItem (_Index_)** -Methode einen Member der Auflistung zurück. Der *Index* ist eine **Variante**, bei der es sich entweder um einen numerischen Index des Elements in der Auflistung handelt, oder um eine Zeichenfolge, die den Namen des Elements enthält.  
  
 Die **__declspec (Property...)** -Compilerdirektive deklariert die **Item** -Eigenschaft als alternative Syntax für die grundlegende **GetItem ()** -Methode jeder Auflistung. Die alternative Syntax verwendet eckige Klammern und ähnelt einem Array Verweis. Im allgemeinen sehen die beiden Formulare wie folgt aus:  
  
```cpp
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```
  
 Weisen Sie z. b. einem Feld eines **Recordset** -Objekts mit dem Namen **_RS_** einen Wert zu, der aus der Tabelle **Authors** der **Pubs** -Datenbank abgeleitet ist. Verwenden Sie die **Item ()** -Eigenschaft für den Zugriff auf das dritte **Feld** der **Recordset** **-Objektfeld** Auflistung (Auflistungen werden von 0 (null) indiziert. angenommen, das dritte Feld heißt **_au \_ fname_**. Anschließend wird die **value ()** -Methode für das **Field** -Objekt aufgerufen, um einen Zeichen folgen Wert zuzuweisen.  
  
 Dies kann in Visual Basic auf die folgenden vier Arten ausgedrückt werden (die beiden letzten Formen sind für Visual Basic eindeutig; andere Sprachen haben keine Entsprechungen):  
  
```cpp
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```
  
 Die Entsprechung in Visual C++ zu den ersten beiden oben aufgeführten Formularen lautet wie folgt:  
  
```cpp
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```
  
 -oder-(die alternative Syntax für die **value** -Eigenschaft wird ebenfalls angezeigt)  
  
```cpp
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```
  
 Beispiele zum Durchlaufen einer Auflistung finden Sie im Abschnitt "ADO-Auflistungen" in "ADO Reference".  
  
## <a name="com-specific-data-types"></a>COM-spezifische Datentypen  
 Im allgemeinen weist jeder Visual Basic Datentyp, den Sie in der ADO-API-Referenz finden, eine Visual C++ Entsprechung auf. Dazu zählen Standard **Datentypen wie "Ganzzahl ohne Vorzeichen char** " für ein Visual Basic **Byte**, **kurz** für " **Integer**" und " **Long** " für **Long**. In der Syntax indexesto sehen Sie genau, was für die Operanden einer bestimmten Methode oder Eigenschaft erforderlich ist.  
  
 Die Ausnahmen für diese Regel sind die spezifischen Datentypen für com: **Variant**, **BSTR**und **SAFEARRAY**.  
  
### <a name="variant"></a>Variant  
 Ein **Variant** ist ein strukturierter Datentyp, der ein Wertmember und einen Datentyp Member enthält. Eine **Variante** kann eine breite Palette anderer Datentypen enthalten, einschließlich einer anderen Variante, BSTR, Boolean, IDispatch oder IUnknown-Zeiger, Währung, Datum usw. COM stellt auch Methoden bereit, die das Konvertieren eines Datentyps in einen anderen erleichtern.  
  
 Die **_variant_t** -Klasse kapselt und verwaltet den **Variant** -Datentyp.  
  
 Wenn der ADO-API-Verweis besagt, dass eine Methode oder ein Eigenschaften Operand einen Wert annimmt, bedeutet dies in der Regel, dass der Wert in einer **_variant_t**.  
  
 Diese Regel ist explizit true, wenn der **Parameter** Abschnitt in den Themen der ADO-API-Referenz besagt, dass ein Operand eine **Variante**ist. Eine Ausnahme ist, wenn die Dokumentation explizit besagt, dass der Operand einen Standard Datentyp (z. b. **Long** oder **Byte**) oder eine Enumeration annimmt. Eine weitere Ausnahme ist, wenn der Operand eine **Zeichenfolge**annimmt.  
  
### <a name="bstr"></a>BSTR  
 Ein **BSTR** (**B**RSWindowsBasic **Str**) ist ein strukturierter Datentyp, der eine Zeichenfolge und die Länge der Zeichenfolge enthält. COM stellt Methoden zum zuordnen, bearbeiten und Freigeben eines **BSTR**bereit.  
  
 Die **_bstr_t** -Klasse kapselt und verwaltet den **BSTR** -Datentyp.  
  
 Wenn die ADO-API-Referenz besagt, dass eine Methode oder Eigenschaft einen **Zeichen** folgen Wert annimmt, bedeutet dies, dass der Wert in Form einer **_bstr_t**ist.  
  
### <a name="casting-_variant_t-and-_bstr_t-classes"></a>Umwandeln von _variant_t-und _bstr_t Klassen  
 Häufig ist es nicht notwendig, eine **_variant_t** oder **_bstr_t** in einem Argument für einen Vorgang explizit zu codieren. Wenn die **_variant_t** oder **_bstr_t** Klasse über einen Konstruktor verfügt, der mit dem Datentyp des Arguments übereinstimmt, generiert der Compiler die entsprechende **_variant_t** oder **_bstr_t**.  
  
 Wenn das Argument jedoch mehrdeutig ist, d. h., dass der Datentyp des Arguments mit mehr als einem Konstruktor übereinstimmt, müssen Sie das Argument mit dem entsprechenden Datentyp umwandeln, um den korrekten Konstruktor aufzurufen.  
  
 Beispielsweise lautet die Deklaration für die **Recordset:: Open** -Methode wie folgt:  
  
```cpp
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```
  
 Das- `ActiveConnection` Argument nimmt einen Verweis auf einen **_variant_t**an, den Sie als Verbindungs Zeichenfolge oder als Zeiger auf ein geöffnetes **Verbindungs** Objekt codieren können.  
  
 Die richtige **_variant_t** wird implizit erstellt, wenn Sie eine Zeichenfolge wie z `DSN=pubs;uid=MyUserName;pwd=MyPassword;` . b. "" oder einen Zeiger wie " `(IDispatch *) pConn` " übergeben.  
  
> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.  
  
 Oder Sie können eine **_variant_t** mit einem Zeiger wie "" explizit codieren `_variant_t((IDispatch *) pConn, true)` . Die Umwandlung `(IDispatch *)` löst die Mehrdeutigkeit mit einem anderen Konstruktor auf, der einen Zeiger auf eine IUnknown-Schnittstelle annimmt.  
  
 Es ist eine entscheidende, aber selten erwähnte Tatsache, dass ADO eine IDispatch-Schnittstelle ist. Wenn ein Zeiger auf ein ADO-Objekt als **Variant**weitergegeben werden muss, muss dieser Zeiger als Zeiger auf eine IDispatch-Schnittstelle umgewandelt werden.  
  
 Im letzten Fall wird das zweite boolesche Argument des Konstruktors explizit mit dem optionalen Standardwert von codiert `true` . Dieses Argument bewirkt, dass der **Variant** -Konstruktor seine **adressf**()-Methode aufruft, die die **_variant_t:: Release**()-Methode automatisch aufruft, wenn die ADO-Methode oder der Eigenschafts Aufruf abgeschlossen wird.  
  
### <a name="safearray"></a>SafeArray  
 Ein **SAFEARRAY** ist ein strukturierter Datentyp, der ein Array anderer Datentypen enthält. Ein **SAFEARRAY** wird als *sicher* bezeichnet, da es Informationen über die Begrenzungen der einzelnen Array Dimensionen enthält und den Zugriff auf Array Elemente innerhalb dieser Begrenzungen einschränkt.  
  
 Wenn der ADO-API-Verweis besagt, dass eine Methode oder eine Eigenschaft ein Array annimmt oder zurückgibt, bedeutet dies, dass die Methode oder Eigenschaft ein **SAFEARRAY**annimmt oder zurückgibt, kein natives C/C++-Array.  
  
 Beispielsweise erfordert der zweite Parameter der **OpenSchema** -Methode des **Connection** -Objekts ein Array von **Variant** -Werten. Diese **Variant** -Werte müssen als Elemente eines **SAFEARRAY**übergeben werden, und das **SAFEARRAY** muss als Wert einer anderen **Variante**festgelegt werden. Dabei handelt es sich um eine andere **Variante** , die als zweites Argument von **OpenSchema**übermittelt wird.  
  
 Als weiteres Beispiel ist das erste Argument der **Find** -Methode eine **Variante** , deren Wert ein eindimensionales **SAFEARRAY**ist. jedes optionale erste und zweite Argument von **AddNew** ist ein eindimensionales **SAFEARRAY**. und der Rückgabewert der **GetRows** -Methode ist eine **Variante** , deren Wert ein zweidimensionales **SAFEARRAY**ist.  
  
## <a name="missing-and-default-parameters"></a>Fehlende und Standardparameter  
 Visual Basic lässt fehlende Parameter in Methoden zu. Beispielsweise verfügt die **Open** -Methode des **Recordset** -Objekts über fünf Parameter, aber Sie können zwischen Parameter überspringen und nachfolgende Parameter weglassen. Ein standardmäßiger **BSTR** oder **Variant** wird abhängig vom Datentyp des fehlenden Operanden ersetzt.  
  
 In C/C++ müssen alle Operanden angegeben werden. Wenn Sie einen fehlenden Parameter angeben möchten, dessen Datentyp eine Zeichenfolge ist, geben Sie einen **_bstr_t** an, der eine NULL-Zeichenfolge enthält. Wenn Sie einen fehlenden Parameter angeben möchten, dessen Datentyp eine **Variante**ist, geben Sie eine **_variant_t** mit dem Wert DISP_E_PARAMNOTFOUND und einem VT_ERROR Typ an. Alternativ dazu können Sie auch die entsprechende **_variant_t** Konstante ( **vtMissing**) angeben, die von der **#Import** -Direktive bereitgestellt wird.  
  
 Drei Methoden sind Ausnahmen für die typische Verwendung von **vtMissing**. Dabei handelt es sich um die **Execute** -Methoden der **Connection** -und **Command** -Objekte und die **NextRecordset** -Methode des **Recordset** -Objekts. Im folgenden finden Sie die folgenden Signaturen:  
  
```cpp
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```
  
 Die Parameter " *recordsaffzierte* " und " *Parameters*" sind Zeiger auf eine **Variante**. *Parameter* ist ein Eingabeparameter, der die Adresse einer **Variante** angibt, die einen einzelnen Parameter oder ein Array von Parametern enthält, die den ausgeführten Befehl ändern. *Recordsafffiziert* ist ein Ausgabeparameter, der die Adresse einer **Variante**angibt, bei der die Anzahl der von der Methode betroffenen Zeilen zurückgegeben wird.  
  
 Geben Sie in der **Execute** -Methode des **Command** -Objekts an, dass keine Parameter angegeben werden, indem Sie *Parameter* entweder auf `&vtMissing` (empfohlen) oder auf den NULL-Zeiger festlegen (d. h. **null** oder NULL (0)). Wenn *Parameters* auf den NULL-Zeiger festgelegt ist, ersetzt die Methode intern das Äquivalent von **vtMissing**und schließt dann den Vorgang ab.  
  
 Geben Sie in allen Methoden an, dass die Anzahl der betroffenen Datensätze nicht durch Festlegen von *recordsafffür* den NULL-Zeiger zurückgegeben werden soll. In diesem Fall ist der NULL-Zeiger nicht so viel ein fehlender Parameter als Anzeichen dafür, dass die-Methode die Anzahl der betroffenen Datensätze verwerfen sollte.  
  
 Daher ist es für diese drei Methoden gültig, etwas wie zu programmieren:  
  
```cpp
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```
  
## <a name="error-handling"></a>Fehlerbehandlung  
 In com geben die meisten Vorgänge einen HRESULT-Rückgabecode zurück, der angibt, ob eine Funktion erfolgreich abgeschlossen wurde. Die **#Import** -Direktive generiert Wrapper Code um jede "RAW"-Methode oder-Eigenschaft und überprüft das zurückgegebene HRESULT. Wenn HRESULT einen Fehler anzeigt, löst der Wrapper Code einen com-Fehler aus, indem _com_issue_errorex () mit dem HRESULT-Rückgabecode als Argument aufgerufen wird. COM-Fehler Objekte können in einem **try**- - **catch** -Block abgefangen werden. (Aus Effizienzgründen sollten Sie einen Verweis auf ein **_com_error** Objekt abfangen.)  
  
 Beachten Sie, dass es sich hierbei um ADO-Fehler handelt: Sie ergeben einen Fehler beim ADO-Vorgang. Fehler, die vom zugrunde liegenden Anbieter zurückgegeben werden, werden in der Auflistung der **Verbindungs** Objekt **Fehler** als **Fehler** Objekte angezeigt.  
  
 Die **#Import** -Direktive erstellt nur Fehlerbehandlungsroutinen für Methoden und Eigenschaften, die in der ADO. dll deklariert werden. Allerdings können Sie denselben Mechanismus zur Fehlerbehandlung nutzen, indem Sie ein eigenes Fehler Überprüfungs Makro oder eine Inline Funktion schreiben. Beispiele finden Sie im Thema [Visual C++ Erweiterungen](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md)oder im Code in den folgenden Abschnitten.  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Visual C++ Entsprechungen von Visual Basic Konventionen  
 Im folgenden finden Sie eine Zusammenfassung der verschiedenen Konventionen in der ADO-Dokumentation, die in Visual Basic programmiert sind, sowie deren Entsprechungen in Visual C++.  
  
### <a name="declaring-an-ado-object"></a>Deklarieren eines ADO-Objekts  
 In Visual Basic wird eine ADO-Objekt Variable (in diesem Fall für ein **Recordset** -Objekt) wie folgt deklariert:  
  
```vb
Dim rst As ADODB.Recordset  
```
  
 Die-Klausel `ADODB.Recordset` ist die ProgID des **Recordset** -Objekts, wie in der Registrierung definiert. Eine neue Instanz eines **Datensatz** -Objekts wird wie folgt deklariert:  
  
```vb
Dim rst As New ADODB.Recordset  
```
  
 - oder -  
  
```vb
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```
  
 In Visual C++ generiert die **#Import** -Direktive intelligente Zeigertyp Deklarationen für alle ADO-Objekte. Beispielsweise ist eine Variable, die auf ein **_Recordset** Objekt verweist, vom Typ **_RecordsetPtr**und wird wie folgt deklariert:  
  
```cpp
_RecordsetPtr  rs;  
```
  
 Eine Variable, die auf eine neue Instanz eines **_Recordset** Objekts zeigt, wird wie folgt deklariert:  
  
```cpp
_RecordsetPtr  rs("ADODB.Recordset");  
```
  
 - oder -  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance("ADODB.Recordset");  
```
  
 - oder -  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance(__uuidof(_Recordset));  
```
  
 Nachdem die **Methode "** -Methode" aufgerufen wurde, kann die Variable wie folgt verwendet werden:  
  
```cpp
rs->Open(...);  
```
  
 Beachten Sie, dass in einem Fall der `.` Operator "" verwendet wird, als ob die Variable eine Instanz einer Klasse ( `rs.CreateInstance` ) wäre, und in einem anderen Fall `->` wird der Operator "" verwendet, als ob die Variable ein Zeiger auf eine Schnittstelle ( `rs->Open` ) wäre.  
  
 Eine Variable kann auf zwei Arten verwendet werden, da der `->` Operator "" überladen ist, um zuzulassen, dass eine Instanz einer Klasse sich wie ein Zeiger auf eine Schnittstelle verhält. Ein privates Klassenmember der Instanzvariablen enthält einen Zeiger auf die **_Recordset** -Schnittstelle. der `->` Operator "" gibt diesen Zeiger zurück, und der zurückgegebene Zeiger greift auf die Member des **_Recordset** Objekts zu.  
  
### <a name="coding-a-missing-parameter---string"></a>Codieren einer fehlenden Parameter Zeichenfolge  
 Wenn Sie einen fehlenden **Zeichen** folgen Operanden in Visual Basic codieren müssen, lassen Sie lediglich den Operanden aus. Sie müssen den Operanden in Visual C++ angeben. Codieren einer **_bstr_t** , die eine leere Zeichenfolge als Wert aufweist.  
  
```cpp
_bstr_t strMissing(L"");  
```
  
### <a name="coding-a-missing-parameter---variant"></a>Codieren eines fehlenden Parameter-Variant  
 Wenn Sie einen fehlenden **Variant** -Operanden in Visual Basic codieren müssen, lassen Sie lediglich den Operanden aus. Sie müssen alle Operanden in Visual C++ angeben. Codieren Sie einen fehlenden **Variant** -Parameter, bei dem ein **_variant_t** auf den speziellen Wert, DISP_E_PARAMNOTFOUND und Typ, VT_ERROR festgelegt ist. Alternativ können Sie **vtMissing**angeben. dabei handelt es sich um eine äquivalente, von der **#Import** -Direktive angegebene vordefinierte Konstante  
  
```cpp
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```
  
 oder verwenden Sie-  
  
```cpp
...vtMissing...;  
```
  
### <a name="declaring-a-variant"></a>Deklarieren einer Variante  
 In Visual Basic wird eine **Variante** mit der **Dim** -Anweisung wie folgt deklariert:  
  
```vb
Dim VariableName As Variant  
```
  
 Deklarieren Sie in Visual C++ eine Variable als Typ **_variant_t**. Unten sind einige Schemas **_variant_t** Deklarationen aufgeführt.  
  
> [!NOTE]
>  Diese Deklarationen haben lediglich einen groben Überblick über das, was Sie in Ihrem eigenen Programm Programmieren würden. Weitere Informationen finden Sie in den Beispielen unten und in der Visual C + +-Dokumentation.  
  
```cpp
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```
  
### <a name="using-arrays-of-variants"></a>Verwenden von Arrays von Varianten  
 In Visual Basic können Arrays von **Varianten** mit der **Dim** -Anweisung codiert werden, oder Sie können die **Array** -Funktion verwenden, wie im folgenden Beispielcode gezeigt:  
  
```vb
Public Sub ArrayOfVariants  
Dim cn As ADODB.Connection  
Dim rs As ADODB.Recordset  
Dim fld As ADODB.Field  
  
    cn.Open "DSN=pubs"  
    rs = cn.OpenSchema(adSchemaColumns, _  
        Array(Empty, Empty, "authors", Empty))  
    For Each fld in rs.Fields  
        Debug.Print "Name = "; fld.Name  
    Next fld  
    rs.Close  
    cn.Close  
End Sub  
```
  
 Im folgenden Visual C++ Beispiel wird die Verwendung eines **SAFEARRAY** veranschaulicht, das mit einem **_variant_t**verwendet wird.  
  
#### <a name="notes"></a>Notizen  
 Die folgenden Hinweise entsprechen den kommentierten Abschnitten im Codebeispiel.  
  
1.  Auch hier ist die Funktion "testhr () Inline" definiert, um den vorhandenen Mechanismus zur Fehlerbehandlung zu nutzen.  
  
2.  Sie benötigen nur ein eindimensionales Array, sodass Sie **safearraykreatevector**anstelle der allgemeinen **SAFEARRAYBOUND** -Deklaration und der **SafeArrayCreate** -Funktion verwenden können. Im folgenden sehen Sie, wie der Code mit **SafeArrayCreate**aussehen würde:  
  
    ```cpp
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```
  
3.  Das Schema, das durch die Enumerationskonstante, **adSchemaColumns**, identifiziert wird, ist vier Einschränkungs Spalten zugeordnet: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME und column_name. Daher wird ein Array von **Variant** -Werten mit vier Elementen erstellt. Anschließend wird ein Einschränkungs Wert angegeben, der der dritten Spalte (table_name) entspricht.  
  
     Das **Recordset** , das zurückgegeben wird, besteht aus mehreren Spalten, bei denen es sich um eine Teilmenge der Einschränkungs Spalten handelt. Die Werte der Einschränkungs Spalten für jede zurückgegebene Zeile müssen mit den entsprechenden Einschränkungs Werten übereinstimmen.  
  
4.  Diejenigen, die mit **SAFEARRAYs** vertraut sind, sind möglicherweise überrascht, dass **SafeArrayDestroy**() nicht vor dem Beenden aufgerufen wird. Tatsächlich führt das Aufrufen von **SafeArrayDestroy**() in diesem Fall zu einer Lauf Zeit Ausnahme. Der Grund hierfür ist, dass der Dekonstruktor für `vtCriteria` **VariantClear**() aufruft, wenn das **_variant_t** den Gültigkeitsbereich verlässt, wodurch das **SAFEARRAY**freigegeben wird. Wenn Sie **SafeArrayDestroy**aufrufen, ohne die **_variant_t**manuell zu löschen, würde der Dekonstruktor versuchen, einen ungültigen **SAFEARRAY** -Zeiger zu löschen.  
  
     Wenn **SafeArrayDestroy** aufgerufen wurde, sieht der Code wie folgt aus:  
  
    ```cpp
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```
  
     Es ist jedoch viel einfacher, die **_variant_t** die Verwaltung von **SAFEARRAY**zuzulassen.  
  
```cpp
// Visual_CPP_ADO_Prog_1.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Note 1  
inline void TESTHR( HRESULT _hr ) {   
   if FAILED(_hr)   
      _com_issue_error(_hr);   
}  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _RecordsetPtr pRs("ADODB.Recordset");  
      _ConnectionPtr pCn("ADODB.Connection");  
      _variant_t vtTableName("authors"), vtCriteria;  
      long ix[1];  
      SAFEARRAY *pSa = NULL;  
  
      pCn->Provider = "sqloledb";  
      pCn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
      // Note 2, Note 3  
      pSa = SafeArrayCreateVector(VT_VARIANT, 1, 4);  
      if (!pSa)   
         _com_issue_error(E_OUTOFMEMORY);  
  
      // Specify TABLE_NAME in the third array element (index of 2).   
      ix[0] = 2;        
      TESTHR(SafeArrayPutElement(pSa, ix, &vtTableName));  
  
      // There is no Variant constructor for a SafeArray, so manually set the   
      // type (SafeArray of Variant) and value (pointer to a SafeArray).  
  
      vtCriteria.vt = VT_ARRAY | VT_VARIANT;  
      vtCriteria.parray = pSa;  
  
      pRs = pCn->OpenSchema(adSchemaColumns, vtCriteria, vtMissing);  
  
      long limit = pRs->GetFields()->Count;  
      for ( long x = 0 ; x < limit ; x++ )  
         printf( "%d: %s\n", x + 1, ((char*) pRs->GetFields()->Item[x]->Name) );  
      // Note 4  
      pRs->Close();  
      pCn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Error:\n");  
      printf("Code = %08lx\n", e.Error());  
      printf("Code meaning = %s\n", (char*) e.ErrorMessage());  
      printf("Source = %s\n", (char*) e.Source());  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   CoUninitialize();  
}  
```
  
### <a name="using-property-getputputref"></a>Verwenden der Get/Put/PutRef-Eigenschaft  
 In Visual Basic wird der Name einer Eigenschaft nicht durch das Abrufen, zuweisen oder Zuweisen eines Verweises qualifiziert.  
  
```vb
Public Sub GetPutPutRef  
Dim rs As New ADODB.Recordset  
Dim cn As New ADODB.Connection  
Dim sz as Integer  
cn.Open "Provider=sqloledb;Data Source=yourserver;" & _  
         "Initial Catalog=pubs;Integrated Security=SSPI;"  
rs.PageSize = 10  
sz = rs.PageSize  
rs.ActiveConnection = cn  
rs.Open "authors",,adOpenStatic  
' ...  
rs.Close  
cn.Close  
End Sub  
```
  
 In diesem Visual C++ Beispiel wird die **Get** / **Put** / **PutRef**-_Eigenschaft_veranschaulicht.  
  
#### <a name="notes"></a>Notizen  
 Die folgenden Hinweise entsprechen den kommentierten Abschnitten im Codebeispiel.  
  
1.  In diesem Beispiel werden zwei Formen eines fehlenden Zeichen folgen Arguments verwendet: eine explizite Konstante, ein **Strauch**und eine Zeichenfolge, mit der der Compiler eine temporäre **_bstr_t** erstellt, die für den Bereich der **Open** -Methode vorhanden ist.  
  
2.  Es ist nicht erforderlich, den Operanden von `rs->PutRefActiveConnection(cn)` in umzuwandeln, `(IDispatch *)` da der Typ des Operanden bereits ist `(IDispatch *)` .  
  
```cpp
// Visual_CPP_ado_prog_2.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _bstr_t strMissing(L"");  
      long oldPgSz = 0, newPgSz = 5;  
  
      // Note 1  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", strMissing, "", adConnectUnspecified);  
  
      oldPgSz = rs->GetPageSize();  
      // -or-  
      // oldPgSz = rs->PageSize;  
  
      rs->PutPageSize(newPgSz);  
      // -or-  
      // rs->PageSize = newPgSz;  
  
      // Note 2  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockReadOnly, adCmdTable);  
      printf("Original pagesize = %d, new pagesize = %d\n", oldPgSz, rs->GetPageSize());  
      rs->Close();  
      cn->Close();  
  
   }  
   catch (_com_error &e) {  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```
  
### <a name="using-getitemx-and-itemx"></a>Verwenden von GetItem (x) und Element [x]  
 In diesem Visual Basic Beispiel wird die standardmäßige und alternative Syntax für **Item**() veranschaulicht.  
  
```vb
Public Sub GetItemItem  
Dim rs As New ADODB.Recordset  
Dim name as String  
rs = rs.Open "authors", "DSN=pubs;", adOpenDynamic, _  
         adLockBatchOptimistic, adTable  
name = rs(0)  
' -or-  
name = rs.Fields.Item(0)  
rs(0) = "Test"  
rs.UpdateBatch  
' Restore name  
rs(0) = name  
rs.UpdateBatch  
rs.Close  
End Sub  
```
  
 In diesem Visual C++ Beispiel wird das- **Element**veranschaulicht.  
  
> [!NOTE]
>  Der folgende Hinweis entspricht den kommentierten Abschnitten im Codebeispiel: beim Zugriff auf die Auflistung mit dem **Element**muss der Index **2**in **Long** umgewandelt werden, damit ein entsprechender Konstruktor aufgerufen wird.  
  
```cpp
// Visual_CPP_ado_prog_3.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
void main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _variant_t vtFirstName;  
  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", "", "", adConnectUnspecified);  
  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockOptimistic, adCmdTable);  
      rs->MoveFirst();  
  
      // Note 1. Get a field.  
      vtFirstName = rs->Fields->GetItem((long)2)->GetValue();  
      // -or-  
      vtFirstName = rs->Fields->Item[(long)2]->Value;  
  
      printf( "First name = '%s'\n", (char*)( (_bstr_t)vtFirstName) );  
  
      rs->Fields->GetItem((long)2)->Value = L"TEST";  
      rs->Update(vtMissing, vtMissing);  
  
      // Restore name  
      rs->Fields->GetItem((long)2)->PutValue(vtFirstName);  
      // -or-  
      rs->Fields->GetItem((long)2)->Value = vtFirstName;  
      rs->Update(vtMissing, vtMissing);  
      rs->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>Umwandeln von ADO-Objekt Zeigern mit (IDispatch *)  
 Im folgenden Visual C++ Beispiel wird die Verwendung von (IDispatch *) zum Umwandeln von ADO-Objekt Zeigern veranschaulicht.  
  
#### <a name="notes"></a>Notizen  
 Die folgenden Hinweise entsprechen den kommentierten Abschnitten im Codebeispiel.  
  
1.  Geben Sie in einem explizit codierten **Variant**ein offenes **Verbindungs** Objekt an. Wandeln Sie es mit (IDispatch \* ) um, damit der richtige Konstruktor aufgerufen wird. Legen Sie außerdem den zweiten **_variant_t** -Parameter explizit auf den Standardwert **true**fest, sodass der Objekt Verweis Zähler richtig ist, wenn der **Recordset:: Open** -Vorgang beendet wird.  
  
2.  Der Ausdruck, `(_bstr_t)` , ist keine Umwandlung, sondern ein **_variant_t** Operator, der eine **_bstr_t** Zeichenfolge aus der als **Wert**zurückgegebenen **Variante** extrahiert.  
  
 Der Ausdruck, `(char*)` , ist keine Umwandlung, sondern ein **_bstr_t** Operator, der einen Zeiger auf die gekapselte Zeichenfolge in einem **_bstr_t** -Objekt extrahiert.  
  
 In diesem Code Abschnitt werden einige der nützlichen Verhalten von **_variant_t** und **_bstr_t** Operatoren veranschaulicht.  
  
```cpp
// Visual_CPP_ado_prog_4.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr pConn("ADODB.Connection");  
      _RecordsetPtr pRst("ADODB.Recordset");  
  
      pConn->Provider = "sqloledb";  
      pConn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
  
      // Note 1.  
      pRst->Open("authors", _variant_t((IDispatch *) pConn, true), adOpenStatic, adLockReadOnly, adCmdTable);  
      pRst->MoveLast();  
  
      // Note 2.  
      printf("Last name is '%s %s'\n",   
         (char*) ((_bstr_t) pRst->GetFields()->GetItem("au_fname")->GetValue()),  
         (char*) ((_bstr_t) pRst->Fields->Item["au_lname"]->Value));  
  
      pRst->Close();  
      pConn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }     
   ::CoUninitialize();  
}  
```
