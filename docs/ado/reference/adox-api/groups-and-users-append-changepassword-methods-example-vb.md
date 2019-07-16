---
title: Gruppen und Benutzer Append, ChangePassword Methods Example (VB) | Microsoft-Dokumentation
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
- ChangePassword method [ADOX], Visual Basic example
- Append method [ADOX], Visual Basic example
ms.assetid: c9426757-9cdd-4a95-b506-d3d011569109
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2b384167358f578835256c0e3f7906db20cf5bb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966203"
---
# <a name="groups-and-users-append-changepassword-methods-example-vb"></a>Append- und ChangePassword-Methoden für Gruppen und Benutzer – Beispiel (VB)
Dieses Beispiel zeigt die [Append](../../../ado/reference/adox-api/append-method-adox-groups.md) -Methode der [Gruppen](../../../ado/reference/adox-api/groups-collection-adox.md), als auch die [Anfügen](../../../ado/reference/adox-api/append-method-adox-users.md) -Methode der [Benutzer](../../../ado/reference/adox-api/users-collection-adox.md) durch Hinzufügen einer neuen [Gruppe](../../../ado/reference/adox-api/group-object-adox.md) und ein neues [Benutzer](../../../ado/reference/adox-api/user-object-adox.md) an das System. Die neue **Gruppe** wird angefügt, um die **Gruppen** -Sammlung der neuen **Benutzer**. Daher ist die neue **Benutzer** hinzugefügt wird die **Gruppe**. Darüber hinaus die [ChangePassword](../../../ado/reference/adox-api/changepassword-method-adox.md) Methode dient zum Angeben der **Benutzer** Kennwort.  
  
> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.  
  
```  
' BeginGroupVB  
Sub Main()  
    On Error GoTo GroupXError  
  
    Dim cat As ADOX.Catalog  
    Dim usrNew As ADOX.User  
    Dim usrLoop As ADOX.User  
    Dim grpLoop As ADOX.Group  
  
    Set cat = New ADOX.Catalog  
  
    cat.ActiveConnection = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';" & _  
        "jet oledb:system database=" & _  
        "'system.mdw'"  
  
    With cat  
        'Create and append new group with a string.  
        .Groups.Append "Accounting"  
  
        ' Create and append new user with an object.  
        Set usrNew = New ADOX.User  
        usrNew.Name = "Pat Smith"  
        usrNew.ChangePassword "", "Password1"  
        .Users.Append usrNew  
  
        ' Make the user Pat Smith a member of the  
        ' Accounting group by creating and adding the  
        ' appropriate Group object to the user's Groups  
        ' collection. The same is accomplished if a User  
        ' object representing Pat Smith is created and  
        ' appended to the Accounting group Users collection  
        usrNew.Groups.Append "Accounting"  
  
        ' Enumerate all User objects in the  
        ' catalog's Users collection.  
        For Each usrLoop In .Users  
            Debug.Print "  " & usrLoop.Name  
            Debug.Print "    Belongs to these groups:"  
            ' Enumerate all Group objects in each User  
            ' object's Groups collection.  
            If usrLoop.Groups.Count <> 0 Then  
                For Each grpLoop In usrLoop.Groups  
                    Debug.Print "    " & grpLoop.Name  
                Next grpLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next usrLoop  
  
        ' Enumerate all Group objects in the default  
        ' workspace's Groups collection.  
        For Each grpLoop In .Groups  
            Debug.Print "  " & grpLoop.Name  
            Debug.Print "    Has as its members:"  
            ' Enumerate all User objects in each Group  
            ' object's Users collection.  
            If grpLoop.Users.Count <> 0 Then  
                For Each usrLoop In grpLoop.Users  
                    Debug.Print "    " & usrLoop.Name  
                Next usrLoop  
            Else  
                Debug.Print "    [None]"  
            End If  
        Next grpLoop  
  
        ' Delete new User and Group objects because this  
        ' is only a demonstration.  
        ' These two line are commented out because the sub "OwnersX" uses  
        ' the group "Accounting".  
'        .Users.Delete "Pat Smith"  
'        .Groups.Delete "Accounting"  
  
    End With  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set usrNew = Nothing  
    Exit Sub  
  
GroupXError:  
  
    Set cat = Nothing  
    Set usrNew = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndGroupVB  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Append-Methode (ADOX-Gruppen)](../../../ado/reference/adox-api/append-method-adox-groups.md)   
 [Append-Methode (ADOX-Benutzer)](../../../ado/reference/adox-api/append-method-adox-users.md)   
 [Katalogobjekt (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [ChangePassword-Methode (ADOX)](../../../ado/reference/adox-api/changepassword-method-adox.md)   
 [Group-Objekt (ADOX)](../../../ado/reference/adox-api/group-object-adox.md)   
 [Groups-Auflistung (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)   
 [User-Objekt (ADOX)](../../../ado/reference/adox-api/user-object-adox.md)   
 [Users-Auflistung (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)
