---
title: Filter Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Filter
helpviewer_keywords:
- Filter property
ms.assetid: 80263a7a-5d21-45d1-84fc-34b7a9be4c22
author: rothja
ms.author: jroth
ms.openlocfilehash: bcc1b02671d73e9056babb417ba2fa22a4d6cf0e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762541"
---
# <a name="filter-property"></a>Filter-Eigenschaft
Gibt einen Filter für Daten in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)an.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte

Legt einen **Variant** -Wert fest oder gibt einen Wert zurück, der eines der folgenden Elemente enthalten kann:  
  
-   **Kriterien Zeichenfolge:** Eine Zeichenfolge, die aus einer oder mehreren einzelnen Klauseln besteht, die mit den Operatoren **and** oder **or** verkettet sind.  
  
-   **Array von Lesezeichen:** Ein Array von eindeutigen Lesezeichen Werten, die auf Datensätze im **Recordset** -Objekt zeigen.  
  
-   Ein [filtergroupum](../../../ado/reference/ado-api/filtergroupenum.md) -Wert.  
  
## <a name="remarks"></a>Bemerkungen

Verwenden Sie die **Filter** -Eigenschaft, um Datensätze in einem **Recordset** -Objekt selektiv auszulagern. Das gefilterte **Recordset** wird zum aktuellen Cursor. Andere Eigenschaften, die Werte auf Grundlage des aktuellen **Cursors** zurückgeben, sind betroffen, wie z. b. die [AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md), die [AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md), die [RecordCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md)und die [PageCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md). Wenn die **Filter** -Eigenschaft auf einen bestimmten neuen Wert festgelegt wird, wird der aktuelle Datensatz in den ersten Datensatz verschoben, der den neuen Wert erfüllt.
  
Die Kriterienzeichenfolge besteht aus Klauseln in der Form *FieldName-Operator-Value* (z `"LastName = 'Smith'"` . b.). Sie können Verbund Klauseln erstellen, indem Sie einzelne Klauseln mit **and** (z. b. `"LastName = 'Smith' AND FirstName = 'John'"` ) oder **or** (z. b `"LastName = 'Smith' OR LastName = 'Jones'"` .) verketten. Verwenden Sie für Kriterienzeichenfolgen die folgenden Richtlinien:

-   Der *Feldname* muss ein gültiger Feldname aus dem **Recordset**sein. Wenn der Feldname Leerzeichen enthält, müssen Sie den Namen in eckigen Klammern einschließen.  
  
-   Der Operator muss eine der folgenden sein: \< , >, \< =, >=,  <>, = oder **like**.  
  
