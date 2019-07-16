---
title: CustomData (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d2884e23cbee78acacdb72e386f0e99610e9629f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135827"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


  Gibt den Wert des der **CustomData** Verbindungszeichenfolgen-Eigenschaft, wenn definiert ist, andernfalls **null**.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Die **CustomData** Funktion abrufen kann die **CustomData** Verbindung Zeichenfolgeneigenschaft und übergeben Sie eine Konfigurationseinstellung, die von MDX (Multidimensional Expressions)-Funktionen und-Anweisungen verwendet werden, z. B. [UserName (MDX)](../mdx/username-mdx.md) und [CALL-Anweisung (MDX)](../mdx/mdx-data-manipulation-call.md). Diese Funktion kann z. B. in einem dynamischen Sicherheitsausdruck verwendet werden, zum Auswählen der zulässigen/verweigerten Mengenelemente für den Zeichenfolgenwert in die **CustomData** Verbindungszeichenfolgen-Eigenschaft.  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage zeigt den Rückgabewert von der **CustomData** Funktion in einem berechneten Measure:  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
