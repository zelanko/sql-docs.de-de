---
title: Visual C++-ADO-Programmierung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c8145b4000a621ecb09abff074e4b5e06aea7c80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702621"
---
# <a name="visual-c-ado-programming"></a>Visual C++-ADO-Programmierung
Die ADO-API-Referenz beschreibt die Funktionalität von der ADO-Anwendungsprogrammierschnittstelle (API) mithilfe einer Syntax ähnlich wie auf Microsoft Visual Basic. Obwohl alle Benutzer, die Zielgruppe ist ADO Programmierern verschiedene Sprachen wie Visual Basic, Visual C++ (mit und ohne die **#import** Richtlinie), und Visual J++ (mit dem Paket für den ADO/WFC-Klasse).  

> [!NOTE]
> Microsoft Support für Visual J++ 2004 endete.

 Um diese Vielfalt, die zu berücksichtigen die [ADO für Visual C++ – Syntaxindizes](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) bieten sprachspezifische Visual C++-Syntax mit Links zu allgemeinen Beschreibungen der Funktionen, Parameter, außergewöhnliche Verhalten und So weiter, in der API Verweis.  
  
 ADO wird mit COM (Component Object Model)-Schnittstellen implementiert. Allerdings ist es einfacher für Programmierer, die Arbeit mit COM in einer bestimmten Programmiersprache als andere. Beispielsweise werden nahezu alle Details der Verwendung von COM implizit für Visual Basic-Programmierer behandelt, während Visual C++-Programmierer zu diesen Details selbst kümmern müssen.  
  
 In den folgenden Abschnitten zusammenfassen von Informationen für C- und C++-Programmierer, die mithilfe von ADO und **#import** Richtlinie. Der Schwerpunkt liegt auf Datentypen, die spezifisch für COM (**Variant**, **BSTR**, und **SafeArray**), und der Fehlerbehandlung (_com_error).  
  
## <a name="using-the-import-compiler-directive"></a>Verwenden der #import-Compiler-Anweisung  
 Die **#import** Visual C++-Compiler-Anweisung vereinfacht die Verwendung mit dem ADO-Methoden und Eigenschaften. Die Direktive nimmt den Namen einer Datei mit einer Typbibliothek, wie z. B. die ADO-DLL-Datei ("MSADO15.dll"), und Headerdateien, typedef-Deklarationen und intelligente Zeiger für Schnittstellen und Enumerationskonstanten enthält, generiert. Jede Schnittstelle ist gekapselt, oder in einer Klasse umschlossen.  
  
 Für jeden Vorgang innerhalb einer Klasse (d. h. eine Methode oder Eigenschaft aufrufen) besteht eine Deklaration, um den Vorgang direkt (d. h. das "unformatiert" Form des Vorgangs) aufzurufen und eine Deklaration, um den unformatierten Vorgang aufrufen und einen COM-Fehler ausgelöst, wenn der Vorgang fehlschlägt, Succ ausgeführt essfully. Wenn der Vorgang eine Eigenschaft ist, besteht in der Regel eine Compiler-Anweisung, die eine alternative Syntax für den Vorgang erstellt, deren Syntax wie Visual Basic.  
  
 Vorgänge, die den Wert einer Eigenschaft abzurufen haben Namen im Format **erhalten**_Eigenschaft_. Vorgänge, die der Wert einer Eigenschaft festgelegt haben, Namen des Formulars, **Put**_Eigenschaft_. Vorgänge, die der Wert einer Eigenschaft mit einem Zeiger auf ein ADO-Objekt festgelegt haben, Namen des Formulars, **PutRef**_Eigenschaft_.  
  
 Sie können abrufen oder Festlegen einer Eigenschaft durch Aufrufe der folgenden Formen:  
  
```cpp
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```
  
## <a name="using-property-directives"></a>Using-Eigenschaftendirektiven  
 Die **__declspec(property...)**  Compilerdirektive ist eine Erweiterung der Microsoft-spezifischen C-Sprache, die eine Funktion, die als eine Eigenschaft verwendet, um eine alternative Syntax deklariert. Sie können daher festlegen oder Abrufen der Werte einer Eigenschaft in einer Weise ähnlich wie in Visual Basic. Beispielsweise können Sie festlegen, und erhalten eine Eigenschaft auf diese Weise:  
  
```cpp
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```
  
 Beachten Sie, dass Sie nicht in Code:  
  
```cpp
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```
  
 Der Compiler generiert den entsprechenden **erhalten** _-_ , **Put**-, oder **PutRef** _-Eigenschaft_ aufrufbasierte, auf welche alternative Syntax deklariert wird, und gibt an, ob die Eigenschaft wird gelesen bzw. geschrieben werden.  
  
 Die **__declspec(property...)**  Compilerdirektive kann nur deklarieren **erhalten**, **put**, oder **erhalten** und **put** alternative Syntax für eine Funktion. Schreibgeschützte Vorgänge nur haben eine **erhalten** Deklaration; nur-schreiben-Vorgänge, die nur eine **put** Deklaration; Vorgänge, die sind sowohl Lese-als auch sowohl **erhalten** und **put** Deklarationen.  
  
 Mit dieser Richtlinie sind nur zwei Deklarationen enthalten; Jede Eigenschaft kann jedoch drei Eigenschaftenfunktionen verfügen: **Erste**_Eigenschaft_, **Put**_Eigenschaft_, und **PutRef**_Eigenschaft_. In diesem Fall haben nur zwei Formen der Eigenschaft, die alternative Syntax.  
  
 Z. B. die **Befehl** Objekt **ActiveConnection** Eigenschaft wird deklariert, mit der eine alternative Syntax für **erhalten**_ActiveConnection_und **PutRef**_ActiveConnection_. Die **PutRef**-Syntax ist eine gute Wahl, da in der Praxis in der Regel Sie eine offene put möchten **Verbindung** Objekt (, also eine **Verbindung** Objektzeiger) in diesem Diese Eigenschaft. Auf der anderen Seite der **Recordset** Objekt verfügt über **erhalten**-, **Put**–, und **PutRef**_ActiveConnection_Vorgänge, jedoch keine alternative Syntax.  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>Sammlungen, die GetItem-Methode und die Item-Eigenschaft  

 ADO definiert mehrere Auflistungen, einschließlich **Felder**, **Parameter**, **Eigenschaften**, und **Fehler**. In Visual C++ die **GetItem (_Index_)** Methode gibt ein Element der Auflistung zurück. *Index* ist eine **Variant**, dessen Wert ist entweder einen numerischen Index des Elements in der Auflistung oder eine Zeichenfolge, die mit dem Namen des Members.  
  
 Die **__declspec(property...)**  Compiler-Anweisung deklariert den **Element** Eigenschaft als eine alternative Syntax für jede Sammlung der grundlegenden **'GetItem()'** Methode. Die alternative Syntax verwendet eckige Klammern und Verweis auf ein Array ähnelt. Im Allgemeinen werden die beiden Formen wie folgt aussehen:  
  
```cpp
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```
  
 Z. B. ein Feld einen Wert zuweisen einer **Recordset** Objekt, mit dem Namen  **_Rs_** , abgeleitet von der **Autoren** Tabelle mit den **Pubs** Datenbank. Verwenden der **Item()** Eigenschaft auf die dritte **Feld** von der **Recordset** Objekt **Felder** (Sammlungen werden indiziert aus Auflistung 0 (null); Angenommen, das dritte Feld den Namen  **_au\_Fname_** ). Rufen Sie dann die **Value()** Methode für die **Feld** Objekt, das einen Zeichenfolgenwert zuweisen.  
  
 Dies kann ausgedrückt werden in Visual Basic in der folgenden vier Methoden (die letzten beiden Formen sind nur in Visual Basic; andere Sprachen müssen keine Entsprechungen):  
  
```cpp
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```
  
 In Visual C++ entspricht auf die ersten beiden Formulare, die oben aufgeführten:  
  
```cpp
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```
  
 – oder – (die alternative Syntax für die **Wert** Eigenschaft wird ebenfalls angezeigt.)  
  
```cpp
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```
  
 Beispiele für eine Auflistung durchlaufen finden Sie im Abschnitt "ADO-Collections" "ADO Reference".  
  
## <a name="com-specific-data-types"></a>COM-spezifischen Datentypen  
 Im Allgemeinen haben alle Visual Basic-Datentyp, die in der ADO-API-Referenz Sie finden eine Visual C++ entspricht. Dazu gehören z. B. Standarddatentypen **unsigned Char** für eine Visual Basic **Byte**, **kurze** für **Ganzzahl**, und  **lange** für **lange**. Suchen in der Syntax Indexesto angezeigt, was für die Operanden des einer bestimmten Methode oder Eigenschaft benötigt wird.  
  
 Die Ausnahmen von dieser Regel werden die spezifisch für COM-Datentypen: **Variant**, **BSTR**, und **SafeArray**.  
  
### <a name="variant"></a>Variant  
 Ein **Variant** ist ein Typ von strukturierten Daten, die ein Wertemember und einen Datenmember des Typs enthält. Ein **Variant** kann eine Vielzahl von anderen Datentypen, einschließlich einer anderen Variante, BSTR, boolescher Wert, IDispatch oder IUnknown-Zeiger, Währung, Datum und usw. enthalten. COM stellt auch, dass Methoden, mit denen sie einfach einen Datentyp in einen anderen konvertieren.  
  
 Die **_variant_t** -Klasse kapselt und verwaltet die **Variant** -Datentyp.  
  
 Die ADO-API-Referenz, sagt eine Methode oder Eigenschaft Operand akzeptiert einen Wert, in der Regel bedeutet dies der Wert wird übergeben, einem **_variant_t**.  
  
 Mit dieser Regel wird explizit "true", wenn die **Parameter** Abschnitt in den Themen der Referenz zu ADO-API besagt, dass ein Operand ist eine **Variant**. Eine Ausnahme ist die Dokumentation ausdrücklich darauf hinweist, die Operanden akzeptiert kein standard-Datentyp, z. B. **lange** oder **Byte**, oder eine Enumeration. Eine weitere Ausnahme bilden, wenn der Operand übernimmt eine **Zeichenfolge**.  
  
### <a name="bstr"></a>BSTR  
 Ein **BSTR** (**B**rswindowsbasic **STR**Ing) ist ein Typ von strukturierten Daten, die eine Zeichenfolge und die Länge der Zeichenfolge enthält. COM stellt Methoden zum zuordnen, bearbeiten und Freigeben einer **BSTR**.  
  
 Die **_bstr_t** -Klasse kapselt und verwaltet die **BSTR** -Datentyp.  
  
 Wird bei der ADO-API-Referenz auf eine Methode oder Eigenschaft sagt eine **Zeichenfolge** Wert bedeutet dies, dass der Wert in Form von einem **_bstr_t**.  
  
### <a name="casting-variantt-and-bstrt-classes"></a>Umwandeln von _variant_t und _bstr_t-Klasse  
 Häufig ist es nicht notwendig, explizit Code eine **_variant_t** oder **_bstr_t** in einem Argument für einen Vorgang. Wenn die **_variant_t** oder **_bstr_t** -Klasse verfügt über einen Konstruktor, der den Datentyp des Arguments entspricht, generiert der Compiler den entsprechenden **_variant_t** oder **_bstr_t**.  
  
 Allerdings, wenn das Argument nicht eindeutig ist, d. h. Datentyp des Arguments entspricht mehr als einen Konstruktor, müssen Sie das Argument mit den entsprechenden Datentyp, den korrekten Konstruktor aufrufen eine Umwandlung.  
  
 Z. B. die Deklaration für die **Open** Methode ist:  
  
```cpp
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```
  
 Die `ActiveConnection` Argument akzeptiert einen Verweis auf eine **_variant_t**, den Sie als eine Verbindungszeichenfolge oder ein Zeiger auf ein offenes codieren können **Verbindung** Objekt.  
  
 Die richtige **_variant_t** werden implizit erstellt werden, wenn Sie eine Zeichenfolge, wie z. B. übergeben "`DSN=pubs;uid=MyUserName;pwd=MyPassword;`", oder ein Zeiger, z. B. "`(IDispatch *) pConn`".  
  
> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.  
  
 Oder Sie können explizit einen **_variant_t** , enthalten einen Zeiger wie "`_variant_t((IDispatch *) pConn, true)`". Die Umwandlung, `(IDispatch *)`, löst die Mehrdeutigkeit mit einem anderen Konstruktor, der einen Zeiger auf eine IUnknown-Schnittstelle verwendet.  
  
 Es ist eine wichtige, jedoch nur selten tatsächlich bereits erwähnt, ADO eine IDispatch-Schnittstelle ist. Jedes Mal, wenn für die ein Zeiger auf ein ADO-Objekt übergeben werden muss, als eine **Variant**, diesen Zeiger als Zeiger auf eine IDispatch-Schnittstelle umgewandelt werden muss.  
  
 Im letzte Fall codes explizit das zweite boolesche Argument des Konstruktors mit den optional, Standardwert `true`. Dieses Argument bewirkt, dass die **Variant** Konstruktor aufrufen, die **"AddRef"** ()-Methode, die ADO automatisch kompensiert die **_variant_t::Release()** ()-Methode Wenn die ADO-Methode oder Eigenschaft aufrufen abgeschlossen ist.  
  
### <a name="safearray"></a>SafeArray  
 Ein **SafeArray** ist ein strukturierte Daten-Typ, der ein Array mit anderen Datentypen enthält. Ein **SafeArray** heißt *sicher* da Informationen über die Grenzen jeder Arraydimension enthält und den Zugriff auf Elemente innerhalb dieser Grenzen des Arrays schränkt.  
  
 Wenn die ADO-API-Referenz, sagt eine Methode oder Eigenschaft akzeptiert, oder gibt ein Array zurück, es bedeutet, dass die Methode oder Eigenschaft akzeptiert bzw. zurückgibt eine **SafeArray**, keines systemeigenen C/C++-Arrays.  
  
 Beispielsweise der zweite Parameter, der die **Verbindung** Objekt **OpenSchema** Methode erfordert ein Array von **Variant** Werte. Die **Variant** Werte übergeben werden müssen, als Elemente einer **SafeArray**, und die **SafeArray** muss festgelegt werden, als der Wert eines anderen **Variant** . Es ist, die andere **Variant** als das zweite Argument der übergebene **OpenSchema**.  
  
 Ausführlichere Beispiele, die das erste Argument von der **finden** Methode ist eine **Variant** , deren Wert ist ein eindimensionales **SafeArray**; jede der ersten und zweiten optionalen Argumente der **AddNew** ist ein eindimensionales **SafeArray**; und der Rückgabewert von der **GetRows** Methode ist eine **Variant** , deren Wert ist ein zweidimensionales **SafeArray**.  
  
## <a name="missing-and-default-parameters"></a>Fehlende und Standardparameter  
 Visual Basic ermöglicht-Parametern in Methoden fehlt. Z. B. die **Recordset** Objekt **öffnen** Methode über fünf Parameter verfügt, aber Sie überspringen und nachfolgende Parameter lassen können. Eine standardmäßige **BSTR** oder **Variant** wird je nach den Datentyp, der den fehlenden Operanden ersetzt werden.  
  
 In C/C++ müssen alle Operanden angegeben werden. Wenn Sie einen fehlenden Parameter angeben möchten, deren Datentyp eine Zeichenfolge ist, geben Sie einen **_bstr_t** , die eine null-Zeichenfolge enthält. Sollten Sie einen fehlenden Parameter angeben, deren Datentyp, eine **Variant**, geben Sie einen **_variant_t** mit einem Wert von DISP_E_PARAMNOTFOUND und einen Typ eines VT_ERROR. Alternativ geben Sie die entsprechende **_variant_t** konstant **VtMissing**, wird die vom der **#import** Richtlinie.  
  
 Drei Methoden werden Ausnahmen von der typischen Verwendung von **VtMissing**. Hierbei handelt es sich die **Execute** Methoden der **Verbindung** und **Befehl** Objekte, und die **NextRecordset** Methode der **Recordset** Objekt. Im folgenden sind die Signaturen:  
  
```cpp
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```
  
 Die Parameter *RecordsAffected* und *Parameter*, sind Zeiger auf eine **Variant**. *Parameter* ist ein Eingabeparameter, die angibt, die Adresse einer **Variant** mit einem einzelnen Parameter oder Array von Parametern, die den Befehl ausgeführt wird, geändert werden. *RecordsAffected* ist ein Ausgabeparameter, der angibt, die Adresse einer **Variant**, in dem die Anzahl der Zeilen betroffen sind, von der Methode zurückgegeben wird.  
  
 In der **Befehl** Objekt **Execute** -Methode, um anzugeben, dass keine Parameter, indem Sie festlegen angegeben werden *Parameter* entweder `&vtMissing` (empfohlen) oder der null-Zeiger (d. h. **NULL** oder 0 (null)). Wenn *Parameter* festgelegt ist, der null-Zeiger, ersetzt die Methode intern die Entsprechung der **VtMissing**, und schließt dann den Vorgang.  
  
 In den Methoden, anzugeben, dass die Anzahl der betroffenen Datensätze nicht zurückgegeben werden soll, können Sie durch Festlegen von *RecordsAffected* zum null-Zeiger. In diesem Fall ist der null-Zeiger nicht so viel einen fehlenden Parameter anzugeben, dass die Methode die Anzahl der betroffenen Datensätze verwerfen soll.  
  
 Für diese drei Methoden ist es daher etwas wie z. B. Code gültig:  
  
```cpp
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```
  
## <a name="error-handling"></a>Fehlerbehandlung  
 In COM geben die meisten Vorgänge einen HRESULT-Rückgabecode, der angibt, ob eine Funktion erfolgreich abgeschlossen. Die **#import** Richtlinie Wrappercode, um jede "rohes" Methode oder Eigenschaft generiert und überprüft das zurückgegebene HRESULT. Wenn HRESULT Fehler weist darauf hin, löst der Code einen COM-Fehler vom aufrufenden _com_issue_errorex() mit dem HRESULT-Rückgabecode als Argument an. COM-Fehlerobjekte abgefangen werden können, eine **versuchen**-**catch** Block. (Aus Gründen der Effizienz catch einen Verweis auf eine **_com_error** Objekt.)  
  
 Denken Sie daran, diese ADO-Fehler: sie auf die ADO-Vorgangsfehler zurückzuführen. Fehler, die vom zugrunde liegenden Anbieter zurückgegeben werden, als **Fehler** Objekte in der **Verbindung** Objekt **Fehler** Auflistung.  
  
 Die **#import** Richtlinie erstellt nur Fehler Ereignisbehandlungsroutinen für Methoden und Eigenschaften, die in der ADO-DLL-Datei deklariert. Allerdings können Sie dieses gleiche Mechanismus zur Fehlerbehandlung durch Schreiben eigener fehlerüberprüfung-Makro oder zur Inlinefunktion nutzen. Finden Sie unter [Visual C++-Erweiterungen](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md), oder den Code in den folgenden Abschnitten für Beispiele.  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Visual C++-Entsprechungen von VB-Konventionen  
 Folgendes ist eine Zusammenfassung der mehrere Konventionen in der ADO-Dokumentation in Visual Basic als auch deren Entsprechungen in Visual C++ programmiert.  
  
### <a name="declaring-an-ado-object"></a>Deklarieren eines ADO-Objekts  
 In Visual Basic eine ADO-Objekt-Variable (in diesem Fall für eine **Recordset** Objekt) wie folgt deklariert:  
  
```vb
Dim rst As ADODB.Recordset  
```
  
 Der Klausel "`ADODB.Recordset`", ist die ProgID des der **Recordset** in der Registrierung definiert sind. Eine neue Instanz der ein **Datensatz** Objekt wie folgt deklariert:  
  
```vb
Dim rst As New ADODB.Recordset  
```
  
 -oder-  
  
```vb
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```
  
 In Visual C++ die **#import** -Direktive generiert intelligenten Zeigertyp Deklarationen für die ADO-Objekte. Z. B. eine Variable, die auf zeigt eine **_Recordset** Objekt weist Typ **_RecordsetPtr**, und wie folgt deklariert:  
  
```cpp
_RecordsetPtr  rs;  
```
  
 Eine Variable, die auf eine neue Instanz der verweist eine **_Recordset** Objekt wie folgt deklariert:  
  
```cpp
_RecordsetPtr  rs("ADODB.Recordset");  
```
  
 -oder-  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance("ADODB.Recordset");  
```
  
 -oder-  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance(__uuidof(_Recordset));  
```
  
 Nach der **CreateInstance** -Methode aufgerufen wird, kann die Variable wie folgt verwendet werden:  
  
```cpp
rs->Open(...);  
```
  
 Beachten Sie, dass in einem Fall ist die "`.`" Operator wird verwendet, als wären die Variable eine Instanz einer Klasse (`rs.CreateInstance`), und klicken Sie in einem anderen Fall der "`->`" Operator wird verwendet, als wären die Variable ein Zeiger auf eine Schnittstelle (`rs->Open`).  
  
 Eine Variable kann auf zwei Arten verwendet werden, da die "`->`"-Operator wird überladen, um eine Instanz einer Klasse zu verhalten sich wie ein Zeiger auf eine Schnittstelle zu ermöglichen. Ein Mitglied von private Klasse für die Instanzvariable enthält einen Zeiger auf die **_Recordset** Schnittstelle; die "`->`" Operator gibt diesen Zeiger; und der zurückgegebene Zeiger greift auf die Member des der **_Recordset**  Objekt.  
  
### <a name="coding-a-missing-parameter---string"></a>Codieren eines fehlenden Parameters - Zeichenfolge  
 Wenn Sie einen fehlenden code müssen **Zeichenfolge** Operanden in Visual Basic, lassen Sie lediglich den Operanden. Sie müssen den Operanden in Visual C++ angeben. Code eine **_bstr_t** , die eine leere Zeichenfolge als Wert verfügt.  
  
```cpp
_bstr_t strMissing(L"");  
```
  
### <a name="coding-a-missing-parameter---variant"></a>Codieren einen fehlenden Parameters - Variante  
 Wenn Sie einen fehlenden code müssen **Variant** Operanden in Visual Basic, lassen Sie lediglich den Operanden. Sie müssen alle Operanden in Visual C++ angeben. Code, ein fehlendes **Variant** Parameter mit einer **_variant_t** auf den Sonderwert DISP_E_PARAMNOTFOUND und Typ VT_ERROR festgelegt. Geben Sie alternativ **VtMissing**, die ist eine entsprechende vordefinierte Konstante angegeben, durch die **#import** Richtlinie.  
  
```cpp
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```
  
 \- oder -  
  
```cpp
...vtMissing...;  
```
  
### <a name="declaring-a-variant"></a>Deklarieren Sie eine Variante  
 In Visual Basic eine **Variant** wird deklariert, mit der **Dim** -Anweisung wie folgt:  
  
```vb
Dim VariableName As Variant  
```
  
 In visuellen C++, deklarieren Sie eine Variable als Typ **_variant_t**. Einige schematische **_variant_t** Deklarationen werden unten angezeigt.  
  
> [!NOTE]
>  Diese Deklarationen geben lediglich eine ungefähre Vorstellung davon, was Sie in der eigenen Anwendung programmieren würde. Weitere Informationen finden Sie unter den folgenden Beispielen und die Visual C++-Dokumentation.  
  
```cpp
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```
  
### <a name="using-arrays-of-variants"></a>Verwenden von Arrays von Varianten  
 In Visual Basic, Arrays von **Varianten** codiert werden können, mit der **Dim** -Anweisung, oder Sie können die **Array** Funktion, wie im folgenden Beispielcode gezeigt:  
  
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
  
 Die folgende Visualisierung C++ Beispiel veranschaulicht die Verwendung einer **SafeArray** mit verwendet eine **_variant_t**.  
  
#### <a name="notes"></a>Hinweise  
 Die folgenden Hinweise entsprechen kommentierten Abschnitten im Codebeispiel.  
  
1.  Wieder ist die TESTHR() Inline-Funktion definiert, um die vorhandenen Fehlerbehandlungsmechanismus nutzen.  
  
2.  Benötigen Sie nur ein eindimensionales Array, sodass Sie verwenden können **SafeArrayCreateVector**, statt den allgemeinen **SAFEARRAYBOUND** Deklaration und **"SafeArrayCreate"** -Funktion. Im folgenden finden Sie diesen Code mit aussehen würde **"SafeArrayCreate"** :  
  
    ```cpp
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```
  
3.  Das Schema, das die Enumerationskonstante identifizierte **AdSchemaColumns**, vier Einschränkungsspalten zugeordnet ist: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME und COLUMN_NAME. Aus diesem Grund wird ein Array von **Variant** Werte mit vier Elementen erstellt wird. Anschließend wird ein Einschränkungswert, der dritten Spalte, TABLE_NAME entspricht, angegeben.  
  
     Die **Recordset** zurückgegeben wird, besteht aus mehreren Spalten, die eine Teilmenge davon besteht aus den Einschränkungsspalten. Die Werte der Einschränkungsspalten für jede zurückgegebene Zeile müssen die entsprechenden Einschränkungswerte identisch sein.  
  
4.  Wer sich mit **SafeArrays** möglicherweise überrascht es, dass **"SafeArrayDestroy"** () wird nicht aufgerufen, bevor das Beenden. In der Tat Aufrufen **"SafeArrayDestroy"** () in diesem Fall führt dazu, dass eine Laufzeitausnahme. Der Grund ist, dass der Destruktor für `vtCriteria` ruft **VariantClear**() Wenn die **_variant_t** außerhalb des gültigen Bereichs, auf dem frei wird, wird die **SafeArray**. Aufrufen von **"SafeArrayDestroy"** , ohne manuellen Löschen der **_variant_t**, würde dazu führen, dass den Destruktor, um zu versuchen, eine ungültige löschen **SafeArray** Zeiger.  
  
     Wenn **"SafeArrayDestroy"** wurden aufgerufen wird, würde der Code wie folgt aussehen:  
  
    ```cpp
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```
  
     Es ist jedoch viel einfacher, Sie können die **_variant_t** verwalten die **SafeArray**.  
  
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
  
### <a name="using-property-getputputref"></a>Verwenden die Eigenschaft Get/Put/PutRef  
 Der Name einer Eigenschaft wird in Visual Basic nicht qualifiziert, gibt an, ob es abgerufen, zugewiesen oder ein Verweis zugewiesen wird.  
  
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
  
 Dieses Visual C++-Beispiel zeigt die **erhalten**/**Put**/**PutRef**_Eigenschaft_.  
  
#### <a name="notes"></a>Hinweise  
 Die folgenden Hinweise entsprechen kommentierten Abschnitten im Codebeispiel.  
  
1.  Dieses Beispiel verwendet zwei Arten von ein Fehlendes Zeichenfolgenargument: eine explizite-Konstante, **StrMissing**, und eine Zeichenfolge, die der Compiler verwendet, um das Erstellen eines temporären **_bstr_t** sind, die für den Rahmen der vorhanden **Open** Methode.  
  
2.  Es ist nicht erforderlich, der Operand des umzuwandeln `rs->PutRefActiveConnection(cn)` zu `(IDispatch *)` da der Typ des Operanden bereits `(IDispatch *)`.  
  
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
  
### <a name="using-getitemx-and-itemx"></a>Verwenden von GetItem(x)"und Artikel [X]  
 Diese Visual Basic-Beispiel wird veranschaulicht, die Standard- und alternative Syntax für **Element**().  
  
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
  
 Dieses Visual C++-Beispiel zeigt, **Element**.  
  
> [!NOTE]
>  Beachten Sie die folgenden entspricht kommentierten Abschnitten im Codebeispiel:  Wenn die Auflistung zugegriffen wird, mit **Element**, den Index **2**, umgewandelt werden muss **lange** damit ein geeigneter Konstruktor aufgerufen wird.  
  
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
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>ADO-Objektzeigern mit umwandeln (IDispatch *)  
 Im folgende Visual C++-Beispiel veranschaulicht die Verwendung (IDispatch *), ADO-Objektzeigern Umwandlung.  
  
#### <a name="notes"></a>Hinweise  
 Die folgenden Hinweise entsprechen kommentierten Abschnitten im Codebeispiel.  
  
1.  Geben Sie eine offene **Verbindung** Objekt in einen codierten explizit **Variant**. Wandeln sie mit (IDispatch \*), damit der richtige Konstruktor aufgerufen wird. Außerdem explizit festlegen, die zweite **_variant_t** Parameter, um den Standardwert **"true"** , sodass der Verweiszähler des Objekts richtig, wenn sein wird die **Open** Vorgang beendet.  
  
2.  Der Ausdruck `(_bstr_t)`, wird nicht umgewandelt, aber ein **_variant_t** Operator, der extrahiert eine **_bstr_t** die Zeichenfolge, aus der **Variant** zurückgegebenes **Wert** .  
  
 Der Ausdruck `(char*)`, wird nicht umgewandelt, aber ein **_bstr_t** Operator, der einen Zeiger auf die gekapselte Zeichenfolge in extrahiert eine **_bstr_t** Objekt.  
  
 In diesem Abschnitt werden einige nützliche Verhaltensweisen von veranschaulicht **_variant_t** und **_bstr_t** Operatoren.  
  
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
