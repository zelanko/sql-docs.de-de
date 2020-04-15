---
title: Aktualisieren von Daten mit SQLSetPos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
- SQLSetPos function [ODBC], updating data
ms.assetid: e9625b59-06a0-4883-b155-b932ba7528d9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16476a1e1007905f34ec2e70ce6032eb8d81fe7a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286160"
---
# <a name="updating-data-with-sqlsetpos"></a>Aktualisieren von Daten mit SQLSetPos
Anwendungen können jede Zeile im Rowset mit **SQLSetPos**aktualisieren oder löschen. Das Aufrufen von **SQLSetPos** ist eine praktische Alternative zum Erstellen und Ausführen einer SQL-Anweisung. Es ermöglicht einem ODBC-Treiber die Unterstützung positionierter Updates, auch wenn die Datenquelle keine positionierten SQL-Anweisungen unterstützt. Es ist Teil des Paradigmas, einen vollständigen Datenbankzugriff durch Funktionsaufrufe zu erreichen.  
  
 **SQLSetPos** arbeitet mit dem aktuellen Rowset und kann nur nach einem Aufruf von **SQLFetchScroll**verwendet werden. Die Anwendung gibt die Nummer der zu aktualisierenden, zu löschenden oder einzufügenden Zeile an, und der Treiber ruft die neuen Daten für diese Zeile aus den Rowsetpuffern ab. **SQLSetPos** kann auch verwendet werden, um eine angegebene Zeile als aktuelle Zeile festzulegen oder eine bestimmte Zeile im Rowset aus der Datenquelle zu aktualisieren.  
  
 Die Rowsetgröße wird durch einen Aufruf von **SQLSetStmtAttr** mit dem *Attributargument* SQL_ATTR_ROW_ARRAY_SIZE festgelegt. **SQLSetPos** verwendet jedoch eine neue Rowsetgröße, jedoch erst nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**. Wenn z. B. die Rowsetgröße geändert wird, **wird SQLSetPos** aufgerufen und dann **SQLFetch** oder **SQLFetchScroll** aufgerufen, und der Aufruf von **SQLSetPos** verwendet die alte Rowsetgröße, während **SQLFetch** oder **SQLFetchScroll** die neue Rowsetgröße verwendet.  
  
 Die erste Zeile im Rowset ist die Zeile 1. Das *RowNumber-Argument* in **SQLSetPos** muss eine Zeile im Rowset identifizieren. Das heißt, sein Wert muss im Bereich zwischen 1 und der Anzahl der Zeilen liegen, die zuletzt abgerufen wurden (was möglicherweise kleiner als die Rowsetgröße ist). Wenn *RowNumber* 0 ist, gilt der Vorgang für jede Zeile im Rowset.  
  
 Da die meisten Interaktionen mit relationalen Datenbanken über SQL erfolgen, wird **SQLSetPos** nicht umfassend unterstützt. Ein Treiber kann ihn jedoch leicht emulieren, indem er eine **UPDATE-** oder **DELETE-Anweisung** erstellt und ausführt.  
  
 Um zu bestimmen, welche Vorgänge **SQLSetPos** unterstützt, ruft eine Anwendung **SQLGetInfo** mit der Informationsoption SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 auf (je nach Typ des Cursors).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)  
  
-   [Löschen von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/deleting-rows-in-the-rowset-with-sqlsetpos.md)
