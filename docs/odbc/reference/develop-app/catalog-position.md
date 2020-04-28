---
title: Katalog Position | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0305d978dc4ecd21892a0be3916fa5072b7be95a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303381"
---
# <a name="catalog-position"></a>Katalogposition
Die Position eines Katalog namens in einem Bezeichner und die Art, wie diese vom Rest des Bezeichners getrennt ist, variieren von der Datenquelle zu der Datenquelle. Beispielsweise ist der Katalog Name in einer xbase-Datenquelle ein Verzeichnis, und in Microsoft® Windows® wird der Tabellenname (ein Dateiname) durch einen umgekehrten Schrägstrich (\\) getrennt. Diese Bedingung wird in der folgenden Abbildung veranschaulicht.  
  
 ![Katalogposition: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 In einer SQL Server Datenquelle handelt es sich bei dem Katalog um eine Datenbank, die von den Schema-und Tabellennamen durch einen Zeitraum (.) getrennt ist.  
  
 ![Katalogposition: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 In einer Oracle-Datenquelle ist der Katalog ebenfalls die Datenbank, aber folgt dem Tabellennamen und wird von den Schema-und Tabellennamen durch ein @-Zeichen (@) getrennt.  
  
 ![Katalogposition: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Um das Katalog Trennzeichen und den Speicherort des Katalog namens zu ermitteln, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CATALOG_NAME_SEPARATOR und SQL_CATALOG_LOCATION auf. Interoperable Anwendungen sollten Bezeichner entsprechend diesen Werten erstellen.  
  
 Beim Zitieren von bezeichnerbezeichnerzeichen, die mehr als einen Teil enthalten, müssen Anwendungen darauf achten, die einzelnen Teile separat anzugeben und das Zeichen, das die Bezeichner trennt, nicht anzugeben. Beispielsweise werden durch die folgende Anweisung, um alle Zeilen und Spalten einer xbase-Tabelle auszuwählen, die Namen Catalog (\xbase\sales\corp) und Table (Parts. dbf), aber nicht das Katalog Trennzeichen\\() angezeigt:  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 Mit der folgenden Anweisung können Sie alle Zeilen und Spalten einer Oracle-Tabelle auswählen, die die Namen Catalog (Sales), Schema (Corporate) und Table (Parts), jedoch nicht die-Trennzeichen Catalog (@) oder Schema (.):  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Weitere Informationen über Bezeichner von [Bezeichnern finden](../../../odbc/reference/develop-app/quoted-identifiers.md)Sie im nächsten Abschnitt in Anführungszeichen.
