---
title: SQLPrimaryKeys | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 538b1a11962cf861aeaa1e95443f994b27feb87c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088660"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  Eine Tabelle ist möglicherweise eine oder mehrere Spalten, die als eindeutige Zeilenbezeichner dienen können, und Tabellen, die ohne PRIMARY KEY-Einschränkung erstellt zurückgeben, ein leeres Resultset SQLPrimaryKeys. Der ODBC-Funktion [SQLSpecialColumns](sqlspecialcolumns.md) meldet zeilenbezeichnerkandidaten für Tabellen ohne Primärschlüssel.  
  
 SQLPrimaryKeys gibt SQL_SUCCESS zurück, unabhängig davon, ob Werte vorhanden sind, für die *CatalogName*, *SchemaName*, oder *TableName* Parameter. SQLFetch gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 SQLPrimaryKeys kann in einem statischen Servercursor ausgeführt werden. SQLPrimaryKeys in einem aktualisierbaren (dynamischen oder Keyset-) Cursor ausgeführt wird, wird SQL_SUCCESS_WITH_INFO, der angibt, dass der Cursortyp geändert wurde.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die *CatalogName* Parameter: *linked_server_name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys und Tabellenwertparameter  
 Wenn das SQL_SOPT_SS_NAME_SCOPE-Anweisungsattribut den Wert SQL_SS_NAME_SCOPE_TABLE_TYPE statt auf den Standardwert SQL_SS_NAME_SCOPE_TABLE aufweist, wird SQLPrimaryKeys Informationen zu Primärschlüsselspalten von Tabellentypen zurück. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLPrimaryKeys-Funktion](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
