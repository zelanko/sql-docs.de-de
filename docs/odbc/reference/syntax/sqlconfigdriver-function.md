---
title: Sqlconfigdriver-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDriver
helpviewer_keywords:
- SQLConfigDriver function [ODBC]
ms.assetid: 4f681961-ac9f-4d88-b065-5258ba112642
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e324b1f49bd6f8d0cad15ac2bcde73f558220330
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68121448"
---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,5  
  
 **Zusammenfassung**  
 **Sqlconfigdriver** lädt die entsprechende Treiber-Setup-DLL und ruft die **ConfigDriver** -Funktion auf.  
  
 Auf die Funktionalität von **sqlconfigdriver** kann auch mit [odbcconf zugegriffen werden. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLConfigDriver(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszArgs,  
     LPSTR    lpszMsg,  
     WORD     cbMsgMax,  
     WORD *   pcbMsgOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 Der Handle des übergeordneten Fensters. Die Funktion zeigt keine Dialogfelder an, wenn das Handle NULL ist.  
  
 *fRequest*  
 Der Der Typ der Anforderung. *fRequest* muss einen der folgenden Werte enthalten:  
  
 ODBC_CONFIG_DRIVER: ändert das Verbindungspooling-Timeout, das vom Treiber verwendet wird.  
  
 ODBC_INSTALL_DRIVER: Hiermit wird ein neuer Treiber installiert.  
  
 ODBC_REMOVE_DRIVER: entfernt einen vorhandenen Treiber.  
  
 Diese Option kann auch Treiber spezifisch sein. in diesem Fall muss die *häufigste* für die erste Option von ODBC_CONFIG_DRIVER_MAX + 1 beginnen. Die *fRequest* -Option für jede zusätzliche Option muss auch von einem Wert größer als ODBC_CONFIG_DRIVER_MAX + 1 beginnen.  
  
 *lpszDriver*  
 Der Der Name des Treibers, der in den Systeminformationen registriert ist.  
  
 *lpszargs*  
 Der Eine NULL-terminierte Zeichenfolge, die Argumente für eine Treiber spezifische *fRequest*enthält.  
  
 *lpszmsg*  
 Ausgeben Eine auf NULL endenden Zeichenfolge, die eine Ausgabe Meldung vom Treiber Setup enthält.  
  
 *cbmsgmax*  
 Der Länge von *lpszmsg.*  
  
 *pcbmsgout*  
 Ausgeben Die Gesamtanzahl der Bytes, die in " *lpszmsg*" zurückgegeben werden können. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbmsgmax*ist, wird die Ausgabe Nachricht in *lpszmsg* auf *cbmsgmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbmsgout* -Argument kann ein NULL-Zeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlconfigdriver** "false" zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Das *lpszmsg* -Argument war ungültig.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster handle.|Das *hwndParent* -Argument war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das *fRequest* -Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Das *fRequest* -Argument war eine Treiber spezifische Option, die kleiner oder gleich ODBC_CONFIG_DRIVER_MAX war.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpszDriver* -Argument war ungültig. Sie konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das *lpszargs* -Argument enthielt einen Syntax Fehler.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Vom Installationsprogramm konnte der vom *fRequest* -Argument angeforderte Vorgang nicht durchgeführt werden. Fehler beim **ConfigDriver** -Rückruf.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber-oder Konvertierungs-Setup Bibliothek konnte nicht geladen werden.|Die Treiber Setup Bibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlconfigdriver** ermöglicht es einer Anwendung, die **ConfigDriver** -Routine eines Treibers aufzurufen, ohne den Namen kennen zu müssen und die Treiber spezifische Setup-DLL zu laden. Diese Funktion wird von einem Setup Programm aufgerufen, nachdem die Treiber-Setup-DLL installiert wurde. Das aufrufende Programm sollte beachten, dass diese Funktion möglicherweise nicht für alle Treiber verfügbar ist. In einem solchen Fall sollte das aufrufenden Programm ohne Fehler fortgesetzt werden.  
  
## <a name="driver-specific-options"></a>Treiber spezifische Optionen  
 Eine Anwendung kann mit dem *fRequest* -Argument Treiber spezifische Funktionen anfordern, die vom Treiber verfügbar gemacht werden. Die *häufigste* für die erste Option ist ODBC_CONFIG_DRIVER_MAX + 1, und zusätzliche Optionen werden von diesem Wert um 1 erhöht. Alle Argumente, die für diese Funktion für den Treiber erforderlich sind, sollten in einer mit NULL endenden Zeichenfolge bereitgestellt werden, die im *lpszargs* -Argument übergeben wird. Treiber, die diese Funktionalität bereitstellen, sollten eine Tabelle mit treiberspezifischen Optionen verwalten. Die Optionen sollten vollständig in der Treiber Dokumentation dokumentiert werden. Anwendungs Schreiber, die Treiber spezifische Optionen verwenden, sollten sich bewusst sein, dass die Anwendung durch diese Verwendung weniger interoperabel wird.  
  
## <a name="setting-connection-pooling-timeout"></a>Timeout für Verbindungs Pooling wird festgelegt  
 Timeout Eigenschaften für Verbindungspooling können festgelegt werden, wenn Sie die Konfiguration des Treibers festlegen. **Sqlconfigdriver** wird mit einer *Häufigkeit* von ODBC_CONFIG_DRIVER und *lpszargs* aufgerufen, die auf **CPTimeout**festgelegt sind. **CPTimeout** bestimmt den Zeitraum, in dem eine Verbindung im Verbindungspool verbleiben kann, ohne verwendet zu werden. Wenn das Timeout abläuft, wird die Verbindung geschlossen und aus dem Pool entfernt. Der Standardwert für das Timeout beträgt 60 Sekunden.  
  
 Wenn **sqlconfigdriver** aufgerufen wird, wobei *fRequest* auf ODBC_INSTALL_DRIVER oder ODBC_REMOVE_DRIVER festgelegt ist, lädt der Treiber-Manager die entsprechende Treiber-Setup-DLL und ruft die **ConfigDriver** -Funktion auf. Wenn **sqlconfigdriver** mit dem ODBC_CONFIG_DRIVER am *häufigsten* aufgerufen wird, wird die gesamte Verarbeitung im ODBC-Installer ausgeführt, sodass die Treiber-Setup-DLL nicht geladen werden muss.  
  
## <a name="messages"></a>Meldungen  
 Eine Treiber-Setup Routine kann eine Textnachricht als auf NULL endende Zeichen folgen im *lpszmsg* -Puffer an eine Anwendung senden. Die Nachricht wird von der **ConfigDriver** -Funktion auf *cbmsgmax* abzüglich des NULL-Beendigungs Zeichens gekürzt, wenn Sie größer oder gleich *cbmsgmax* -Zeichen ist.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)(in der Setup-DLL)|  
|Entfernen der Standarddaten Quelle|[Sqlremovedefaultdatasource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|
