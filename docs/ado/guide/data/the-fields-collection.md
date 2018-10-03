---
title: Der Fields-Sammlung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Field object [ADO], fields collection
- Fields collection [ADO]
ms.assetid: 574cf36e-e5f5-403b-983c-749ef93c108f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4bd852423ed285165b4d699b391807b9a748f9b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730676"
---
# <a name="the-fields-collection"></a>Die Fields-Collection
Die **Felder** Collection ist eines der systeminternen des ADO-Auflistungen. Eine Sammlung ist eine geordnete Menge von Elementen, die auf die als Einheit verwiesen werden kann. Weitere Informationen zu Sammlungen mit ADO finden Sie unter [der ADO-Objektmodell](../../../ado/guide/data/ado-objects-and-collections.md).  
  
 Die **Felder** Auflistung enthält ein **Feld** -Objekt für jedes Feld (Spalte) in der **Recordset**. Wie alle ADO-Sammlungen, hat es **Anzahl** und **Element** Eigenschaften als auch **Append** und **aktualisieren** Methoden. Sie hat auch **CancelUpdate**, **löschen**, **Resync**, und **Update** -Methoden, die nicht mit anderen Sammlungen ADO verfügbar sind.  
  
## <a name="examining-the-fields-collection"></a>Untersuchen der Fields-Sammlung  
 Betrachten Sie die **Felder** Auflistung des Beispiels **Recordset** eingeführt, die in diesem Abschnitt. Das Beispiel **Recordset** abgeleitet wurde, aus der SQL-Anweisung  
  
```  
SELECT ProductID, ProductName, UnitPrice FROM Products WHERE CategoryID = 7  
```  
  
 Daher werden Sie feststellen, dass die **Recordset Fields** Auflistung enthält drei Felder.  
  
```  
'BeginWalkFields  
    Dim objFields As ADODB.Fields  
    Dim intLoop As Integer  
  
    objRs.Open strSQL, strConnStr, adOpenForwardOnly, adLockReadOnly, adCmdText  
  
    Set objFields = objRs.Fields  
  
    For intLoop = 0 To (objFields.Count - 1)  
        Debug.Print objFields.Item(intLoop).Name  
    Next  
'EndWalkFields  
```  
  
 Dieser Code einfach bestimmt die Anzahl der **Feld** Objekte in der **Felder** Sammlung mithilfe der **Anzahl** -Eigenschaft und durchläuft die Auflistung, der Wert von die **Namen** -Eigenschaft für jedes **Feld** Objekt. Sie können viele weitere **Feld** Eigenschaften zum Abrufen von Informationen über ein Feld. Weitere Informationen zum Abfragen einer **Feld**, finden Sie unter [Field-Objekt](../../../ado/guide/data/the-field-object.md).  
  
## <a name="counting-columns"></a>Zählen von Spalten  
 Wie zu erwarten, die **Anzahl** Eigenschaft gibt die tatsächliche Anzahl der **Feld** Objekte in der **Felder** Auflistung. Für Mitglieder einer Sammlung Nummerierung beginnt bei 0 (null), Sie sollten code stets Schleifen, beginnend mit dem Element 0 (null) und endet mit dem Wert der **Anzahl** -Eigenschaft minus 1. Wenn Sie Microsoft Visual Basic verwenden und, die Elemente einer Auflistung durchlaufen, ohne Überprüfung möchten der **Anzahl** Eigenschaft verwenden der **für jede... Nächste** Befehl.  
  
 Wenn die **Anzahl** -Eigenschaft ist 0 (null), es sind keine Objekte in der Auflistung.  
  
## <a name="getting-to-the-field"></a>Einführung in das Feld ""  
 Wie bei jeder ADO-Auflistung, die **Element** -Eigenschaft ist die Standardeigenschaft der Auflistung. Gibt die einzelnen **Feld** durch seinen Namen angegebenen Objekt oder an sie übergebenen Index. Aus diesem Grund sind die folgenden Anweisungen für das Beispiel entsprechende **Recordset**:  
  
