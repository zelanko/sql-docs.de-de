---
title: JDBC 4.3 Kompatibilität für den JDBC-Treiber | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: fc2fbb2b217880b255d522149dabd38701a8c0e4
ms.sourcegitcommit: 8bc5d85bd157f9cfd52245d23062d150b76066ef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2019
ms.locfileid: "57579060"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3-Kompatibilität für den JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Versionen des Microsoft JDBC-Treibers für SQL Server vor Version 6.4 sind nur mit den Spezifikationen der JDBC-API 4.2 (Java Database Connectivity) konform. Dieser Abschnitt trifft auf Versionen bis einschließlich Version 6.4 nicht zu.

Ab Version 6.4, Microsoft JDBC-Treiber für SQL Server, JAVA 9 kompatibel ist, und löst `SQLFeatureNotSupportedException` für neue JDBC 4.3-APIs, die Methoden nicht implementiert haben.

Mit Microsoft JDBC-Treiber 7.0 für SQL Server-Version des Treibers ist nun JAVA 10 kompatibel und unterstützt, die unten genannten APIs. Löst der Treiber `SQLFeatureNotSupportedException` für andere nicht implementierten Methoden von JDBC 4.3-Spezifikationen.

|Neue API|Beschreibung|Bemerkenswerte Implementierungsdetails|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Hinweise an, die der Treiber, den eine Anforderung, unabhängige Einheit arbeiten, für diese Verbindung beginnt. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Speichert die Werte der Verbindungsfelder, die geändert werden, über die öffentliche API-Methoden sind: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall`, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Hinweise an, die der Treiber, den eine Anforderung, eine unabhängige Arbeitseinheit abgeschlossen wurde. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Schließen die Anweisungen, die während der die Arbeitseinheit erstellt werden, und alle geöffneten Transaktionen ein Rollback aus. Die Methode wird auch die Änderungen an die Verbindungsfelder, die oben aufgeführt sind.|
