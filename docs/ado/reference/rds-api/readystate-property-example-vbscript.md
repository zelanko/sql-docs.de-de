---
title: ReadyState-Eigenschaft – Beispiel (VBScript) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ReadyState property [ADO], VBScript example
ms.assetid: e3e18da4-0511-4ece-a35d-699978bc28c6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b27a26eede798b8a8f8df9d76451125f042510a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963606"
---
# <a name="readystate-property-example-vbscript"></a>ReadyState-Eigenschaft – Beispiel (VBScript)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Das folgende Beispiel zeigt, wie Sie lesen die [ReadyState](../../../ado/reference/rds-api/readystate-property-rds.md) Eigenschaft der [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt zur Laufzeit in VBScript-Code. **ReadyState** ist eine schreibgeschützte Eigenschaft.  
  
 Klicken Sie zum Testen dieses Beispiels, schneiden, und fügen Sie diesen Code zwischen den \<Text > und \</Body > Tags in ein normales HTML-Dokument, und nennen Sie sie **RDSReadySt.asp**. Verwenden Sie **finden** suchen Sie die Datei Adovbs.inc, und fügen ihn in das Verzeichnis, das Sie verwenden möchten. ASP-Skript wird auf den Server identifiziert.  
  
```  
<!-- BeginReadyStateVBS -->  
<%@ Language=VBScript %>  
<!--#include file="adovbs.inc"-->  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>RDS.DataControl ReadyState Property</title>  
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
</head>  
  
<body>  
<H1>RDS.DataControl ReadyState Property</H1>  
<H2>RDS API Code Examples </H2>  
<HR>  
<!-- RDS.DataControl with parameters set at design time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID=RDS>  
   <PARAM NAME="SQL" VALUE="Select * from Orders">  
   <PARAM NAME="SERVER" VALUE="https://<%=Request.ServerVariables("SERVER_NAME")%>">  
   <PARAM NAME="CONNECT" VALUE="Provider=SQLOLEDB;Integrated Security=SSPI;Initial Catalog=Northwind">  
   <PARAM NAME="ExecuteOptions" VALUE="2">   
   <PARAM NAME="FetchOptions" VALUE="3">  
</OBJECT>  
  
<TABLE DATASRC=#RDS>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="OrderID"></SPAN></TD>  
  </TR>  
</TBODY>  
</TABLE>  
  
<Script Language="VBScript">  
  
   Sub Window_OnLoad  
  
      Select Case RDS.ReadyState  
         case 2   'adcReadyStateLoaded  
          MsgBox "Executing Query"  
         case 3   'adcReadyStateInteractive  
          MsgBox "Fetching records in background"  
         case 4   'adcReadyStateComplete  
          MsgBox "All records fetched"  
      End Select  
  
   End Sub  
</Script>  
  
</body>  
</html>  
<!-- EndReadyStateVBS -->  
```  
  
## <a name="see-also"></a>Siehe auch  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [ReadyState-Eigenschaft (RDS)](../../../ado/reference/rds-api/readystate-property-rds.md)


