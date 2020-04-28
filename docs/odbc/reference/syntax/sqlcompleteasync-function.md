---
title: Sqlcompleteasync-Funktion | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299655"
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,8  
  
 Einhaltung von Standards: keine  
  
 **Zusammenfassung**  
 **Sqlcompleteasync** kann verwendet werden, um zu bestimmen, wann eine asynchrone Funktion mithilfe der Benachrichtigungs-oder Abruf basierten Verarbeitung abgeschlossen wurde. Weitere Informationen zu asynchronen Vorgängen finden Sie unter [asynchrone Ausführung](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **Sqlcompleteasync** ist nur im ODBC-Treiber-Manager implementiert.  
  
 Im Benachrichtigungs basierten asynchronen Verarbeitungsmodus muss **sqlcompleteasync** aufgerufen werden, nachdem der Treiber-Manager das Ereignis Objekt ausgelöst hat, das für die Benachrichtigung verwendet wird. **Sqlcompleteasync** schließt die asynchrone Verarbeitung ab, und die asynchrone Funktion generiert einen Rückgabecode.  
  
 Im Abruf basierten asynchronen Verarbeitungsmodus stellt **sqlcompleteasync** eine Alternative zum Aufrufen der ursprünglichen asynchronen Funktion dar, ohne dass die Argumente im ursprünglichen asynchronen Funktionsaufruf angegeben werden müssen. **Sqlcompleteasync** kann unabhängig davon verwendet werden, ob die ODBC-Cursor Bibliothek aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 Der Der Typ des Handles, für das die asynchrone Verarbeitung beendet werden soll. Gültige Werte sind SQL_HANDLE_DBC oder SQL_HANDLE_STMT.  
  
 *Handle*  
 Der Das Handle, für das die asynchrone Verarbeitung beendet werden soll. Wenn *handle* kein gültiges Handle des Typs ist, der durch den- *Handlertyp*angegeben wird, gibt **sqlcompleteasync** SQL_INVALID_HANDLE zurück.  
  
 Wenn *handle* kein gültiges Handle des Typs ist, der durch den- *Handlertyp*angegeben wird, gibt **sqlcompleteasync** SQL_INVALID_HANDLE zurück.  
  
 *Asynkretcodeptr*  
 Ausgeben Zeiger auf einen Puffer, der den Rückgabecode der asynchronen API enthält. Wenn *asynkretcodeptr* NULL ist, gibt **sqlcompleteasync** SQL_ERROR zurück.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS, SQL_ERROR, SQL_NO_DATA oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **sqlcompleteasync** SQL_SUCCESS zurückgibt, sollte eine Anwendung den Rückgabecode der asynchronen Funktion aus dem Puffer erhalten, auf den von *asynkretcodeptr*verwiesen wird. Der zugeordnete SQLSTATE kann, sofern vorhanden, durch den Aufruf von **SQLGetDiagRec** mit dem *Handlertyp* SQL_HANDLE_STMT und einem Anweisungs Handle oder einem *Handlertyp* von SQL_HANDLE_DBC und einem Verbindungs Handle abgerufen werden. Diese Diagnosedaten Sätze sind der asynchronen Funktion und nicht dieser **sqlcompleteasync** -Funktion zugeordnet.  
  
 **Sqlcompleteasync** gibt einen anderen Code als SQL_SUCCESS zurück, um anzugeben, dass **sqlcompleteasync** nicht ordnungsgemäß aufgerufen wird. **Sqlcompleteasync** stellt in diesem Fall keinen Diagnosedaten Satz bereit. Folgende Rückgabecodes sind möglich:  
  
-   SQL_INVALID_HANDLE: das Handle, das von " *Lenker Type* " und " *handle* " angegeben wird, ist kein gültiges Handle.  
  
-   SQL_ERROR: " *asynkretcodeptr* " ist NULL, oder die asynchrone Verarbeitung ist für das Handle nicht aktiviert.  
  
-   SQL_NO_DATA: im Benachrichtigungs Modus wird kein asynchroner Vorgang ausgeführt, oder der Treiber-Manager hat die Anwendung nicht benachrichtigt. Im Abruf Modus wird kein asynchroner Vorgang ausgeführt.  
  
## <a name="comments"></a>Kommentare  
 Im Abruf basierten asynchronen Verarbeitungsmodus kann *asynkretcodeptr* SQL_STILL_EXECUTING werden, wenn **sqlcompleteasync** SQL_SUCCESS zurückgibt. Die Anwendung sollte den Abruf fortsetzen, bis *asynkretcodeptr* nicht SQL_STILL_EXECUTING ist. Im Benachrichtigungs basierten asynchronen Verarbeitungsmodus wird *asynkretcodeptr* nie SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
