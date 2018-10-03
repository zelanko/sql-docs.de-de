---
title: SQLColumnPrivileges | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColumnPrivileges function
ms.assetid: c78acd4e-8668-4abc-9bc9-6ad381965863
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0deb4c3099807e42bbc0e5f0e3b588481733c7f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217540"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges** gibt SQL_SUCCESS zurück, unabhängig davon, ob Werte vorhanden sind, für die*CatalogName*, *SchemaName*, *TableName*, oder  *ColumnName* Parameter. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLColumnPrivileges** kann in einem statischen Servercursor ausgeführt werden. Der Versuch, auszuführen **SQLColumnPrivileges** in einem aktualisierbaren (dynamischen oder Keyset-) Cursor der Cursor SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die *CatalogName* Parameter: *linked_server_name*.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLColumnPrivileges-Funktion](http://go.microsoft.com/fwlink/?LinkId=59335)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
