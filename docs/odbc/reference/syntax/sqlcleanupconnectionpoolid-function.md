---
title: SQLCleanupConnectionPoolID-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a74a92cc05ecd41e99ff87642c7fe3ee527e0c98
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301320"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.81 Standard-Konformität: ODBC  
  
 **Zusammenfassung**  
 **SQLCleanupConnectionPoolID** informiert einen Treiber darüber, dass ein Zeitvertreib für eine Pool-ID festgelegt wurde. Eine Pool-ID kann ein Timeout geben, wenn alle Verbindungen in einem Pool, der dieser Pool-ID zugeordnet ist, ein Timeout durchgeführt wurden. Weitere Informationen zum Verbindungstimeout finden Sie [unter Pooling in den Microsoft Data Access Components.](https://msdn.microsoft.com/library/ms810829.aspx)  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Argumente  
 *EnvironmentHandle*  
 [Eingabe] Der Umgebungshandle des Pools.  
  
 *PoolID*  
 [Eingabe] Der Pool, der der Pool-ID zugeordnet ist, für die ein Timeout gilt.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Der Treiber-Manager verarbeitet keine Diagnoseinformationen, die von **SQLCleanupConnectionPoolID**zurückgegeben werden.  
  
 Eine Anwendung kann die vom Treiber zurückgegebene Fehlermeldung nicht empfangen.  
  
## <a name="remarks"></a>Bemerkungen  
 **SQLCleanupConnectionPoolID** kann jederzeit aufgerufen werden, aber der Treiber-Manager garantiert, dass kein anderer Thread gleichzeitig **SQLGetPoolID** aufruft und kein anderer Thread gleichzeitig **SQLRateConnection** und **SQLPoolConnect** mit einem Verbindungsinfotoken aufruft, das dieser Pool-ID zugewiesen ist. Daher muss der Treiber sicherstellen, dass diese Funktion threadsicher ist.  
  
 Ein Treiber kann die Ressourcen bereinigen, die der Pool-ID zugeordnet sind.  
  
 Anwendungen sollten diese Funktion nicht direkt aufrufen. Ein ODBC-Treiber, der treiberbewusstes Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi.h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber-Aware-Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
