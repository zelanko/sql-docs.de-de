---
title: ODBC-Rückgabecodes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- return codes [ODBC]
- diagnostic information [ODBC], return codes
ms.assetid: e893b719-4392-476f-911a-5ed6da6f7e94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aee8914493c66ff451d7bca7f56fc8723d2a7ca0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63254142"
---
# <a name="return-codes-odbc"></a>ODBC-Rückgabecodes
Jede Funktion in der ODBC gibt einen Code, bekannt als die *Rückgabecode,* gibt den Erfolg oder Fehler bei der Funktion an. Die Programmlogik basiert im Allgemeinen auf Rückgabecodes.  
  
 Beispielsweise der folgende code ruft **SQLFetch** zum Abrufen der Zeilen in einem Resultset. Er überprüft den Rückgabecode der Funktion, die bestimmen, ob das Ende des Resultsets (SQL_NO_DATA), erreicht wurde, wenn alle Warnungsinformationen (SQL_SUCCESS_WITH_INFO) zurückgegeben wurde, oder bei einem Fehler (SQL_ERROR).  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
while ((rc=SQLFetch(hstmt)) != SQL_NO_DATA) {  
   if (rc == SQL_SUCCESS_WITH_INFO) {  
      // Call function to display warning information.  
   } else if (rc == SQL_ERROR) {  
      // Call function to display error information.  
      break;  
   }  
   // Process row.  
}  
```  
  
 Der Rückgabecode SQL_INVALID_HANDLE gibt immer einen Programmierfehler an und sollte zur Laufzeit nie auftreten. Alle anderen Rückgabecodes stellen Laufzeitinformationen bereit, wenngleich SQL_ERROR einen Programmierfehler angeben kann.  
  
 Der folgenden Tabelle werden die Rückgabecodes.  
  
|Rückgabecode|Beschreibung|  
|-----------------|-----------------|  
|SQL_SUCCESS|Die Funktion wurde erfolgreich abgeschlossen. Ruft die Anwendung **SQLGetDiagField** um zusätzliche Informationen aus dem Headerdatensatz abzurufen.|  
|SQL_SUCCESS_WITH_INFO|Die Funktion wurde erfolgreich abgeschlossen, möglicherweise mit einem nicht schwerwiegenden Fehler (Warnung). Ruft die Anwendung **SQLGetDiagRec** oder **SQLGetDiagField** um zusätzliche Informationen abzurufen.|  
|SQL_ERROR|Fehler bei der Funktion. Ruft die Anwendung **SQLGetDiagRec** oder **SQLGetDiagField** um zusätzliche Informationen abzurufen. Der Inhalt der Ausgabeargumente an die Funktion ist nicht definiert.|  
|SQL_INVALID_HANDLE|Fehler bei der Funktion aufgrund eines ungültigen Handles für Umgebung "," Verbindung ","-Anweisung "oder"-Deskriptor. Dies weist einen Programmierungsfehler hin. Keine zusätzlichen Informationen steht in **SQLGetDiagRec** oder **SQLGetDiagField**. Dieser Code wird zurückgegeben, nur, wenn das Handle ein null-Zeiger ist oder den falschen Typ hat, z. B. wenn ein Anweisungshandle für ein Argument übergeben wird, die ein Verbindungshandle erforderlich sind.|  
|SQL_NO_DATA|Es war keine weiteren Daten verfügbar. Ruft die Anwendung **SQLGetDiagRec** oder **SQLGetDiagField** um zusätzliche Informationen abzurufen. Einen oder mehrere treiberdefinierten Statusdatensätze in der Klasse 02xxx können zurückgegeben werden. **Hinweis**:  In ODBC 2. *x*, damit die Code hieß SQL_NO_DATA_FOUND zurückgegeben.|  
|SQL_NEED_DATA|Mehr Daten erforderlich ist, z. B. wenn die Parameterdaten zum Zeitpunkt der Ausführung gesendet wird, oder zusätzliche Verbindungsinformationen ist erforderlich. Ruft die Anwendung **SQLGetDiagRec** oder **SQLGetDiagField** um zusätzliche Informationen, ggf. abzurufen.|  
|SQL_STILL_EXECUTING|Eine Funktion, die asynchron gestartet wurde, wird weiterhin ausgeführt. Ruft die Anwendung **SQLGetDiagRec** oder **SQLGetDiagField** um zusätzliche Informationen, ggf. abzurufen.|
