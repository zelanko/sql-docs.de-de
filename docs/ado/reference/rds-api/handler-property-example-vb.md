---
title: Handler-Eigenschaft – Beispiel (VB) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c87dcf67e7da0c9ff0abf3aac7676a508a7bcd10
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51601390"
---
# <a name="handler-property-example-vb"></a>Handler-Eigenschaft – Beispiel (VB)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Dieses Beispiel zeigt die [RDS DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt [Handler](../../../ado/reference/rds-api/handler-property-rds.md) Eigenschaft. (Finden Sie unter [DataFactory-Anpassung](../../../ado/guide/remote-data-service/datafactory-customization.md) Weitere Details.)  
  
 Nehmen Sie an, dass die folgenden Abschnitte in der Parameterdatei "Msdfmap.ini", auf dem Server gespeichert sind:  
  
```  
[connect AuthorDataBase]  
Access=ReadWrite  
Connect="DSN=Pubs"  
[sql AuthorById]  
SQL="SELECT * FROM Authors WHERE au_id = ?"  
```  
  
 Ihr Code sieht folgendermaßen aus. Der Befehl zugewiesen der [SQL](../../../ado/reference/rds-api/sql-property.md) Eigenschaft entspricht der ***AuthorById*** Bezeichner und ruft eine Zeile für den Autor Michael O'Leary. Die **DataControl** Objekt **Recordset** -Eigenschaft zugewiesen wird, einem nicht verbundenen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt einfacherer Schreiben von Code.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Handler-Eigenschaft (RDS)](../../../ado/reference/rds-api/handler-property-rds.md)


