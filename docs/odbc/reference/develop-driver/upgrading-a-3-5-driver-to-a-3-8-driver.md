---
title: Aktualisieren eines 3.5 Treibers auf einen 3.8-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df2fa8df9af317bd76b2d7f10e50f7cc937e4660
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63254151"
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>Aktualisieren eines 3.5 Treibers auf einen 3.8-Treiber
Dieses Thema enthält Richtlinien und Überlegungen zum Upgrade von einer ODBC 3.5 Treibers auf einen ODBC 3.8-Treiber.  
  
##### <a name="version-numbers"></a>Versionsnummern  
 Die folgenden Richtlinien beziehen sich auf Versionsnummern:  
  
-   Ein Treiber muss SQL_OV_ODBC3_80 für SQL_ATTR_ODBC_VERSION, wird SQL_ERROR zurückgegeben, für andere Werte als SQL_OV_ODBC2 SQL_OV_ODBC3 fest und SQL_OV_ODBC3_80 unterstützen. Zukünftige Versionen des Treiber-Managers der Annahme, dass ein Treiber eine ODBC-Compliance-Ebene unterstützt, wenn der Treiber gibt SQL_SUCCESS aus zurück, [SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md).  
  
-   Ein Version 3.8-Treiber sollte 03.80 aus zurückgeben **SQLGetInfo** Wenn SQL_DRIVER_ODBC_VER übergeben wird, um *Informationsart*. Jedoch ältere Treiber-Manager verwenden, die in früheren Versionen von Microsoft Windows enthalten waren, behandelt den Treiber als einen Treiber der Version 3.5, und eine Warnung ausgeben.  
  
     In Windows 7 ist die Treiber-Manager-Version 03.80. In Windows 8 ist die Treiber-Manager-Version 03.81 über die SQLGetInfo SQL_DM_VER (*Informationsart* Parameter). SQL_ODBC_VER gibt die Version 03.80 sowohl Windows 7 und Windows 8.  
  
