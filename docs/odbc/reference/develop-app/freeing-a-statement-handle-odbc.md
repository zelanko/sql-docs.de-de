---
description: Freigeben einer Anweisungshandle-ODBC
title: Freigeben eines Anweisungs Handles (ODBC) | Microsoft-Dokumentation
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
ms.openlocfilehash: d199d00c007abc6836755f5a78e93e3fd85b140b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461462"
---
# <a name="freeing-a-statement-handle-odbc"></a>Freigeben einer Anweisungshandle-ODBC
Wie bereits erwähnt, ist es effizienter,-Anweisungen wiederzuverwenden, als Sie zu löschen und neue zuzuweisen. Vor dem Ausführen einer neuen SQL-Anweisung für eine-Anweisung müssen Anwendungen sicherstellen, dass die aktuellen Anweisungs Einstellungen geeignet sind. Dazu zählen beispielsweise Anweisungsattribute, Parameterbindungen und Resultsetbindungen. Im Allgemeinen müssen die Bindung von Parametern und Resultsets für die alte SQL-Anweisung aufgehoben werden (durch Aufrufen von **SQLFreeStmt** mit den Optionen SQL_RESET_PARAMS und SQL_UNBIND) und für die neue SQL-Anweisung erneut.  
  
 Wenn die Anwendung die Verwendung der-Anweisung abgeschlossen hat, wird **SQLFreeHandle** aufgerufen, um die-Anweisung freizugeben. Nach dem Freigeben der-Anweisung handelt es sich um einen Fehler bei der Anwendungsprogrammierung, bei dem das-Handle der Anweisung in einem Rückruf einer ODBC-Funktion verwendet wird. Dies hat nicht definierte, aber wahrscheinlich schwerwiegende Konsequenzen.  
  
 Wenn **SQLFreeHandle** aufgerufen wird, gibt der Treiber die-Struktur frei, die zum Speichern von Informationen über die-Anweisung verwendet wird.  
  
 **SQLDisconnect** gibt automatisch alle Anweisungen für eine Verbindung frei.
