---
title: Sqlcleanupconnectionpoolid-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301320"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,81 Standards Compliance: ODBC  
  
 **Zusammenfassung**  
 **Sqlcleanupconnectionpoolid** informiert einen Treiber darüber, dass ein Timeout für eine Pool-ID aufgetreten ist. Ein Timeout für eine Pool-ID kann auftreten, wenn für alle Verbindungen in einem Pool, der dieser Pool-ID zugeordnet ist, ein Timeout Weitere Informationen zum Verbindungs Timeout finden Sie unter [Pooling in den Microsoft Data Access Components](https://msdn.microsoft.com/library/ms810829.aspx) .  
  
## <a name="syntax"></a>Syntax  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>Argumente  
 *Environment-THandle*  
 Der Das Umgebungs Handle des Pools.  
  
 *Poolid*  
 Der Der Pool, der der Pool-ID zugeordnet ist, für die ein Timeout aufgetreten ist.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Der Treiber-Manager verarbeitet keine Diagnoseinformationen, die von **sqlcleanupconnectionpoolid**zurückgegeben werden.  
  
 Eine Anwendung kann die vom Treiber zurückgegebene Fehlermeldung nicht empfangen.  
  
## <a name="remarks"></a>Bemerkungen  
 **Sqlcleanupconnectionpoolid** kann jederzeit aufgerufen werden, aber der Treiber-Manager garantiert, dass kein anderer Thread gleichzeitig **sqlgetpoolid** aufruft und kein anderer Thread gleichzeitig **sqlrateconnetction** und **sqlpoolconnect** mit einem Verbindungs Informations Token aufruft, das dieser Pool-ID zugewiesen ist. Daher muss der Treiber sicherstellen, dass diese Funktion Thread sicher ist.  
  
 Ein Treiber kann die der Pool-ID zugeordneten Ressourcen bereinigen.  
  
 Anwendungen sollten diese Funktion nicht direkt aufzurufen. Ein ODBC-Treiber, der Treiber fähiges Verbindungspooling unterstützt, muss diese Funktion implementieren.  
  
 Fügen Sie sqlspi. h für die ODBC-Treiberentwicklung ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Developing Connection-Pool Awareness in an ODBC Driver (Entwickeln von Verbindungspool-Unterstützung in einem ODBC-Treiber)](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
