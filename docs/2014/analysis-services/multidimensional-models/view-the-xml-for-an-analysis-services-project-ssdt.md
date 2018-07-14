---
title: Anzeigen des XML für eine Analysis-Projekt (SSDT Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [Analysis Services], viewing XML
ms.assetid: dd1a4bc6-57b5-47df-8619-09f921aa6351
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: df5f976c08f6c16b73628ce96b459f6fd8b0fc5b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187227"
---
# <a name="view-the-xml-for-an-analysis-services-project-ssdt"></a>Anzeigen des XML für ein Analysis Services-Projekt (SSDT)
  Wenn Sie eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Datenbank im Projektmodus verwenden, wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] eine XML-Definition für jedes im Projektordner enthaltene Objekt erstellt. Sie können die Inhalte der XML-Datei für jedes Objekt innerhalb von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]anzeigen. Die XML-Datei kann auch direkt bearbeitet werden, jedoch wird in den meisten Situationen davon abgeraten, da Sie Änderungen vornehmen können, die die Unlesbarkeit der XML-Datei in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]bewirken.  
  
> [!NOTE]  
>  Sie können den XML-Code nicht für ein Gesamtprojekt, sondern nur für die jeweiligen Objekte anzeigen, da für jedes Objekt eine eigene Datei vorhanden ist. Die einzige Möglichkeit zum Anzeigen des Codes für ein Gesamtprojekt besteht, das Projekt zu erstellen und anzeigen den ASSL-code in die \<Projektname > .asdatabase-Datei.  
  
### <a name="to-view-the-xml-code-for-an-object"></a>So zeigen Sie den XML-Code für ein Objekt an  
  
1.  Öffnen Sie das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
2.  Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Objekt, und klicken Sie dann auf **Code anzeigen**.  
  
     Der XML-Code des Objekts wird in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Analysis Services-Projekten &#40;SSDT&#41;](build-analysis-services-projects-ssdt.md)  
  
  
