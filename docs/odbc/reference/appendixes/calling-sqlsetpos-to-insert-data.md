---
title: Aufrufen von SQLSetPos zum Einfügen von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], inserting data
- backward compatibility [ODBC], SqlSetPos
ms.assetid: 03e5c4d0-2bb3-4649-9781-89cab73f78eb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c7424206318436532cad62690b01427f079a589
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63159276"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>Aufrufen von SQLSetPos zum Einfügen von Daten
Wenn eine ODBC-2. *x* Anwendung mit einer ODBC 3.*.x* Treiber ruft **SQLSetPos** mit einer *Vorgang* Argument SQL_ADD, der Treiber-Manager Ordnet diesen Aufruf nicht **SQLBulkOperations**. Wenn eine ODBC 3.*.x* Treiber können auf eine Anwendung, die Aufrufe **SQLSetPos** SQL_ADD, sollten der Treiber diesen Vorgang unterstützen.  
  
 Ein wesentlicher Unterschied im Verhalten beim **SQLSetPos** aufgerufen wird und SQL_ADD tritt auf, wenn sie sich im Zustand S6 aufgerufen wird. In ODBC 2. *x*, S1010 zurückgegeben beim **SQLSetPos** aufgerufen wurde, wobei SQL_ADD Status S6 (nachdem Sie mit der Cursor positioniert ist **SQLFetch**). In ODBC 3.*.x*, **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD kann im Zustand S6 aufgerufen werden. Ein zweite wichtigster Unterschied ist, die **SQLBulkOperations** mit einer *Vorgang* von SQL_ADD können sein, während er sich im Zustand S5 aufgerufen, **SQLSetPos** mit eine  **Vorgang** von SQL_ADD nicht möglich. Für die Anweisung Übergänge, die auftreten können, für den gleichen Aufruf in ODBC 3.*.x*, finden Sie unter [Anhang B: ODBC-Übergang Statustabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
