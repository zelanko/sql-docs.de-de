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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 35bd61c12933dac25ac90d8b56afb0e17b44d3ab
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706323"
---
# <a name="sqlcolumnprivileges"></a>SQLColumnPrivileges
  **SQLColumnPrivileges** gibt SQL_SUCCESS zurück, ob Werte für die Parameter*CatalogName*, Schema Name, *TableName*oder *ColumnName* *vorhanden sind.* **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLColumnPrivileges** kann auf einem statischen Server Cursor ausgeführt werden. Der Versuch, **SQLColumnPrivileges** für einen aktualisierbaren (dynamischen oder Keyset-) Cursor auszuführen, gibt SQL_SUCCESS_WITH_INFO zurück, der angibt, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für den *CatalogName* -Parameter akzeptiert: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLColumnPrivileges-Funktion](https://go.microsoft.com/fwlink/?LinkId=59335)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
