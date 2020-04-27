---
title: Anzeigen des XML-Codes für ein Analysis Services-Projekt (SSDT) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f4826be0fd38118e94921f63e02882935132a4d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072480"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Anzeigen des XML für ein Analysis Services-Projekt (SSDT)
  Wenn Sie eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank im Projektmodus verwenden, wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] eine XML-Definition für jedes im Projektordner enthaltene Objekt erstellt. Sie können die Inhalte der XML-Datei für jedes Objekt innerhalb von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]anzeigen. Die XML-Datei kann auch direkt bearbeitet werden, jedoch wird in den meisten Situationen davon abgeraten, da Sie Änderungen vornehmen können, die die Unlesbarkeit der XML-Datei in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]bewirken.  
  
> [!NOTE]  
>  Sie können den XML-Code nicht für ein Gesamtprojekt, sondern nur für die jeweiligen Objekte anzeigen, da für jedes Objekt eine eigene Datei vorhanden ist. Die einzige Möglichkeit, den Code für ein gesamtes Projekt anzuzeigen, besteht darin, das Projekt zu erstellen und den ASSL- \<Code im Projektnamen>. asdatabase-Datei anzuzeigen.  
  
### <a name="to-view-the-xml-code-for-an-object"></a>So zeigen Sie den XML-Code für ein Objekt an  
  
1.  Öffnen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Objekt, und klicken Sie dann auf **Code anzeigen**.  
  
     Der XML-Code des Objekts wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Analysis Services-Projekten &#40;SSDT&#41;](build-analysis-services-projects-ssdt.md)  
  
  
