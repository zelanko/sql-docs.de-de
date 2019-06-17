---
title: Speichern und öffnen Sie die Methode – Beispiel (VB) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 32ed7e6240f5f9622bfcb80e2f05a633fcaf2fdc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711636"
---
# <a name="save-and-open-methods-example-vb"></a>Save- und Open-Methode – Beispiel (VB)
Diese drei Beispielen wird gezeigt, wie die [speichern](../../../ado/reference/ado-api/save-method.md) und [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methoden gemeinsam verwendet werden können.  
  
 Angenommen Sie, Sie sind im Begriff auf einer Geschäftsreise und auf eine Tabelle aus einer Datenbank ausführen möchten. Bevor Sie fortfahren, Sie greifen auf die Daten als eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) und speichern Sie ihn in einem Formular austauschen. Wenn Sie sich an Ihr Ziel eingehen, Zugriff auf die **Recordset** als lokales, getrennt **Recordset**. Nehmen Sie Änderungen an der **Recordset**, und speichern Sie es erneut. Schließlich, wenn Sie auf Startseite zurückkehren, Sie erneut eine Verbindung mit der Datenbank her und aktualisieren Sie es mit den Änderungen, die Sie unterwegs vorgenommen.  
  
 Zuerst Zugriff auf und speichern Sie die ***Autoren*** Tabelle.  
  
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
  
 An diesem Punkt haben Sie am Ziel angekommen. Greifen Sie auf die ***Autoren*** Tabelle als eine lokale, getrennt **Recordset**. Sie benötigen die **MSPersist** Anbieter auf dem Computer, die Sie verwenden die gespeicherte Datei, den Zugriff auf a:\Pubs.xml.  
  
```  
Attribute VB_Name = "Save"  
```  
  
 Anschließend wird der Rückgabewert Startseite. Aktualisieren Sie die Datenbank jetzt mit Ihren Änderungen.  
  
```  
Attribute VB_Name = "Save"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Open Sie-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Recordset Object (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Weitere Informationen zur Recordset-Beibehaltung](../../../ado/guide/data/more-about-recordset-persistence.md)   
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
