---
title: ConfigDSN-Funktion | Microsoft Docs
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
ms.openlocfilehash: fbae126c819088bd277621b207454503a86c8955
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306041"
---
# <a name="configdsn-function"></a>ConfigDSN-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0  
  
 **Zusammenfassung**  
 **ConfigDSN** fügt Datenquellen aus den Systeminformationen hinzu, ändert oder löscht sie. Möglicherweise wird der Benutzer aufgefordert, Verbindungsinformationen einzugeben. Sie kann sich in der Treiber-DLL oder in einer separaten Setup-DLL befinden.  
  
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
 [Eingabe] Übergeordnetes Fensterhandle. Die Funktion zeigt keine Dialogfelder an, wenn das Handle null ist.  
  
 *fRequest*  
 [Eingabe] Art der Anforderung. Das *fRequest-Argument* muss einen der folgenden Werte enthalten:  
  
 ODBC_ADD_DSN: Fügen Sie eine neue Datenquelle hinzu.  
  
 ODBC_CONFIG_DSN: Konfigurieren (ändern) einer vorhandenen Datenquelle.  
  
 ODBC_REMOVE_DSN: Entfernen Sie eine vorhandene Datenquelle.  
  
 *lpszDriver*  
 [Eingabe] Treiberbeschreibung (in der Regel der Name des zugehörigen DBMS), die den Benutzern anstelle des physischen Treibernamens angezeigt wird.  
  
 *lpszAttributes*  
 [Eingabe] Eine doppelt null-terminierte Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Weitere Informationen finden Sie unter "Kommentare".  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigDSN** FALSE zurückgibt, wird ein zugeordneter * \*pfErrorCode-Wert* durch einen Aufruf von **SQLPostInstallerError** an den Installer-Fehlerpuffer gesendet und kann durch Aufrufen von **SQLInstallerError**abgerufen werden. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fensterhandle|Das *Argument hwndParent* war ungültig.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültige Schlüsselwort-Wert-Paare|Das Argument *lpszAttributes* enthielt einen Syntaxfehler.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Treiber- oder Übersetzername|Das *Argument lpszDriver* war ungültig. Sie konnte in der Registrierung nicht gefunden werden.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das *fRequest-Argument* war nicht eines der folgenden:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* fehlgeschlagen|Der vom *fRequest-Argument* angeforderte Vorgang konnte nicht ausgeführt werden.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Treiber- oder Übersetzerspezifischer Fehler|Ein treiberspezifischer Fehler, für den kein definierter ODBC-Installationsfehler vorliegt. Das *SzError-Argument* in einem Aufruf der **SQLPostInstallerError-Funktion** sollte die treiberspezifische Fehlermeldung enthalten.|  
  
## <a name="comments"></a>Kommentare  
 **ConfigDSN** empfängt Verbindungsinformationen von der Installations-DLL als Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Jedes Paar wird mit einem NULL-Byte beendet, und die gesamte Liste wird mit einem NULL-Byte beendet. (Das heißt, zwei Nullbytes markieren das Ende der Liste.) Leerzeichen sind um das Gleichheitszeichen im Schlüsselwort-Wert-Paar nicht zulässig. **ConfigDSN** kann Schlüsselwörter akzeptieren, die keine gültigen Schlüsselwörter für **SQLBrowseConnect** und **SQLDriverConnect**sind. **ConfigDSN** unterstützt nicht unbedingt alle Schlüsselwörter, die gültige Schlüsselwörter für **SQLBrowseConnect** und **SQLDriverConnect**sind. (**ConfigDSN** akzeptiert das **DRIVER-Schlüsselwort** nicht.) Die von der **ConfigDSN-Funktion** verwendeten Schlüsselwörter müssen alle Optionen unterstützen, die zum erneuten Erstellen der Datenquelle mithilfe der AUTO-Setupfunktion des Installationsprogramms erforderlich sind. Wenn die Verwendung der **ConfigDSN-Werte** und der Verbindungszeichenfolgenwerte identisch sind, sollten dieselben Schlüsselwörter verwendet werden.  
  
 Wie in **SQLBrowseConnect** und **SQLDriverConnect**sollten die Schlüsselwörter und ihre Werte nicht die **[] (),;?{} \*=!** Zeichen, und der Wert des **DSN-Schlüsselworts** kann nicht nur aus Leerzeichen bestehen. Aufgrund der Registrierungsgrammatik dürfen Schlüsselwörter und Datenquellennamen nicht\\den umgekehrten Schrägstrich ( ) enthalten.  
  
 **ConfigDSN** sollte **SQLValidDSN** aufrufen, um die Länge des Datenquellennamens zu überprüfen und um sicherzustellen, dass keine ungültigen Zeichen im Namen enthalten sind. Wenn der Datenquellenname länger als SQL_MAX_DSN_LENGTH ist oder ungültige Zeichen enthält, gibt **SQLValidDSN** einen Fehler und **ConfigDSN** einen Fehler zurück. Die Länge des Datenquellennamens wird auch von **SQLWriteDSNToIni**überprüft.  
  
 Um beispielsweise eine Datenquelle zu konfigurieren, für die eine Benutzer-ID, ein Kennwort und ein Datenbankname erforderlich sind, kann eine Setupanwendung die folgenden Schlüsselwort-Wert-Paare übergeben:  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 Weitere Informationen zu diesen Schlüsselwörtern finden Sie unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) und in der Dokumentation der einzelnen Treiber.  
  
 Um ein Dialogfeld anzuzeigen, darf *hwndParent* nicht null sein.  
  
