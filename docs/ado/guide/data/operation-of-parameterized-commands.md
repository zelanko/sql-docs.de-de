---
title: Parametrisierte Befehle | Microsoft-Dokumentation
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
ms.openlocfilehash: e7d4399a8cf279ed2283061fff9064ffcc1adfba
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924739"
---
# <a name="operation-of-parameterized-commands"></a>Verarbeitung parametrisierter Befehle
Wenn Sie mit einem großen untergeordneten **Recordset**arbeiten, besonders im Vergleich zur Größe des übergeordneten **Recordsets**, aber nur auf ein paar untergeordneter Kapitel zugreifen müssen, ist es möglicherweise effizienter, einen parametrisierten Befehl zu verwenden.  
  
 Ein *nicht parametrisierter Befehl* ruft sowohl das gesamte übergeordnete als auch das untergeordnete **Recordset**ab, fügt eine Kapitel Spalte an das übergeordnete Element an und weist dann einen Verweis auf das verwandte untergeordnete Kapitel für jede übergeordnete Zeile zu.  
  
 Ein *parametrisierter Befehl* Ruft das gesamte übergeordnete **Recordset**ab, ruft jedoch nur das Kapitel **Recordset** ab, wenn auf die Kapitel Spalte zugegriffen wird. Dieser Unterschied in der Abruf Strategie kann zu erheblichen Leistungsvorteilen führen.  
  
 Sie können z. b. Folgendes angeben:  
  
```  
SHAPE {SELECT * FROM customer}   
   APPEND ({SELECT * FROM orders WHERE cust_id = ?}   
   RELATE cust_id TO PARAMETER 0)  
```  
  
 Die über-und untergeordneten Tabellen haben einen gemeinsamen Spaltennamen *cust_id*. Der untergeordnete *Befehl* weist den Platzhalter "?" auf, auf den sich die Verwandte Klausel bezieht (d. h. "... Parameter 0 ").  
  
> [!NOTE]
>  Die Parameter Klausel bezieht sich ausschließlich auf die Syntax des Shape-Befehls. Sie ist weder dem ADO- [Parameter](../../../ado/reference/ado-api/parameter-object.md) Objekt noch der [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung zugeordnet.  
  
 Wenn der Befehl für die parametrisierte Form ausgeführt wird, geschieht Folgendes:  
  
1.  Der über *geordnete-Befehl* wird ausgeführt, und es wird ein übergeordnetes **Recordset** aus der Customers-Tabelle zurückgegeben.  
  
2.  Eine Kapitel Spalte wird an das übergeordnete **Recordset**angehängt.  
  
3.  Wenn auf die Kapitel-Spalte einer übergeordneten Zeile zugegriffen wird, wird der untergeordnete *-Befehl* mit dem Wert von Customer. cust_id als Wert des-Parameters ausgeführt.  
  
4.  Alle Zeilen im Datenanbieter-Rowset, das in Schritt 3 erstellt wurde, werden verwendet, um das untergeordnete **Recordset aufzufüllen**. In diesem Beispiel handelt es sich dabei um alle Zeilen in der Orders-Tabelle, in der die cust_id dem Wert von Customer. cust_id entspricht. Standardmäßig werden die untergeordneten **Recordsets**auf dem Client zwischengespeichert, bis alle Verweise auf das übergeordnete **Recordset** freigegeben werden. Um dieses Verhalten zu ändern, legen Sie die untergeordneten Zeilen des **Recordset** [Dynamic Property](../../../ado/reference/ado-api/ado-dynamic-property-index.md) **Cache** auf **false**fest.  
  
5.  Ein Verweis auf die abgerufenen untergeordneten Zeilen (d. h. das Kapitel des untergeordneten **Recordsets**) wird in der Spalte Kapitel der aktuellen Zeile des übergeordneten **Recordsets**platziert.  
  
6.  Die Schritte 3-5 werden wiederholt, wenn auf die Kapitel-Spalte einer anderen Zeile zugegriffen wird.  
  
 Die dynamische Eigenschaft des Cache untergeordneter **Zeilen** ist standardmäßig auf **true** festgelegt. Das Caching-Verhalten variiert abhängig von den Parameterwerten der Abfrage. In einer Abfrage mit einem einzelnen Parameter wird das untergeordnete **Recordset** für einen angegebenen Parameterwert zwischen Anforderungen für ein untergeordnetes Element mit diesem Wert zwischengespeichert. Dies veranschaulicht der folgende Code:  
  
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
  
 In einer Abfrage mit zwei oder mehr Parametern wird ein zwischengespeichertes untergeordnetes Element nur verwendet, wenn alle Parameterwerte den zwischengespeicherten Werten entsprechen.  
  
## <a name="parameterized-commands-and-complex-parent-child-relations"></a>Parametrisierte Befehle und komplexe Beziehungen zwischen übergeordneten und untergeordneten Elementen  
 Neben der Verwendung parametrisierter Befehle zum Verbessern der Leistung einer Equi-Join-Typhierarchie können parametrisierte Befehle verwendet werden, um komplexere Beziehungen zwischen übergeordneten und untergeordneten Elementen zu unterstützen. Nehmen wir beispielsweise an, eine kleine Liga-Datenbank mit zwei Tabellen besteht aus den Teams (team_id TEAM_NAME) und den anderen spielen (Date, home_team, visiting_team).  
  
 Mithilfe einer nicht parametrisierten Hierarchie gibt es keine Möglichkeit, die Teams und Spiel Tabellen so zu verknüpfen, dass das untergeordnete **Recordset** für jedes Team seinen kompletten Zeitplan enthält. Sie können Kapitel erstellen, die den Basis Zeitplan oder den Plan für die Straße enthalten, aber nicht beides. Dies liegt daran, dass die Klausel "Verwandte Beziehung" Sie auf Beziehungen zwischen übergeordneten und untergeordneten Elementen im Formular (PC1 = cc1) und (PC2 = PC2) beschränkt. Wenn der Befehl beispielsweise "team_id mit home_team in Beziehung team_id visiting_team" eingeschlossen ist, würden Sie nur Spiele erhalten, in denen sich ein Team selbst abgespielt hat. Was Sie möchten, ist "(team_id = home_team) oder (team_id = visiting_team)", aber der Shape-Anbieter unterstützt die-oder-Klausel nicht.  
  
 Um das gewünschte Ergebnis zu erhalten, können Sie einen parametrisierten Befehl verwenden. Beispiel:  
  
```  
SHAPE {SELECT * FROM teams}   
APPEND ({SELECT * FROM games WHERE home_team = ? OR visiting_team = ?}   
        RELATE team_id TO PARAMETER 0,   
               team_id TO PARAMETER 1)   
```  
  
 In diesem Beispiel wird die größere Flexibilität der SQL-WHERE-Klausel ausgenutzt, um das benötigte Ergebnis zu erhalten.  
  
> [!NOTE]
>  Bei Verwendung von WHERE-Klauseln können Parameter die SQL-Datentypen für Text, ntext und Image nicht verwenden, oder es tritt ein Fehler auf, der `Invalid operator for data type`die folgende Beschreibung enthält:.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Daten Strukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Form Grammatik](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
