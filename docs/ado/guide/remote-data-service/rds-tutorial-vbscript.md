---
title: RDS-Tutorial (VBScript) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- RDS tutorial [ADO], VBScript
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5384bfc186427231ed34e855e2fedc845aca6a66
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699646"
---
# <a name="rds-tutorial-vbscript"></a>RDS-Tutorial (VBScript)
Dies ist die RDS-Tutorial, in Microsoft Visual Basic Scripting Edition geschrieben. Eine Beschreibung des Zwecks dieses Tutorials finden Sie unter den [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md).  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 In diesem Tutorial [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) und [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) erstellt zur Entwurfszeit - d. h. sie definiert sind mit Objekttags, wie folgt: `<OBJECT>...</OBJECT>`. Sie können auch erstellt werden, zur Laufzeit mit der [CreateObject-Methode (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md) Methode. Z. B. die **RDS. DataControl** Objekt wie folgt erstellt werden konnte:  
  
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
  
## <a name="step-1---specify-a-server-program"></a>Schritt 1: Serverprogramm angeben  
 VBScript kann der Name des im IIS-Webserver ausgeführt wird für den Zugriff auf die VBScript ermitteln **Request.ServerVariables** verfügbare Methode zum Active Server Pages:  
  
```vb
"https://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 Für dieses Tutorial müssen Sie allerdings verwenden Sie die imaginären Server, "Ihr Server".  
  
> [!NOTE]
>  Achten Sie darauf, den Datentyp der **ByRef** Argumente. VBScript ist nicht möglich, die den Variablentyp, angeben, damit Sie immer übergeben müssen eine **Variant**. Bei Verwendung von HTTP RDS können Sie eine Variante an eine Methode übergeben, die einen anderen Typ erwartet, wenn Sie es mit Aufrufen der **RDS. DataSpace** Objekt [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) Methode. Wenn DCOM oder in-Process-Server verwenden, müssen Sie die Parametertypen an den Client und Server Seiten entsprechen, oder wird die Fehlermeldung "Typenkonflikt".  
  
```vb
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "https://yourServer")  
```  
  
## <a name="step-2a---invoke-the-server-program-with-rdsdatacontrol"></a>Schritt 2a: Aufrufen des Programms mit RDS. DataControl  
 In diesem Beispiel wird lediglich zur Veranschaulichung, dass das Standardverhalten der **RDS. DataControl** besteht darin, die angegebene Abfrage auszuführen.  
  
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
  
## <a name="step-2b---invoke-the-server-program-with-rdsserverdatafactory"></a>Schritt 2 b: Serverprogramm mit RDSServer.DataFactory aufrufen  
  
## <a name="step-3---server-obtains-a-recordset"></a>Schritt 3: Server erhält ein Recordset  
  
## <a name="step-4---server-returns-the-recordset"></a>Schritt 4: Server gibt das Recordset  
  
```vb
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5---datacontrol-is-made-usable-by-visual-controls"></a>Schritt 5: DataControl wird durch visuelle Steuerelemente nutzbar gemacht.  
  
```vb
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a---changes-are-sent-to-the-server-with-rdsdatacontrol"></a>Schritt 6a: Änderungen werden mit RDS an den Server gesendet. DataControl  
 In diesem Beispiel dient lediglich zur Veranschaulichung wie die **RDS. DataControl** führt Updates.  
  
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
  
## <a name="step-6b---changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>Schritt 6 b: Änderungen an den Server mit RDSServer.DataFactory gesendet werden  
  
```vb
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **Dies ist das Ende des Tutorials.**  
  
## <a name="see-also"></a>Siehe auch  
 [RDS-Tutorial](../../../ado/guide/remote-data-service/rds-tutorial.md)   