```  
objField = objRecordset.Fields.Item("ProductID")  
objField = objRecordset.Fields("ProductID")  
objField = objRecordset.Fields.Item(0)  
objField = objRecordset.Fields(0)  
```  
  
 Wenn diese Methoden äquivalent sind, ist der beste? Es setzt. Verwenden einen Index zum Abrufen einer **Feld** aus der Auflistung ist schneller, da er greift auf die **Feld** direkt, ohne dass eine Suche durchführen. Andererseits, die Reihenfolge der **Felder** in der Auflistung muss bekannt sein, und wenn die Reihenfolge ändert, den Verweis auf die **des Felds** Index müssen geändert werden, wo er auftritt. Obwohl etwas langsamer, mit dem Namen des der **Feld** ist flexibler, da es in der Größenordnung von abhängig sind, nicht die **Felder** in der Auflistung.  
  
## <a name="using-the-refresh-method"></a>Verwenden die Refresh-Methode  
 Im Gegensatz zu einigen anderen ADO Auflistungen mit den **aktualisieren** Methode für die **Felder** Auflistung wirkt sich nicht sichtbar. Um Änderungen aus der zugrunde liegenden Datenbankstruktur abzurufen, müssen Sie verwenden entweder die **Requery** -Methode, oder, wenn die **Recordset** Objekt unterstützt keine Lesezeichen die **MoveFirst**-Methode, die führt den Befehl für den Anbieter erneut ausgeführt werden.  
  
## <a name="adding-fields-to-a-recordset"></a>Hinzufügen von Feldern zu einem Recordset  
 Die **Append** Methode dient zum Hinzufügen von Feldern zu einer **Recordset**.  
  
 Können Sie die **Append** Methode zum Erstellen einer **Recordset** programmgesteuert, ohne eine Verbindung mit einer Datenquelle öffnen. Wird ein Laufzeitfehler auftreten, wenn die **Append** Methode wird aufgerufen, auf die **Felder** Auflistung eines geöffneten **Recordset** oder auf eine **Recordset** in denen die **ActiveConnection** -Eigenschaft festgelegt wurde. Können Sie nur für Felder Anfügen einer **Recordset** , ist nicht geöffnet und noch nicht mit einer Datenquelle verbunden wurde. Allerdings zum Angeben von Werten für das neu angefügte **Felder**, **Recordset** muss zuerst geöffnet werden.  
  
 Entwickler benötigen häufig eine Möglichkeit zum vorübergehend einige Daten zu speichern, oder möchten einige Daten zum Verhalten, als ob er einen Server stammt, damit sie bei der Datenbindung in einer Benutzeroberfläche teilnehmen kann. ADO (in Verbindung mit der [Microsoft Cursor Service für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)) kann der Entwickler zum Erstellen einer leeres **Recordset** Objekt, indem die Spalteninformationen angeben und Aufrufen **Öffnen**. Im folgenden Beispiel werden drei neue Felder zu einem neuen angefügt **Recordset** Objekt. Die **Recordset** geöffnet wird, zwei neue Einträge hinzugefügt werden, und die **Recordset** wird in einer Datei beibehalten. (Weitere Informationen zu **Recordset** Persistenz finden Sie unter [wird aktualisiert und Beibehalten von Daten](../../../ado/guide/data/updating-and-persisting-data.md).)  
  
```  
'BeginFabricate  
    Dim objRs As ADODB.Recordset  
    Set objRs = New ADODB.Recordset  
  
    With objRs.Fields  
        .Append "StudentID", adChar, 11, adFldUpdatable  
        .Append "FullName", adVarChar, 50, adFldUpdatable  
        .Append "PhoneNmbr", adVarChar, 20, adFldUpdatable  
    End With  
  
    With objRs  
        .Open  
  
        .AddNew  
        .Fields(0) = "123-45-6789"  
        .Fields(1) = "John Doe"  
        .Fields(2) = "(425) 555-5555"  
        .Update  
  
        .AddNew  
        .Fields(0) = "123-45-6780"  
        .Fields(1) = "Jane Doe"  
        .Fields(2) = "(615) 555-1212"  
        .Update  
    End With  
  
    objRs.Save App.Path & "FabriTest.adtg", adPersistADTG  
  
    objRs.Close  
'EndFabricate  
```  
  
 Die Verwendung der **Felder anzufügen** Methode unterscheidet sich zwischen den **Recordset** Objekt und die **Datensatz** Objekt. Weitere Informationen zu den **Datensatz** Objekt, finden Sie unter [Datensätze und Datenströme](../../../ado/guide/data/records-and-streams.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Fabricating Hierarchical Recordsets (Herstellen hierarchischer Recordsets)](../../../ado/guide/data/fabricating-hierarchical-recordsets.md)
