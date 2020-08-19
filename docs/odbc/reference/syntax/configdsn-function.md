---
description: ConfigDSN-Funktion
title: ConfigDSN-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDSN
helpviewer_keywords:
- ConfigDSN [ODBC]
ms.assetid: 01ced74e-c575-4a25-83f5-bd7d918123f8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e4ea667678fcbd0905ee3587f94554eb6e39b03
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421304"
---
# <a name="configdsn-function"></a>ConfigDSN-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0  
  
 **Zusammenfassung**  
 **ConfigDSN** fügt Datenquellen in den Systeminformationen hinzu, ändert oder löscht sie. Möglicherweise wird der Benutzer zur Eingabe von Verbindungsinformationen aufgefordert. Sie kann sich in der Treiber-DLL oder einer separaten Setup-DLL befinden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL ConfigDSN(  
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
  
 ODBC_ADD_DSN: Fügen Sie eine neue Datenquelle hinzu.  
  
 ODBC_CONFIG_DSN: eine vorhandene Datenquelle konfigurieren (ändern).  
  
 ODBC_REMOVE_DSN: Entfernen Sie eine vorhandene Datenquelle.  
  
 *lpszDriver*  
 Der Treiber Beschreibung (in der Regel der Name des zugeordneten DBMS), der Benutzern anstelle des Namens des physischen Treibers angezeigt wird.  
  
 *lpszattribute*  
 Der Eine doppelt auf NULL endend beendete Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Weitere Informationen finden Sie unter "comments".  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigDSN** false zurückgibt, wird ein zugeordneter Wert von " * \* Pferd rorcode* " durch einen Aufruf von " **sqlpostinstallererror** " an den Installer-Fehler Puffer gesendet und kann durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster handle.|Das *hwndParent* -Argument war ungültig.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das *lpszattribute* -Argument enthielt einen Syntax Fehler.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber-oder Konvertierungs Name|Das *lpszDriver* -Argument war ungültig. Sie konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das *fRequest* -Argument war keiner der folgenden:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Der vom *fRequest* -Argument angeforderte Vorgang konnte nicht durchgeführt werden.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Treiber-oder Konvertierungs spezifischer Fehler|Ein Treiber spezifischer Fehler, für den kein ODBC-Installationsprogramm Fehler definiert wurde. Das *szerror* -Argument in einem aufzurufenden Befehl der **sqlpostinstallererror** -Funktion sollte die Treiber spezifische Fehlermeldung enthalten.|  
  
## <a name="comments"></a>Kommentare  
 **ConfigDSN** empfängt Verbindungsinformationen von der Installer-dll als Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Jedes Paar wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei NULL-Bytes markieren das Ende der Liste.) Leerzeichen sind um das Gleichheitszeichen im Schlüsselwort-Wert-Paar nicht zulässig. **ConfigDSN** kann Schlüsselwörter akzeptieren, bei denen es sich nicht um gültige Schlüsselwörter für **sqlbrowseconnetct** und **SQLDriverConnect**handelt. **ConfigDSN** unterstützt nicht notwendigerweise alle Schlüsselwörter, die gültige Schlüsselwörter für **sqlbrowseconnetct** und **SQLDriverConnect**sind. (**ConfigDSN** akzeptiert das **Driver** -Schlüsselwort nicht.) Die von der **ConfigDSN** -Funktion verwendeten Schlüsselwörter müssen alle Optionen unterstützen, die zum Neuerstellen der Datenquelle mithilfe der automatischen Setup Funktion des Installers erforderlich sind. Wenn die Verwendungen der **ConfigDSN** -Werte und der Verbindungs Zeichenfolgen-Werte identisch sind, sollten dieselben Schlüsselwörter verwendet werden.  
  
 Wie in **sqlbrowseconnetct** und **SQLDriverConnect**dürfen die Schlüsselwörter und ihre Werte nicht das **[] {} (),;? \* enthalten. =! @** -Zeichen, und der Wert des **DSN** -Schlüssel Worts darf nicht nur aus Leerzeichen bestehen. Aufgrund der Registrierungs Grammatik dürfen Schlüsselwörter und Datenquellen Namen keinen umgekehrten Schrägstrich ( \\ ) enthalten.  
  
 **ConfigDSN** sollte **sqlvaliddsn** aufzurufen, um die Länge des Datenquellen namens zu überprüfen und zu überprüfen, ob der Name ungültige Zeichen enthält. Wenn der Name der Datenquelle länger ist als SQL_MAX_DSN_LENGTH oder ungültige Zeichen enthält, gibt **sqlvaliddsn** einen Fehler zurück, und **ConfigDSN** gibt einen Fehler zurück. Die Länge des Datenquellen namens wird auch von **sqlschreitedsneinini**geprüft.  
  
 Wenn Sie z. b. eine Datenquelle konfigurieren möchten, die eine Benutzer-ID, ein Kennwort und einen Datenbanknamen erfordert, kann eine Setup Anwendung die folgenden Schlüsselwort-Wert-Paare übergeben:  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 Weitere Informationen zu diesen Schlüsselwörtern finden Sie unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) und Dokumentation zu den einzelnen Treibern.  
  
 Um ein Dialogfeld anzuzeigen, darf *hwndParent* nicht NULL sein.  
  
