---
title: JDBC 4,3-Kompatibilität für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20cefb029a126b0a262d86a2dc0a0791959085bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956367"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3-Kompatibilität für den JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Versionen des Microsoft JDBC-Treibers für SQL Server vor Version 6.4 sind nur mit den Spezifikationen der JDBC-API 4.2 (Java Database Connectivity) konform. Dieser Abschnitt trifft auf Versionen bis einschließlich Version 6.4 nicht zu.

Ab Version 6,4 ist der Microsoft JDBC-Treiber für SQL Server Java 9-kompatibel und `SQLFeatureNotSupportedException` löst neue JDBC 4,3-APIs mit nicht implementierten Methoden aus.

Mit dem Microsoft JDBC Driver 7,0 for SQL Server Release ist der Treiber jetzt Java 10-kompatibel und unterstützt die unten erwähnten APIs. Der Treiber `SQLFeatureNotSupportedException` löst für andere nicht implementierte Methoden aus JDBC 4,3-Spezifikationen aus.

|Neue API|und Beschreibung|Bemerkenswerte Implementierungsdetails|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Hinweise für den Treiber, dass eine Anforderung, eine unabhängige Arbeitseinheit, mit dieser Verbindung beginnt. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Speichert die Werte der Verbindungs Felder, die durch öffentliche API-Methoden geändert werden können `databaseAutoCommitMode`: `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall`,, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Gibt dem Treiber Hinweise, dass eine Anforderung (eine unabhängige Arbeitseinheit) abgeschlossen wurde. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Schließt die-Anweisungen, die während der Arbeitseinheit erstellt werden, und führt ein Rollback für alle geöffneten Transaktionen aus. Die-Methode stellt auch die Änderungen an den oben aufgeführten Verbindungs Feldern wieder her.|
