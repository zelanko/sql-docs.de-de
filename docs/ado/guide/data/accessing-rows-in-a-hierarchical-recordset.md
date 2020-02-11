---
title: Zugreifen auf Zeilen in einem hierarchischen Recordset | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: 25f1d2a1-6d5e-4457-aa07-5db5c75dee18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e73b2ca96cc5e7eb7683b72aa19fd59a318b8596
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926357"
---
# <a name="accessing-rows-in-a-hierarchical-recordset-example"></a>Zugreifen auf Zeilen in einem hierarchischen Recordset (Beispiel)
Das folgende Beispiel zeigt die erforderlichen Schritte für den Zugriff auf Zeilen in einem hierarchischen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md):

1.  **Recordset** -Objekte aus den Tabellen " **Authors** " und " **titleauthor** " sind durch die Autoren-ID verknüpft.

2.  Die äußere Schleife zeigt den vor-und Nachnamen, den Status und die Identifizierung jedes Autors an.

3.  Das angefügte **Recordset** für jede Zeile wird aus der [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung abgerufen und *rsttitleauthor*zugewiesen.

4.  Die innere Schleife zeigt vier Felder aus jeder Zeile im angefügten **Recordset**an.

 Die [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) -Eigenschaft ist zur Veranschaulichung auf **false** festgelegt, sodass Sie das Kapitel ändern in jeder Iterations Schleife der äußeren Schleife explizit sehen können. Um das Codebeispiel effizienter zu gestalten, können Sie die Zuweisung in Schritt 3 vor der ersten Zeile in Schritt 2 verschieben, sodass die Zuweisung nur einmal ausgeführt wird. Legen Sie dann die [StayInSync](../../../ado/reference/ado-api/stayinsync-property.md) -Eigenschaft auf **true**fest, damit *rsttitleauthor* implizit und automatisch in das entsprechende Kapitel wechselt, wenn *RST* zu einer neuen Zeile wechselt.

## <a name="example"></a>Beispiel

```
Sub datashape()
   Dim cnn As New ADODB.Connection
   Dim rst As New ADODB.Recordset
   Dim rstTitleAuthor As New ADODB.Recordset

   cnn.Provider = "MSDataShape"
   cnn.Open    "Data Provider=MSDASQL;" & _
               "Data Source=SRV;Integrated Security=SSPI;Database=Pubs"
' STEP 1
   rst.StayInSync = FALSE
   rst.Open    "SHAPE  {select * from authors} "  & _
               "APPEND ({select * from titleauthor} " & _
               "RELATE au_id TO au_id) AS chapTitleAuthor", _
               cnn
' STEP 2
   While Not rst.EOF
      Debug.Print    rst("au_fname"), rst("au_lname"), _
                     rst("state"), rst("au_id")
' STEP 3
      Set rstTitleAuthor = rst("chapTitleAuthor").Value
' STEP 4
      While Not rstTitleAuthor.EOF
         Debug.Print rstTitleAuthor(0), rstTitleAuthor(1), _
                     rstTitleAuthor(2), rstTitleAuthor(3)
         rstTitleAuthor.MoveNext
      Wend
      rst.MoveNext
   Wend
End Sub
```

## <a name="see-also"></a>Weitere Informationen
 [Übersicht über die Daten Strukturierung](../../../ado/guide/data/data-shaping-overview.md) [Field Object](../../../ado/reference/ado-api/field-object.md) [Fields Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md) [formal Shape Grammar](../../../ado/guide/data/formal-shape-grammar.md) [Microsoft Data Strukturierung Service for OLE DB (ADO Service Provider)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) [(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [erforderliche Anbieter für das Strukturieren von Daten strukturieren von](../../../ado/guide/data/required-providers-for-data-shaping.md) [](../../../ado/guide/data/shape-append-clause.md) [Form Befehlen in der allgemeinen](../../../ado/guide/data/shape-commands-in-general.md) [Form COMPUTE-Klausel](../../../ado/guide/data/shape-compute-clause.md) [Visual Basic for Applications Functions](../../../ado/guide/data/visual-basic-for-applications-functions.md)
