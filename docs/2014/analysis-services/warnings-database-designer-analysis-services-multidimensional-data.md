---
title: Warnungen (Datenbank-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.databasedesigner.warnings.f1
ms.assetid: 13f58b4d-f345-4fbc-ae2d-b3c8290a797d
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e00890be8fac0fb97f0887034d5c7b04c049ebd0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059884"
---
# <a name="warnings-database-designer-analysis-services---multidimensional-data"></a>Warnungen (Datenbank-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe der Registerkarte **Warnungen** können Sie Regeln anzeigen und global verwerfen sowie bestimmte Instanzen verworfener Warnungen anzeigen und erneut aktivieren. Die Registerkarte **Warnungen** enthält zwei Raster: **Entwurfswarnungsregeln** und **Verworfene Warnungen**.  
  
 **Auf die Registerkarte "Warnungen" anzeigen**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt.  
  
2.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt, klicken Sie auf **Datenbank bearbeiten**und anschließend auf die Registerkarte **Warnungen** .  
  
## <a name="design-warning-rules-grid"></a>Raster Entwurfswarnungsregeln  
 Das Raster **Entwurfswarnungsregeln** enthält alle Entwurfswarnungsregeln. Mit diesem Raster wird auch gesteuert, welche Regeln für die Datenbank aktiviert sind. Um eine Warnregel zu aktivieren oder zu deaktivieren, aktivieren bzw. deaktivieren das zugehörige Kontrollkästchen.  
  
 Das Raster **Entwurfswarnungsregeln** weist die folgenden Spalten auf:  
  
 **Beschreibung**  
 Zeigt den Namen der Regel an. Regeln werden nach Kategorien gruppiert.  
  
 **Wichtigkeit**  
 Zeigt die der Regel zugewiesene Wichtigkeit an.  
  
 **Kommentare**  
 (Optional) Ermöglicht es dem Benutzer, einen Kommentar einzugeben, der erklärt, warum die Warnung verworfen wurde.  
  
## <a name="dismissed-warnings-grid"></a>Raster Verworfene Warnungen  
 Das Raster **Verworfene Warnungen** enthält die einzelnen Warnungen, die aus der **Fehlerliste**entfernt wurden. Um eine Warnung erneut zu aktivieren, markieren Sie sie im Raster, und klicken Sie dann auf **Erneut aktivieren**.  
  
 Das Raster **Verworfene Warnungen** umfasst folgende Elemente:  
  
 **Objekt**  
 Zeigt ein Symbol an, das den Objekttyp und den Objektnamen darstellt.  
  
 **Typ**  
 Zeigt den Objekttyp an.  
  
 **Beschreibung**  
 Zeigt den Namen der Regel an.  
  
 **Wichtigkeit**  
 Zeigt die der Regel zugewiesene Wichtigkeit an.  
  
 **Kommentare**  
 Zeigt den Kommentar an, der eingegeben wurde, als die Warnung verworfen wurde. Sie können hier einen Kommentar hinzufügen oder ändern.  
  
 **Erneut aktivieren**  
 Aktiviert die ausgewählten Warnungen erneut.  
  
> [!NOTE]  
>  Wenn ein Objekt über eine Warnung verfügt, sich das Objekt aber in einem ungültigen Zustand befindet oder von Hand aus dem Projekt entfernt wurde, wird in der Liste ein Fehlersymbol neben der Warnung angezeigt. Um die Warnung zu verwerfen, wählen Sie das Objekt aus, und klicken Sie anschließend auf **Erneut aktivieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Warnungsdialogfeld verwerfen &#40;Analysis Services – mehrdimensionale Daten&#41;](dismiss-warning-dialog-box-analysis-services-multidimensional-data.md)   
 [Allgemeine &#40;Datenbank-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](general-database-designer-analysis-services-multidimensional-data.md)  
  
  