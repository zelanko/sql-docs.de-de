---
title: Angeben eines Knoten Tests im Speicherort Pfad (SQLXML)
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
ms.openlocfilehash: f94f155ee86df6daf0c039a18f27c30e294d57df
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75254737"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Angeben eines Knotentests unter dem Speicherortpfad (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ein Knotentest gibt den vom Positionsschritt ausgewählten Knotentyp an. Jede**Achse (unter**geordnetes Element, über **geordnetes**Element, **Attribut**oder **Self**) verfügt über einen Prinzipal Knotentyp. Für die **Attribut** Achse ist ** \< **der Haupt Knotentyp Attribute>. Für die übergeordnete **, unter** **geordnete**und die **Self** -Achse ist ** \< **der Haupt Knotentyp Element>.  
  
> [!NOTE]  
>  Der Platzhalterknotentest * (z. B. `child::*`) wird nicht unterstützt.  
  
## <a name="node-test-example-1"></a>Knoten Test: Beispiel 1  
 Der Speicherort `child::Customer` Pfad wählt ** \<Kunden>** untergeordneten Elementen des Kontext Knotens aus.  
  
 In diesem Beispiel ist `child` die Achse, und `Customer` ist der Knotentest. Der Haupt Knotentyp für **die untergeordnete** Achse ist ** \<Element>**. Daher ist der Knoten Test true, wenn der ** \<Kunde>** Knoten ein ** \<Element>** Knoten ist. Wenn der Kontext Knoten über keine ** \<Kunden>** untergeordneten Elemente verfügt, wird ein leerer Satz von Knoten zurückgegeben.  
  
## <a name="node-test-example-2"></a>Knotentest: Beispiel 2  
 Der Speicherort `attribute::CustomerID` Pfad wählt das **CustomerID-** Attribut des Kontext Knotens aus.  
  
 Im Beispiel ist `attribute` die Achse, und `CustomerID` ist der Knotentest. Der Haupt Knotentyp der **Attribut** Achse ist ** \<Attribut>**. Daher ist der Knoten Test true, wenn **CustomerID** ein ** \<Attribut>** Knoten ist. Wenn der Kontext Knoten über keine **CustomerID**verfügt, wird ein leerer Knoten Satz zurückgegeben.  
  
> [!NOTE]  
>  In dieser Implementierung von XPath wird ein Fehler generiert, wenn ein Location-Step auf ein ** \<Element>** oder ein ** \<Attribut>** Typ verweist, der nicht im Schema deklariert ist. Dies unterscheidet sich von der Implementierung von XPath in MSXML, bei der ein leerer Knotensatz zurückgegeben wird.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Abgekürzte Syntax für die Achsen  
 Es wird die folgende abgekürzte Syntax für den Speicherortpfad unterstützt:  
  
-   
  `attribute::` kann als `@` abgekürzt werden.  
  
     Der Speicherortpfad `Customer[@CustomerID="ALFKI"]` entspricht `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   
  `child::` kann von einem Speicherortschritt ausgelassen werden.  
  
     Daher ist **Child** die Standard Achse. Der Speicherortpfad `Customer/Order` entspricht `child::Customer/child::Order`.  
  
-   
  `self::node()` kann zu einem Punkt (.) abgekürzt werden, und `parent::node()` kann zu zwei Punkten (..) abgekürzt werden.  
  
  
