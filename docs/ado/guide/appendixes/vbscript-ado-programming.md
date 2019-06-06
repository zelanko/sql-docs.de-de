---
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a9c13b532e1ac234c207fc70fe7578be341f72b4
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701124"
---
# <a name="vbscript-ado-programming"></a>VBScript-ADO-Programmierung
## <a name="creating-an-ado-project"></a>Erstellen eines ADO-Projekts  
 Microsoft Visual Basic, Scripting Edition unterstützt keine Typbibliotheken, damit Sie nicht ADO in Ihrem Projekt verweisen müssen. Daher werden keine zugehörigen Features wie z. B. die Vervollständigung der Befehlszeile unterstützt. Darüber hinaus sind ADO aufgezählt werden standardmäßig in VBScript nicht definiert.  
  
 ADO bietet jedoch, dass Sie mit zwei Dateien, die die folgenden Definitionen mit VBScript enthalten:  
  
-   Verwenden, Sie für serverseitige Skripting Adovbs.inc wird die im Ordner "c:\Programme\Microsoft Dateien\System\ADO\" standardmäßig installiert.  
  
-   Verwenden, Sie für die clientseitige Skripting Adcvbs.inc wird die im Ordner c:\Program Files\Common Files\System\msdac\ standardmäßig installiert.  
  
 Sie können entweder kopieren und Einfügen Konstantendefinitionen aus diesen Dateien in ASP-Seiten, oder, wenn Sie serverseitige Skripts, kopieren Sie Adovbs.inc-Datei in einen Ordner auf Ihrer Website, und verweisen Sie darauf der ASP-Seite wie folgt:  
  
```vb
<!--#include File="adovbs.inc"-->  
```  
  
## <a name="creating-ado-objects-in-vbscript"></a>Erstellen von ADO-Objekte in VBScript  
 Sie können keine der **Dim** Anweisung, um Objekte eines bestimmten Typs in VBScript zuweisen. VBScript unterstützt auch nicht die **neu** Syntax verwendet, mit der **Dim** -Anweisung in Visual Basic für Applikationen. Verwenden Sie stattdessen die **CreateObject** Funktionsaufruf:  
  
```vb
Dim Rs1  
Set Rs1 = Server.CreateObject( "ADODB.Recordset" )  
```  
  
## <a name="vbscript-examples"></a>Beispiele für VBScript  
 Der folgende Code ist ein allgemeines Beispiel VBScript-serverseitige Programmierung in einer Active Server Page (ASP)-Datei:  
  
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
  
 Genauere Beispiele für VBScript sind in der ADO-Dokumentation enthalten. Weitere Informationen finden Sie unter [ADO-Codebeispiele in Microsoft Visual Basic Scripting Edition](../../../ado/reference/ado-api/ado-code-examples-vbscript.md).  
  
## <a name="differences-between-vbscript-and-visual-basic"></a>Unterschiede zwischen VBScript und Visual Basic  
 Verwenden von ADO mit VBScript ähnelt der Verwendung von ADO mit Visual Basic in vielerlei Hinsicht einschließlich wie Syntax verwendet wird. Allerdings sind einige wesentliche Unterschiede vorhanden:  
  
-   VBScript unterstützt nur den Variant-Datentyp, der unterschiedliche Arten von Daten enthalten kann. Sie können die benötigten Daten in einen Variant-Datentyp speichern, und die Daten funktioniert entsprechend aufgrund der Umwandlung von VBScript ausgeführt. Erkennt den ADO erforderlichen Typ und den Wert in die Variante entsprechend konvertiert.  
  
-   Sie können keine **auf Fehler "GoTo" \<Label >** in VBScript.  
  
-   VBScript unterstützt einige der integrierten Visual Basic-Funktionen wie z. B. **Msgbox**, **Datum**, und **IsNumeric**. Da VBScript eine Teilmenge von Visual Basic ist, werden jedoch nicht alle integrierte Funktionen unterstützt. Z. B. VBScript unterstützt nicht die **Format** Funktion und die e/a-Funktionen.
