---
title: SQLPrimaryKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPrimaryKeys function
ms.assetid: bc61cd5b-d2f4-4f87-abc7-743cf9ea772d
caps.latest.revision: 37
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb0dc440025730c278206a751a5ce741b69b0f6e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048972"
---
# <a name="sqlprimarykeys"></a>SQLPrimaryKeys
  Möglicherweise eine Tabelle eine Spalte oder Spalten, die als eindeutiger Zeilenbezeichner dienen können, und Tabellen ohne eine PRIMARY KEY-Einschränkung erstellt geben ein leeres Resultset SQLPrimaryKeys zurück. Der ODBC-Funktion [SQLSpecialColumns](sqlspecialcolumns.md) meldet zeilenbezeichnerkandidaten für Tabellen ohne Primärschlüssel.  
  
 SQLPrimaryKeys gibt SQL_SUCCESS zurück, unabhängig davon, ob Werte für vorhanden *CatalogName*, *SchemaName*, oder *TableName* Parameter. SQLFetch gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 SQLPrimaryKeys kann in einem statischen Servercursor ausgeführt werden. Der Versuch SQLPrimaryKeys auf einem aktualisierbaren (dynamischen oder Keyset-) Cursor auszuführen Cursor SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt die Berichtsinformationen für Tabellen auf Verbindungsservern durch akzeptieren einen zweiteiligen Namen für die *CatalogName* Parameter: *linked_server_name*.  
  
## <a name="sqlprimarykeys-and-table-valued-parameters"></a>SQLPrimaryKeys und Tabellenwertparameter  
 Wenn das SQL_SOPT_SS_NAME_SCOPE-Anweisungsattribut den Wert SQL_SS_NAME_SCOPE_TABLE_TYPE statt den Standardwert sql_ss_name_scope_table aufweist, wird die SQLPrimaryKeys Informationen zu Primärschlüsselspalten von Tabellentypen zurück. Weitere Informationen zu SQL_SOPT_SS_NAME_SCOPE finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLPrimaryKeys-Funktion](http://go.microsoft.com/fwlink/?LinkId=59361)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  