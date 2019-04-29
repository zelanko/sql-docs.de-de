---
title: Strukturieren von COMPUTE-Klausel | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- compute clause [ADO]
- data shaping [ADO], COMPUTE clause
ms.assetid: 3fdfead2-b5ab-4163-9b1d-3d2143a5db8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b78abac5ccbade0b686176f432618b4abc35ccab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062816"
---
# <a name="shape-compute-clause"></a>SHAPE COMPUTE-Klausel
Eine Shape COMPUTE-Klausel generiert ein übergeordnetes Element **Recordset**, einen Verweis auf das untergeordnete Element, dessen Spalten bestehen aus **Recordset**; optional, deren Inhalt neue Kapitel oder berechnete Spalten werden, Spalten oder die Ergebnis der Ausführung von Aggregatfunktionen auf dem untergeordneten Element **Recordset** oder eine zuvor geformten **Recordset**; und alle Spalten von den untergeordneten **Recordset** in aufgeführt die optionale BY-Klausel.  
  
## <a name="syntax"></a>Syntax  
  
```  
SHAPE child-command [AS] child-alias  
   COMPUTE child-alias [[AS] name], [appended-column-list]  
   [BY grp-field-list]  
```  
  
## <a name="description"></a>Description  
 Die Teile des diese Klausel lauten wie folgt aus:  
  
 *child-command*  
 Besteht aus einem der folgenden:  
  
-   Einen Abfragebefehl in geschweiften Klammern ("{}"), die ein untergeordnetes Element zurückgibt **Recordset** Objekt. Die Ausgabe des Befehls wird an den zugrunde liegenden Datenanbieter und die Syntax hängt von den Anforderungen von diesem Anbieter. Dies ist der SQL-Sprache in der Regel wird, obwohl ADO keine bestimmte Abfragesprache erforderlich ist.  
  
-   Der Name eines vorhandenen strukturiert **Recordset**.  
  
-   Eine andere Form-Befehl.  
  
-   Das TABLE-Schlüsselwort, gefolgt vom Namen einer Tabelle in der Datenanbieter.  
  
 *child-alias*  
 Ein Alias zum Verweisen auf die **Recordset** zurückgegebenes der *untergeordneten-Befehl.* Die *untergeordnete-Alias* ist in der Liste der Spalten in der COMPUTE-Klausel erforderlich und definiert die Beziehung zwischen den übergeordneten und untergeordneten **Recordset** Objekte.  
  
 *appended-column-list*  
 Eine Liste, in der jedes Element eine Spalte in der generierten übergeordneten Element definiert. Jedes Element enthält, entweder eine Kapitelspalte, eine neue Spalte, einer berechneten Spalte oder einen Wert, der durch eine Aggregatfunktion für das untergeordnete Element **Recordset**.  
  
 *grp-field-list*  
 Eine Liste der Spalten in den übergeordneten und untergeordneten **Recordset** Objekten, das angibt, wie Zeilen in der untergeordneten gruppiert werden sollen.  
  
 Für jede Spalte in der *Grp--Feldliste* ist es eine entsprechende Spalte in den untergeordneten und übergeordneten **Recordset** Objekte. Für jede Zeile in der übergeordneten **Recordset**, *Grp Feldliste* Spalten verfügen über eindeutige Werte und das untergeordnete Element **Recordset** verwiesen wird, durch das übergeordnete Zeile besteht ausschließlich aus untergeordneten Zeilen, deren *Grp Feldliste* Spalten enthalten die gleichen Werte wie die übergeordnete Zeile.  
  
 Wenn die BY-Klausel enthalten, ist das untergeordnete Element **Recordset**die Zeilen werden basierend auf den Spalten in der COMPUTE-Klausel gruppiert werden. Das übergeordnete Element **Recordset** enthält eine Zeile für jede Gruppe von Zeilen in der untergeordneten **Recordset**.  
  
 Wenn die BY-Klausel weggelassen wird, das gesamte untergeordnete **Recordset** behandelt, als eine einzelne Gruppe und das übergeordnete Element **Recordset** genau eine Zeile enthält. Diese Zeile verweist auf das gesamte untergeordnete **Recordset**. Die BY-Klausel auslassen, können Sie zum Berechnen von "Gesamtsumme" Aggregate über das gesamte untergeordnete **Recordset**.  
  
 Zum Beispiel:  
  
