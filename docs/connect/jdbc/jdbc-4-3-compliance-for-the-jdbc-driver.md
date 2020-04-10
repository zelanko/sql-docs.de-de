---
title: JDBC 4.3-Konformität für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 099664892564a6b38e270f934cb3208029fdd05f
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928357"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3-Kompatibilität für den JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Versionen des Microsoft JDBC-Treibers für SQL Server vor Version 6.4 sind nur mit den Spezifikationen der JDBC-API 4.2 (Java Database Connectivity) konform. Dieser Abschnitt trifft auf Versionen bis einschließlich Version 6.4 nicht zu.

Ab Version 6.4 ist der JDBC-Treiber für SQL Server JAVA 9-kompatibel und löst `SQLFeatureNotSupportedException` für neue JDBC 4.3-APIs aus, die nicht implementierte Methoden aufweisen.

Mit dem Release des JDBC-Treibers 7.0 für SQL Server ist der Treiber nun JAVA 10-kompatibel und unterstützt die unten aufgeführten APIs. Der Treiber löst `SQLFeatureNotSupportedException` für andere, nicht implementierte Methoden von JDBC 4.3-Spezifikationen aus.

|Neue API|BESCHREIBUNG|Bemerkenswerte Implementierungsdetails|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Weist den Treiber darauf hin, dass eine Anforderung, eine unabhängige Arbeitseinheit, auf dieser Verbindung beginnt. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Speichert die Werte der Verbindungsfelder, die über öffentliche API-Methoden geändert werden können: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall`, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Weist den Treiber darauf hin, dass eine Anforderung, eine unabhängige Arbeitseinheit, abgeschlossen wurde. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Beendet Anweisungen, die während der Arbeitseinheit erstellt wurden, und führt ein Rollback für alle ausstehenden Transaktionen durch. Die Methode setzt auch die Änderungen an den oben aufgeführten Verbindungsfeldern zurück.|
