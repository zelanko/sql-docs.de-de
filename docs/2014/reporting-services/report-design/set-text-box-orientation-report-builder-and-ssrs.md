---
title: Festlegen der Textfeldausrichtung (Berichts-Generator und SSRS) |- Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6acffc286e913d35846b2eeb156cf1980b42fab3
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66104976"
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Festlegen der Textfeldausrichtung (Berichts-Generator und SSRS)
  Ein Textfeld kann in verschiedene Richtungen ausgerichtet werden: horizontal, vertikal (der Text wird von unten nach oben gelesen) oder um 270 Grad gedreht (Text wird von unten nach oben gelesen). Da die Ausrichtung für das Textfeld und nicht den Text selbst festgelegt wird, gilt sie für den gesamten Text im Textfeld. Sie können keine anderen Ausrichtungen für Teile des Texts angeben. Passen Sie die Spaltenbreite und die Zeilenhöhe manuell an, damit der gedrehte Text vollständig angezeigt wird.  
  
 Die WritingMode-Eigenschaft, die Sie verwenden, um die textausrichtung angegeben, ist nicht verfügbar, in der **Textfeldeigenschaften** Dialogfeld. Zum Festlegen der Eigenschaft müssen Sie das Eigenschaftenfenster öffnen und die Eigenschaft dort festlegen. Die verfügbaren Werte für die WritingMode-Eigenschaft sind **horizontale** (Text mit Schreibrichtung von links nach rechts), **vertikale** (leserichtung von oben nach unten) und **Rotate270** (leserichtung von unten nach oben). Sie müssen die Spaltenbreite und die Zeilenhöhe manuell anpassen, damit der Text vollständig angezeigt wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-text-orientation"></a>So legen Sie die Textausrichtung fest  
  
1.  Erstellen Sie einen neuen Bericht, oder öffnen Sie einen vorhandenen Bericht.  
  
2.  Wenn der Eigenschaftenbereich nicht geöffnet ist, klicken Sie auf die Registerkarte **Ansicht** , und aktivieren Sie das Kontrollkästchen **Eigenschaften** .  
  
3.  Klicken Sie auf das Textfeld, für das die Textausrichtung geändert werden soll.  
  
4.  Suchen Sie die WritingMode-Eigenschaft im Bereich Eigenschaften und in der Dropdown-Liste Wählen Sie die Ausrichtung von Text in das Textfeld angewendet.  
  
    > [!NOTE]  
    >  Wenn die Eigenschaften im Eigenschaftenbereich in Kategorien angeordnet sind, befindet sich WritingMode in der Kategorie **Lokalisierung** .  
  
5.  Wählen Sie im Listenfeld **Horizontal**, **Vertical**oder **Rotate270**aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Textfelder &#40;Berichts-Generator und SSRS&#41;](text-boxes-report-builder-and-ssrs.md)   
 [Tutorial: Formatieren von Text &#40;Berichts-Generator&#41;](../tutorial-format-text-report-builder.md)  
  
  
