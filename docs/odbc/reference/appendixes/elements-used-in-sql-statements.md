---
title: In SQL-Anweisungen verwendete Elemente | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307021"
---
# <a name="elements-used-in-sql-statements"></a>Elemente, die in SQL-­Anweisungen verwendet werden
Die folgenden Elemente werden in den zuvor aufgeführten SQL-Anweisungen verwendet.  
  
## <a name="element"></a>Element  
 *base-table-Identifier* :: = *benutzerdefinierter Name*  
  
 *base-table-Name* :: = *base-table-Identifier*  
  
 *boolescher Faktor* :: = [nicht] *Boolean-primär*  
  
 *Boolean-Primary* :: = Comparison *-Predicate* &#124; ( *Such Bedingung* )  
  
 *Boolean-Term* :: = *boolescher Faktor* [und *boolescher*Ausdruck]  
  
 *Character-String-Literale* :: = ' ' {*Character*}... ' ' (*Zeichen* ist ein beliebiges Zeichen im Zeichensatz des Treibers bzw. der Datenquelle. Verwenden Sie zwei Literale Anführungszeichen [' ' ' '], um ein einzelnes Anführungszeichen (' ') in ein Zeichenfolgenliteralzeichen einzufügen.  
  
 *Column-Identifier* :: = *benutzerdefinierter Name*  
  
 *Column-Name* :: = [*Tabellenname*] *Spalten Bezeichner*  
  
 *Comparison-Operator* :: = < &#124; > &#124; \<= &#124; >= &#124; = &#124; <>  
  
 *Comparison-Predicate* :: = *Expression* Comparison-Operator Ausdruck  
  
 *Data-Type* :: = *Character-String-type* (*Zeichen folgen vom Typ Zeichenfolge* ) ist ein beliebiger Datentyp, für den die Spalte "" data_type "" im Resultset, das von SQLGetTypeInfo zurückgegeben wurde, entweder SQL_CHAR oder SQL_VARCHAR ist.)  
  
 *Ziffer* :: = 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9  
  
 *Dynamic-Parameter* :: =?  
  
 *Expression* :: = Term &#124; Ausdruck {+&#124;-} Term  
  
 *Faktor* :: = [*+*&#124;*-*]*primär*  
  
 *Insert-Value* :: =  
  
 *Dynamic-Parameter*  
  
 &#124; *Literale*  
  
 &#124; NULL  
  
 &#124; Benutzer  
  
 *Buchstabe* :: = *Kleinbuchstabe &#124; groß* Buchstaben  
  
 *Literalzeichen* :: = *Zeichen folgen Literale*  
  
 *klein* Buchstaben:: = a &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; h &#124; &#124; &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y z  
  
 *Order-by-clause* :: = Order by *Sort-Specification* [, *Sort-Specification*]...  
  
 *Primary* :: = *Spaltenname*  
  
 *Dynamische Parameter* &#124;  
  
 &#124; *Literale*  
  
 &#124; ( *Ausdruck* )  
  
 *Search-Condition* :: = *Boolean-Term* [oder *Search-Condition*]  
  
 *Select-List* :: = \* &#124; *Select-unterst* [, *Select-subList*]...  (*Select-List* darf keine Parameter enthalten.)  
  
 *Select-subList* :: =- *Ausdruck*  
  
 *Sort-Specification* :: = {*unsigned-Integer &#124; Spaltenname*} [*ASC &#124;* Debug]  
  
 *Table-Identifier* :: = *benutzerdefinierter Name*  
  
 *Table-Name* :: = *Table-Identifier*  
  
 *Table-Reference* :: = *Tabellenname*  
  
 *Table-Reference-List* :: = *Tabellen Verweis* [,*Tabellen Verweis*]...  
  
 *Begriff* :: = *Faktor* &#124; *Begriff* {\*&#124;*/*} *Faktor*  
  
 *unsigned-Integer* :: = {*Digit*}  
  
 *groß* Buchstaben:: = *A &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; H &#124; I &#124; J &#124; K &#124; L &#124; M &#124; N &#124; O &#124; P &#124; Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; X &#124; Y &#124; Z*  
  
 *benutzerdefinierter Name* :: = *Letter*[*Digit* &#124; *Letter* &#124; *_*]...
