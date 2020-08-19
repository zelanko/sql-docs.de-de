---
description: Arbeiten mit Recordsets
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 84f60e269bcd01bdacc7647f1498c588620f049e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452522"
---
# <a name="working-with-recordsets"></a>Arbeiten mit Recordsets
Das **Recordset** -Objekt verfügt über integrierte Funktionen, mit denen Sie die Reihenfolge der Daten im Resultset neu anordnen können, um anhand der von Ihnen bereitgestellten Kriterien nach einem bestimmten Datensatz zu suchen und um diese Suchvorgänge mithilfe von Indizes zu optimieren. Ob diese Features zur Verwendung verfügbar sind, hängt vom Anbieter und in einigen Fällen (z. b. von der [Index](../../../ado/reference/ado-api/index-property.md) Eigenschaft-der Struktur der Datenquelle) ab.  
  
## <a name="arranging-data"></a>Anordnen von Daten  
 Häufig ist die effizienteste Methode zum Sortieren der Daten in Ihrem **Recordset** die Angabe einer ORDER BY-Klausel im SQL-Befehl, mit der die Ergebnisse zurückgegeben werden. Möglicherweise müssen Sie jedoch die Reihenfolge der Daten in einem **Recordset** ändern, das bereits erstellt wurde. Sie können die **Sort** -Eigenschaft verwenden, um die Reihenfolge festzulegen, in der die Zeilen eines **Recordsets** durchlaufen werden. Außerdem legt die **Filter** -Eigenschaft fest, auf welche Zeilen beim Durchlaufen von Zeilen zugegriffen werden kann.  
  
 Die **Sort** -Eigenschaft legt einen Zeichen folgen Wert fest oder gibt einen **Zeichen** folgen Wert zurück, der die Feldnamen im zu sortierende **Recordset** angibt. Jeder Name wird durch ein Komma getrennt, gefolgt von einem Leerzeichen und dem Schlüsselwort **ASC** (bei dem das Feld in aufsteigender Reihenfolge sortiert wird) oder **DESC** (bei dem das Feld in absteigender Reihenfolge sortiert wird). Wenn kein Schlüsselwort angegeben wird, wird das Feld standardmäßig in aufsteigender Reihenfolge sortiert.  
  
 Der Sortiervorgang ist effizient, da die Daten nicht physisch neu angeordnet werden, sondern in der durch einen Index angegebenen Reihenfolge aufgerufen wird.  
  
 Die **Sort** -Eigenschaft erfordert, dass die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt ist. Ein temporärer Index wird für jedes Feld erstellt, das in der **Sort** -Eigenschaft angegeben ist, wenn noch kein Index vorhanden ist.  
  
 Wenn Sie die **Sort** -Eigenschaft auf eine leere Zeichenfolge festlegen, werden die Zeilen auf Ihre ursprüngliche Reihenfolge zurückgesetzt und temporäre Indizes gelöscht. Vorhandene Indizes werden nicht gelöscht.  
  
 Angenommen, ein **Recordset** enthält drei Felder namens *FirstName*, *Mittel dleinitial*und *LastName*. Legen Sie die **Sort** -Eigenschaft auf die Zeichenfolge " `lastName DESC, firstName ASC` " fest, wodurch das **Recordset** nach dem Nachnamen in absteigender Reihenfolge und dann nach dem Vornamen in aufsteigender Reihenfolge sortiert wird. Der erste Mittelwert wird ignoriert.  
  
 Kein Feld, auf das in einer Sortier Kriterienzeichenfolge verwiesen wird, kann "ASC" oder "DESC" genannt werden, weil diese Namen in Konflikt mit den Schlüsselwörtern **ASC** und **DESC** Weisen Sie einem Feld mit einem in Konflikt stehenden Namen einen Alias zu, indem Sie das **As** -Schlüsselwort in der Abfrage verwenden, die das **Recordset**zurückgibt.  
  
 Weitere Informationen zum Filtern von **Recordsets** finden Sie weiter unten in diesem Thema unter "Filtern der Ergebnisse".  
  
