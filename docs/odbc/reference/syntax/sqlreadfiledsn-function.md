---
title: SQLReadFileDSN-Funktion | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303951"
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLReadFileDSN** liest Informationen aus einem Datei-DSN.  
  
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
 *lpszFileName*  
 [Eingabe] Zeiger auf den Datenpuffer, der den Namen der .dsn-Datei enthält. Eine .dsn-Erweiterung wird an alle Dateinamen angehängt, die noch keine .dsn-Erweiterung haben. Der Wert in * \*lpszFileName* muss eine null-terminierte Zeichenfolge sein.  
  
 *lpszAppName*  
 [Eingabe] Zeiger auf den Datenpuffer, der den Namen der Anwendung enthält. Dies ist "ODBC" für den ODBC-Abschnitt. Der Wert in * \*lpszAppName* muss eine null-terminierte Zeichenfolge sein.  
  
 *lpszKeyName*  
 [Eingabe] Zeigen Sie auf den Datenpuffer, der den Namen des zu lesenden Schlüssels enthält. Siehe "Kommentare" für reservierte Keywords. Der Wert in * \*lpszAppName* muss eine null-terminierte Zeichenfolge sein.  
  
 *lpszString*  
 [Ausgabe] Zeiger auf den Datenpuffer, der die Zeichenfolge enthält, die dem zu lesenden Schlüssel zugeordnet ist.  
  
 Wenn * \*lpszFileName* ein gültiger .dsn-Dateiname ist, das *Argument lpszAppName* jedoch ein Nullzeiger ist und das Argument *lpszKeyName* ein Nullzeiger ist, enthält * \*lpszString* eine Liste gültiger Anwendungen. Wenn * \*lpszFileName* ein gültiger .dsn-Dateiname ist und * \*lpszAppName* ein gültiger Anwendungsname ist, das *Argument lpszKeyName* jedoch ein Nullzeiger ist, enthält * \*lpszString* eine Liste gültiger reservierter Schlüsselwörter im entsprechenden Abschnitt der DSN-Datei, die durch Semikolons getrennt ist. Wenn * \*lpszFileName* ein gültiger .dsn-Dateiname ist, * \*aber lpszAppName* ein Nullzeiger ist und das *Argument lpszKeyName* ein Nullzeiger ist, enthält * \*lpszString* eine Liste der Abschnitte in der DSN-Datei, die durch Semikolons getrennt ist.  
  
 *cbString*  
 [Eingabe] Länge des * \*lpszString-Puffers.*  
  
 *pcbString*  
 [Ausgabe] Gesamtanzahl der bytes, die in * \*lpszString*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbString*ist, wird die Ausgabezeichenfolge in * \*lpszString* auf *cbString* abzüglich des Null-Beendigungszeichens abgeschnitten. Das *argumentpcbString* kann ein Nullzeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLReadFileDSN** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallerError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge|Das *Argument lpszString* war NULL.<br /><br /> Das *argument cbString* war kleiner oder gleich 0.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad|Der Pfad des im Argument *lpszFileName* angegebenen Dateinamens war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das *Argument lpszAppName* war NULL, während das Argument *lpszKeyName* gültig war.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund eines Speichermangels nicht ausführen.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Ausgabezeichenfolge abgeschnitten|Die in * \*lpszString* zurückgegebene Zeichenfolge wurde abgeschnitten, da der Wert in *cbString* kleiner oder gleich dem Wert in * \*pcbString*war.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Das Schlüsselwort war in der Datei DSN nicht vorhanden.|  
  
## <a name="comments"></a>Kommentare  
 ODBC reserviert den Abschnittsnamen [ODBC], in dem die Verbindungsinformationen gespeichert werden sollen. Die reservierten Schlüsselwörter für diesen Abschnitt entsprechen denen, die für eine Verbindungszeichenfolge in **SQLDriverConnect**reserviert sind. (Weitere Informationen finden Sie in der [SQLDriverConnect-Funktionsbeschreibung.)](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Anwendungen können diese reservierten Schlüsselwörter verwenden, um die Informationen in einem Datei-DSN zu lesen. Wenn eine Anwendung die DSN-lose Verbindungszeichenfolge ermitteln möchte, die einem Datei-DSN zugeordnet ist, kann sie **SQLReadFileDSN** für alle reservierten Verbindungszeichenfolgenschlüsselwörter im Abschnitt [ODBC] aufrufen. Die vollständige Verbindungszeichenfolge, die in einer DSN-losen Verbindung übergeben wird, ist eine Kombination aller Schlüsselwörter (reserviert und treiberspezifisch) im Abschnitt [ODBC].  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Schreiben von Informationen in ein Datei-DSN|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
