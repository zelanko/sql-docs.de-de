---
title: Aktualisieren eines 3.5-Treibers auf einen 3.8-Treiber | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ffba36ac-d22e-40b9-911a-973fa9e10bd3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dcd01d050e806b733d75c54058945d367a33d6a7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294431"
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>Aktualisieren eines 3.5 Treibers auf einen 3.8-Treiber
Dieses Thema enthält Richtlinien und Überlegungen zum Aktualisieren eines ODBC 3.5-Treibers auf einen ODBC 3.8-Treiber.  
  
##### <a name="version-numbers"></a>Versionsnummern  
 Die folgenden Richtlinien beziehen sich auf Versionsnummern:  
  
-   Ein Treiber sollte SQL_OV_ODBC3_80 für SQL_ATTR_ODBC_VERSION unterstützen und SQL_ERROR für andere Werte als SQL_OV_ODBC2, SQL_OV_ODBC3 und SQL_OV_ODBC3_80 zurückgeben. Zukünftige Versionen des Treiber-Managers gehen davon aus, dass ein Treiber eine ODBC-Kompatibilitätsebene unterstützt, wenn der Treiber SQL_SUCCESS von [SQLSetEnvAttr Function](../../../odbc/reference/syntax/sqlsetenvattr-function.md)zurückgibt.  
  
-   Ein Treiber der Version 3.8 sollte 03.80 von **SQLGetInfo** zurückgeben, wenn SQL_DRIVER_ODBC_VER an *InfoType*übergeben wird. Ältere Treiber-Manager, die in älteren Versionen von Microsoft Windows enthalten waren, behandeln den Treiber jedoch als Treiber der Version 3.5 und geben eine Warnung aus.  
  
     In Windows 7 ist die Treiber-Manager-Version 03.80. In Windows 8 ist die Treiber-Manager-Version 03.81 über den SQLGetInfo SQL_DM_VER (*InfoType-Parameter).* SQL_ODBC_VER meldet die Version als 03.80 in Windows 7 und Windows 8.  
  