## <a name="finding-a-specific-record"></a>Suchen eines bestimmten Datensatzes  
 ADO stellt die [Such](../../../ado/reference/ado-api/seek-method.md) -und Such [Methoden zum Suchen](../../../ado/reference/ado-api/find-method-ado.md) eines bestimmten Datensatzes in einem **Recordset**bereit. Die **Find** -Methode wird von einer Vielzahl von Anbietern unterstützt, ist aber auf ein einzelnes Suchkriterium beschränkt. Die **Seek** -Methode unterstützt das Suchen nach mehreren Kriterien, wird aber von vielen Anbietern nicht unterstützt.  
  
 Indizes für Felder können die Leistung der Methode **Suchen** und **Sortieren** und **Filtern** des **Recordset** -Objekts erheblich verbessern. Sie können einen internen Index für ein **Feld** Objekt erstellen, indem Sie die dynamische [Optimierungs](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) Eigenschaft festlegen. Diese dynamische Eigenschaft wird der **Properties** -Auflistung des **Field** -Objekts hinzugefügt, wenn Sie die Eigenschaft " [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) " auf " **adUseClient**" festlegen. Beachten Sie, dass es sich um einen internen Index für ADO handelt. Sie können darauf nicht zugreifen oder ihn für andere Zwecke verwenden. Außerdem unterscheidet sich dieser Index von der [Index](../../../ado/reference/ado-api/index-property.md) -Eigenschaft des **Recordset** -Objekts.  
  
 Die **Find** -Methode sucht schnell einen Wert in einer Spalte (Feld) eines **Recordsets**. Sie können die Geschwindigkeit der **Find** -Methode für eine Spalte häufig verbessern, indem Sie die Eigenschaft **optimieren** verwenden, um einen Index dafür zu erstellen.  
  
 Die **Find** -Methode schränkt die Suche auf den Inhalt eines Felds ein. Die **Seek** -Methode erfordert, dass Sie über einen Index verfügen und auch über andere Einschränkungen verfügen. Wenn Sie nach mehreren Feldern suchen müssen, die nicht die Basis eines Indexes sind, oder wenn der Anbieter keine Indizes unterstützt, können Sie die Ergebnisse einschränken, indem Sie die **Filter** -Eigenschaft des **Recordset** -Objekts verwenden.  
  
