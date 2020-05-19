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
author: rothja
ms.author: jroth
ms.openlocfilehash: 8556576656d4b6eb6ba5e38216a78074cd1f9fc4
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82748211"
---
# <a name="xslt-transformations"></a>XSLT-Transformationen
XSLT kann auf den generierten XML-Code angewendet werden, um ihn in ein anderes Format umzuwandeln. Wenn Sie das XML-Format in ADO verstehen, können Sie XSLT-Vorlagen entwickeln, die Sie in ein benutzerfreundliches Formular umwandeln können.  
  
 Beispielsweise wissen Sie, dass jede Zeile des Recordsets als z:row-Element im RS: Data-Element gespeichert wird. Ebenso wird jedes Feld des Recordsets als Attribut/Wert-Paar für dieses Element gespeichert.  
  
## <a name="remarks"></a>Bemerkungen  
 Das folgende XSLT-Skript kann auf den im vorherigen Abschnitt gezeigten XML-Code angewendet werden, um ihn in eine HTML-Tabelle umzuwandeln, die im Browser angezeigt werden soll:  
  
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
  
 XSLT konvertiert den XML-Stream, der von der ADO-Speichermethode generiert wurde, in eine HTML-Tabelle, in der jedes Feld des Recordsets zusammen mit einer Tabellen Überschrift angezeigt wird. Tabellen Überschriften und-Zeilen werden auch unterschiedliche Schriftarten und Farben zugewiesen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Datensätzen im XML-Format](../../../ado/guide/data/persisting-records-in-xml-format.md)
