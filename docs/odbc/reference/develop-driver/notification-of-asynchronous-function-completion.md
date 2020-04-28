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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a453967f2ffdda4af2a44429737f700f4a994cf8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287820"
---
# <a name="notification-of-asynchronous-function-completion"></a>Benachrichtigung der Asynchronen Funktionsvollendung
Im Windows 8 SDK wurde von ODBC ein Mechanismus hinzugefügt, mit dem Anwendungen benachrichtigt werden, wenn ein asynchroner Vorgang abgeschlossen ist. Dies wird als "Benachrichtigung bei Abschluss" bezeichnet. (Weitere Informationen finden Sie unter [asynchrone Ausführung (Benachrichtigungs Methode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) .) In diesem Thema werden einige der Probleme für Treiber Entwickler erläutert.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>Die Schnittstelle zwischen Treiber-Manager und Treiber  
 Der Treiber-Manager stellt intern eine Rückruffunktion der [sqlasyncnotificationcallback-Funktion](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md)bereit. **Sqlasyncnotificationcallback** kann nur vom Treiber aufgerufen werden. eine Anwendung kann Sie nicht direkt aufrufen. Der Treiber ruft **sqlasyncnotificationcallback** immer dann auf, wenn nach der letzten Rückgabe SQL_STILL_EXECUTING neue Daten vom Server empfangen wurden.  
  
 Der Treiber-Manager stellt einen Rückrufmechanismus bereit, damit ein Treiber den Treiber-Manager benachrichtigen kann, wenn beim Ausführen eines asynchronen Vorgangs nach dem Zurücksetzen der entsprechenden Funktion ein Fortschritt erfolgt SQL_STILL_EXECUTING  
  
 Der Treiber-Manager legt das SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK-Attribut für ein Treiber Verbindungs Handle mit einem Funktionszeiger ungleich NULL fest, der vom Typ SQL_ASYNC_NOTIFICATION_CALLBACK ist, damit der Treiber im Benachrichtigungs Modus für alle asynchronen Vorgänge in diesem Handle funktioniert. Entsprechend legt der Treiber-Manager das SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK-Attribut für ein Treiber Anweisungs Handle mit einem Funktionszeiger ungleich NULL fest, der auch vom Typ "SQL_ASYNC_NOTIFICATION_CALLBACK" ist, damit der Treiber im Benachrichtigungs Modus für asynchrone Vorgänge auf diesem Handle funktioniert.  
  
 Wenn ein asynchroner Vorgang für ein Treiber handle ausgeführt wird, sollten die asynchronen Treiberfunktionen in einem nicht blockierenden Stil funktionieren. Wenn der Vorgang nicht sofort durchgeführt werden kann, sollte die Treiber Funktion SQL_STILL_EXECUTING zurückgeben. Diese Anforderung gilt sowohl für den Abruf Modus als auch den Benachrichtigungs Modus.  
  
 Wenn sich ein Handle im asynchronen Benachrichtigungs Modus befindet, muss der Treiber die Benachrichtigungs Rückruffunktion, deren Adresse der Wert für das SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK Attribut ist, nach der Rückgabe SQL_STILL_EXECUTING abrufen. Anders ausgedrückt: eine Rückgabe SQL_STILL_EXECUTING muss mit einem Aufruf der Benachrichtigungs Rückruffunktion gekoppelt werden. Der Treiber sollte den aktuellen Wert des SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT handle-Attributs als Wert für den Parameter *pContext*der Rückruffunktion verwenden.  
  
 Der Treiber darf keinen Rückruf in dem Thread aufrufen, der die Treiber Funktion aufruft. Es gibt keinen Grund, den Fortschritt zu benachrichtigen, bevor die Funktion zurückgegeben wird. Der Treiber sollte seinen eigenen Thread für den Rückruf verwenden. Der Treiber-Manager verwendet nicht den Rückruf Thread des Treibers für die Ausführung umfangreicher Verarbeitungslogik.  
  
 Der Treiber-Manager ruft die ursprüngliche Funktion erneut auf, nachdem der Treiber einen Rückruf durchführt. Der Treiber-Manager kann einen Thread verwenden, bei dem es sich weder um einen Anwendungs Thread noch um einen Treiber Thread handelt. Wenn der Treiber einige Informationen verwendet, die dem Thread zugeordnet sind (z. b. ein Sicherheits Token oder eine Benutzer-ID), sollte der Treiber die erforderlichen Informationen im ersten asynchronen aufzurufen speichern und den gespeicherten Wert verwenden, bevor der gesamte asynchrone Vorgang abgeschlossen wird. In der Regel muss nur **SQLDriverConnect**, **SQLCONNECT**oder **sqlbrowseconnetct** diese Art von Informationen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Developing an ODBC Driver (Entwickeln eines ODBC-Treibers)](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
