---
title: SQLServerNClob-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b063f191-175e-4430-aab7-d88907f4ebec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81bcb5406a491d0e7b73ec098b160008c1a11c4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795538"
---
# <a name="sqlservernclob-members"></a>SQLServerNClob-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  In den folgenden Tabellen sind die Elemente aufgeführt, die von der [SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine.  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
 Keine.  
  
## <a name="methods"></a>Methoden  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlservernclob.md)|Mit dieser Methode werden das **NCLOB**-Objekt sowie die von diesem verwendeten Ressourcen freigegeben.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|Ruft die **NCLOB** Wert festgelegt, durch die **java.sql.NClob** Objekts als ASCII-Datenstrom.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|Ruft die **NCLOB** Wert festgelegt, durch die **java.sql.NClob** Objekt.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|Ruft eine Kopie der angegebenen Teilzeichenfolge im ab der **NCLOB** Wert festgelegt, durch die **java.sql.NClob** Objekt.|  
|[length](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|Ruft die Anzahl der Zeichen in der **NCLOB** Wert festgelegt, durch die **java.sql.NClob** Objekt.|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|Ruft die Zeichenposition des angegebenen **java.sql.NClob** Objekt oder einer Teilzeichenfolge in der **java.sql.NClob** basierend auf der angegebenen Anfangsposition.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|Ruft einen Datenstrom ab, der verwendet wird, um ab der angegebenen Position ASCII-Zeichen in den **NCLOB**-Wert zu schreiben, der von diesem **java.sql.NClob**-Objekt dargestellt wird.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|Ruft einen Datenstrom ab, der verwendet wird, um ab der angegebenen Position einen Datenstrom von Unicode-Zeichen in den **NCLOB**-Wert zu schreiben, der von diesem **java.sql.NClob**-Objekt dargestellt wird.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|Schreibt das angegebene **Zeichenfolge** auf die **NCLOB** an der angegebenen Position ab.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|Kürzt den **NCLOB**-Wert auf die angegebene Länge.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von|Methoden|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
