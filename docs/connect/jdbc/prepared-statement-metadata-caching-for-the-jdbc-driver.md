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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "69027841"
---
# <a name="prepared-statement-metadata-caching-for-the-jdbc-driver"></a>Vorbereitetes Caching von Anweisungsmetadaten für den JDBC-Treiber
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel enthält Informationen zu den beiden Änderungen, die implementiert werden, um die Leistung des Treibers zu verbessern.

## <a name="batching-of-unprepare-for-prepared-statements"></a>Rückgängigmachen der Vorbereitung für vorbereitete Anweisungen in Batchverarbeitung
Seit Version 6.1.6-preview wurde eine Verbesserung der Leistung durch Minimieren von Serverroundtrips in SQL Server implementiert. Zuvor wurde für jede prepareStatement-Abfrage auch ein Aufruf zum Rückgängigmachen der Vorbereitung gesendet. Der Treiber führt nun eine Batchverarbeitung von Abfragen für das Rückgängigmachen der Vorbereitung bis zum Schwellenwert „ServerPreparedStatementDiscardThreshold“ (Standardwert 10) durch.

> [!NOTE]  
>  Benutzer können den Standardwert mit der folgenden Methode ändern: setServerPreparedStatementDiscardThreshold(int-Wert)

Eine weitere Änderung, die von 6.1.6-preview eingeführt wurde, ist, dass der Treiber vorher immer „sp_prepexec“ aufruft. Nun ruft der Treiber für die erste Ausführung einer vorbereiteten Anweisung „sp_executesql“ auf, und für den Rest führt er „sp_prepexec“ aus und weist ihm ein Handle zu. Weitere Informationen finden Sie [hier](https://github.com/Microsoft/mssql-jdbc/wiki/PreparedStatement-metadata-caching).

> [!NOTE]  
>  Benutzer können das Standardverhalten früherer Versionen wiederherstellen, sodass immer „sp_prepexec“ aufgerufen wird, indem sie enablePrepareOnFirstPreparedStatementCall mithilfe der Methode setEnablePrepareOnFirstPreparedStatementCall(boolescher Wert) auf **true** festlegen.

### <a name="list-of-the-new-apis-introduced-with-this-change-for-batching-of-unprepare-for-prepared-statements"></a>Liste der neuen, mit dieser Änderung eingeführten APIs für das Rückgängigmachen der Vorbereitung für vorbereitete Anweisungen in Batchverarbeitung

 **SQLServerConnection**
 
|Methode „New“|Beschreibung|  
|-----------|-----------------|  
|int getDiscardedServerPreparedStatementCount()|Gibt die Anzahl der aktuell ausstehenden Aktionen zum Rückgängigmachen der Vorbereitung für vorbereitete Anweisungen zurück.|
|void closeUnreferencedPreparedStatementHandles()|Erzwingt, dass Anforderungen zum Rückgängigmachen der Vorbereitung für ausstehende verworfene vorbereitete Anweisungen ausgeführt werden.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Gibt das Verhalten einer bestimmten Verbindungsinstanz an. Bei „false“ ruft die erste Ausführung „sp_executesql“ auf und bereitet keine Anweisung vor. Sobald die zweite Ausführung erfolgt, ruft diese „sp_prepexec“ auf und richtet tatsächlich ein Handle für vorbereitete Anweisungen ein. Bei den folgenden Ausführungen wird „sp_execute“ aufgerufen. Dadurch ist „sp_unprepare“ nicht mehr für den Abschluss einer vorbereiteten Anweisung erforderlich, falls diese nur einmal ausgeführt wird. Der Standardwert für diese Option kann durch Aufrufen von setDefaultEnablePrepareOnFirstPreparedStatementCall() geändert werden.|
|void setEnablePrepareOnFirstPreparedStatementCall(boolescher Wert)|Mit dieser Methode geben Sie das Verhalten einer bestimmten Verbindungsinstanz an. Bei „false“ ruft die erste Ausführung „sp_executesql“ auf und bereitet keine Anweisung vor. Sobald die zweite Ausführung erfolgt, ruft diese „sp_prepexec“ auf und richtet tatsächlich ein Handle für vorbereitete Anweisungen ein. Bei den folgenden Ausführungen wird „sp_execute“ aufgerufen. Dadurch ist „sp_unprepare“ nicht mehr für den Abschluss einer vorbereiteten Anweisung erforderlich, falls diese nur einmal ausgeführt wird.|
|int getServerPreparedStatementDiscardThreshold()|Gibt das Verhalten einer bestimmten Verbindungsinstanz an. Mit dieser Einstellung steuern Sie, wie viele ausstehende Aktionen zum Verwerfen vorbereiteter Anweisungen (sp_unprepare) pro Verbindung vorhanden sein dürfen, bevor ein Aufruf zum Bereinigen der ausstehenden Handles auf dem Server ausgeführt wird. Wenn diese Einstellung <= 1 ist, werden Aktionen zum Rückgängigmachen der Vorbereitung sofort nach Abschluss der vorbereiteten Anweisung ausgeführt. Wenn die Einstellung auf {@literal >} 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den Aufwand zu häufiger Aufrufe von „sp_unprepare“ zu vermeiden. Der Standardwert für diese Option kann durch Aufrufen von getDefaultServerPreparedStatementDiscardThreshold() geändert werden.|
|void setServerPreparedStatementDiscardThreshold(int value)|Mit dieser Methode geben Sie das Verhalten einer bestimmten Verbindungsinstanz an. Mit dieser Einstellung steuern Sie, wie viele ausstehende Aktionen zum Verwerfen vorbereiteter Anweisungen (sp_unprepare) pro Verbindung vorhanden sein dürfen, bevor ein Aufruf zum Bereinigen der ausstehenden Handles auf dem Server ausgeführt wird. Wenn diese Einstellung <= 1 ist, werden Aktionen zum Rückgängigmachen der Vorbereitung sofort nach Abschluss der vorbereiteten Anweisung ausgeführt. Wenn die Einstellung auf > 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den Aufwand zu häufiger Aufrufe von „sp_unprepare“ zu vermeiden.|

 **SQLServerDataSource**
 
|Methode „New“|Beschreibung|  
|-----------|-----------------|  
|void setEnablePrepareOnFirstPreparedStatementCall(boolesch enablePrepareOnFirstPreparedStatementCall)|Wenn diese Konfiguration „false“ ist, ruft die erste Ausführung einer vorbereiteten Anweisung „sp_executesql“ auf und erstellt keine vorbereitete Anweisung. Sobald die zweite Ausführung erfolgt, ruft diese „sp_prepexec“ auf und richtet tatsächlich ein Handle für eine vorbereitete Anweisung ein. Bei den folgenden Ausführungen wird „sp_execute“ aufgerufen. Dadurch ist „sp_unprepare“ nicht mehr für den Abschluss einer vorbereiteten Anweisung erforderlich, falls diese nur einmal ausgeführt wird.|
|boolean getEnablePrepareOnFirstPreparedStatementCall()|Wenn diese Konfiguration „false“ zurückgibt, ruft die erste Ausführung einer vorbereiteten Anweisung „sp_executesql“ auf und erstellt keine vorbereitete Anweisung. Sobald die zweite Ausführung erfolgt, ruft diese „sp_prepexec“ auf und richtet tatsächlich ein Handle für eine vorbereitete Anweisung ein. Bei den folgenden Ausführungen wird „sp_execute“ aufgerufen. Dadurch ist sp_unprepare nicht mehr für den Abschluss einer vorbereiteten Anweisung erforderlich, falls die Anweisung nur einmal ausgeführt wird.|
|void setServerPreparedStatementDiscardThreshold(int serverPreparedStatementDiscardThreshold)|Mit dieser Einstellung steuern Sie, wie viele ausstehende Aktionen zum Verwerfen vorbereiteter Anweisungen (sp_unprepare) pro Verbindung vorhanden sein dürfen, bevor ein Aufruf zum Bereinigen der ausstehenden Handles auf dem Server ausgeführt wird. Wenn diese Einstellung <= 1 ist, werden Aktionen zum Rückgängigmachen der Vorbereitung sofort nach Abschluss der vorbereiteten Anweisung ausgeführt. Wenn die Einstellung auf {@literal >} 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den Aufwand zu häufiger Aufrufe von „sp_unprepare“ zu vermeiden.|
|int getServerPreparedStatementDiscardThreshold()|Mit dieser Einstellung steuern Sie, wie viele ausstehende Aktionen zum Verwerfen vorbereiteter Anweisungen (sp_unprepare) pro Verbindung vorhanden sein dürfen, bevor ein Aufruf zum Bereinigen der ausstehenden Handles auf dem Server ausgeführt wird. Wenn diese Einstellung <= 1 ist, werden Aktionen zum Rückgängigmachen der Vorbereitung sofort nach Abschluss der vorbereiteten Anweisung ausgeführt. Wenn die Einstellung auf {@literal >} 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den Aufwand zu häufiger Aufrufe von „sp_unprepare“ zu vermeiden.|

## <a name="prepared-statement-metatada-caching"></a>Zwischenspeichern von Metadaten zu vorbereiteten Anweisungen
Ab der 6.3.0-preview-Version unterstützt der Microsoft JDBC-Treiber für SQL Server das Zwischenspeichern vorbereiteter Anweisungen. Wenn vor v6.3.0-preview eine Abfrage ausgeführt wurde, die bereits vorbereitet war und im Cache gespeichert wurde, führte der erneute Aufruf derselben Abfrage nicht zu deren Vorbereitung. Nun sucht der Treiber die Abfrage im Cache, findet das Handle und führt es mit „sp_execute“ aus.
Das Zwischenspeichern von Metadaten zu vorbereiteten Anweisungen ist **standardmäßig** deaktiviert. Um es zu aktivieren, müssen Sie die folgende Methode für das Verbindungsobjekt aufrufen:

`setStatementPoolingCacheSize(int value)   //value is the desired cache size (any value bigger than 0)`
`setDisableStatementPooling(boolean value) //false allows the caching to take place`

Beispiel: `connection.setStatementPoolingCacheSize(10)`
`connection.setDisableStatementPooling(false)`

### <a name="list-of-the-new-apis-introduced-with-this-change-for-prepared-statement-metadata-caching"></a>Liste der neuen, mit dieser Änderung eingeführten APIs für das Zwischenspeichern von Metadaten zu vorbereiteten Anweisungen

 **SQLServerConnection**
 
|Methode „New“|Beschreibung|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolescher Wert)|Diese Methode legt das Anweisungspooling auf „true“ oder „false“ fest.|
|boolean getDisableStatementPooling()|Gibt „true“ zurück, wenn das Anweisungspooling deaktiviert ist.|
|void setStatementPoolingCacheSize(int-Wert)|Legt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung fest. Bei einem kleineren Wert als 1 wird kein Cache verwendet.|
|int getStatementPoolingCacheSize()|Gibt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung zurück. Bei einem kleineren Wert als 1 wird kein Cache verwendet.|
|int getStatementHandleCacheEntryCount()|Gibt die aktuelle Anzahl von Handles für vorbereitete Anweisungen zurück, die in einem Pool zusammengefasst sind.|
|boolean isPreparedStatementCachingEnabled()|Gibt zurück, ob für diese Verbindung Anweisungspooling aktiviert ist|

 **SQLServerDataSource**
 
|Methode „New“|Beschreibung|  
|-----------|-----------------|  
|void setDisableStatementPooling(boolesch disableStatementPooling)|Legt das Anweisungspooling auf „true“ oder „false“ fest.|
|boolean getDisableStatementPooling()|Gibt „true“ zurück, wenn das Anweisungspooling deaktiviert ist.|
|void setStatementPoolingCacheSize(int statementPoolingCacheSize)|Legt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung fest. Bei einem kleineren Wert als 1 wird kein Cache verwendet.|
|int getStatementPoolingCacheSize()|Gibt die Größe des Caches für vorbereitete Anweisungen für diese Verbindung zurück. Bei einem kleineren Wert als 1 wird kein Cache verwendet.|

## <a name="see-also"></a>Weitere Informationen  
 [Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
