---
description: SQLServerClob-Elemente
title: SQLServerClob-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: Assembly
ms.assetid: 7db785ca-edd5-4833-8053-17fdbf87279a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c08ab28a64ddbb463f8a86d2d5a8a66f14f1ca82
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478572"
---
# <a name="sqlserverclob-members"></a>SQLServerClob-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  In den folgenden Tabellen sind die Elemente aufgeführt, die von der [SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md)|Initialisiert eine neue Instanz der SQLServerClob-Klasse.|  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
 Keine.  
  
## <a name="methods"></a>Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlserverclob.md)|Mit dieser Methode werden das CLOB sowie die von diesem verwendeten Ressourcen freigegeben.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverclob.md)|Materialisiert das CLOB als ASCII-Datenstrom.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)|Gibt die CLOB-Daten als java.io.Reader-Objekt oder als Zeichendatenstrom zurück.|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlserverclob.md)|Gibt eine Kopie der angegebenen Teilzeichenfolge im CLOB auf der Grundlage der angegebenen Startposition und der Anzahl der zu kopierenden Zeichen zurück.|  
|[length](../../../connect/jdbc/reference/length-method-sqlserverclob.md)|Gibt die Anzahl von Zeichen im CLOB zurück.|  
|[position](../../../connect/jdbc/reference/position-method-sqlserverclob.md)|Gibt die Zeichenposition des angegebenen CLOBs oder der Zeichenfolge im CLOB auf der Grundlage der angegebenen Startposition zurück.|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverclob.md)|Gibt einen Datenstrom zurück, der verwendet wird, um ab der angegebenen Position ASCII-Zeichen in das CLOB zu schreiben.|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverclob.md)|Gibt einen Datenstrom zurück, der verwendet wird, um ab der angegebenen Position einen Unicode-Zeichendatenstrom in das CLOB zu schreiben.|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)|Schreibt die angegebene Zeichenfolge ab der angegebenen Position in das CLOB.|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlserverclob.md)|Kürzt das CLOB auf die angegebene Länge.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von|Methoden|  
|--------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerClob-Klasse](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
