---
title: Beispiel für die datenstrukturierung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], about data shaping
ms.assetid: 1bfdcad4-52e1-45bc-ad21-783657ef0a44
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 92e34de1b9fd675570527f9a28f8476a51597f10
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696428"
---
# <a name="data-shaping-example"></a>Datenstrukturierung – Beispiel
Die folgenden Daten strukturieren Befehl veranschaulicht, wie eine hierarchische **Recordset** aus der **Kunden** und **Bestellungen** Tabellen in der Northwind-Datenbank.  
  
```  
SHAPE {SELECT CustomerID, ContactName FROM Customers}   
APPEND ({SELECT OrderID, OrderDate, CustomerID FROM Orders} AS chapOrders   
RELATE customerID TO customerID)   
```  
  
 Wenn dieser Befehl verwendet wird, öffnen Sie eine **Recordset** Objekt (siehe [Visual Basic Beispiel der Datenstrukturierung](../../../ado/guide/data/visual-basic-example-of-data-shaping.md)), erstellt ein Kapitel (**ChapOrders**) für die einzelnen zurückgegebenen Datensätze von der **Kunden** Tabelle. Dieses Kapitel besteht aus einer Teilmenge von der **Recordset** zurückgegeben, die von der **Bestellungen** Tabelle. Die **ChapOrders** Kapitel enthält alle angeforderten Informationen über die Bestellungen, die von den jeweiligen Kunden. In diesem Beispiel das Kapitel besteht aus drei Spalten: **"OrderID"**, **OrderDate**, und **"CustomerID"**.  
  
 Die ersten beiden Einträge von der resultierenden strukturiert **Recordset** lauten wie folgt:  
  
|CustomerID|ContactName|OrderID|OrderDate|CustomerID|  
|----------------|-----------------|-------------|---------------|----------------|  
|ALFKI|Maria Ander|10643<br /><br /> 10692<br /><br /> 10702<br /><br /> 10835<br /><br /> 10952<br /><br /> 11011|1997-08-25<br /><br /> 1997-10-03<br /><br /> 1997-10-13<br /><br /> 1998-01-15<br /><br /> 1998-03-16<br /><br /> 1998-04-09|ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI<br /><br /> ALFKI|  
|ANATR|SQL-Batchdatei(en) ANA Trujillo|10308<br /><br /> 10625<br /><br /> 10759<br /><br /> 10926|1996-09-18<br /><br /> 1997-08-08<br /><br /> 1997-11-28<br /><br /> 1998-03-04|ANATR<br /><br /> ANATR<br /><br /> ANATR<br /><br /> ANATR|  
  
 In einer SHAPE-Befehl ANFÜGEN verwendet, um ein untergeordnetes Element erstellen **Recordset** im Zusammenhang mit der das übergeordnete Element **Recordset** (wie vom Anbieter-spezifischen Befehl unmittelbar nach dem Form-Schlüsselwort, das besprochen wurde zurückgegeben weiter oben) von der RELATE-Klausel. Die über- und untergeordneten in der Regel haben mindestens eine Spalte gemeinsam: der Wert der Spalte in einer Zeile des übergeordneten Elements ist identisch mit dem Wert der Spalte in allen Zeilen des untergeordneten Elements.  
  
 Es wird eine zweite Methode zur Verwendung von SHAPE-Befehle: nämlich, um ein übergeordnetes Element zu generieren **Recordset** von einem untergeordneten **Recordset**. Die Datensätze in der untergeordneten **Recordset** gruppiert sind, in der Regel mithilfe der BY-Klausel und eine Zeile zum übergeordneten Element hinzugefügt wird **Recordset** für jede Gruppe resultierende, in das untergeordnete Element. Wenn die BY-Klausel weggelassen wird, das untergeordnete Element **Recordset** Formular wird, eine einzelne Gruppe und das übergeordnete Element **Recordset** genau eine Zeile enthält. Dies ist hilfreich zum Berechnen von "Gesamtsumme" Aggregate über das gesamte untergeordnete **Recordset**.  
  
 Das Konstrukt der SHAPE-Befehl können Sie programmgesteuert eine geformten erstellen **Recordset**. Anschließend können Sie die Bestandteile zugreifen der **Recordset** programmgesteuert oder über eine geeignete visuelle Steuerelemente. Ein Shape-Befehl wird wie jeder andere ADO-Befehlstext ausgegeben. Weitere Informationen finden Sie unter [Shape-Befehle in der Regel](../../../ado/guide/data/shape-commands-in-general.md).  
  
 Unabhängig davon, wie das übergeordnete Element **Recordset** wird gebildet, enthält es eine Kapitelspalte, die verwendet wird, um es auf ein untergeordnetes Element verknüpfen **Recordset**. Wenn Sie möchten, das übergeordnete Element **Recordset** Spalten, die Aggregate (SUM, MIN, MAX, usw.) enthalten kann auch über die untergeordneten Zeilen haben. Sowohl das übergeordnete Element und dem untergeordneten Element **Recordset** haben Spalten, die einen Ausdruck in der Zeile enthält die **Recordset**sowie Spalten sind neu und anfangs leere.  
  
 In diesem Abschnitt wird mit dem folgenden Thema fortgesetzt.  
  
-   [Visual Basic Example of Data Shaping (Visual Basic-Beispiel der Datenstrukturierung)](../../../ado/guide/data/visual-basic-example-of-data-shaping.md)
