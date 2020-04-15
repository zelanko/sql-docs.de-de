---
title: SQLCompleteAsync-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
f1_keywords:
- SQLCompleteAsync
helpviewer_keywords:
- SQLCompleteAsync function [ODBC]
ms.assetid: 1b97c46a-d2e5-4540-8239-9d975e5321c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e09d61ef516e846798dd3af2d07dafa78af4605
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299655"
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.8  
  
 Einhaltung der Standards: Keine  
  
 **Zusammenfassung**  
 **SQLCompleteAsync** kann verwendet werden, um zu bestimmen, wann eine asynchrone Funktion mithilfe einer Benachrichtigungs- oder Polling-basierten Verarbeitung abgeschlossen ist. Weitere Informationen zu asynchronen Vorgängen finden Sie unter [Asynchrone Ausführung](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **SQLCompleteAsync** wird nur im ODBC Driver Manager implementiert.  
  
 Im benachrichtigungsbasierten asynchronen Verarbeitungsmodus muss **SQLCompleteAsync** aufgerufen werden, nachdem der Treiber-Manager das für die Benachrichtigung verwendete Ereignisobjekt auslöst. **SQLCompleteAsync** schließt die asynchrone Verarbeitung ab, und die asynchrone Funktion generiert einen Rückgabecode.  
  
 Im abfragebasierten asynchronen Verarbeitungsmodus ist **SQLCompleteAsync** eine Alternative zum Aufrufen der ursprünglichen asynchronen Funktion, ohne die Argumente im ursprünglichen asynchronen Funktionsaufruf angeben zu müssen. **SQLCompleteAsync** kann unabhängig davon verwendet werden, ob die ODBC-Cursorbibliothek aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles, für das die asynchrone Verarbeitung abgeschlossen werden soll. Gültige Werte werden SQL_HANDLE_DBC oder SQL_HANDLE_STMT.  
  
 *Handle*  
 [Eingabe] Das Handle, für das die asynchrone Verarbeitung abgeschlossen werden soll. Wenn *Handle* kein gültiges Handle des von *HandleType*angegebenen Typs ist, gibt **SQLCompleteAsync** SQL_INVALID_HANDLE zurück.  
  
 Wenn *Handle* kein gültiges Handle des von *HandleType*angegebenen Typs ist, gibt **SQLCompleteAsync** SQL_INVALID_HANDLE zurück.  
  
 *AsyncRetCodePtr*  
 [Ausgabe] Zeiger auf einen Puffer, der den Rückgabecode der asynchronen API enthält. Wenn *AsyncRetCodePtr* NULL ist, gibt **SQLCompleteAsync** SQL_ERROR zurück.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCompleteAsync** SQL_SUCCESS zurückgibt, sollte eine Anwendung den Rückgabecode der asynchronen Funktion aus dem Puffer abrufen, auf den *AsyncRetCodePtr*zeigt. Die zugeordnete SQLSTATE kann ggf. abgerufen werden, indem **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT und einem Anweisungshandle oder einem *HandleType* von SQL_HANDLE_DBC und einem Verbindungshandle aufgerufen wird. Diese Diagnosedatensätze sind der asynchronen Funktion zugeordnet, nicht dieser **SQLCompleteAsync-Funktion.**  
  
 **SQLCompleteAsync** gibt einen anderen Code als SQL_SUCCESS zurück, um anzugeben, dass **SQLCompleteAsync** nicht korrekt aufgerufen wird. **SQLCompleteAsync** gibt in diesem Fall keinen Diagnosedatensatz. Mögliche Rücksendecodes sind:  
  
-   SQL_INVALID_HANDLE: Das von *HandleType* und *Handle* angegebene Handle ist kein gültiges Handle.  
  
-   SQL_ERROR: *AsyncRetCodePtr* ist NULL oder die asynchrone Verarbeitung ist für das Handle nicht aktiviert.  
  
-   SQL_NO_DATA: Im Benachrichtigungsmodus wird kein asynchroner Vorgang ausgeführt, oder der Treiber-Manager hat die Anwendung nicht benachrichtigt. Im Abrufmodus wird kein asynchroner Vorgang ausgeführt.  
  
## <a name="comments"></a>Kommentare  
 Im abfragebasierten asynchronen Verarbeitungsmodus kann *AsyncRetCodePtr* SQL_STILL_EXECUTING sein, wenn **SQLCompleteAsync** SQL_SUCCESS zurückgibt. Die Anwendung sollte die Abfrage so lange beibehalten, bis *AsyncRetCodePtr* nicht SQL_STILL_EXECUTING ist. Im benachrichtigungsbasierten asynchronen Verarbeitungsmodus wird *AsyncRetCodePtr* nie SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
