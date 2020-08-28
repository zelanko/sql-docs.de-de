---
description: SHAPE COMPUTE-Klausel
title: Shape-COMPUTE-Klausel | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- compute clause [ADO]
- data shaping [ADO], COMPUTE clause
ms.assetid: 3fdfead2-b5ab-4163-9b1d-3d2143a5db8c
author: rothja
ms.author: jroth
ms.openlocfilehash: 67411cf8d9be50571a515b5e7cf906fd19a650ec
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979601"
---
# <a name="shape-compute-clause"></a>SHAPE COMPUTE-Klausel
Eine Shape-COMPUTE-Klausel generiert ein übergeordnetes **Recordset**, dessen Spalten aus einem Verweis auf das untergeordnete **Recordset**bestehen. optionale Spalten, deren Inhalt Kapitel, neue oder berechnete Spalten ist, oder das Ergebnis der Ausführung von Aggregatfunktionen für das untergeordnete **Recordset** oder ein zuvor geformtes **Recordset**. und alle Spalten aus dem untergeordneten **Recordset** , die in der optionalen BY-Klausel aufgeführt sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
SHAPE child-command [AS] child-alias  
   COMPUTE child-alias [[AS] name], [appended-column-list]  
   [BY grp-field-list]  
```  
  
## <a name="description"></a>BESCHREIBUNG  
 Diese Klausel enthält folgende Teile:  
  
 *untergeordneter Befehl*  
 Besteht aus einer der folgenden:  
  
-   Ein Abfragebefehl in geschweiften Klammern (" {} "), der ein untergeordnetes **Recordset** -Objekt zurückgibt. Der Befehl wird an den zugrunde liegenden Datenanbieter ausgegeben, und seine Syntax hängt von den Anforderungen dieses Anbieters ab. Dies ist normalerweise die SQL-Sprache, auch wenn ADO keine bestimmte Abfragesprache erfordert.  
  
-   Der Name eines vorhandenen geformten **Recordsets**.  
  
-   Ein anderer Shape-Befehl.  
  
-   Das Tabellen Schlüsselwort, gefolgt vom Namen einer Tabelle im Datenanbieter.  
  
 *untergeordneter Alias*  
 Ein Alias, mit dem auf das **Recordset** verwiesen wird, das vom untergeordneten Befehl zurückgegeben wird *.* Der untergeordnete Alias ist in der Liste der Spalten in der COMPUTE *-* Klausel erforderlich und definiert die Beziehung zwischen dem übergeordneten und dem untergeordneten **Recordset** -Objekt.  
  
 *angefügte Spaltenliste*  
 Eine Liste, in der jedes Element eine Spalte im generierten übergeordneten Element definiert. Jedes Element enthält entweder eine Kapitel Spalte, eine neue Spalte, eine berechnete Spalte oder einen Wert, der sich aus einer Aggregatfunktion für das untergeordnete **Recordset**ergibt.  
  
 *GRP-Feldliste*  
 Eine Liste von Spalten in den übergeordneten und untergeordneten **Recordset** -Objekten, die angibt, wie Zeilen im untergeordneten Element gruppiert werden sollen.  
  
 Für jede Spalte in der " *GRP-field-list* " gibt es eine entsprechende Spalte in den untergeordneten und übergeordneten **Recordset** -Objekten. Für jede Zeile im übergeordneten **Recordset**verfügen die *GRP-field-list-* Spalten über eindeutige Werte, und das untergeordnete **Recordset** , auf das von der übergeordneten Zeile verwiesen wird, besteht nur aus untergeordneten Zeilen, deren *GRP-field-list-* Spalten dieselben Werte wie die übergeordnete Zeile aufweisen.  
  
 Wenn die by-Klausel eingeschlossen ist, werden die Zeilen des untergeordneten **Recordsets**basierend auf den Spalten in der COMPUTE-Klausel gruppiert. Das übergeordnete **Recordset** enthält eine Zeile für jede Gruppe von Zeilen im untergeordneten **Recordset**.  
  
 Wenn die by-Klausel weggelassen wird, wird das gesamte untergeordnete **Recordset** als eine einzelne Gruppe behandelt, und das übergeordnete **Recordset** enthält genau eine Zeile. Diese Zeile verweist auf das gesamte untergeordnete **Recordset**. Das Weglassen der by-Klausel ermöglicht es Ihnen, "Gesamtsumme"-Aggregate für das gesamte untergeordnete **Recordset**zu berechnen.  
  
 Beispiel:  
  
```  
SHAPE {select * from Orders} AS orders             COMPUTE orders, SUM(orders.OrderAmount) as TotalSales         
```  
  
 Unabhängig davon, wie das übergeordnete **Recordset** (mithilfe von COMPUTE oder mithilfe von Append) formatiert wird, enthält es eine Kapitel Spalte, die verwendet wird, um es mit einem untergeordneten **Recordset**zu verknüpfen. Wenn Sie möchten, kann das übergeordnete **Recordset** auch Spalten enthalten, die Aggregate (Sum, min, Max usw.) für die untergeordneten Zeilen enthalten. Sowohl das übergeordnete als auch das untergeordnete **Recordset** enthalten möglicherweise Spalten, die einen Ausdruck in der Zeile im **Recordset**enthalten, sowie neue und Anfangs leere Spalten.  
  
## <a name="operation"></a>Vorgang  
 Der untergeordnete *Befehl* wird an den Anbieter ausgegeben, der ein untergeordnetes **Recordset**zurückgibt.  
  
 Die COMPUTE-Klausel gibt die Spalten des übergeordneten **Recordsets**an. Hierbei kann es sich um einen Verweis auf das untergeordnete **Recordset**, ein oder mehrere Aggregate, einen berechneten Ausdruck oder neue Spalten handeln. Wenn eine by-Klausel vorhanden ist, werden die definierten Spalten auch an das übergeordnete **Recordset**angehängt. Die by-Klausel gibt an, wie die Zeilen des untergeordneten **Recordsets** gruppiert werden.  
  
 Nehmen Sie beispielsweise an, Sie verfügen über eine Tabelle mit dem Namen Demographics, die aus den Feldern State, City und Population besteht. (Die Bevölkerungszahlen in der Tabelle werden ausschließlich als Beispiel bereitgestellt.)  
  
|State|City|Auffüllung|  
|-----------|----------|----------------|  
|WA|Seattle|700.000|  
|oder|Medford|200.000|  
|oder|Portland|400.000|  
|CA|Los Angeles|800.000|  
|CA|San Diego|600.000|  
|WA|Tacoma|500.000|  
|oder|Corvallis|300.000|  
  
 Geben Sie nun diesen Form Befehl aus:  
  
```  
rst.Open  "SHAPE {select * from demographics} AS rs "  & _  
          "COMPUTE rs, SUM(rs.population) BY state", _  
           objConnection  
