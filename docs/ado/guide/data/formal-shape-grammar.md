---
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
ms.openlocfilehash: ce65f6961502a5bfe43278e4a29a11c4210d4af8
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758256"
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
|\<Shape-Befehls>|Form [ \< Table-Exp> [[as] \< Alias>]] [ \< Shape-Action>]|  
|\<Table-Exp->|{ \< Provider-Command-Text>} &#124;<br /><br /> ( \< Shape-Command>) &#124;<br /><br /> Tabelle in Anführungszeichen \< -Name> &#124;<br /><br /> \<> in Anführungszeichen|  
|\<Shape-Aktions>|Anfügen von \< Aliasing-field-list-> &#124;<br /><br /> Compute \< -Aliasing-Feld-List-> [nach \< Feldliste>]|  
|\<Aliasing-field-list->|\<Aliasing-Feld> [, \< Alias-Field... >]|  
|\<Aliasing-Feld>|\<Field-Exp> [[as] \< Alias>]|  
|\<Field-Exp->|( \< Relation-Exp>) &#124;<br /><br /> \<> &#124; "berechnet-Exp"<br /><br /> \<Aggregat-Exp-> &#124;<br /><br /> \<New-Exp->|  
|<relation_exp>|\<Table-Exp> [[as] \< Alias>]<br /><br /> \<Beziehung verknüpfen-> der Liste|  
|\<Relation-Liste der>|\<Relation-der-> [, \< Relation->...]|  
|\<Relation-->|\<Feldname> zu untergeordnetem Verweis \<>|  
|\<untergeordnete Ref>|\<Feldname> &#124;<br /><br /> Parameter \< param-Ref>|  
|\<param-Ref->|\<Anzahl>|  
|\<> der Feldliste|\<Feldname> [, \< Feldname>]|  
|\<Aggregat-Exp->|Sum ( \< qualified-Field-Name>) &#124;<br /><br /> AVG ( \< qualified-Field-Name>) &#124;<br /><br /> MIN ( \< qualified-Field-Name>) &#124;<br /><br /> Max ( \< qualified-Field-Name>) &#124;<br /><br /> COUNT ( \< qualified-Alias> &#124; \< Qualified-Name>) &#124;<br /><br /> StDev ( \< qualified-Field-Name>) &#124;<br /><br /> Any ( \< qualified-Field-Name>)|  
|\<> "berechnet-Exp"|Calc ( \< Ausdrucks>)|  
|\<Qualified-Field-Name>|\<Alias>. [ \< Alias>...] \< Feldname>|  
|\<Alias>|\<> in Anführungszeichen|  
|\<Feldname>|\<Anführungszeichen-Name> [[as] \< Alias>]|  
|\<> in Anführungszeichen|" \< String>" &#124;<br /><br /> " \< String>" &#124;<br /><br /> [ \< String>] &#124;<br /><br /> \<Name>|  
|\<qualifizierter Name>|Alias [. Alias...]|  
|\<Name>|Alpha [alpha &#124; Ziffer &#124; _ &#124; # &#124;: &#124;...]|  
|\<Anzahl>|Ziffern [Ziffer...]|  
|\<New-Exp->|Neuer \< Feldtyp> [( \< Number> [, \< Number>])]|  
|\<Feldtyp>|Ein OLE DB-oder ADO-Datentyp.|  
|\<Zeichen folgen>|Unicode-Char [Unicode-Char...]|  
|\<Ausdruck>|Ein Visual Basic for Applications Ausdruck, dessen Operanden andere nicht-Calc-Spalten in derselben Zeile sind.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Übersicht über die Daten Strukturierung](../../../ado/guide/data/data-shaping-overview.md)   
 [Erforderliche Anbieter für die Daten Strukturierung](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape-APPEND-Klausel](../../../ado/guide/data/shape-append-clause.md)   
 [Shape-Befehle im allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Shape-COMPUTE-Klausel](../../../ado/guide/data/shape-compute-clause.md)   
 [Visual Basic for Applications-Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md)
