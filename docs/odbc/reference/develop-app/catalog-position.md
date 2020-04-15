---
title: Katalogposition | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303381"
---
# <a name="catalog-position"></a>Katalogposition
Die Position eines Katalognamens in einem Bezeichner und die Trennung vom Rest des Bezeichners variiert von Datenquelle zu Datenquelle. In einer Xbase-Datenquelle ist der Katalogname beispielsweise ein Verzeichnis und wird in Microsoft® Windows® durch einen umgekehrten Schrägstrich\\( ) vom Tabellennamen (der ein Dateiname ist) getrennt. Die folgende Abbildung veranschaulicht diese Bedingung.  
  
 ![Katalogposition: Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 In einer SQL Server-Datenquelle ist der Katalog eine Datenbank und wird durch einen Punkt (.) von den Schema- und Tabellennamen getrennt.  
  
 ![Katalogposition: SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 In einer Oracle-Datenquelle ist der Katalog auch die Datenbank, folgt jedoch dem Tabellennamen und wird durch ein at-Zeichen vom Schema und den Tabellennamen getrennt.  
  
 ![Katalogposition: Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Um das Katalogtrennzeichen und den Speicherort des Katalognamens zu bestimmen, ruft eine Anwendung **SQLGetInfo** mit den Optionen SQL_CATALOG_NAME_SEPARATOR und SQL_CATALOG_LOCATION auf. Interoperable Anwendungen sollten Bezeichner gemäß diesen Werten erstellen.  
  
 Beim Zitieren von Bezeichnern, die mehr als ein Teil enthalten, müssen Anwendungen darauf achten, jedes Teil separat zu zitieren und nicht das Zeichen zu zitieren, das die Bezeichner trennt. Die folgende Anweisung zum Auswählen aller Zeilen und Spalten einer Xbase-Tabelle zitiert z. B. die Namen des Katalogs (XBASE-SALES-CORP) und der Tabelle (Parts.dbf), jedoch nicht den Katalogtrennzeichen (\\):  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 Die folgende Anweisung zum Auswählen aller Zeilen und Spalten einer Oracle-Tabelle zitiert die Namen Katalog (Verkauf), Schema (Unternehmen) und Tabelle (Teile), nicht jedoch die Katalog- oder Schematrennzeichen:  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Weitere Informationen zum Angeben von Bezeichnern finden Sie im nächsten [Abschnitt, Quoted Identifiers](../../../odbc/reference/develop-app/quoted-identifiers.md).
