---
title: Argumente in Katalogfunktionen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 819c10d0b137d5e0999c1e10bf22810392509f76
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288166"
---
# <a name="arguments-in-catalog-functions"></a>Argumente in Katalogfunktionen
Alle Katalogfunktionen akzeptieren Argumente, mit denen eine Anwendung den Umfang der zurückgegebenen Daten einschränken kann. Der erste und der zweite Aufruf von **SQLTables** im folgenden Code geben z. B. ein Resultset zurück, das Informationen zu allen Tabellen enthält, während der dritte Aufruf Informationen über die Tabelle Orders zurückgibt:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Katalogfunktionszeichenfolgenargumente lassen sich in vier verschiedene Typen ein: ordinary argument (OA), pattern value argument (PV), identifier argument (ID) und value list argument (VL). Die meisten Zeichenfolgenargumente können je nach Wert des SQL_ATTR_METADATA_ID-Anweisungsattributs aus einem von zwei verschiedenen Typen bestehen. In der folgenden Tabelle sind die Argumente für jede Katalogfunktion aufgeführt und der Typ des Arguments für eine SQL_TRUE oder SQL_FALSE Wert von SQL_ATTR_METADATA_ID beschrieben.  
  
|Funktion|Argument|Geben Sie ein, wenn SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Geben Sie ein, wenn SQL_<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ID-ID-ID-ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ID-ID-ID-ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName* *FKTableName*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnName*|OA PV PV PV|ID-ID-ID-ID|  
|**'SQLProcedures'**|*CatalogName* *SchemaName* *ProcName*|OA PV PV|ID-ID-ID|  
|**'SQLSpecialColumns'**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**'SQLStatistics'**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA PV PV|ID-ID-ID|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *TableType*|PV PV PV VL|ID ID ID VL|  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Normale Argumente](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Argumente des Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Bezeichnerargumente](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Argumente der Werteliste](../../../odbc/reference/develop-app/value-list-arguments.md)
