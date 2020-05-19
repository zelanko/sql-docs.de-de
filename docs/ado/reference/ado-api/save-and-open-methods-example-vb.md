---
title: Beispiel für das Speichern und Öffnen von Methoden (VB) | Microsoft-Dokumentation
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
- Save method [ADO], Visual Basic example
- Open method [ADO]
ms.assetid: ddccdf58-9c57-4c9b-8b7f-0cf193f955fb
author: rothja
ms.author: jroth
ms.openlocfilehash: 37237094c3778fad9c45a2ccad3eebdce02a62bc
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755930"
---
# <a name="save-and-open-methods-example-vb"></a>Save- und Open-Methode – Beispiel (VB)
Diese drei Beispiele veranschaulichen, wie die [Save](../../../ado/reference/ado-api/save-method.md) -Methode und die [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode gleichzeitig verwendet werden können.  
  
 Nehmen wir an, dass Sie einen geschäftlichen Trip ausführen und eine Tabelle aus einer Datenbank aufnehmen möchten. Bevor Sie fortfahren, greifen Sie auf die Daten als [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) zu, und speichern Sie Sie in einem austauschen-Format. Wenn Sie das Ziel erreichen, greifen Sie als lokales, nicht verbundenes **Recordset**auf das **Recordset** zu. Sie nehmen Änderungen am **Recordset**vor und speichern es dann erneut. Wenn Sie zu Hause zurückkehren, stellen Sie erneut eine Verbindung mit der Datenbank her, und aktualisieren Sie Sie mit den Änderungen, die Sie auf dem Weg vorgenommen haben.  
  
 Greifen Sie zuerst auf die ***Autoren*** Tabelle zu, und speichern Sie Sie.  
  
```  
'BeginSaveVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstAuthors As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "SELECT au_id, au_lname, au_fname, city, phone FROM Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenDynamic, adLockOptimistic, adCmdText  
  
    'For sake of illustration, save the Recordset to a diskette in XML format  
    rstAuthors.Save "c:\Pubs.xml", adPersistXML  
  
    ' clean up  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    'clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndSaveVB  
```  
  
 An diesem Punkt haben Sie Ihr Ziel erreicht. Sie greifen auf die ***Autoren*** Tabelle als lokales, nicht verbundenes **Recordset**zu. Sie müssen über den **MSPersist** -Anbieter auf dem Computer verfügen, den Sie für den Zugriff auf die gespeicherte Datei verwenden, a:\pubs.Xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Und schließlich kehren Sie zu Home zurück. Aktualisieren Sie nun die Datenbank mit Ihren Änderungen.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Weitere Informationen zur Speicherung von Recordsets](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
