---
title: SQLConfigDataSource-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299630"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **SQLConfigDataSource** fügt Datenquellen hinzu, ändert oder löscht sie.  
  
 Auf die Funktionalität von **SQLConfigDataSource** kann auch mit [ODBCCONF zugegriffen werden. EXE](../../../odbc/odbcconf-exe.md).  
  
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
 [Eingabe] Übergeordnetes Fensterhandle. Die Funktion zeigt keine Dialogfelder an, wenn das Handle null ist.  
  
 *fRequest*  
 [Eingabe] Art der Anforderung. Das *fRequest-Argument* muss einen der folgenden Werte enthalten:  
  
 ODBC_ADD_DSN: Fügen Sie eine neue Benutzerdatenquelle hinzu.  
  
 ODBC_CONFIG_DSN: Konfigurieren (ändern) einer vorhandenen Benutzerdatenquelle.  
  
 ODBC_REMOVE_DSN: Entfernen Sie eine vorhandene Benutzerdatenquelle.  
  
 ODBC_ADD_SYS_DSN: Fügen Sie eine neue Systemdatenquelle hinzu.  
  
 ODBC_CONFIG_SYS_DSN: Ändern sie eine vorhandene Systemdatenquelle.  
  
 ODBC_REMOVE_SYS_DSN: Entfernen Sie eine vorhandene Systemdatenquelle.  
  
 ODBC_REMOVE_DEFAULT_DSN: Entfernen Sie den Standardmäßigen Datenquellenspezifikationsabschnitt aus den Systeminformationen. (Außerdem wird der Standardmäßige Treiberspezifikationsabschnitt aus dem Eintrag Odbcinst.ini in den Systeminformationen entfernt. Diese *fRequest* führt dieselbe Funktion wie die veraltete **SQLRemoveDefaultDataSource-Funktion** aus.) Wenn diese Option angegeben ist, sollten alle anderen Parameter im Aufruf von **SQLConfigDataSource** NULLs sein. Wenn sie nicht NULL sind, werden sie ignoriert.  
  
 *lpszDriver*  
 [Eingabe] Treiberbeschreibung (in der Regel der Name des zugehörigen DBMS), die den Benutzern anstelle des physischen Treibernamens angezeigt wird.  
  
 *lpszAttributes*  
 [Eingabe] Eine doppelt null-terminierte Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Weitere Informationen finden Sie unter [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt. Wenn beim Aufruf dieser Funktion kein Eintrag in den Systeminformationen vorhanden ist, gibt die Funktion FALSE zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLConfigDataSource** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallerError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fensterhandle|Das *Argument hwndParent* war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das *fRequest-Argument* war nicht eines der folgenden:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das *Argument lpszDriver* war ungültig. Sie konnte in der Registrierung nicht gefunden werden.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das Argument *lpszAttributes* enthielt einen Syntaxfehler.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Das Installationsprogramm konnte den vom *fRequest-Argument* angeforderten Vorgang nicht ausführen. Der Aufruf von **ConfigDSN** ist fehlgeschlagen.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber- oder Übersetzereinrichtungsbibliothek konnte nicht geladen werden.|Die Treibereinrichtungsbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLConfigDataSource** verwendet den Wert *von lpszDriver,* um den vollständigen Pfad der Setup-DLL für den Treiber aus den Systeminformationen zu lesen. Es lädt die DLL und ruft **ConfigDSN** mit den gleichen Argumenten auf, die an sie übergeben wurden.  
  
 **SQLConfigDataSource** gibt FALSE zurück, wenn die Setup-DLL nicht gefunden oder geladen werden kann oder wenn der Benutzer das Dialogfeld abbricht. Andernfalls wird der Status zurückgegeben, den sie von **ConfigDSN**erhalten hat.  
  
 **SQLConfigDataSource** ordnet die System-DSN-fRequest s dem Benutzer DSN *fRequest*s (ODBC_ADD_SYS_DSN ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN zu ODBC_CONFIG_DSN und ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DSN) zu. *fRequest* Um Benutzer- und System-DSNs zu unterscheiden, legt **SQLConfigDataSource** den Installationskonfigurationsmodus gemäß der folgenden Tabelle fest. Vor der Rückgabe setzt **SQLConfigDataSource** den Konfigurationsmodus auf BOTHDSN zurück. **ConfigDSN** (implementiert von Treibern) sollte **SQLWriteDSNToIni** und **SQLWritePrivateProfileString** aufrufen, um ein System-DSN zu unterstützen. Weitere Informationen finden Sie unter [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*fRequest*|Konfigurationsmodus|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in der Setup-DLL)|  
|Entfernen eines Datenquellennamens aus den Systeminformationen|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Hinzufügen eines Datenquellennamens zu den Systeminformationen|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
