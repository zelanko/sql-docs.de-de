---
title: SQLColumnPrivileges | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1f4ec3c0837f282193c937a4b0e8800b7456b57f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68113592"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLColumnPrivileges** gibt SQL_SUCCESS zurück, unabhängig davon, ob Werte vorhanden sind, für die*CatalogName*, *SchemaName*, *TableName*, oder  *ColumnName* Parameter. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLColumnPrivileges** kann in einem statischen Servercursor ausgeführt werden. Der Versuch, auszuführen **SQLColumnPrivileges** in einem aktualisierbaren (dynamischen oder Keyset-) Cursor der Cursor SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die *CatalogName* Parameter: *Linked_server_name*.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLColumnPrivileges-Funktion](https://go.microsoft.com/fwlink/?LinkId=59335)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
