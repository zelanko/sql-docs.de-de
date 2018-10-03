---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c1f199d5f3318181aa03499c31d9597f2348fec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47655378"
---
# <a name="configdsn-function"></a>ConfigDSN-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC 1.0  
  
 **Zusammenfassung**  
 **ConfigDSN** hinzufügt, ändert oder löscht Sie Datenquellen aus der Systeminformationen. Sie können den Benutzer zur Verbindungsinformationen aufgefordert. Es kann in die Treiber-DLL oder eine separate Setup-DLL sein.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
BOOL ConfigDSN(  
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
  
 ODBC_ADD_DSN: Fügen Sie eine neue Datenquelle hinzu.  
  
 ODBC_CONFIG_DSN: Konfigurieren (ändern) einer vorhandenen Datenquelle.  
  
 ODBC_REMOVE_DSN: Entfernen einer vorhandenen Datenquelle.  
  
 *lpszDriver*  
 [Eingabe] Treiberbeschreibung (normalerweise der Name des zugeordneten DBMS) für Benutzer anstelle des Namens des physischen Treiber angezeigt werden.  
  
 *lpszAttributes*  
 [Eingabe] Eine doppelt Null-terminierte Liste von Attributen in Form von Schlüsselwort-Wert-Paaren. Weitere Informationen finden Sie unter "Kommentare".  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **ConfigDSN** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert an den Installer Fehler Puffer gesendet wird, durch einen Aufruf von **SQLPostInstallerError** und erhalten Sie durch Aufrufen von **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Ungültiges Fenster-handle|Die *HwndParent* Argument war ungültig.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Ungültiges Schlüsselwort-Wert-Paaren|Die *LpszAttributes* Argument enthalten einen Syntaxfehler.|  
|ODBC_ERROR_INVALID_NAME|Ungültiger Name für Treiber oder das Konvertierungsprogramm|Die *LpszDriver* Argument war ungültig. Es konnte nicht in der Registrierung gefunden werden.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *häufigsten* Argument war keiner der folgenden:<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN|  
|ODBC_ERROR_REQUEST_FAILED|*Anforderung* Fehler|Den angeforderte Vorgang konnte nicht ausgeführt werden die *häufigsten* Argument.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Oder Translator-treiberspezifischen Fehler|Ein Treiber-spezifische Fehler, für die kein definierten ODBC-Installer-Fehler vorliegt. Die *SzError* Argument in einem Aufruf der **SQLPostInstallerError** Funktion sollte die treiberspezifische Fehlermeldung enthalten.|  
  
## <a name="comments"></a>Kommentare  
 **ConfigDSN** empfängt Verbindungsinformationen aus dem Installationsprogramm-DLL als eine Liste der Attribute in Form von Schlüsselwort-Wert-Paaren. Jedes Paar wird mit null Byte beendet, und die gesamte Liste wird mit null Byte beendet. (D. h., markieren Sie zwei null-Bytes am Ende der Liste.) Leerzeichen sind vor und hinter dem Gleichzeichen im Schlüsselwort-Wert-Paar nicht zulässig. **ConfigDSN** lässt Schlüsselwörter, die keine gültigen Schlüsselwörter für sind **SQLBrowseConnect** und **SQLDriverConnect**. **ConfigDSN** unterstützt nicht zwangsläufig alle Schlüsselwörter, die gültigen Schlüsselwörter für **SQLBrowseConnect** und **SQLDriverConnect**. (**ConfigDSN** akzeptiert nicht den **Treiber** Schlüsselwort.) Die Schlüsselwörter ein, die die **ConfigDSN** Funktion muss unterstützen alle Optionen erforderlich, um die Datenquelle über die automatische-Setup-Funktion des Installationsprogramms erneut zu erstellen. Wenn die Verwendung der **ConfigDSN** Werte und die Werte der Verbindungszeichenfolgen sind identisch, die gleichen Schlüsselwörtern verwendet werden sollte.  
  
 Wie in **SQLBrowseConnect** und **SQLDriverConnect**, Schlüsselwörter und deren Werte sollten keine der **[]{}();? \*=! @** Zeichen und den Wert des der **DSN** Schlüsselwort darf nicht ausschließlich aus Leerzeichen bestehen. Aufgrund der Grammatik Registrierung darf keine Schlüsselwörter und Namen von Datenquellen enthalten, den umgekehrten Schrägstrich (\\) Zeichen.  
  
 **ConfigDSN** sollten Aufrufen **SQLValidDSN** überprüfen die Länge der Namen der Datenquelle und stellen Sie sicher, dass keine ungültigen Zeichen im Namen enthalten sind. Wenn der Name der Datenquelle länger als SQL_MAX_DSN_LENGTH ist oder ungültige Zeichen enthält, **SQLValidDSN** gibt einen Fehler zurück und **ConfigDSN** gibt einen Fehler zurück. Außerdem wird die Länge der Namen der Datenquelle durch überprüft **SQLWriteDSNToIni**.  
  
 Zum Konfigurieren einer Datenquelle, die ein Benutzer-ID, Kennwort und Name der Datenbank erfordert möglicherweise eine setupanwendung z. B. die folgenden Schlüsselwort-Wert-Paare übergeben:  
  
```  
DSN=Personnel Data\0UID=Smith\0PWD=Sesame\0DATABASE=Personnel\0\0  
```  
  
 Weitere Informationen zu diesen Schlüsselwörtern finden Sie unter [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) und des Treibers-Dokumentation.  
  
 Um ein Dialogfeld anzuzeigen *HwndParent* darf nicht null sein.  
  
## <a name="adding-a-data-source"></a>Hinzufügen von Datenquellen  
 Wenn Name der Datenquelle, um übergeben wird **ConfigDSN** in *LpszAttributes*, **ConfigDSN** stellt sicher, dass der Name gültig ist. Wenn der Name der Datenquelle einen existierender Datenquellenname übereinstimmt und *HwndParent* null ist, **ConfigDSN** überschreibt den vorhandenen Namen. Wenn sie einen vorhandenen Namen übereinstimmt und *HwndParent* ist nicht null, **ConfigDSN** fordert den Benutzer auf den vorhandenen Namen zu überschreiben.  
  
 Wenn *LpszAttributes* enthält genügend Informationen zur Verbindung mit einer Datenquelle **ConfigDSN** hinzufügen können, die Datenquelle oder zeigt ein Dialogfeld, mit denen der Benutzer kann die Verbindungsinformationen ändern. Wenn *LpszAttributes* enthält genügend Informationen zur Verbindung mit einer Datenquelle keine **ConfigDSN** müssen die erforderlichen Informationen ermitteln, ob *HwndParent* ist nicht null ist, ein Dialogfeld zum Abrufen von Informationen aus dem Benutzer angezeigt.  
  
 Wenn **ConfigDSN** wird ein Dialogfeld angezeigt, müssen sie alle Verbindungsinformationen, die im übergebenen anzeigen *LpszAttributes*. Insbesondere, wenn der Name der Datenquelle an sie übergeben wurde **ConfigDSN** wird dieser Name angezeigt, nicht jedoch den Benutzer, ihn zu ändern. **ConfigDSN** können Standardwerte für die Verbindungsinformationen, die nicht übergeben, in bereitstellen *LpszAttributes*.  
  
 Wenn **ConfigDSN** kann nicht abgerufen werden vollständige Verbindungsinformationen für eine Datenquelle, wird FALSE zurückgegeben.  
  
 Wenn **ConfigDSN** erhalten vollständigen Verbindungsinformationen für eine Datenquelle, ruft es **SQLWriteDSNToIni** im Installationsprogramm-DLL für die Angabe der neuen Datenquelle auf die Datei Odbc.ini (oder die Registrierung) hinzufügen. **SQLWriteDSNToIni** im Abschnitt [ODBC-Datenquellen] der Name der Datenquelle hinzugefügt, erstellt Data Source-Spezifikation-Abschnitt und fügt die **Treiber** Schlüsselwort mit der treiberbeschreibung "als Wert. **ConfigDSN** Aufrufe **SQLWritePrivateProfileString** im Installationsprogramm-DLL für jede zusätzliche Schlüsselwörter und Werte, die vom Treiber verwendeten hinzufügen.  
  
## <a name="modifying-a-data-source"></a>Ändern einer Datenquelle  
 Um eine Datenquelle zu ändern, Name der Datenquelle übergeben werden muss, um **ConfigDSN** in *LpszAttributes*. **ConfigDSN** Überprüfungen, die Namen der Datenquelle in der Datei Odbc.ini (oder das Registrierung) ist.  
  
 Wenn *HwndParent* null ist, **ConfigDSN** verwendet die Informationen in *LpszAttributes* zum Ändern der Informationen in der Datei Odbc.ini (oder Registrierung). Wenn *HwndParent* ist nicht null, **ConfigDSN** zeigt ein Dialogfeld mit den Informationen in *LpszAttributes*Informationen, die nicht in *LpszAttributes* , Informationen aus der Systeminformationen verwendet. Der Benutzer kann die Informationen vor dem Ändern **ConfigDSN** speichert sie in den Systeminformationen.  
  
 Wenn der Name der Datenquelle geändert wurde, **ConfigDSN** ruft zuerst **SQLRemoveDSNFromIni** im Installer source DLL So entfernen Sie die vorhandenen Daten Spezifikation aus der Datei Odbc.ini (oder Registrierung). Daraus folgt dann die Schritte im vorherigen Abschnitt, um die Angabe der neuen Datenquelle hinzufügen. Wenn der Name der Datenquelle nicht geändert wurde, **ConfigDSN** Aufrufe **SQLWritePrivateProfileString** im Installationsprogramm-DLL für andere Änderungen vornehmen. **ConfigDSN** möglicherweise nicht löschen oder ändern Sie den Wert, der die **Treiber** Schlüsselwort.  
  
## <a name="deleting-a-data-source"></a>Löschen einer Datenquelle  
 Um eine Datenquelle zu löschen, Name der Datenquelle übergeben werden muss, um **ConfigDSN** in *LpszAttributes*. **ConfigDSN** Überprüfungen, die Namen der Datenquelle in der Datei Odbc.ini (oder das Registrierung) ist. Es ruft dann **SQLRemoveDSNFromIni** im Installationsprogramm-DLL für die Datenquelle zu entfernen.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Hinzufügen, ändern oder Entfernen einer Datenquelle|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Übergeben eines Werts aus der Datei Odbc.ini oder die Registrierung|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|  
|Entfernen die Standarddatenquelle|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Entfernen einen Datenquellennamen Odbc.ini (oder der Registrierung)|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Hinzufügen von einem Datenquellennamen Odbc.ini (oder Registrierung)|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|  
|Schreiben einen Wert in der Datei Odbc.ini oder die Registrierung|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|
