---
title: Textfelder (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10134"
- sql12.rtp.rptdesigner.textproperties.general.f1
- "10120"
- sql12.rtp.rptdesigner.textboxproperties.general.f1
ms.assetid: df49e4e3-f279-4c63-a03b-b70c095f4ba2
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 3f8135c0f0526efe1db46011e22491e96db39777
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057531"
---
# <a name="text-boxes-report-builder-and-ssrs"></a>Textfelder (Berichts-Generator und SSRS)
  Wenn Sie an ein Textfeld denken, stellen Sie sich wahrscheinlich ein eigenständiges Feld mit Text vor, wie es zum Beispiel in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office PowerPoint verwendet wird. Im Berichts-Generator entsprechen einige Textfelder dieser Vorstellung und können eigentlichen Text für Titel, Beschreibungen und Beschriftungen oder dynamischen Text basierend auf Ausdrücken enthalten. Jede Zelle in einer Tabelle oder Matrix (einem Tablix-Datenbereich) enthält jedoch auch ein Textfeld, das auf dieselbe Weise formatiert werden kann wie eigenständige Textfelder in einem Bericht.  
  
> [!NOTE]  
>  Wenn Sie einen Feldwert für ein Berichtsdataset direkt auf die Berichtsentwurfsoberfläche ziehen oder auf ein Textfeld auf der Berichtsentwurfsoberfläche, können Sie beim Ausführen des Berichts nur den ersten Wert im Resultset sehen. Um alle Werte für ein Feld zu sehen, müssen Sie das Feld in eine Tabellen- oder Matrixzelle ziehen. Auf diese Weise werden beim Ausführen des Berichts alle Werte in diesem Feld angezeigt.  
  
 Um wiederholten Text in einem Freiformlayout anzuzeigen, fügen Sie ein Textfeld in einen Listendatenbereich ein. Verwenden Sie eine Liste, wenn Sie ein Formular für mehrere Werte wiederholen möchten, z. B. ein Kundenrechnungsformular, das einmal pro Kunde wiederholt wird. Weitere Informationen finden Sie unter [listet &#40;Berichts-Generator und SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).  
  
 Verwenden Sie einen rechteckigen Container, wenn Sie das Textfeldlayout steuern möchten und unterhalb des letzten Textfelds ein Abstand gelassen werden soll. Weitere Informationen finden Sie unter [Rechtecke und Linien (Berichts-Generator und SSRS)](rectangles-and-lines-report-builder-and-ssrs.md).  
  
 Die Ausdrücke in einem Textfeld können Literaltext enthalten, auf ein Feld in der Datenbank verweisen oder Daten berechnen. Alle Ausdrücke werden als Platzhaltertext angezeigt, sodass Sie Zahlen, Farben und andere Darstellungseigenschaften formatieren können. Im gleichen Textfeld können Sie auch Platzhalter mit Literaltext kombinieren.  
  
 Sie können den Text in einem einzelnen Textfeld anhand von mehreren Schriftarten, Farben, Stilen und Aktionen formatieren. Weitere Informationen finden Sie unter [Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="GrowShrinkTextBox"></a> Vergrößern und Verkleinern eines Textfelds  
 Standardmäßig haben Textfelder eine feste Größe. Sie können zulassen, dass ein Textfeld auf Grundlage seines Inhalts verkleinert oder vertikal erweitert wird. Weitere Informationen finden Sie unter [zulassen, dass Textfelder vergrößert oder verkleinert &#40;Berichts-Generator und SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md).  
  
## <a name="orienting-a-text-box"></a>Ausrichten eines Textfelds  
 Durch das Ausrichten von Textfeldern können Sie die Lesbarkeit von Berichten verbessern, gebietsschemaspezifische Textausrichtungen unterstützen, in einem gedruckten Bericht mit fester Seitengröße eine größere Spaltenanzahl unterbringen und grafisch ansprechendere Berichte erstellen. Ein Textfeld kann in verschiedene Richtungen ausgerichtet werden: horizontal, vertikal oder um 270 Grad gedreht. Die Option für die vertikale Ausrichtung wird am häufigsten für ostasiatische Sprachen verwendet, deren Schreibrichtung von oben nach unten verläuft. In den meisten Renderern wird die Eigenschaft für das Drehen von Symbolen durch die Option für die vertikale Ausrichtung behandelt, damit der Text von oben nach unten geschrieben wird, die Zeichen jedoch nicht auf der Seite liegen. Bei anderen Sprachen wird Text, auf den die Optionen für vertikale Ausrichtung und Drehung um 270 Grad angewendet werden, seitwärts geschrieben.  
  
 Sie können Textfelder ausrichten, die wörtlichen Text, Felder aus einem Berichtsdataset oder berechnete Daten enthalten. Das Textfeld kann eigenständig im Hauptteil des Berichts, in einer Tabelle oder Matrix oder in einem Berichtskopf und -fuß verwendet werden.  
  
 Die folgende Abbildung zeigt drei Versionen eines Tabellenberichts, in dem Daten nach Monat gruppiert sind. Für das Textfeld, das den Monatswert enthält, wird eine abweichende Textfeldausrichtung verwendet.  
  
 ![Rs_Textfeldausrichtung](../media/rs-textboxorientation.gif "Rs_TextBoxOrientation")  
  
 Die Ausrichtung wird für das Textfeld festgelegt und gilt für den gesamten Text im Textfeld. Sie können keine andere Ausrichtung für Teile des Textfelds angeben.  
  
 Schnelleinstieg mit Ausrichtung von Text zu ändern, finden Sie im Abschnitt zum Drehen von Text in der [Lernprogramm: Formatieren von Text &#40;Berichts-Generator&#41;](../tutorial-format-text-report-builder.md). Weitere Informationen finden Sie unter [Festlegen der Textfeldausrichtung &#40;Berichts-Generator und SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md).  
  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 [Hinzufügen, verschieben oder Löschen von Textfeldern &#40;Berichts-Generator und SSRS&#41;](add-move-or-delete-a-text-box-report-builder-and-ssrs.md)  
  
 [Formatieren von Text in einem Textfeld &#40;Berichts-Generator und SSRS&#41;](format-text-in-a-text-box-report-builder-and-ssrs.md)  
  
 [Festlegen der Textfeldausrichtung &#40;Berichts-Generator und SSRS&#41;](set-text-box-orientation-report-builder-and-ssrs.md)  
  
 [Zulassen, dass Textfelder vergrößert oder verkleinert &#40;Berichts-Generator und SSRS&#41;](allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Formatieren von Text und Platzhaltern &#40;Berichts-Generator und SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md)   
 [Formatieren von Zahlen und Datumsangaben &#40;Berichts-Generator und SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md)  
  
  