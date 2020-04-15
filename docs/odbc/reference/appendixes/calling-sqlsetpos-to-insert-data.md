---
title: Aufrufen von SQLSetPos zum Einfügen von Daten | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cb374b2506d55b400207c8f60bdf42bb6bb4065e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306601"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>Aufrufen von SQLSetPos zum Einfügen von Daten
Wenn eine ODBC *2.x-Anwendung,* die mit einem ODBC *3.x-Treiber* arbeitet, **SQLSetPos** mit dem *Operation-Argument* SQL_ADD aufruft, wird dieser Aufruf im Treiber-Manager nicht **SQLBulkOperations**zugeordnet. Wenn ein ODBC *3.x-Treiber* mit einer Anwendung arbeiten soll, die **SQLSetPos** mit SQL_ADD aufruft, sollte der Treiber diesen Vorgang unterstützen.  
  
 Ein großer Unterschied im Verhalten, wenn **SQLSetPos** mit SQL_ADD aufgerufen wird, tritt auf, wenn es im Zustand S6 aufgerufen wird. In ODBC *2.x*hat der Treiber S1010 zurückgegeben, als **SQLSetPos** mit SQL_ADD im Zustand S6 aufgerufen wurde (nachdem der Cursor mit **SQLFetch**positioniert wurde). In ODBC *3.x*kann **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD im Zustand S6 aufgerufen werden. Ein zweiter großer Unterschied im Verhalten besteht darin, dass **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD im Zustand S5 aufgerufen werden kann, während **SQLSetPos** mit einem **Vorgang** von SQL_ADD nicht. Informationen zu Anweisungsübergängen, die für denselben Aufruf in ODBC *3.x*auftreten können, finden Sie in [Anhang B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
