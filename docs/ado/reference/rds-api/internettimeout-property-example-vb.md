---
description: InternetTimeout-Eigenschaft – Beispiel (VB)
title: InternetTimeout-Eigenschaft (Beispiel) (VB) | Microsoft-Dokumentation
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
- InternetTimeout property [ADO], Visual Basic example
ms.assetid: b35d2f4a-449c-4170-aab6-9ff88c890043
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b2d5e2b34c5a82d222ee7018d0751cb7ec5f092
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438942"
---
# <a name="internettimeout-property-example-vb"></a>InternetTimeout-Eigenschaft – Beispiel (VB)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 In diesem Beispiel wird die [InternetTimeout](../../../ado/reference/rds-api/internettimeout-property-rds.md) -Eigenschaft veranschaulicht, die für die Objekte [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) und [DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) vorhanden ist. In diesem Beispiel wird das **DataControl** -Objekt verwendet und der Timeout Wert auf 20 Sekunden festgelegt.  
  
```  
'BeginInternetTimeoutVB  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim dc As RDS.DataControl  
    Dim rst As ADODB.Recordset  
    Set dc = New RDS.DataControl  
  
    dc.Server = "https://MyServer"  
    dc.ExecuteOptions = 1  
    dc.FetchOptions = 1  
    dc.Connect = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    dc.SQL = "SELECT * FROM Authors"  
     ' Wait at least 20 seconds  
    dc.InternetTimeout = 200  
  
    dc.Refresh  
     ' Use another Recordset as a convenience  
    Set rst = dc.Recordset  
    Do While Not rst.EOF  
       Debug.Print rst!au_fname & " " & rst!au_lname  
       rst.MoveNext  
    Loop  
  
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
'EndInternetTimeoutVB  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [DataSpace-Objekt (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [InternetTimeout-Eigenschaft (RDS)](../../../ado/reference/rds-api/internettimeout-property-rds.md)


