---
title: SQLWritePrivateProfileString-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWritePrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWritePrivateProfileString
helpviewer_keywords:
- SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b0de5ad074fb2b760420686feddff58b26887112
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286883"
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString-Funktion
**Konformität**  
 Eingeführte Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLWritePrivateProfileString** schreibt einen Wertnamen und Daten in den Unterschlüssel Odbc.ini der Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszSection*  
 [Eingabe] Zeigt auf eine null-terminierte Zeichenfolge, die den Namen des Abschnitts enthält, in den die Zeichenfolge kopiert wird. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist großfeinen Bestandteil; Die Zeichenfolge kann eine beliebige Kombination aus Groß- und Kleinbuchstaben sein.  
  
 *lpszEntry*  
 [Eingabe] Zeigt auf eine null-terminierte Zeichenfolge, die den Namen des Schlüssels enthält, der einer Zeichenfolge zugeordnet werden soll. Wenn der Schlüssel im angegebenen Abschnitt nicht vorhanden ist, wird er erstellt. Wenn dieses Argument NULL ist, wird der gesamte Abschnitt, einschließlich aller Einträge innerhalb des Abschnitts, gelöscht.  
  
 *lpszString*  
 [Eingabe] Verweist auf eine null-beendete Zeichenfolge, die in die Datei geschrieben werden soll. Wenn dieses Argument NULL ist, wird der Schlüssel, auf den das Argument *lpszEntry* zeigt, gelöscht.  
  
 *lpszDateiname*  
 [Ausgabe] Verweist auf eine null-terminierte Zeichenfolge, die die Initialisierungsdatei benennt.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLWritePrivateProfileString** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallerError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Die angeforderten Systeminformationen konnten nicht geschrieben werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **SQLWritePrivateProfileString** wird als einfache Möglichkeit zum Portieren von Treibern und Treiber-Setup-DLLs von Microsoft® Windows® auf Microsoft Windows NT®/Windows 2000 bereitgestellt. Aufrufe von **WritePrivateProfileString,** die eine Profilzeichenfolge in die Datei Odbc.ini schreiben, sollten durch Aufrufe von **SQLWritePrivateProfileString**ersetzt werden. **SQLWritePrivateProfileString** ruft Funktionen in der Win32®-API auf, um den angegebenen Wertnamen und die angegebenen Daten zum Unterschlüssel Odbc.ini der Systeminformationen hinzuzufügen.  
  
 Ein Konfigurationsmodus gibt an, wo sich die DSN-Werte von Odbc.ini in den Systeminformationen befinden. Wenn es sich bei dem DSN um eine Benutzer-DSN handelt (die Zustandsvariable ist USERDSN_ONLY), schreibt die Funktion in den Eintrag Odbc.ini in HKEY_CURRENT_USER. Wenn es sich bei dem DSN um ein System-DSN (SYSTEMDSN_ONLY) handelt, schreibt die Funktion in den Eintrag Odbc.ini in HKEY_LOCAL_MACHINE. Wenn die Zustandsvariable BOTHDSN ist, wird HKEY_CURRENT_USER versucht, und wenn sie fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Abrufen eines Werts aus den Systeminformationen|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
