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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789268"
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
|\<table-exp>|{\<Anbieter Befehlstext >}&#124;<br /><br /> (\<Shape-Befehl >)&#124;<br /><br /> Tabelle \<in Anführungszeichen-Name >&#124;<br /><br /> \<in Anführungszeichen-Name >|  
|\<Shape-Action >|APPEND \<Alias-Feld-List >&#124;<br /><br /> COMPUTE- \<Alias-Feld-List > [BY \<Feldliste >]|  
|\<aliased-field-list>|\<Alias-Feld > [, \<Alias-Feld >]|  
|\<aliased-field>|\<field-exp> [[AS] \<alias>]|  
|\<field-exp>|(\<Beziehung: "exp" >)&#124;<br /><br /> \<berechnet "exp" >&#124;<br /><br /> \<aggregate-exp> &#124;<br /><br /> \<new-exp>|  
|<relation_exp>|\<table-exp> [[AS] \<alias>]<br /><br /> RELATE \<Beziehung-Cond-List >|  
|\<relation-cond-list>|\<Relation-Cond-> [, \<Beziehung Cond >...]|  
|\<relation-cond>|\<Feld-Name > für \<untergeordnete-Ref->|  
|\<child-ref>|\<Feld-Name >&#124;<br /><br /> PARAMETER \<Param-Ref->|  
|\<param-ref>|\<Anzahl >|  
|\<field-list>|\<Feld-Name > [, \<Feld-Name >]|  
|\<aggregate-exp>|SUM (\<qualifizierten-Feld-Name >)&#124;<br /><br /> AVG (\<qualifizierten-Feld-Name >)&#124;<br /><br /> MIN (\<qualifizierten-Feld-Name >)&#124;<br /><br /> MAX (\<qualifizierten-Feld-Name >)&#124;<br /><br /> COUNT (\<qualifizierten-Alias > &#124; \<qualifizierte Name >)&#124;<br /><br /> STDEV (\<qualifizierten-Feld-Name >)&#124;<br /><br /> Alle (\<qualifizierten-Feld-Name >)|  
|\<calculated-exp>|CALC (\<Ausdruck >)|  
|\<qualifizierte-Feld-Name >|\<Alias >. [\<Alias >...] \<Feldnamen >|  
|\<alias>|\<in Anführungszeichen-Name >|  
|\<Feld-Name >|\<in Anführungszeichen-Name > [[AS] \<Alias >]|  
|\<in Anführungszeichen-Name >|"\<String >"&#124;<br /><br /> "\<String >"&#124;<br /><br /> [\<Zeichenfolge >]&#124;<br /><br /> \<Name >|  
|\<Vollständiger Name >|Alias [.alias...]|  
|\<Name >|Alpha [Alpha &#124; Ziffer &#124; _ &#124; # &#124; : &#124; ...]|  
|\<Anzahl >|Ziffer [Ziffer...]|  
|\<new-exp>|NEUE \<Feldtyp > [(\<Anzahl > [, \<Anzahl >])]|  
|\<field-type>|Ein OLE DB oder ADO-Datentyp.|  
|\<Zeichenfolge >|Unicode-Zeichen [Unicode-Zeichen...]|  
|\<Ausdruck >|Eine Visual Basic für Applikationen-Ausdruck, deren Operanden andere nicht-CALC-Spalten in der gleichen Zeile sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Daten strukturieren (Übersicht)](../../../ado/guide/data/data-shaping-overview.md)   
 [Erforderliche Anbieter für die Strukturierung der Daten](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape APPEND-Klausel](../../../ado/guide/data/shape-append-clause.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Shape COMPUTE-Klausel](../../../ado/guide/data/shape-compute-clause.md)   
 [Visual Basic for Applications-Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md)
