---
title: SQLWriteFileDSN-Funktion | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 58002ec0e8ceacae49f4d54be5d3406ea3014d59
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536779"
---
# <a name="sqlwritefiledsn-function"></a>SQLWriteFileDSN-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLWriteFileDSN** schreibt Informationen in einen Datei-DSN.  
  
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
 [Eingabe] Zeiger auf den Namen der Datei-DSN. Eine DSN-Erweiterung wird an alle Dateinamen angefügt, die noch nicht über eine DSN-Erweiterung verfügen.  
  
 *lpszAppName*  
 [Eingabe] Zeiger auf den Namen der Anwendung. Dies ist "ODBC" für den ODBC-Abschnitt.  
  
 *lpszKeyName*  
 [Eingabe] Zeiger auf den Namen des Schlüssels, der gelesen werden. Reservierte Schlüsselwörter finden Sie unter "Kommentare".  
  
 *lpszString*  
 [Ausgabe] Verweist auf die Zeichenfolge, die dem Schlüssel, geschrieben werden soll. Die maximale Länge der Zeichenfolge verweist dieses Argument ist 32.767 Bytes.  
  
## <a name="returns"></a>Rückgabewert  
 Die Funktion gibt "true" bei Erfolg, FALSE, wenn ein Fehler auftritt.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLWriteFileDSN** gibt "false", ein zugeordnetes  *\*PfErrorCode* Wert abgerufen werden kann, durch den Aufruf **SQLInstallerError**. Die folgende Tabelle enthält die  *\*PfErrorCode* Werte, die zurückgegeben werden können **SQLInstallerError** und jeweils im Kontext dieser Funktion erläutert.  
  
|*\*pfErrorCode*|Fehler|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Allgemeine Installer-Fehler|Fehler für die gab es keine bestimmte Installer-Fehlers.|  
|ODBC_ERROR_INVALID_PATH|Ungültiger-Installationspfad|Der Pfad der Datei angegeben, der *LpszFileName* Argument war ungültig.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Ungültiger Typ der Anforderung|Die *LpszAppName*, *LpszKeyName*, oder *LpszString* -Argument war NULL.|  
  
## <a name="comments"></a>Kommentare  
 ODBC reserviert den Namen des Abschnitts [ODBC], in dem Sie die Verbindungsinformationen zu speichern. Die reservierten Schlüsselwörter in diesem Abschnitt sind identisch mit dieser für eine Verbindungszeichenfolge in reserviert **SQLDriverConnect**. (Weitere Informationen finden Sie unter den [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) funktionsbeschreibung.)  
  
 Anwendungen können diese reservierten Schlüsselwörter verwenden, um Informationen direkt in einen Datei-DSN schreiben. Wenn eine Anwendung Daten zum Erstellen oder ändern die DSN-lose Verbindung-Zeichenfolge, die einen Datei-DSN zugeordnet wird, können sie aufrufen **SQLWriteFileDSN** für keines der reservierten Schlüsselwörter für Verbindungszeichenfolgen im Abschnitt [ODBC].  
  
 Wenn die *LpszString* Argument ist ein null-Zeiger ist das Schlüsselwort verweist die *LpszKeyName* Argument die DSN-Datei gelöscht wird. Wenn die *LpszString* und *LpszKeyName* Argumente sind null-Zeiger, Abschnitt verweist die *LpszAppName* Argument die DSN-Datei gelöscht wird.  
  
## <a name="related-functions"></a>Verwandte Funktionen  
  
|Informationen zu|Finden Sie unter|  
|---------------------------|---------|  
|Lesen von Informationen aus der Datei-DSNs|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|
