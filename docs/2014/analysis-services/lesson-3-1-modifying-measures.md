---
title: Ändern von Measures | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7bd48810-15ce-45ff-862b-372d08606995
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 663ef21dc9c4d0f3698ae468637fe0a8fd55a16e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66078900"
---
# <a name="modifying-measures"></a>Ändern von Measures
  Sie können die **FormatString** -Eigenschaft verwenden, um Formatierungseinstellungen zu definieren, die die Darstellung von Measures steuern. In dieser Aufgabe geben Sie Formatierungseigenschaften für die Währungs- und Prozentsatzmeasures im [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube an.  
  
### <a name="to-modify-the-measures-of-the-cube"></a>So ändern Sie die Measures des Cubes  
  
1.  Wechseln Sie zur Registerkarte **Cubestruktur** des Cube-Designers für den [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial-Cube, erweitern Sie die **Internet Sales** -Measuregruppe im Bereich **Measures** , klicken Sie mit der rechten Maustaste auf **Order Quantity**, und klicken Sie anschließend auf **Eigenschaften**.  
  
2.  Klicken Sie im Eigenschaftenfenster auf das Pushpin-Symbol **Automatisch im Hintergrund** , um das Eigenschaftenfenster offen zu halten.  
  
     Das Ändern von Eigenschaften für eine Reihe von Elementen ist einfacher, wenn das Eigenschaftenfenster geöffnet bleibt.  
  
3.  Klicken Sie im Eigenschaftenfenster auf die Liste **FormatString** , und geben Sie anschließend **#,#** ein.  
  
4.  Klicken Sie auf der Symbolleiste der Registerkarte **Cubestruktur** auf der linken Seite auf das Symbol **Measuresraster anzeigen** .  
  
     In der Rasteransicht können Sie mehrere Measures gleichzeitig auswählen.  
  
5.  Wählen Sie eine der folgenden Measures aus. Um mehrere Measures auszuwählen, halten Sie beim Klicken die STRG-TASTE gedrückt:  
  
    -   **Unit Price**  
  
    -   **Extended Amount**  
  
    -   **Discount Amount**  
  
    -   **Product Standard Cost**  
  
    -   **Total Product Cost**  
  
    -   **Sales Amount**  
  
    -   **Tax Amt**  
  
    -   **Freight (Fracht)**  
  
6.  Wählen Sie im Eigenschaftenfenster in der **FormatString** -Liste **Currency**aus.  
  
7.  Wählen Sie im Dropdown-Listenfeld oben im Eigenschaftenfenster (rechts unterhalb der Titelleiste) das Measure **Unit Price Discount Pct**und anschließend in der Liste **FormatString** die Option **Percent** aus.  
  
8.  Ändern Sie `Unit Price Discount Percentage`im Eigenschaftenfenster die **Name** -Eigenschaft für das **Unit Price discount PCT** -Measure in.  
  
9. Klicken Sie im Bereich Measures auf **Tax Amt** , und ändern Sie den Namen dieses `Tax Amount` **Measures** in.  
  
10. Klicken Sie im Eigenschaftenfenster auf das Symbol **Automatisch im Hintergrund** , um das Eigenschaftenfenster auszublenden, und anschließend auf der Symbolleiste der Registerkarte **Cubestruktur** auf **Measuresstruktur anzeigen** .  
  
11. Klicken Sie im Menü **Datei** auf **Alle speichern**.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Ändern der Customer-Dimension](lesson-3-2-modifying-the-customer-dimension.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Definieren von Daten Bank Dimensionen](multidimensional-models/define-database-dimensions.md)   
 [Konfigurieren von Measureeigenschaften](multidimensional-models/configure-measure-properties.md)  
  
  
