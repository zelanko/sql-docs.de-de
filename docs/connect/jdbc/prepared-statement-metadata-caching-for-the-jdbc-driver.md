---
title: Vorbereitetes Caching von Anweisungsmetadaten für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72ef56833f8f6a6ed4cc66a91dcb7a9e4576c7f5
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52395833"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Vorbereitetes Caching von Anweisungsmetadaten für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel enthält Informationen zu den zwei Änderungen, die implementiert werden, um die Leistung des Treibers zu verbessern.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Batchverarbeitung von Unprepare für vorbereitete Anweisungen
Da Version 6.1.6-preview, eine Verbesserung der Leistung durch Minimierung implementiert wurde Serverroundtrips mit SQL Server. Bisher wurde für jede Abfrage PrepareStatement ein Aufruf von unprepare auch gesendet. Der Treiber wird nun Batchverarbeitung unprepare Abfragen bis zu dem Schwellenwert "ServerPreparedStatementDiscardThreshold", die einen Standardwert von 10 hat.

> [!NOTE]  
>  Benutzer können den Standardwert ändern, mit der folgenden Methode: SetServerPreparedStatementDiscardThreshold (Int-Wert)

Eine weitere Änderung, die von 6.1.6-preview eingeführt wird, vor diesem Treiber Sp_prepexec jederzeit aufrufen würden. Jetzt für die erste Ausführung einer vorbereiteten Anweisung, ruft der Treiber Sp_executesql und für den Rest Sp_prepexec ausführt und ein Handle zugewiesen. Weitere Informationen finden Sie [hier](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Benutzer können das Standardverhalten ändern, um den früheren Versionen von Aufrufen stets Sp_prepexec EnablePrepareOnFirstPreparedStatementCall festlegen, um **"true"** mit dem folgenden Verfahren: SetEnablePrepareOnFirstPreparedStatementCall (boolescher Wert)

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Liste der neuen APIs eingeführt, die durch diese Änderung für die Batchverarbeitung von Unprepare für vorbereitete Anweisungen

 **SQLServerConnection**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|Int getDiscardedServerPreparedStatementCount()|Gibt die Anzahl der derzeit ausstehenden vorbereitete Anweisung unprepare Aktionen.|
|"void" closeUnreferencedPreparedStatementHandles()|Erzwingt, dass die Unprepare-Anforderungen für alle ausstehenden verworfenen vorbereiteten Anweisungen ausgeführt werden.|
|Boolesche getEnablePrepareOnFirstPreparedStatementCall()|Gibt das Verhalten für eine bestimmte Verbindung-Instanz zurück. False gibt an, die erste Ausführung Sp_executesql aufruft und keine Anweisung vorbereiten, nach die zweite Ausführung erfolgt, dass Sp_prepexec aufgerufen, und setup tatsächlich einem vorbereiteten Anweisungshandle ab. Die folgenden Ausführungen Aufrufe Sp_execute. Dies erspart die Notwendigkeit Sp_unprepare für vorbereitete Anweisung schließen, wenn die Anweisung nur einmal ausgeführt wird. Der Standardwert für diese Option kann vom aufrufenden setDefaultEnablePrepareOnFirstPreparedStatementCall() geändert werden.|
|"void" setEnablePrepareOnFirstPreparedStatementCall(boolean value)|Gibt das Verhalten für eine bestimmte Verbindung-Instanz. Falls der Wert "false", die erste Ausführung Sp_executesql aufruft und keine Anweisung vorbereiten, nach die zweite Ausführung erfolgt, dass Sp_prepexec aufgerufen, und setup tatsächlich einem vorbereiteten Anweisungshandle ab. Die folgenden Ausführungen Aufrufe Sp_execute. Dies erspart die Notwendigkeit Sp_unprepare für vorbereitete Anweisung schließen, wenn die Anweisung nur einmal ausgeführt wird.|
|Int getServerPreparedStatementDiscardThreshold()|Gibt das Verhalten für eine bestimmte Verbindung-Instanz zurück. Diese Einstellung steuert, wie viele ausstehende verwerfen der Anweisung vorbereitet, die Aktionen (Sp_unprepare) pro Verbindung ausstehenden sein können, bevor ein Aufruf zum Bereinigen der ausstehende Handles auf dem Server ausgeführt wird. Wenn die Einstellung < = 1, unprepare Aktionen sofort auf Schließen die vorbereitete Anweisung ausgeführt werden. Wenn sie, um festgelegt ist {@literal >} 1, diese Aufrufe sind einem Batch zusammengefasst um Mehraufwand aufrufenden Sp_unprepare oft zu vermeiden. Der Standardwert für diese Option kann vom aufrufenden getDefaultServerPreparedStatementDiscardThreshold() geändert werden.|
|"void" setServerPreparedStatementDiscardThreshold(int value)|Gibt das Verhalten für eine bestimmte Verbindung-Instanz. Diese Einstellung steuert, wie viele ausstehende verwerfen der Anweisung vorbereitet, die Aktionen (Sp_unprepare) pro Verbindung ausstehenden sein können, bevor ein Aufruf zum Bereinigen der ausstehende Handles auf dem Server ausgeführt wird. Wenn die Einstellung < = 1 unprepare Aktionen sofort auf Schließen die vorbereitete Anweisung ausgeführt werden. Wenn sie auf > 1 festgelegt ist werden diese Aufrufe zusammengefasst um Mehraufwand Sp_unprepare oft aufrufen zu vermeiden.|

 **SQLServerDataSource**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|"void" setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)|Wenn diese Konfiguration auf "false" festgelegt ist, die erste Ausführung einer vorbereiteten Anweisung Sp_executesql aufruft und keine Anweisung vorbereiten, nach die zweite Ausführung erfolgt, dass Sp_prepexec aufgerufen, und setup tatsächlich einem vorbereiteten Anweisungshandle ab. Die folgenden Ausführungen Aufrufe Sp_execute. Dies erspart die Notwendigkeit Sp_unprepare für vorbereitete Anweisung schließen, wenn die Anweisung nur einmal ausgeführt wird.|
