---
title: Angeben eines Knoten Tests im Speicherort Pfad (SQLXML)
description: Erfahren Sie, wie Sie einen Knoten Test im Speicherort Pfad einer SQLXML 4,0 XPath-Abfrage angeben.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e0b7934b73589f71e5152bff33b2080c6eeb353e
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85649749"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Angeben eines Knotentests unter dem Speicherortpfad (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Ein Knotentest gibt den vom Positionsschritt ausgewählten Knotentyp an. Jede**Achse (unter**geordnetes Element, über **geordnetes**Element, **Attribut**oder **Self**) verfügt über einen Prinzipal Knotentyp. Für die **Attribut** Achse ist der Haupt Knotentyp **\<attribute>** . Für die übergeordnete **, unter** **geordnete**und die **Self** -Achse ist der Haupt Knotentyp **\<element>** .  
  
> [!NOTE]  
>  Der Platzhalterknotentest * (z. B. `child::*`) wird nicht unterstützt.  
  
## <a name="node-test-example-1"></a>Knoten Test: Beispiel 1  
 Der Speicherort Pfad wählt untergeordnete `child::Customer` **\<Customer>** Elemente des Kontext Knotens aus.  
  
 In diesem Beispiel ist `child` die Achse, und `Customer` ist der Knotentest. Der Haupt Knotentyp für **die untergeordnete** Achse ist **\<element>** . Daher ist der Knoten Test true, wenn der **\<Customer>** Knoten ein- **\<element>** Knoten ist. Wenn der Kontext Knoten keine untergeordneten Elemente besitzt **\<Customer>** , wird eine leere Gruppe von Knoten zurückgegeben.  
  
## <a name="node-test-example-2"></a>Knotentest: Beispiel 2  
 Der Speicherort Pfad `attribute::CustomerID` wählt das **CustomerID-** Attribut des Kontext Knotens aus.  
  
 Im Beispiel ist `attribute` die Achse, und `CustomerID` ist der Knotentest. Der Haupt Knotentyp der **Attribut** Achse ist **\<attribute>** . Daher ist der Knoten Test true, wenn **CustomerID** ein **\<attribute>** Knoten ist. Wenn der Kontext Knoten über keine **CustomerID**verfügt, wird ein leerer Knoten Satz zurückgegeben.  
  
> [!NOTE]  
>  In dieser Implementierung von XPath wird ein Fehler generiert, wenn ein Location-Step auf einen **\<element>** oder einen Typ verweist, **\<attribute>** der nicht im Schema deklariert ist. Dies unterscheidet sich von der Implementierung von XPath in MSXML, bei der ein leerer Knotensatz zurückgegeben wird.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Abgekürzte Syntax für die Achsen  
 Es wird die folgende abgekürzte Syntax für den Speicherortpfad unterstützt:  
  
-   `attribute::` kann als `@` abgekürzt werden.  
  
     Der Speicherortpfad `Customer[@CustomerID="ALFKI"]` entspricht `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` kann von einem Speicherortschritt ausgelassen werden.  
  
     Daher ist **Child** die Standard Achse. Der Speicherortpfad `Customer/Order` entspricht `child::Customer/child::Order`.  
  
-   `self::node()` kann zu einem Punkt (.) abgekürzt werden, und `parent::node()` kann zu zwei Punkten (..) abgekürzt werden.  
  
  
