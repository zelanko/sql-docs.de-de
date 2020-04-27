---
title: Erstellen von benutzerdefinierten Hierarchien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- user-defined hierarchies [Analysis Services]
ms.assetid: 16715b85-0630-4a8e-99b0-c0d213cade26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1a1106c4b374b34351e3375adae102686f7e41fe
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072567"
---
# <a name="create-user-defined-hierarchies"></a>Erstellen von benutzerdefinierten Hierarchien
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ermöglicht das Erstellen benutzerdefinierter Hierarchien. Eine Hierarchie ist eine Auflistung von Ebenen, die auf Attributen basiert. So kann beispielsweise eine Zeithierarchie die Ebenen Jahr, Quartal, Monat, Woche und Tag enthalten. In einigen Hierarchien impliziert jedes Elementattribut das jeweils übergeordnete Elementattribut. Dies wird auch als natürliche Hierarchie bezeichnet. Eine Hierarchie kann von Endbenutzern verwendet werden, um Cubedaten zu durchsuchen. Zum Definieren von Hierarchien verwenden Sie den Bereich Hierarchien des Dimensions-Designers in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Wenn Sie eine benutzerdefinierte Hierarchie erstellen, kann die Hierarchie *unregelmäßig*werden. In einer unregelmäßigen Hierarchie befindet sich das logisch übergeordnete Element mindestens eines Elements nicht auf der Ebene unmittelbar über dem betreffenden Element. Wenn Sie über eine unregelmäßige Hierarchie verfügen, können Sie festlegen, ob die fehlenden Elemente sichtbar sind und wie sie angezeigt werden sollen. Weitere Informationen finden Sie unter [Unregelmäßige Hierarchien](user-defined-hierarchies-ragged-hierarchies.md).  
  
> [!NOTE]  
>  Weitere Informationen zu Leistungsproblemen im Zusammenhang mit dem Design und der Konfiguration von benutzerdefinierten Hierarchien finden Sie im [SQL Server 2005 Analysis Services Performance Guide](https://docsbay.net/Microsoft-SQL-Server-2005-Analysis-Services-Performance-Guide).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaften der Benutzer Hierarchie](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [Eigenschaften der Ebene &#91;&#93;](../multidimensional-models-olap-logical-dimension-objects/user-hierarchies-level-properties.md)   
 [Über-und untergeordnete Hierarchie](parent-child-dimension.md)  
  
  
