---
description: ODBC-Rückgabecodes
title: Rückgabe Codes ODBC | Microsoft-Dokumentation
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
ms.openlocfilehash: 79a06ad170f747c3841c42eadef0288af6fef39a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494636"
---
# <a name="return-codes-odbc"></a>ODBC-Rückgabecodes
Jede Funktion in ODBC gibt einen Code zurück, der als *Rückgabecode bezeichnet wird,* der den Gesamterfolg oder Misserfolg der Funktion angibt. Die Programmlogik basiert im Allgemeinen auf Rückgabecodes.  
  
 Der folgende Code ruft z. b. **SQLFetch** auf, um die Zeilen in einem Resultset abzurufen. Der Rückgabecode der Funktion wird überprüft, um zu bestimmen, ob das Ende des Resultsets erreicht wurde (SQL_NO_DATA), ob Warnungs Informationen zurückgegeben wurden (SQL_SUCCESS_WITH_INFO) oder ob ein Fehler aufgetreten ist (SQL_ERROR).  
  
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
  
 In der folgenden Tabelle sind die Rückgabecodes definiert.  
  
|Rückgabecode|Beschreibung|  
|-----------------|-----------------|  
|SQL_SUCCESS|Die Funktion wurde erfolgreich abgeschlossen. Die Anwendung ruft **SQLGetDiagField** auf, um zusätzliche Informationen aus dem Header Daten Satz abzurufen.|  
|SQL_SUCCESS_WITH_INFO|Die Funktion wurde erfolgreich abgeschlossen, möglicherweise mit einem nicht schwerwiegenden Fehler (Warnung). Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um weitere Informationen abzurufen.|  
|SQL_ERROR|Fehler bei der Funktion. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um weitere Informationen abzurufen. Der Inhalt von Ausgabe Argumenten für die Funktion ist nicht definiert.|  
|SQL_INVALID_HANDLE|Funktion konnte aufgrund einer ungültigen Umgebung, Verbindung, Anweisung oder eines Deskriptorhandles nicht ausgeführt werden. Dies weist auf einen Programmierfehler hin. In **SQLGetDiagRec** oder **SQLGetDiagField**sind keine weiteren Informationen verfügbar. Dieser Code wird nur zurückgegeben, wenn das Handle ein NULL-Zeiger ist oder den falschen Typ hat, z. b. Wenn ein Anweisungs Handle für ein Argument, das ein Verbindungs Handle erfordert, übermittelt wird.|  
|SQL_NO_DATA|Es waren keine weiteren Daten verfügbar. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um weitere Informationen abzurufen. Ein oder mehrere Treiber definierte Statusdaten Sätze in der Klasse 02xxx können zurückgegeben werden. **Hinweis:**  In ODBC 2. *x*, dieser Rückgabecode wurde SQL_NO_DATA_FOUND benannt.|  
|SQL_NEED_DATA|Es werden weitere Daten benötigt, z. b. wenn Parameterdaten zur Ausführungszeit gesendet werden oder zusätzliche Verbindungsinformationen erforderlich sind. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um ggf. Weitere Informationen abzurufen.|  
|SQL_STILL_EXECUTING|Eine Funktion, die asynchron gestartet wurde, wird weiterhin ausgeführt. Die Anwendung ruft **SQLGetDiagRec** oder **SQLGetDiagField** auf, um ggf. Weitere Informationen abzurufen.|
