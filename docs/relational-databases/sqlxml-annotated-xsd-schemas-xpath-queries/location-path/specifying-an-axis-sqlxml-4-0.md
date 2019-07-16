---
title: Angeben einer Achse (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- XPath queries [SQLXML], location paths
- self axis
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- location path for XPath query
- axes [SQLXML]
ms.assetid: 65631795-3389-40cf-90ea-85e9438956c5
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 29d97b92f6979a7e5bbc67185f6e5a47ff82af68
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073286"
---
# <a name="specifying-an-axis-sqlxml-40"></a>Angeben einer Achse (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
    
-   Die Achse gibt die Strukturbeziehung zwischen den vom Positionsschritt ausgewählten Knoten und dem Kontextknoten an. Die folgenden Achsen werden unterstützt: **untergeordneten**  
  
     Enthält das untergeordnete Element des Kontextknotens.  
  
     Der folgende XPath-Ausdruck (Speicherortpfad) Wählt aus dem aktuellen Kontextknoten darstellen, die alle die  **\<Kunden >** untergeordnete Elemente:  
  
    ```  
    child::Customer  
    ```  
  
     In der folgenden XPath-Abfrage ist `child` die Achse. `Customer` ist der Knotentest.  
  
-   **parent**  
  
     Enthält das übergeordnete Element des Kontextknotens.  
  
     Der folgende XPath-Ausdruck wählt alle dem  **\<Kunden >** übergeordneten Elementen von der  **\<Reihenfolge >** untergeordnete Elemente:  
  
    ```  
    child::Customer/child::Order[parent::Customer/@customerID="ALFKI"]  
    ```  
  
     Dies entspricht exakt der Angabe `child::Customer`. In dieser XPath-Abfrage sind `child` und `parent` die Achsen. `Customer` und `Order` sind die Knotentests.  
  
-   **attribute**  
  
     Enthält das Attribut des Kontextknotens.  
  
     Der folgende XPath-Ausdruck wählt den **"CustomerID"** Attribut des Kontextknotens aus:  
  
    ```  
    attribute::CustomerID  
    ```  
  
-   **self**  
  
     Enthält den Kontextknoten selbst.  
  
     Der folgende XPath-Ausdruck wählt den aktuellen Knoten aus, ist dies die  **\<Reihenfolge >** Knoten:  
  
    ```  
    self::Order  
    ```  
  
     In dieser XPath-Abfrage ist `self` die Achse und `Order` der Knotentest.  
  
  
