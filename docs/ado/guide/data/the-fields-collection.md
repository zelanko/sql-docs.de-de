---
description: Die Fields-Collection
title: Die Fields-Auflistung | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 580ded2e3f2539d484d2a60c85adca56ac8e3ac1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452752"
---
# <a name="the-fields-collection"></a>Die Fields-Collection
Die **Fields** -Auflistung ist eine der systemeigenen ADO-Auflistungen. Eine Auflistung ist eine geordnete Menge von Elementen, auf die als Einheit verwiesen werden kann. Weitere Informationen zu ADO-Auflistungen finden Sie [unter ADO-Objektmodell](../../../ado/guide/data/ado-objects-and-collections.md).  
  
 Die **Fields** -Auflistung enthält ein **Feld** Objekt für jedes Feld (Spalte) im **Recordset**. Wie alle ADO-Auflistungen verfügt er über **count** -und **Item** -Eigenschaften sowie über **Append** -und **Refresh** -Methoden. Außerdem gibt es die Methoden **CancelUpdate**, **Delete**, **Resync**und **Update** , die für andere ADO-Auflistungen nicht verfügbar sind.  
  
## <a name="examining-the-fields-collection"></a>Untersuchen der Fields-Auflistung  
 Sehen Sie sich die **Fields** -Auflistung des in diesem Abschnitt eingeführten Beispiel- **Recordsets** an. Das **Recordset** für das Beispiel wurde von der SQL-Anweisung abgeleitet.  
  
```  
SELECT ProductID, ProductName, UnitPrice FROM Products WHERE CategoryID = 7  
```  
  
 Daher sollten Sie feststellen, dass die **Recordset Fields** -Auflistung drei Felder enthält.  
  
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
  
 Mit diesem Code wird lediglich die Anzahl von **Feld** Objekten in **der Fields** -Auflistung mithilfe der **count** -Eigenschaft bestimmt, und die Auflistung wird durchlaufen, und der Wert der **Name** -Eigenschaft wird für jedes **Feld** Objekt zurückgegeben. Sie können viele weitere **Feld** Eigenschaften verwenden, um Informationen zu einem Feld zu erhalten. Weitere Informationen zum Abfragen eines **Felds**finden Sie [unter dem Feld Objekt](../../../ado/guide/data/the-field-object.md).  
  
## <a name="counting-columns"></a>Zählen von Spalten  
 Die **count** -Eigenschaft gibt die tatsächliche Anzahl von **Feld** Objekten in der **Fields** -Auflistung zurück. Da die Nummerierung für Member einer Auflistung mit Null beginnt, sollten Sie immer Code Schleifen programmieren, die mit dem nullmember beginnen und mit dem Wert der **count** -Eigenschaft minus 1 enden. Wenn Sie Microsoft Visual Basic verwenden und die Mitglieder einer Auflistung durchlaufen möchten, ohne die **count** -Eigenschaft zu überprüfen, verwenden Sie die **for each-... Nächster** Befehl.  
  
 Wenn die **count** -Eigenschaft 0 (null) ist, sind keine Objekte in der Auflistung vorhanden.  
  
## <a name="getting-to-the-field"></a>Gelangen zum Feld  
 Wie bei jeder ADO-Auflistung ist die **Item** -Eigenschaft die Standard Eigenschaft der Auflistung. Er gibt das einzelne **Feld** Objekt zurück, das durch den an ihn über gebenden Namen oder Index angegeben wird. Daher sind die folgenden Anweisungen für das Beispiel- **Recordset**gleichwertig:  
  
```  
objField = objRecordset.Fields.Item("ProductID")  
objField = objRecordset.Fields("ProductID")  
objField = objRecordset.Fields.Item(0)  
objField = objRecordset.Fields(0)  
```  
  
 Wenn diese Methoden gleichwertig sind, was am besten ist? Das ist unterschiedlich. Die Verwendung eines Indexes zum Abrufen eines **Felds** aus der Auflistung ist schneller, da es direkt auf das **Feld** zugreift, ohne eine Zeichen folgen Suche durchführen zu müssen. Andererseits muss die Reihenfolge der **Felder** in der Auflistung bekannt sein, und wenn sich die Reihenfolge ändert, muss der Verweis auf den Index des **Felds** immer dann geändert werden, wenn er auftritt. Obwohl etwas langsamer ist, ist die Verwendung des **Feld** namens flexibler, da Sie nicht von der Reihenfolge der **Felder** in der Auflistung abhängig ist.  
  
## <a name="using-the-refresh-method"></a>Verwenden der Refresh-Methode  
 Anders als bei einigen anderen ADO-Auflistungen hat die Verwendung der **Refresh** -Methode für die **Fields** -Auflistung keinen sichtbaren Effekt. Zum Abrufen von Änderungen aus der zugrunde liegenden Datenbankstruktur müssen Sie entweder die **Requery** -Methode verwenden oder, wenn das **Recordset** -Objekt Lesezeichen nicht unterstützt, die Methode " **muvefirst** ", die bewirkt, dass der Befehl erneut für den Anbieter ausgeführt wird.  
  
## <a name="adding-fields-to-a-recordset"></a>Hinzufügen von Feldern zu einem Recordset  
 Die **Append** -Methode wird verwendet, um einem **Recordset**Felder hinzuzufügen.  
  
 Sie können die **Append** -Methode verwenden, um ein **Recordset** Programm gesteuert zu fabrizieren, ohne eine Verbindung mit einer Datenquelle zu öffnen. Ein Laufzeitfehler tritt auf, wenn die **Append** -Methode für die **Fields** -Auflistung eines geöffneten **Recordsets** oder für ein **Recordset** aufgerufen wird, in dem die **ActiveConnection** -Eigenschaft festgelegt wurde. Sie können Felder nur an ein **Recordset** anfügen, das nicht geöffnet ist und noch keine Verbindung mit einer Datenquelle hergestellt hat. Zum Angeben von Werten für die neu angefügten **Felder**muss das **Recordset** jedoch zuerst geöffnet werden.  
  
 Entwickler benötigen häufig einen Ort, um einige Daten temporär zu speichern, oder Sie möchten, dass einige Daten so agieren, als ob Sie von einem Server stammen, damit Sie in einer Benutzeroberfläche an der Datenbindung teilnehmen können. ADO (in Verbindung mit dem [Microsoft-Cursor Dienst für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)) ermöglicht es dem Entwickler, ein leeres Recordsetobjekt zu erstellen, indem Spalten Informationen angegeben und **Open**aufgerufen wird. **Recordset** Im folgenden Beispiel werden drei neue Felder an ein neues **Recordset** -Objekt angehängt. Anschließend wird das **Recordset** geöffnet, zwei neue Datensätze werden hinzugefügt, und das **Recordset** wird in einer Datei gespeichert. (Weitere Informationen zur **Festlegung von Recordsets** finden Sie unter [aktualisieren und](../../../ado/guide/data/updating-and-persisting-data.md)beibehalten von Daten.)  
  
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
  
 Die Verwendung der **Fields-Append** -Methode unterscheidet sich zwischen dem **Recordset** -Objekt und dem **Datensatz** -Objekt. Weitere Informationen zum **Datensatz** -Objekt finden Sie unter [Datensätze und Streams](../../../ado/guide/data/records-and-streams.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Herstellen hierarchischer Recordsets](../../../ado/guide/data/fabricating-hierarchical-recordsets.md)
