---
description: GetObjectOwner- und SetObjectOwner-Methoden – Beispiel (VB)
title: Beispiel für die GetObjectOwner-und die-Methode von "seetobjectowner" (VB) Microsoft-Dokumentation
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
- SetObjectOwner method [ADOX], Visual Basic example
- GetObjectOwner method [ADOX], Visual Basic example
ms.assetid: e44ec3d4-42ae-447d-aaed-bdea53cb0cca
author: rothja
ms.author: jroth
ms.openlocfilehash: dc9a111b3315c7737229ec0240e5ee4ed6e406b9
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88770549"
---
# <a name="getobjectowner-and-setobjectowner-methods-example-vb"></a>GetObjectOwner- und SetObjectOwner-Methoden – Beispiel (VB)
In diesem Beispiel werden die [GetObjectOwner](./getobjectowner-method-adox.md) [-Methode](./setobjectowner-method.md) und die-Methode für die Methode "". In diesem Code wird davon ausgegangen, dass die Gruppen Buchhaltungs Gruppe vorhanden ist. (Weitere Informationen zum Hinzufügen dieser Gruppe zum System finden Sie im [Beispiel Gruppen und Benutzer anfügen, ChangePassword-Methoden Beispiel (VB)](./groups-and-users-append-changepassword-methods-example-vb.md) . Der Besitzer der Categories-Tabelle ist auf Accounting festgelegt.  
  
```  
' BeginOwnersVB  
Sub OwnersX()  
  
    Dim tblLoop As New ADOX.Table  
    Dim cat As New ADOX.Catalog  
    Dim strOwner As String  
  
    ' Open the Catalog.  
    cat.ActiveConnection = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=c:\Program Files\" & _  
        "Microsoft Office\Office\Samples\Northwind.mdb;" & _  
        "jet oledb:system database=" & _  
        "c:\Program Files\Microsoft Office\Office\system.mdw"  
  
    ' Print the original owner of Categories  
    strOwner = cat.GetObjectOwner("Categories", adPermObjTable)  
    Debug.Print "Owner of Categories: " & strOwner  
  
    ' Set the owner of Categories to Accounting  
    cat.SetObjectOwner "Categories", adPermObjTable, "Accounting"  
  
    ' List the owners of all tables and columns in the catalog.  
    For Each tblLoop In cat.Tables  
        Debug.Print "Table: " & tblLoop.Name  
        Debug.Print "   Owner: " & _  
            cat.GetObjectOwner(tblLoop.Name, adPermObjTable)  
    Next tblLoop  
  
    ' Restore the original owner of Categories  
    cat.SetObjectOwner "Categories", adPermObjTable, strOwner  
  
End Sub  
' EndOwnersVB  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Catalog-Objekt (ADOX)](./catalog-object-adox.md)   
 [GetObjectOwner-Methode (ADOX)](./getobjectowner-method-adox.md)   
 [SetObjectOwner-Methode](./setobjectowner-method.md)