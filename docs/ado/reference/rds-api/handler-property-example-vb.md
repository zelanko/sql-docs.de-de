---
description: Handler-Eigenschaft – Beispiel (VB)
title: Beispiel für Handlereigenschaft (VB) | Microsoft-Dokumentation
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
- Handler property [ADO], Visual Basic example
ms.assetid: 9664f9a6-65fc-4e7f-be3d-3e4b501b558a
author: rothja
ms.author: jroth
ms.openlocfilehash: 56227da17b5c302a6682db905fe3f397c5e9e3fd
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91722150"
---
# <a name="handler-property-example-vb"></a>Handler-Eigenschaft – Beispiel (VB)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
 In diesem Beispiel wird die Eigenschaft " [RDS DataControl](./datacontrol-object-rds.md) Object [Handler](./handler-property-rds.md) " veranschaulicht. (Weitere Informationen finden Sie unter [DataFactory-Anpassung](../../guide/remote-data-service/datafactory-customization.md) .)  
  
 Angenommen, die folgenden Abschnitte in der Parameterdatei Msdfmap.ini befinden sich auf dem Server:  
  
```  
[connect AuthorDataBase]  
Access=ReadWrite  
Connect="DSN=Pubs"  
[sql AuthorById]  
SQL="SELECT * FROM Authors WHERE au_id = ?"  
```  
  
 Der Code sieht wie folgt aus. Der Befehl, der der [SQL](./sql-property.md) -Eigenschaft zugewiesen ist, entspricht dem ***AuthorById*** -Bezeichner und ruft eine Zeile für den Autor Michael \ Leary ab. Die **DataControl** -Objekt **Recordset** -Eigenschaft wird einem getrennten [Recordset](../ado-api/recordset-object-ado.md) -Objekt ausschließlich als Codierungs Zweck zugewiesen.  
  
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
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)   
 [Handler-Eigenschaft (RDS)](./handler-property-rds.md)