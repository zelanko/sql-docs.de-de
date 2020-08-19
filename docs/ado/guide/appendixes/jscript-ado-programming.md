---
description: JScript-ADO-Programmierung
title: JScript-ADO-Programmierung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- JScript programming in ADO
- ADO, JScript programming
ms.assetid: 62273658-0fe7-4aac-b4d8-f725e6baf043
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f1cad0a2717bb652759a7c8b0d60efc4b3f4541
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444562"
---
# <a name="jscript-ado-programming"></a>JScript-ADO-Programmierung
## <a name="creating-an-ado-project"></a>Erstellen eines ADO-Projekts  
 Microsoft JScript unterstützt keine Typbibliotheken, sodass Sie nicht auf ADO in Ihrem Projekt verweisen müssen. Folglich werden keine zugeordneten Features wie z. b. Befehlszeilen Vervollständigung unterstützt. Außerdem sind ADO-Enumerationskonstanten standardmäßig nicht in JScript definiert.  
  
 ADO bietet Ihnen jedoch zwei Includedateien, die die folgenden Definitionen enthalten, die mit JScript verwendet werden sollen:  
  
-   Verwenden Sie für die serverseitige Skripterstellung die Datei "adojavas. Inc", die in den Ordnern der ADO-Bibliothek installiert ist.  
  
-   Verwenden Sie für die Client seitige Skripterstellung Adcjavas. Inc, das in den Ordnern der ADO-Bibliothek installiert ist.  
  
 Sie können entweder Konstante Definitionen aus diesen Dateien kopieren und in Ihre ASP-Seiten einfügen. Wenn Sie serverseitige Skripterstellung durchlaufen, kopieren Sie die Datei adojavas. Inc in einen Ordner auf der Website, und verweisen Sie auf Ihre ASP-Seite wie folgt:  
  
```javascript
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Erstellen von ADO-Objekten in JScript  
 Sie müssen **stattdessen den-** Funktions aufrufbefehl in der-Funktion verwenden:  
  
```javascript
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>JScript-Beispiel  
 Der folgende Code ist ein allgemeines Beispiel für die serverseitige JScript-Programmierung in einer Active Server Page (ASP)-Datei, die ein **Recordset** -Objekt öffnet:  
  
```javascript
<%  @LANGUAGE="JScript" %>  
<!--#include File="adojavas.inc"-->  
<HTML>  
<BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
<%  
var Source = "SELECT * FROM Authors";  
var Connect =  "Provider=sqloledb;Data Source=srv;" +  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
var Rs1 = Server.CreateObject( "ADODB.Recordset.2.5" );  
Rs1.Open(Source,Connect,adOpenForwardOnly);  
Response.Write("Success!");  
%>  
</BODY>  
</HTML>  
```