```  
SHAPE {select * from Orders} AS orders             COMPUTE orders, SUM(orders.OrderAmount) as TotalSales         
```  
  
 Unabhängig davon, wie das übergeordnete Element **Recordset** wird gebildet (COMPUTE oder ANFÜGEN), enthält es eine Kapitelspalte, die verwendet wird, um es auf ein untergeordnetes Element verknüpfen **Recordset**. Wenn Sie möchten, das übergeordnete Element **Recordset** kann auch über die untergeordneten Zeilen enthalten, Spalten, die Aggregate (SUM, MIN, MAX, usw.) enthalten. Sowohl das übergeordnete Element und dem untergeordneten Element **Recordset** Spalten, die einen Ausdruck in der Zeile enthalten darf der **Recordset**sowie Spalten, die neue und anfangs leere.  
  
## <a name="operation"></a>Vorgang  
 Die *untergeordneten Befehl* ausgegeben wird, an den Anbieter, wodurch ein untergeordnetes Element **Recordset**.  
  
 Die COMPUTE-Klausel gibt die Spalten des übergeordneten Elements **Recordset**, die möglicherweise einen Verweis auf das untergeordnete Element **Recordset**, einem oder mehreren Aggregaten, eines berechneten Ausdrucks oder neue Spalten. Wenn eine BY-Klausel vorhanden ist, werden die Spalten, die sie definiert außerdem das dem übergeordneten angefügt **Recordset**. Die BY-Klausel gibt an, wie die Zeilen der untergeordneten **Recordset** gruppiert werden.  
  
 Nehmen wir beispielsweise an, dass Sie eine Tabelle namens Demographics verfügen, besteht aus Status, Stadt und der Bevölkerung Felder. (Die Auffüllung-Abbildungen in der Tabelle dienen lediglich als Beispiel).  
  
|Status|Ort|Auffüllung|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|oder|Medford|200,000|  
|oder|Portland|400,000|  
|CA|Los Angeles|800,000|  
|CA|SAN Diego|600,000|  
|WA|Tacoma|500,000|  
|oder|Corvallis|300,000|  
  
 Geben Sie jetzt diese Form-Befehl aus:  
  
```  
rst.Open  "SHAPE {select * from demographics} AS rs "  & _  
          "COMPUTE rs, SUM(rs.population) BY state", _  
           objConnection  
```  
  
 Dieser Befehl öffnet ein geformten **Recordset** mit zwei Ebenen. Die übergeordnete Ebene ist eine generierte **Recordset** mit einer Spalte aggregieren (`SUM(rs.population)`), eine Spalte verweisen auf das untergeordnete Element **Recordset** (`rs`), und eine Spalte zum Gruppieren des untergeordneten **Recordset** (`state`). Die untergeordnete Ebene ist die **Recordset** von den Abfragebefehl zurückgegeben (`select * from demographics`).  
  
 Das untergeordnete Element **Recordset** Detailzeilen werden nach Zustand gruppiert, aber ansonsten keine bestimmte Reihenfolge. Die Gruppen werden, also nicht in alphabetischer oder numerischer Reihenfolge. Wenn Sie möchten, dass das übergeordnete Element **Recordset** um bestellt werden, können Sie die **Sortieren des Recordset** Methode, um das übergeordnete order **Recordset**.  
  
 Sie können jetzt im geöffneten übergeordneten navigieren **Recordset** und Zugriff auf die Details der untergeordneten **Recordset** Objekte. Weitere Informationen finden Sie unter [den Zugriff auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
## <a name="resultant-parent-and-child-detail-recordsets"></a>Übergeordnete und untergeordnete Detail Recordsets  
  
### <a name="parent"></a>Parent  
  
|SUM (Rs. Auffüllung)|rs|Status|  
|---------------------------|--------|-----------|  
|1,300,000|Verweis auf child1|CA|  
|1,200,000|Verweis auf child2|WA|  
|1,100,000|Verweis auf child3|oder|  
  
## <a name="child1"></a>Child1  
  
|Status|Ort|Auffüllung|  
|-----------|----------|----------------|  
|CA|Los Angeles|800,000|  
|CA|SAN Diego|600,000|  
  
## <a name="child2"></a>Child2  
  
|Status|Ort|Auffüllung|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|WA|Tacoma|500,000|  
  
## <a name="child3"></a>Child3  
  
|Status|Ort|Auffüllung|  
|-----------|----------|----------------|  
|oder|Medford|200,000|  
|oder|Portland|400,000|  
|oder|Corvallis|300,000|  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Daten strukturieren (Übersicht)](../../../ado/guide/data/data-shaping-overview.md)   
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Recordset Object (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Erforderliche Anbieter für die Strukturierung der Daten](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape APPEND-Klausel](../../../ado/guide/data/shape-append-clause.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Value-Eigenschaft (ADO)](../../../ado/reference/ado-api/value-property-ado.md)   
 [Visual Basic for Applications-Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md)
