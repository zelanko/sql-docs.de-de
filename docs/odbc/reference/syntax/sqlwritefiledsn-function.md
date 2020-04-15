---
title: SQLWriteFileDSN-Funktion | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e781f1be79e0079f33b3d0800c665f5f5e9fda4d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286890"
---
# <a name="sqlwritefiledsn-function"></a>SQLWriteFileDSN-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLWriteFileDSN** schreibt Informationen in eine Datei-DSN.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Argumente  
 *lpszFileName*  
 [Eingabe] Zeiger auf den Namen des Datei-DSN. Eine DSN-Erweiterung wird an alle Dateinamen angehängt, die noch nicht über eine DSN-Erweiterung verfügen.  
  
 *lpszAppName*  
 [Eingabe] Zeiger auf den Namen der Anwendung. Dies ist "ODBC" für den ODBC-Abschnitt.  
  
 *lpszKeyName*  
 [Eingabe] Zeigen Sie auf den Namen des zu lesenden Schlüssels. Siehe "Kommentare" für reservierte Keywords.  
  
 *lpszString*  
 [Ausgabe] Auf die Zeichenfolge verwiesen, die dem zu schreibenden Schlüssel zugeordnet ist. Die maximale Länge der Zeichenfolge, auf die dieses Argument zeigt, beträgt 32.767 Bytes.  
  
## <a name="returns"></a>Rückgabe  
 Die Funktion gibt TRUE zurück, wenn sie erfolgreich ist, FALSE, wenn sie fehlschlägt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLWriteFileDSN** FALSE zurückgibt, kann ein zugeordneter * \*pfErrorCode-Wert* abgerufen werden, indem **SQLInstallError**aufgerufen wird. In der folgenden Tabelle sind die * \*pfErrorCode-Werte* aufgeführt, die von **SQLInstallerError** zurückgegeben werden können, und es werden die einzelnen Werte im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeiner Installationsfehler|Es ist ein Fehler aufgetreten, für den kein spezifischer Installationsfehler aufgetreten ist.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger Installationspfad|Der Pfad des im Argument *lpszFileName* angegebenen Dateinamens war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Anforderungstyp|Das Argument *lpszAppName*, *lpszKeyName*oder *lpszString* war NULL.|  
  
## <a name="comments"></a>Kommentare  
 ODBC reserviert den Abschnittsnamen [ODBC], in dem die Verbindungsinformationen gespeichert werden sollen. Die reservierten Schlüsselwörter für diesen Abschnitt entsprechen denen, die für eine Verbindungszeichenfolge in **SQLDriverConnect**reserviert sind. (Weitere Informationen finden Sie in der [SQLDriverConnect-Funktionsbeschreibung.)](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Anwendungen können diese reservierten Schlüsselwörter verwenden, um Informationen direkt in ein Datei-DSN zu schreiben. Wenn eine Anwendung die DSN-lose Verbindungszeichenfolge erstellen oder ändern möchte, die einem Datei-DSN zugeordnet ist, kann sie **SQLWriteFileDSN** für alle reservierten Verbindungszeichenfolgenschlüsselwörter im Abschnitt [ODBC] aufrufen.  
  
 Wenn das *Argument lpszString* ein Nullzeiger ist, wird das Schlüsselwort, auf das das Argument *lpszKeyName* zeigt, aus der .dsn-Datei gelöscht. Wenn die Argumente *lpszString* und *lpszKeyName* beide NULL-Zeiger sind, wird der Abschnitt, auf den das Argument *lpszAppName* zeigt, aus der .dsn-Datei gelöscht.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen über|Finden Sie unter|  
|---------------------------|---------|  
|Lesen von Informationen aus Datei-DSNs|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
