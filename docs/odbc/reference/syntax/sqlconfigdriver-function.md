---
title: SQLConfigDriver-Funktion | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 20316f2a7932768951633ae24e1b1e180c1dfb49
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537576"
---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.5  
  
 **Zusammenfassung**  
 **SQLConfigDriver** lädt die Setup-DLL für geeigneter Treiber und ruft die **ConfigDriver** Funktion.  
  
 Die Funktionalität von **SQLConfigDriver** kann auch mit zugegriffen werden [ODBCCONF. EXE-Datei](../../../odbc/odbcconf-exe.md).  
  
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
 [Eingabe] Handle des übergeordneten Fensters. Die Funktion wird keine Dialogfelder angezeigt, wenn das Handle null ist.  
  
 *fRequest*  
 [Eingabe] Typ der Anforderung. *Häufigsten* muss einen der folgenden Werte enthalten:  
  
 ODBC_CONFIG_DRIVER: Ändert das Verbindungs-pooling Timeout, die vom Treiber verwendet.  
  
 ODBC_INSTALL_DRIVER: Installiert einen neuen Treiber.  
  
 ODBC_REMOVE_DRIVER: Entfernt einen vorhandenen Treiber.  
  
 Diese Option kann auch sein treiberspezifische, in diesem Fall die *häufigsten* für die erste Option von ODBC_CONFIG_DRIVER_MAX + 1 starten muss. Die *häufigsten* für eine zusätzliche Option auch über einen Wert größer als ODBC_CONFIG_DRIVER_MAX + 1 starten muss.  
  
 *lpszDriver*  
 [Eingabe] Der Name des Treibers, der in den Systeminformationen registriert.  
  
 *lpszArgs*  
 [Eingabe] Eine auf Null endende Zeichenfolge, die Argumente für eine treiberspezifische enthält *häufigsten*.  
  
 *lpszMsg*  
 [Ausgabe] Ein Null-terminierte Zeichenfolge, die eine Ausgabenachricht von der Setup-Treiber enthält.  
  
 *cbMsgMax*  
 [Eingabe] Länge der *LpszMsg.*  
  
 *pcbMsgOut*  
 [Ausgabe] Gesamtzahl der Bytes, die für die Rückgabe in verfügbar *LpszMsg*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbMsgMax*, der Ausgabenachricht im *LpszMsg* auf abgeschnitten *CbMsgMax* minus Null-Terminierung vorliegt Zeichen. Die *PcbMsgOut* Argument kann ein null-Zeiger sein.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLConfigDriver** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Die *LpszMsg* Argument war ungültig.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster-handle|Die *HwndParent* Argument war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *häufigsten* Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Die *häufigsten* Argument wurde eine treiberspezifische-Option, die kleiner oder gleich ODBC_CONFIG_DRIVER_MAX wurde.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Name für Treiber oder das Konvertierungsprogramm|Die *LpszDriver* Argument war ungültig. Es konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültiges Schlüsselwort-Wert-Paaren|Die *LpszArgs* Argument enthalten einen Syntaxfehler.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* Fehler|Der Installer konnte nicht ausgeführt werden, den angeforderte Vorgang die *häufigsten* Argument. Der Aufruf von **ConfigDriver** ist fehlgeschlagen.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber oder Translator-Setup-Bibliothek konnte nicht geladen werden.|Der Setup-Treiberbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLConfigDriver** ermöglicht es einer Anwendung zum Aufrufen des Treibers **ConfigDriver** ohne den Namen kennen, und laden das Setup-DLL für Treiber-spezifische Routine. Ein Setup-Programm ruft diese Funktion nach dem Setup-Treiber, die DLL installiert wurde. Das aufrufende Programm sollten bedenken, dass diese Funktion möglicherweise nicht für alle Treiber verfügbar. In diesem Fall muss das aufrufende Programm ohne Fehler fortgesetzt werden.  
  
## <a name="driver-specific-options"></a>Treiberspezifische Optionen  
 Eine Anwendung kann anfordern treiberspezifische Funktionen, die vom Treiber verfügbar gemacht, mit der *häufigsten* Argument. Die *häufigsten* für die erste Option ODBC_CONFIG_DRIVER_MAX + 1, zusätzliche Optionen werden um 1, die von diesem Wert erhöht werden. Übergeben von Argumenten, die vom Treiber erforderlich sind, für diese Funktion in einer Null-terminierte Zeichenfolge bereitgestellt werden sollen die *LpszArgs* Argument. Treiber, die solche Funktionen bereitstellen, sollten eine Tabelle mit treiberspezifischen Optionen beibehalten. Die Optionen sollten in der Dokumentation zu Driver vollständig dokumentiert werden. Anwendungsentwickler, die treiberspezifische Optionen verwenden, sollten bedenken, dass es sich bei dieser Verwendung die Anwendung weniger interoperable machen werden.  
  
## <a name="setting-connection-pooling-timeout"></a>Festlegen der Timeout-Verbindungspooling  
 Verbindungs-pooling Timeouteigenschaften kann festgelegt werden, wenn Sie festlegen, dass die Konfiguration des Treibers. **SQLConfigDriver** aufgerufen wird und ein *häufigsten* von ODBC_CONFIG_DRIVER und *LpszArgs* festgelegt **CPTimeout**. **CPTimeout** bestimmt den Zeitraum, der eine Verbindung im Verbindungspool verbleiben kann, verwendet wird. Wenn das Timeout abläuft, wird die Verbindung geschlossen und aus dem Pool entfernt. Das Standardzeitlimit beträgt 60 Sekunden.  
  
 Wenn **SQLConfigDriver** aufgerufen wird und *häufigsten* ODBC_INSTALL_DRIVER oder ODBC_REMOVE_DRIVER festgelegt, der Treiber-Manager lädt, die Setup-DLL für geeigneter Treiber und ruft die  **ConfigDriver** Funktion. Wenn **SQLConfigDriver** aufgerufen wird und ein *häufigsten* von ODBC_CONFIG_DRIVER, die gesamte Verarbeitung erfolgt in des ODBC-Installationsprogramms, damit der Setup-DLL für Treiber nicht geladen werden.  
  
## <a name="messages"></a>Meldungen  
 Eine Setuproutine Treiber kann eine Textnachricht zu einer Anwendung als Null-terminierte Zeichenfolgen in die *LpszMsg* Puffer. Die Nachricht wird abgeschnitten und *CbMsgMax* minus der Null-Terminierungszeichen, durch die **ConfigDriver** ausgeführt werden, wenn es größer als oder gleich ist *CbMsgMax* Zeichen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)(in der Setup-DLL)|  
|Entfernen die Standarddatenquelle|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|
