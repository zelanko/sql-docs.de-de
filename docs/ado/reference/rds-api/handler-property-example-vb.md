---
title: Beispiel für Handlereigenschaft (VB) | Microsoft-Dokumentation
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
- Handler property [ADO], Visual Basic example
ms.assetid: 9664f9a6-65fc-4e7f-be3d-3e4b501b558a
author: rothja
ms.author: jroth
ms.openlocfilehash: 829059639c182fa607ccb9ffe62658705500692d
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82751983"
---
# <a name="handler-property-example-vb"></a>Handler-Eigenschaft – Beispiel (VB)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 In diesem Beispiel wird die Eigenschaft " [RDS DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Object [Handler](../../../ado/reference/rds-api/handler-property-rds.md) " veranschaulicht. (Weitere Informationen finden Sie unter [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md) .)  
  
 Angenommen, die folgenden Abschnitte in der Parameterdatei "msdfmap. ini" befinden sich auf dem Server:  
  
```  
[connect AuthorDataBase]  
Access=ReadWrite  
Connect="DSN=Pubs"  
[sql AuthorById]  
SQL="SELECT * FROM Authors WHERE au_id = ?"  
```  
  
 Der Code sieht wie folgt aus. Der Befehl, der der [SQL](../../../ado/reference/rds-api/sql-property.md) -Eigenschaft zugewiesen ist, entspricht dem ***AuthorById*** -Bezeichner und ruft eine Zeile für den Autor Michael \ Leary ab. Die **DataControl** -Objekt **Recordset** -Eigenschaft wird einem getrennten [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt ausschließlich als Codierungs Zweck zugewiesen.  
  
```  
'BeginHandlerVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim dc As New DataControl  
    Dim rst As ADODB.Recordset  
  
    dc.Handler = "MSDFMAP.Handler"  
    dc.ExecuteOptions = 1  
    dc.FetchOptions = 1  
    dc.Server = "https://MyServer"  
    dc.Connect = "Data Source=AuthorDataBase"  
    dc.SQL = "AuthorById('267-41-2394')"  
    dc.Refresh                  'Retrieve the record  
    Set rst = dc.Recordset      'Use another Recordset as a convenience  
    Debug.Print "Author is '" & rst!au_fname & " " & rst!au_lname & "'"  
  
    ' clean up  
    If rst.State = adStateOpen Then rst.Close  
    Set rst = Nothing  
    Set dc = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
    Set dc = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndHandlerVB  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Handler-Eigenschaft (RDS)](../../../ado/reference/rds-api/handler-property-rds.md)


