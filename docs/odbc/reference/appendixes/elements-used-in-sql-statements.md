---
title: In SQL-Anweisungen verwendete Elemente | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], elements supported
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 49a1cd54957426d4d14d84d43df670c8c3d96189
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307021"
---
# <a name="elements-used-in-sql-statements"></a>Elemente, die in SQL-­Anweisungen verwendet werden
Die folgenden Elemente werden in den zuvor aufgeführten SQL-Anweisungen verwendet.  
  
## <a name="element"></a>Element  
 *Base-Table-Bezeichner* ::= *benutzerdefinierter Name*  
  
 *Basis-Tabellenname* ::= *Base-Table-Bezeichner*  
  
 *boolean-Faktor* ::= [NOT] *boolean-primär*  
  
 *boolean-primär* ::= Vergleich *-prädikat* &#124; ( *Suchbedingung* )  
  
 *boolesch-term* ::= *boolean-factor* [AND *boolean-term*]  
  
 *character-string-literal* ::=*''''zeichen*'...'' (*Zeichen* ist ein beliebiges Zeichen im Zeichensatz des Treibers/der Datenquelle. Um ein einzelnes wörtliches Anführungszeichen ('') in ein Zeichen-Zeichenfolgenliteral einzuschließen, verwenden Sie zwei literale Anführungszeichen [''''].)  
  
 *Spaltenbezeichner* ::= *benutzerdefinierter Name*  
  
 *Spaltenname* ::= [*Tabellenname*.] *Spaltenbezeichner*  
  
 *Vergleichsoperator* ::= \< < &#124; > &#124; = &#124; >= &#124; = &#124; <>  
  
 *Vergleichsprädikat* ::= Ausdrucksvergleich-Operator-Ausdruck *expression*  
  
 *data-type* ::= *character-string-type* *(character-string-type* ist ein beliebiger Datentyp, für den die Spalte ""DATA_TYPE"" in dem von SQLGetTypeInfo zurückgegebenen Resultset entweder SQL_CHAR oder SQL_VARCHAR ist.)  
  
 *Ziffer* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; &#124; 7 &#124; 8 &#124; 9  
  
 *dynamischer Parameter* ::= ?  
  
 *Ausdruck* ::= Ausdruck &#124; Ausdrucks ,&#124;-" -Term  
  
 *Faktor* ::=*+* *-*[&#124;]*primär*  
  
 *Insert-Wert* ::=  
  
 *dynamischer Parameter*  
  
 &#124; *wörtlich*  
  
 &#124; NULL  
  
 &#124; USER  
  
 *Buchstabe* ::= *Kleinbuchstaben &#124; Großbuchstaben*  
  
 *Literal* ::= *Zeichen-Zeichenfolge-Literal*  
  
 *Kleinbuchstabe* ::= a &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; h &#124; i &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y &#124; z  
  
 *order-by-clause* ::= ORDER BY *sort-specification* [, *sort-specification*]...  
  
 *Primär ::=* *Spaltenname*  
  
 &#124; *dynamischer Parameter*  
  
 &#124; *wörtlich*  
  
 &#124; ( *Ausdruck* )  
  
 *Suchbedingung* ::= *boolescher Begriff* [ODER *Suchbedingung*]  
  
 *Select-Liste* ::= \* &#124; *Select-Unterliste* [, *Select-Unterliste*]...  (*Auswahlliste* darf keine Parameter enthalten.)  
  
 *select-sublist* ::= *Ausdruck*  
  
 *sort-specification* ::= '*unsigned-integer &#124; column-name*' [*ASC &#124; DESC*]  
  
 *Tabellenbezeichner* ::= *benutzerdefinierter Name*  
  
 *Tabellenname* ::= *Tabellenbezeichner*  
  
 *Tabellenverweis* ::= *Tabellenname*  
  
 *Tabellen-Referenzliste* ::= *Tabellenverweis* [,*Tabellenverweis*]...  
  
 *Begriff* ::= *Faktor* \* &#124; */* *Begriffs* ,&#124;*Faktor*  
  
 *Unsigned-integer* ::=*digit*  
  
 *Großbuchstaben* ::= *A &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; H &#124; J &#124; J &#124; &#124; K &#124; L &#124; &#124; M &#124; N &#124; O &#124; &#124; P &#124; Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; &#124; X &#124; Y &#124; Z*  
  
 *benutzerdefinierter Name* ::= *Buchstabe*[*Ziffer* &#124; *Buchstabe* &#124; *_*]...