## <a name="adding-a-data-source"></a>Hinzufügen von Datenquellen  
 Wenn ein Datenquellen Name in *lpszattribute*an **ConfigDSN** übergeben wird, prüft **ConfigDSN** , ob der Name gültig ist. Wenn der Name der Datenquelle mit einem vorhandenen Datenquellen Namen übereinstimmt und *hwndParent* den Wert NULL hat, überschreibt **ConfigDSN** den vorhandenen Namen. Wenn Sie mit einem vorhandenen Namen übereinstimmt und *hwndParent* nicht NULL ist, wird der Benutzer von **ConfigDSN** aufgefordert, den vorhandenen Namen zu überschreiben.  
  
 Wenn *lpszattribute* genügend Informationen zum Herstellen einer Verbindung mit einer Datenquelle enthält, kann **ConfigDSN** die Datenquelle hinzufügen oder ein Dialogfeld anzeigen, mit dem der Benutzer die Verbindungsinformationen ändern kann. Wenn *lpszattribute* nicht genügend Informationen zum Herstellen einer Verbindung mit einer Datenquelle enthält, muss der **ConfigDSN** die erforderlichen Informationen bestimmen. Wenn *hwndParent* nicht NULL ist, wird ein Dialogfeld angezeigt, in dem die Informationen vom Benutzer abgerufen werden.  
  
 Wenn in **ConfigDSN** ein Dialogfeld angezeigt wird, müssen alle an ihn weiter gegebenen Verbindungsinformationen in *lpszattribute*angezeigt werden. Insbesondere, wenn ein Datenquellen Name an ihn übermittelt wurde, wird in **ConfigDSN** dieser Name angezeigt, aber der Benutzer kann ihn nicht ändern. **ConfigDSN** kann Standardwerte für Verbindungsinformationen bereitstellen, die nicht in *lpszattribute*an ihn übergeben werden.  
  
 Wenn **ConfigDSN** keine kompletten Verbindungsinformationen für eine Datenquelle erhalten kann, wird false zurückgegeben.  
  
 Wenn **ConfigDSN** umfassende Verbindungsinformationen für eine Datenquelle erhalten kann, wird **sqlwrite tedsndeini** in der Installationsprogramm-dll aufgerufen, um die neue Datenquellen Spezifikation zur Odbc.ini Datei (oder Registrierung) hinzuzufügen. **Sqlwrite tedsndeini** fügt dem Abschnitt [ODBC Data Sources] den Datenquellen Namen hinzu, erstellt den Abschnitt Datenquellen Spezifikation und fügt das **Treiber** Schlüsselwort mit der Treiber Beschreibung als Wert hinzu. **ConfigDSN** ruft **sqlwrite teprivateprofilestring** in der Installationsprogramm-dll auf, um alle zusätzlichen Schlüsselwörter und Werte hinzuzufügen, die vom Treiber verwendet werden.  
  
## <a name="modifying-a-data-source"></a>Ändern einer Datenquelle  
 Um eine Datenquelle zu ändern, muss ein Datenquellen Name in *lpszattribute*an **ConfigDSN** übergeben werden. **ConfigDSN** überprüft, ob der Name der Datenquelle in der Odbc.ini Datei (oder Registrierung) enthalten ist.  
  
 Wenn *hwndParent* den Wert NULL hat, verwendet **ConfigDSN** die Informationen in *lpszattribute* , um die Informationen in der Odbc.ini-Datei (oder Registrierung) zu ändern. Wenn *hwndParent* nicht NULL ist, zeigt **ConfigDSN** ein Dialogfeld mit den Informationen in *lpszattribute*an. Informationen, die nicht in *lpszattribute*verwendet werden, werden anhand der Informationen aus den Systeminformationen verwendet. Der Benutzer kann die Informationen ändern, bevor er von **ConfigDSN** in den Systeminformationen gespeichert wird.  
  
 Wenn der Name der Datenquelle geändert wurde, ruft **ConfigDSN** zuerst **sqlremovedsnfromini** in der Installationsprogramm-dll auf, um die vorhandene Datenquellen Spezifikation aus der Odbc.ini Datei (oder Registrierung) zu entfernen. Anschließend werden die Schritte im vorherigen Abschnitt befolgt, um die neue Datenquellen Spezifikation hinzuzufügen. Wenn der Datenquellen Name nicht geändert wurde, ruft **ConfigDSN** **sqlwrite teprivateprofilestring** in der Installationsprogramm-dll auf, um weitere Änderungen vorzunehmen. Der Wert des **Treiber** Schlüsselworts kann von **ConfigDSN** nicht gelöscht oder geändert werden.  
  
## <a name="deleting-a-data-source"></a>Löschen einer Datenquelle  
 Zum Löschen einer Datenquelle muss ein Datenquellen Name in *lpszattribute*an **ConfigDSN** übergeben werden. **ConfigDSN** überprüft, ob der Name der Datenquelle in der Odbc.ini Datei (oder Registrierung) enthalten ist. Anschließend wird **sqlremovedsnfromini** in der Installationsprogramm-dll aufgerufen, um die Datenquelle zu entfernen.  
  
## <a name="note"></a>Hinweis
 Wenn Sie eine Unicode-Version dieser Routine schreiben, muss Sie mit "LPCWSTR"-Argumenten anstelle von "LPCSTR" als " **configdsnw**" bezeichnet werden.
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Erhalten eines Werts aus der Odbc.ini Datei oder der Registrierung|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|Entfernen der Standarddaten Quelle|[Sqlremovedefaultdatasource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Entfernen eines Datenquellen namens aus Odbc.ini (oder der Registrierung)|[Sqlremovedsnfromini](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Hinzufügen eines Datenquellen namens zu Odbc.ini (oder Registrierung)|[Sqlschreitedsnder ini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Schreiben eines Werts in die Odbc.ini Datei oder die Registrierung|[Sqlschreiteprivateprofilestring](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
