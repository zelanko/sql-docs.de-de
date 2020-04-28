---
title: Fehler (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 91d07c6bbb4eb4731c9a802e47cd8f4c71aa5aeb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68031228"
---
# <a name="error-mdx"></a>Error (MDX)


  Löst einen Fehler aus. Optional wird eine angegebene Fehlermeldung ausgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Error_Text*  
 Ein gültiger Zeichenfolgenausdruck, der die zurückzugebende Fehlermeldung enthält.  
  
## <a name="examples"></a>Beispiele  
 Die folgende Abfrage zeigt, wie die **Error** -Funktion in einem berechneten Measure verwendet wird:  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
