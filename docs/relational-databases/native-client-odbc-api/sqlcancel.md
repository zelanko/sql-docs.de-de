---
title: SQLCancel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLCancel function
ms.assetid: d4c965ae-c1ac-4e9d-b4b9-32b561401106
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1758088319a712564fe2f11a136f5833b12111f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014702"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Im [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516) -Thema erfahren Sie, dass in ODBC 2.x bei einem Aufruf von **SQLCancel** durch eine Anwendung ohne anschließende Bearbeitung der Anweisung **SQLCancel** dieselben Auswirkungen wie **SQLFreeStmt** bei Verwendung der **SQL_CLOSE** -Option hat; dieses Verhalten wird nur der Vollständigkeit halber definiert, und Anwendungen sollten **SQLFreeStmt** oder **SQLCloseCursoder** to close cursoders. Aber auch wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anwendung die ODBC API-Version auf 3.5.x oder höher festlegt, verwendet die **SQLCancel** -Funktion das ODBC 2.x-Verhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [SQLCancel](https://go.microsoft.com/fwlink/?LinkId=203516)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
