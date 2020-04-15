---
title: Löschen von Zeilen im Rowset mit SQLSetPos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940bcc3e2ee6a042394797d6038028cce64862f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305951"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Löschen von Zeilen im Rowset mit SQLSetPos
Durch den Löschvorgang von **SQLSetPos** wird die Datenquelle eine oder mehrere ausgewählte Zeilen einer Tabelle löschen. Um Zeilen mit **SQLSetPos**zu löschen, ruft die Anwendung **SQLSetPos** *auf,* wobei Operation auf SQL_DELETE festgelegt ist und *RowNumber* auf die Nummer der zu löschenden Zeile festgelegt ist. Wenn *RowNumber* 0 ist, werden alle Zeilen im Rowset gelöscht.  
  
 Nachdem **SQLSetPos** zurückgegeben wurde, ist die gelöschte Zeile die aktuelle Zeile, deren Status SQL_ROW_DELETED ist. Die Zeile kann nicht in weiteren positionierten Vorgängen verwendet werden, z. B. in Aufrufen von **SQLGetData** oder **SQLSetPos**.  
  
 Beim Löschen aller Zeilen des Rowsets *(RowNumber* ist gleich 0) kann die Anwendung verhindern, dass der Treiber bestimmte Zeilen mithilfe des Zeilenoperationarrays löscht, genauso wie für den Aktualisierungsvorgang von **SQLSetPos**. (Siehe [Aktualisieren von Zeilen im Rowset mit SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Jede Zeile, die gelöscht wird, sollte eine Zeile sein, die im Resultset vorhanden ist. Wenn die Anwendungspuffer durch Abrufen gefüllt wurden und ein Zeilenstatusarray beibehalten wurde, sollten seine Werte an jeder dieser Zeilenpositionen nicht SQL_ROW_DELETED, SQL_ROW_ERROR oder SQL_ROW_NOROW sein.
