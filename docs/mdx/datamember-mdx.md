---
title: DataMember (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4395f0ff113c8549ec2250d5fa87d37090627b3c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68892914"
---
# <a name="datamember-mdx"></a>DataMember (MDX)


  Gibt das systemgenerierte Datenelement zurück, das einem Nicht-Blattelement einer Dimension zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Argumente  
 *Member_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der ein Element zurückgibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion wird für nicht Blatt Elemente in einer beliebigen Hierarchie verwendet und kann vom Befehl " [Update CUBE-Anweisung (MDX)](../mdx/mdx-data-manipulation-update-cube.md) " verwendet werden, um Daten direkt an ein nicht Blatt Element zurückzuschreiben, anstatt in die Nachfolger Elemente des Blatt Elements.  
  
> [!NOTE]  
>  Gibt das angegebene Element zurück, wenn es ein Blattelement ist, oder wenn das Nichtblattelement über keine dazugehörigen Datenelemente verfügt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die **DataMember** -Funktion in einem berechneten Measure verwendet, um das Vertriebs Kontingent für jeden einzelnen Mitarbeiter anzuzeigen:  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [MDX-Funktionsreferenz &#40;MDX-&#41;](../mdx/mdx-function-reference-mdx.md)   
 [Wichtige Konzepte in MDX-&#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)  
  
  
