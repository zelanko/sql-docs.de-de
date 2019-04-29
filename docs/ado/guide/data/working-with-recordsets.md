---
title: Arbeiten mit Recordsets | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO]
ms.assetid: bdf9a56a-de4a-44de-9111-2f11ab7b16ea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2378d438c575ad54a89f09c4c9ddcb157c246ffd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184826"
---
# <a name="working-with-recordsets"></a>Arbeiten mit Recordsets
Die **Recordset** Objekt verfügt über integrierte Features, mit denen Sie die Reihenfolge der Daten im Resultset, suchen Sie nach einem bestimmten Datensatz basierend auf Kriterien, die Sie angeben, und sogar die Suchvorgänge mithilfe von Indizes optimieren ändern können. Gibt an, ob diese Features verwendet werden könne.n hängt davon ab, der Anbieter und in einigen Fällen – wie z. B. mit der die [Index](../../../ado/reference/ado-api/index-property.md) -Eigenschaft: die Struktur der Datenquelle selbst.  
  
## <a name="arranging-data"></a>Anordnen von Daten  
 In vielen Fällen die effizienteste Methode zum Sortieren der Daten in Ihre **Recordset** durch Angeben von ORDER BY-Klausel in der SQL-Befehl verwendet, um die Ergebnisse zurückgegeben wird. Allerdings möglicherweise so ändern Sie die Reihenfolge der Daten in einem **Recordset** , die bereits erstellt wurde. Können Sie die **Sortierreihenfolge** Eigenschaft, um die Reihenfolge festlegen, welche Zeilen der einen **Recordset** werden durchlaufen. Darüber hinaus die **Filter** Eigenschaft bestimmt, welche Zeilen sind kann zugegriffen werden, wenn Zeilen durchlaufen.  
  
 Die **sortieren** Eigenschaft legt fest oder gibt einen **Zeichenfolge** Wert, der das Feld gibt Namen, der **Recordset** für die Sortierung. Jeder Name wird durch ein Komma getrennt und ggf. gefolgt von einem Leerzeichen und dem Schlüsselwort **ASC** (das Feld in aufsteigender Reihenfolge sortiert) oder **DESC** (das Feld in absteigender Reihenfolge sortiert). In der Standardeinstellung Wenn kein Schlüsselwort angegeben ist, wird das Feld in aufsteigender Reihenfolge sortiert.  
  
 Der Sortiervorgang ist effizient, da die Daten physisch nicht neu angeordnet, aber in der Reihenfolge, die durch einen Index angegebenen zugegriffen werden.  
  
 Die **Sortierreihenfolge** Eigenschaft ist erforderlich, die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft festgelegt werden, um **AdUseClient**. Ein temporärer Index erstellt werden für jedes Feld im angegebenen die **Sortierreihenfolge** Eigenschaft, wenn ein Index noch nicht vorhanden ist.  
  
 Festlegen der **Sortierreihenfolge** Eigenschaft auf eine leere Zeichenfolge wird die Zeilen in der ursprünglichen Reihenfolge zurücksetzen und Löschen temporärer Indizes. Vorhandene Indizes werden nicht gelöscht werden.  
  
 Nehmen Sie an einer **Recordset** enthält drei Felder, die mit dem Namen *FirstName*, *MiddleInitial*, und *"LastName"*. Legen Sie die **sortieren** Eigenschaft, um die Zeichenfolge "`lastName DESC, firstName ASC`", welcher Reihenfolge werden die **Recordset** nach dem Nachnamen in absteigender Reihenfolge und klicken Sie dann nach Vornamen in aufsteigender Reihenfolge. Der Wert von MiddleInitial wird ignoriert.  
  
 Kein Feld verwiesen wird, in der Sortierkriterien kann den Namen "ASC" oder "DESC", da diese Namen in mit den Schlüsselwörtern Konflikt **ASC** und **DESC**. Geben Sie ein Feld mit einem in Konflikt stehendem Namen einen Alias mithilfe die **AS** Schlüsselwort in der Abfrage, die zurückgibt der **Recordset**.  
  
 Weitere Informationen zu **Recordset** filtern, finden Sie unter "Filtern der Ergebnisse" weiter unten in diesem Thema.  
  
