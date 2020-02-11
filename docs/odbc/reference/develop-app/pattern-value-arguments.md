---
title: Muster Wert Argumente | Microsoft-Dokumentation
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
ms.openlocfilehash: 53c091fd0b7a6cfdf390997fb5163fbc9d98e18c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023343"
---
# <a name="pattern-value-arguments"></a>Argumente des Musterwerts
Einige Argumente in den Katalog Funktionen, wie z. b. das *TableName* -Argument in **SQLTables**, akzeptieren Suchmuster. Diese Argumente akzeptieren Suchmuster, wenn das SQL_ATTR_METADATA_ID-Anweisungs Attribut auf SQL_FALSE festgelegt ist. Sie sind bezeichnerargumente, die kein Suchmuster akzeptieren, wenn dieses Attribut auf SQL_TRUE festgelegt ist.  
  
 Die Suchmuster Zeichen lauten:  
  
-   Ein Unterstrich (_), der ein beliebiges einzelnes Zeichen darstellt.  
  
-   Ein Prozentzeichen (%), das eine beliebige Sequenz von NULL oder mehr Zeichen darstellt.  
  
-   Ein Escapezeichen, das Treiber spezifisch ist und verwendet wird, um Unterstriche, Prozentzeichen und das Escapezeichen als Literale einzuschließen. Wenn das Escapezeichen vor einem nicht-Sonderzeichen steht, hat das Escapezeichen keine besondere Bedeutung. Wenn das Escapezeichen einem Sonderzeichen vorangestellt ist, wird es mit Escapezeichen versehen. "\A" würde z. b. als zwei Zeichen behandelt werden:\\"" und "a", "\\%" wird jedoch als nicht spezielles einzelnes Zeichen "%" behandelt.  
  
 Das Escapezeichen wird mit der SQL_SEARCH_PATTERN_ESCAPE-Option in **SQLGetInfo**abgerufen. Sie muss vor allen unterstrichen, Prozentzeichen oder Escapezeichen in einem Argument stehen, das Suchmuster annimmt, um das Zeichen als Literalzeichen einzuschließen. Beispiele sind in der folgenden Tabelle aufgeführt.  
  
|Suchmuster|BESCHREIBUNG|  
|--------------------|-----------------|  
|Ein|Alle Bezeichner, die den Buchstaben A enthalten.|  
|ABC_|Alle vier Zeichen Bezeichner, die mit ABC beginnen|  
|ABC\\_|Der Bezeichner abc_, vorausgesetzt, das Escapezeichen ist\\ein umgekehrter Schrägstrich ()|  
|\\\\%|Alle Bezeichner, die mit einem umgekehrten schräg\\Strich () beginnen, vorausgesetzt, das Escapezeichen ist ein umgekehrter Schrägstrich|  
  
 Es muss besonders darauf geachtet werden, dass Suchmuster Zeichen in Argumenten, die Suchmuster akzeptieren, umgangen werden. Dies gilt insbesondere für den Unterstrich, der häufig in bezeichlern verwendet wird. Ein häufiger Fehler in Anwendungen besteht darin, einen Wert aus einer Katalog Funktion abzurufen und diesen Wert an ein Suchmuster Argument in einer anderen Katalog Funktion zu übergeben. Nehmen wir beispielsweise an, dass eine Anwendung den Tabellennamen MY_TABLE aus dem Resultset für **SQLTables** abruft und diese an **SQLColumns** übergibt, um eine Liste der Spalten in MY_TABLE abzurufen. Anstatt die Spalten für MY_TABLE zu erhalten, erhält die Anwendung die Spalten für alle Tabellen, die dem Suchmuster MY_TABLE entsprechen, z. b. MY_TABLE, MY1TABLE, MY2TABLE usw.  
  
> [!NOTE]
>  ODBC 2. *x* -Treiber unterstützen keine Suchmuster im *CatalogName* -Argument in **SQLTables**. ODBC 3 *. x* -Treiber akzeptieren Suchmuster in diesem Argument, wenn das SQL_ATTR_ ODBC_VERSION Environment-Attribut auf "SQL_OV_ODBC3" festgelegt ist. Sie akzeptieren keine Suchmuster in diesem Argument, wenn Sie auf SQL_OV_ODBC2 festgelegt ist.  
  
 Durch die Übergabe eines NULL-Zeigers an ein Suchmuster Argument wird die Suche nach diesem Argument nicht eingeschränkt. Das heißt, ein NULL-Zeiger und das Suchmuster% (beliebige Zeichen) sind gleichwertig. Ein Suchmuster der Länge 0 (null), d. h. ein gültiger Zeiger auf eine Zeichenfolge mit einer Länge von 0 (null) entspricht nur der leeren Zeichenfolge ("").
