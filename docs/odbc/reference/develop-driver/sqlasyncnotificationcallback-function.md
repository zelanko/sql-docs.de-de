---
description: SQLAsyncNotificationCallback-Funktion
title: Sqlasyncnotificationcallback-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: b9d03e8a3fa7e62c19dd09a210dca3a56348c692
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476229"
---
# <a name="sqlasyncnotificationcallback-function"></a>SQLAsyncNotificationCallback-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 3,8  
  
 Einhaltung von Standards: keine  
  
 **Zusammenfassung**  
 **Sqlasyncnotificationcallback** ermöglicht einem Treiber, einen Rückruf an den Treiber-Manager auszuführen, wenn der Fortschritt für den aktuellen asynchronen Vorgang fortgesetzt wird, nachdem der Treiber SQL_STILL_EXECUTING zurückgegeben hat. **Sqlasyncnotificationcallback** kann nur vom Treiber aufgerufen werden.  
  
 Treiber rufen **sqlasyncnotificationcallback** nicht mit dem Funktionsnamen **sqlasyncnotificationcallback**auf. Stattdessen übergibt der Treiber-Manager einen Funktionszeiger an einen Treiber als Wert für die SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK Attribut des entsprechenden Verbindungs Handles bzw. Anweisungs Handles. Unterschiedlichen Handles können unterschiedliche Funktionszeiger Werte zugewiesen werden. Der Typ des Funktions Zeigers ist als SQL_ASYNC_NOTIFICATION_CALLBACK definiert.  
  
 **Sqlasyncnotificationcallback** ist Thread sicher. Ein Treiber kann mehrere Threads verwenden, die **sqlasyncnotificationcallback** gleichzeitig für verschiedene Handles aufrufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef SQLRETURN (SQL_API *SQL_ASYNC_NOTIFICATION_CALLBACK)(  
   SQLPOINTER pContex,   
   BOOL fLast);  
```  
  
## <a name="arguments"></a>Argumente  
 *pConfig*  
 Zeiger auf eine vom Treiber-Manager definierte Datenstruktur. Der Wert wird über SQLSetConnectAttr (SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT) oder SQLSetStmtAttr (SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT) an den Treiber übermittelt.  Der Treiber hat keinen Zugriff auf den Wert.  
  
 *nicht zuletzt*  
 Wird von einem Treiber verwendet, um darauf hinzudeuten, dass dieser Rückruf Funktionsaufruf der letzte für den aktuellen asynchronen Vorgang ist. Der Treiber gibt einen anderen Rückgabecode als SQL_STILL_EXECUTING zurück, wenn der Treiber-Manager die Funktion erneut aufruft. Der Treiber-Manager kann diese Informationen z. b. verwenden, um die Anwendung darüber zu informieren, dass der asynchrone Vorgang beendet wird.  
  
 Wenn *handle* kein gültiges Handle des Typs ist, der von " *Lenker*" angegeben wird, gibt **sqlcancelhandle** SQL_INVALID_HANDLE zurück.  
  
## <a name="returns"></a>Rückgabe  
 SQL_SUCCESS oder SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnose  
 **Sqlasyncnotificationcallback** kann in den folgenden zwei Fällen SQL_ERROR zurückgeben (Dies deutet auf ein Implementierungs Problem im Treiber-oder Treiber-Manager hin.  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|Die Verbindung oder Anweisung hat keine Benachrichtigung angefordert.||  
|Ungültiges *handle*|Der Treiber hat ein ungültiges Handle bestanden, bei dem die internen Treiber-Manager-Validierungstests fehlgeschlagen sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Asynchrone Ausführung (Abruf Methode)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
