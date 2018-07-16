---
title: Angeben eines Knotentests unter dem Speicherortpfad (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a8f383e8c1a8fbf16d10d4f8633d1e05a385cd74
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37307580"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>Angeben eines Knotentests unter dem Speicherortpfad (SQLXML 4.0)
  Ein Knotentest gibt den vom Positionsschritt ausgewählten Knotentyp an. Jede Achse (`child`, `parent`, `attribute`, oder `self`) hat einen Hauptknotentyp. Für die `attribute` Achse, der primäre Knotentyp ist  **\<Attribut >**. Für die `parent`, `child`, und `self` Achsen, der primäre Knotentyp ist  **\<Element >**.  
  
> [!NOTE]  
>  Der Platzhalterknotentest * (z. B. `child::*`) wird nicht unterstützt.  
  
## <a name="node-test-example-1"></a>Knotentest: Beispiel 1  
 Der Pfad zum Speicherort `child::Customer` wählt  **\<Kunden >** untergeordneten-Elemente des Kontextknotens aus.  
  
 In diesem Beispiel ist `child` die Achse, und `Customer` ist der Knotentest. Der primäre Knotentyp für die `child` Achse ist  **\<Element >**. Aus diesem Grund ist der Knotentest TRUE, wenn die  **\<Kunden >** Knoten ist ein  **\<Element >** Knoten. Wenn der Kontextknoten keine  **\<Kunden >** untergeordneten Elemente ein leerer Satz Knoten zurückgegeben.  
  
## <a name="node-test-example-2"></a>Knotentest: Beispiel 2  
 Der Pfad zum Speicherort `attribute::CustomerID` wählt die **"CustomerID"** Attribut des Kontextknotens aus.  
  
 Im Beispiel ist `attribute` die Achse, und `CustomerID` ist der Knotentest. Der primäre Knotentyp, der die `attribute` Achse ist  **\<Attribut >**. Aus diesem Grund ist der Knotentest TRUE, wenn **"CustomerID"** ist ein  **\<Attribut >** Knoten. Wenn der Kontextknoten keine **"CustomerID"**, wird ein leerer Satz Knoten zurückgegeben.  
  
> [!NOTE]  
>  In dieser Implementierung von XPath, wenn ein speicherortschritt ein  **\<Element >** oder  **\<Attribut >** Typ, der nicht im Schema deklariert ist, wird ein Fehler generiert. Dies unterscheidet sich von der Implementierung von XPath in MSXML, bei der ein leerer Knotensatz zurückgegeben wird.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>Abgekürzte Syntax für die Achsen  
 Es wird die folgende abgekürzte Syntax für den Speicherortpfad unterstützt:  
  
-   `attribute::` kann als `@` abgekürzt werden.  
  
     Der Speicherortpfad `Customer[@CustomerID="ALFKI"]` entspricht `child::Customer[attribute::CustomerID="ALFKI"]`.  
  
-   `child::` kann von einem Speicherortschritt ausgelassen werden.  
  
     Daher ist `child` die Standardachse. Der Speicherortpfad `Customer/Order` entspricht `child::Customer/child::Order`.  
  
-   `self::node()` kann zu einem Punkt (.) abgekürzt werden, und `parent::node()` kann zu zwei Punkten (..) abgekürzt werden.  
  
  
