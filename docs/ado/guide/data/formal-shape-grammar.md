---
description: Formale Grammatik für Strukturen
title: Formale Form Grammatik | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO], shape grammar
- data shaping [ADO], shape grammar
ms.assetid: ea691475-0f03-4abe-a785-b77e77712d1d
author: rothja
ms.author: jroth
ms.openlocfilehash: 6a8d92abc3a1b0d7e6d39ac4149c186c5a2fc2eb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453372"
---
# <a name="formal-shape-grammar"></a>Formale Grammatik für Strukturen
Dies ist die formale Grammatik zum Erstellen beliebiger Form Befehle:  
  
-   Erforderliche grammatische Begriffe sind Text Zeichenfolgen, die durch eckige Klammern ("<>") getrennt sind.  
  
-   Optionale Begriffe werden durch eckige Klammern ("[]") getrennt.  
  
-   Alternativen werden durch ein virgul ("&#124;") angezeigt.  
  
-   Sich wiederholende Alternativen werden durch Auslassungs Punkte ("...") angezeigt.  
  
-   *Alpha* gibt eine Zeichenfolge von alphabetischen Buchstaben an.  
  
-   *Ziffer* gibt eine Zeichenfolge mit Zahlen an.  
  
-   *Unicode-Digit* gibt eine Zeichenfolge von Unicode-Ziffern an.  
  
 Alle anderen Begriffe sind Literale.  
  
|Begriff|Definition|  
|----------|----------------|  
|\<shape-command>|Form [[ \<table-exp> [as] \<alias> ]] [ \<shape-action> ]|  
|\<table-exp>|{ \<provider-command-text> } &#124;<br /><br /> ( \<shape-command> ) &#124;<br /><br /> Tabellen \<quoted-name> &#124;<br /><br /> \<quoted-name>|  
|\<shape-action>|&#124; anfügen \<aliased-field-list><br /><br /> Compute \<aliased-field-list> [by \<field-list> ]|  
|\<aliased-field-list>|\<aliased-field> [, \<aliased-field...>]|  
|\<aliased-field>|\<field-exp> [[As] \<alias> ]|  
|\<field-exp>|( \<relation-exp> ) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[As] \<alias> ]<br /><br /> Beziehung \<relation-cond-list>|  
|\<relation-cond-list>|\<relation-cond> [, \<relation-cond>...]|  
|\<relation-cond>|\<field-name> An \<child-ref>|  
|\<child-ref>|\<field-name> &#124;<br /><br /> Parame \<param-ref>|  
|\<param-ref>|\<number>|  
|\<field-list>|\<field-name> [, \<field-name>]|  
|\<aggregate-exp>|Sum ( \<qualified-field-name> )-&#124;<br /><br /> AVG ( \<qualified-field-name> )-&#124;<br /><br /> MIN ( \<qualified-field-name> )-&#124;<br /><br /> Max ( \<qualified-field-name> )-&#124;<br /><br /> Anzahl ( \<qualified-alias> &#124; \<qualified-name> ) &#124;<br /><br /> StDev ( \<qualified-field-name> )-&#124;<br /><br /> Any ( \<qualified-field-name> )|  
|\<calculated-exp>|Calc ( \<expression> )|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<quoted-name>|  
|\<field-name>|\<quoted-name> [[As] \<alias> ]|  
|\<quoted-name>|" \<string> " &#124;<br /><br /> " \<string> " &#124;<br /><br /> [ \<string> ] &#124;<br /><br /> \<name>|  
|\<qualified-name>|Alias [. Alias...]|  
|\<name>|Alpha [alpha &#124; Ziffer &#124; _ &#124; # &#124;: &#124;...]|  
|\<number>|Ziffern [Ziffer...]|  
|\<new-exp>|Neu \<field-type> [( \<number> [, \<number> ])]|  
|\<field-type>|Ein OLE DB-oder ADO-Datentyp.|  
|\<string>|Unicode-Char [Unicode-Char...]|  
|\<expression>|Ein Visual Basic for Applications Ausdruck, dessen Operanden andere nicht-Calc-Spalten in derselben Zeile sind.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Übersicht über die Daten Strukturierung](../../../ado/guide/data/data-shaping-overview.md)   
 [Erforderliche Anbieter für die Daten Strukturierung](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape-APPEND-Klausel](../../../ado/guide/data/shape-append-clause.md)   
 [Shape-Befehle im allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Shape-COMPUTE-Klausel](../../../ado/guide/data/shape-compute-clause.md)   
 [Visual Basic for Applications-Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md)
