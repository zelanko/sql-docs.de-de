---
title: Die CustomData-Funktion (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 172915d99b231490cbdca24f70d1d38da27a1d3d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739302"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


  Gibt den Wert der **CustomData** Verbindungszeichenfolgeneigenschaft, falls definiert; andernfalls, **null**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die **CustomData** Funktion abrufen kann die **CustomData** Verbindung Zeichenfolgeneigenschaft und übergeben Sie eine Konfigurationseinstellung, die von MDX (Multidimensional Expressions)-Funktionen und Anweisungen, die verwendet werden, z. B. [UserName (MDX)](../mdx/username-mdx.md) und [aufrufen-Anweisung (MDX)](../mdx/mdx-data-manipulation-call.md). Diese Funktion kann z. B. in einem dynamischen Sicherheitsausdruck verwendet werden, wählen Sie die zulässigen/verweigerten Mengenelemente für den Zeichenfolgenwert in den **CustomData** Verbindungszeichenfolgen-Eigenschaft.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage zeigt den Rückgabewert von der **CustomData** Funktion in einem berechneten Measure:  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
