---
title: Argumente in Katalogfunktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5dd36e82b71ff862a543bfa38cda4b4a660738a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789318"
---
# <a name="arguments-in-catalog-functions"></a>Argumente in Katalogfunktionen
Alle Katalogfunktionen akzeptieren Argumente, die mit denen eine Anwendung den Bereich der zurückgegebenen Daten einschränken kann. Z. B. die erste und zweite Aufrufe **SQLTables** Zurückgeben von Resultsets, die Informationen zu allen Tabellen enthält, während der dritte Aufruf gibt Informationen über die Orders-Tabelle zurück, in den folgenden Code:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Katalog-Funktion Zeichenfolgenargumente fallen in vier verschiedenen Typen: normale Argument (OA), Pattern-Wert-Argument (PV), Argument Bezeichner (ID) und Wert Listenargument (VL). Die meisten Zeichenfolgenargumente können eines der zwei verschiedene Arten, abhängig vom Wert des Attributs SQL_ATTR_METADATA_ID-Anweisung sein. Die folgende Tabelle listet die Argumente für jede Katalogfunktion und beschreibt den Typ des Arguments für eine Wert SQL_TRUE oder SQL_FALSE SQL_ATTR_METADATA_ID.  
  
|Funktion|Argument|Geben Sie bei SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Geben Sie bei SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ID-ID-ID-ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA BW, BW PV|ID-ID-ID-ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName*  *FKTableName*|OA OA OA OA OA OA|ID-ID-ID-ID-ID-ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnName*|OA BW, BW PV|ID-ID-ID-ID|  
|**SQLProcedures**|*CatalogName* *SchemaName* *ProcName*|OA PV PV|ID-ID-ID|  
|**SQLSpecialColumns**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**SQLStatistics**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA PV PV|ID-ID-ID|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *für TableType*|BW, BW PV VL|ID-ID ID VL|  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Normale Argumente](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Argumente des Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Bezeichnerargumente](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Argumente der Wertliste](../../../odbc/reference/develop-app/value-list-arguments.md)
