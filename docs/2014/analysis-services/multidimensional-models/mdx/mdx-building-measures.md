---
title: Entwickeln von Measures in MDX | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7587e3304d1464beb7ef94cd7d3093982f394bcc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074590"
---
# <a name="building-measures-in-mdx"></a>Erstellen von Measures in MDX
  In MDX (Multidimensional Expressions) ist ein Measure ein benannter DAX-Ausdruck, der durch das Berechnen des Ausdrucks aufgelöst wird, um einen Wert in einem tabellarischen Modell zurückzugeben. Diese einfach klingende Definition hat immense Auswirkungen. Die Erstellung und Verwendung von Measures in einer MDX-Abfrage eröffnet umfassende Änderungsmöglichkeiten für Tabellendaten.  
  
> [!WARNING]  
>  Measures können nur in tabellarischen Modellen definiert werden. Wenn die Datenbank auf den mehrdimensionalen Modus festgelegt ist, tritt beim Erstellen eines Measures ein Fehler auf.  
  
 Mit dem WITH-Schlüsselwort können Sie ein Measure erstellen, das als Teil einer MDX-Abfrage definiert ist und deren Bereich daher auf die Abfrage beschränkt ist. Anschließend können Sie das Measure in einer SELECT-Anweisung von MDX verwenden. Bei dieser Vorgehensweise kann das mit dem WITH-Schlüsselwort erstellte berechnete Element geändert werden, ohne dass die SELECT-Anweisung davon beeinflusst wird. In MDX wird auf das Measure jedoch auf andere Weise als in DAX-Ausdrücken verwiesen. Zum Verweisen auf das Measure benennen Sie es als Mitglied der [Measures]-Dimension, wie im folgenden MDX-Beispiel dargestellt:  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 Nach der Ausführung werden die folgenden Daten zurückgegeben:  
  
||Total Sales Amount||  
|-|------------------------|-|  
|2001|11331808.96||  
|2002|30674773.18||  
|2003|41993729.72||  
|2004|25808962.34||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Create Member-Anweisung &#40;MDX-&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [MDX-Funktionsreferenz &#40;MDX-&#41;](/sql/mdx/mdx-function-reference-mdx)   
 [SELECT-Anweisung &#40;MDX-&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
