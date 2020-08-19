---
description: SQLWritePrivateProfileString-Funktion
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1110b60d6dc0ba079804ba8a9f21c06f0c1f78d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420954"
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 2,0  
  
 **Zusammenfassung**  
 **Sqlwrite teprivateprofilestring** schreibt einen Wertnamen und Daten in den Odbc.ini Unterschlüssel der Systeminformationen.  
  
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
 Wenn **sqlwrite teprivateprofilestring** false zurückgibt, kann ein zugeordneter " * \* pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die " * \* pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Die angeforderten Systeminformationen konnten nicht geschrieben werden.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
  
## <a name="comments"></a>Kommentare  
 **Sqlwrite teprivateprofilestring** ist eine einfache Möglichkeit zum Portieren von Treibern und Treiber Setup-DLLs von Microsoft® Windows® an Microsoft Windows NT®/Windows 2000. Aufrufe von "Write- **PrivateProfileString** ", die eine Profil Zeichenfolge in die Odbc.ini Datei schreiben, sollten durch Aufrufe von " **sqlschreiteprivateprofilestring**" ersetzt werden. **Sqlwrite teprivateprofilestring** Ruft Funktionen in der Win32-®-API auf, um den angegebenen Wertnamen und die Daten dem Odbc.ini Unterschlüssel der Systeminformationen hinzuzufügen.  
  
 Ein Konfigurations Modus gibt an, wo die Odbc.ini Eintrag DSN-Werte in den Systeminformationen enthalten ist. Wenn es sich bei dem DSN um einen Benutzer-DSN handelt (die Zustands Variable ist USERDSN_ONLY), schreibt die Funktion in HKEY_CURRENT_USER in den Odbc.ini Eintrag. Wenn es sich bei dem DSN um einen System-DSN (SYSTEMDSN_ONLY) handelt, schreibt die Funktion in HKEY_LOCAL_MACHINE in den Odbc.ini Eintrag. Wenn die Zustands Variable bothdsn ist, wird HKEY_CURRENT_USER versucht, und wenn Sie fehlschlägt, wird HKEY_LOCAL_MACHINE verwendet.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Erhalten eines Werts aus den Systeminformationen|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|
