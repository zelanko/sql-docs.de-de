---
title: SQL-Mindestgrammatik | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304991"
---
# <a name="sql-minimum-grammar"></a>Minimale SQL-Grammatik
In diesem Abschnitt wird die minimale SQL-Syntax beschrieben, die ein ODBC-Treiber unterstützen muss. Die in diesem Abschnitt beschriebene Syntax ist eine Teilmenge der Syntax der Einstiegsebene von SQL-92.  
  
 Eine Anwendung kann eine beliebige Syntax in diesem Abschnitt verwenden und sicher sein, dass jeder ODBC-kompatible Treiber diese Syntax unterstützt. Um zu bestimmen, ob zusätzliche Features von SQL-92, die nicht in diesem Abschnitt enthalten sind, unterstützt werden, sollte die Anwendung **SQLGetInfo** mit dem SQL_SQL_CONFORMANCE-Informationstyp aufrufen. Auch wenn der Treiber keiner SQL-92-Konformitätsstufe entspricht, kann eine Anwendung weiterhin die in diesem Abschnitt beschriebene Syntax verwenden. Wenn ein Treiber einer SQL-92-Ebene entspricht, unterstützt er hingegen die gesamte Syntax, die in dieser Ebene enthalten ist. Dies schließt die Syntax in diesem Abschnitt ein, da die hier beschriebene minimale Grammatik eine reine Teilmenge der niedrigsten SQL-92-Konformitätsebene ist. Sobald die Anwendung die unterstützte SQL-92-Ebene kennt, kann sie feststellen, ob ein Feature auf höherer Ebene (falls vorhanden) unterstützt wird, indem **SQLGetInfo** mit dem einzelnen Informationstyp aufgerufen wird, der diesem Feature entspricht.  
  
 Treiber, die nur mit schreibgeschützten Datenquellen arbeiten, unterstützen möglicherweise nicht die In diesem Abschnitt enthaltenen Teile der Grammatik, die sich mit dem Ändern von Daten befassen. Eine Anwendung kann feststellen, ob eine Datenquelle schreibgeschützt ist, indem **sie SQLGetInfo** mit dem SQL_DATA_SOURCE_READ_ONLY-Informationstyp aufruft.  
  
## <a name="statement"></a>-Anweisung.  
 *create-table-Anweisung* ::=  
  
 CREATE TABLE *Basistabellenname*  
  
 (*Spaltenbezeichner-Datentyp* [*,spalten-bezeichner-Datentyp*]...)  
  
> [!IMPORTANT]  
>  Als *Datentyp* in einer *create-table-statement*müssen Anwendungen einen Datentyp aus der TYPE_NAME Spalte des von **SQLGetTypeInfo**zurückgegebenen Resultsets verwenden.  
  
 *delete-statement-searched* ::=  
  
 DELETE FROM *Tabellenname* [WHERE *Suchbedingung*]  
  
 *drop-table-Anweisung* ::=  
  
 DROP TABLE *Basistabellenname*  
  
 *Insert-Anweisung* ::=  
  
 INSERT INTO *Tabellenname* [( *Spaltenbezeichner* [, *Spaltenbezeichner*]...)]      VALUES (*Einfügewert*[, *Einfügewert*]... )  
  
 *select-statement* ::=  
  
 SELECT [ALL &#124; DISTINCT] *Auswahlliste*  
  
 Aus *Tabellen-Referenzliste*  
  
 [WHERE *Suchbedingung*]  
  
 [*Reihenfolge nach Klausel*]  
  
 *Anweisung* ::= *create-table-statement*  
  
 &#124; *delete-statement-searched*  
  
 &#124; *Drop-Table-Anweisung*  
  
 &#124; *Insert-Anweisung*  
  
 &#124; *Select-Anweisung*  
  
 &#124; *Update-Statement-gesucht*  
  
 *update-statement-searched*  
  
 *UPDATE-Tabellenname*  
  
 *SET-Spaltenbezeichner* =*Ausdruck* &#124; NULL  
  
 [, *spalten-identifier* = '*Ausdruck* &#124; NULL']...  
  
 [WHERE *Suchbedingung*]  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Elemente, die in SQL-­Anweisungen verwendet werden](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [Datentyp-Unterstützung](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [Parameterdatentypen](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [Parametermarkierungen](../../../odbc/reference/appendixes/parameter-markers.md)
