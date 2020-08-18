---
description: CustomData (MDX)
title: CustomData (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ed7bfe2841caf9bd5b2c6e6caf102323db6d62ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413166"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


  Gibt den Wert der **CustomData** -Verbindungs Zeichenfolgen-Eigenschaft zurück, sofern definiert. andernfalls **null**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die **CustomData** -Funktion kann die **CustomData** -Verbindungs Zeichenfolgen-Eigenschaft abrufen und eine Konfigurationseinstellung übergeben, die von MDX-Funktionen und-Anweisungen (Multidimensional Expressions) verwendet wird, wie z. b. [username (MDX)](../mdx/username-mdx.md) und [callstatement (MDX)](../mdx/mdx-data-manipulation-call.md). Diese Funktion kann z. b. in einem dynamischen Sicherheits Ausdruck verwendet werden, um die zulässigen/verweigerten Satz Elemente für den Zeichen folgen Wert in der **CustomData** -Verbindungs Zeichenfolgen-Eigenschaft auszuwählen.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage zeigt den Wert an, der von der **CustomData** -Funktion in einem berechneten Measure zurückgegeben wird:  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
