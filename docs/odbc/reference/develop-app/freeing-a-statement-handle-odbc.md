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
manager: craigg
ms.openlocfilehash: bc16e820671aa69c15365413d44fb9bcf807236b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061545"
---
# <a name="freeing-a-statement-handle-odbc"></a>Freigeben einer Anweisungshandle-ODBC
Wie bereits erwähnt, ist es effizienter, Wiederverwenden von Anweisungen als zum Löschen und neu zuzuordnen. Vor der Ausführung einer neuen SQL-Anweisung in einer Anweisung, sollten Anwendungen sicher sein, dass die aktuellen anweisungseinstellungen korrekt sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im allgemeinen Parametern und Resultsets für die alte SQL-Anweisung müssen entfernt werden soll (durch Aufrufen von **SQLFreeStmt** mit den Optionen SQL_RESET_PARAMS und SQL_UNBIND) und den neu zugeordneten für die neue SQL-Anweisung.  
  
 Wenn die Anwendung mithilfe der Anweisung abgeschlossen ist, ruft er **SQLFreeHandle** um die Anweisung freizugeben. Nach der Freigabe der der Anweisung, ist es ein anwendungsprogrammierungsfehler Fehler Handle von der Anweisung in einem Aufruf von einer ODBC-Funktion zu verwenden. Dies ist also nicht definierte, aber wahrscheinlich schwerwiegende Folgen.  
  
 Wenn **SQLFreeHandle** aufgerufen wird, wird der Treiberversionen, die die Struktur, die zum Speichern von Informationen über die Anweisung verwendet.  
  
 **SQLDisconnect** alle Anweisungen für eine Verbindung automatisch freigibt.
