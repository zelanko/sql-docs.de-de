---
title: SQLTablePrivileges | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c5ab485199920932bd88ce8740a51b7e56152a0b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014092"
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLTablePrivileges** kann für einen statischen Cursor ausgeführt werden. Wenn versucht wird, **SQLTablePrivileges** in einem aktualisierbaren (keysetgesteuerten oder dynamischen) Cursor auszuführen, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt Meldung von Informationen für Tabellen auf Verbindungsservern, indem er einen zweiteiligen Namen für die *CatalogName* Parameter: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLTablePrivileges-Funktion] (https://go.microsoft.com/fwlink/?LinkId=59373\)   
 [ODBC-API-Implementierungsdetails](~/relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
