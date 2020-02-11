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
ms.openlocfilehash: de3496661f2ab329e5bf662a9cb8fa749cb81bfc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129324"
---
# <a name="notification-of-asynchronous-function-completion"></a>Benachrichtigung der Asynchronen Funktionsvollendung
Im Windows 8 SDK wurde von ODBC ein Mechanismus hinzugefügt, mit dem Anwendungen benachrichtigt werden, wenn ein asynchroner Vorgang abgeschlossen ist. Dies wird als "Benachrichtigung bei Abschluss" bezeichnet. (Weitere Informationen finden Sie unter [asynchrone Ausführung (Benachrichtigungs Methode)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md) .) In diesem Thema werden einige der Probleme für Treiber Entwickler erläutert.  
  
## <a name="the-interface-between-the-driver-manager-and-driver"></a>Die Schnittstelle zwischen Treiber-Manager und Treiber  
 Der Treiber-Manager stellt intern eine Rückruffunktion der [sqlasyncnotificationcallback-Funktion](../../../odbc/reference/develop-driver/sqlasyncnotificationcallback-function.md)bereit. **Sqlasyncnotificationcallback** kann nur vom Treiber aufgerufen werden. eine Anwendung kann Sie nicht direkt aufrufen. Der Treiber ruft **sqlasyncnotificationcallback** immer dann auf, wenn nach der letzten Rückgabe SQL_STILL_EXECUTING neue Daten vom Server empfangen wurden.  
  
 Der Treiber-Manager stellt einen Rückrufmechanismus bereit, damit ein Treiber den Treiber-Manager benachrichtigen kann, wenn beim Ausführen eines asynchronen Vorgangs nach dem Zurücksetzen der entsprechenden Funktion ein Fortschritt erfolgt SQL_STILL_EXECUTING  
  
 Der Treiber-Manager legt das SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK-Attribut für ein Treiber Verbindungs Handle mit einem Funktionszeiger ungleich NULL fest, der vom Typ "SQL_ASYNC_NOTIFICATION_CALLBACK" ist, damit der Treiber im Benachrichtigungs Modus für alle asynchronen Vorgänge funktioniert. Vorgänge für dieses handle. Entsprechend legt der Treiber-Manager das SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK-Attribut für ein Treiber Anweisungs Handle auf einen nicht-NULL-Funktionszeiger fest, der auch vom Typ "SQL_ASYNC_NOTIFICATION_CALLBACK" ist, damit der Treiber im Benachrichtigungs Modus für Alle asynchronen Vorgänge für dieses handle.  
  
 Wenn ein asynchroner Vorgang für ein Treiber handle ausgeführt wird, sollten die asynchronen Treiberfunktionen in einem nicht blockierenden Stil funktionieren. Wenn der Vorgang nicht sofort durchgeführt werden kann, sollte die Treiber Funktion SQL_STILL_EXECUTING zurückgeben. Diese Anforderung gilt sowohl für den Abruf Modus als auch den Benachrichtigungs Modus.  
  
 Wenn sich ein Handle im asynchronen Benachrichtigungs Modus befindet, muss der Treiber die Benachrichtigungs Rückruffunktion abrufen, deren Adresse der Wert für die SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACK oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CALLBACK Attribut ist, einmal nach Rückgabe SQL_STILL_EXECUTING. Anders ausgedrückt: eine Rückgabe SQL_STILL_EXECUTING muss mit einem Aufruf der Benachrichtigungs Rückruffunktion gekoppelt werden. Der Treiber sollte den aktuellen Wert des SQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXT oder SQL_ATTR_ASYNC_STMT_NOTIFICATION_CONTEXT handle-Attributs als Wert für den Parameter *pContext*der Rückruffunktion verwenden.  
  
 Der Treiber darf keinen Rückruf in dem Thread aufrufen, der die Treiber Funktion aufruft. Es gibt keinen Grund, den Fortschritt zu benachrichtigen, bevor die Funktion zurückgegeben wird. Der Treiber sollte seinen eigenen Thread für den Rückruf verwenden. Der Treiber-Manager verwendet nicht den Rückruf Thread des Treibers für die Ausführung umfangreicher Verarbeitungslogik.  
  
 Der Treiber-Manager ruft die ursprüngliche Funktion erneut auf, nachdem der Treiber einen Rückruf durchführt. Der Treiber-Manager kann einen Thread verwenden, bei dem es sich weder um einen Anwendungs Thread noch um einen Treiber Thread handelt. Wenn der Treiber einige Informationen verwendet, die mit dem Thread verknüpft sind (z. b. ein Sicherheits Token oder eine Benutzer-ID), sollte der Treiber die erforderlichen Informationen im ersten asynchronen aufzurufen speichern und den gespeicherten Wert vor dem gesamten asynchronen Vorgang verwenden. Bit. In der Regel muss nur **SQLDriverConnect**, **SQLCONNECT**oder **sqlbrowseconnetct** diese Art von Informationen verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Entwickeln eines ODBC-Treibers](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
