---
title: Musterwert-Argumente | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], pattern value
- pattern value arguments [ODBC]
ms.assetid: 1d3f0ea6-87af-4836-807f-955e7df2b5df
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0b8e7b7de64d8051118089a54cf14eb45dc96f74
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282380"
---
# <a name="pattern-value-arguments"></a>Argumente des Musterwerts
Einige Argumente in den Katalogfunktionen, z. B. das *TableName-Argument* in **SQLTables**, akzeptieren Suchmuster. Diese Argumente akzeptieren Suchmuster, wenn das SQL_ATTR_METADATA_ID Anweisungsattribut auf SQL_FALSE festgelegt ist. Sie sind Bezeichnerargumente, die kein Suchmuster akzeptieren, wenn dieses Attribut auf SQL_TRUE festgelegt ist.  
  
 Die Suchmusterzeichen sind:  
  
-   Ein Unterstrich (_), der ein beliebiges einzelnes Zeichen darstellt.  
  
-   Ein Prozentzeichen (%), das eine beliebige Folge von null oder mehr Zeichen darstellt.  
  
-   Ein Fluchtzeichen, das fahrerspezifisch ist und verwendet wird, um Unterstriche, Prozentzeichen und das Escapezeichen als Literale einzuschließen. Wenn das Escape-Zeichen einem nicht-besonderen Zeichen vorausgeht, hat das Escape-Zeichen keine besondere Bedeutung. Wenn das Escape-Zeichen einem Sonderzeichen vorausgeht, entgeht es dem Sonderzeichen. Beispielsweise würde "a" als zwei Zeichen behandelt\\werden, " "\\und "a", aber " %" würde als das nicht-spezielle EinzelneZeichen "%" behandelt werden.  
  
 Das Escapezeichen wird mit der Option SQL_SEARCH_PATTERN_ESCAPE in **SQLGetInfo**abgerufen. Es muss jedem Unterstrich, einem Prozentzeichen oder einem Escapezeichen in einem Argument vorangehen, das Suchmuster akzeptiert, um dieses Zeichen als Literal einzuschließen. Beispiele sind in der folgenden Tabelle dargestellt.  
  
|Suchmuster|Beschreibung|  
|--------------------|-----------------|  
|%A%|Alle Bezeichner, die den Buchstaben A enthalten|  
|ABC_|Alle vier Zeichenbezeichner, die mit ABC beginnen|  
|ABC\\_|Der Bezeichner ABC_, vorausgesetzt, das\\Escapezeichen ist ein umgekehrter Schrägstrich ( )|  
|\\\\%|Alle Bezeichner, die mit\\einem umgekehrten Schrägstrich ( ) beginnen, vorausgesetzt, das Escapezeichen ist ein umgekehrter Schrägstrich|  
  
 Besondere Vorsicht ist geboten, um Suchmusterzeichen in Argumenten zu entkommen, die Suchmuster akzeptieren. Dies gilt insbesondere für das Unterstrichzeichen, das häufig in Bezeichnern verwendet wird. Ein häufiger Fehler in Anwendungen besteht darin, einen Wert aus einer Katalogfunktion abzurufen und diesen Wert an ein Suchmusterargument in einer anderen Katalogfunktion zu übergeben. Angenommen, eine Anwendung ruft den Tabellennamen MY_TABLE aus dem Resultset für **SQLTables** ab und übergibt diesen an **SQLColumns,** um eine Liste von Spalten in MY_TABLE abzurufen. Anstatt die Spalten für MY_TABLE abzubekommen, erhält die Anwendung die Spalten für alle Tabellen, die dem Suchmuster MY_TABLE entsprechen, z. B. MY_TABLE, MY1TABLE, MY2TABLE usw.  
  
> [!NOTE]
>  ODBC 2. *x-Treiber* unterstützen keine Suchmuster im *Argument CatalogName* in **SQLTables**. ODBC 3 *.x-Treiber* akzeptieren Suchmuster in diesem Argument, wenn das SQL_ATTR_ ODBC_VERSION Umgebungsattribut auf SQL_OV_ODBC3 festgelegt ist. Sie akzeptieren keine Suchmuster in diesem Argument, wenn es auf SQL_OV_ODBC2 festgelegt ist.  
  
 Das Übergeben eines Nullzeigers an ein Suchmusterargument schränkt die Suche nach diesem Argument nicht ein. D. h., ein Nullzeiger und das Suchmuster % (alle Zeichen) sind äquivalent. Ein Suchmuster mit einer Länge von null - d. h. ein gültiger Zeiger auf eine Zeichenfolge mit der Länge Null - entspricht jedoch nur der leeren Zeichenfolge ("").
