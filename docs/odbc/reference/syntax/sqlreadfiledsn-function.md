---
title: SQLReadFileDSN-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f32e23be700f17fee88cc6354f8652bb1333a12c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537347"
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLReadFileDSN** liest Informationen aus einer Datei-DSN.  
  
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
 [Eingabe] Zeiger auf den Datenpuffer, der mit dem Namen der Datei ".DSN". Eine Erweiterung ".DSN" wird an alle Dateinamen angefügt, die noch nicht über eine Erweiterung ".DSN" verfügen. Der Wert in  *\*LpszFileName* muss eine Null-terminierte Zeichenfolge sein.  
  
 *lpszAppName*  
 [Eingabe] Zeiger auf den Datenpuffer, der mit dem Namen der Anwendung. Dies ist "ODBC" für den ODBC-Abschnitt. Der Wert in  *\*LpszAppName* muss eine Null-terminierte Zeichenfolge sein.  
  
 *lpszKeyName*  
 [Eingabe] Zeiger auf den Datenpuffer, der mit dem Namen des Schlüssels, der gelesen werden. Reservierte Schlüsselwörter finden Sie unter "Kommentare". Der Wert in  *\*LpszAppName* muss eine Null-terminierte Zeichenfolge sein.  
  
 *lpszString*  
 [Ausgabe] Zeiger auf den Datenpuffer mit der Zeichenfolge, die dem Schlüssel, die gelesen werden.  
  
 Wenn  *\*LpszFileName* ist ein Dateiname gültig ".DSN" aber die *LpszAppName* Argument ist ein null-Zeiger und die *LpszKeyName* Argument ist ein null-Zeiger  *\*LpszString* enthält eine Liste der gültigen Anwendungen. Wenn  *\*LpszFileName* ist ein Dateiname gültig ".DSN" und  *\*LpszAppName* ist ein gültiger Anwendungsname angegeben wird, aber die *LpszKeyName* Argument ist ein NULL-Wert -Zeiger ist, klicken Sie dann  *\*LpszString* enthält eine Liste der gültigen reservierten Schlüsselwörter in den entsprechenden Abschnitt der DSN-Datei, die durch ein Semikolon getrennt. Wenn  *\*LpszFileName* ist ein Dateiname gültig ".DSN" aber  *\*LpszAppName* ist ein null-Zeiger und die *LpszKeyName* Argument ist ein null-Zeiger Klicken Sie dann  *\*LpszString* enthält eine Liste der Abschnitte in der DSN-Datei durch ein Semikolon getrennt.  
  
 *cbString*  
 [Eingabe] Länge der  *\*LpszString* Puffer.  
  
 *pcbString*  
 [Ausgabe] Gesamtzahl der Bytes, die für die Rückgabe in verfügbar  *\*LpszString*. Wenn die Anzahl der Bytes, die für die Rückgabe verfügbar, größer als oder gleich ist *CbString*, die Ausgabezeichenfolge in  *\*LpszString* auf abgeschnitten *CbString* minus das Zeichen Null-Terminierung vorliegt. Die *PcbString* Argument kann ein null-Zeiger sein.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLReadFileDSN** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Beschreibung|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Ungültige Pufferlänge.|Die *LpszString* -Argument war NULL.<br /><br /> Die *CbString* Argument war kleiner als oder gleich 0.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger-Installationspfad|Der Pfad der Datei angegeben, der *LpszFileName* Argument war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *LpszAppName* -Argument war NULL, während die *LpszKeyName* Argument war ungültig.|  
|ODBC_ERROR_OUT_OF_MEM|Nicht genügend Arbeitsspeicher.|Das Installationsprogramm konnte die Funktion aufgrund von unzureichendem Speicher nicht ausgeführt werden.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Die Ausgabezeichenfolge abgeschnitten|Die Zeichenfolge, die in zurückgegebenen  *\*LpszString* wurde abgeschnitten, da der Wert in *CbString* war kleiner als oder gleich dem Wert in  *\*PcbString*.|  
|ODBC_ERROR_REQUEST_FAILED|Fehler bei der Anforderung|Das Schlüsselwort war in der DSN-Datei nicht vorhanden.|  
  
## <a name="comments"></a>Kommentare  
 ODBC reserviert den Namen des Abschnitts [ODBC], in dem Sie die Verbindungsinformationen zu speichern. Die reservierten Schlüsselwörter in diesem Abschnitt sind identisch mit dieser für eine Verbindungszeichenfolge in reserviert **SQLDriverConnect**. (Weitere Informationen finden Sie unter den [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) funktionsbeschreibung.)  
  
 Anwendungen können diese reservierten Schlüsselwörter verwenden, um die Informationen in einem DSN-Datei lesen zu können. Wenn eine Anwendung finden Sie die DSN-lose Verbindungszeichenfolge zugeordneten einen Datei-DSN aufrufen möchte **SQLReadFileDSN** für keines der reservierten Schlüsselwörter für Verbindungszeichenfolgen im Abschnitt [ODBC]. Die komplette Verbindungszeichenfolge übergeben, die in einer DSN-lose Verbindung ist eine Kombination der Schlüsselwörter (reservierte und treiberspezifische) im Abschnitt [ODBC].  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Schreiben von Informationen in einen Datei-DSN|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|
