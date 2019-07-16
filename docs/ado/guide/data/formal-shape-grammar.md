---
title: Formale Grammatik für Formen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91bdf0cfbfe87075d2c9484bca7edd835a950ee6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925348"
---
# <a name="formal-shape-grammar"></a>Formale Grammatik für Strukturen
Dies ist die formale Grammatik für die Erstellung von Shape-Befehlen:  
  
-   Erforderliche grammatische Begriffe sind Textzeichenfolgen, die durch die spitzen Klammern ("<>") getrennt.  
  
-   Optionale Ausdrücke werden durch eckige Klammern ("[]") getrennt.  
  
-   Alternativen sind gekennzeichnet durch einen Schrägstrich ("&#124;").  
  
-   Sich wiederholende alternativen werden durch ein Auslassungszeichen ("…") angegeben.  
  
-   *Alpha* gibt eine Zeichenfolge von Buchstaben.  
  
-   *Ziffer* gibt eine Zeichenfolge von Zahlen.  
  
-   *Unicode-Ziffern* gibt eine Zeichenfolge von Unicode-Ziffern.  
  
 Alle anderen Begriffe sind Literale.  
  
|Begriff|Definition|  
|----------|----------------|  
|\<shape-command>|Form vom Typ [\<Tabelle-"exp" > [[AS] \<Alias >]] [\<Form Action->]|  
|\<table-exp>|{\<provider-command-text>} &#124;<br /><br /> (\<shape-command>) &#124;<br /><br /> Tabelle \<in Anführungszeichen-Name >&#124;<br /><br /> \<in Anführungszeichen-Name >|  
|\<shape-action>|APPEND \<Alias-Feld-List >&#124;<br /><br /> COMPUTE- \<Alias-Feld-List > [BY \<Feldliste >]|  
|\<aliased-field-list>|\<Alias-Feld > [, \<Alias-Feld >]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<Beziehung-Cond-List >|  
|\<relation-cond-list>|\<Relation-Cond-> [, \<Beziehung Cond >...]|  
|\<relation-cond>|\<Feld-Name > für \<untergeordnete-Ref->|  
|\<child-ref>|\<field-name> &#124;<br /><br /> PARAMETER \<Param-Ref->|  
|\<param-ref>|\<Anzahl >|  
|\<field-list>|\<Feld-Name > [, \<Feld-Name >]|  
|\<aggregate-exp>|SUM (\<qualifizierten-Feld-Name >)&#124;<br /><br /> AVG (\<qualifizierten-Feld-Name >)&#124;<br /><br /> MIN(\<qualified-field-name>) &#124;<br /><br /> MAX (\<qualifizierten-Feld-Name >)&#124;<br /><br /> COUNT (\<qualifizierten-Alias > &#124; \<qualifizierte Name >)&#124;<br /><br /> STDEV(\<qualified-field-name>) &#124;<br /><br /> Alle (\<qualifizierten-Feld-Name >)|  
|\<calculated-exp>|CALC (\<Ausdruck >)|  
|\<qualifizierte-Feld-Name >|\<Alias >. [\<Alias >...] \<Feldnamen >|  
|\<alias>|\<in Anführungszeichen-Name >|  
|\<Feld-Name >|\<in Anführungszeichen-Name > [[AS] \<Alias >]|  
|\<in Anführungszeichen-Name >|"\<string>" &#124;<br /><br /> "\<String >"&#124;<br /><br /> [\<Zeichenfolge >]&#124;<br /><br /> \<Name >|  
|\<Vollständiger Name >|Alias [.alias...]|  
|\<Name >|Alpha [Alpha &#124; Ziffer &#124; _ &#124; # &#124; : &#124; ...]|  
|\<Anzahl >|Ziffer [Ziffer...]|  
|\<new-exp>|NEUE \<Feldtyp > [(\<Anzahl > [, \<Anzahl >])]|  
|\<field-type>|Ein OLE DB oder ADO-Datentyp.|  
|\<string>|Unicode-Zeichen [Unicode-Zeichen...]|  
|\<expression>|Eine Visual Basic für Applikationen-Ausdruck, deren Operanden andere nicht-CALC-Spalten in der gleichen Zeile sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Daten strukturieren (Übersicht)](../../../ado/guide/data/data-shaping-overview.md)   
 [Erforderliche Anbieter für die Strukturierung der Daten](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape APPEND-Klausel](../../../ado/guide/data/shape-append-clause.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Shape COMPUTE-Klausel](../../../ado/guide/data/shape-compute-clause.md)   
 [Visual Basic for Applications-Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md)
