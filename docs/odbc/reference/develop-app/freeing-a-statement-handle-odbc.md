---
title: Freigeben eines Anweisungshandles ODBC | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement handles [ODBC]
- handles [ODBC], statement
- freeing statement handles [ODBC]
ms.assetid: ee18e2f1-2690-4cc1-9e5c-e20244e5d480
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 638cf9fb3c7af73130cf1413559b9baee2a354c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68069779"
---
# <a name="freeing-a-statement-handle-odbc"></a>Freigeben einer Anweisungshandle-ODBC
Wie bereits erwähnt, ist es effizienter, Wiederverwenden von Anweisungen als zum Löschen und neu zuzuordnen. Vor der Ausführung einer neuen SQL-Anweisung in einer Anweisung, sollten Anwendungen sicher sein, dass die aktuellen anweisungseinstellungen korrekt sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im allgemeinen Parametern und Resultsets für die alte SQL-Anweisung müssen entfernt werden soll (durch Aufrufen von **SQLFreeStmt** mit den Optionen SQL_RESET_PARAMS und SQL_UNBIND) und den neu zugeordneten für die neue SQL-Anweisung.  
  
 Wenn die Anwendung mithilfe der Anweisung abgeschlossen ist, ruft er **SQLFreeHandle** um die Anweisung freizugeben. Nach der Freigabe der der Anweisung, ist es ein anwendungsprogrammierungsfehler Fehler Handle von der Anweisung in einem Aufruf von einer ODBC-Funktion zu verwenden. Dies ist also nicht definierte, aber wahrscheinlich schwerwiegende Folgen.  
  
 Wenn **SQLFreeHandle** aufgerufen wird, wird der Treiberversionen, die die Struktur, die zum Speichern von Informationen über die Anweisung verwendet.  
  
 **SQLDisconnect** alle Anweisungen für eine Verbindung automatisch freigibt.