## <a name="finding-a-specific-record"></a>Suchen eines bestimmten Datensatzes  
 ADO bietet die [finden](../../../ado/reference/ado-api/find-method-ado.md) und [Seek](../../../ado/reference/ado-api/seek-method.md) Methoden für die Suche nach einem bestimmten Datensatz in einem **Recordset**. Die **finden** Methode wird durch eine Vielzahl von Anbietern unterstützt, aber auf ein einzelnes Suchkriterium begrenzt ist. Die **Seek** Methode auf mehreren Kriterien Suchvorgänge unterstützt, aber nicht von vielen Anbietern unterstützt wird.  
  
 Indizes für Felder können die Leistung erheblich verbessern die **finden** Methode und **sortieren** und **Filter** Eigenschaften der **Recordset** -Objekt. Sie können angeben, erstellen einen internen Index für eine **Feld** Objekt durch Festlegen der dynamischen [optimieren](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) Eigenschaft. Diese dynamische Eigenschaft hinzugefügt wird die **Eigenschaften** Auflistung von der **Feld** Objekt, wenn Sie festlegen, die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient**. Denken Sie daran, dass dieser Index für ADO intern ist – Sie können nicht auf sie zugreifen oder für andere Zwecke verwenden. Dieser Index außerdem unterscheidet sich von der [Index](../../../ado/reference/ado-api/index-property.md) Eigenschaft der **Recordset** Objekt.  
  
 Die **finden** Methode einen Wert innerhalb einer Spalte (Feld) schnell und sucht nach einem **Recordset**. Sie können die Geschwindigkeit der häufig verbessern die **finden** Methode für eine Spalte mit der **optimieren** Eigenschaft, um einen Index dafür erstellen.  
  
 Die **finden** schränkt die Suche auf den Inhalt eines Felds. Die **Seek** Methode erfordert, dass Sie es weitere Einschränkungen sowie noch und einen Index haben. Wenn Sie suchen müssen, nach mehreren Feldern, die nicht auf der Basis eines Indexes sind oder wenn Ihr Anbieter die Indizes nicht unterstützt, können Sie Ihre Ergebnisse einschränken, indem Sie mit der **Filter** Eigenschaft der **Recordset** Objekt.  
  
### <a name="find"></a>Suchen  
 Die **finden** -Methode sucht ein **Recordset** für die Zeile, die ein angegebenes Kriterium erfüllt. Optional kann die Richtung der Suche, Startzeile und Offset von der Startzeile angegeben werden. Wenn das Kriterium erfüllt ist, wird die aktuelle Zeilenposition auf den gefundenen Datensatz festgelegt. Andernfalls wird die Position festgelegt, oder zum Ende (Start) von der **Recordset**, je nachdem, auf die suchrichtung.  
  
 Nur können eine einzelne Spalten für das Kriterium angegeben werden. Das heißt, unterstützt diese Methode nicht für mehrere Spalten sucht.  
  
 Der Vergleichsoperator für das Kriterium kann sein"**>**"(größer als),"**\<**" (kleiner als), "=" (gleich), "> =" (größer als oder gleich), "< =" (kleiner als oder gleich), " <> "(nicht gleich), oder"LIKE"(Mustervergleich).  
  
 Der kriteriumwert kann es sich um eine Zeichenfolge, eine Gleitkommazahl oder ein Datum sein. Zeichenfolgenwerte mit einfachen Anführungszeichen oder "#" (Nummernzeichen) markiert werden (z. B. "State ="WA"" oder "Status = #WA #"). Date-Werte als "#" (Nummernzeichen) ein Trennzeichen (z. B. "Start_date > #7/22/97 #").  
  
 Wenn der Vergleichsoperator "like" ist, kann der Zeichenfolgenwert ein Sternchen (*), um die einem oder mehreren Vorkommen eines beliebigen Zeichens oder einer Teilzeichenfolge suchen enthalten. Z. B. "werde Zustand wie\*'" Maine und Massachusetts. Sie können auch führende und nachfolgende Sternchen verwenden, nach einer Teilzeichenfolge suchen, die in den Werten enthalten ist. Z. B. "State wie"\*als\*"" übereinstimmt, Alaska Arkansas und Massachusetts.  
  
 Sternchen können nur am Ende einer Zeichenfolge für die Kriterien oder zusammen am Anfang und Ende einer Kriterienzeichenfolge verwendet werden, wie oben beschrieben. Sie nicht das Sternchen als führender Platzhalter verwenden ("* str') oder eingebettete Platzhalter ('s\*R"). Dadurch wird einen Fehler.  
  
