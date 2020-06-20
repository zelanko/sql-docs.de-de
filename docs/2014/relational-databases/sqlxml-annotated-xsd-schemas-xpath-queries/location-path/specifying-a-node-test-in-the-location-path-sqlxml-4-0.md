---
title: Angeben eines Knoten Tests im Speicherort Pfad (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: rothja
ms.author: jroth
ms.openlocfilehash: 02f78577eab391f1774251ad2c6ca7b9a4bd2dab
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015219"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Angeben eines Knotentests unter dem Speicherortpfad (SQLXML 4.0)
  Ein Knotentest gibt den vom Positionsschritt ausgewählten Knotentyp an. Jede Achse ( `child` , `parent` , `attribute` oder `self` ) hat einen Prinzipal Knotentyp. Für die- `attribute` Achse ist der Haupt Knotentyp **\<attribute>** . Für die `parent` `child` Achsen, und `self` ist der Haupt Knotentyp **\<element>** .  
  
> [!NOTE]  
>  Der Platzhalterknotentest * (z. B. `child::*`) wird nicht unterstützt.  
  
## <a name="node-test-example-1"></a>Knoten Test: Beispiel 1  
 Der Speicherort Pfad wählt untergeordnete `child::Customer` **\<Customer>** Elemente des Kontext Knotens aus.  
  
 In diesem Beispiel ist `child` die Achse, und `Customer` ist der Knotentest. Der Haupt Knotentyp für die- `child` Achse ist **\<element>** . Daher ist der Knoten Test true, wenn der **\<Customer>** Knoten ein- **\<element>** Knoten ist. Wenn der Kontext Knoten keine untergeordneten Elemente besitzt **\<Customer>** , wird eine leere Gruppe von Knoten zurückgegeben.  
  
## <a name="node-test-example-2"></a>Knotentest: Beispiel 2  
 Der Speicherort Pfad `attribute::CustomerID` wählt das **CustomerID-** Attribut des Kontext Knotens aus.  
  
 Im Beispiel ist `attribute` die Achse, und `CustomerID` ist der Knotentest. Der Haupt Knotentyp der `attribute` Achse ist **\<attribute>** . Daher ist der Knoten Test true, wenn **CustomerID** ein **\<attribute>** Knoten ist. Wenn der Kontext Knoten über keine **CustomerID**verfügt, wird ein leerer Knoten Satz zurückgegeben.  
  
> [!NOTE]  
>  In dieser Implementierung von XPath wird ein Fehler generiert, wenn ein Location-Step auf einen **\<element>** oder einen Typ verweist, **\<attribute>** der nicht im Schema deklariert ist. Dies unterscheidet sich von der Implementierung von XPath in MSXML, bei der ein leerer Knotensatz zurückgegeben wird.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Abgekürzte Syntax für die Achsen  
 Es wird die folgende abgekürzte Syntax für den Speicherortpfad unterstützt:  
  
-   `attribute::` kann als `@` abgekürzt werden.  
  
     Der Speicherortpfad `Customer[@CustomerID="ALFKI"]` entspricht `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` kann von einem Speicherortschritt ausgelassen werden.  
  
     Daher ist `child` die Standardachse. Der Speicherortpfad `Customer/Order` entspricht `child::Customer/child::Order`.  
  
-   `self::node()` kann zu einem Punkt (.) abgekürzt werden, und `parent::node()` kann zu zwei Punkten (..) abgekürzt werden.  
  
  
