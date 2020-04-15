---
title: SQLInstallerError-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallerError
helpviewer_keywords:
- SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e749237cf87c5054b8273f38531d9336d316e040
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302101"
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.0  
  
 **Zusammenfassung**  
 **SQLInstallerError** gibt Fehler- oder Statusinformationen für die ODBC-Installationsfunktionen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Argumente  
 *iError*  
 [Eingabe] Fehlerdatensatznummer. Gültige Zahlen sind von 1 bis 8.  
  
 *pfErrorCode*  
 [Ausgabe] Installer-Fehlercode. (Weitere Informationen finden Sie unter "Kommentare.")  
  
 *lpszErrorMsg*  
 [Ausgabe] Zeiger auf den Speicher für den Fehlermeldungstext.  
  
 *cbErrorMsgMax*  
 [Eingabe] Maximale Länge des *szErrorMsg-Puffers.* Dies muss kleiner oder gleich SQL_MAX_MESSAGE_LENGTH abzüglich des Null-Beendigungszeichens sein.  
  
 *cbErrorMsgMax*  
 [Eingabe] Maximale Länge des *szErrorMsg-Puffers.* Dies muss kleiner oder gleich SQL_MAX_MESSAGE_LENGTH abzüglich des Null-Beendigungszeichens sein.  
  
 *pcbErrorMsg*  
 [Ausgabe] Zeiger auf die Gesamtzahl der Bytes (mit Ausnahme des Null-Beendigungszeichens), die in *lpszErrorMsg*zurückgegeben werden können. Wenn die Anzahl der zurückzugebenden Bytes größer oder gleich *cbErrorMsgMax*ist, wird der Fehlermeldungstext in *lpszErrorMsg* auf *cbErrorMsgMax* abzüglich der Null-Beendigungszeichenbytes abgeschnitten. Das Argument *pcbErrorMsg* kann ein Nullzeiger sein.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA oder SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLInstallerError** gibt keine Fehlerwerte für sich selbst. **SQLInstallerError** gibt SQL_NO_DATA zurück, wenn keine Fehlerinformationen abgerufen werden können (in diesem Fall ist *pfErrorCode* nicht definiert). Wenn **SQLInstallerError** aus irgendeinem Grund, der normalerweise SQL_ERROR zurückgeben würde, nicht auf Fehlerwerte zugreifen kann, gibt **SQLInstallerError** SQL_ERROR, gibt jedoch keine Fehlerwerte zurück. Wenn Sie die Länge der Warnzeichenfolge (*lpszErrorMsg*) nicht kennen, können Sie *lpszErrorMsg* auf NULL setzen und **SQLInstallerError**aufrufen. **SQLInstallerError** gibt dann die Länge der Warnungszeichenfolge in *cbErrorMsgMax*zurück. Wenn der Puffer für die Fehlermeldung zu kurz ist, gibt **SQLInstallerError** SQL_SUCCESS_WITH_INFO und den richtigen *pfErrorCode-Wert* für **SQLInstallerError**zurück.  
  
 Um zu bestimmen, ob eine Kürzung in der Fehlermeldung aufgetreten ist, kann eine Anwendung den Wert im Argument *cbErrorMsgMax* mit der tatsächlichen Länge des in das Argument *pcbErrorMsg* geschriebenen Nachrichtentexts vergleichen. Wenn eine Abschneide erfolgt, sollte die richtige Pufferlänge für *lpszErrorMsg* zugewiesen werden, und **SQLInstallerError** sollte mit dem entsprechenden *iError-Datensatz* erneut aufgerufen werden.  
  
## <a name="comments"></a>Kommentare  
 Eine Anwendung ruft **SQLInstallerError** auf, wenn ein vorheriger Aufruf der ODBC-Installationsfunktion FALSE zurückgibt. ODBC Installer und Treiber- oder Übersetzer-Setup-Funktionen nach Null oder mehr Fehler nur, wenn die Funktion fehlschlägt (gibt FALSE zurück); Daher ruft eine Anwendung **SQLInstallerError** erst auf, nachdem eine ODBC-Installationsfunktion fehlschlägt.  
  
 Die ODBC-Installationsfehlerwarteschlange wird jedes Mal geleert, wenn eine neue Installationsfunktion aufgerufen wird. Daher kann eine Anwendung nicht erwarten, Fehler für andere Funktionen als vom letzten Installationsfunktionsaufruf abzurufen.  
  
 Um mehrere Fehler für einen Funktionsaufruf abzurufen, ruft eine Anwendung **SQLInstallerError** mehrmals auf.  
  
 Wenn keine zusätzlichen Informationen vorhanden sind, gibt **SQLInstallerError** SQL_NO_DATA zurück, das *argument pfErrorCode* ist nicht definiert, das *Argument pcbErrorMsg* gleich 0 und das Argument *lpszErrorMsg* enthält ein einzelnes NULL-Beendigungszeichen (es sei denn, das Argument *cbErrorMsgMax* ist gleich 0).
