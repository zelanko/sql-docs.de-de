---
title: Zeile Zeilensichtbarkeit (Dialogfeld) (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 128f101a1bc43ac27c30a24b2b220ff09f59d2e8
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015421"
---
# <a name="row-visibility-dialog-box-report-builder"></a>Zeilensichtbarkeit (Dialogfeld) (Berichts-Generator)
  Mit dem Dialogfeld **Sichtbarkeit anzeigen** können Sie die ausgewählte Zeile beim ersten Ausführen des Berichts anzeigen oder ausblenden oder die Sichtbarkeit der Zeile mit einem anderen Berichtselement aktivieren bzw. deaktivieren.  
  
## <a name="options"></a>Optionen  
 **Bei erstmaliger Ausführung des Berichts**  
 Wählen Sie eine Option aus, um die ursprüngliche Anzeige der Zeile im Bericht anzugeben.  
  
 **Anzeigen**  
 Wählen Sie diese Option aus, um die Zeile anzuzeigen.  
  
 **Hide**  
 Wählen Sie diese Option aus, um die Zeile auszublenden.  
  
 **Je nach Ausdruck einblenden / ausblenden**  
 Wählen Sie diese Option aus, um die ursprüngliche Sichtbarkeit mithilfe eines Ausdrucks zu variieren.  
  
 Geben Sie einen Ausdruck ein, der das Element ausblendet, wenn der `Boolean` Wert `True` ausgewertet wird, oder der das Element anzeigt, wenn `False` ausgewertet wird. Klicken Sie auf die **Ausdrucksschaltfläche** (*fx*), um den Ausdruck zu bearbeiten.  
  
 **Sichtbarkeit kann von diesem Berichtselement ein-/ausgeschaltet werden**  
 Wählen Sie diese Option aus, um ein Umschaltbild anzuzeigen, mit dem der Benutzer diese Zeile in einem HTML Berichts-Viewer anzeigen oder ausblenden kann.  
  
 Sie müssen den Namen eines Textfelds im Bericht eingeben oder wählen, in dem ein Umschaltbild angezeigt werden soll. Beispiel: Textbox1 Das gewählte Textfeld muss im aktuellen oder enthaltenden Bereich für dieses Berichtselement enthalten sein. Beispiel: Wenn Sie die Sichtbarkeit von Zeilen umschalten möchten, die mit einer untergeordneten Gruppe verknüpft sind, wählen Sie ein Textfeld in einer Zeile, die mit der übergeordneten Gruppe verknüpft ist. Wählen Sie ein Textfeld, das in demselben enthaltenden Bereich enthalten ist wie das Diagramm, um die Sichtbarkeit eines Diagramms umzuschalten. Beispiel: der Berichtshauptteil oder ein Rechteck.  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Hinzufügen einer Erweiterungs- oder Reduzieraktion zu einem Element (Berichts-Generator und SSRS)](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Bilder &#40;Berichts-Generator und SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
