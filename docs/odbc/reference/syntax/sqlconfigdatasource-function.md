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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ef74d98102c424a71ac1728d664fddbeac2296c
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53215599"
---
# <a name="sqlconfigdatasource-function"></a>SQLConfigDataSource-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **SQLConfigDataSource** hinzufügt, ändert oder löscht Sie Datenquellen.  
  
 Die Funktionalität von **SQLConfigDataSource** kann auch mit zugegriffen werden [ODBCCONF. EXE-Datei](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Argumente  
 *hwndParent*  
 [Eingabe] Handle des übergeordneten Fensters. Die Funktion wird keine Dialogfelder angezeigt, wenn das Handle null ist.  
  
 *Häufigsten*  
 [Eingabe] Typ der Anforderung. Die *häufigsten* Argument muss einen der folgenden Werte enthalten:  
  
 ODBC_ADD_DSN: Fügen Sie eine neue Datenquelle für den Benutzer hinzu.  
  
 ODBC_CONFIG_DSN: Konfigurieren (ändern) einer vorhandenen Datenquelle für den Benutzer.  
  
 ODBC_REMOVE_DSN: Entfernen Sie eine vorhandene Datenquelle für den Benutzer.  
  
 ODBC_ADD_SYS_DSN: Fügen Sie eine neue System-Datenquelle hinzu.  
  
 ODBC_CONFIG_SYS_DSN: Ändern einer vorhandenen System-Datenquelle.  
  
 MIT ODBC_REMOVE_SYS_DSN: Entfernen einer vorhandenen System-Datenquelle.  
  
 ODBC_REMOVE_DEFAULT_DSN: Entfernen Sie den Standardabschnitt Data Source-Spezifikation aus der Systeminformationen. (Es entfernt auch den Abschnitt "Default-Treiber-Spezifikation" aus dem Eintrag "Odbcinst.ini" in den Systeminformationen. Dies *häufigsten* führt die gleiche Funktion wie der veraltete **SQLRemoveDefaultDataSource** Funktion.) Wenn diese Option angegeben wird, alle anderen Parameter im Aufruf von **SQLConfigDataSource** sollte Null sein, wenn sie nicht NULL sind, werden diese ignoriert.  
  
 *lpszDriver*  
 [Eingabe] Treiberbeschreibung (normalerweise der Name des zugeordneten DBMS) für Benutzer anstelle des Namens des physischen Treiber angezeigt werden.  
  
 *lpszAttributes*  
 [Eingabe] Eine doppelt Null-terminierte Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Weitere Informationen finden Sie unter [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt. Wenn kein Eintrag in den Systeminformationen ist vorhanden, wenn diese Funktion aufgerufen wird, gibt die Funktion "false".  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLConfigDataSource** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster-handle|Die *HwndParent* Argument war ungültig oder NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *häufigsten* Argument war keiner der folgenden:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN MIT ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Name für Treiber oder das Konvertierungsprogramm|Die *LpszDriver* Argument war ungültig. Es konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültiges Schlüsselwort-Wert-Paaren|Die *LpszAttributes* Argument enthalten einen Syntaxfehler.|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* Fehler|Der Installer konnte nicht ausgeführt werden, den angeforderte Vorgang die *häufigsten* Argument. Der Aufruf von **ConfigDSN** ist fehlgeschlagen.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Die Treiber oder Translator-Setup-Bibliothek konnte nicht geladen werden.|Der Setup-Treiberbibliothek konnte nicht geladen werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLConfigDataSource** verwendet den Wert der *LpszDriver* , lesen den vollständigen Pfad der Setup-DLL für den Treiber aus den Systeminformationen. Es lädt die DLL und die Aufrufe **ConfigDSN** mit den gleichen Argumenten, die an sie übergeben wurden.  
  
 **SQLConfigDataSource** gibt FALSE zurück, wenn sie nicht gefunden oder das Setup-DLL zu laden oder wenn der Benutzer das Dialogfeld abbricht. Andernfalls wird den Status von Empfang **ConfigDSN**.  
  
 **SQLConfigDataSource** ordnet die System-DSN *häufigsten*s, um die Benutzer-DSN *häufigsten*s (ODBC_ADD_SYS_DSN zu ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN ODBC_CONFIG_DSN und ODBC_REMOVE_SYS_ DSN, ODBC_REMOVE_DSN). Benutzer und System-DSNs unterscheiden **SQLConfigDataSource** setzt das Installationsprogramm Konfigurationsmodus gemäß der folgenden Tabelle. Vor der Rückgabe, **SQLConfigDataSource** Konfigurationsmodus auf BOTHDSN zurückgesetzt. **ConfigDSN** (durch Treiber implementiert) sollten Aufrufen **SQLWriteDSNToIni** und **SQLWritePrivateProfileString** um einen System-DSN zu unterstützen. Weitere Informationen finden Sie unter [ConfigDSN-Funktion](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*Häufigsten*|Konfigurationsmodus|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|MIT ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (in der Setup-DLL)|  
|Name der Datenquelle entfernen aus der Systeminformationen|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Name der Datenquelle hinzufügen, um die Systeminformationen|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|
