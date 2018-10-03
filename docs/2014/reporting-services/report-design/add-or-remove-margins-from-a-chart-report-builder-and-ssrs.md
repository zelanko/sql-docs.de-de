---
title: Hinzufügen oder Entfernen von Rändern aus einem Diagramm (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 91c43f58-5771-4d33-a54d-0e802d2f5cba
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 1dce4183ff7e873fd16ac3df8a346a600c7cb0dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48105830"
---
# <a name="add-or-remove-margins-from-a-chart-report-builder-and-ssrs"></a>Hinzufügen oder Entfernen von Rändern aus einem Diagramm (Berichts-Generator und SSRS)
  Bei Säulen- und Punktdiagrammen werden an den Enden der x-Achse automatisch Seitenränder hinzugefügt. Bei Balkendiagrammen werden an den Enden der x-Achse automatisch Seitenränder hinzugefügt. Bei allen anderen Diagrammtypen fügt das Diagramm keine Seitenränder hinzu. Die Größe der Seitenränder kann nicht geändert werden.  
  
 Dieses Thema gilt nicht für Kreis-, Ring-, Trichter- oder Pyramidendiagramme.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-enable-or-disable-side-margins"></a>So aktivieren oder deaktivieren Sie Seitenränder  
  
1.  Klicken Sie mit der rechten Maustaste auf die Achse, und wählen Sie **Achseneigenschaften**aus. Das Dialogfeld **Eigenschaften für vertikale Achsen** oder **Eigenschaften für horizontale Achsen** wird angezeigt.  
  
2.  Legen Sie auf der Seite **Achsenoptionen** die Eigenschaft **Seitenränder** fest:  
  
    -   **Automatisch:** Das Diagramm bestimmt basierend auf dem Diagrammtyp, ob ein Seitenrand hinzugefügt wird.  
  
    -   **Deaktiviert:** Balken-, Säulen- und Punktdiagramme haben keine Seitenränder.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Achsenbezeichnungen in einem Diagramm &#40;Berichts-Generator und SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [Achseneigenschaften (Dialogfeld), Achsenoptionen (Berichts-Generator und SSRS)](../axis-properties-dialog-box-axis-options-report-builder-and-ssrs.md)   
 [Angeben eines Achsenintervalls (Berichts-Generator und SSRS)](specify-an-axis-interval-report-builder-and-ssrs.md)   
 [Formatieren von Achsenbezeichnungen als Datumsangabe oder Währung (Berichts-Generator und SSRS)](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [Diagramme &#40;Berichts-Generator und SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
