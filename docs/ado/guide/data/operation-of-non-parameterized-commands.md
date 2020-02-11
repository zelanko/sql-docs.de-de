---
title: Vorgang von nicht parametrisierten Befehlen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- non-parameterized commands [ADO]
- data shaping [ADO], non-parameterized commands
ms.assetid: 9700e50a-9f17-4ba3-8afb-f750741dc6ca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3512b484425749ed027f6533dab7398765c1af2e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924747"
---
# <a name="operation-of-non-parameterized-commands"></a>Verarbeitung nicht-parametrisierter Befehle
Bei nicht parametrisierten Befehlen werden alle Anbieter Befehle ausgeführt, und die **Recordsets** werden während der Ausführung des Befehls erstellt. Wenn der Befehl synchron ausgeführt wird, werden alle **Recordsets** vollständig aufgefüllt. Wenn ein asynchroner auffüllungs Modus ausgewählt wurde, hängt der auffüllungs Status der **Recordsets** vom auffüllungs Modus und der Größe der **Recordsets**ab.  
  
 Der über *geordnete Befehl* könnte z. b. eine **recordmenge** von Kunden für ein Unternehmen aus einer Customers-Tabelle zurückgeben, und der untergeordnete Befehl könnte ein **Recordset** von Bestellungen für alle Kunden aus einer Orders *-* Tabelle zurückgeben.  
  
```  
SHAPE {SELECT * FROM Customers}   
   APPEND ({SELECT * FROM Orders} AS chapOrders   
   RELATE customerID TO customerID)  
```  
  
 Bei nicht parametrisierten Beziehungen zwischen übergeordneten und untergeordneten Elementen muss jedes übergeordnete und untergeordnete **Recordset** -Objekt über eine gemeinsame Spalte verfügen, um diese zuzuordnen. Die Spalten werden in der Beziehung Klausel, der über *geordneten Spalte* First und der untergeordneten *Spalte*benannt. Die Spalten können unterschiedliche Namen in den jeweiligen **recordsetobjekten** aufweisen, müssen jedoch auf dieselben Informationen verweisen, um eine sinnvolle Beziehung anzugeben. Beispielsweise könnten die **Kunden** -und **Orders-Recordset** -Objekte über ein CustomerID-Feld verfügen. Da die Mitgliedschaft des untergeordneten **Recordsets** durch den Anbieter Befehl bestimmt wird, kann das untergeordnete **Recordset** verwaiste Zeilen enthalten. Auf diese verwaisten Zeilen kann ohne zusätzliche Umgestaltung nicht zugegriffen werden.  
  
 Die Daten Strukturierung fügt eine Kapitel Spalte an das übergeordnete **Recordset**an. Die Werte in der Spalte "Chapter" sind Verweise auf Zeilen im untergeordneten **Recordset**, die die Klausel "Verwandte Beziehung" erfüllen. Das heißt, der gleiche Wert befindet sich in der über *geordneten Spalte* einer angegebenen übergeordneten Zeile, die sich in der untergeordneten *Spalte* aller Zeilen des untergeordneten Elements befindet. Wenn mehrere to-Klauseln in derselben Beziehung Klausel verwendet werden, werden Sie implizit mithilfe eines and-Operators kombiniert. Wenn die übergeordneten Spalten in der Beziehung-Klausel keinen Schlüssel für das übergeordnete **Recordset**bilden, kann eine einzelne untergeordnete Zeile über mehrere übergeordnete Zeilen verfügen.  
  
 Wenn Sie auf den Verweis in der Kapitel-Spalte zugreifen, ruft ADO automatisch das **Recordset** ab, das durch den Verweis dargestellt wird. Beachten Sie, dass in einem nicht parametrisierten Befehl, obwohl das gesamte untergeordnete **Recordset** abgerufen wurde, das Kapitel nur eine Teilmenge der Zeilen darstellt.  
  
 Wenn die angefügte Spalte keinen *Chapter-Alias*hat, wird automatisch ein Name generiert. Ein [Feld](../../../ado/reference/ado-api/field-object.md) Objekt für die Spalte wird an die [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung des **Recordset** -Objekts angehängt, und sein Datentyp **lautet adChapter**.  
  
 Informationen zum Navigieren in einem hierarchischen **Recordset**finden Sie unter [zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Daten Strukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Form Grammatik](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
