---
title: Logische Ausdrücke (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- logical operators [SQL Server], XQuery
- effective Boolean value [XQuery]
- logical expressions [XQuery]
- EBV
- expressions [XQuery], logical
ms.assetid: de94cd2e-2d48-49fb-9ebd-a2d90c79bf62
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b1dc7b961dd0b85824ea180cbc4815d5488a360
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68004508"
---
# <a name="logical-expressions-xquery"></a>Logische Ausdrücke (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery unterstützt die logischen **and** -und **or** -Operatoren.  
  
```  
expression1 and expression2  
expression1 or expression2  
```  
  
 Die Test Ausdrücke, `expression1,``expression2`, in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] können zu einer leeren Sequenz, einer Sequenz von einem oder mehreren Knoten oder einem einzelnen booleschen Wert führen. Basierend auf dem Ergebnis wird der effektive boolesche Wert auf folgende Weise bestimmt:  
  
-   Wenn der Testausdruck eine leere Sequenz ergibt, ist das Ergebnis des Ausdrucks False.  
  
-   Wenn der Testausdruck einen einzelnen booleschen Wert ergibt, gilt dieser Wert als Ergebnis des Ausdrucks.  
  
-   Wenn der Testausdruck eine Sequenz aus einem oder mehreren Knoten ergibt, ist das Ergebnis des Ausdrucks True.  
  
-   Anderenfalls wird ein statischer Fehler ausgegeben.  
  
 Der logische **and** -Operator und der **or** -Operator werden dann auf die resultierenden booleschen Werte der Ausdrücke mit der logischen Standard Semantik angewendet.  
  
 Mit der folgenden Abfrage werden die kleinen Bilder des <`Picture`>-Elements für ein bestimmtes Produktmodell aus dem Produktkatalog abgerufen. Beachten Sie, dass der Katalog für jedes Produktbeschreibungsdokument eine oder mehrere Produktabbildungen mit verschiedenen Attributen wie z. B. Größe und Ansicht speichern kann.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     for $F in /PD:ProductDescription/PD:Picture[PD:Size="small"   
                                                 and PD:Angle="front"]  
     return   
         $F   
    ') as Result  
FROM  Production.ProductModel  
where ProductModelID=19  
```  
  
 Dies ist das Ergebnis:  
  
```  
<PD:Picture   
  xmlns:PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
  <PD:Angle>front</PD:Angle>  
  <PD:Size>small</PD:Size>  
  <PD:ProductPhotoID>31</PD:ProductPhotoID>  
</PD:Picture>  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [XQuery-Ausdrücke](../xquery/xquery-expressions.md)  
  
  
