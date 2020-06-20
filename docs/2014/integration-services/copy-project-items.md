---
title: Projekt Elemente kopieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Integration Services], copying
- packages [Integration Services], copying
- copying data source views
- copying data sources
- copying packages
- data source views [Integration Services], copying
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 32b5f3f11bb15576ca30b83f1c0709cb4b77ff6d
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84917480"
---
# <a name="copy-project-items"></a>Kopieren von Projektelementen
  In diesem Thema wird beschrieben, wie Sie Objekte in einem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt oder zwischen [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekten kopieren können. Sie können Objekte auch zwischen anderen Typen von [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] -Projekten, [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]kopieren. Für den Kopiervorgang zwischen den Projekten müssen die Projekte Teil derselben [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] -Projektmappe sein. Weitere Informationen finden Sie unter [Integration Services-Projekte &#40;SSIS&#41;](integration-services-ssis-projects-and-solutions.md).  
  
### <a name="to-copy-project-level-items"></a>So kopieren Sie Projektebenenelemente  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt bzw. die Projektmappe, mit dem bzw. mit der Sie arbeiten möchten.  
  
2.  Erweitern Sie das Projekt und den Elementordner, aus dem Sie kopieren möchten.  
  
3.  Klicken Sie mit der rechten Maustaste auf das Element, und klicken Sie anschließend auf **Kopieren**.  
  
4.  Klicken Sie mit der rechten Maustaste auf das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Projekt, in das kopiert werden soll, und klicken Sie auf **Einfügen**.  
  
     Die Elemente werden automatisch in den richtigen Ordner kopiert. Wenn Sie in das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt Elemente kopieren, die keine Pakete darstellen, werden die Elemente in den Ordner **Sonstiges** kopiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services &#40;SSIS-&#41; Paketen](../../2014/integration-services/integration-services-ssis-packages.md)   
 [Kopieren von Paketobjekten](../../2014/integration-services/copy-package-objects.md)  
  
  
