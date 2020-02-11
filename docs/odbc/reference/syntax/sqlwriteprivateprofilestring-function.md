---
title: Sqlwrite teprivateprofilestring-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039384"
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **Sqlwrite teprivateprofilestring** schreibt einen Wertnamen und Daten in den Unterschlüssel ODBC. ini der Systeminformationen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszsection*  
 Der Verweist auf eine auf NULL endende Zeichenfolge, die den Namen des Abschnitts enthält, in den die Zeichenfolge kopiert werden soll. Wenn der Abschnitt nicht vorhanden ist, wird er erstellt. Der Name des Abschnitts ist groß-und Kleinschreibung. die Zeichenfolge kann eine beliebige Kombination aus Groß-und Kleinbuchstaben sein.  
  
 *lpszentry*  
 Der Verweist auf eine auf NULL endende Zeichenfolge mit dem Namen des Schlüssels, der einer Zeichenfolge zugeordnet werden soll. Wenn der Schlüssel nicht im angegebenen Abschnitt vorhanden ist, wird er erstellt. Wenn dieses Argument NULL ist, wird der gesamte Abschnitt, einschließlich aller Einträge innerhalb des Abschnitts, gelöscht.  
  
 *lpszstring*  
 Der Verweist auf eine mit NULL endende Zeichenfolge, die in die Datei geschrieben werden soll. Wenn dieses Argument NULL ist, wird der Schlüssel, auf den vom *lpszentry* -Argument verwiesen wird, gelöscht.  
  
 *lpszfilename*  
 Ausgeben Verweist auf eine mit NULL endenden Zeichenfolge, die die Initialisierungsdatei benennt.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlwrite teprivateprofilestring** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_REQUEST_FAILED|Anforderung fehlgeschlagen|Die angeforderten Systeminformationen konnten nicht geschrieben werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlwrite teprivateprofilestring** ist eine einfache Möglichkeit zum Portieren von Treibern und Treiber Setup-DLLs von Microsoft® Windows® an Microsoft Windows NT®/Windows 2000. Aufrufe von " **Write-PrivateProfileString** ", die eine Profil Zeichenfolge in die Datei "ODBC. ini" schreiben, sollten durch Aufrufe von **sqlschreiteprivateprofilestring**ersetzt werden. **Sqlwrite teprivateprofilestring** Ruft Funktionen in der Win32-®-API auf, um den angegebenen Wertnamen und die Daten dem Unterschlüssel "ODBC. ini" der Systeminformationen hinzuzufügen.  
  
 Ein Konfigurations Modus gibt an, wo sich der Eintrag "ODBC. ini" mit den DSN-Werten in den Systeminformationen befindet. Wenn es sich bei dem DSN um einen Benutzer-DSN handelt (die Zustands Variable ist USERDSN_ONLY), schreibt die Funktion in HKEY_CURRENT_USER in den Eintrag "ODBC. ini". Wenn es sich bei dem DSN um einen System-DSN (SYSTEMDSN_ONLY) handelt, schreibt die Funktion in HKEY_LOCAL_MACHINE in den Eintrag "ODBC. ini". Wenn die Zustands Variable bothdsn ist, wird HKEY_CURRENT_USER versucht, und wenn Sie fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Erhalten eines Werts aus den Systeminformationen|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
