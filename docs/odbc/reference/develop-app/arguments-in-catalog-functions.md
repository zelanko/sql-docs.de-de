---
description: Argumente in Katalogfunktionen
title: Argumente in Katalog Funktionen | Microsoft-Dokumentation
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
ms.openlocfilehash: ef53514f41d28e93648970b03fa53927529d8344
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483133"
---
# <a name="arguments-in-catalog-functions"></a>Argumente in Katalogfunktionen
Alle Katalog Funktionen akzeptieren Argumente, mit denen eine Anwendung den Gültigkeitsbereich der zurückgegebenen Daten einschränken kann. Der erste und zweite Aufruf von **SQLTables** im folgenden Code gibt beispielsweise ein Resultset mit Informationen zu allen Tabellen zurück, während der dritte Aufruf Informationen zur Tabelle Orders zurückgibt:  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 Zeichen folgen Argumente für Katalog Funktionen lassen sich in vier verschiedene Typen unterscheiden: normales Argument (OA), Muster Wert Argument (PV), bezeichnerargument (ID) und Wert Listen Argument (VL). Die meisten Zeichen folgen Argumente können einen von zwei unterschiedlichen Typen aufweisen, je nach dem Wert des Attributs der SQL_ATTR_METADATA_ID Anweisung. In der folgenden Tabelle werden die Argumente für jede Katalog Funktion aufgelistet und der Typ des Arguments für einen SQL_TRUE oder SQL_FALSE Wert von SQL_ATTR_METADATA_ID beschrieben.  
  
|Funktion|Argument|Beim SQL_ eingeben<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|Beim SQL_ eingeben<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ID-ID-ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ID-ID-ID|  
|**SQLForeignKeys**|*PKCatalogName* *pkschemaname* *PKTableName* *skcatalogname* *skschemaname* - *Schlüssel Name*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *Prozess Name* *ColumnName*|OA PV PV PV|ID-ID-ID|  
|**'SQLProcedures'**|*CatalogName* *SchemaName* *Prozess Name*|OA-PV-PV|ID-ID-ID|  
|**'SQLSpecialColumns'**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**'SQLStatistics'**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID-ID-ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA-PV-PV|ID-ID-ID|  
|**SQLTables**|" *CatalogName* *SchemaName* *TableName* *TABLETYPE* "|PV PV PV-VL|ID-ID VL|  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Normale Argumente](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [Argumente des Musterwerts](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [Bezeichnerargumente](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [Argumente der Werteliste](../../../odbc/reference/develop-app/value-list-arguments.md)
