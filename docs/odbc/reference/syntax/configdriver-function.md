---
title: ConfigDriver-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDriver
helpviewer_keywords:
- ConfigDriver [ODBC]
ms.assetid: 9473f48f-bcae-4784-89c1-7839bad4ed13
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a2da5fd5ce01bd97f13d7c8d805c615c1ac436a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303961"
---
# <a name="configdriver-function"></a>ConfigDriver-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.5  
  
 **Zusammenfassung**  
 **ConfigDriver** ermöglicht es einem Setup-Programm, Installations- und Deinstallationsfunktionen auszuführen, ohne dass das Programm **ConfigDSN**aufrufen muss. Diese Funktion führt treiberspezifische Funktionen aus, z. B. das Erstellen treiberspezifischer Systeminformationen und das Durchführen von DSN-Konvertierungen während der Installation sowie das Bereinigen von Systeminformationen während der Deinstallation. Diese Funktion wird durch die Treibereinrichtungs-DLL oder eine separate Setup-DLL verfügbar gemacht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL ConfigDriver(  
      HWND    hwndParent,  
      WORD    fRequest,  
      LPCSTR  lpszDriver,  
      LPCSTR  lpszArgs,  
      LPSTR   lpszMsg,  
      WORD    cbMsgMax,  
      WORD *  pcbMsgOut);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 [Eingabe] Übergeordnetes Fensterhandle. Die Funktion zeigt keine Dialogfelder an, wenn das Handle null ist.  
  
 *fRequest*  
 [Eingabe] Art der Anforderung. Das *fRequest-Argument* muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_DRIVER: Installieren Sie einen neuen Treiber.  
  
 ODBC_REMOVE_DRIVER: Entfernen Sie einen Treiber.  
  
 Diese Option kann auch treiberspezifisch sein, in diesem Fall muss das *fRequest-Argument* für die erste Option von ODBC_CONFIG_DRIVER_MAX+1 beginnen. Das *fRequest-Argument* für eine zusätzliche Option muss ebenfalls von einem Wert beginnen, der größer als ODBC_CONFIG_DRIVER_MAX+1 ist.  
  
 *lpszDriver*  
 [Eingabe] Der Name des Treibers, der im Schlüssel Odbcinst.ini der Systeminformationen registriert ist.  
  
 *lpszArgs*  
 [Eingabe] Eine null-terminierte Zeichenfolge, die Argumente für eine treiberspezifische *fRequest*enthält.  
  
 *lpszMsg*  
 [Ausgabe] Eine null-terminierte Zeichenfolge, die eine Ausgabenachricht aus dem Treiber-Setup enthält.  
  
 *cbMsgMax*  
 [Eingabe] Länge von *lpszMsg*.  
  
 *pcbMsgOut*  
 [Ausgabe] Gesamtanzahl der verfügbaren Bytes, die in *lpszMsg*zurückgegeben werden können.  
  
 Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbMsgMax*ist, wird die Ausgabenachricht in *lpszMsg* auf *cbMsgMax* abzüglich des Null-Beendigungszeichens abgeschnitten. Das *Argument pcbMsgOut* kann ein Nullzeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigDriver** FALSE zurückgibt, wird ein zugeordneter * \*pfErrorCode-Wert* durch einen Aufruf von **SQLPostInstallerError** an den Installer-Fehlerpuffer gesendet und kann durch Aufrufen von **SQLInstallerError**abgerufen werden. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fensterhandle|Das *Argument hwndParent* war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das *fRequest-Argument* war nicht eines der folgenden:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Die treiberspezifische Option war kleiner oder gleich ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das *Argument lpszDriver* war ungültig. Sie konnte in der Registrierung nicht gefunden werden.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Der vom *fRequest-Argument* angeforderte Vorgang konnte nicht ausgeführt werden.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Treiber- oder Übersetzerspezifischer Fehler|Ein treiberspezifischer Fehler, für den kein definierter ODBC-Installationsfehler vorliegt. Das *SzError-Argument* in einem Aufruf der **SQLPostInstallerError-Funktion** sollte die treiberspezifische Fehlermeldung enthalten.|  
  
## <a name="comments"></a>Kommentare  
  
### <a name="driver-specific-options"></a>Treiberspezifische Optionen  
 Eine Anwendung kann treiberspezifische Features anfordern, die vom Treiber mithilfe des *fRequest-Arguments* verfügbar gemacht werden. Die *fRequest* für die erste Option wird ODBC_CONFIG_DRIVER_MAX plus 1, und zusätzliche Optionen werden um 1 von diesem Wert erhöht. Alle Argumente, die vom Treiber für diese Funktion benötigt werden, sollten in einer null-terminierten Zeichenfolge bereitgestellt werden, die im *Argument lpszArgs* übergeben wird. Treiber, die eine solche Funktionalität bereitstellen, sollten eine Tabelle mit treiberspezifischen Optionen verwalten. Die Optionen sollten vollständig in der Treiberdokumentation dokumentiert werden. Anwendungsautoren, die treiberspezifische Optionen verwenden, sollten sich bewusst sein, dass die Anwendung dadurch weniger interoperabel wird.  
  
### <a name="messages"></a>Meldungen  
 Eine Treibereinrichtungsroutine kann eine Textnachricht als null-terminierte Zeichenfolge im *lpszMsg-Puffer* an eine Anwendung senden. Die Nachricht wird von der **ConfigDriver-Funktion** auf *cbMsgMax* abzüglich des Null-Beendigungszeichens abgeschnitten, wenn sie größer oder gleich *cbMsgMax-Zeichen* ist.