## <a name="adding-a-data-source"></a>Hinzufügen von Datenquellen  
 Wenn ein Datenquellenname in *lpszAttributes*an **ConfigDSN** übergeben wird, überprüft **ConfigDSN,** ob der Name gültig ist. Wenn der Datenquellenname mit einem vorhandenen Datenquellennamen übereinstimmt und *hwndParent* null ist, überschreibt **ConfigDSN** den vorhandenen Namen. Wenn es mit einem vorhandenen Namen übereinstimmt und *hwndParent* nicht null ist, fordert **ConfigDSN** den Benutzer auf, den vorhandenen Namen zu überschreiben.  
  
 Wenn *lpszAttributes* genügend Informationen zum Herstellen einer Verbindung mit einer Datenquelle enthält, kann **ConfigDSN** die Datenquelle hinzufügen oder ein Dialogfeld anzeigen, mit dem der Benutzer die Verbindungsinformationen ändern kann. Wenn *lpszAttributes* nicht genügend Informationen zum Herstellen einer Verbindung mit einer Datenquelle enthält, muss **ConfigDSN** die erforderlichen Informationen ermitteln. Wenn *hwndParent* nicht null ist, wird ein Dialogfeld angezeigt, um die Informationen vom Benutzer abzurufen.  
  
 Wenn **ConfigDSN** ein Dialogfeld anzeigt, muss es alle Verbindungsinformationen anzeigen, die an das Dialogfeld in *lpszAttributes*übergeben werden. Wenn ihm insbesondere ein Datenquellenname übergeben wurde, zeigt **ConfigDSN** diesen Namen an, erlaubt dem Benutzer jedoch nicht, ihn zu ändern. **ConfigDSN** kann Standardwerte für Verbindungsinformationen bereitstellen, die in *lpszAttributes*nicht an ihn übergeben werden.  
  
 Wenn **ConfigDSN** keine vollständigen Verbindungsinformationen für eine Datenquelle abrufen kann, wird FALSE zurückgegeben.  
  
 Wenn **ConfigDSN** vollständige Verbindungsinformationen für eine Datenquelle abrufen kann, ruft es **SQLWriteDSNToIni** in der Installations-DLL auf, um die neue Datenquellenspezifikation zur Datei (oder Registrierung) Odbc.ini hinzuzufügen. **SQLWriteDSNToIni** fügt den Datenquellennamen zum Abschnitt [ODBC Data Sources] hinzu, erstellt den Abschnitt datenquellenspezifikation und fügt das **Schlüsselwort DRIVER** mit der Treiberbeschreibung als Wert hinzu. **ConfigDSN** ruft **SQLWritePrivateProfileString** in der Installations-DLL auf, um zusätzliche Schlüsselwörter und Werte hinzuzufügen, die vom Treiber verwendet werden.  
  
## <a name="modifying-a-data-source"></a>Ändern einer Datenquelle  
 Um eine Datenquelle zu ändern, muss ein Datenquellenname in *lpszAttributes*an **ConfigDSN** übergeben werden. **ConfigDSN** überprüft, ob sich der Datenquellenname in der Datei (oder Registrierung) von Odbc.ini befindet.  
  
 Wenn *hwndParent* null ist, verwendet **ConfigDSN** die Informationen in *lpszAttributes,* um die Informationen in der Datei Odbc.ini (oder Registrierung) zu ändern. Wenn *hwndParent* nicht null ist, zeigt **ConfigDSN** ein Dialogfeld mit den Informationen in *lpszAttributes*an. für Informationen, die nicht in *lpszAttributes*enthalten sind, werden Informationen aus den Systeminformationen verwendet. Der Benutzer kann die Informationen ändern, bevor **ConfigDSN** sie in den Systeminformationen speichert.  
  
 Wenn der Datenquellenname geändert wurde, ruft **ConfigDSN** **SQLRemoveDSNFromIni** zuerst in der Installations-DLL auf, um die vorhandene Datenquellenspezifikation aus der Odbc.ini-Datei (oder Registrierung) zu entfernen. Anschließend folgen die Schritte im vorherigen Abschnitt, um die neue Datenquellenspezifikation hinzuzufügen. Wenn der Datenquellenname nicht geändert wurde, ruft **ConfigDSN** **SQLWritePrivateProfileString** in der Installations-DLL auf, um weitere Änderungen vorzunehmen. **ConfigDSN** darf den Wert des **Schlüsselworts Driver** nicht löschen oder ändern.  
  
## <a name="deleting-a-data-source"></a>Löschen einer Datenquelle  
 Um eine Datenquelle zu löschen, muss ein Datenquellenname in *lpszAttributes*an **ConfigDSN** übergeben werden. **ConfigDSN** überprüft, ob sich der Datenquellenname in der Datei (oder Registrierung) von Odbc.ini befindet. Anschließend wird **SQLRemoveDSNFromIni** in der Installations-DLL aufruft, um die Datenquelle zu entfernen.  
  
## <a name="note"></a>Hinweis
 Wenn Sie eine Unicode-Version dieser Routine schreiben, muss sie **ConfigDSNW**heißen, mit LPCWSTR-Argumenten anstelle von LPCSTR.
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, Ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Abrufen eines Werts aus der Datei Odbc.ini oder der Registrierung|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|Entfernen der Standarddatenquelle|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Entfernen eines Datenquellennamens aus Odbc.ini (oder Registrierung)|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Hinzufügen eines Datenquellennamens zu Odbc.ini (oder Registrierung)|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Schreiben eines Werts in die Datei Odbc.ini oder die Registrierung|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
