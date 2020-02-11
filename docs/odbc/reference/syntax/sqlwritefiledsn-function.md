---
title: Sqlwrite tefiledsn-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWriteFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteFileDSN
helpviewer_keywords:
- SQLWriteFileDSN [ODBC]
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8b1ce34074a2326d17a199537b308a9a670d8163
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039430"
---
# <a name="sqlwritefiledsn-function"></a>SQLWriteFileDSN-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqlwrite tefiledsn** schreibt Informationen in einen Datei-DSN.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszfilename*  
 Der Zeiger auf den Namen des Datei-DSN. Eine DSN-Erweiterung wird an alle Dateinamen angehängt, die noch nicht über eine DSN-Erweiterung verfügen.  
  
 *lpszappname*  
 Der Zeiger auf den Namen der Anwendung. Dies ist "ODBC" für den ODBC-Abschnitt.  
  
 *lpszkeyname*  
 Der Zeiger auf den Namen des zu lesenden Schlüssels. Informationen zu reservierten Schlüsselwörtern finden Sie unter "Kommentare".  
  
 *lpszstring*  
 Ausgeben Verweist auf die Zeichenfolge, die dem zu schreibenden Schlüssel zugeordnet ist. Die maximale Länge der Zeichenfolge, auf die durch dieses Argument verwiesen wird, beträgt 32.767 bytes.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlwrite tefiledsn** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad.|Der im *lpszfilename* -Argument angegebene Dateiname ist ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das Argument " *lpszappname*", " *lpszkeyname*" oder " *lpszstring* " war NULL.|  
  
## <a name="comments"></a>Kommentare  
 ODBC reserviert den Abschnittsnamen [ODBC], in dem die Verbindungsinformationen gespeichert werden sollen. Die reservierten Schlüsselwörter für diesen Abschnitt sind identisch mit denen, die für eine Verbindungs Zeichenfolge in **SQLDriverConnect**reserviert sind. (Weitere Informationen finden Sie in der Beschreibung der [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) -Funktion.)  
  
 Anwendungen können diese reservierten Schlüsselwörter verwenden, um Informationen direkt in einen Datei-DSN zu schreiben. Wenn eine Anwendung die DSN-Less-Verbindungs Zeichenfolge erstellen oder ändern möchte, die einem Datei-DSN zugeordnet ist, kann Sie **sqlwrite tefiledsn** für beliebige Schlüsselwörter der reservierten Verbindungs Zeichenfolge im Abschnitt [ODBC] aufzurufen.  
  
 Wenn das *lpszstring* -Argument ein NULL-Zeiger ist, wird das Schlüsselwort, auf das durch das *lpszkeyname* -Argument verwiesen wird, aus der DSN-Datei gelöscht. Wenn die Argumente *lpszstring* und *lpszkeyname* beide NULL-Zeiger sind, wird der Abschnitt, auf den das *lpszappname* -Argument zeigt, aus der DSN-Datei gelöscht.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Lesen von Informationen aus Datei-DSNs|[Sqllesfiledsn](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
