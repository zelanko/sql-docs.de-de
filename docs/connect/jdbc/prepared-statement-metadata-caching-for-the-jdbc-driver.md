---
title: Vorbereitetes Caching von Anweisungsmetadaten für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97224f53bb716abe3b79dd00df12d0eed4a63cec
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027841"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Vorbereitetes Caching von Anweisungsmetadaten für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel enthält Informationen zu den beiden Änderungen, die implementiert werden, um die Leistung des Treibers zu verbessern.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Batch Verarbeitung von "Unprepare for Prepared"-Anweisungen
Seit Version 6.1.6-Preview wurde eine Verbesserung der Leistung durch Minimieren von Serverroundtrips zur SQL Server implementiert. Zuvor wurde für jede prepareStatement-Abfrage auch ein Unprepare-aufrusungstyp gesendet. Der Treiber ist nun in der Batch Verarbeitung der Abfrage für die Aufhebung der Vorbereitung bis zum Schwellenwert "serverpreparedstatus". der Standardwert ist 10.

> [!NOTE]  
>  Benutzer können den Standardwert mit der folgenden Methode ändern: setserverpreparedstatus ementverwerdthreshold (int-Wert)

Eine weitere Änderung, die von 6.1.6-Preview eingeführt wurde, ist, dass der Treiber vor diesem Fall immer sp_prepexec aufruft. Nun ruft der Treiber für die erste Ausführung einer vorbereiteten Anweisung sp_executesql auf, und für den Rest führt er sp_prepexec aus und weist ihm ein Handle zu. Weitere Informationen finden Sie [hier](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Benutzer können das Standardverhalten in die früheren Versionen von immer Aufrufen von sp_prepexec ändern, indem Sie enableprepareonfirstpreparedstatuementcall mithilfe der folgenden Methode auf " **true** " festlegen: setenableprepareonfirstpreparedstatuementcall (boolescher Wert )

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Liste der neuen APIs, die mit dieser Änderung eingeführt wurden, für die Batch Verarbeitung von Unprepare für vorbereitete Anweisungen

 **SQLServerConnection**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|Gibt die Anzahl der aktuell ausstehenden vorbereiteten Anweisungs Aktionen für die Vorbereitung zurück.|
|void closeUnreferencedPreparedStatementHandles()|Erzwingt die Ausführung der Unprepare-Anforderungen für alle ausstehenden verworfenen vorbereiteten Anweisungen.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Gibt das Verhalten für eine bestimmte Verbindungs Instanz zurück. Wenn false, ruft die erste Ausführung sp_executesql auf und bereitet eine Anweisung nicht vor, sobald die zweite Ausführung stattfindet, ruft Sie sp_prepexec auf und eingerichtet tatsächlich ein vorbereitetes Anweisungs Handle. Die folgenden Ausführungen rufen sp_execute auf. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird. Der Standardwert für diese Option kann durch Aufrufen von setdefaultenableprepareonfirstpreparedstatuementcall () geändert werden.|
|void "stenableprepareonfirstpreparedstatus" (boolescher Wert)|Gibt das Verhalten für eine bestimmte Verbindungs Instanz an. Wenn value den Wert false hat, ruft die erste Ausführung sp_executesql auf und bereitet eine Anweisung nicht vor, sobald die zweite Ausführung stattfindet, dass Sie sp_prepexec aufruft und tatsächlich ein vorbereitetes Anweisungs Handle eingerichtet. Die folgenden Ausführungen rufen sp_execute auf. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird.|
|int getServerPreparedStatementDiscardThreshold()|Gibt das Verhalten für eine bestimmte Verbindungs Instanz zurück. Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung auf < = 1 festgelegt ist, werden die Aktionen zum Vorbereiten von Aktionen sofort für die vorbereitete Anweisung Close ausgeführt. Wenn Sie auf {@literal >} 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den mehr Aufwand des Aufrufs von sp_unprepare zu vermeiden. Der Standardwert für diese Option kann durch Aufrufen von getdefaultserverpreparedstatus Token () geändert werden.|
|void setServerPreparedStatementDiscardThreshold(int value)|Gibt das Verhalten für eine bestimmte Verbindungs Instanz an. Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung auf < = 1 festgelegt ist, werden die Aktionen zum Vorbereiten der Vorbereitung direkt für die vorbereitete Anweisung Close ausgeführt Wenn Sie auf > 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den mehr Aufwand des Aufrufs von sp_unprepare zu vermeiden.|

 **SQLServerDataSource**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|void setenableprepareonfirstpreparedstatuementcall(boolescher Wert enableprepareonfirstpreparedstatus-Rückruf)|Wenn diese Konfiguration false ist, ruft die erste Ausführung einer vorbereiteten Anweisung sp_executesql auf, und es wird keine Anweisung vorbereitet, sobald die zweite Ausführung stattfindet, ruft Sie sp_prepexec auf und richtet tatsächlich ein vorbereitetes Anweisungs Handle ein. Die folgenden Ausführungen rufen sp_execute auf. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Wenn diese Konfiguration false zurückgibt, wird bei der ersten Ausführung einer vorbereiteten Anweisung sp_executesql aufgerufen, und es wird keine Anweisung vorbereitet. nach der zweiten Ausführung wird sp_prepexec aufgerufen und tatsächlich ein vorbereitetes Anweisungs Handle eingerichtet. Die folgenden Ausführungen rufen sp_execute auf. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird.|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung auf < = 1 festgelegt ist, werden die Aktionen zum Vorbereiten der Vorbereitung direkt für die vorbereitete Anweisung Close ausgeführt Wenn Sie auf {@literal >} 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den mehr Aufwand des Aufrufs von sp_unprepare zu vermeiden.|
|int getServerPreparedStatementDiscardThreshold()|Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung auf < = 1 festgelegt ist, werden die Aktionen zum Vorbereiten der Vorbereitung direkt für die vorbereitete Anweisung Close ausgeführt Wenn Sie auf {@literal >} 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den mehr Aufwand des Aufrufs von sp_unprepare zu vermeiden.|

## <a name="prepared-statement-metatada-caching"></a>Die vorbereitete Anweisung Metadaten Caching
Ab der 6.3.0-Preview-Version unterstützt der Microsoft JDBC-Treiber für SQL Server vorbereitetes Anweisungs Caching. Wenn eine Abfrage, die bereits vorbereitet und im Cache gespeichert wurde, vor v 6.3.0-Preview ausgeführt wird, führt dies nicht zu einer Vorbereitung. Nun sucht der Treiber die Abfrage im Cache und findet das Handle und führt es mit sp_execute aus.
Das Zwischenspeichern vorbereiteter Anweisungs Metadaten ist standardmäßig **deaktiviert** . Um es zu aktivieren, müssen Sie die folgende Methode für das Verbindungs Objekt aufzurufen:

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Beispiel: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Liste der neuen APIs, die mit dieser Änderung eingeführt wurden, für das Zwischenspeichern vorbereiteter Anweisungs Metadaten

 **SQLServerConnection**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|void setdisablestatus Pooling (boolescher Wert)|Legt das Anweisungs Pooling auf true oder false fest.|
|boolean getDisableStatementPooling()|Gibt true zurück, wenn das Anweisungs Pooling deaktiviert ist.|
|void setstatuementpoolingcachesize (int-Wert)|Gibt die Größe des vorbereiteten Anweisungs Caches für diese Verbindung an. Ein Wert kleiner als 1 bedeutet kein Cache.|
|int getStatementPoolingCacheSize()|Gibt die Größe des vorbereiteten Anweisungs Caches für diese Verbindung zurück. Ein Wert kleiner als 1 bedeutet kein Cache.|
|int getStatementHandleCacheEntryCount()|Gibt die aktuelle Anzahl von gepoolten vorbereiteten Anweisungs Handles zurück.|
|boolean isPreparedStatementCachingEnabled()|Gibt an, ob das Anweisungs Pooling für diese Verbindung aktiviert ist.|

 **SQLServerDataSource**
 
|Methode „New“|und Beschreibung|  
|-----------|-----------------|  
|void setdisablestatus Pooling (Boolean disablestatus Pooling)|Legt das Anweisungs Pooling auf true oder false fest.|
|boolean getDisableStatementPooling()|Gibt true zurück, wenn das Anweisungs Pooling deaktiviert ist.|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|Gibt die Größe des vorbereiteten Anweisungs Caches für diese Verbindung an. Ein Wert kleiner als 1 bedeutet kein Cache.|
|int getStatementPoolingCacheSize()|Gibt die Größe des vorbereiteten Anweisungs Caches für diese Verbindung zurück. Ein Wert kleiner als 1 bedeutet kein Cache.|

## <a name="see-also"></a>Siehe auch  
 [Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
