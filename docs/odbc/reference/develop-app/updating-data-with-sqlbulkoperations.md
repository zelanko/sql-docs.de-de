---
title: Aktualisieren von Daten mit SQLBulkOperations | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298484"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Aktualisieren von Daten mit SQLBulkOperations
Anwendungen können Massenaktualisierungs-, Lösch-, Abruf- oder Einfügevorgänge für die zugrunde liegende Tabelle in der Datenquelle mit einem Aufruf von **SQLBulkOperations**ausführen. Das Aufrufen von **SQLBulkOperations** ist eine praktische Alternative zum Erstellen und Ausführen einer SQL-Anweisung. Es ermöglicht einem ODBC-Treiber die Unterstützung positionierter Updates, auch wenn die Datenquelle keine positionierten SQL-Anweisungen unterstützt. Es ist Teil des Paradigmas, einen vollständigen Datenbankzugriff durch Funktionsaufrufe zu erreichen.  
  
 **SQLBulkOperations** arbeitet mit dem aktuellen Rowset und kann nur nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**verwendet werden. Die Anwendung gibt die Zeilen an, die aktualisiert, gelöscht oder aktualisiert werden sollen, indem ihre Lesezeichen zwischengespeichert werden. Der Treiber ruft die neuen Daten für zu aktualisierende Zeilen oder die neuen Daten, die in die zugrunde liegende Tabelle eingefügt werden sollen, aus den Rowsetpuffern ab.  
  
 Die von **SQLBulkOperations** zu verwendende Rowsetgröße wird durch einen Aufruf von **SQLSetStmtAttr** mit dem *Attributargument* SQL_ATTR_ROW_ARRAY_SIZE festgelegt. Im Gegensatz zu **SQLSetPos**, das eine neue Rowsetgröße erst nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**verwendet, verwendet **SQLBulkOperations** die neue Rowsetgröße nach dem Aufruf von **SQLSetStmtAttr**.  
  
 Da die meisten Interaktionen mit relationalen Datenbanken über SQL erfolgen, wird **SQLBulkOperations** nicht umfassend unterstützt. Ein Treiber kann ihn jedoch leicht emulieren, indem er eine **UPDATE-,** **DELETE-** oder **INSERT-Anweisung** erstellt und ausführt.  
  
 Um zu bestimmen, welche Vorgänge **SQLBulkOperation** unterstützt, ruft eine Anwendung SQLGetInfo mit der **SQL_DYNAMIC_CURSOR_ATTRIBUTES1-,** SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1-, SQL_KEYSET_CURSOR_ATTRIBUTES1- oder SQL_STATIC_CURSOR_ATTRIBUTES1-Informationsoption auf (je nach Typ des Cursors).  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Aktualisieren von Zeilen durch Textmarken mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Löschen von Zeilen durch Textmarken mit SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Einfügen von Zeilen mit SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Abrufen von Zeilen mit SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
