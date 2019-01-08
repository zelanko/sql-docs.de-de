---
title: Von parametrisierten Befehlen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
ms.assetid: 4fae0d54-83b6-4ead-99cc-bcf532daa121
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: faa4d4887079064ac6ccbe9536ac6c36fe8b9f79
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516991"
---
# <a name="operation-of-parameterized-commands"></a>Verarbeitung parametrisierter Befehle
Bei Verwendung mit einem großen untergeordneten **Recordset**, insbesondere auf die Größe des übergeordneten Elements verglichene **Recordset**, müssen nur wenige untergeordnete Kapitel zugreifen, aber Sie finden es möglicherweise effizienter, verwenden eine parametrisierte Befehle.  
  
 Ein *nicht parametrisierten Befehl* Ruft ab, die gesamte über- und untergeordneten **Recordsets**, fügt Sie an das übergeordnete Element eine Kapitelspalte an und weist dann einen Verweis auf das zugehörige untergeordnete Kapitel für jede Zeile der übergeordneten .  
  
 Ein *parametrisierten Befehl* Ruft ab, das gesamte übergeordnete **Recordset**, sondern nur im Kapitel über das abruft **Recordset** beim Zugriff auf die Kapitelspalte im. Dieser Unterschied bei der Abrufstrategie für die kann beachtliche Leistungsvorteile erzielt werden.  
  
 Beispielsweise können Sie Folgendes angeben:  
  
```  
SHAPE {SELECT * FROM customer}   
   APPEND ({SELECT * FROM orders WHERE cust_id = ?}   
   RELATE cust_id TO PARAMETER 0)  
```  
  
 Die über- und untergeordneten Tabellen haben einen Spaltennamen im Allgemeinen, Cust_id *.* Die *untergeordneten Befehl* verfügt über ein "?" Platzhalter, die auf den die RELATE-Klausel verweist (d. h. "... PARAMETER 0").  
  
> [!NOTE]
>  Die PARAMETER-Klausel bezieht sich ausschließlich auf die Befehlssyntax Form. Es ist nicht verknüpft mit entweder dem ADO [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt oder die [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung.  
  
 Wenn der parametrisierten Form-Befehl ausgeführt wird, geschieht Folgendes:  
  
1.  Die *übergeordnete Befehl* ausgeführt wird, und gibt ein übergeordnetes Element **Recordset** aus der Customers-Tabelle.  
  
2.  Eine Kapitelspalte wird angefügt, das dem übergeordneten **Recordset**.  
  
3.  Wenn die Kapitelspalte von einer übergeordneten Zeile zugegriffen wird, die *untergeordneten Befehl* ausgeführt wird, mit dem Wert von der Customer. cust_id als der Wert des Parameters.  
  
4.  Alle Zeilen im Rowset Daten-Anbieter in Schritt 3 erstellte werden verwendet, um das untergeordnete Element Auffüllen **Recordset**. In diesem Beispiel werden alle Zeilen in der Orders-Tabelle, in der die Cust_id der Wert von Customer. cust_id entspricht, darstellt. Standardmäßig wird das untergeordnete Element **Recordset**s wird auf dem Client zwischengespeichert werden, bis alle Verweise auf das übergeordnete Element **Recordset** freigegeben werden. Um dieses Verhalten zu ändern, legen die **Recordset** [dynamische Eigenschaft](../../../ado/reference/ado-api/ado-dynamic-property-index.md) **Cache untergeordneten Zeilen** zu **"false"**.  
  
5.  Ein Verweis auf die abgerufenen untergeordneten Zeilen (d. h. das Kapitel des untergeordneten Elements **Recordset**) befindet sich in der Kapitelspalte "im" der aktuellen Zeile des übergeordneten Elements **Recordset**.  
  
6.  Schritte 3 bis 5 werden wiederholt, wenn die Kapitelspalte mit einer anderen Zeile zugegriffen wird.  
  
 Die **Cache untergeordneten Zeilen** dynamische Eigenschaft nastaven NA hodnotu **"true"** standardmäßig. Das Verhalten beim Zwischenspeichern variiert in Abhängigkeit von der Werte der Parameter der Abfrage. In einer Abfrage mit einem einzigen Parameter, der das untergeordnete Element **Recordset** Wert wird für einen bestimmten Parameter zwischen den Anforderungen für ein untergeordnetes Element mit diesem Wert zwischengespeichert werden. Der folgende Code veranschaulicht dies:  
  
```  
SCmd = "SHAPE {select * from customer} " & _  
         "APPEND({select * from orders where cust_id = ?} " & _  
         "RELATE cust_id TO PARAMETER 0) AS chpCustOrder"  
Rst1.Open sCmd, Cnn1  
Set RstChild = Rst1("chpCustOrder").Value  
Rst1.MoveNext      ' Next cust_id passed to Param 0, & new rs fetched   
                   ' into RstChild.  
Rst1.MovePrevious  ' RstChild now holds cached rs, saving round trip.  
```  
  
 In einer Abfrage mit zwei oder mehr Parameter wird die zwischengespeicherte ein untergeordnetes Element verwendet, nur dann, wenn alle Werte der Parameter die zwischengespeicherten Werte übereinstimmen.  
  
## <a name="parameterized-commands-and-complex-parent-child-relations"></a>Parametrisierte Befehle und komplexe übergeordneten untergeordneten Beziehungen  
 Zusätzlich zur Verwendung parametrisierter Befehle zur Verbesserung der Leistung einer Typhierarchie Equi-Join, können auch parametrisierte Befehle zur Unterstützung komplexer über-/ unterordnungsbeziehung verwendet werden. Betrachten Sie beispielsweise eine kleine League-Datenbank mit zwei Tabellen: eine bestehend aus den Teams (Team_id, Teamname) und der andere vom Spiele ("Datum", "Home_team", "Visiting_team").  
  
 Verwenden eine Hierarchie mit nicht parametrisierten, besteht keine Möglichkeit, um die Teams und Spiele Tabellen so zu verknüpfen, die das untergeordnete Element **Recordset** für jedes Team seine vollständige Liste enthält. Sie können Kapiteln erstellen, die den privaten Zeitplan oder den Zeitplan für die Straße, aber nicht beides enthalten. Dies ist, da die RELATE-Klausel Sie über-und untergeordneten Beziehungen des Formulars schränkt (pc1 cc1 =) und (pc2 pc2 =). Also, wenn der Befehl "RELATE Team_id für Home_team, Team_id für Visiting_team" enthalten, nur Spiele erhalten Sie, in denen wurde ein Team selbst wiedergeben. Sie möchten "(team_id=home_team) oder (Team_id = Visiting_team)", aber die Shape-Anbieter unterstützt nicht die OR-Klausel.  
  
 Um das gewünschte Ergebnis zu erhalten, können Sie einen parametrisierten Befehl. Zum Beispiel:  
  
```  
SHAPE {SELECT * FROM teams}   
APPEND ({SELECT * FROM games WHERE home_team = ? OR visiting_team = ?}   
        RELATE team_id TO PARAMETER 0,   
               team_id TO PARAMETER 1)   
```  
  
 Dieses Beispiel nutzt die von der SQL-WHERE-Klausel, um das Ergebnis zu erhalten, das Sie benötigen mehr Flexibilität.  
  
> [!NOTE]
>  Wenn mithilfe von WHERE-Klauseln, Parameter können nicht die SQL-Datentypen für Text, Ntext und Image oder Fehler führt, enthält die folgende Beschreibung: `Invalid operator for data type`.  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die datenstrukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