##### <a name="driver-specific-c-data-types"></a>Treiberspezifische C-Datentypen  
 Ein Treiber kann über angepasste C-Datentypen verfügen, wenn er mit einer ODBC-Anwendung der Version 3.8 funktioniert. (Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Es ist jedoch nicht erforderlich, dass ein 3.8-Treiber treiberspezifische C-Typen implementiert. Der Fahrer sollte jedoch weiterhin die Bereichsprüfung der C-Typen durchführen; Der Treiber-Manager tut dies nicht für 3.8-Treiber. Um die Treiberentwicklung zu erleichtern, kann der Wert des treiberspezifischen C-Datentyps im folgenden Format definiert werden:  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute  
 Beim Entwickeln eines neuen Treibers sollten Sie den treiberspezifischen Bereich für Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute verwenden. Treiberspezifische Bereiche und deren Basistypwerte werden in [Treiberspezifische Datentypen, Deskriptortypen, Informationstypen, Diagnosetypen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)erläutert.  
  
##### <a name="connection-pooling"></a>Verbindungspooling  
 Zur besseren Verwaltung des Verbindungspoolings führt ODBC 3.8 das SQL_ATTR_RESET_CONNECTION Verbindungsattribut in **SQLSetConnectAttr**ein. SQL_RESET_CONNECTION_YES ist der einzige gültige Wert für dieses Attribut. SQL_ATTR_RESET_CONNECTION wird kurz vor dem Stellendesherschalten des Treiber-Managers im Verbindungspool festgelegt, sodass der Treiber die anderen Verbindungsattribute auf seine Standardwerte zurücksetzen kann.  
  
 Um unnötige Kommunikation mit dem Server zu vermeiden, kann ein Treiber das Zurücksetzen des Verbindungsattributs bis zur nächsten Kommunikation mit dem Remoteserver verschieben, nachdem die Verbindung vom Pool wiederverwendet wurde.  
  
 Beachten Sie, dass SQL_ATTR_RESET_CONNECTION nur in der Kommunikation zwischen dem Treiber-Manager und einem Treiber verwendet wird. Eine Anwendung kann dieses Attribut nicht direkt festlegen. Alle Treiber der Version 3.8 sollten dieses Verbindungsattribut implementieren.  
  
##### <a name="streamed-output-parameters"></a>Gestreamte Ausgabeparameter  
 ODBC-Version 3.8 führt gestreamte Ausgabeparameter ein, eine skalierbarere Möglichkeit, Ausgabeparameter abzurufen. (Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mithilfe von SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Um diese Funktion zu unterstützen, sollte ein Treiber SQL_GD_OUTPUT_PARAMS im Rückgabewert festlegen, wenn SQL_GETDATA_EXTENSIONS *der InfoType* in einem **SQLGetInfo-Aufruf** ist. Die Unterstützung für einen SQL-Typ mit gestreamten Ausgabeparametern muss im Treiber implementiert werden. Der Treiber-Manager generiert keinen Fehler für einen ungültigen SQL-Typ. Die SQL-Typen, die gestreamte Ausgabeparameter unterstützen, sind im Treiber definiert.  
  
 Ein Treiber sollte SQL_ERROR zurückgeben, wenn die Anwendung **SQLGetData** verwendet hat, um einen Parameter abzurufen, der nicht mit dem von **SQLParamData**zurückgegebenen Parameter identisch ist.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Asynchrone Ausführung für Verbindungsvorgänge (Polling-Methode)  
 Ein Treiber kann asynchrone Unterstützung für verschiedene Verbindungsvorgänge aktivieren.  
  
 Ab Windows 7 unterstützt ODBC die Polling-Methode (weitere Informationen finden Sie unter [Asynchrone Ausführung (Polling-Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Es ist nicht erforderlich, dass ein ODBC-Treiber der Version 3.8 asynchrone Vorgänge für Verbindungshandles implementiert. Auch wenn ein Treiber keine asynchronen Vorgänge für Verbindungshandles implementiert, sollte der Treiber die SQL_ASYNC_DBC_FUNCTIONS *InfoType* implementieren und **SQL_ASYNC_DBC_NOT_CAPABLE**zurückgeben.  
  
 Wenn asynchrone Verbindungsvorgänge aktiviert sind, ist die Laufzeit eines Verbindungsvorgangs die Gesamtzeit aller wiederholten Aufrufe. Wenn der letzte wiederholte Aufruf erfolgt, nachdem die Gesamtzeit den vom SQL_ATTR_CONNECTION_TIMEOUT Verbindungsattribut festgelegten Wert überschritten hat und der Vorgang noch nicht abgeschlossen ist, gibt der Treiber SQL_ERROR zurück und protokolliert einen Diagnosedatensatz mit SQLState HYT01 und die Meldung "Verbindungstimeout abgelaufen". Es gibt kein Timeout, wenn der Vorgang abgeschlossen ist.  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle-Funktion  
 ODBC 3.8 unterstützt [die SQLCancelHandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md), die zum Abbrechen von Verbindungs- und Anweisungsvorgängen verwendet wird. Ein Treiber, der **SQLCancelHandle** unterstützt, muss die Funktion exportieren. Ein Treiber sollte keine synchrone oder asynchrone Verbindungsfunktion abbrechen, die ausgeführt wird, wenn die Anwendung **SQLCancel** oder **SQLCancelHandle** für ein Anweisungshandle aufruft. Ebenso sollte ein Treiber keine synchrone oder asynchrone Anweisungsfunktion abbrechen, die ausgeführt wird, wenn eine Anwendung **SQLCancelHandle** für das Verbindungshandle aufruft. Außerdem sollte ein Treiber den Browservorgang nicht abbrechen **(SQLBrowseConnect** gibt SQL_NEED_DATA zurück), wenn die Anwendung **SQLCancelHandle** für das Verbindungshandle aufruft. In diesen Fällen sollte ein Treiber HY010, "Funktionssequenzfehler" zurückgeben.  
  
 Es ist nicht erforderlich, sowohl **SQLCancelHandle** als auch asynchrone Verbindungsvorgänge gleichzeitig zu unterstützen. Ein Treiber kann asynchrone Verbindungsvorgänge unterstützen, jedoch nicht **SQLCancelHandle**oder umgekehrt.  
  
##### <a name="suspended-connections"></a>Angehaltene Verbindungen  
 Der ODBC 3.8 Treiber-Manager kann eine Verbindung in den angehaltenen Zustand versetzen. Eine Anwendung ruft **SQLDisconnect** auf, um Ressourcen freizugeben, die der Verbindung zugeordnet sind. In diesem Fall sollte ein Treiber versuchen, so viele Ressourcen wie möglich freizugeben, ohne den Status der Verbindung zu überprüfen. Weitere Informationen zum angehaltenen Zustand finden Sie unter [SQLEndTran-Funktion](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling  
 ODBC in Windows 8 ermöglicht es Treibern, das Verhalten des Verbindungspools anzupassen. Weitere Informationen finden Sie unter [Treiber-Aware Connection Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Asynchrone Ausführung (Benachrichtigungsmethode)  
 ODBC 3.8 unterstützt die Benachrichtigungsmethode für asynchrone Vorgänge, die ab Windows 8 verfügbar ist. Weitere Informationen finden Sie unter [Asynchrone Ausführung (Benachrichtigungsmethode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Von Microsoft gelieferte ODBC-Treiber](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
