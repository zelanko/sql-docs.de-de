---
title: Wählen Sie das Dialogfeld Farbe (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.selectcolor.f1
- "10090"
helpviewer_keywords:
- Select Color dialog box
ms.assetid: ac7089a3-5c7b-4f53-8348-180610e86da2
caps.latest.revision: 10
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2b14615cb231f6df5385306ded4257a86998a56
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185774"
---
# <a name="select-color-dialog-box-report-builder-and-ssrs"></a>Farbe auswählen (Dialogfeld) (Berichts-Generator und SSRS)
  Im Dialogfeld **Farbe auswählen** können Sie Farboptionen für den Hintergrund einer einzelnen Zelle oder mehrerer Zellen innerhalb eines Datenbereichs, eines Textfelds oder eines Diagramms angeben.  
  
## <a name="options"></a>Tastatur  
 **Farbauswahl**  
 Wählen Sie eine von drei Optionen aus, die angeben, wie Sie Farben auswählen möchten:  
  
-   **Auswahl – Farbkreis** Wählen Sie anhand der HSB-Farbwerte (Hue/Saturation/Brightness – Farbton/Sättigung/Helligkeit) eine Farbe aus.  
  
-   **Auswahl – Farbquadrat** Wählen Sie anhand der RGB-Farbwerte (Red/Green/Blue – Rot/Grün/Blau) eine Farbe aus.  
  
-   **Palette – Standardfarben** Wählen Sie eine Farbe aus einer vordefinierten Liste von Farbwerten aus.  
  
 **Farbkreis**  
 Verwenden Sie diese Option für HSB-Farben, da HSB-Werte in einem zylindrischen Koordinatensystem zugeordnet werden. "Farbton" ist die tatsächliche Farbe, "Sättigung" steht für die Reinheit der Farbe und "Helligkeit" entspricht der relativen Helligkeit oder Dunkelheit.  
  
 Wenn Sie eine Farbe auswählen, bestimmt das Zentrum des Kreises die Farbe. Verwenden Sie den Farbschieberegler, um den Farbton zu ändern. Die X- bzw. Y-Koordinaten stellen die Sättigungs- bzw. Helligkeitswerte dar.  
  
 **Farbquadrat**  
 Verwenden Sie diese Option für RGB-Farben, da RGB-Werte in einem kartesischen Koordinatensystem zugeordnet werden. "R" steht für den Wert für Rot, "G" für Grün und "B" für Blau.  
  
 Wenn Sie eine Farbe auswählen, bestimmt das Zentrum des Quadrats die Farbe. Verwenden Sie den Farbschieberegler, um den Bereich der ausgewählten Farbe zu ändern. Die X- und Y-Koordinaten stellen die beiden anderen Farben dar. Wenn Sie beispielsweise "Grün" auswählen, zeigt der Farbschieberegler den Bereich der grünen Werte an. Die X- bzw. Y-Koordinaten stellen die roten bzw. blauen Werte dar.  
  
 **Standardpalettenfarbe**  
 Verwenden Sie diese Option aus der `KnownColor`-Enumeration für benannte Farben vom [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
 **Farbsystem**  
 Geben Sie RGB- oder HSB-Farben an. Diese Auswahl ändert die Anzeige auf RGB- oder HSB-Werte, die interaktiv aktualisiert werden, wenn Sie einen Farbkreis oder ein Farbquadrat für die **Farbauswahl**verwenden.  
  
 Der **Alpha** -Wert zeigt für einige Eigenschaften an, ob eine Farbe einen Transparenzwert einschließen kann. Beispiel: Diagrammreihenfüllbereich. Für Eigenschaften, die keine Transparenz unterstützen, wird dieser Wert deaktiviert.  
  
 **Rot:**  
 Der Dezimalwert für den roten Anteil der RGB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Grün:**  
 Der Dezimalwert für den grünen Anteil der RGB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Blau:**  
 Der Dezimalwert für den blauen Anteil der RGB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Alpha**  
 Der Dezimalwert für den Alpha- oder Transparenzanteil der Farbe. Wenn dieser Wert aktiviert ist, können Sie den gewünschten Transparenzgrad mit dem Schieberegler anpassen.  
  
 **Farbt.:**  
 Der Dezimalwert für den Farbton der HSB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Sättigung**  
 Der Dezimalwert für die Sättigung der HSB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Helligkeit**  
 Der Dezimalwert für die Helligkeit der HSB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Farbbeispiel**  
 Zeigt die aktuelle Farbe in der linken Hälfte des Bereichs und die neu ausgewählte Farbe interaktiv in der rechten Hälfte des Bereichs an. Wenn keine Standardfarbe vorhanden ist, ist die linke Hälfte des Bereichs weiß. Die meisten RDL-Eigenschaften verfügen nicht über eine Standardfarbe.  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Berichtselementen (Berichts-Generator und SSRS)](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Formatieren von Text und Platzhaltern &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  
