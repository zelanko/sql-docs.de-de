---
description: DataFactory-Objekt, Abfragemethode und CreateObject-Methode – Beispiel (VBScript)
title: Erstellen eines RDSServer. DataFactory-Objekts mithilfe von "|" (VBScript) | Microsoft-Dokumentation
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
- DataFactory object [ADO], VBScript example
- CreateObject method [ADO], VBScript example
- Query method [ADO], VBScript example
ms.assetid: b4e2844a-120a-4513-860b-f1b6e4b5dda4
author: rothja
ms.author: jroth
ms.openlocfilehash: 53c9d3161126a1728335c132fc7886b49297f2cb
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88768489"
---
# <a name="datafactory-object-query-method-and-createobject-method-example-vbscript"></a>DataFactory-Objekt, Abfragemethode und CreateObject-Methode – Beispiel (VBScript)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 In diesem Beispiel wird ein [RDSServer. DataFactory](./datafactory-object-rdsserver.md) -Objekt mithilfe der Methode " [kreateobject](./createobject-method-rds.md) " des [RDS erstellt. DataSpace](./dataspace-object-rds.md) -Objekt. Um dieses Beispiel zu testen, schneiden Sie diesen Code zwischen den \<Body> \</Body> Tags und in ein normales HTML-Dokument aus, und nennen Sie ihn " **datafactor yvb. ASP**". Das ASP-Skript identifiziert Ihren Server.  
  
```  
<!-- BeginDataFactoryVBS -->  
<HTML>  
<HEAD>  
<!--use the following META tag instead of adovbs.inc-->  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<META name="VI60_DefaultClientScript" Content="VBScript">  
  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<TITLE>DataFactory Object, Query Method, and   
CreateObject Method Example (VBScript)</TITLE>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</HEAD>  
<BODY>  
<h1>DataFactory Object, Query Method, and   
CreateObject Method Example (VBScript)</h1>  
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Using Query Method of RDSServer.DataFactory</H3>  
  
<!-- RDS.DataSpace  ID RDS1-->  
<OBJECT ID="RDS1" WIDTH=1 HEIGHT=1  
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
</OBJECT>  
  
<!-- RDS.DataControl with parameters   
set at run time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDS WIDTH=1 HEIGHT=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDS>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="FirstName"></SPAN></TD>  
    <TD><SPAN DATAFLD="LastName"></SPAN></TD>  
  </TR>  
</TBODY>      
</TABLE>  
  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run">  
<BR>  
<H4>Click Run -    
The <i>CreateObject</i> Method of the RDS.DataSpace Object Creates   
an instance of the RDSServer.DataFactory;   
The <i>Query</i> Method of the RDSServer.DataFactory is used  
to bring back a Recordset. </H4>  
  
<Script Language="VBScript">  
  
    Dim rdsDF  
    Dim strServer  
    Dim strCnxn  
    Dim strSQL  
  
    strServer = "https://<%=Request.ServerVariables("SERVER_NAME")%>"  
    strCnxn = "Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';"  
    strSQL = "Select FirstName, LastName from Employees"  
  
    Sub Run_OnClick()  
  
        ' Create RDSServer.DataFactory Object  
        Dim rs  
        ' Get Recordset  
        Set DF = RDS1.CreateObject("RDSServer.DataFactory", strServer)  
        Set rs = DF.Query(strCnxn, strSQL)  
        ' Set parameters of RDS.DataControl at Run Time  
        RDS.Server = strServer  
        RDS.SQL = strSQL  
        RDS.Connect = strCnxn  
        RDS.Refresh  
  
    End Sub  
</Script>  
  
</BODY>  
</HTML>  
<!-- EndDataFactoryVBS -->  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Methode "kreateobject" (RDS)](./createobject-method-rds.md)   
 [DataFactory-Objekt (RDSServer)](./datafactory-object-rdsserver.md)   
 [DataSpace-Objekt (RDS)](./dataspace-object-rds.md)   
 [Query-Methode (RDS)](./query-method-rds.md)