|Boolesche getEnablePrepareOnFirstPreparedStatementCall()|Wenn diese Konfiguration gibt "false", die erste Ausführung einer vorbereiteten Anweisung Sp_executesql aufruft und eine Anweisung nicht vorbereitet werden, nachdem die zweite Ausführung erfolgt, wird der Sp_prepexec, und setup tatsächlich einem vorbereiteten Anweisungshandle. Die folgenden Ausführungen Aufrufe Sp_execute. Dies erspart die Notwendigkeit Sp_unprepare für vorbereitete Anweisung schließen, wenn die Anweisung nur einmal ausgeführt wird.|
|"void" setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Diese Einstellung steuert, wie viele ausstehende verwerfen der Anweisung vorbereitet, die Aktionen (Sp_unprepare) pro Verbindung ausstehenden sein können, bevor ein Aufruf zum Bereinigen der ausstehende Handles auf dem Server ausgeführt wird. Wenn die Einstellung < = 1 unprepare Aktionen sofort auf Schließen die vorbereitete Anweisung ausgeführt werden. Wenn sie, um festgelegt ist {@literal >} 1, die diese Aufrufe einem zusammengefasst Batch sind um Mehraufwand Sp_unprepare oft aufrufen zu vermeiden|
|Int getServerPreparedStatementDiscardThreshold()|Diese Einstellung steuert, wie viele ausstehende verwerfen der Anweisung vorbereitet, die Aktionen (Sp_unprepare) pro Verbindung ausstehenden sein können, bevor ein Aufruf zum Bereinigen der ausstehende Handles auf dem Server ausgeführt wird. Wenn die Einstellung < = 1 unprepare Aktionen sofort auf Schließen die vorbereitete Anweisung ausgeführt werden. Wenn sie, um festgelegt ist {@literal >} 1, die diese Aufrufe einem zusammengefasst Batch sind um Mehraufwand Sp_unprepare oft aufrufen zu vermeiden.|

## <a name="prepared-statement-metatada-caching"></a>Vorbereitete Anweisung Metadaten-Zwischenspeicherung
Ab Version 6.3.0-preview unterstützt Microsoft JDBC-Treiber für SQL Server das Zwischenspeichern von vorbereiteten Anweisung. Vor v6.3.0-Preview Wenn eine Ausführung einer Abfrage, die bereits vorbereitet und im Cache gespeichert wurde führen die gleiche Abfrage erneut aufrufen nicht vorbereiten. Jetzt der Treiber sucht die Abfrage im Cache, und suchen Sie das Handle und führen Sie es mit Sp_execute haben.
Vorbereitete Anweisungsmetadaten-Zwischenspeicherung ist **deaktiviert** standardmäßig. Um es zu aktivieren, müssen Sie die folgende Methode für das Verbindungsobjekt aufrufen:

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Beispiel: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Liste der neuen APIs eingeführt, die durch diese Änderung für die vorbereitete Anweisung Zwischenspeichern von Metadaten

 **SQLServerConnection**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|"void" setDisableStatementPooling(boolean value)|Legt fest, anweisungspools "true" oder "false".|
|Boolesche getDisableStatementPooling()|Gibt true zurück, wenn anweisungspools deaktiviert ist.|
|"void" setStatementPoolingCacheSize(int value)|Gibt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung an. Ein Wert kleiner als 1 bedeutet, dass kein Cache.|
|Int getStatementPoolingCacheSize()|Gibt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung zurück. Ein Wert kleiner als 1 bedeutet, dass kein Cache.|
|Int getStatementHandleCacheEntryCount()|Gibt die aktuelle Anzahl der in einem Pool zusammengefasste vorbereiteter Anweisungshandles zurück.|
|Boolesche isPreparedStatementCachingEnabled()|Ob anweisungspools aktiviert ist oder nicht für diese Verbindung.|

 **SQLServerDataSource**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|"void" setDisableStatementPooling(boolean disableStatementPooling)|Der pooling-Anweisung festgelegt werden, auf "true" oder "false"|
|Boolesche getDisableStatementPooling()|Gibt true zurück, wenn anweisungspools deaktiviert ist.|
|"void" setStatementPoolingCacheSize(int statementPoolingCacheSize)|Gibt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung an. Ein Wert kleiner als 1 bedeutet, dass kein Cache.|
|Int getStatementPoolingCacheSize()|Gibt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung zurück. Ein Wert kleiner als 1 bedeutet, dass kein Cache.|

## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
