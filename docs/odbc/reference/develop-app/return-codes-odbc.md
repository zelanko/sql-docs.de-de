---
title: Rückgabecodes ODBC | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15e434025ed1201ca61371c2fb88e70143e131a5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304311"
---
# <a name="return-codes-odbc"></a>ODBC-Rückgabecodes
Jede Funktion in ODBC gibt einen Code zurück, der als *Rückgabecode* bezeichnet wird und den Gesamterfolg oder Fehler der Funktion angibt. Die Programmlogik basiert im Allgemeinen auf Rückgabecodes.  
  
 Der folgende Code ruft z. B. **SQLFetch** auf, um die Zeilen in einem Resultset abzurufen. Es überprüft den Rückgabecode der Funktion, um festzustellen, ob das Ende des Resultsets erreicht wurde (SQL_NO_DATA), ob Warnungsinformationen zurückgegeben wurden (SQL_SUCCESS_WITH_INFO), oder ob ein Fehler aufgetreten ist (SQL_ERROR).  
  
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
  
 In der folgenden Tabelle werden die Rückgabecodes definiert.  
  
|Rückgabecode|Beschreibung|  
|-----------------|-----------------|  
|SQL_SUCCESS|Funktion erfolgreich abgeschlossen. Die Anwendung ruft **SQLGetDiagField** auf, um zusätzliche Informationen aus dem Headerdatensatz abzurufen.|  
|Sql_success_with_info|Funktion erfolgreich abgeschlossen, möglicherweise mit einem nicht tödlichen Fehler (Warnung). Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um zusätzliche Informationen abzurufen.|  
|SQL_ERROR|Funktion fehlgeschlagen. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um zusätzliche Informationen abzurufen. Der Inhalt aller Ausgabeargumente für die Funktion ist nicht definiert.|  
|SQL_INVALID_HANDLE|Die Funktion ist aufgrund einer ungültigen Umgebung, einer Verbindung, einer Anweisung oder eines Deskriptorhandles fehlgeschlagen. Dies weist auf einen Programmierfehler hin. Zusätzliche Informationen sind von **SQLGetDiagRec** oder **SQLGetDiagField**nicht verfügbar. Dieser Code wird nur zurückgegeben, wenn es sich bei dem Handle um einen Nullzeiger oder um den falschen Typ handelt, z. B. wenn ein Anweisungshandle für ein Argument übergeben wird, das ein Verbindungshandle erfordert.|  
|SQL_NO_DATA|Weitere Daten waren nicht verfügbar. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um zusätzliche Informationen abzurufen. Ein oder mehrere treiberdefinierte Statusdatensätze in Klasse 02xxx können zurückgegeben werden. **Hinweis:**  In ODBC 2. *x*wurde dieser Rückgabecode SQL_NO_DATA_FOUND genannt.|  
|SQL_NEED_DATA|Es werden weitere Daten benötigt, z. B. wenn Parameterdaten zur Ausführungszeit oder zusätzliche Verbindungsinformationen gesendet werden. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um ggf. zusätzliche Informationen abzurufen.|  
|SQL_STILL_EXECUTING|Eine Funktion, die asynchron gestartet wurde, wird immer noch ausgeführt. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um ggf. zusätzliche Informationen abzurufen.|
