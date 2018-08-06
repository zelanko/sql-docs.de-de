---
title: JDBC 4.3 Kompatibilität für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f529c88044444f3fb6e428b6c69f5a5cf5917251
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278911"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>JDBC 4.3-Kompatibilität für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Versionen des Microsoft JDBC-Treibers für SQL Server vor Version 6.4 sind mit den Spezifikationen der JDBC-API 4.2 (Java Database Connectivity) konform. Dieser Abschnitt trifft auf Versionen vor Version 6.4 nicht zu.  
  
 Ab Version 6.4 Microsoft JDBC-Treiber für SQL Server ist JAVA 10 kompatibel, aber es ist nicht vollständig kompatibel mit den JDBC-API-4.3-Spezifikationen. Der Treiber löst SQLFeatureNotSupportedException für eine nicht implementierte Methode aus. 
 
 Die folgenden JDBC 4.3-API-Methoden werden in Microsoft JDBC-Treiber 6.4 für SQL Server implementiert.
 
  **SQLServerConnection-Klasse**  
  
|Neue Methoden|und Beschreibung|Bemerkenswerte Implementierungsdetails|  
|-----------------|-----------------|-------------------------------|  
|"void" beginRequest()|Hinweise an, die der Treiber, den eine Anforderung, unabhängige Einheit arbeiten, für diese Verbindung beginnt. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Speichert die Werte der Verbindungsfelder, die geändert werden, über die öffentliche API-Methoden sind: `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall `, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|"void" endRequest()|Hinweise an, die der Treiber, den eine Anforderung, eine unabhängige Arbeitseinheit abgeschlossen wurde. Weitere Informationen finden Sie unter [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Schließen die Anweisungen, die während der die Arbeitseinheit erstellt werden, und alle geöffneten Transaktionen ein Rollback aus. Die Methode wird auch die Änderungen an die Verbindungsfelder, die oben aufgeführt sind.|