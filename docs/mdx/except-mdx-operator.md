---
title: '- (Ausnahme:) (MDX) | Microsoft Docs'
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '-'
dev_langs:
- kbMDX
helpviewer_keywords:
- Except operator [MDX]
- '- (except operator)'
ms.assetid: 8971a09d-b254-4c4c-a099-103664783589
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 17fd5aa25df6119e7b848b2ad06d00d6daeb31af
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="except-mdx-operator"></a>EXCEPT-Operator (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Führt eine Mengenoperation aus, die die Differenz zwischen zwei Mengen zurückgibt. Dabei werden doppelte Werte entfernt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set_Expression - Set_Expression  
```  
  
#### <a name="parameters"></a>Parameter  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine Menge mit Elementen, die nicht in beiden angegebenen Parametern vorkommen.  
  
## <a name="remarks"></a>Hinweise  
 Die **- (außer)** Operator ist funktionell gleichwertig mit der [außer](../mdx/except-mdx-function.md) Funktion.  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt die Verwendung dieses Operators:  
  
```  
// This query shows the quantity of orders for all product categories  
// with the exception of Components.  
SELECT   
   [Measures].[Order Quantity] ON COLUMNS,  
   [Product].[Product Categories].[All].Children   
   - [Product].[Product Categories].[Components] ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Operatorreferenz &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
