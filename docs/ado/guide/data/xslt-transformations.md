---
title: XSLT-Transformationen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XSLT transformations in ADO
ms.assetid: 1a46196e-839f-4734-a59e-2c64609ffb9e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59b00a521624759af8f73a94f75c4a74101b1937
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839678"
---
# <a name="xslt-transformations"></a>XSLT-Transformationen
XSLT kann auf den generierten XML-Code, um ihn in ein anderes Format zu transformieren angewendet werden. Grundlegendes zu XML-Format in ADO hilft bei der Entwicklung von XSLT-Vorlagen, die es in ein benutzerfreundlicheres Format transformiert werden können.  
  
 Beispielsweise wissen Sie, dass jede Zeile des Recordsets als Element innerhalb des Elements Rs: Daten Z: Zeile gespeichert wird. Auf ähnliche Weise wird jedes Feld des Recordset-Objekts als ein Attribut / Wert-Paar für dieses Element gespeichert.  
  
## <a name="remarks"></a>Hinweise  
 Die folgende XSLT-Skript kann angewendet werden, dem XML-Code im vorherigen Abschnitt gezeigt, um ihn in eine HTML-Tabelle transformieren, die im Browser angezeigt werden:  
  
```  
<?xml version="1.0" encoding="ISO-8859-1"?>  
<html xmlns:xsl="http://www.w3.org/TR/WD-xsl">  
<body STYLE="font-family:Arial, helvetica, sans-serif; font-size:12pt; background-color:white">  
<table border="1" style="table-layout:fixed" width="600">  
  <col width="200"></col>  
  <tr bgcolor="teal">  
    <th><font color="white">CustomerId</font></th>  
    <th><font color="white">CompanyName</font></th>  
    <th><font color="white">ContactName</font></th>  
  </tr>  
<xsl:for-each select="xml/rs:data/z:row">  
  <tr bgcolor="navy">  
    <td><font color="white"><xsl:value-of select="@CustomerID"/></font></td>  
    <td><font color="white"><xsl:value-of select="@CompanyName"/></font></td>  
    <td><font color="white"><xsl:value-of select="@ContactName"/></font></td>   
  </tr>  
</xsl:for-each>  
</table>  
</body>  
</html>  
```  
  
 Die XSLT-Datei konvertiert, den XML-Stream, die von der ADO speichern-Methode generiert, das in einer HTML-Tabelle, die jedes Feld des Recordset-Objekts zusammen mit einer Überschrift der Tabelle angezeigt wird. Tabellenüberschriften und Zeilen werden auch verschiedene Schriftarten und Farben zugewiesen.  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