### <a name="seek-and-index"></a>Suchen und Indizieren  
 Verwenden der **Seek** -Methode zusammen mit den **Index** Eigenschaft, wenn der zugrunde liegenden Anbieter Indizes auf unterstützt die **Recordset** Objekt. Verwenden der [unterstützt](../../../ado/reference/ado-api/supports-method.md)**(AdSeek)** Methode, um zu bestimmen, ob der zugrunde liegenden Anbieter unterstützt **Seek**, und die **Supports(adIndex)** Methode, um zu bestimmen, ob der Anbieter Indizes unterstützt. (Z. B. die [OLE DB-Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) unterstützt **Seek** und **Index**.)  
  
 Wenn **Seek** befindet sich nicht gefunden werden der gewünschten Zeile, kein Fehler auftritt, und für die Zeile am Ende der **Recordset**. Legen Sie die **Index** Eigenschaft, um den gewünschten Index vor dem Ausführen dieser Methode.  
  
 Diese Methode wird nur mit serverseitiger Cursor unterstützt. Suchen wird nicht unterstützt, wenn die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaftswert, der die **Recordset** Objekt **AdUseClient**.  
  
 Diese Methode kann verwendet werden, nur, wenn die **Recordset** Objekt mit geöffnet wurde eine [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) Wert **AdCmdTableDirect**.  
  
## <a name="filtering-the-results"></a>Filtern der Ergebnisse  
 Die **finden** schränkt die Suche auf den Inhalt eines Felds. Die **Seek** Methode erfordert, dass Sie es weitere Einschränkungen sowie noch und einen Index haben. Wenn Sie suchen müssen, nach mehreren Feldern, die nicht auf der Basis eines Indexes sind oder wenn Ihr Anbieter die Indizes nicht unterstützt, können Sie Ihre Ergebnisse einschränken, indem Sie mit der **Filter** Eigenschaft der **Recordset** Objekt.  
  
 Verwenden der **Filter** Eigenschaft, um selektiv um Datensätze im Bildschirm ein **Recordset** Objekt. Die gefilterten **Recordset** wird der aktuelle Cursor, der Möglichkeit, in dem aufgezeichnet, die nicht erfüllt die **Filter** Kriterien sind nicht verfügbar, in der **Recordset** bis der **Filter** wird entfernt. Andere Eigenschaften, die basierend auf den aktuellen Cursor Rückgabewerte sind betroffen, z. B. **AbsolutePosition**, **AbsolutePage**, **RecordCount**, und  **PageCount**. Dies ist, da das Festlegen der **Filter** wechselt Eigenschaft auf einen bestimmten Wert des aktuellen Datensatzes in den ersten Datensatz, der den neuen Wert entspricht.  
  
 Die **Filter** Eigenschaft akzeptiert ein Argument vom Typ variant. Dieser Wert stellt dar, eine der drei Methoden für die Verwendung der **Filter** Eigenschaft: Kriterienzeichenfolge eine **FilterGroupEnum** -Konstante oder ein Array von Lesezeichen. Weitere Informationen finden Sie weiter unten in diesem Thema Filterung mit einer Zeichenfolge der Suchkriterien und Filterung mit einer Konstanten Filtern mit Lesezeichen.  
  
> [!NOTE]
>  Wenn Sie wissen, dass die Daten, die Sie auswählen möchten, ist es in der Regel effizienter, öffnen Sie eine **Recordset** mit einer SQL­Anweisung, die das Resultset, statt die standardremotedatenbank effektiv filtert die **Filter** Eigenschaft.  
  
 So entfernen Sie einen Filter aus einem **Recordset**, verwenden Sie die **AdFilterNone** Konstanten. Festlegen der **Filter** Eigenschaft, um eine Zeichenfolge der Länge 0 (null) ("") hat dieselbe Wirkung wie die Verwendung der **AdFilterNone** Konstanten.  
  
