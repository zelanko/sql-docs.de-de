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
ms.openlocfilehash: 303742b8e7b7bf8221565e09cf23d2e18cdca8de
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67970948"
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
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlservernclob.md)|Ruft den **NCLOB**-Wert ab, der vom **java.sql.NClob**-Objekt als ASCII-Datenstrom festgelegt wurde|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlservernclob.md)|Ruft den **NCLOB**-Wert ab, der vom **java.sql.NClob**-Objekt festgelegt wurde|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlservernclob.md)|Ruft eine Kopie der angegebenen Teilzeichenfolge im vom **java.sql.NClob**-Objekt angegebenen **NCLOB**-Wert ab.|  
|[length](../../../connect/jdbc/reference/length-method-sqlservernclob.md)|Ruft die Anzahl der Zeichen im vom **java.sql.NClob**-Objekt angegebenen **NCLOB**-Wert ab.|  
|[position](../../../connect/jdbc/reference/position-method-sqlservernclob.md)|Ruft die Zeichenposition des angegebenen **java.sql.NClob**-Objekts oder der Teilzeichenfolge in **java.sql.NClob** auf der Grundlage der angegebenen Startposition ab.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlservernclob.md)|Ruft einen Datenstrom ab, der verwendet wird, um ab der angegebenen Position ASCII-Zeichen in den **NCLOB**-Wert zu schreiben, der von diesem **java.sql.NClob**-Objekt dargestellt wird.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlservernclob.md)|Ruft einen Datenstrom ab, der verwendet wird, um ab der angegebenen Position einen Datenstrom von Unicode-Zeichen in den **NCLOB**-Wert zu schreiben, der von diesem **java.sql.NClob**-Objekt dargestellt wird.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlservernclob.md)|Schreibt die angegebene **Zeichenfolge** ab der angegebenen Position in das **NCLOB**.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlservernclob.md)|Kürzt den **NCLOB**-Wert auf die angegebene Länge.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von|Methoden|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Clob|free, getAsciiStream, getCharacterStream, getSubString, length, position, setAsciiStream, setCharacterStream, setString, truncate|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
