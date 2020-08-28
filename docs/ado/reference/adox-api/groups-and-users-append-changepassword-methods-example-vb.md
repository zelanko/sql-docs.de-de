---
description: Append- und ChangePassword-Methoden für Gruppen und Benutzer – Beispiel (VB)
title: Anfügen von Gruppen und Benutzern, ChangePassword-Methoden (Beispiel) (VB) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 824cf44560335152ac6079c4ff61f2177368447c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88984381"
---
# <a name="groups-and-users-append-changepassword-methods-example-vb"></a>Append- und ChangePassword-Methoden für Gruppen und Benutzer – Beispiel (VB)
In diesem Beispiel werden die [Append](./append-method-adox-groups.md) -Methode von [Gruppen](./groups-collection-adox.md)sowie die [Append](./append-method-adox-users.md) -Methode von [Benutzern](./users-collection-adox.md) veranschaulicht, indem dem System eine neue [Gruppe](./group-object-adox.md) und ein neuer [Benutzer](./user-object-adox.md) hinzugefügt werden. Die neue **Gruppe** wird an die **Groups** -Auflistung des neuen **Benutzers**angehängt. Folglich wird der neue **Benutzer** der **Gruppe**hinzugefügt. Außerdem wird die [ChangePassword](./changepassword-method-adox.md) -Methode verwendet, um das **Benutzer** Kennwort anzugeben.  
  
> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Append-Methode (ADOX-Gruppen)](./append-method-adox-groups.md)   
 [Append-Methode (ADOX-Benutzer)](./append-method-adox-users.md)   
 [Catalog-Objekt (ADOX)](./catalog-object-adox.md)   
 [ChangePassword-Methode (ADOX)](./changepassword-method-adox.md)   
 [Group-Objekt (ADOX)](./group-object-adox.md)   
 [Groups-Auflistung (ADOX)](./groups-collection-adox.md)   
 [User-Objekt (ADOX)](./user-object-adox.md)   
 [Users-Collection (ADOX)](./users-collection-adox.md)