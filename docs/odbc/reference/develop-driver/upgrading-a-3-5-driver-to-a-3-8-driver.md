---
title: Aktualisieren eines 3,5-Treibers auf einen 3,8-Treiber | Microsoft-Dokumentation
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
ms.openlocfilehash: 97b100b1ade97e1e88cf1421f09a7723412c8b76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915490"
---
# <a name="upgrading-a-35-driver-to-a-38-driver"></a>Aktualisieren eines 3.5 Treibers auf einen 3.8-Treiber
Dieses Thema enthält Richtlinien und Überlegungen zum Aktualisieren eines ODBC 3,5-Treibers auf einen ODBC 3,8-Treiber.  
  
##### <a name="version-numbers"></a>Versionsnummern  
 Die folgenden Richtlinien beziehen sich auf die Versionsnummern:  
  
-   Ein Treiber sollte SQL_OV_ODBC3_80 für SQL_ATTR_ODBC_VERSION unterstützen und SQL_ERROR für andere Werte als SQL_OV_ODBC2, SQL_OV_ODBC3 und SQL_OV_ODBC3_80 zurückgeben. In zukünftigen Versionen des Treiber-Managers wird davon ausgegangen, dass ein Treiber eine ODBC-Kompatibilitäts Stufe unterstützt, wenn der Treiber SQL_SUCCESS von der [SQLSetEnvAttr-Funktion](../../../odbc/reference/syntax/sqlsetenvattr-function.md)zurückgibt.  
  
-   Ein Treiber der Version 3,8 sollte 03,80 von **SQLGetInfo** zurückgeben, wenn SQL_DRIVER_ODBC_VER an *InfoType*weitergeleitet wird. Ältere Treiber-Manager, die in älteren Versionen von Microsoft Windows enthalten waren, behandeln den Treiber jedoch als Treiber der Version 3,5 und geben eine Warnung aus.  
  
     In Windows 7 ist die Treiber-Manager-Version 03,80. In Windows 8 ist die Treiber-Manager-Version 03,81 über den SQLGetInfo-SQL_DM_VER (*InfoType* -Parameter). SQL_ODBC_VER meldet die Version sowohl in Windows 7 als auch in Windows 8 als 03,80.  
  
##### <a name="driver-specific-c-data-types"></a>Treiber spezifische C-Datentypen  
 Ein Treiber kann angepasste C-Datentypen aufweisen, wenn er mit einer ODBC-Anwendung der Version 3,8 funktioniert. (Weitere Informationen finden Sie unter [C-Datentypen in ODBC](../../../odbc/reference/develop-app/c-data-types-in-odbc.md).) Es ist jedoch nicht erforderlich, dass ein 3,8-Treiber Treiber spezifische C-Typen implementiert. Der Treiber sollte jedoch weiterhin die Bereichs Überprüfung von C-Typen durchführen. der Treiber-Manager wird nicht für 3,8-Treiber verwendet. Um die Treiberentwicklung zu vereinfachen, kann der Wert des treiberspezifischen C-Datentyps im folgenden Format definiert werden:  
  
```  
SQL_DRIVER_C_TYPE_BASE+0, SQL_DRIVER_C_TYPE_BASE+1  
```  
  
##### <a name="driver-specific-data-types-descriptor-types-information-types-diagnostic-types-and-attributes"></a>Treiber spezifische Datentypen, deskriptortypen, Informationstypen, Diagnose Typen und Attribute  
 Wenn Sie einen neuen Treiber entwickeln, sollten Sie den treiberspezifischen Bereich für Datentypen, deskriptortypen, Informationstypen, Diagnose Typen und Attribute verwenden. Treiber spezifische Bereiche und deren Basistyp Werte werden unter [Treiber spezifische Datentypen, deskriptortypen, Informationstypen, Diagnose Typen und Attribute](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)erläutert.  
  
##### <a name="connection-pooling"></a>Verbindungspooling  
 Zur besseren Verwaltung von Verbindungspooling führt ODBC 3,8 das SQL_ATTR_RESET_CONNECTION Connection-Attribut in **SQLSetConnectAttr**ein. SQL_RESET_CONNECTION_YES ist der einzige gültige Wert für dieses Attribut. SQL_ATTR_RESET_CONNECTION wird festgelegt, kurz bevor der Treiber-Manager eine Verbindung in den Verbindungspool einfügt, sodass der Treiber die anderen Verbindungs Attribute auf die Standardwerte zurücksetzen kann.  
  
 Um unnötige Kommunikation mit dem Server zu vermeiden, kann ein Treiber das Zurücksetzen des Verbindungs Attributs bis zur nächsten Kommunikation mit dem Remote Server verzögern, nachdem die Verbindung aus dem Pool wieder verwendet wurde.  
  
 Beachten Sie, dass SQL_ATTR_RESET_CONNECTION nur bei der Kommunikation zwischen dem Treiber-Manager und einem Treiber verwendet wird. Eine Anwendung kann dieses Attribut nicht direkt festlegen. Alle Treiber der Version 3,8 sollten dieses Verbindungs Attribut implementieren.  
  