### <a name="filtering-with-a-criteria-string"></a>Filtern mit einer Zeichenfolge der Suchkriterien  
 Die Zeichenfolge der Suchkriterien besteht aus der Klauseln in der Form *FieldName Operatorwert* (z. B. `"LastName = 'Smith'"`). Sie können zusammengesetzte Klauseln erstellen, durch die Verkettung der einzelnen Klauseln mit **und** (z. B. `"LastName = 'Smith' AND FirstName = 'John'"`) und **oder** (z. B. `"LastName = 'Smith' OR LastName = 'Jones'"`). Verwenden Sie die folgenden Richtlinien, für die Kriterienzeichenfolgen:  
  
-   *FieldName* muss ein gültiger Feldname aus der **Recordset**. Wenn der Name des Felds Leerzeichen enthält, müssen Sie den Namen in eckige Klammern einschließen.  
  
-   *Operator* muss eine der folgenden sein: **\<**, **>**, **\< =**, **>=** , **<>**, **=**, oder **wie**.  
  
-   *Wert* ist der Wert, mit denen Sie die Feldwerte vergleichen (z. B. `'Smith'`, `#8/24/95#`, `12.345`, oder `$50.00`). Verwenden Sie einfache Anführungszeichen ('), mit Zeichenfolgen und Nummernzeichen (`#`) mit Datumsangaben. Für Zahlen können Sie das Dezimaltrennzeichen, Dollarzeichen und wissenschaftliche Schreibweise. Wenn *Operator* ist **wie**, *Wert* können Platzhalterzeichen verwenden. Nur das Sternchen (\*) und Prozentzeichen (%) Platzhalterzeichen sind zulässig, und sie müssen das letzte Zeichen in der Zeichenfolge sein. *Wert* darf nicht null sein.  
  
    > [!NOTE]
    >  Einfache Anführungszeichen (') in den Filter eingeschlossen *Wert*, verwenden Sie zwei einfache Anführungszeichen, um einen darstellen. Beispielsweise einen Filter für *Malley*, die Zeichenfolge der Suchkriterien muss `"col1 = 'O''Malley'"`. Um einzelne Anführungszeichen am Anfang und Ende der Filterwert einzuschließen, schließen Sie die Zeichenfolge in Nummernzeichen (#). Beispielsweise einen Filter für *'1'*, die Zeichenfolge der Suchkriterien muss `"col1 = #'1'#"`.  
  
 Es gibt keine Rangfolge zwischen **und** und **oder**. Klauseln können innerhalb von Klammern gruppiert werden. Allerdings können nicht gruppiert werden Klauseln, die mithilfe einer **oder** und treten Sie der Gruppe klicken Sie dann mit einer anderen Klausel mit einer AND, aus wie folgt.  
  
```  
(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'  
```  
  
 Stattdessen würden Sie diesen Filter wie folgt erstellen.  
  
```  
(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')  
```  
  
 In einer **wie** -Klausel, können Sie am Anfang und Ende des Musters einen Platzhalter (z. B. `LastName Like '*mit*'`) oder nur am Ende des Musters (z. B. `LastName Like 'Smit*'`).  
  
### <a name="filtering-with-a-constant"></a>Mit einer Konstanten filtern  
 Die folgenden Konstanten sind verfügbar für die Filterung **Recordsets**.  
  
|Konstante|Description|  
|--------------|-----------------|  
|**adFilterAffectedRecords**|Filter für die Anzeige von nur Datensätze, die von der letzten betroffen **löschen**, **Resync**, **UpdateBatch**, oder **CancelBatch** aufrufen.|  
|**adFilterConflictingRecords**|Die Filter zum Anzeigen der Datensätze, die Fehler bei der letzten Batchaktualisierung.|  
|**adFilterFetchedRecords**|Filter zum Anzeigen der Datensätze im aktuellen Cache – d. h. die Ergebnisse der dem letzten Aufruf von Datensätzen aus der Datenbank abzurufen.|  
|**adFilterNone**|Entfernt den aktuellen Filter und alle Datensätze für die Anzeige wiederhergestellt.|  
|**adFilterPendingRecords**|Filter für das Anzeigen von Datensätzen, die geändert haben, aber noch nicht an den Server gesendet wurden. Gilt nur für den Modus "Batch-Update".|  
  
 Die Filter-Konstanten erleichtern das zum Auflösen einzelner Datensatz Konflikte während der Modus "Batch-Update", sodass Sie anzeigen, z. B. nur die Datensätze, die während des letzten betroffen **UpdateBatch** -Methodenaufruf, siehe die folgende Beispiel.  
  
 `Attribute VB_Name = "modExaminingData"`  
  
### <a name="filtering-with-bookmarks"></a>Filtern mit Lesezeichen  
 Schließlich können Sie ein variant-Array von Lesezeichen zum Übergeben der **Filter** Eigenschaft. Bei dem Cursor enthält nur die Datensätze, deren Lesezeichen in der Eigenschaft übergeben wurde. Das folgende Codebeispiel erstellt ein Array von Lesezeichen aus den Datensätzen in einer **Recordset** die haben einer "B" in der *ProductName* Feld. Anschließend übergibt er das Array, das die **Filter** -Eigenschaft und zeigt Informationen zu gefilterten resultierenden **Recordset**.  
  
```  
'BeginFilterBkmk  
Dim vBkmkArray() As Variant  
Dim i As Integer  
  
'Recordset created using "SELECT * FROM Products" as command.  
'So, we will check to see if ProductName has a capital B, and  
'if so, add to the array.  
i = 0  
Do While Not objRs.EOF  
    If InStr(1, objRs("ProductName"), "B") Then  
        ReDim Preserve vBkmkArray(i)  
        vBkmkArray(i) = objRs.Bookmark  
        i = i + 1  
        Debug.Print objRs("ProductName")  
    End If  
    objRs.MoveNext  
Loop  
  
'Filter using the array of bookmarks.  
objRs.Filter = vBkmkArray  
  
objRs.MoveFirst  
Do While Not objRs.EOF  
    Debug.Print objRs("ProductName")  
    objRs.MoveNext  
Loop  
'EndFilterBkmk  
```  
  
## <a name="creating-a-clone-of-a-recordset"></a>Erstellen eines Klons von einem Recordset  
 Verwenden der **Klon** dupliziert-Methode zum Erstellen mehrerer **Recordset** Objekte, insbesondere, wenn Sie mehr als einem aktuellen Datensatz in einer bestimmten Gruppe von Datensätzen beibehalten möchten. Mithilfe der **Klon** Methode ist effizienter als das Erstellen und öffnen ein neues **Recordset** Objekt mit der gleichen Definition wie das Original.  
  
 Der aktuelle Datensatz des neu erstellten Klons ist ursprünglich auf den ersten Eintrag festgelegt. Der Zeiger des aktuellen Datensatzes in einer geklonten **Recordset** ist nicht synchronisiert, wobei die ursprüngliche oder umgekehrt. Sie können unabhängig voneinander in den einzelnen navigieren **Recordset**.  
  
 Änderungen an einer **Recordset** Objekt im aller seiner Klone unabhängig vom Cursortyp sichtbar sind. Jedoch nach der Ausführung [Requery](../../../ado/reference/ado-api/requery-method.md) auf dem ursprünglichen **Recordset**, Klone werden nicht mehr auf den ursprünglichen synchronisiert werden.  
  
 Schließen die ursprüngliche **Recordset** schließt nicht seine Datenbankkopien ebenso wie die ursprünglichen oder einen der anderen Kopien nicht schließen eine Kopie zu schließen.  
  
 Sie können Klonen eine **Recordset** Objekt nur, wenn sie Lesezeichen unterstützt. Lesezeichenwerte sind austauschbar. d. h. ein Lesezeichenverweis von einem **Recordset** -Objekt verweist auf den gleichen Datensatz in einer seiner Klone.
