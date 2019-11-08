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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a295df72be56343cdca65591a147adf173b36059
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785578"
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLTablePrivileges** kann für einen statischen Cursor ausgeführt werden. Wenn versucht wird, **SQLTablePrivileges** in einem aktualisierbaren (keysetgesteuerten oder dynamischen) Cursor auszuführen, wird SQL_SUCCESS_WITH_INFO zurückgegeben. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt die Meldung von Informationen für Tabellen auf verknüpften Servern, indem er einen zweiteiligen Namen für den *CatalogName* -Parameter unterstützt: *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLTablePrivileges-Funktion] (https://go.microsoft.com/fwlink/?LinkId=59373\)   
 [ODBC-API-Implementierungsdetails](~/relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