-   Value ist der Wert, mit dem Sie die Feldwerte vergleichen (z. b. "Smith", #8/24/95 #, 12,345 oder $50,00). Verwenden Sie einfache Anführungszeichen mit Zeichen folgen und Nummern Zeichen (#) mit Datumsangaben. Für Zahlen können Sie Dezimaltrennzeichen, Dollarzeichen und wissenschaftliche Schreibweise verwenden. Wenn der Operator **like**ist, kann der Wert Platzhalter verwenden. Nur das Sternchen (*) und das Prozentzeichen (%) Platzhalter sind zulässig, und Sie müssen das letzte Zeichen in der Zeichenfolge sein. Wert darf nicht NULL sein.  
  
> [!NOTE]
>  Wenn Sie einfache Anführungszeichen (') in den Filter Wert einschließen möchten, verwenden Sie zwei einfache Anführungszeichen, um eine zu repräsentieren. Wenn Sie z. b. nach "o" filtern möchten, sollte die Kriterienzeichenfolge lauten `"col1 = 'O''Malley'"` . Um einfache Anführungszeichen sowohl am Anfang als auch am Ende des Filter Werts einzuschließen, müssen Sie die Zeichenfolge mit Zeichen Zeichen (#) einschließen. Wenn Sie z. b. nach ' 1 ' filtern möchten, sollte die Kriterienzeichenfolge lauten `"col1 = #'1'#"` .  
  
-   Es gibt keine Rangfolge zwischen und und oder. Klauseln können innerhalb von Klammern gruppiert werden. Sie können jedoch keine Klauseln gruppieren, die von einem oder verknüpft sind, und dann die Gruppe mit einem und verknüpfen, wie im folgenden Code Ausschnitt:  
 `(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   Stattdessen erstellen Sie diesen Filter als  
 `(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   In einer **like** -Klausel können Sie am Anfang und am Ende des Musters einen Platzhalter verwenden. Sie können z. B. `LastName Like '*mit*'` verwenden. Oder mit **like** können Sie einen Platzhalter nur am Ende des Musters verwenden. Beispiel: `LastName Like 'Smit*'`.  
  
 Die Filter Konstanten vereinfachen das Auflösen einzelner Daten Satz Konflikte im Batch Aktualisierungs Modus, da Sie z. b. nur die Datensätze anzeigen können, die während des letzten [UpdateBatch-Methoden](../../../ado/reference/ado-api/updatebatch-method.md) Aufrufes aufgetreten sind.  
  
Das Festlegen der **Filter** Eigenschaft selbst kann aufgrund eines Konflikts mit den zugrunde liegenden Daten fehlschlagen. Dieser Fehler kann z. b. auftreten, wenn ein Datensatz bereits von einem anderen Benutzer gelöscht wurde. In einem solchen Fall gibt der Anbieter Warnungen an die Auflistung der [Fehler Auflistung (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md) zurück, hält die Ausführung des Programms jedoch nicht an. Ein Fehler zur Laufzeit tritt nur auf, wenn für alle angeforderten Datensätze Konflikte vorliegen. Verwenden Sie die Eigenschaft [Status Eigenschaft (ADO Recordset)](../../../ado/reference/ado-api/status-property-ado-recordset.md) , um Datensätze mit Konflikten zu suchen.  
  
Wenn die **Filter** -Eigenschaft auf eine Zeichenfolge der Länge 0 (null) festgelegt wird, hat dies dieselbe Auswirkung wie die Verwendung der **adfilternone** -Konstante.
  
Wenn die **Filter** -Eigenschaft festgelegt ist, wechselt die aktuelle Daten Satz Position zum ersten Datensatz in der gefilterten Teilmenge der Datensätze im **Recordset**. Wenn die **Filter** -Eigenschaft gelöscht wird, wechselt die aktuelle Daten Satz Position entsprechend in den ersten Datensatz im **Recordset**.

Angenommen, ein **Recordset** wird anhand eines Felds eines Varianten Typs gefiltert, z. b. vom Typ sql_variant. Ein Fehler (DISP_E_TYPEMISMATCH oder 80020005) tritt auf, wenn die Untertypen der Feld-und Filter Werte, die in der Kriterienzeichenfolge verwendet werden, nicht übereinstimmen. Nehmen Sie beispielsweise Folgendes an:

- Ein **Recordset** -Objekt (RS) enthält eine Spalte (C) des sql_variant Typs.
- Und einem Feld dieser Spalte wurde der Wert 1 des I4-Typs zugewiesen. Die Kriterienzeichenfolge ist für das Feld auf festgelegt `rs.Filter = "C='A'"` .

Diese Konfiguration erzeugt den Fehler zur Laufzeit. `rs.Filter = "C=2"`Das Anwenden auf das gleiche Feld führt jedoch nicht zu einem Fehler. Und das Feld wird aus dem aktuellen Daten Satz Satz herausgefiltert.

Eine Erläuterung der Bookmark-Werte, aus denen Sie ein Array erstellen können, das mit der Filter-Eigenschaft verwendet werden kann, finden Sie unter der Eigenschaft " [Bookmark Property (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md) ".

Nur Filter in Form von Kriterienzeichenfolgen beeinflussen den Inhalt eines permanenten **Recordsets**. Ein Beispiel für eine Kriterienzeichenfolge ist `OrderDate > '12/31/1999'` . Filter, die mit einem Array von Lesezeichen erstellt wurden oder einen Wert aus dem **filtergroupum**verwenden, wirken sich nicht auf den Inhalt des beibehaltenen **Recordsets**aus. Diese Regeln gelten für Recordsets, die entweder mit Client seitigen oder serverseitigen Cursorn erstellt wurden.
  
> [!NOTE]
>  Wenn Sie das Flag adfilterbatdingrecords auf ein gefiltertes und geändertes **Recordset** im Batch Aktualisierungs Modus anwenden, ist das resultierende **Recordset** leer, wenn die Filterung auf dem Schlüsselfeld einer eingebundenen Tabelle basiert und die Änderungen an den Schlüssel Feldwerten vorgenommen wurden. Das resultierende **Recordset** ist nicht leer, wenn eine der folgenden Aussagen zutrifft:  
  
-   Die Filterung basiert auf nicht Schlüsselfeldern in einer einzelnen Schlüssel Tabelle.  
  
-   Die Filterung basiert auf Feldern in einer mehrfach Schlüssel Tabelle.  
  
-   An nicht Schlüsselfeldern in einer eingebundenen Tabelle wurden Änderungen vorgenommen.  
  
-   An Feldern in einer mehrfach Schlüssel Tabelle wurden Änderungen vorgenommen.  
  
In der folgenden Tabelle werden die Auswirkungen von **adfilterpdingrecords** in verschiedenen Kombinationen aus Filtern und Änderungen zusammengefasst. In der linken Spalte werden die möglichen Änderungen angezeigt. Es können Änderungen an jedem der nicht-Schlüsselfelder, im Schlüsselfeld in einer eingebundenen Tabelle oder in einem der Schlüsselfelder in einer mehrfach Schlüssel Tabelle vorgenommen werden. Die obere Zeile zeigt das Filter Kriterium an. Das Filtern kann auf einem der nicht-Schlüsselfelder, dem Schlüsselfeld in einer eingebundenen Tabelle oder einem der Schlüsselfelder in einer mehrfach Schlüssel Tabelle basieren. Die sich überschneidenden Zellen zeigen die Ergebnisse an. Ein **+** Pluszeichen bedeutet, dass das Anwenden von **adfilterpdingrecords** ein nicht leeres **Recordset**ergibt. Ein **-** Minuszeichen bedeutet ein leeres **Recordset**.  
  
||Nicht Schlüssel|Einzelner Schlüssel|Mehrere Schlüssel|
|-|--------------|----------------|-------------------|
|**Nicht Schlüssel**|+|+|+|
|**Einzelner Schlüssel**|+|-|–|
|**Mehrere Schlüssel**|+|–|+|
|||||
  
## <a name="applies-to"></a>Gilt für

[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen

[Filter-und RecordCount-Eigenschaften (Beispiel) (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md) 
 [Filter-und RecordCount-Eigenschaften (Beispiel) (VC + +)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md) 
 [Clear-Methode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md) 
 [Optimieren von Eigenschaften-Dynamic (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)
