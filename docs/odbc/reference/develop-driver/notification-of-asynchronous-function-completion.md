---
title: Benachrichtigung über den Abschluss der asynchronen Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a453967f2ffdda4af2a44429737f700f4a994cf8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287820"
---
# <a name="notification-of-asynchronous-function-completion"></a>Benachrichtigung der Asynchronen Funktionsvollendung
Im Windows 8 SDK hat ODBC einen Mechanismus zum Benachrichtigen von Anwendungen hinzugefügt, wenn ein asynchroner Vorgang abgeschlossen ist, den wir als "Benachrichtigung nach Abschluss" bezeichnen. (Weitere Informationen finden Sie unter [Asynchrone Ausführung (Benachrichtigungsmethode).)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) In diesem Thema werden einige der Probleme für Treiberentwickler behandelt.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>Die Schnittstelle zwischen Treiber-Manager und Treiber  
 Der Treiber-Manager stellt intern eine Rückruffunktion [SQLAsyncNotificationCallback Function](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md)bereit. **SQLAsyncNotificationCallback** kann nur vom Treiber aufgerufen werden – eine Anwendung kann es nicht direkt aufrufen. Der Treiber ruft **SQLAsyncNotificationCallback auf,** wenn neue Daten, die vom Server nach der letzten Rückgabe SQL_STILL_EXECUTING empfangen wurden.  
  
 Der Treiber-Manager stellt einen Rückrufmechanismus bereit, damit ein Treiber den Treiber-Manager benachrichtigen kann, wenn bei der Ausführung eines asynchronen Vorgangs Einfluß erzielt wurde, nachdem die entsprechende Funktion SQL_STILL_EXECUTING  
  
 Der Treiber-Manager legt das SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK-Attribut für ein Treiberverbindungshandle mit einem Nicht-NULL-Funktionszeiger vom Typ SQL_ASYNC_NOTIFICATION_CALLBACK fest, damit der Treiber im Benachrichtigungsmodus für alle asynchronen Vorgänge in diesem Handle arbeitet. In ähnlicher Weise legt der Treiber-Manager das SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK-Attribut für ein Treiberanweisungshandle mit einem Nicht-NULL-Funktionszeiger fest, der ebenfalls vom Typ SQL_ASYNC_NOTIFICATION_CALLBACK ist, damit der Treiber im Benachrichtigungsmodus für alle asynchronen Vorgänge in diesem Handle arbeitet.  
  
 Wenn ein asynchroner Vorgang für ein Treiberhandle ausgeführt wird, sollten die asynchronen Treiberfunktionen in einem nicht blockierenden Stil funktionieren. Wenn der Vorgang nicht sofort abgeschlossen werden kann, sollte die Treiberfunktion SQL_STILL_EXECUTING zurückgeben. Diese Anforderung gilt sowohl für den Abrufmodus als auch für den Benachrichtigungsmodus.  
  
 Wenn sich ein Handle im asynchronen Benachrichtigungsmodus befindet, muss der Treiber die Benachrichtigungsrückruffunktion, deren Adresse der Wert für das attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK ist, einmal nach der Rückgabe SQL_STILL_EXECUTING aufrufen. Mit anderen Worten, ein SQL_STILL_EXECUTING muss mit einem Aufruf der Benachrichtigungsrückruffunktion gekoppelt werden. Der Treiber sollte den aktuellen Wert des attributs SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT handle als Wert für den Rückruffunktionsparameter *pContext*verwenden.  
  
 Der Treiber darf nicht im Thread zurückrufen, der die Treiberfunktion aufruft. Es gibt keinen Grund, den Fortschritt zu benachrichtigen, bevor die Funktion zurückgegeben wird. Der Treiber sollte einen eigenen Thread zum Rückruf verwenden. Der Treiber-Manager verwendet den Rückrufthread des Treibers nicht für die Ausführung umfangreicher Verarbeitungslogik.  
  
 Der Treiber-Manager ruft die ursprüngliche Funktion erneut auf, nachdem der Treiber zurückruft. Der Treiber-Manager kann einen Thread verwenden, der weder ein Anwendungsthread noch ein Treiberthread ist. Wenn der Treiber einige Informationen verwendet, die dem Thread zugeordnet sind (z. B. Sicherheitstoken oder Benutzerbezeichner), sollte der Treiber die erforderlichen Informationen im ursprünglichen asynchronen Aufruf speichern und den gespeicherten Wert verwenden, bevor der gesamte asynchrone Vorgang abgeschlossen ist. Normalerweise müssen nur **SQLDriverConnect**, **SQLConnect**oder **SQLBrowseConnect** diese Art von Informationen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
