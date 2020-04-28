---
title: SQLConfigDataSource-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90a51193a8f4edbb013527c4dde0625b75131583
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299630"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0  
  
 **Zusammenfassung**  
 **SQLConfigDataSource** fügt Datenquellen hinzu, ändert Sie oder löscht sie.  
  
 Auf die Funktionalität von **SQLConfigDataSource** kann auch mit [odbcconf zugegriffen werden. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 Der Handle des übergeordneten Fensters. Die Funktion zeigt keine Dialogfelder an, wenn das Handle NULL ist.  
  
 *fRequest*  
 Der Der Typ der Anforderung. Das *fRequest* -Argument muss einen der folgenden Werte enthalten:  
  
 ODBC_ADD_DSN: Fügen Sie eine neue Benutzerdaten Quelle hinzu.  
  
 ODBC_CONFIG_DSN: Hiermit wird eine vorhandene Benutzerdaten Quelle konfiguriert (geändert).  
  
 ODBC_REMOVE_DSN: eine vorhandene Benutzerdaten Quelle entfernen.  
  
 ODBC_ADD_SYS_DSN: Fügen Sie eine neue Systemdaten Quelle hinzu.  
  
 ODBC_CONFIG_SYS_DSN: eine vorhandene Systemdaten Quelle ändern.  
  
 ODBC_REMOVE_SYS_DSN: Entfernen Sie eine vorhandene Systemdaten Quelle.  
  
 ODBC_REMOVE_DEFAULT_DSN: Entfernen Sie den Abschnitt "Standarddaten Quellen Spezifikation" aus den Systeminformationen. (Außerdem wird der Abschnitt "Standardtreiber Spezifikation" aus dem Eintrag "Odbcinst. ini" in den Systeminformationen entfernt. Dieses *fRequest* führt dieselbe Funktion aus wie die veraltete **sqlremovedefaultdatasource** -Funktion.) Wenn diese Option angegeben ist, sollten alle anderen Parameter im-Befehl von **SQLConfigDataSource** NULL sein. Wenn Sie nicht NULL sind, werden Sie ignoriert.  
  
 *lpszDriver*  
 Der Treiber Beschreibung (in der Regel der Name des zugeordneten DBMS), der Benutzern anstelle des Namens des physischen Treibers angezeigt wird.  
  
 *lpszattribute*  
 Der Eine doppelt auf NULL endend beendete Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Weitere Informationen finden Sie unter [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false. Wenn in den Systeminformationen kein Eintrag vorhanden ist, wenn diese Funktion aufgerufen wird, gibt die Funktion false zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLConfigDataSource** "false" zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von **sqlinstallererror**abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster handle.|Das *hwndParent* -Argument war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das *fRequest* -Argument war keiner der folgenden:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpszDriver* -Argument war ungültig. Sie konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das *lpszattribute* -Argument enthielt einen Syntax Fehler.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Vom Installationsprogramm konnte der vom *fRequest* -Argument angeforderte Vorgang nicht durchgeführt werden. Fehler beim **ConfigDSN** -Rückruf.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber-oder Konvertierungs-Setup Bibliothek konnte nicht geladen werden.|Die Treiber Setup Bibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLConfigDataSource** verwendet den Wert von *lpszDriver* , um den vollständigen Pfad der Setup-DLL für den Treiber aus den Systeminformationen zu lesen. Die dll wird geladen, und **ConfigDSN** wird mit denselben Argumenten aufgerufen, die an Sie übermittelt wurden.  
  
 **SQLConfigDataSource** gibt false zurück, wenn die Setup-DLL nicht gefunden oder geladen werden kann oder wenn der Benutzer das Dialogfeld abbricht. Andernfalls wird der von **ConfigDSN**empfangene Status zurückgegeben.  
  
 **SQLConfigDataSource** ordnet die am häufigsten verwendeten *DSN-* Daten der Benutzer an, die am *häufigsten*angezeigt werden (ODBC_ADD_SYS_DSN ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN ODBC_CONFIG_DSN, und ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DSN). Um Benutzer-und System-DSNs zu unterscheiden, legt **SQLConfigDataSource** den installerkonfigurationsmodus gemäß der folgenden Tabelle fest. Vor der Rückgabe setzt **SQLConfigDataSource** den Konfigurations Modus auf bothdsn zurück. **ConfigDSN** (implementiert von Treibern) sollte **sqlschreitedsndeini** und **sqlschreiteprivateprofilestring** aufrufen, um einen System-DSN zu unterstützen. Weitere Informationen finden Sie unter [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*fRequest*|Konfigurations Modus|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in der Setup-DLL)|  
|Entfernen eines Datenquellen namens aus den Systeminformationen|[Sqlremovedsnfromini](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Hinzufügen eines Datenquellen namens zu den Systeminformationen|[Sqlschreitedsnder ini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
