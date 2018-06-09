---
title: UserName (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f8c08855d70d6a880607cc4310e6adcabbf7d9ad
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743479"
---
# <a name="username-mdx"></a>UserName (MDX)


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
  
  
