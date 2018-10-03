---
title: Filter-Eigenschaft | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cede9be7c484d40c2220fc891779f7dfb6e5a8df
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762740"
---
# <a name="filter-property"></a>Filter-Eigenschaft
Gibt einen Filter für Daten in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte

Legt fest oder gibt einen **Variant** -Wert, der einen der folgenden Elemente enthalten kann:  
  
-   **Die Zeichenfolge Suchkriterien:** eine Zeichenfolge, bestehend aus einer oder mehreren einzelnen Klauseln, die mit verkettet **und** oder **OR** Operatoren.  
  
-   **Array von Lesezeichen:** ein Array von Lesezeichen mit eindeutigen Werten, die auf Datensätze in der **Recordset** Objekt.  
  
-   Ein [FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md) Wert.  
  
## <a name="remarks"></a>Hinweise

Verwenden der **Filter** Eigenschaft, um selektiv um Datensätze im Bildschirm ein **Recordset** Objekt. Die gefilterten **Recordset** wird der aktuelle Cursor. Andere Eigenschaften, die Werte zurückgeben, basierend auf dem aktuellen **Cursor** betroffen sind, z. B. [AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md), [AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md), [ RecordCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/recordcount-property-ado.md), und [PageCount-Eigenschaft (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md). Festlegen der **Filter** Eigenschaft auf einen bestimmten neuen Wert verschiebt den aktuellen Datensatz auf den ersten Eintrag, der den neuen Wert entspricht.
  
Die Zeichenfolge der Suchkriterien besteht aus der Klauseln in der Form *FieldName-Operator-Wert* (z. B. `"LastName = 'Smith'"`). Sie können zusammengesetzte Klauseln erstellen, durch die Verkettung der einzelnen Klauseln mit **und** (z. B. `"LastName = 'Smith' AND FirstName = 'John'"`) oder **OR** (z. B. `"LastName = 'Smith' OR LastName = 'Jones'"`). Verwenden Sie für Kriterienzeichenfolgen die folgenden Richtlinien:

-   *FieldName* muss ein gültiger Feldname aus der **Recordset**. Wenn der Name des Felds Leerzeichen enthält, müssen Sie den Namen in eckige Klammern einschließen.  
  
-   Operator muss eine der folgenden sein: \<, >, \<=, > =, <>, =, oder **wie**.  
  
-   Wert ist der Wert, mit denen Sie die Feldwerte vergleichen (z. B. 'Smith' #8/24/95-# 12.345 oder 50,00 $). Verwenden Sie einfache Anführungszeichen mit Zeichenfolgen und Nummernzeichen (#) mit Datumsangaben. Für Zahlen können Sie das Dezimaltrennzeichen, Dollarzeichen und wissenschaftliche Schreibweise. Wenn der Operator ist **wie**, Wert kann Platzhalter verwenden. Nur das Sternchen (*) und Prozentzeichen (%) Platzhalter sind zulässig, und sie müssen das letzte Zeichen in der Zeichenfolge sein. Wert darf nicht null sein.  
  
> [!NOTE]
>  Wenn einfache Anführungszeichen (') in den Filterwert einschließen möchten, verwenden Sie zwei einfache Anführungszeichen zum Darstellen einer. Z. B. um Malley filtern, die Zeichenfolge der Suchkriterien muss `"col1 = 'O''Malley'"`. Um einzelne Anführungszeichen am Anfang und Ende der Filterwert einzuschließen, schließen Sie die Zeichenfolge mit dem Nummernzeichen (#). Z. B. zum Filtern nach "1" die Zeichenfolge der Suchkriterien muss `"col1 = #'1'#"`.  
  
-   Es gibt keine Rangfolge zwischen und und. Klauseln können innerhalb von Klammern gruppiert werden. Jedoch kann nicht verknüpft oder Klauseln group und treten Sie der Gruppe klicken Sie dann mit einer anderen Klausel mit einer AND, wie im folgenden Codeausschnitt:  
 `(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'`  
  
-   Stattdessen würden Sie diesen Filter als erstellen.  
 `(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')`  
  
-   In einem **wie** -Klausel, können Sie einen Platzhalter am Anfang und Ende des Musters. Beispielsweise können Sie `LastName Like '*mit*'`. Oder mit **wie** können Sie einen Platzhalter nur am Ende des Musters. Beispiel: `LastName Like 'Smit*'`.  
  
 Die Filter-Konstanten erleichtern das zum Auflösen einzelner Datensatz Konflikte während der Modus "Batch-Update", sodass Sie anzeigen, z. B. nur die Datensätze, die während des letzten betroffen [UpdateBatch-Methode](../../../ado/reference/ado-api/updatebatch-method.md) Methodenaufruf.  
  
Festlegen der **Filter** -Eigenschaft selbst möglicherweise aufgrund eines Konflikts mit der zugrunde liegenden Daten. Dieser Fehler kann z. B. auftreten, wenn es sich bei ein Datensatz bereits von einem anderen Benutzer gelöscht wurde. In diesem Fall gibt der Anbieter Warnungen zurück, mit die [Fehler Auflistung (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md) -Auflistung, aber nicht die Ausführung des Programms angehalten wurde. Fehler bei der Ausführung tritt auf, nur dann, wenn Konflikte für alle angeforderten Datensätze bestehen. Verwenden der [Status-Eigenschaft (ADO Recordset)](../../../ado/reference/ado-api/status-property-ado-recordset.md) Eigenschaft, um Datensätze mit Konflikten zu suchen.  
  
Festlegen der **Filter** Eigenschaft, um eine Zeichenfolge der Länge 0 (null) ("") hat dieselbe Wirkung wie die Verwendung der **AdFilterNone** Konstanten.
  
Wenn die **Filter** Eigenschaft festgelegt ist, verschiebt die Position des aktuelle Datensatzes auf den ersten Eintrag in der gefilterten Teilmenge der Datensätze in der **Recordset**. Auf ähnliche Weise, wenn die **Filter** Eigenschaft deaktiviert ist, verschiebt die Position des aktuelle Datensatzes auf den ersten Eintrag in der **Recordset**.

Nehmen wir an, die eine **Recordset** auf ein Feld vom Typ variant, z. B. den Datentyp ' sql_variant ' basierend gefiltert wird. Fehler (DISP_E_TYPEMISMATCH oder 80020005) tritt auf, wenn die Untertypen von in die Zeichenfolge der Suchkriterien verwendeten Felder und Filter Werte nicht übereinstimmen. Nehmen wir beispielsweise an:

- Ein **Recordset** Objekt (Rs) enthält eine Spalte (C) von der Sql_variant-Typ.
- Und ein Feld in dieser Spalte den Wert 1 vom Typ I4 zugewiesen wurde. Die Zeichenfolge der Suchkriterien nastaven NA hodnotu `rs.Filter = "C='A'"` für das Feld.

Diese Konfiguration wird der Fehler während der Laufzeit. Allerdings `rs.Filter = "C=2"` angewendet werden, auf dem gleichen Feld kein Fehler erzeugt. Und das Feld aus der aktuellen Ressourceneintragssatz herausgefiltert wird.

Finden Sie unter den [Bookmark-Eigenschaft (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md) -Eigenschaft für eine Erläuterung der Lesezeichenwerte, die aus dem Sie ein Array mit der Filter-Eigenschaft erstellen können.

Nur Filter in Form von Kriterienzeichenfolgen den Inhalt einer dauerhaften betreffen **Recordset**. Ein Beispiel für eine Zeichenfolge der Suchkriterien ist `OrderDate > '12/31/1999'`. Filter erstellt, die mit einem Array von Lesezeichen oder mithilfe eines Werts aus der **FilterGroupEnum**, wirken sich nicht auf den Inhalt des beibehaltenen **Recordset**. Diese Regeln gelten für Recordsets, die mit einem clientseitigen oder serverseitigen Cursor erstellt wurde.
  
> [!NOTE]
>  Wenn Sie das Flag AdFilterPendingRecords anwenden, um einen gefilterten und geändert **Recordset** in den Batchmodus Update verwendet wird, die resultierenden **Recordset** ist leer, wenn die Filterung auf das Schlüsselfeld der basiert ein Tabelle mit einzelnen Schlüsseln und die Änderung wurde versucht, auf die Schlüsselfeldwerte. Die resultierenden **Recordset** werden nicht leer, wenn eine der folgenden Aussagen zutrifft:  
  
-   Die Filterung basiert auf nicht-Schlüsselfelder in einer Tabelle mit einzelnen Schlüsseln.  
  
-   Die Filterung basiert in allen Feldern in einer Tabelle mit mehreren Schlüsseln.  
  
-   Änderungen, die auf nicht-Schlüsselfelder in einer Tabelle mit einzelnen Schlüsseln vorgenommen wurden.  
  
-   Änderungen, die in allen Feldern in einer Tabelle mit mehreren Schlüsseln vorgenommen wurden.  
  
Der folgenden Tabelle werden die Auswirkungen der **AdFilterPendingRecords** in verschiedenen Kombinationen von Filterung und Änderungen. Die linke Spalte zeigt die möglichen Änderungen. Änderungen können auf die nicht als Schlüssel Felder, auf das Schlüsselfeld in einer Tabelle mit einzelnen Schlüsseln oder auf die wichtigsten Felder in einer Tabelle mit mehreren Schlüsseln vorgenommen werden. Die oberste Zeile enthält das Filterkriterium an. Filterung kann auf eines der Felder nicht sortiert das Schlüsselfeld in einer Tabelle oder eines der wichtigsten Felder in einer Tabelle mit mehreren Schlüsseln basieren. Die sich überschneidenden Zellen zeigen die Ergebnisse an. Ein **+** Pluszeichen (+) bedeutet, dass diese Anwendung **AdFilterPendingRecords** führt zu einer nicht leeren **Recordset**. Ein **-** Minuszeichen (-) bedeutet, dass eine leere **Recordset**.  
  
||Nicht-Schlüssel|Einzelner Schlüssel|Mehrere Schlüssel|
|-|--------------|----------------|-------------------|
|**Nicht-Schlüssel**|+|+|+|
|**Einzelner Schlüssel**|+|-|–|
|**Mehrere Schlüssel**|+|–|+|
|||||
  
## <a name="applies-to"></a>Gilt für

[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch

[Filter und RecordCount – Beispiel (VB)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vb.md)
[Filter und RecordCount – Beispiel (VC++)](../../../ado/reference/ado-api/filter-and-recordcount-properties-example-vc.md)
[Clear-Methode (ADO)](../../../ado/reference/ado-api/clear-method-ado.md) 
 [Optimieren dynamische Eigenschaft (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)
