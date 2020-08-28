---
description: RDS-Tutorial (VBScript)
title: RDS-Tutorial (VBScript) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- RDS tutorial [ADO], VBScript
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
author: rothja
ms.author: jroth
ms.openlocfilehash: c9d3876b358721c7d63b1bbbb0aca98c56721b83
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977851"
---
# <a name="rds-tutorial-vbscript"></a>RDS-Tutorial (VBScript)
Dies ist das RDS-Tutorial, das in Microsoft Visual Basic Scripting Edition geschrieben wurde. Eine Beschreibung des Zwecks dieses Tutorials finden Sie im RDS- [Tutorial](./rds-tutorial.md).  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 In diesem Tutorial [RDS. DataControl](../../reference/rds-api/datacontrol-object-rds.md) und [RDS. DataSpace](../../reference/rds-api/dataspace-object-rds.md) werden zur Entwurfszeit erstellt, d. h., Sie werden mit Objekt Tags wie folgt definiert: `<OBJECT>...</OBJECT>` . Sie können auch zur Laufzeit mit der Methode der Methode " [Methode (Methode)](../../reference/rds-api/createobject-method-rds.md) " erstellt werden. Beispielsweise **RDS. Das DataControl** -Objekt könnte wie folgt erstellt werden:  
  
```vb
Set DC = Server.CreateObject("RDS.DataControl")  
   <!-- RDS.DataControl -->  
   <OBJECT   
      ID="DC1" CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E33">  
   </OBJECT>  
  
   <!-- RDS.DataSpace -->  
   <OBJECT   
      ID="DS1" WIDTH=1 HEIGHT=1  
      CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
   </OBJECT>  
  
   <SCRIPT LANGUAGE="VBScript">  
  
   Sub RDSTutorial()  
   Dim DF1   
```  
  
## <a name="step-1---specify-a-server-program"></a>Schritt 1: Angeben eines Server Programms  
 VBScript kann den Namen des IIS-Webservers ermitteln, auf dem er ausgeführt wird, indem er auf die VBScript **Request. ServerVariables** -Methode zugreift, die für Active Server Seiten verfügbar ist:  
  
```vb
"https://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 Verwenden Sie für dieses Tutorial jedoch den imaginären Server "yourServer".  
  
> [!NOTE]
>  Achten Sie auf den Datentyp der **ByRef** -Argumente. Mit VBScript können Sie den Variablentyp nicht angeben, sodass Sie immer eine **Variante**übergeben müssen. Wenn Sie http verwenden, können Sie mit RDS eine Variante an eine Methode übergeben, die eine nicht-Variant erwartet, wenn Sie Sie mit **RDS aufrufen. DataSpace** -Objekt (Methode " [kreateobject](../../reference/rds-api/createobject-method-rds.md) "). Wenn Sie DCOM oder einen in-Process-Server verwenden, müssen Sie die Parametertypen auf den Client-und Server Seiten vergleichen, oder Sie erhalten den Fehler "Typkonflikt".  
  
```vb
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "https://yourServer")  
```  
  
## <a name="step-2a---invoke-the-server-program-with-rdsdatacontrol"></a>Schritt 2a: Rufen Sie das Serverprogramm mit RDS auf. DataControl  
 Dieses Beispiel zeigt lediglich einen Kommentar, der das Standardverhalten des **RDS veranschaulicht. DataControl** ist die Ausführung der angegebenen Abfrage.  
  
```vb
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="https://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial2A()  
   Dim RS  
   DC1.Refresh  
   Set RS = DC1.Recordset  
...  
```  
  
## <a name="step-2b---invoke-the-server-program-with-rdsserverdatafactory"></a>Schritt 2B: Aufrufen des Server Programms mit RDSServer. DataFactory  
  
## <a name="step-3---server-obtains-a-recordset"></a>Schritt 3: Server erhält ein Recordset  
  
## <a name="step-4---server-returns-the-recordset"></a>Schritt 4-Server gibt das Recordset zurück  
  
```vb
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5---datacontrol-is-made-usable-by-visual-controls"></a>Schritt 5: DataControl wird von visuellen Steuerelementen verwendet.  
  
```vb
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a---changes-are-sent-to-the-server-with-rdsdatacontrol"></a>Schritt 6a: Änderungen werden mit RDS an den Server gesendet. DataControl  
 Dieses Beispiel zeigt lediglich einen Kommentar, der veranschaulicht, wie **RDS ist. DataControl** führt Updates aus.  
  
```vb
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="https://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial6A()  
Dim RS  
DC1.Refresh  
...  
Set RS = DC1.Recordset  
' Edit the Recordset object...  
' The SERVER and CONNECT properties are already set from Step 2A.  
Set DC1.SourceRecordset = RS  
...  
DC1.SubmitChanges  
```  
  
## <a name="step-6b---changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>Schritt 6b: Änderungen werden mit RDSServer. DataFactory an den Server gesendet.  
  
```vb
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **Dies ist das Ende des Tutorials.**  
  
## <a name="see-also"></a>Weitere Informationen  
 [RDS-Tutorial](./rds-tutorial.md)