##### <a name="streamed-output-parameters"></a>Ausgabeparameter gestreamt  
 In ODBC, Version 3,8, werden Streaming-Ausgabeparameter eingeführt, eine skalierbare Möglichkeit zum Abrufen von Ausgabeparametern. (Weitere Informationen finden Sie unter [Abrufen von Ausgabeparametern mit SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).) Um diese Funktion zu unterstützen, sollte ein Treiber SQL_GD_OUTPUT_PARAMS im Rückgabewert festlegen, wenn SQL_GETDATA_EXTENSIONS der *InfoType* in einem **SQLGetInfo-Befehl** ist. Die Unterstützung für einen SQL-Typ mit gestreuten Ausgabeparametern muss im Treiber implementiert werden. Der Treiber-Manager generiert keinen Fehler für einen ungültigen SQL-Typ. Die SQL-Typen, die Streaming-Ausgabeparameter unterstützen, werden im Treiber definiert.  
  
 Ein Treiber sollte SQL_ERROR zurückgeben, wenn die Anwendung **SQLGetData** zum Abrufen eines Parameters verwendet hat, der nicht der gleiche ist wie der von **SQLParamData**zurückgegebene Parameter.  
  
##### <a name="asynchronous-execution-for-connection-operations-polling-method"></a>Asynchrone Ausführung für Verbindungs Vorgänge (Abruf Methode)  
 Ein Treiber kann die asynchrone Unterstützung für verschiedene Verbindungs Vorgänge aktivieren.  
  
 Ab Windows 7 unterstützt ODBC die Abruf Methode (Weitere Informationen finden Sie unter [asynchrone Ausführung (Abruf Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md). Es ist nicht erforderlich, dass ein ODBC-Treiber der Version 3,8 asynchrone Vorgänge für Verbindungs Handles implementiert. Selbst wenn ein Treiber keine asynchronen Vorgänge für Verbindungs Handles implementiert, sollte der Treiber weiterhin den SQL_ASYNC_DBC_FUNCTIONS *InfoType* implementieren und **SQL_ASYNC_DBC_NOT_CAPABLE**zurückgeben.  
  
 Wenn asynchrone Verbindungs Vorgänge aktiviert sind, ist die laufende Zeit eines Verbindungs Vorgangs die Gesamtzeit aller wiederholten Aufrufe. Wenn der letzte wiederholte Aufruf erfolgt, nachdem die Gesamtzeit den vom SQL_ATTR_CONNECTION_TIMEOUT-Verbindungs Attribut festgelegten Wert überschritten hat und der Vorgang nicht abgeschlossen wurde, gibt der Treiber SQL_ERROR zurück und protokolliert einen Diagnosedaten Satz mit SQLSTATE HYT01 und der Meldung "das Verbindungs Timeout ist abgelaufen". Es gibt kein Timeout, wenn der Vorgang beendet wurde.  
  
##### <a name="sqlcancelhandle-function"></a>SQLCancelHandle-Funktion  
 ODBC 3,8 unterstützt die [sqlcancelhandle-Funktion](../../../odbc/reference/syntax/sqlcancelhandle-function.md), mit der sowohl Verbindungs-als auch Anweisungs Vorgänge abgebrochen werden. Ein Treiber, der **sqlcancelhandle** unterstützt, muss die Funktion exportieren. Ein Treiber sollte keine synchrone oder asynchrone Verbindungsfunktion abbrechen, die gerade ausgeführt wird, wenn die Anwendung **SQLCancel** oder **sqlcancelhandle** für ein Anweisungs Handle aufruft. Ebenso sollte ein Treiber keine synchrone oder asynchrone Anweisungs Funktion abbrechen, die gerade ausgeführt wird, wenn eine Anwendung **sqlcancelhandle** für das Verbindungs Handle aufruft. Außerdem sollte ein Treiber den Suchvorgang nicht abbrechen (**sqlbrowseconnetct** gibt SQL_NEED_DATA zurück), wenn die Anwendung **sqlcancelhandle** für das Verbindungs Handle aufruft. In diesen Fällen sollte ein Treiber HY010 "Function Sequence Error" zurückgeben.  
  
 Es ist nicht erforderlich, gleichzeitig sowohl **sqlcancelhandle** -als auch asynchronen-Verbindungs Vorgänge zu unterstützen. Ein Treiber kann asynchrone Verbindungs Vorgänge unterstützen, jedoch nicht **sqlcancelhandle**(oder umgekehrt).  
  
##### <a name="suspended-connections"></a>Angehaltene Verbindungen  
 Der Treiber-Manager für ODBC 3,8 kann eine Verbindung in den Zustand "angehalten" versetzen. Eine Anwendung ruft **SQLDisconnect** auf, um die der Verbindung zugeordneten Ressourcen freizugeben. In diesem Fall sollte ein Treiber versuchen, so viele Ressourcen wie möglich freizugeben, ohne den Status der Verbindung zu überprüfen. Weitere Informationen zum angehaltenen Status finden Sie unter [SQLEndTran Function](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
##### <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling  
 Mithilfe von ODBC in Windows 8 können Treiber das Verhalten des Verbindungspools anpassen. Weitere Informationen finden Sie unter [Treiber fähiges Verbindungs Pooling](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md).  
  
##### <a name="asynchronous-execution-notification-method"></a>Asynchrone Ausführung (Benachrichtigungsmethode)  
 ODBC 3,8 unterstützt die Benachrichtigungs Methode für asynchrone Vorgänge, die ab Windows 8 verfügbar sind. Weitere Informationen finden Sie unter [asynchrone Ausführung (Benachrichtigungs Methode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Von Microsoft bereitgestellte ODBC-Treiber](../../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)   
 [Neuerungen in ODBC 3.8](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
