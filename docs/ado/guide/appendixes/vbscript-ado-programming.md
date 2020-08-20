---
description: VBScript-ADO-Programmierung
title: VBScript-ADO-Programmierung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- ADO, VBScript
- VBScript [ADO]
ms.assetid: 6aaaf6d0-1376-4473-bea6-b81f2645a9ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 8bea576e55537d2b4ee75fb8e7a0fcdebea4847e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453962"
---
# <a name="vbscript-ado-programming"></a>VBScript-ADO-Programmierung
## <a name="creating-an-ado-project"></a>Erstellen eines ADO-Projekts  
 Microsoft Visual Basic, die Skript Edition unterstützt keine Typbibliotheken, sodass Sie nicht auf ADO in Ihrem Projekt verweisen müssen. Folglich werden keine zugeordneten Features wie z. b. Befehlszeilen Vervollständigung unterstützt. Außerdem sind ADO-Enumerationskonstanten standardmäßig nicht in VBScript definiert.  
  
 ADO bietet Ihnen jedoch zwei Includedateien, die die folgenden Definitionen enthalten, die mit VBScript verwendet werden sollen:  
  
-   Verwenden Sie für die serverseitige Skripterstellung adovb. Inc, das standardmäßig im Ordner c:\Programme\Common files\system\ado\ installiert ist.  
  
-   Verwenden Sie für die Client seitige Skripterstellung adcvb. Inc, das standardmäßig im Ordner c:\Programme\Common files\system\msdac\ installiert ist.  
  
 Sie können entweder Konstante Definitionen aus diesen Dateien kopieren und in Ihre ASP-Seiten einfügen. Wenn Sie serverseitige Skripterstellung durchführen, kopieren Sie die Datei "Adovbs. Inc" in einen Ordner auf der Website, und verweisen Sie auf Ihre ASP-Seite wie folgt:  
  
```vb
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Erstellen von ADO-Objekten in VBScript  
 Sie können die **Dim** -Anweisung nicht verwenden, um einem bestimmten Typ in VBScript Objekte zuzuweisen. VBScript unterstützt außerdem nicht die **neue** Syntax, die in Visual Basic for Applications mit der **Dim** -Anweisung verwendet wird. Sie müssen **stattdessen den-** Funktions aufrufbefehl in der-Funktion verwenden:  
  
```vb
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>VBScript-Beispiele  
 Der folgende Code ist ein allgemeines Beispiel für die serverseitige VBScript-Programmierung in einer Active Server Page (ASP)-Datei:  
  
```vb
<%  @LANGUAGE="VBSCRIPT" %>  
<%  Option Explicit %>  
<!--#include File="adovbs.inc"-->  
<HTML>  
    <BODY BGCOLOR="White" topmargin="10" leftmargin="10">  
  
    <!-- Your ASP Code goes here -->  
<%  
Dim Source  
Dim Connect  
Dim Rs1  
  
Source = "SELECT * FROM Authors"  
Connect = "Provider=sqloledb;Data Source=srv;" & _  
    "Initial Catalog=Pubs;Integrated Security=SSPI;"  
  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
Rs1.Open Source, Connect, adOpenForwardOnly  
Response.Write("Success!")  
%>  
    </BODY>  
</HTML>  
```  
  
 Spezifischere VBScript-Beispiele sind in der ADO-Dokumentation enthalten. Weitere Informationen finden Sie unter [ADO-Code Beispiele in Microsoft Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Unterschiede zwischen VBScript und Visual Basic  
 Die Verwendung von ADO mit VBScript ähnelt der Verwendung von ADO mit Visual Basic in vielerlei Hinsicht, einschließlich der Verwendung der Syntax. Es gibt jedoch einige bedeutende Unterschiede:  
  
-   VBScript unterstützt nur den Variant-Datentyp, der unterschiedliche Datentypen enthalten kann. Sie können die benötigten Daten in einem Variant-Datentyp speichern, und die Daten funktionieren entsprechend der Umwandlung durch VBScript ordnungsgemäß. Er erkennt den von ADO benötigten Typ und konvertiert den Wert in der Variante entsprechend.  
  
-   In VBScript können Sie **bei \<label> fehlergoto** nicht verwenden.  
  
-   VBScript unterstützt einige der integrierten Visual Basic Funktionen wie **MsgBox**, **Date**und **ISNUMERIC**. Da VBScript jedoch eine Teilmenge Visual Basic ist, werden nicht alle integrierten Funktionen unterstützt. VBScript unterstützt z. b. die **Format** -und Datei-e/a-Funktionen nicht.
