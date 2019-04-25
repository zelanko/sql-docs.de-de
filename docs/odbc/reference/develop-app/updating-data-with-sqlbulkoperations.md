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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 958514adc02452cdc75a05e7ad28cd31f4e8e0e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62632443"
---
# <a name="updating-data-with-sqlbulkoperations"></a>Aktualisieren von Daten mit SQLBulkOperations
Anwendungen können Massenvorgänge Update, Delete, Abrufen oder Einfügen auf die zugrunde liegende Tabelle in der Datenquelle mit einem Aufruf von **SQLBulkOperations**. Aufrufen von **SQLBulkOperations** ist eine praktische Alternative zum Erstellen und Ausführen einer SQL-Anweisung. Sie können einen ODBC-Treiber positionierte Updates zu unterstützen, auch wenn die Datenquelle positionierte SQL-Anweisungen nicht unterstützt. Es ist Teil des Paradigmas Zugriff auf die vollständige Datenbank mithilfe von Funktionsaufrufen zu erreichen.  
  
 **SQLBulkOperations** greift auf das aktuelle Rowset und kann verwendet werden, nur nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**. Die Anwendung gibt die Zeilen aus, um zu aktualisieren, löschen oder aktualisieren, indem Sie ihre Lesezeichen Zwischenspeichern. Der Treiber Ruft ab, die neuen Daten für die Zeilen aktualisiert werden, oder die neuen Daten in der zugrunde liegenden Tabelle, aus dem Rowset Puffer eingefügt werden soll.  
  
 Die Rowsetgröße von verwendet werden **SQLBulkOperations** festgelegt ist, durch einen Aufruf von **SQLSetStmtAttr** mit einer *Attribut* SQL_ATTR_ROW_ARRAY_SIZE Argument. Im Gegensatz zu **SQLSetPos**, die eine neue Rowsetgröße verwendet, nur nach einem Aufruf von **SQLFetch** oder **SQLFetchScroll**, **SQLBulkOperations** verwendet das neue Rowsetgröße, nach dem Aufruf von **SQLSetStmtAttr**.  
  
 Da die meisten Interaktion mit relationalen Datenbanken über SQL und erfolgt **SQLBulkOperations** wird allgemein nicht unterstützt. Treiber kann jedoch problemlos emulieren, sie durch Erstellen und Ausführen einer **UPDATE**, **löschen**, oder **einfügen** Anweisung.  
  
 Um zu bestimmen, welche Vorgänge **SQLBulkOperation** unterstützt werden, um eine Anwendung ruft **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1, SQL_KEYSET_CURSOR _ATTRIBUTES1 oder SQL_STATIC_CURSOR_ATTRIBUTES1 Informationsoption (je nach Art des Cursors).  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Aktualisieren von Zeilen durch Lesezeichen mit SQLBulkOperations](../../../odbc/reference/develop-app/updating-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Löschen von Zeilen durch Lesezeichen mit SQLBulkOperations](../../../odbc/reference/develop-app/deleting-rows-by-bookmark-with-sqlbulkoperations.md)  
  
-   [Einfügen von Zeilen mit SQLBulkOperations](../../../odbc/reference/develop-app/inserting-rows-with-sqlbulkoperations.md)  
  
-   [Abrufen von Zeilen mit SQLBulkOperations](../../../odbc/reference/develop-app/fetching-rows-with-sqlbulkoperations.md)
