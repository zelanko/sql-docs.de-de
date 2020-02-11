---
title: SQLTables | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8209bf586e5a0b288b4975869ee8903a73a27f06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63188665"
---
# <a name="sqltables"></a>SQLTables
  SQLTables kann auf einem statischen Server Cursor ausgeführt werden. Der Versuch, SQLTables für einen aktualisierbaren (dynamischen oder Keyset-) Cursor auszuführen, gibt SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 SQLTables meldet Tabellen aus allen Datenbanken, wenn der *CatalogName* -Parameter SQL_ALL_CATALOGS und alle anderen Parameter Standardwerte (null-Zeiger) enthalten.  
  
 SQLTables verwendet zum Melden von verfügbaren Katalogen, Schemas und Tabellentypen eine besondere Verwendung leerer Zeichen folgen (Byte Zeiger der Länge 0 (null)). Leere Zeichenfolgen sind keine Standardwerte (NULL-Zeiger).  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für den *CatalogName* -Parameter akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
 SQLTables gibt Informationen zu allen Tabellen zurück, deren Namen *TableName* entsprechen und deren Besitzer der aktuelle Benutzer ist.  
  
## <a name="sqltables-and-table-valued-parameters"></a>'SQLTables'- und Tabellenwertparameter  
 Wenn das Anweisungs Attribut SQL_SOPT_SS_NAME_SCOPE den Wert SQL_SS_NAME_SCOPE_TABLE_TYPE anstelle des Standardwerts SQL_SS_NAME_SCOPE_TABLE enthält, gibt SQLTables Informationen zu Tabellentypen zurück. Der TABLE_TYPE Wert, der für einen Tabellentyp in Spalte 4 des von SQLTables zurückgegebenen Resultsets zurückgegeben wird, ist der Tabellentyp. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Tabellen, Sichten und Synonyme nutzen einen gemeinsamen Namespace, der sich von dem Namespace unterscheidet, den Tabellentypen verwenden. Wenngleich ein und derselbe Namespace nicht eine Tabelle und eine Sicht enthalten kann, ist es hingegen möglich, dass ein Namespace im selben Katalog und Schema eine Tabelle und einen Tabellentypen enthält.  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="example"></a>Beispiel  
  
```  
// Get a list of all tables in the current database.  
SQLTables(hstmt, NULL, 0, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of all tables in all databases.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, NULL, 0, NULL, 0, NULL,0);  
  
// Get a list of databases on the current connection's server.  
SQLTables(hstmt, (SQLCHAR*) "%", SQL_NTS, (SQLCHAR*)"", 0, (SQLCHAR*)"",  
    0, NULL, 0);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLTables-Funktion](https://go.microsoft.com/fwlink/?LinkId=59374)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
