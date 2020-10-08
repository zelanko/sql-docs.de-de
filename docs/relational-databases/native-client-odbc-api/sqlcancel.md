---
description: SQLCancel
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86f50105acb4c506b6ecb937ff0f302f32b24bb3
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91811138"
---
# <a name="sqlcancel"></a>SQLCancel
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Im [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md) -Thema erfahren Sie, dass in ODBC 2.x bei einem Aufruf von **SQLCancel** durch eine Anwendung ohne anschließende Bearbeitung der Anweisung **SQLCancel** dieselben Auswirkungen wie **SQLFreeStmt** bei Verwendung der **SQL_CLOSE** -Option hat; dieses Verhalten wird nur der Vollständigkeit halber definiert, und Anwendungen sollten **SQLFreeStmt** oder **SQLCloseCursoder** to close cursoders. Aber auch wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Anwendung die ODBC API-Version auf 3.5.x oder höher festlegt, verwendet die **SQLCancel** -Funktion das ODBC 2.x-Verhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLCancel](../../odbc/reference/syntax/sqlcancel-function.md)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
