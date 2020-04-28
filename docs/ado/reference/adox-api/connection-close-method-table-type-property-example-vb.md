---
title: Connection Close-Methode, Table Type-Eigenschafts Beispiel (VB) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Close method [ADOX], Visual Basic example
- Type property [ADOX], Visual Basic example
ms.assetid: f88e7a3b-19ed-46e2-b2ce-3b611d9b8166
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4559a8d46852f37f2e828ce8f4abbd0e40845744
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67966705"
---
# <a name="connection-close-method-table-type-property-example-vb"></a>Connection Close-Methode, Table Type-Eigenschaft – Beispiel (VB)
Wenn die [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) -Eigenschaft auf **Nothing** festgelegt wird, sollte die Verbindung mit dem Katalog geschlossen werden. Zugeordnete Sammlungen sind leer. Alle Objekte, die aus Schema Objekten im Katalog erstellt wurden, sind verwaist. Alle Eigenschaften von Objekten, die zwischengespeichert wurden, sind weiterhin verfügbar, aber ein Versuch, Eigenschaften zu lesen, die einen-Anrufe an den Anbieter erfordern, schlägt fehl.  
  
```  
' BeginCloseConnectionVB  
Sub Main()  
    On Error GoTo CloseConnectionByNothingError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Set tbl = cat.Tables(0)  
    Debug.Print tbl.Type    ' Cache tbl.Type info  
    Set cat.ActiveConnection = Nothing  
    Debug.Print tbl.Type    ' tbl is orphaned  
    ' Previous line will succeed if this info was cached.  
    Debug.Print tbl.Columns(0).DefinedSize  
    ' Previous line will fail if this info has not been cached.  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CloseConnectionByNothingError:  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCloseConnectionVB  
```  
  
 Das Schließen eines [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekts, das zum Öffnen des Katalogs verwendet wurde, sollte dieselbe Auswirkung haben wie das Festlegen der **ActiveConnection** -Eigenschaft auf " **Nothing**".  
  
```  
Attribute VB_Name = "Connection"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ActiveConnection-Eigenschaft (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Catalog-Objekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Column-Objekt (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Columns-Auflistung (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Table-Objekt (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Tables-Auflistung (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type-Eigenschaft (Tabelle) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
