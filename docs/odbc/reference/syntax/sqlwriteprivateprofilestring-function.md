---
title: SQLWritePrivateProfileString-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4b847576e503fbbbb511d2dda8f60675c298681c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039384"
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 2.0  
  
 **Zusammenfassung**  
 **SQLWritePrivateProfileString** schreibt eine Wertnamen und die Daten in der Odbc.ini Unterschlüssel der Systeminformationen.  
  
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
 [Eingabe] Verweist auf einen Null-terminierte Zeichenfolge, die mit dem Namen des Abschnitts, der die Zeichenfolge kopiert werden. Wenn der Abschnitt nicht vorhanden ist, wird es erstellt. Der Name des Abschnitts wird die Groß-/Kleinschreibung unabhängig; die Zeichenfolge kann eine beliebige Kombination von Groß- und Kleinbuchstaben sein.  
  
 *lpszEntry*  
 [Eingabe] Verweist auf einen Null-terminierte Zeichenfolge, die mit dem Namen des Schlüssels mit einer Zeichenfolge zugeordnet werden soll. Wenn der Schlüssel nicht im angegebenen Abschnitt vorhanden ist, wird es erstellt. Wenn dieses Argument NULL ist, wird der gesamte Abschnitt, einschließlich der Einträge im Abschnitt gelöscht.  
  
 *lpszString*  
 [Eingabe] Verweist auf einen Null-terminierte Zeichenfolge, die in die Datei geschrieben werden. Wenn dieses Argument NULL ist, der Schlüssel verweist die *LpszEntry* Argument wird gelöscht.  
  
 *lpszFilename*  
 [Ausgabe] Verweist auf eine auf Null endende Zeichenfolge, die Namen die Initialisierungsdatei.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLWritePrivateProfileString** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Die angeforderte Systeminformationen konnte nicht geschrieben werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
  
## <a name="comments"></a>Kommentare  
 **SQLWritePrivateProfileString** dient als eine einfache Möglichkeit, die Port-Treiber und Treiber-Setup-DLLs von Microsoft® Windows® für Microsoft Windows/Windows 2000. Aufrufe von **WritePrivateProfileString** schreiben eine Profil-Zeichenfolge in die Datei Odbc.ini ersetzt werden soll, mit Aufrufen von **SQLWritePrivateProfileString**. **SQLWritePrivateProfileString** Aufrufe von Funktionen in der Win32®-API der angegebenen Wertnamen und die Daten in der Unterschlüssel Odbc.ini die Systeminformationen hinzufügen.  
  
 Ein Konfigurationsmodus gibt an, in dem der Odbc.ini Eintrag Auflisten von DSN-Werte in den Systeminformationen. Wenn der DSN eine Benutzer-DSN ist (die Statusvariable USERDSN_ONLY), schreibt die Funktion, auf den Eintrag der Odbc.ini in HKEY_CURRENT_USER. Wenn der DSN eine System-DSN (SYSTEMDSN_ONLY) ist, schreibt die Funktion, auf den Eintrag der Odbc.ini in HKEY_LOCAL_MACHINE. HKEY_CURRENT_USER wird versucht, wenn die Statusvariable BOTHDSN ist, und schlägt fehl, HKEY_LOCAL_MACHINE verwendet wird.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Übergeben eines Werts aus der Systeminformationen|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
