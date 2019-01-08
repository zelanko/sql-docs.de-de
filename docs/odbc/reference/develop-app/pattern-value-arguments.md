---
title: Value-Argumenten des Musters | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f4a32d9ab637de5b52466cfcb628a57ff6c044b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53208330"
---
# <a name="pattern-value-arguments"></a>Argumente des Musterwerts
Einige Argumente im Katalog-Funktionen, wie die *TableName* -Argument in **SQLTables**, Suchmuster akzeptieren. Diese Argumente akzeptieren, Suchmuster, wenn das SQL_ATTR_METADATA_ID-Anweisungsattribut auf SQL_FALSE; festgelegt ist Sie sind bezeichnerargumente, die einem Suchmuster nicht akzeptiert werden, wenn dieses Attribut auf SQL_TRUE festgelegt ist.  
  
 Die Suchzeichenfolge für die Muster sind:  
  
-   Ein Unterstrich (_), der einem beliebigen einzelnes Zeichen darstellt.  
  
-   Ein Prozentzeichen (%), die eine beliebige Sequenz von NULL oder mehr Zeichen darstellt.  
  
-   Ein Escapezeichen verwenden, die treiberspezifische und wird verwendet, um die Unterstriche enthalten, enthalten Prozent anmeldet, und das Escapezeichen als Literale. Wenn das Escape-Zeichen ein Zeichen nicht spezieller vorangestellt ist, hat das Escape-Zeichen keine besondere Bedeutung. Wenn das Escape-Zeichen ein Sonderzeichen vorangeht, Escapezeichen, die Sonderzeichen enthalten. Z. B. "\a" als zwei Zeichen behandelt werden würde "\\" und "a", aber "\\%" als einzelnes Zeichen "%" nicht spezieller behandelt werden sollen.  
  
 Das Escapezeichen wird abgerufen, mit der Option SQL_SEARCH_PATTERN_ESCAPE **SQLGetInfo**. Es muss Unterstriche, Prozentzeichen oder Escape-Zeichen in einem Argument vorangestellt sein, das Suchmuster enthält das Zeichen als Literal akzeptiert. Beispiele sind in der folgenden Tabelle gezeigt.  
  
|Suchmuster|Description|  
|--------------------|-----------------|  
|%A %|Alle Bezeichner, die mit dem Buchstaben A|  
|ABC_|Alle aus vier Buchstaben bestehende Bezeichner ab, die mit ABC|  
|ABC\\_|Der Bezeichner ABC_, vorausgesetzt das Escapezeichen ist ein umgekehrter Schrägstrich (\\)|  
|\\\\%|Alle IDs beginnen mit einem umgekehrten Schrägstrich (\\), sofern das Escapezeichen ist ein umgekehrter Schrägstrich|  
  
 Spezielle muss darauf geachtet werden Muster der Suchzeichenfolge in-Argumente mit Escapezeichen versehen, die Suchmuster zu akzeptieren. Dies gilt insbesondere für den Unterstrich, der häufig in Bezeichnern verwendet wird. Ein häufiger Fehler in Anwendungen ist das Abrufen eines Werts aus einer Katalogfunktion, und übergeben Sie diesen Wert auf ein Suchmusterargument in einer anderen Katalogfunktion. Nehmen wir beispielsweise an, die eine Anwendung ruft den Namen der Tabelle MY_TABLE aus dem Ergebnis legen Sie für **SQLTables** und übergibt Sie diese Option, um **SQLColumns** zum Abrufen einer Liste der Spalten im MY_TABLE. Anstelle der Spalten für MY_TABLE abrufen, erhalten die Anwendung die Spalten für alle Tabellen, die das Suchmuster MY_TABLE, z. B. MY_TABLE, MY1TABLE, MY2TABLE und So weiter zu entsprechen.  
  
> [!NOTE]
>  ODBC-2. *x* Treiber unterstützen keine Suchmuster in der *CatalogName* -Argument in **SQLTables**. ODBC 3.*.x* Treiber Suchmustern, die in diesem Argument akzeptieren, wenn umgebungsattributs SQL_ATTR_ ODBC_VERSION auf SQL_OV_ODBC3 festgelegt ist; sie akzeptieren keine Suchmustern, die in diesem Argument, wenn er auf SQL_OV_ODBC2 festgelegt ist.  
  
 Übergeben einen null-Zeiger auf ein Suchmusterargument schränkt die Suche für dieses Argument nicht; d. h. sind ein null-Zeiger und die Suche Muster% (Zeichen) Äquivalent. Eine Zeichenfolge der Länge Null Suchmuster – d. h. ein gültiger Zeiger auf eine Zeichenfolge der Länge 0 (null) - entspricht jedoch nur die leere Zeichenfolge ("").
