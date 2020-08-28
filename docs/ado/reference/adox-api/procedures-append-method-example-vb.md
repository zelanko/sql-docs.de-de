---
description: Append-Methode für Prozeduren – Beispiel(VB)
title: Prozeduren Append-Methode (Beispiel) (VB) | Microsoft-Dokumentation
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
- Append method [ADOX], Visual Basic example
ms.assetid: ce83b966-474b-4f57-8eb9-370996dfc5c0
author: rothja
ms.author: jroth
ms.openlocfilehash: d757b2df05bd4f376bb7c6744fa75ac5453f83f6
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88983581"
---
# <a name="procedures-append-method-example-vb"></a>Append-Methode für Prozeduren – Beispiel(VB)
Der folgende Code veranschaulicht, wie ein [Befehls](../ado-api/command-object-ado.md) Objekt und die [Prozeduren](./procedures-collection-adox.md) -Auflistungs [Methode zum](./append-method-adox-procedures.md) Erstellen einer neuen Prozedur in der zugrunde liegenden Datenquelle verwendet werden.  
  
```  
' BeginCreateProcedureVB  
Sub Main()  
    On Error GoTo CreateProcedureError  
  
    Dim cnn As New ADODB.Connection  
    Dim cmd As New ADODB.Command  
    Dim prm As ADODB.Parameter  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Connection  
    cnn.Open _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Create the parameterized command (Microsoft Jet specific)  
    Set cmd.ActiveConnection = cnn  
    cmd.CommandText = "PARAMETERS [CustId] Text;" & _  
    "Select * From Customers Where CustomerId = [CustId]"  
  
    ' Open the Catalog  
    Set cat.ActiveConnection = cnn  
  
    ' Create the new Procedure  
    cat.Procedures.Append "CustomerById", cmd  
  
    'Clean  
    cnn.Close  
    Set cat = Nothing  
    Set cmd = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CreateProcedureError:  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCreateProcedureVB  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ActiveConnection-Eigenschaft (ADOX)](./activeconnection-property-adox.md)   
 [Append-Methode (ADOX-Prozeduren)](./append-method-adox-procedures.md)   
 [Catalog-Objekt (ADOX)](./catalog-object-adox.md)   
 [Procedure-Objekt (ADOX)](./procedure-object-adox.md)   
 [Procedures-Collection (ADOX)](./procedures-collection-adox.md)