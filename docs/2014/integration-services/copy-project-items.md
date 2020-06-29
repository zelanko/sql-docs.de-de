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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3456209c467c3b8474e130181d02304911098d2c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437977"
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
  
  
