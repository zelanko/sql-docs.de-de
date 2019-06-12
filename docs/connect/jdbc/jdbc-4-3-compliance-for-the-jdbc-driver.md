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
manager: jroth
ms.openlocfilehash: 02aef28bb40c4d4f48b28630d1752c9e5f88c3e5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781546"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3-Kompatibilität für den JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Versionen des Microsoft JDBC-Treibers für SQL Server vor Version 6.4 sind nur mit den Spezifikationen der JDBC-API 4.2 (Java Database Connectivity) konform. Dieser Abschnitt trifft auf Versionen bis einschließlich Version 6.4 nicht zu.

Ab Version 6.4, Microsoft JDBC-Treiber für SQL Server, JAVA 9 kompatibel ist, und löst `SQLFeatureNotSupportedException` für neue JDBC 4.3-APIs, die Methoden nicht implementiert haben.

Mit Microsoft JDBC-Treiber 7.0 für SQL Server-Version des Treibers ist nun JAVA 10 kompatibel und unterstützt, die unten genannten APIs. Löst der Treiber `SQLFeatureNotSupportedException` für andere nicht implementierten Methoden von JDBC 4.3-Spezifikationen.

|Neue API|und Beschreibung|Bemerkenswerte Implementierungsdetails|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Hinweise an, die der Treiber, den eine Anforderung, unabhängige Einheit arbeiten, für diese Verbindung beginnt. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Speichert die Werte der Verbindungsfelder, die geändert werden, über die öffentliche API-Methoden sind: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall`, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Hinweise an, die der Treiber, den eine Anforderung, eine unabhängige Arbeitseinheit abgeschlossen wurde. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Schließen die Anweisungen, die während der die Arbeitseinheit erstellt werden, und alle geöffneten Transaktionen ein Rollback aus. Die Methode wird auch die Änderungen an die Verbindungsfelder, die oben aufgeführt sind.|
