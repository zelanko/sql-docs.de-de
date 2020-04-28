---
title: Sqlleserfiledsn-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLReadFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLReadFileDSN
helpviewer_keywords:
- SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abda956ee7682c9ac49270e8bf69fb039641790
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303951"
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,0  
  
 **Zusammenfassung**  
 **Sqllesefiledsn** liest Informationen aus einem Datei-DSN.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLReadFileDSN(  
     LPCSTR   lpszFileName,  
     LPCSTR   lpszAppName,  
     LPCSTR   lpszKeyName,  
     LPSTR    lpszString,  
     WORD     cbString,  
     WORD *   pcbString);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszfilename*  
 Der Ein Zeiger auf den Datenpuffer, der den Namen der DSN-Datei enthält. Eine DSN-Erweiterung wird an alle Dateinamen angehängt, die noch nicht über eine DSN-Erweiterung verfügen. Der Wert in * \*"lpszfilename* " muss eine NULL-terminierte Zeichenfolge sein.  
  
 *lpszappname*  
 Der Zeiger auf den Datenpuffer, der den Namen der Anwendung enthält. Dies ist "ODBC" für den ODBC-Abschnitt. Der Wert in * \*"lpszappname* " muss eine NULL-terminierte Zeichenfolge sein.  
  
 *lpszkeyname*  
 Der Ein Zeiger auf den Datenpuffer, der den Namen des zu lesenden Schlüssels enthält. Informationen zu reservierten Schlüsselwörtern finden Sie unter "Kommentare". Der Wert in * \*"lpszappname* " muss eine NULL-terminierte Zeichenfolge sein.  
  
 *lpszstring*  
 Ausgeben Ein Zeiger auf den Datenpuffer, der die Zeichenfolge enthält, die dem zu lesenden Schlüssel zugeordnet ist.  
  
 Wenn * \*lpszfilename* ein gültiger DSN-Dateiname ist, das *lpszappname* -Argument jedoch ein NULL-Zeiger ist und das *lpszkeyname* -Argument ein NULL-Zeiger ist, enthält * \*lpszstring* eine Liste gültiger Anwendungen. Wenn * \*lpszfilename* ein gültiger DSN-Dateiname und * \*lpszappname* ein gültiger Anwendungsname ist, das *lpszkeyname* -Argument jedoch ein NULL-Zeiger ist, enthält * \*lpszstring* eine Liste gültiger reservierter Schlüsselwörter im entsprechenden Abschnitt der DSN-Datei, getrennt durch Semikolons. Wenn * \*lpszfilename* ein gültiger DSN-Dateiname ist, aber * \*lpszappname* ein NULL-Zeiger ist und das *lpszkeyname* -Argument ein NULL-Zeiger ist, enthält * \*lpszstring* eine Liste der Abschnitte in der DSN-Datei, die durch Semikolons getrennt sind.  
  
 *cbString*  
 Der Länge des * \*lpszstring* -Puffers.  
  
 *pcbstring*  
 Ausgeben Gesamtanzahl von Bytes, die in * \*lpszstring*zurückgegeben werden können. Wenn die Anzahl von Bytes, die zurückgegeben werden können, größer oder gleich *cbString*ist, wird die Ausgabe Zeichenfolge in * \*lpszstring* auf *cbString* abzüglich des NULL-Beendigungs Zeichens gekürzt. Das *pcbstring* -Argument kann ein NULL-Zeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt true zurück, wenn Sie erfolgreich ist, andernfalls false.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqllefiledsn** false zurückgibt, kann ein zugeordneter " * \*pferrorcode* "-Wert durch Aufrufen von " **sqlinstallererror**" abgerufen werden. In der folgenden Tabelle sind die * \*"pferrorcode* "-Werte aufgelistet, die von " **sqlinstallererror** " zurückgegeben werden können. Diese werden im Kontext dieser Funktion erläutert.  
  
|*\*pferrorcode*|Fehler|BESCHREIBUNG|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installer-Fehler|Es ist ein Fehler aufgetreten, bei dem kein spezifischer installerfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Das *lpszstring* -Argument war NULL.<br /><br /> Das *cbString* -Argument war kleiner als oder gleich 0 (null).|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad.|Der im *lpszfilename* -Argument angegebene Dateiname ist ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung.|Das *lpszappname* -Argument war NULL, während das *lpszkeyname* -Argument gültig war.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines fehlenden Speichers nicht ausführen.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Ausgabe Zeichenfolge abgeschnitten|Die in * \*"lpszstring* " zurückgegebene Zeichenfolge wurde abgeschnitten, da der Wert in " *cbString* " kleiner oder gleich dem Wert in * \*"pcbstring*" war.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Das Schlüsselwort ist im Datei-DSN nicht vorhanden.|  
  
## <a name="comments"></a>Kommentare  
 ODBC reserviert den Abschnittsnamen [ODBC], in dem die Verbindungsinformationen gespeichert werden sollen. Die reservierten Schlüsselwörter für diesen Abschnitt sind identisch mit denen, die für eine Verbindungs Zeichenfolge in **SQLDriverConnect**reserviert sind. (Weitere Informationen finden Sie in der Beschreibung der [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) -Funktion.)  
  
 Anwendungen können diese reservierten Schlüsselwörter verwenden, um die Informationen in einem Datei-DSN zu lesen. Wenn eine Anwendung die DSN-Less-Verbindungs Zeichenfolge ermitteln möchte, die einem Datei-DSN zugeordnet ist, kann Sie **sqlinfofiledsn** für beliebige Schlüsselwörter der reservierten Verbindungs Zeichenfolge im Abschnitt [ODBC] aufzurufen. Die vollständige Verbindungs Zeichenfolge, die an eine DSN-lose Verbindung weitergegeben wurde, ist eine Kombination aus allen Schlüsselwörtern (reserviert und Treiber spezifisch) im Abschnitt [ODBC].  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Siehe|  
|---------------------------|---------|  
|Schreiben von Informationen in einen Datei-DSN|[Sqlschreitefiledsn](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
