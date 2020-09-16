---
description: SQLServerResultSetMetaData-Elemente
title: SQLServerResultSetMetaData-Elemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 37587981-2979-49a3-a6ab-df4bfb9b8748
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1010b3d45bcca0c7b719e0a91d007f3acbc0f684
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462652"
---
# <a name="sqlserverresultsetmetadata-members"></a>SQLServerResultSetMetaData-Elemente
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Die folgenden Tabellen enthalten die Elemente, die von der [SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)-Klasse verfügbar gemacht werden.  
  
## <a name="constructors"></a>Konstruktoren  
 Keine  
  
## <a name="fields"></a>Felder  
 Keine.  
  
## <a name="inherited-fields"></a>Geerbte Felder  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|java.sql.ResultSetMetaData|columnNoNulls, columnNullable, columnNullableUnknown|  
  
## <a name="methods"></a>Methoden  
  
|Name|BESCHREIBUNG|  
|----------|-----------------|  
|[getCatalogName](../../../connect/jdbc/reference/getcatalogname-method-sqlserverresultsetmetadata.md)|Ruft den Katalognamen für die Tabelle mit der angegebenen Spalte ab.|  
|[getColumnClassName](../../../connect/jdbc/reference/getcolumnclassname-method-sqlserverresultsetmetadata.md)|Gibt den vollqualifizierten Namen der Java-Klasse zurück, deren Instanzen erstellt werden, wenn die [getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse aufgerufen wird, um einen Wert aus der Spalte abzurufen.|  
|[getColumnCount](../../../connect/jdbc/reference/getcolumncount-method-sqlserverresultsetmetadata.md)|Gibt die Anzahl von Spalten im Resultset zurück.|  
|[getColumnDisplaySize](../../../connect/jdbc/reference/getcolumndisplaysize-method-sqlserverresultsetmetadata.md)|Gibt die normale maximale Breite der angegebenen Spalte in Zeichen zurück.|  
|[getColumnLabel](../../../connect/jdbc/reference/getcolumnlabel-method-sqlserverresultsetmetadata.md)|Ruft den Titel ab, der für Ausdrucke und Anzeigen der angegebenen Spalte empfohlen wird.|  
|[getColumnName](../../../connect/jdbc/reference/getcolumnname-method-sqlserverresultsetmetadata.md)|Ruft den Namen der angegebenen Spalte ab.|  
|[getColumnType](../../../connect/jdbc/reference/getcolumntype-method-sqlserverresultsetmetadata.md)|Ruft den SQL-Typ der angegebenen Spalte ab.|  
|[getColumnTypeName](../../../connect/jdbc/reference/getcolumntypename-method-sqlserverresultsetmetadata.md)|Ruft den datenbankspezifischen Typnamen der angegebenen Spalte ab.|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverresultsetmetadata.md)|Ruft die Anzahl von Dezimalstellen für die angegebene Spalte ab.|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverresultsetmetadata.md)|Ruft für die angegebene Spalte die Anzahl von Stellen hinter dem Dezimalzeichen ab.|  
|[getSchemaName](../../../connect/jdbc/reference/getschemaname-method-sqlserverresultsetmetadata.md)|Ruft den Tabellenschemanamen für die angegebene Spalte ab.|  
|[getTableName](../../../connect/jdbc/reference/gettablename-method-sqlserverresultsetmetadata.md)|Ruft den Tabellennamen der angegebenen Spalte ab.|  
|[isAutoIncrement](../../../connect/jdbc/reference/isautoincrement-method-sqlserverresultsetmetadata.md)|Gibt an, ob die angegebene Spalte automatisch nummeriert wird, wodurch sie schreibgeschützt wird.|  
|[isCaseSensitive](../../../connect/jdbc/reference/iscasesensitive-method-sqlserverresultsetmetadata.md)|Gibt an, ob in einer Spalte die Groß-/Kleinschreibung berücksichtigt wird.|  
|[isCurrency](../../../connect/jdbc/reference/iscurrency-method-sqlserverresultsetmetadata.md)|Gibt an, ob es sich bei der angegebenen Spalte um einen Währungswert handelt.|  
|[isDefinitelyWritable](../../../connect/jdbc/reference/isdefinitelywritable-method-sqlserverresultsetmetadata.md)|Gibt an, ob ein Schreibvorgang in der angegebenen Spalte definitiv erfolgreich sein wird.|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverresultsetmetadata.md)|Gibt die NULL-Zulässigkeit von Werten in der angegebenen Spalte an.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverresultsetmetadata.md)|Gibt an, ob die angegebene Spalte definitiv schreibgeschützt ist.|  
|[isSearchable](../../../connect/jdbc/reference/issearchable-method-sqlserverresultsetmetadata.md)|Gibt an, ob die angegebene Spalte in einer SQL-Klausel vom Typ "WHERE" verwendet werden kann.|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverresultsetmetadata.md)|Gibt an, ob es sich bei den Werten in der angegebenen Spalte um Zahlen mit Vorzeichen handelt.|  
|[isSparseColumnSet](../../../connect/jdbc/reference/issparsecolumnset-method-sqlserverresultsetmetadata.md)|Gibt an, ob eine Spalte in einem Resultset ein Satz von Sparsespalten ist.|  
|[isWritable](../../../connect/jdbc/reference/iswritable-method-sqlserverresultsetmetadata.md)|Gibt an, ob ein Schreibvorgang in der angegebenen Spalte möglich ist.|  
  
## <a name="inherited-methods"></a>Geerbte Methoden  
  
|Klasse geerbt von:|Methoden|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSetMetaData-Klasse](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
