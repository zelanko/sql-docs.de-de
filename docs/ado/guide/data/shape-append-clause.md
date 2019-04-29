---
title: Shape APPEND-Klausel | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- data shaping [ADO], APPEND clause
- append clause [ADO]
ms.assetid: f90fcf55-6b24-401d-94e1-d65bd24bd342
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13a91d6b8512b2c1287c3cc8e36e43a1317022d7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062856"
---
# <a name="shape-append-clause"></a>SHAPE APPEND-Klausel
Die APPEND-Klausel in Shape-Befehl fügt eine oder mehrere Spalten zu einer **Recordset**. Diese Spalten sind in vielen Fällen Kapitelspalten, die auf ein untergeordnetes Element verweisen **Recordset**.  
  
## <a name="syntax"></a>Syntax  
  
```  
SHAPE [parent-command [[AS] parent-alias]] APPEND column-list  
```  
  
## <a name="description"></a>Description  
 Die Teile des diese Klausel lauten wie folgt aus:  
  
 *parent-command*  
 0 (null) oder eines der folgenden (können Sie weglassen der *übergeordnete Befehl* vollständig):  
  
-   Ein Anbieterbefehl, der in geschweifte Klammern eingeschlossen ("{}") zurückgibt, die eine **Recordset** Objekt. Die Ausgabe des Befehls wird an den zugrunde liegenden Datenanbieter und die Syntax hängt von den Anforderungen von diesem Anbieter. Dies ist der SQL-Sprache in der Regel wird, obwohl ADO keine bestimmte Abfragesprache erforderlich ist.  
  
-   Ein anderes Shape-Befehl, eingebettet in Klammern angegeben.  
  
-   Das TABLE-Schlüsselwort, gefolgt vom Namen einer Tabelle in der Datenanbieter.  
  
 *parent-alias*  
 Ein optionaler Alias, der auf das übergeordnete Element verweist **Recordset**.  
  
 *column-list*  
 Eine oder mehrere der folgenden:  
  
-   Die aggregierte Spalte.  
  
-   Eine berechnete Spalte.  
  
-   Eine neue Spalte, die mithilfe der neuen-Klausel erstellt wird.  
  
-   Eine Kapitelspalte. Die Definition einer Kapitel-Spalte wird in Klammern ("()") eingeschlossen. Finden Sie die folgende Syntax.  
  
```  
SHAPE [parent-command [[AS] parent-alias]]  
   APPEND (child-recordset [ [[AS] child-alias]   
      RELATE parent-column TO child-column | PARAMETER param-number, ... ])  
   [[AS] chapter-alias]   
   [, ... ]  
```  
  
## <a name="remarks"></a>Hinweise  
 *child-recordset*  
 -   Ein Anbieterbefehl, der in geschweifte Klammern eingeschlossen ("{}") zurückgibt, die eine **Recordset** Objekt. Die Ausgabe des Befehls wird an den zugrunde liegenden Datenanbieter und die Syntax hängt von den Anforderungen von diesem Anbieter. Dies ist der SQL-Sprache in der Regel wird, obwohl ADO keine bestimmte Abfragesprache erforderlich ist.  
  
-   Ein anderes Shape-Befehl, eingebettet in Klammern angegeben.  
  
-   Der Name eines vorhandenen strukturiert **Recordset**.  
  
-   Das TABLE-Schlüsselwort, gefolgt vom Namen einer Tabelle in der Datenanbieter.  
  
 *child-alias*  
 Ein Alias, der auf das untergeordnete Element verweist **Recordset**.  
  
 *parent-column*  
 Eine Spalte in der **Recordset** zurückgegebenes der *übergeordneter-Befehl.*  
  
 *child-column*  
 Eine Spalte in der **Recordset** zurückgegebenes der *untergeordneten Befehl*.  
  
 *param-number*  
 Finden Sie unter [von parametrisierten Befehlen](../../../ado/guide/data/operation-of-parameterized-commands.md).  
  
 *chapter-alias*  
 Ein Alias, der auf die Kapitelspalte angefügt, das dem übergeordneten verweist.  
  
> [!NOTE]
>  Die *"übergeordnete Spalte* für *untergeordnete Spalte"* -Klausel ist tatsächlich eine Liste, jede Beziehung definiert ist, in dem durch ein Komma getrennt.  
  
> [!NOTE]
>  Die Klausel nach dem ANFÜGEN-Schlüsselwort ist tatsächlich eine Liste, in dem jede Klausel, die durch ein Komma getrennt ist und eine weitere Spalte definiert, das dem übergeordneten angefügt werden soll.  
  
## <a name="remarks"></a>Hinweise  
 Erstellen der Anbieterbefehlen aus Benutzereingaben als Teil einer SHAPE-Befehl Form ein Befehls als nicht transparente Zeichenfolge behandelt den vom Benutzer bereitgestellten und Übergabe an dem Anbieter enthalten. Beispielsweise in der folgenden SHAPE-Befehl  
  
```  
SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 Form "führt zwei Befehle: `select * from t1` und (`select * from t2 RELATE k1 TO k2)`. Wenn der Benutzer einen zusammengesetzten Befehl bereitstellt, der mehrere Anbieterbefehle, die durch Semikolons getrennte besteht, ist die Form nicht den Unterschied zu unterscheiden. Also in den folgenden Befehl für die Form "  
  
```  
SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 Form führt `select * from t1; drop table t1` und (`select * from t2 RELATE k1 TO k2),` nicht bemerken, die `drop table t1` ist eine Separate und in diesem Fall, birgt Risiken, Anbieter-Befehl. Anwendungen müssen immer die Benutzereingabe auf solche potenziellen Hackerangriffe verhindern überprüfen.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Operation of Non-Parameterized Commands (Verarbeitung nicht-parametrisierter Befehle)](../../../ado/guide/data/operation-of-non-parameterized-commands.md)  
  
-   [Operation of Parameterized Commands (Verarbeitung parametrisierter Befehle)](../../../ado/guide/data/operation-of-parameterized-commands.md)  
  
-   [Hybridbefehle](../../../ado/guide/data/hybrid-commands.md)  
  
-   [Intervening Shape COMPUTE Clauses (Zwischenschalten von SHAPE COMPUTE-Klauseln)](../../../ado/guide/data/intervening-shape-compute-clauses.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die datenstrukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
