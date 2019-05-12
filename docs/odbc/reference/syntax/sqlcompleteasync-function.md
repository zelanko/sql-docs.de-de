---
title: SQLCompleteAsync-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 736867be33531a73c0ada66a3be0f1245f1c483a
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537600"
---
# <a name="sqlcompleteasync-function"></a>SQLCompleteAsync-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.8  
  
 Einhaltung von Standards: None  
  
 **Zusammenfassung**  
 **SQLCompleteAsync** können verwendet werden, um zu ermitteln, wann eine asynchrone Funktion mithilfe von entweder oder Abruf-benachrichtigungsbasierte Verarbeitung abgeschlossen ist. Weitere Informationen zu asynchronen Vorgängen finden Sie unter [asynchrone Ausführung](../../../odbc/reference/develop-app/asynchronous-execution.md).  
  
 **SQLCompleteAsync** wird nur in der ODBC-Treiber-Manager implementiert.  
  
 Im Modus für asynchrone Verarbeitung der Benachrichtigung basierend **SQLCompleteAsync** muss aufgerufen werden, nachdem der Treiber-Manager löst aus, das Ereignisobjekt für Benachrichtigungen verwendet. **SQLCompleteAsync** schließt den asynchronen Verarbeitung und die asynchrone Funktion generiert einen Rückgabecode.  
  
 Im Modus für asynchrone Verarbeitung abrufen, die Grundlage **SQLCompleteAsync** ist eine Alternative zu die ursprüngliche asynchrone Funktion, ohne dass die Argumente in den ursprünglichen Aufruf der asynchronen Funktion aufrufen. **SQLCompleteAsync** kann verwendet werden, unabhängig davon, ob die ODBC-Cursorbibliothek aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
  
SQLRETURN SQLCompleteAsync(  
      SQLSMALLINT HandleType,  
      SQLHANDLE   Handle,  
      RETCODE *   AsyncRetCodePtr);  
```  
  
## <a name="arguments"></a>Argumente  
 *HandleType*  
 [Eingabe] Der Typ des Handles für die asynchronen Abschluss verarbeiten zu können. Gültige Werte sind SQL_HANDLE_DBC auf oder SQL_HANDLE_STMT auf.  
  
 *Handle*  
 [Eingabe] Das Handle für die asynchronen Abschluss verarbeiten zu können. Wenn *behandeln* ist kein gültiges Handle des Typs vom angegebenen *HandleType*, **SQLCompleteAsync** SQL_INVALID_HANDLE gibt.  
  
 Wenn *behandeln* ist kein gültiges Handle des Typs vom angegebenen *HandleType*, **SQLCompleteAsync** SQL_INVALID_HANDLE gibt.  
  
 *AsyncRetCodePtr*  
 [Ausgabe] Zeiger auf einen Puffer, der den Rückgabecode der asynchronen API enthält. Wenn *AsyncRetCodePtr* NULL ist, **SQLCompleteAsync** gibt SQL_ERROR zurück.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS SQL_ERROR, SQL_NO_DATA zurückgibt oder SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnose  
 Wenn **SQLCompleteAsync** gibt SQL_SUCCESS zurück, die eine Anwendung sollte den Rückgabecode der asynchronen Funktion abzurufen, aus dem Puffer, der auf *AsyncRetCodePtr*. Zugeordnete SQLSTATE, sofern vorhanden, erhalten Sie durch Aufrufen **SQLGetDiagRec** mit einem *HandleType* von SQL_HANDLE_STMT auf, und ein Anweisungshandle oder ein *HandleType* von SQL_ HANDLE_DBC und eine Verbindung behandeln. Diese DiagnoseDatensätze sind die asynchrone Funktion, falsch zugeordnet **SQLCompleteAsync** Funktion.  
  
 **SQLCompleteAsync** gibt einen Code als SQL_SUCCESS an, dass **SQLCompleteAsync** ist nicht richtig aufgerufen. **SQLCompleteAsync** jedem Diagnosedatensatz nicht in diesem Fall gesendet. Mögliche Rückgabecodes sind:  
  
-   SQL_INVALID_HANDLE: Das Handle angegeben wird, indem *HandleType* und *behandeln* ist kein gültiges Handle.  
  
-   SQL_ERROR: *AsyncRetCodePtr* NULL ist oder die asynchrone Verarbeitung auf das Handle nicht aktiviert ist.  
  
-   SQL_NO_DATA: In den Benachrichtigungsmodus ein asynchroner Vorgang wird nicht ausgeführt, oder der Treiber-Manager hat die Anwendung nicht benachrichtigt. Im Modus "Abfrage" ist ein asynchroner Vorgang nicht ausgeführt.  
  
## <a name="comments"></a>Kommentare  
 Im Modus für asynchrone Verarbeitung abrufen, die Grundlage *AsyncRetCodePtr* SQL_STILL_EXECUTING möglicherweise beim **SQLCompleteAsync** gibt SQL_SUCCESS zurück. Anwendung sollte bis zum Abruf behalten *AsyncRetCodePtr* ist kein SQL_STILL_EXECUTING. Im Modus für asynchrone Verarbeitung der Benachrichtigung basierend *AsyncRetCodePtr* werden nie SQL_STILL_EXECUTING.  
  
## <a name="see-also"></a>Siehe auch  
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
