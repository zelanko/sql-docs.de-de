---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64655ad666954b2fb63448cb1e55430dd6191491
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350464"
---
# <a name="jscript-ado-programming"></a>JScript-ADO-Programmierung
## <a name="creating-an-ado-project"></a>Erstellen eines ADO-Projekts  
 Microsoft JScript unterstützt keine-Typbibliotheken ist, benötigen Sie nicht auf ADO-Verweis in Ihrem Projekt. Daher werden keine zugehörigen Features wie z. B. die Vervollständigung der Befehlszeile unterstützt. Darüber hinaus sind ADO aufgezählt werden standardmäßig in JScript nicht definiert.  
  
 ADO bietet jedoch, dass Sie mit zwei Dateien, die die folgenden Definitionen mit JScript enthalten:  
  
-   Verwenden Sie für serverseitige Skripting Adojavas.inc, die in den Ordnern der ADO-Bibliothek installiert wird.  
  
-   Verwenden Sie für die clientseitige Skripting Adcjavas.inc, die in den Ordnern der ADO-Bibliothek installiert wird.  
  
 Sie können entweder kopieren und Einfügen von Konstantendefinitionen aus diesen Dateien in ASP-Seiten, oder wenn Sie serverseitige Skripts, ausführen Adojavas.inc-Datei in einen Ordner auf Ihrer Website kopieren und verweist auf sie aus der ASP-Seite wie folgt:  
  
```javascript
<!--#include File="adojavas.inc"-->  
```  
  
## <a name="creating-ado-objects-in-jscript"></a>Erstellen von ADO-Objekte in JScript  
 Verwenden Sie stattdessen die **CreateObject** Funktionsaufruf:  
  
```javascript
var Rs1;  
Rs1 = Server.CreateObject("ADODB.Recordset");  
```  
  
## <a name="jscript-example"></a>JScript-Beispiel  
 Der folgende Code ist ein allgemeines Beispiel JScript-serverseitige Programmierung in einer Active Server Page (ASP)-Datei, die geöffnet wird eine **Recordset** Objekt:  
  
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
