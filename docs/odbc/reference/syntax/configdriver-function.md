---
description: ConfigDriver-Funktion
title: ConfigDriver-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: 3d59765d1b6a6a662c02b459e07bac10895838a2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428952"
---
# <a name="configdriver-function"></a>ConfigDriver-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,5  
  
 **Zusammenfassung**  
 **ConfigDriver** ermöglicht einem Setup Programm das Ausführen von Installations-und Deinstallations Funktionen, ohne dass das Programm **ConfigDSN**aufruft. Diese Funktion führt Treiber spezifische Funktionen aus, z. b. das Erstellen von treiberspezifischen Systeminformationen und das Ausführen von DSN-Konvertierungen während der Installation sowie das Bereinigen von System Informations Änderungen während der Deinstallation. Diese Funktion wird durch die Treiber-Setup-DLL oder eine separate Setup-DLL verfügbar gemacht.  
  
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
 Der Handle des übergeordneten Fensters. Die Funktion zeigt keine Dialogfelder an, wenn das Handle NULL ist.  
  
 *fRequest*  
 Der Der Typ der Anforderung. Das *fRequest* -Argument muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_DRIVER: Installieren Sie einen neuen Treiber.  
  
 ODBC_REMOVE_DRIVER: Entfernen eines Treibers.  
  
 Diese Option kann auch Treiber spezifisch sein. in diesem Fall muss das *fRequest* -Argument für die erste Option von ODBC_CONFIG_DRIVER_MAX + 1 beginnen. Das *fRequest* -Argument für eine beliebige zusätzliche Option muss auch mit einem Wert beginnen, der größer als ODBC_CONFIG_DRIVER_MAX + 1 ist.  
  
 *lpszDriver*  
 Der Der Name des Treibers, der im Odbcinst.ini Schlüssel der Systeminformationen registriert ist.  
  
 *lpszargs*  
 Der Eine NULL-terminierte Zeichenfolge, die Argumente für eine Treiber spezifische *fRequest*enthält.  
  
 *lpszmsg*  
 Ausgeben Eine auf NULL endenden Zeichenfolge, die eine Ausgabe Meldung vom Treiber Setup enthält.  
  
 *cbmsgmax*  
 Der Länge von *lpszmsg*.  
  
 *pcbmsgout*  
 Ausgeben Die Gesamtanzahl der Bytes, die in " *lpszmsg*" zurückgegeben werden können.  
  
 Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbmsgmax*ist, wird die Ausgabe Nachricht in *lpszmsg* auf *cbmsgmax* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbmsgout* -Argument kann ein NULL-Zeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigDriver** false zurückgibt, wird ein zugeordneter Wert von " * \* Pferd rorcode* " durch einen Aufruf von " **sqlpostinstallererror** " an den Installer-Fehler Puffer gesendet und kann durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster handle.|Das *hwndParent* -Argument war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das *fRequest* -Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Die Treiber spezifische Option war kleiner als oder gleich ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpszDriver* -Argument war ungültig. Sie konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Der vom *fRequest* -Argument angeforderte Vorgang konnte nicht durchgeführt werden.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Treiber-oder Konvertierungs spezifischer Fehler|Ein Treiber spezifischer Fehler, für den kein ODBC-Installationsprogramm Fehler definiert wurde. Das *szerror* -Argument in einem aufzurufenden Befehl der **sqlpostinstallererror** -Funktion sollte die Treiber spezifische Fehlermeldung enthalten.|  
  
## <a name="comments"></a>Kommentare  
  
### <a name="driver-specific-options"></a>Treiber spezifische Optionen  
 Eine Anwendung kann mit dem *fRequest* -Argument Treiber spezifische Funktionen anfordern, die vom Treiber verfügbar gemacht werden. Die *häufigste* für die erste Option ist ODBC_CONFIG_DRIVER_MAX Plus 1, und zusätzliche Optionen werden von diesem Wert um 1 erhöht. Alle Argumente, die für diese Funktion für den Treiber erforderlich sind, sollten in einer mit NULL endenden Zeichenfolge bereitgestellt werden, die im *lpszargs* -Argument übergeben wird. Treiber, die diese Funktionalität bereitstellen, sollten eine Tabelle mit treiberspezifischen Optionen verwalten. Die Optionen sollten vollständig in der Treiber Dokumentation dokumentiert werden. Anwendungs Schreiber, die Treiber spezifische Optionen verwenden, sollten sich bewusst sein, dass dadurch die Anwendung weniger interoperabel wird.  
  
### <a name="messages"></a>Meldungen  
 Eine Treiber-Setup Routine kann eine Textnachricht an eine Anwendung als eine mit NULL endende Zeichenfolge im *lpszmsg* -Puffer senden. Die Nachricht wird von der **ConfigDriver** -Funktion auf *cbmsgmax* abzüglich des NULL-Beendigungs Zeichens gekürzt, wenn Sie größer oder gleich *cbmsgmax* -Zeichen ist.
