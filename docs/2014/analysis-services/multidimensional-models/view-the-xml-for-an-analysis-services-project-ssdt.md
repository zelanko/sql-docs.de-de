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
ms.openlocfilehash: 1c320145be2073c741498bed0f10732ac8d528e9
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84535553"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Anzeigen des XML für ein Analysis Services-Projekt (SSDT)
  Wenn Sie eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank im Projektmodus verwenden, wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] eine XML-Definition für jedes im Projektordner enthaltene Objekt erstellt. Sie können die Inhalte der XML-Datei für jedes Objekt innerhalb von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]anzeigen. Die XML-Datei kann auch direkt bearbeitet werden, jedoch wird in den meisten Situationen davon abgeraten, da Sie Änderungen vornehmen können, die die Unlesbarkeit der XML-Datei in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]bewirken.  
  
> [!NOTE]  
>  Sie können den XML-Code nicht für ein Gesamtprojekt, sondern nur für die jeweiligen Objekte anzeigen, da für jedes Objekt eine eigene Datei vorhanden ist. Die einzige Möglichkeit, den Code für ein gesamtes Projekt anzuzeigen, besteht darin, das Projekt zu erstellen und den ASSL-Code in der \<project name> . asdatabase-Datei anzuzeigen.  
  
### <a name="to-view-the-xml-code-for-an-object"></a>So zeigen Sie den XML-Code für ein Objekt an  
  
1.  Öffnen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Objekt, und klicken Sie dann auf **Code anzeigen**.  
  
     Der XML-Code des Objekts wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Analysis Services-Projekten &#40;SSDT&#41;](build-analysis-services-projects-ssdt.md)  
  
  