```  
  
 Dieser Befehl öffnet ein geformtes **Recordset** mit zwei Ebenen. Die übergeordnete Ebene ist ein generiertes **Recordset** mit einer Aggregat Spalte ( `SUM(rs.population)` ), eine Spalte, die auf das untergeordnete **Recordset** ( `rs` ) verweist, und eine Spalte zum Gruppieren des untergeordneten **Recordsets** ( `state` ). Die untergeordnete Ebene ist das **Recordset** , das vom Abfragebefehl zurückgegeben wird ( `select * from demographics` ).  
  
 Die Detail Zeilen des untergeordneten **Recordsets** werden nach dem Zustand gruppiert, aber andernfalls in keiner bestimmten Reihenfolge. Das heißt, die Gruppen werden nicht in alphabetischer oder numerischer Reihenfolge angegeben. Wenn Sie möchten, dass das übergeordnete **Recordset** sortiert wird, können Sie das übergeordnete **Recordset**mit der **Recordset-Sortiermethode sortieren** .  
  
 Sie können jetzt im geöffneten übergeordneten **Recordset** navigieren und auf die untergeordneten Detail- **Recordset** -Objekte zugreifen. Weitere Informationen finden Sie unter [zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
## <a name="resultant-parent-and-child-detail-recordsets"></a>Resultierende übergeordnete und untergeordnete Detail Recordsets  
  
### <a name="parent"></a>Parent  
  
|Sum (RS). Bevölkerungs|rs|State|  
|---------------------------|--------|-----------|  
|1,3 Millionen|Verweis auf child1|CA|  
|1,2 Millionen|Verweis auf child2|WA|  
|1,1 Millionen|Verweis auf Child3|oder|  
  
## <a name="child1"></a>Child1  
  
|State|City|Auffüllung|  
|-----------|----------|----------------|  
|CA|Los Angeles|800.000|  
|CA|San Diego|600.000|  
  
## <a name="child2"></a>Child2  
  
|State|City|Auffüllung|  
|-----------|----------|----------------|  
|WA|Seattle|700.000|  
|WA|Tacoma|500.000|  
  
## <a name="child3"></a>Child3  
  
|State|City|Auffüllung|  
|-----------|----------|----------------|  
|oder|Medford|200.000|  
|oder|Portland|400.000|  
|oder|Corvallis|300.000|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Übersicht über die Daten Strukturierung](../../../ado/guide/data/data-shaping-overview.md)   
 [Field-Objekt](../../../ado/reference/ado-api/field-object.md)   
 [Formale Form Grammatik](../../../ado/guide/data/formal-shape-grammar.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Erforderliche Anbieter für die Daten Strukturierung](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape-APPEND-Klausel](../../../ado/guide/data/shape-append-clause.md)   
 [Shape-Befehle im allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Value-Eigenschaft (ADO)](../../../ado/reference/ado-api/value-property-ado.md)   
 [Visual Basic for Applications-Funktionen](../../../ado/guide/data/visual-basic-for-applications-functions.md)
