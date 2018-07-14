---
title: Spalte Zeilensichtbarkeit (Dialogfeld) (Berichts-Generator) | Microsoft-Dokumentation
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
- "10127"
ms.assetid: 0c030cab-6087-45a5-99f0-c7bd693f20a1
caps.latest.revision: 12
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6a91788f90fc5fb4e6afddf5a7b7e60c49cbfb49
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205020"
---
# <a name="column-visibility-dialog-box-report-builder"></a>Spaltensichtbarkeit (Dialogfeld) (Berichts-Generator)
  Mithilfe des Dialogfelds **Spaltensichtbarkeit** können Sie die ausgewählte Spalte beim ersten Ausführen des Berichts anzeigen oder ausblenden oder die Sichtbarkeit der Spalte mit einem anderen Berichtselement aktivieren bzw. deaktivieren.  
  
## <a name="options"></a>Tastatur  
 **Bei erstmaliger Ausführung des Berichts**  
 Wählen Sie eine Option aus, um die ursprüngliche Anzeige des Berichtselements im Bericht anzugeben.  
  
 **Anzeigen**  
 Wählen Sie diese Option aus, um die Spalte anzuzeigen.  
  
 **Ausblenden**  
 Wählen Sie diese Option aus, um die Spalte auszublenden.  
  
 **Je nach Ausdruck einblenden / ausblenden**  
 Wählen Sie diese Option aus, um die ursprüngliche Sichtbarkeit mithilfe eines Ausdrucks zu variieren.  
  
 Geben Sie einen Ausdruck, der ergibt eine `Boolean` Wert `True` das Element ausblendet und `False` das Element anzeigt. Klicken Sie auf die Schaltfläche „Ausdruck“ (*fx*), um den Ausdruck zu bearbeiten.  
  
 **Sichtbarkeit kann von diesem Berichtselement ein-/ausgeschaltet werden**  
 Wählen Sie diese Option aus, um ein Umschaltbild anzuzeigen, mit dem der Benutzer diese Spalte in einem HTML Berichts-Viewer anzeigen oder ausblenden kann.  
  
 Sie müssen den Namen eines Textfelds im Bericht eingeben oder wählen, in dem ein Umschaltbild angezeigt werden soll. Beispiel: Textbox1 Das gewählte Textfeld muss im aktuellen oder enthaltenden Bereich für dieses Berichtselement enthalten sein. Beispiel: Wenn Sie die Sichtbarkeit von Zeilen umschalten möchten, die mit einer untergeordneten Gruppe verknüpft sind, wählen Sie ein Textfeld in einer Zeile, die mit der übergeordneten Gruppe verknüpft ist. Wählen Sie ein Textfeld, das in demselben enthaltenden Bereich enthalten ist wie das Diagramm, um die Sichtbarkeit eines Diagramms umzuschalten. Beispiel: der Berichtshauptteil oder ein Rechteck.  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiele für Ausdrücke &#40;Berichts-Generator und SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md)   
 [Hinzufügen einer Erweiterungs- oder Reduzieraktion zu einem Element (Berichts-Generator und SSRS)](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [Images &#40;Berichts-Generator und SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Bildeigenschaften (Dialogfeld), Allgemein (Berichts-Generator und SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
