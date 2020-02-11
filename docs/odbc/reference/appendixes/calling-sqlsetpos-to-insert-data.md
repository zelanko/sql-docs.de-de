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
ms.openlocfilehash: e07bf71f0d622ad9095974cd7020001625edf1f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037716"
---
# <a name="calling-sqlsetpos-to-insert-data"></a>Aufrufen von SQLSetPos zum Einfügen von Daten
Wenn eine ODBC *2. x* -Anwendung, die mit einem ODBC *3. x* -Treiber arbeitet, **SQLSetPos** mit einem *Vorgangs* Argument von SQL_ADD aufruft, ordnet der Treiber-Manager diesen Aufruf **SQLBulkOperations**nicht zu. Wenn ein ODBC *3. x* -Treiber mit einer Anwendung verwendet werden soll, die **SQLSetPos** mit SQL_ADD aufruft, sollte der Treiber diesen Vorgang unterstützen.  
  
 Ein wesentlicher Unterschied im Verhalten beim Aufrufen von **SQLSetPos** mit SQL_ADD tritt auf, wenn es in State S6 aufgerufen wird. In ODBC *2. x*gab der Treiber S1010 zurück, als **SQLSetPos** mit SQL_ADD in Bundesstaat S6 aufgerufen wurde (nachdem der Cursor mit **SQLFetch**positioniert wurde). In ODBC *3. x*kann **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD in Status S6 aufgerufen werden. Ein zweiter Hauptunterschied besteht darin, dass **SQLBulkOperations** mit einem *Vorgang* von SQL_ADD in dem Status S5 aufgerufen werden kann, während **SQLSetPos** mit einem **Vorgang** von SQL_ADD nicht. Informationen zu den Anweisungs Übergängen, die für denselben-Befehl in ODBC *3. x*auftreten können, finden Sie unter [Anhang B: ODBC-Status Übergangs Tabellen](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
