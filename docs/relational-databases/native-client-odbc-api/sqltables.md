---
title: SQLTables | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTables function
ms.assetid: 77b6c15c-9cf7-4019-b3f0-3d27d23ef656
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3f3fa2b053c41facba7d608b2352772abd3ff103
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291742"
---
# <a name="sqltables"></a>SQLTables
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQLTables kann auf einem statischen Servercursor ausgeführt werden. Der Versuch, SQLTables auf einem aktualisierbaren Cursor (dynamisch oder Keyset) auszuführen, gibt SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 SQLTables meldet Tabellen aus allen Datenbanken, wenn der *Parameter CatalogName* SQL_ALL_CATALOGS ist und alle anderen Parameter Standardwerte (NULL-Zeiger) enthalten.  
  
 Zum Melden verfügbarer Kataloge, Schemas und Tabellentypen verwendet SQLTables spezielle Zeichenfolgen (Bytezeiger mit null Länge). Leere Zeichenfolgen sind keine Standardwerte (NULL-Zeiger).  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für den *CatalogName* -Parameter akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
 SQLTables gibt Informationen zu allen Tabellen zurück, deren Namen mit *TableName* übereinstimmen und die im Besitz des aktuellen Benutzers sind.  
  
## <a name="sqltables-and-table-valued-parameters"></a>'SQLTables'- und Tabellenwertparameter  
 Wenn das Anweisungsattribut SQL_SOPT_SS_NAME_SCOPE den Wert SQL_SS_NAME_SCOPE_TABLE_TYPE und nicht den Standardwert SQL_SS_NAME_SCOPE_TABLE hat, gibt SQLTables Informationen zu Tabellentypen zurück. Der TABLE_TYPE Wert, der für einen Tabellentyp in Spalte 4 des von SQLTables zurückgegebenen Resultsets zurückgegeben wird, ist TABLE TYPE. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Tabellen, Sichten und Synonyme nutzen einen gemeinsamen Namespace, der sich von dem Namespace unterscheidet, den Tabellentypen verwenden. Wenngleich ein und derselbe Namespace nicht eine Tabelle und eine Sicht enthalten kann, ist es hingegen möglich, dass ein Namespace im selben Katalog und Schema eine Tabelle und einen Tabellentypen enthält.  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
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
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
