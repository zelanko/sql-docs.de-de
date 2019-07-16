---
title: SQLAsyncNotificationCallback-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c56aedc9-f7f7-4641-b605-f0f98ed4400c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 96073b8d5e68d10caaff268aae4c5af60554ef76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915542"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC 3.8  
  
 Einhaltung von Standards: None  
  
 **Zusammenfassung**  
 **SQLAsyncNotificationCallback** können Treiber für die zurück an den Treiber-Manager aufrufen, wenn der Fortschritt für den aktuellen asynchronen Vorgang vorhanden ist, nachdem der Treiber SQL_STILL_EXECUTING zurückgibt. **SQLAsyncNotificationCallback** können nur vom Treiber aufgerufen.  
  
 Rufen Sie Treiber nicht **SQLAsyncNotificationCallback** mit Funktionsnamen **SQLAsyncNotificationCallback**. Stattdessen übergibt der Treiber-Manager einen Funktionszeiger auf einen Treiber, als Wert für das Attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK des entsprechenden Verbindungshandle oder Anweisungshandle, bzw. Unterschiedliche Steuerpunkte können andere Funktion Zeigerwerte zugewiesen werden. Der Typ des Funktionszeigers wird als SQL_ASYNC_NOTIFICATION_CALLBACK definiert.  
  
 **SQLAsyncNotificationCallback** ist threadsicher. Treiber können mehrere Threads aufrufen verwenden **SQLAsyncNotificationCallback** auf verschiedenen behandelt gleichzeitig.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Argumente  
 *pContex*  
 Zeiger auf eine Datenstruktur, die vom Treiber-Manager definiert. Der Wert wird an den Treiber über SQLSetConnectAttr(SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) oder SQLSetStmtAttr(SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT) übergeben.  Der Treiber verfügt nicht über die Zugriffsrechte auf den Wert.  
  
 *fLast*  
 Vom Treiber verwendet, gibt an, dass dieser Rückruf Funktionsaufruf das letzte für den aktuellen asynchronen Vorgang ist. Der Treiber gibt einen anderen Rückgabecode als SQL_STILL_EXECUTING zurück, wenn der Treiber-Manager die Funktion erneut aufruft. Der Treiber-Manager können diese Informationen, z. B. verwenden, um die Anwendung im Voraus darüber zu informieren, die der asynchrone Vorgang abgeschlossen wird.  
  
 Wenn *behandeln* ist kein gültiges Handle des Typs vom angegebenen *HandleType*, **SQLCancelHandle** SQL_INVALID_HANDLE gibt.  
  
## <a name="returns"></a>Rückgabewert  
 SQL_SUCCESS oder SQL_ERROR zurück.  
  
## <a name="diagnostics"></a>Diagnose  
 **SQLAsyncNotificationCallback** können SQL_ERROR zurück, für die folgenden beiden Situationen (Diese weisen ein Implementierungsproblem im Treiber oder Treiber-Manager.  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|Verbindung "oder"-Anweisung hat keine Benachrichtigung angefordert werden.||  
|Ungültige *behandeln*|Der Treiber übergeben ein ungültiges Handle, das die interne Validierungstests für den Treiber-Manager ausgeführt wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Asynchrone Ausführung (Abrufmethode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
