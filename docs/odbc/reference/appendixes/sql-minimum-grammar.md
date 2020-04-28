---
title: Minimale SQL-Grammatik | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20eee34feadb8e3140f25019ec6b0d036ff02e14
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304991"
---
# <a name="sql-minimum-grammar"></a>Minimale SQL-Grammatik
In diesem Abschnitt wird die minimale SQL-Syntax beschrieben, die ein ODBC-Treiber unterstützen muss. Die in diesem Abschnitt beschriebene Syntax ist eine Teilmenge der Eintrags Ebenen-Syntax von SQL-92.  
  
 Eine Anwendung kann eine beliebige Syntax in diesem Abschnitt verwenden und sicher sein, dass alle ODBC-kompatiblen Treiber diese Syntax unterstützen. Um zu ermitteln, ob zusätzliche Features von SQL-92 nicht in diesem Abschnitt unterstützt werden, sollte die Anwendung **SQLGetInfo** mit dem SQL_SQL_CONFORMANCE Informationstyp aufrufen. Auch wenn der Treiber keinem SQL-92-Konformitäts Grad entspricht, kann eine Anwendung die in diesem Abschnitt beschriebene Syntax weiterhin verwenden. Wenn ein Treiber einer SQL-92-Ebene entspricht, wird auf der anderen Seite alle in dieser Ebene enthaltenen Syntax unterstützt. Dies schließt die Syntax in diesem Abschnitt ein, da die hier beschriebene minimale Grammatik eine rein Teilmenge der niedrigsten SQL-92-Konformitäts Ebene ist. Nachdem die Anwendung die unterstützte SQL-92-Ebene erkannt hat, kann Sie ermitteln, ob ein höheres Funktions Feature (sofern vorhanden) durch Aufrufen von **SQLGetInfo** mit dem einzelnen Informationstyp, der dieser Funktion entspricht, unterstützt wird.  
  
 Treiber, die nur für schreibgeschützte Datenquellen verwendet werden, unterstützen möglicherweise nicht die in diesem Abschnitt enthaltenen Teile der Grammatik, die sich mit dem Ändern von Daten befassen. Eine Anwendung kann ermitteln, ob eine Datenquelle schreibgeschützt ist, indem **SQLGetInfo** mit dem SQL_DATA_SOURCE_READ_ONLY Informationstyp aufgerufen wird.  
  
## <a name="statement"></a>-Anweisung.  
 *CREATE-TABLE-Statement* :: =  
  
 Create Table *Basistabellen Name*  
  
 (*spaltenbezeichnerdatentyp* [*, Spalten-ID-Datentyp*]...)  
  
> [!IMPORTANT]  
>  Als *Datentyp* in einer *CREATE-TABLE-Anweisung*müssen Anwendungen einen Datentyp aus der TYPE_NAME Spalte des Resultsets verwenden, das von **SQLGetTypeInfo**zurückgegeben wurde.  
  
 *Delete-Statement-durchsucht* :: =  
  
 DELETE FROM *Table-Name* [WHERE *Search-Condition*]  
  
 *DROP-TABLE-Statement* :: =  
  
 Drop Table *Basis-Tabellenname*  
  
 *INSERT-Anweisung* :: =  
  
 INSERT INTO *Table-Name* [( *Spalten-* ID [, *Spalten-* ID]...)]      Values (*Insert-Value*[, *Insert-Value*]...)  
  
 *select-statement* ::=  
  
 SELECT [all &#124; verschieden] *Select-List*  
  
 FROM *Table-Reference-List*  
  
 [WHERE *Such Bedingung*]  
  
 [*Order-By-Klausel*]  
  
 *Statement* :: = *CREATE-TABLE-Statement*  
  
 &#124; *Durchsuchen mit DELETE-Anweisung*  
  
 &#124; *DROP-TABLE-Anweisung*  
  
 &#124; *INSERT-Anweisung*  
  
 &#124; *SELECT-Anweisung*  
  
 &#124; *Update-Anweisungs Suche*  
  
 *Update-Anweisung wurde durchsucht*  
  
 *Tabellennamen* aktualisieren  
  
 Set *Column-Identifier* = {*Expression* &#124; NULL}  
  
 [, *Column-Identifier* = {*Expression* &#124; NULL}]...  
  
 [WHERE *Such Bedingung*]  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Elemente, die in SQL-­Anweisungen verwendet werden](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [Datentypunterstützung](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [Parameterdatentypen](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [Parametermarkierungen](../../../odbc/reference/appendixes/parameter-markers.md)
