---
title: Benachrichtigung über den Abschluss der asynchronen Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 336565da-4203-4745-bce2-4f011c08e357
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c54e545bdbd1ae137c24f79c71b53502480cbca9
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52391283"
---
# <a name="notification-of-asynchronous-function-completion"></a>Benachrichtigung der Asynchronen Funktionsvollendung
Das Windows 8 SDK hinzugefügt ODBC einen Mechanismus, um Anwendungen zu benachrichtigen, wenn ein asynchroner Vorgang abgeschlossen die wir als "Benachrichtigung bei Abschluss" bezeichnet werden ist. (Finden Sie unter [asynchrone Ausführung (Benachrichtigungsmethode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) für Weitere Informationen.) Dieses Thema behandelt einige der Probleme für Treiberentwickler.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>Die Schnittstelle zwischen der Treiber-Manager und Treiber  
 Der Treiber-Manager stellt intern eine Rückruffunktion [SQLAsyncNotificationCallback-Funktion](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md). **SQLAsyncNotificationCallback** kann nur aufgerufen werden vom Treiber – eine Anwendung nicht direkt aufrufen es. Der Treiber ruft **SQLAsyncNotificationCallback** jedes Mal, wenn neue Daten vom Server empfangene nach der letzten zurückgegebenen SQL_STILL_EXECUTING.  
  
 Der Treiber-Manager stellt einen Rückrufmechanismus bereit, damit ein Treiber des Treiber-Managers benachrichtigen kann, wenn der Fortschritt in einen asynchronen Vorgang ausführt, nachdem die entsprechende Funktion SQL_STILL_EXECUTING vorgenommen wurde  
  
 Der Treiber-Manager wird das SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK-Attribut für ein Verbindungshandle "Treiber" mit einem Funktionszeiger ungleich NULL-, das vom Typ SQL_ASYNC_NOTIFICATION_CALLBACK, für den Treiber in den Benachrichtigungsmodus für funktionieren alle asynchronen Vorgänge für dieses Handle. Auf ähnliche Weise wird der Treiber-Manager das SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK-Attribut für ein Anweisungshandle "Treiber" mit einem Funktionszeiger ungleich NULL-, das auch vom Typ SQL_ASYNC_NOTIFICATION_CALLBACK, für den Treiber in den Benachrichtigungsmodus für arbeiten Alle asynchronen Vorgänge auf diesem Handle.  
  
 Wenn ein asynchroner Vorgang in einem Handle Treiber ausgeführt wird, sollte die asynchrone Treiberfunktionen in einem nicht blockierenden Stil funktionieren. Wenn der Vorgang sofort ausführen kann, sollten die-Treiberfunktion SQL_STILL_EXECUTING zurück. Diese Anforderung gilt für sowohl Abruf und Notification-Modus zur Verfügung.  
  
 Ist ein Handle im Notification asynchronen Modus, muss der Treiber die Benachrichtigung Callback-Funktion, mit der Adresse der Wert für das Attribut SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK ist, Aufrufen nach Zurückgeben von SQL_STILL_EXECUTING. Das heißt, muss ein zurückgegebener SQL_STILL_EXECUTING mit einen Aufruf der Rückruffunktion Benachrichtigung kombiniert werden. Sollte der Treiber verwenden den aktuellen Wert des Attributs Handle SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT als Wert für den Aufruf zurück-Funktionsparameter *"pContext"*.  
  
 Der Treiber muss nicht zurück im Thread aufrufen, die der Treiber-Funktion aufruft. Es gibt keinen Grund, den Fortschritt zu benachrichtigen, bevor die Funktion zurückgibt. Der Treiber sollte einen eigenen Thread zum Rückruf verwenden. Der Treiber-Manager verwendet zum Ausführen von umfangreichen Verarbeitungslogik nicht Rückrufthread des Treibers.  
  
 Der Treiber-Manager wird die ursprüngliche Funktion wieder aufrufen, nachdem der Treiber wieder aufgerufen. Der Treiber-Manager kann einen Thread verwenden, der weder ein Anwendungsthread noch einen Treiber-Thread ist. Wenn der Treiber einige Informationen zu den Thread (z. B. Sicherheits-Token "oder" Benutzer-ID) verwendet, sollten der Treiber speichern die erforderliche Informationen in der ersten asynchrone Aufruf und verwenden Sie den gespeicherten Wert vor dem gesamten asynchronen Vorgang ist abgeschlossen. In der Regel nur **SQLDriverConnect**, **SQLConnect**, oder **SQLBrowseConnect** müssen diese Art von Informationen zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