### <a name="find"></a>Suchen  
 Die **Find** -Methode durchsucht ein **Recordset** nach der Zeile, die ein angegebenes Kriterium erfüllt. Optional können die Suchrichtung, die Anfangs Zeile und der Offset der Anfangs Zeile angegeben werden. Wenn das Kriterium erfüllt ist, wird die aktuelle Zeilen Position für den gefundenen Datensatz festgelegt. Andernfalls wird die Position abhängig von der Suchrichtung auf das Ende (oder den Anfang) des **Recordsets**festgelegt.  
  
 Für das Kriterium kann nur ein einspaltige Name angegeben werden. Mit anderen Worten: Diese Methode unterstützt keine Suchvorgänge mit mehreren Spalten.  
  
 Der Vergleichs Operator für das Kriterium kann " **>** " (größer als), "* * \<**" (less than), "=" (equal), "> =" (größer als oder gleich), "<=" (kleiner als oder gleich), "<>" (nicht gleich) oder "like" (Muster Vergleich) sein.  
  
 Der Kriterienwert kann eine Zeichenfolge, eine Gleit Komma Zahl oder ein Datum sein. Zeichen folgen Werte werden durch einfache Anführungszeichen oder #-Zeichen (Nummern Zeichen) getrennt (z. b. "State = ' WA '" oder "State = #WA #"). Datumswerte werden durch die Zeichen "#" (Nummern Zeichen) getrennt (z. b. "start_date > #7/22/97 #").  
  
 Wenn der Vergleichs Operator "like" ist, kann der Zeichen folgen Wert ein Sternchen (*) enthalten, um nach einem oder mehreren Vorkommen eines beliebigen Zeichens oder einer Teil Zeichenfolge zu suchen. Beispiel: "State like es" \* entspricht "Maine and Massachusetts". Sie können auch führende und nachfolgende Sternchen verwenden, um eine Teil Zeichenfolge zu finden, die in den Werten enthalten ist. Beispielsweise entspricht "State like" \* As " \* " Alaska, Arkansas und Massachusetts.  
  
 Sternchen können nur am Ende einer Kriterienzeichenfolge oder sowohl am Anfang als auch am Ende einer Kriterienzeichenfolge verwendet werden, wie zuvor gezeigt. Sie können das Sternchen nicht als führenden Platzhalter (' * Str ') oder eingebetteten Platzhalter (es ist \* r ') verwenden. Dies führt zu einem Fehler.  
  
### <a name="seek-and-index"></a>Suchen und indizieren  
 Verwenden Sie die **Seek** -Methode in Verbindung mit der **Index** -Eigenschaft, wenn der zugrunde liegende Anbieter Indizes für das **Recordset** -Objekt unterstützt. Verwenden Sie die [Unterstützung](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** -Methode, um zu bestimmen, ob der zugrunde liegende Anbieter **Seek**unterstützt, und die **unterstützte (adIndex)** -Methode, um zu bestimmen, ob der Anbieter Indizes (Beispielsweise unterstützt der [OLE DB Anbieter für Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md) **Seek** und **Index**.)  
  
 Wenn **Seek** die gewünschte Zeile nicht findet, tritt kein Fehler auf, und die Zeile wird am Ende des **Recordsets**positioniert. Legen Sie die **Index** -Eigenschaft auf den gewünschten Index fest, bevor Sie diese Methode ausführen.  
  
 Diese Methode wird nur mit serverseitigen Cursorn unterstützt. Seek wird nicht unterstützt, wenn der [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschafts Wert des **Recordset** -Objekts **adUseClient**ist.  
  
 Diese Methode kann nur verwendet werden, wenn das **Recordset** -Objekt mit einem [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) -Wert von **adCmdTableDirect**geöffnet wurde.  
  
## <a name="filtering-the-results"></a>Filtern der Ergebnisse  
 Die **Find** -Methode schränkt die Suche auf den Inhalt eines Felds ein. Die **Seek** -Methode erfordert, dass Sie über einen Index verfügen und auch über andere Einschränkungen verfügen. Wenn Sie nach mehreren Feldern suchen müssen, die nicht die Basis eines Indexes sind, oder wenn der Anbieter keine Indizes unterstützt, können Sie die Ergebnisse einschränken, indem Sie die **Filter** -Eigenschaft des **Recordset** -Objekts verwenden.  
  
 Verwenden Sie die **Filter** -Eigenschaft, um Datensätze in einem **Recordset** -Objekt selektiv auszulagern. Das gefilterte **Recordset** wird zum aktuellen Cursor, was bedeutet, dass Datensätze, die die **Filter** Kriterien nicht erfüllen, im **Recordset** erst verfügbar sind, wenn der **Filter** entfernt wurde. Andere Eigenschaften, die Werte auf Grundlage des aktuellen Cursors zurückgeben, sind betroffen, wie z. b. **AbsolutePosition**, **AbsolutePage**, **RecordCount**und **PageCount**. Dies liegt daran, dass beim Festlegen der **Filter** Eigenschaft auf einen bestimmten Wert der aktuelle Datensatz in den ersten Datensatz verschoben wird, der den neuen Wert erfüllt.  
  
 Die **Filter** -Eigenschaft nimmt ein Variant-Argument an. Dieser Wert stellt eine von drei Methoden für die Verwendung der **Filter** Eigenschaft dar: eine Kriterienzeichenfolge, eine **filtergroupum** -Konstante oder ein Array von Lesezeichen. Weitere Informationen finden Sie unter Filtern mit einer Kriterienzeichenfolge, Filtern mit einer Konstanten und Filtern mit Lesezeichen weiter unten in diesem Thema.  
  
> [!NOTE]
>  Wenn Sie die Daten kennen, die Sie auswählen möchten, ist es in der Regel effizienter, ein **Recordset** mit einer SQL-Anweisung zu öffnen, die das Resultset effektiv filtert, anstatt sich auf die **Filter** -Eigenschaft zu verlassen.  
  
 Um einen Filter aus einem **Recordset**zu entfernen, verwenden Sie die **adfilternone** -Konstante. Wenn die **Filter** -Eigenschaft auf eine Zeichenfolge der Länge 0 (null) festgelegt wird, hat dies dieselbe Auswirkung wie die Verwendung der **adfilternone** -Konstante.  
  
### <a name="filtering-with-a-criteria-string"></a>Filtern mit einer Kriterienzeichenfolge  
 Die Kriterienzeichenfolge besteht aus Klauseln in der Form *FieldName Operator Value* (z `"LastName = 'Smith'"` . b.). Sie können Verbund Klauseln erstellen, indem Sie einzelne Klauseln mit **and** (z. b. `"LastName = 'Smith' AND FirstName = 'John'"` ) und **or** (z. b `"LastName = 'Smith' OR LastName = 'Jones'"` .) verketten. Verwenden Sie die folgenden Richtlinien für Kriterien-Zeichen folgen:  
  
-   Der *Feldname* muss ein gültiger Feldname aus dem **Recordset**sein. Wenn der Feldname Leerzeichen enthält, müssen Sie den Namen in eckigen Klammern einschließen.  
  
-   Der *Operator* muss eine der folgenden sein: **\<**, **>** , **\<=**, **>=** , **<>** , **=** oder **like**.  
  
-   *Value* ist der Wert, mit dem die Feldwerte verglichen werden (z. b `'Smith'` `#8/24/95#` .,, `12.345` oder `$50.00` ). Verwenden Sie einfache Anführungszeichen (') mit Zeichen folgen und Nummern Zeichen ( `#` ) mit Datumsangaben. Für Zahlen können Sie Dezimaltrennzeichen, Dollarzeichen und wissenschaftliche Schreibweise verwenden. Wenn *Operator* der Operator **like**ist, kann *value* Platzhalter Zeichen verwenden. Nur das Sternchen ( \* ) und das Prozentzeichen (%) Platzhalter Zeichen sind zulässig, und Sie müssen das letzte Zeichen in der Zeichenfolge sein. Der *Wert* darf nicht NULL sein.  
  
    > [!NOTE]
    >  Wenn Sie einfache Anführungszeichen (') in den Filter *Wert*einschließen möchten, verwenden Sie zwei einfache Anführungszeichen, um eine zu repräsentieren. Wenn Sie z. b. nach " *o*" filtern möchten, sollte die Kriterienzeichenfolge lauten `"col1 = 'O''Malley'"` . Um einfache Anführungszeichen sowohl am Anfang als auch am Ende des Filter Werts einzuschließen, schließen Sie die Zeichenfolge in Nummern Zeichen (#) ein. Wenn Sie z. b. nach *' 1 '* filtern möchten, sollte die Kriterienzeichenfolge lauten `"col1 = #'1'#"` .  
  
 Es gibt keine Rangfolge zwischen **und** und **oder**. Klauseln können innerhalb von Klammern gruppiert werden. Sie können jedoch keine Klauseln gruppieren, die von einem **oder** verknüpft sind, und dann die Gruppe mit einem und wie folgt mit einer anderen-Klausel verknüpfen.  
  
```  
(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'  
```  
  
 Stattdessen erstellen Sie diesen Filter wie folgt.  
  
```  
(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')  
```  
  
 In einer **like** -Klausel können Sie einen Platzhalter am Anfang und am Ende des Musters (z. b. `LastName Like '*mit*'` ) oder nur am Ende des Musters (z `LastName Like 'Smit*'` . b.) verwenden.  
  
### <a name="filtering-with-a-constant"></a>Filtern mit einer Konstanten  
 Die folgenden Konstanten sind zum Filtern von **Recordsets**verfügbar.  
  
|Konstante|Beschreibung|  
|--------------|-----------------|  
|**adFilterAffectedRecords**|Filter zum Anzeigen nur der Datensätze, die vom letzten **Delete**-, **Resync**-, **Update Batch**-oder **CancelBatch** -Befehl betroffen sind.|  
|**adFilterConflictingRecords**|Filter zum Anzeigen der Datensätze, bei denen das letzte Batch Update nicht erfolgreich war.|  
|**adfilterfetchedrecords**|Filter zum Anzeigen der Datensätze im aktuellen Cache, d. h. die Ergebnisse des letzten Aufrufes zum Abrufen von Datensätzen aus der Datenbank.|  
|**adfilternone**|Entfernt den aktuellen Filter und stellt alle Datensätze für die Anzeige wieder her.|  
|**adfilterpdingrecords**|Filter zum Anzeigen nur von Datensätzen, die geändert wurden, aber noch nicht an den Server gesendet wurden. Gilt nur für den Batch Aktualisierungs Modus.|  
  
 Die Filter Konstanten vereinfachen das Auflösen einzelner Daten Satz Konflikte im Batch Aktualisierungs Modus, da Sie z. b. nur die Datensätze anzeigen können, die während des letzten **UpdateBatch** -Methoden Aufrufes betroffen waren, wie im folgenden Beispiel gezeigt.  
  
 `Attribute VB_Name = "modExaminingData"`  
  
### <a name="filtering-with-bookmarks"></a>Filtern mit Lesezeichen  
 Schließlich können Sie ein Variant-Array von Lesezeichen an die **Filter** -Eigenschaft übergeben. Der resultierende Cursor enthält nur die Datensätze, deren Lesezeichen an die-Eigenschaft übermittelt wurden. Im folgenden Codebeispiel wird ein Array von Lesezeichen aus den Datensätzen in einem **Recordset** erstellt, die im Feld *ProductName* die Zeichenfolge "B" aufweisen. Anschließend übergibt Sie das Array an die **Filter** -Eigenschaft und zeigt Informationen zum resultierenden gefilterten **Recordset**an.  
  
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
  
## <a name="creating-a-clone-of-a-recordset"></a>Erstellen eines Klons eines Recordsets  
 Verwenden Sie die **Clone** -Methode, um mehrere doppelte **Recordset** -Objekte zu erstellen, insbesondere, wenn Sie mehr als einen aktuellen Datensatz in einer bestimmten Gruppe von Datensätzen verwalten möchten. Die Verwendung der **Klon** Methode ist effizienter als das Erstellen und Öffnen eines neuen **Recordset** -Objekts mit der gleichen Definition wie das Original.  
  
 Der aktuelle Datensatz eines neu erstellten Klons ist ursprünglich auf den ersten Datensatz festgelegt. Der aktuelle Daten Satz Zeiger in einem geklonten **Recordset** ist nicht mit dem ursprünglichen oder umgekehrt synchronisiert. Sie können in jedem **Recordset**unabhängig navigieren.  
  
 Änderungen, die Sie an einem **Recordset** -Objekt vornehmen, sind unabhängig vom Cursortyp in allen Klonen sichtbar. Nachdem Sie jedoch die [Requery](../../../ado/reference/ado-api/requery-method.md) für das ursprüngliche **Recordset**ausgeführt haben, werden die Klone nicht mehr mit der ursprünglichen synchronisiert.  
  
 Durch das Schließen des ursprünglichen **Recordsets** werden seine Kopien nicht geschlossen, und das Schließen einer Kopie schließt das Original oder eine der anderen Kopien.  
  
 Sie können ein **Recordset** -Objekt nur Klonen, wenn es Lesezeichen unterstützt. Lesezeichen Werte sind austauschbar. Das heißt, dass sich ein Lesezeichen Verweis von einem **Recordset** -Objekt auf denselben Datensatz in jedem seiner Klone bezieht.
