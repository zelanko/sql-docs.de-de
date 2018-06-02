---
title: UserName (MDX) | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 887af13c84fd06ead5a36564c0dda740a5f6d0b0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581352"
---
# <a name="username-mdx"></a>UserName (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Gibt den Domänennamen und den Benutzernamen der aktuellen Verbindung zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>Hinweise  
 Der zurückgegebene Wert ist eine Zeichenfolge folgenden Formats:  
  
 *Domänenname\Benutzername*  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Benutzername des Benutzers zurückgegeben, der die Abfrage ausführt.  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
