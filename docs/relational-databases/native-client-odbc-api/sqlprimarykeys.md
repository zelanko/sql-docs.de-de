---
title: SQLPrimaryKeys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 26e0a05125e71cbd33aa7e32f584fef2613e0d0a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63014265"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Eine Tabelle ist möglicherweise eine oder mehrere Spalten, die als eindeutige Zeilenbezeichner dienen können, und Tabellen, die ohne PRIMARY KEY-Einschränkung erstellt zurückgeben, ein leeres Resultset SQLPrimaryKeys. Der ODBC-Funktion [SQLSpecialColumns](../../relational-databases/native-client-odbc-api/sqlspecialcolumns.md) meldet zeilenbezeichnerkandidaten für Tabellen ohne Primärschlüssel.  
  
 SQLPrimaryKeys gibt SQL_SUCCESS zurück, unabhängig davon, ob Werte vorhanden sind, für die *CatalogName*, *SchemaName*, oder *TableName* Parameter. SQLFetch gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 SQLPrimaryKeys kann in einem statischen Servercursor ausgeführt werden. SQLPrimaryKeys in einem aktualisierbaren (dynamischen oder Keyset-) Cursor ausgeführt wird, wird SQL_SUCCESS_WITH_INFO, der angibt, dass der Cursortyp geändert wurde.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die *CatalogName* Parameter: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys und Tabellenwertparameter  
 Wenn das SQL_SOPT_SS_NAME_SCOPE-Anweisungsattribut den Wert SQL_SS_NAME_SCOPE_TABLE_TYPE statt auf den Standardwert SQL_SS_NAME_SCOPE_TABLE aufweist, wird SQLPrimaryKeys Informationen zu Primärschlüsselspalten von Tabellentypen zurück. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLPrimaryKeys-Funktion](https://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
