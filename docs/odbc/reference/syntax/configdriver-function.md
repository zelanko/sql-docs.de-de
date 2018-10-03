---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d69db144a460bb2f662c8ba906bf0302cdf98388
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821658"
---
# <a name="configdriver-function"></a>ConfigDriver-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC 2.5  
  
 **Zusammenfassung**  
 **ConfigDriver** können Sie ein Setup-Programm installieren und deinstallieren Sie die Funktionen ohne das Programm aufrufen **ConfigDSN**. Diese Funktion führt treiberspezifische Funktionen, wie z. B. treiberspezifische Systeminformationen zu erstellen und DSN-Konvertierung auszuführen, während der Installation, sowie Informationen systemmodifizierungen bereinigen, während der Deinstallation. Diese Funktion wird durch den Setup-DLL für Treiber oder eine separate Setup-DLL verfügbar gemacht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
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
 [Eingabe] Handle des übergeordneten Fensters. Die Funktion wird keine Dialogfelder angezeigt, wenn das Handle null ist.  
  
 *Häufigsten*  
 [Eingabe] Typ der Anforderung. Die *häufigsten* Argument muss einen der folgenden Werte enthalten:  
  
 ODBC_INSTALL_DRIVER: Installieren Sie einen neuen Treiber.  
  
 ODBC_REMOVE_DRIVER: Entfernen eines Treibers.  
  
 Diese Option kann auch sein treiberspezifische, in diesem Fall die *häufigsten* Argument für die erste Option muss über ODBC_CONFIG_DRIVER_MAX + 1 starten. Die *häufigsten* Argument für eine zusätzliche Option muss auch aus einem Wert größer als ODBC_CONFIG_DRIVER_MAX + 1 beginnen.  
  
 *lpszDriver*  
 [Eingabe] Der Name des Treibers, der die Systeminformationen im Schlüssel "Odbcinst.ini" registriert.  
  
 *lpszArgs*  
 [Eingabe] Eine Null-terminierte Zeichenfolge, die mit Argumenten für eine treiberspezifische *häufigsten*.  
  
 *lpszMsg*  
 [Ausgabe] Eine mit Null endende Zeichenfolge, die eine Ausgabenachricht von der Setup-Treiber.  
  
 *cbMsgMax*  
 [Eingabe] Länge der *LpszMsg*.  
  
 *pcbMsgOut*  
 [Ausgabe] Gesamtzahl der Bytes, die für die Rückgabe in verfügbar *LpszMsg*.  
  
 Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbMsgMax*, der Ausgabenachricht im *LpszMsg* auf abgeschnitten *CbMsgMax* minus Null-Terminierung vorliegt Zeichen. Die *PcbMsgOut* Argument kann ein null-Zeiger sein.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigDriver** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert an den Installer Fehler Puffer gesendet wird, durch einen Aufruf von **SQLPostInstallerError** und erhalten Sie durch Aufrufen von **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster-handle|Die *HwndParent* Argument war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *häufigsten* Argument war keiner der folgenden:<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Der Treiber-spezifische Option war kleiner als oder gleich ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Name für Treiber oder das Konvertierungsprogramm|Die *LpszDriver* Argument war ungültig. Es konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* Fehler|Den angeforderte Vorgang konnte nicht ausgeführt werden die *häufigsten* Argument.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Oder Translator-treiberspezifischen Fehler|Ein Treiber-spezifische Fehler, für die kein definierten ODBC-Installer-Fehler vorliegt. Die *SzError* Argument in einem Aufruf der **SQLPostInstallerError** Funktion sollte die treiberspezifische Fehlermeldung enthalten.|  
  
## <a name="comments"></a>Kommentare  
  
### <a name="driver-specific-options"></a>Treiberspezifische Optionen  
 Eine Anwendung kann anfordern treiberspezifische Funktionen, die vom Treiber verfügbar gemacht, mit der *häufigsten* Argument. Die *häufigsten* für die erste Option ODBC_CONFIG_DRIVER_MAX plus 1, zusätzliche Optionen werden um 1, die von diesem Wert erhöht werden. Übergeben von Argumenten, die vom Treiber erforderlich sind, für diese Funktion in einer Null-terminierte Zeichenfolge bereitgestellt werden sollen die *LpszArgs* Argument. Treiber, die solche Funktionen bereitstellen, sollten eine Tabelle mit treiberspezifischen Optionen beibehalten. Die Optionen sollten in der Dokumentation zu Driver vollständig dokumentiert werden. Anwendungsentwickler, die treiberspezifische Optionen verwenden, sollten bedenken, dass dies die Anwendung zu weniger interoperable machen wird.  
  
### <a name="messages"></a>Meldungen  
 Eine Setuproutine Treiber kann eine Textnachricht zu einer Anwendung als eine Null-terminierte Zeichenfolge in die *LpszMsg* Puffer. Die Nachricht wird abgeschnitten und *CbMsgMax* minus der Null-Terminierungszeichen, durch die **ConfigDriver** ausgeführt werden, wenn es größer als oder gleich ist *CbMsgMax* Zeichen.
