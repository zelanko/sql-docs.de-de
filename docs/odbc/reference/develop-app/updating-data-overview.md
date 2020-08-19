---
description: Aktualisieren einer Datenübersicht
title: Übersicht über das Aktualisieren von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], about updating data
- data updates [ODBC]
- updating data [ODBC]
- data updates [ODBC], about data updates
ms.assetid: 062036a4-cda6-4aaa-9765-f1ec3e0b31b1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2b1755ea75426030a96ed7b349cc82f0fc7e282a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424422"
---
# <a name="updating-data-overview"></a>Aktualisieren einer Datenübersicht
Anwendungen können Daten entweder durch Ausführen von SQL-Anweisungen oder durch Aufrufen von **SQLSetPos** oder **SQLBulkOperations**aktualisieren. **Update**-, **Delete**-und **Insert** -Anweisungen agieren direkt in der Datenquelle und werden in der Regel von Treibern unterstützt. Die durchsuchten Update-und DELETE-Anweisungen enthalten eine Angabe der zu ändernden Zeilen. Positionierte UPDATE-und DELETE-Anweisungen und **SQLSetPos** agieren über einen Cursor für die Datenquelle und werden weniger weit unterstützt.  
  
 Ob Cursor Änderungen erkennen können, die an dem Resultset mit den in diesem Abschnitt beschriebenen Methoden vorgenommen wurden, hängt vom Typ des Cursors und seiner Implementierung ab. Vorwärts Cursor werden keine Zeilen erneut überprüfen und somit keine Änderungen erkennen. Informationen dazu, ob scrollbare Cursor Änderungen erkennen können, finden Sie unter [scrollbare Cursor](../../../odbc/reference/develop-app/scrollable-cursors.md).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [UPDATE-, DELETE- und INSERT-Anweisungen](../../../odbc/reference/develop-app/update-delete-and-insert-statements.md)  
  
-   [Positionierte Aktualisierung und DELETE-Anweisungen](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)  
  
-   [Simulieren von positionierten Aktualisierungen und DELETE-Anweisungen](../../../odbc/reference/develop-app/simulating-positioned-update-and-delete-statements.md)  
  
-   [Bestimmen der Anzahl der betroffenen Zeilen](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)  
  
-   [Aktualisieren von Daten mit SQLSetPos](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)  
  
-   [Aktualisieren von Daten mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)  
  
-   [Long-Daten, SQLSetPos und SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)
