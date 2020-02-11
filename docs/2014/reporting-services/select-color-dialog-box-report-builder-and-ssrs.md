---
title: Farbe auswählen (Dialog Feld) (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.selectcolor.f1
- "10090"
helpviewer_keywords:
- Select Color dialog box
ms.assetid: ac7089a3-5c7b-4f53-8348-180610e86da2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6bcbbe828da811ace5df4feea5cfdf888e1e6ca5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101380"
---
# <a name="select-color-dialog-box-report-builder-and-ssrs"></a>Farbe auswählen (Dialogfeld) (Berichts-Generator und SSRS)
  Im Dialogfeld **Farbe auswählen** können Sie Farboptionen für den Hintergrund einer einzelnen Zelle oder mehrerer Zellen innerhalb eines Datenbereichs, eines Textfelds oder eines Diagramms angeben.  
  
## <a name="options"></a>Tastatur  
 **Farbauswahl**  
 Wählen Sie eine von drei Optionen aus, die angeben, wie Sie Farben auswählen möchten:  
  
-   Auswahl **-Farbkreis** Wählen Sie eine Farbe mithilfe der Farbwerte Hue/Sättigung/Helligkeit (HSB) aus.  
  
-   Auswahl **-Farbquadrat** Wählen Sie eine Farbe mit roten/grünen/blauen (RGB) Farbwerten aus.  
  
-   **Palette-Standard Farben** Wählen Sie eine Farbe aus einer vordefinierten Liste von Farbwerten aus.  
  
 **Farbkreis**  
 Verwenden Sie diese Option für HSB-Farben, da HSB-Werte in einem zylindrischen Koordinatensystem zugeordnet werden. "Farbton" ist die tatsächliche Farbe, "Sättigung" steht für die Reinheit der Farbe und "Helligkeit" entspricht der relativen Helligkeit oder Dunkelheit.  
  
 Wenn Sie eine Farbe auswählen, bestimmt das Zentrum des Kreises die Farbe. Verwenden Sie den Farbschieberegler, um den Farbton zu ändern. Die X- bzw. Y-Koordinaten stellen die Sättigungs- bzw. Helligkeitswerte dar.  
  
 **Farbquadrat**  
 Verwenden Sie diese Option für RGB-Farben, da RGB-Werte in einem kartesischen Koordinatensystem zugeordnet werden. "R" steht für den Wert für Rot, "G" für Grün und "B" für Blau.  
  
 Wenn Sie eine Farbe auswählen, bestimmt das Zentrum des Quadrats die Farbe. Verwenden Sie den Farbschieberegler, um den Bereich der ausgewählten Farbe zu ändern. Die X- und Y-Koordinaten stellen die beiden anderen Farben dar. Wenn Sie beispielsweise "Grün" auswählen, zeigt der Farbschieberegler den Bereich der grünen Werte an. Die X- bzw. Y-Koordinaten stellen die roten bzw. blauen Werte dar.  
  
 **Standardpalettenfarbe**  
 Verwenden Sie für benannte Farben aus [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] `KnownColor` der-Enumeration.  
  
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
  
 **Hue**  
 Der Dezimalwert für den Farbton der HSB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Sättigung**  
 Der Dezimalwert für die Sättigung der HSB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Brightness**  
 Der Dezimalwert für die Helligkeit der HSB-Farbe. Verwenden Sie das Drehfeld, um den Wert zu ändern, oder geben Sie einen Wert zwischen 0 und 255 ein.  
  
 **Farbbeispiel**  
 Zeigt die aktuelle Farbe in der linken Hälfte des Bereichs und die neu ausgewählte Farbe interaktiv in der rechten Hälfte des Bereichs an. Wenn keine Standardfarbe vorhanden ist, ist die linke Hälfte des Bereichs weiß. Die meisten RDL-Eigenschaften verfügen nicht über eine Standardfarbe.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Formatieren von Berichtselementen (Berichts-Generator und SSRS)](report-design/formatting-report-items-report-builder-and-ssrs.md)   
 [Formatieren von Text und Platzhaltern &#40;Berichts-Generator und SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md)  
  
  
