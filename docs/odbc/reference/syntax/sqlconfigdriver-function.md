---
title: SQLConfigDriver-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0da15cef06e5d8392408108ce88b53f7885eb65e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301245"
---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.5  
  
 **Zusammenfassung**  
 **SQLConfigDriver** lädt die entsprechende Treiber-Setup-DLL und ruft die **ConfigDriver-Funktion** auf.  
  
 Auf die Funktionalität von **SQLConfigDriver** kann auch mit [ODBCCONF zugegriffen werden. EXE](../../../odbc/odbcconf-exe.md).  
  
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
 [Eingabe] Übergeordnetes Fensterhandle. Die Funktion zeigt keine Dialogfelder an, wenn das Handle null ist.  
  
 *fRequest*  
 [Eingabe] Art der Anforderung. *fRequest* muss einen der folgenden Werte enthalten:  
  
 ODBC_CONFIG_DRIVER: Ändert das vom Treiber verwendete Zeittimeout für das Verbindungspooling.  
  
 ODBC_INSTALL_DRIVER: Installiert einen neuen Treiber.  
  
 ODBC_REMOVE_DRIVER: Entfernt einen vorhandenen Treiber.  
  
 Diese Option kann auch treiberspezifisch sein, in diesem Fall muss die *fRequest* für die erste Option von ODBC_CONFIG_DRIVER_MAX+1 beginnen. Die *fRequest* für eine zusätzliche Option muss auch von einem Wert größer als ODBC_CONFIG_DRIVER_MAX+1 beginnen.  
  
 *lpszDriver*  
 [Eingabe] Der Name des Treibers, der in den Systeminformationen registriert ist.  
  
 *lpszArgs*  
 [Eingabe] Eine null-terminierte Zeichenfolge, die Argumente für eine treiberspezifische *fRequest*enthält.  
  
 *lpszMsg*  
 [Ausgabe] Eine null-terminierte Zeichenfolge, die eine Ausgabenachricht vom Treibersetup enthält.  
  
 *cbMsgMax*  
 [Eingabe] Länge von *lpszMsg.*  
  
 *pcbMsgOut*  
 [Ausgabe] Gesamtanzahl der verfügbaren Bytes, die in *lpszMsg*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbMsgMax*ist, wird die Ausgabenachricht in *lpszMsg* auf *cbMsgMax* abzüglich des Null-Beendigungszeichens abgeschnitten. Das *Argument pcbMsgOut* kann ein Nullzeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLConfigDriver** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge|Das Argument *lpszMsg* war ungültig.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fensterhandle|Das *Argument hwndParent* war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das *fRequest-Argument* war nicht eines der folgenden:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Das *fRequest-Argument* war eine treiberspezifische Option, die kleiner oder gleich ODBC_CONFIG_DRIVER_MAX war.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das *Argument lpszDriver* war ungültig. Sie konnte in der Registrierung nicht gefunden werden.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das Argument *lpszArgs* enthielt einen Syntaxfehler.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Das Installationsprogramm konnte den vom *fRequest-Argument* angeforderten Vorgang nicht ausführen. Der Aufruf von **ConfigDriver** ist fehlgeschlagen.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber- oder Übersetzereinrichtungsbibliothek konnte nicht geladen werden.|Die Treibereinrichtungsbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLConfigDriver** ermöglicht es einer Anwendung, die **ConfigDriver-Routine** eines Treibers aufzurufen, ohne den Namen kennen und die treiberspezifische Setup-DLL laden zu müssen. Ein Setupprogramm ruft diese Funktion auf, nachdem die Treiber-Setup-DLL installiert wurde. Das aufrufende Programm sollte sich bewusst sein, dass diese Funktion möglicherweise nicht für alle Treiber verfügbar ist. In einem solchen Fall sollte das aufrufende Programm fehlerfrei fortgesetzt werden.  
  
## <a name="driver-specific-options"></a>Treiberspezifische Optionen  
 Eine Anwendung kann treiberspezifische Features anfordern, die vom Treiber mithilfe des *fRequest-Arguments* verfügbar gemacht werden. Die *fRequest* für die erste Option wird ODBC_CONFIG_DRIVER_MAX+1 sein, und zusätzliche Optionen werden um 1 von diesem Wert erhöht. Alle Argumente, die vom Treiber für diese Funktion benötigt werden, sollten in einer null-terminierten Zeichenfolge bereitgestellt werden, die im *Argument lpszArgs* übergeben wird. Treiber, die eine solche Funktionalität bereitstellen, sollten eine Tabelle mit treiberspezifischen Optionen verwalten. Die Optionen sollten vollständig in der Treiberdokumentation dokumentiert werden. Anwendungsautoren, die treiberspezifische Optionen verwenden, sollten sich bewusst sein, dass diese Verwendung die Anwendung weniger interoperabel macht.  
  
## <a name="setting-connection-pooling-timeout"></a>Festlegen des Verbindungspoolingtimeouts  
 Verbindungspooltimeouteigenschaften können festgelegt werden, wenn Sie die Konfiguration des Treibers festlegen. **SQLConfigDriver** wird aufgerufen, wobei eine *fRequest* von ODBC_CONFIG_DRIVER und *lpszArgs* auf **CPTimeout**festgelegt ist. **CPTimeout** bestimmt den Zeitraum, in dem eine Verbindung im Verbindungspool verbleiben kann, ohne verwendet zu werden. Wenn das Timeout abläuft, wird die Verbindung geschlossen und aus dem Pool entfernt. Das Standardtimeout beträgt 60 Sekunden.  
  
 Wenn **SQLConfigDriver** aufgerufen wird, wenn *fRequest* auf ODBC_INSTALL_DRIVER oder ODBC_REMOVE_DRIVER eingestellt ist, lädt der Treiber-Manager die entsprechende Treiber-Setup-DLL und ruft die **ConfigDriver-Funktion** auf. Wenn **SQLConfigDriver** mit einer *fRequest* von ODBC_CONFIG_DRIVER aufgerufen wird, wird die gesamte Verarbeitung im ODBC-Installationsprogramm ausgeführt, sodass die Treiber-Setup-DLL nicht geladen werden muss.  
  
## <a name="messages"></a>Meldungen  
 Eine Treibereinrichtungsroutine kann eine Textnachricht als null-terminierte Zeichenfolgen im *lpszMsg-Puffer* an eine Anwendung senden. Die Nachricht wird von der **ConfigDriver-Funktion** auf *cbMsgMax* abzüglich des Null-Beendigungszeichens abgeschnitten, wenn sie größer oder gleich *cbMsgMax-Zeichen* ist.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen eines Treibers|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)(in der Setup-DLL)|  
|Entfernen der Standarddatenquelle|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|
