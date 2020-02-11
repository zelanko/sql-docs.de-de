---
title: Verwenden von gespeicherten Prozeduren (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4daa38f185569e1579413870cc929a8b1b3b6570
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038003"
---
# <a name="using-stored-procedures-mdx"></a>Verwenden von gespeicherten Prozeduren (MDX)


  Sie können die Funktionalität von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] und Multidimensional Expressions (MDX) erweitern, indem sie mit .NET gespeicherte Prozeduren oder benutzerdefinierte Funktionen erstellen. Weitere Informationen finden Sie unter [ADOMD.NET Server Programming](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
 Wenn Sie auf eine gespeicherte Prozedur verweisen bzw. eine gespeicherte Prozedur aufrufen, geben Sie den Namen der Prozedur und dahinter Klammern an. In den Klammern können Sie Ausdrücke angeben. Diese Ausdrücke werden als Argumente bezeichnet und stellen die Daten bereit, die an die Parameter zu übergeben sind. Wenn Sie eine Funktion aufrufen, müssen Sie Argumentwerte für alle Parameter bereitstellen und die Argumentwerte in derselben Reihenfolge angeben, in der die Parameter in der benutzerdefinierten Funktion definiert sind.  
  
 Die folgende Beispielabfrage geht davon aus, dass Sie über eine auf dem [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Server registrierte Assembly mit dem Namen SampleAssembly verfügen:  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
> [!NOTE]  
>  Die *gespeicherte Prozedur* ist die Terminologie, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] die in für diese Arten von Funktionen verwendet wird. In früheren Versionen [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] von wurden diese Arten von Funktionen als *benutzerdefinierte Funktionen*bezeichnet.  
  
## <a name="types-of-stored-procedures"></a>Arten von gespeicherten Prozeduren  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] unterstützt sowohl COM- als auch CLR-Assemblys. CLR-Assemblys empfehlen sich wegen der für sie verfügbaren verbesserten Sicherheit. Wenn Microsoft Office Excel auf dem Server installiert ist, sind auch die Excel-Funktionen verfügbar.  
  
> [!NOTE]  
>  COM-Assemblys von Microsoft Visual Basic für Applikationen (VBA) werden automatisch registriert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;MDX-Syntax&#41;](../mdx/functions-mdx-syntax.md)  
  
  
