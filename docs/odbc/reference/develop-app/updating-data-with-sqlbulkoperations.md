---
title: Aktualisieren von Daten mit SQLBulkOperations | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBulkOperations function [ODBC], updating data
- data updates [ODBC], SQLBulkOperations
- updating data [ODBC], SQLBulkOperations
ms.assetid: 7645a704-341e-4267-adbe-061a9fda225b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b96e3a43b8385910e4260cf51dea7e4ff508200
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298484"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Aktualisieren von Daten mit SQLBulkOperations
Anwendungen können mithilfe eines Aufrufs von **SQLBulkOperations**Massen Aktualisierungs-, Lösch-, Abruf-oder Einfügevorgänge für die zugrunde liegende Tabelle in der Datenquelle ausführen. Das Aufrufen von **SQLBulkOperations** ist eine bequeme Alternative zum Erstellen und Ausführen einer SQL-Anweisung. Ein ODBC-Treiber kann positionierte Updates auch dann unterstützen, wenn die Datenquelle keine positionierten SQL-Anweisungen unterstützt. Es ist Teil des Paradigmas, mithilfe von Funktionsaufrufen den gesamten Datenbankzugriff zu erreichen.  
  
 **SQLBulkOperations** arbeitet mit dem aktuellen Rowset und kann nur nach einem **SQLFetch** -oder **SQLFetchScroll**-Aufrufs verwendet werden. Die Anwendung gibt die Zeilen an, die aktualisiert, gelöscht oder aktualisiert werden sollen, indem Ihre Lesezeichen zwischengespeichert werden. Der Treiber ruft die neuen Daten für zu Aktualisier Ende Zeilen oder die neuen Daten, die in die zugrunde liegende Tabelle eingefügt werden sollen, aus den rowsetpuffern ab.  
  
 Die Rowsetgröße, die von **SQLBulkOperations** verwendet werden soll, wird durch einen-Befehl von **SQLSetStmtAttr** mit dem *Attribut* Argument SQL_ATTR_ROW_ARRAY_SIZE festgelegt. Anders als bei **SQLSetPos**, bei dem nur nach einem **SQLFetch** -oder **SQLFetchScroll**-Befehl eine neue Rowsetgröße verwendet wird, verwendet **SQLBulkOperations** nach dem Aufrufen von **SQLSetStmtAttr**die neue Rowsetgröße.  
  
 Da die meisten Interaktionen mit relationalen Datenbanken mit SQL durchgeführt werden, wird **SQLBulkOperations** nicht häufig unterstützt. Ein Treiber kann ihn jedoch problemlos emulieren, indem er eine **Update**-, **Delete**-oder **Insert** -Anweisung erstellt und ausführt.  
  
 Um zu ermitteln, welche Vorgänge von **sqlbulkoperation** unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit der Option SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR_ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 Information auf (je nach Cursortyp).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Aktualisieren von Zeilen durch Textmarken mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Löschen von Zeilen durch Textmarken mit SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Einfügen von Zeilen mit SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Abrufen von Zeilen mit SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
