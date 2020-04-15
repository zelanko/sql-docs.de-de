---
title: SQLAsyncNotificationCallback-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6c182c48b8e5ddb70204ddd3a94d9651f97595d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294537"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback-Funktion
**Konformität**  
 Eingeführte Version: ODBC 3.8  
  
 Einhaltung der Standards: Keine  
  
 **Zusammenfassung**  
 **SQLAsyncNotificationCallback** ermöglicht es einem Treiber, den Treiber-Manager zurückzurufen, wenn es einen Fortschritt für den aktuellen asynchronen Vorgang gibt, nachdem der Treiber SQL_STILL_EXECUTING zurückgegeben hat. **SQLAsyncNotificationCallback** kann nur vom Treiber aufgerufen werden.  
  
 Treiber rufen **SQLAsyncNotificationCallback** nicht mit dem Funktionsnamen **SQLAsyncNotificationCallback**auf. Stattdessen übergibt der Treiber-Manager einen Funktionszeiger an einen Treiber als Wert für die SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK bzw. SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK Attribut des entsprechenden Verbindungshandles bzw. Anweisungshandles. Verschiedenen Handles können unterschiedliche Funktionszeigerwerte zugewiesen werden. Der Typ des Funktionszeigers wird als SQL_ASYNC_NOTIFICATION_CALLBACK definiert.  
  
 **SQLAsyncNotificationCallback** ist threadsicher. Ein Treiber kann mehrere Threads verwenden, die **SQLAsyncNotificationCallback** gleichzeitig für verschiedene Handles aufrufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Argumente  
 *pContex*  
 Zeiger auf eine vom Treiber-Manager definierte Datenstruktur. Der Wert wird über SQLSetConnectAttr(SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) oder SQLSetStmtAttr(SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT) an den Treiber übergeben.  Der Treiber hat keinen Zugriff auf den Wert.  
  
 *fLast*  
 Wird von einem Treiber verwendet, um anzuzeigen, dass dieser Rückruffunktion-Aufruf der letzte für den aktuellen asynchronen Vorgang ist. Der Treiber gibt einen anderen Rückgabecode als SQL_STILL_EXECUTING zurück, wenn der Treiber-Manager die Funktion erneut aufruft. Der Treiber-Manager kann diese Informationen verwenden, um die Anwendung beispielsweise im Voraus darüber zu informieren, dass der asynchrone Vorgang abgeschlossen wird.  
  
 Wenn *Handle* kein gültiges Handle des von *HandleType*angegebenen Typs ist, gibt **SQLCancelHandle** SQL_INVALID_HANDLE zurück.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS oder SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLAsyncNotificationCallback** kann SQL_ERROR für die folgenden beiden Situationen zurückgeben (diese weisen auf ein Implementierungsproblem im Treiber oder Treiber-Manager hin.  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|Die Verbindung oder Anweisung hat keine Benachrichtigung anfordern.||  
|Ungültiges *Handle*|Der Treiber hat ein ungültiges Handle übergeben, wodurch die internen Treiber-Manager-Validierungstests fehlgeschlagen sind.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