##### <a name="driver-specific-c-data-types"></a>Treiber-spezifischen C-Datentypen  
 Ein Treiber kann C-Datentypen angepasst haben, wenn es mit einer Version 3.8-ODBC-Anwendung funktioniert. (Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Allerdings besteht keine Notwendigkeit für einen 3.8-Treiber implementiert alle treiberspezifischen C-Typen. Aber der Treiber sollte noch der bereichsüberprüfung C-Typen ausführen; der Treiber-Manager, die für 3.8-Treiber keine. Um Treiberentwicklung zu erleichtern, kann der Wert der Treiber bestimmte, C-Datentyp im folgenden Format definiert werden:  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute  
 Wenn Sie einen neuen Treiber zu entwickeln, sollten Sie den Treiber spezifischen Bereich für die Datentypen, deskriptortypen, Informationstypen, Diagnosetypen und Attribute verwenden. Treiber-spezifische Bereiche und ihre Basistyp-Werte finden Sie im [treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
##### <a name="connection-pooling"></a>Verbindungspooling  
 Für eine bessere Verwaltung des Verbindungspoolings, führt das ODBC 3.8 das SQL_ATTR_RESET_CONNECTION Verbindungsattribut in **SQLSetConnectAttr**. SQL_RESET_CONNECTION_YES ist der einzige gültige Wert für dieses Attribut. SQL_ATTR_RESET_CONNECTION wird festgelegt werden, kurz bevor der Treiber-Manager eine Verbindung im Verbindungspool, setzt, können den Treiber an, die andere Verbindungsattribute auf ihre Standardwerte zurückgesetzt.  
  
 Um unnötige Kommunikation mit dem Server zu vermeiden, kann ein Treiber das Verbindungsattribut, bis der nächsten Kommunikation mit dem Remoteserver, zurücksetzen, nachdem die Verbindung aus dem Pool wiederverwendet wird, verzögern.  
  
 Beachten Sie, dass SQL_ATTR_RESET_CONNECTION nur bei der Kommunikation zwischen der Treiber-Manager und einen Treiber verwendet wird. Dieses Attribut kann nicht direkt eine Anwendung festgelegt werden. Dieses Verbindungsattribut müssen alle Version 3.8-Treiber implementiert werden.  
  
##### <a name="streamed-output-parameters"></a>Gestreamte Output-Parameter  
 ODBC 3.8-Version führt die gestreamte Output-Parameter, eine stärker skalierbare Möglichkeit zum Abrufen der Output-Parameter. (Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Um dieses Feature zu unterstützen, ein Treiber sollte festgelegt SQL_GD_OUTPUT_PARAMS im Rückgabewert bei SQL_GETDATA_EXTENSIONS ist die *Informationsart* in einem **SQLGetInfo** aufrufen. Unterstützung für eine SQL-Typ mit gestreamte Output-Parameter muss in der Treiber implementiert werden. Der Treiber-Manager generiert keine Fehler ein ungültiger SQL-Typ. Die SQL-Typen, die gestreamte Output-Parameter unterstützen in der Treiber definiert ist.  
  
 Ein Treiber sollte SQL_ERROR zurück, wenn die Anwendung verwendet **SQLGetData** Parameter abgerufen, die nicht identisch mit den vom Parameter **SQLParamData**.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Asynchrone Ausführung für Verbindungsvorgänge (Abrufmethode)  
 Treiber kann asynchrone Unterstützung für verschiedene Verbindungsvorgänge aktivieren.  
  
 ODBC unterstützt ab Windows 7 der Abrufmethode (Weitere Informationen finden Sie unter [asynchrone Ausführung (Methode abrufen)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Besteht keine Notwendigkeit für eine Version 3.8-ODBC-Treiber zum Implementieren asynchroner Vorgänge auf Verbindungshandles. Selbst wenn ein Treiber nicht asynchroner Vorgänge auf Verbindungshandles implementiert werden, sollte der Treiber trotzdem die SQL_ASYNC_DBC_FUNCTIONS implementieren *Informationsart* und zurückgeben **SQL_ASYNC_DBC_NOT_CAPABLE**.  
  
 Wenn asynchrone Verbindungsvorgänge aktiviert sind, ist die Ausführungszeit eines Vorgangs für die Verbindung die Gesamtzeit für alle wiederholte Aufrufe. Bei der letzten des Anrufs gewählt wird Wiederholung, nachdem die gesamte Zeit wurde durch das Verbindungsattribut SQL_ATTR_CONNECTION_TIMEOUT festgelegten Wert überschritten, und der Vorgang wurde nicht beendet, wird der Treiber gibt SQL_ERROR zurück, und einen Diagnosedatensatz mit SQLState HYT01 protokolliert und die Meldung "das Verbindungstimeout ist abgelaufen". Es gibt kein Timeout auf, wenn der Vorgang abgeschlossen.  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle-Funktion  
 Unterstützt ODBC 3.8 [SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md), womit sowohl Verbindungs- und Vorgänge abzubrechen. Ein Treiber, unterstützt **SQLCancelHandle** müssen die Funktion "Exportieren". Ein Treiber sollte nicht abgebrochen werden, alle synchron oder asynchron-Verbindung-Funktionen, die ausgeführt wird, wenn die Anwendung ruft **SQLCancel** oder **SQLCancelHandle** für ein Anweisungshandle. Auf ähnliche Weise ein Treiber nicht abbrechen soll alle synchron oder asynchron Anweisung-Funktionen, die ausgeführt wird, wenn eine Anwendung ruft **SQLCancelHandle** auf dem Verbindungshandle. Darüber hinaus ein Treiber sollte nicht den Vorgang abbrechen, zum Durchsuchen (**SQLBrowseConnect** wird SQL_NEED_DATA zurückgegeben.) Wenn die Anwendung ruft **SQLCancelHandle** auf dem Verbindungshandle. In diesen Fällen sollte ein Treiber HY010, "Fehler bei Funktionssequenz" zurückgeben.  
  
 Es ist nicht erforderlich, um beide unterstützen **SQLCancelHandle** und asynchrone Verbindungsvorgänge zur gleichen Zeit. Ein-Treiber unterstützt asynchrone Verbindungsvorgängen sendet, nicht jedoch **SQLCancelHandle**, oder umgekehrt.  
  
##### <a name="suspended-connections"></a>Unterbrochene Verbindungen  
 Der ODBC 3.8-Treiber-Manager kann eine Verbindung in angehaltenen Zustand versetzen. Eine Anwendung ruft **SQLDisconnect** , wenn der Verbindung zugeordnete Ressourcen freigegeben. In diesem Fall sollten ein Treiber so viele Ressourcen wie möglich freizugeben, ohne die Überprüfung des Status der Verbindung. Weitere Informationen zu den Zustand "angehalten", finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling  
 ODBC in Windows 8 kann Treiber für den Pool Verbindungsverhalten angepasst. Weitere Informationen finden Sie unter [Treiberfähiges Verbindungspooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Asynchrone Ausführung (Benachrichtigungsmethode)  
 ODBC 3.8 unterstützt die Benachrichtigungsmethode für asynchrone Vorgänge ist verfügbar unter Windows 8 ab. Weitere Informationen finden Sie unter [asynchrone Ausführung (Benachrichtigungsmethode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln einen ODBC-Treiber](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Von Microsoft gelieferte ODBC-Treiber](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [What's New in ODBC 3.8 (Neues in ODBX 3.8)](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
