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
manager: craigg
ms.openlocfilehash: 3b26eaeb804f8d92a7122814641cadf5889b77b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161416"
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
|\<table-exp>|{\<provider-command-text>} &#124;<br /><br /> (\<shape-command>) &#124;<br /><br /> Tabelle \<in Anführungszeichen-Name >&#124;<br /><br /> \<quoted-name>|  
|\<shape-action>|APPEND \<Alias-Feld-List >&#124;<br /><br /> COMPUTE- \<Alias-Feld-List > [BY \<Feldliste >]|  
|\<aliased-field-list>|\<Alias-Feld > [, \<Alias-Feld >]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<relation-exp>) &#124;<br /><br /> \<calculated-exp> &#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<Beziehung-Cond-List >|  
|\<relation-cond-list>|\<Relation-Cond-> [, \<Beziehung Cond >...]|  
|\<relation-cond>|\<Feld-Name > für \<untergeordnete-Ref->|  
|\<child-ref>|\<field-name> &#124;<br /><br /> PARAMETER \<Param-Ref->|  
|\<param-ref>|\<number>|  
|\<field-list>|\<Feld-Name > [, \<Feld-Name >]|  
|\<aggregate-exp>|SUM(\<qualified-field-name>) &#124;<br /><br /> AVG(\<qualified-field-name>) &#124;<br /><br /> MIN(\<qualified-field-name>) &#124;<br /><br /> MAX(\<qualified-field-name>) &#124;<br /><br /> COUNT(\<qualified-alias> &#124; \<qualified-name>) &#124;<br /><br /> STDEV(\<qualified-field-name>) &#124;<br /><br /> ANY(\<qualified-field-name>)|  
|\<calculated-exp>|CALC (\<Ausdruck >)|  
|\<qualified-field-name>|\<alias>.[\<alias>...]\<field-name>|  
|\<alias>|\<quoted-name>|  
|\<field-name>|\<in Anführungszeichen-Name > [[AS] \<Alias >]|  
|\<quoted-name>|"\<string>" &#124;<br /><br /> '\<string>' &#124;<br /><br /> [\<string>] &#124;<br /><br /> \<name>|  
|\<qualified-name>|Alias [.alias...]|  
|\<name>|Alpha [Alpha &#124; Ziffer &#124; _ &#124; # &#124; : &#124; ...]|  
|\<number>|Ziffer [Ziffer...]|  
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
