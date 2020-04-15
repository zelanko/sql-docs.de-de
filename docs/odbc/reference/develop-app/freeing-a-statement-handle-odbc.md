---
title: Befreien eines Statement Handle ODBC | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01e4cb46edf1b1a0f1c6dfaa0273c1dd5b392686
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305615"
---
# <a name="freeing-a-statement-handle-odbc"></a>Freigeben einer Anweisungshandle-ODBC
Wie bereits erwähnt, ist es effizienter, Anweisungen wiederzuverwenden, als sie fallen zu lassen und neue zuzuweisen. Vor dem Ausführen einer neuen SQL-Anweisung für eine Anweisung sollten Anwendungen sicherstellen, dass die aktuellen Anweisungseinstellungen angemessen sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im Allgemeinen müssen Parameter und Ergebnismengen für die alte SQL-Anweisung ungebunden sein (durch Aufrufen von **SQLFreeStmt** mit den optionen SQL_RESET_PARAMS und SQL_UNBIND) und für die neue SQL-Anweisung zurückgefordert werden.  
  
 Wenn die Anwendung die Anweisung verwendet hat, ruft sie **SQLFreeHandle** auf, um die Anweisung freizugeben. Nach dem Loslassen der Anweisung ist es ein Anwendungsprogrammierfehler, das Handle der Anweisung in einem Aufruf einer ODBC-Funktion zu verwenden. dies hat undefinierte, aber wahrscheinlich fatale Folgen.  
  
 Wenn **SQLFreeHandle** aufgerufen wird, gibt der Treiber die Struktur frei, die zum Speichern von Informationen über die Anweisung verwendet wird.  
  
 **SQLDisconnect** gibt automatisch alle Anweisungen für eine Verbindung frei.
