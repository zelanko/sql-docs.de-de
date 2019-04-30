---
title: Katalogposition | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22a9a9d50891a6101076af6378fb33543274b21b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63237940"
---
# <a name="catalog-position"></a>Katalogposition
Die Position des ein Katalogname in einem Bezeichner und wie sie vom Rest des Bezeichners getrennt ist, aus der Datenquelle zu Datenquelle variiert. Z. B. in einer Xbase-Datenquelle, der Name des Katalogs ist ein Verzeichnis und in Microsoft® Windows®, werden getrennt aus dem Tabellennamen (d.h. ein Dateiname) ein umgekehrter Schrägstrich (\\). Die folgende Abbildung zeigt dies.  
  
 ![Katalogposition: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 Der Katalog in einer SQL Server-Datenquelle ist eine Datenbank und wird aus dem Schema und Tabellennamen durch einen Punkt (.) getrennt.  
  
 ![Katalogposition: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 In einer Oracle-Datenquelle, der Katalog wird auch die Datenbank jedoch den Namen der Tabelle folgt, und wird getrennt von den Schema- und Tabellennamen die Namen von einem at-Zeichen (@).  
  
 ![Katalogposition: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Um das Katalogtrennzeichen und den Speicherort der der Name des Katalogs zu ermitteln, eine Anwendung ruft **SQLGetInfo** mit den Optionen SQL_CATALOG_NAME_SEPARATOR und SQL_CATALOG_LOCATION. Interoperable Anwendungen ausführen können sollten Bezeichner nach diesen Werten erstellen.  
  
 Zitieren von Bezeichnern, die über mehrere Teile enthalten, müssen Anwendungen darauf achten, dass jeder Teil separat Anführungszeichen und nicht das Zeichen, das die Bezeichner trennt, in Anführungszeichen sein. Die folgende Anweisung hinzu, wählen Sie alle Zeilen und Spalten einer Xbase-Tabelle z. B. Anführungszeichen, der Katalog (\XBASE\SALES\CORP) und Tabellennamen (Parts.dbf), aber nicht das Katalogtrennzeichen (\\):  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 Die folgende Anweisung alle Zeilen und Spalten von einer Oracle-Tabelle auswählen (Sales) Katalog, Schema (Unternehmen), und Tabellennamen (Teile), aber nicht über den Katalog zu Anführungszeichen (@) oder Trennzeichen für Schema (.):  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Informationen über Bezeichner finden Sie im nächsten Abschnitt [Bezeichner in Anführungszeichen](../../../odbc/reference/develop-app/quoted-identifiers.md).
