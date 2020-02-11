---
title: Ebene und Elemente (Registerkarte ' Browser ', Dimensions-Designer) (Analysis Services-Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ad602710cab83e2be25a03a4da6cce0c3407493e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078111"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a>Ebenen und Elemente (Registerkarte 'Browser', Dimensions-Designer) (Analysis Services – Mehrdimensionale Daten)
  In diesem Bereich können Sie die Elemente der aktuell ausgewählten Hierarchie und Sprache durchsuchen. Verwenden Sie die Optionen **Hierarchie** und **Sprache** im Bereich **Symbolleiste** , um eine zu durchsuchende Hierarchie oder Sprache auszuwählen. Weitere Informationen zum Symbolleistenbereich finden Sie unter [Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md).  
  
## <a name="writeback-mode"></a>Rückschreibemodus  
 Die Funktionalität dieses Bereichs ändert sich, wenn der Rückschreibemodus aktiviert wird. Für die ausgewählte Dimension muss der Schreibzugriff aktiviert sein (anders ausgedrückt, die `WriteEnabled`-Eigenschaft der Dimension muss auf den Wert True festgelegt sein), und die Dimension muss für eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz bereitgestellt werden, damit der Rückschreibemodus aktiviert werden kann.  
  
 Sie können entweder die Option **Rückschreiben** aus dem Bereich **Symbolleiste** auswählen oder mit der rechten Maustaste auf den Bereich **Ebene und Elemente** klicken und aus dem Kontextmenü die Option **Rückschreiben** auswählen, um den Rückschreibemodus zu aktivieren.  
  
 Wenn der Rückschreibemodus aktiviert ist, können Sie die folgenden zusätzlichen Aktionen im Bereich **** für Ebene und Elemente ausführen:  
  
|Aufgabe|Funktion|  
|-----------|-------------|  
|Erstellen gleichgeordneter und untergeordneter Elemente innerhalb der ausgewählten Hierarchie|Klicken Sie mit der rechten Maustaste auf das ausgewählte Element, und wählen Sie aus dem Kontextmenü entweder **Gleichgeordnetes Element erstellen**aus, um ein gleichgeordnetes Element zu erstellen, oder **Untergeordnetes Element erstellen**, um ein untergeordnetes Element zu erstellen.|  
|Verschieben eines ausgewählten Elements in der Hierarchie nach oben oder nach unten|Ziehen Sie das ausgewählte Element entweder auf das entsprechende über- bzw. untergeordnete Element, oder klicken Sie auf **Einzug vergrößern** bzw. **Einzug verkleinern** im Bereich **Symbolleiste** , um das ausgewählte Element in den Ebenen der Hierarchie noch oben bzw. unten zu verschieben.|  
|Umbenennen eines ausgewählten Elements|Klicken Sie entweder mit der rechten Maustaste auf das ausgewählte Element, und wählen Sie die Option **Umbenennen**aus, oder klicken Sie auf ein bereits ausgewähltes Element.|  
|Bearbeiten der Werte von Elementeigenschaften|Doppelklicken Sie auf den Wert in der ausgewählten Elementeigenschaft für das ausgewählte Element, um den Wert zu bearbeiten.|  
  
## <a name="options"></a>Tastatur  
 **Aktuelle Ebene**  
 Zeigt die Ebene an, zu der das aktuell ausgewählte Element unter **Struktur** gehört.  
  
 **Linde**  
 Zeigt die Elemente der aktuell ausgewählten Hierarchie und Sprache an.  
  
 Wenn Elementeigenschaften aus der Option **Elementeigenschaften** des Symbolleistenbereichs ausgewählt werden, wird jede Elementeigenschaft als eine Spalte angezeigt.  
  
 Wenn der Rückschreibemodus aktiviert ist, wird für jede Schlüsselspalte, der das Schlüsselattribut in der Dimension zugeordnet ist, eine Spalte angezeigt.  
  
## <a name="context-menu"></a>Kontextmenü  
 Die folgenden Optionen sind im Kontextmenü verfügbar, das durch Klicken mit der rechten Maustaste auf einen beliebigen Teil des Bereichs **Ebene und Elemente** für das ausgewählte Element angezeigt wird:  
  
 **Gleichgeordnetes Element erstellen**  
 Erstellt ein neues Element auf derselben Ebene wie das ausgewählte Element.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn ein Element auf einer anderen Ebene als der Ebene (Alle) ausgewählt ist.  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn der Rückschreibemodus aktiviert ist.  
  
 **Untergeordnetes Element erstellen**  
 Erstellt ein neues Element auf der nächstniedrigeren Ebene, als untergeordnetes Element des ausgewählten Elements.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn ein Element auf einer anderen Ebene als der untersten ausgewählt ist.  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn der Rückschreibemodus aktiviert ist.  
  
 **Ausschneiden**  
 Kopiert die ausgewählten Elemente in die Zwischenablage und entfernt sie aus der Hierarchie.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn ein anderes als das Element Alle ausgewählt ist.  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn der Rückschreibemodus aktiviert ist.  
  
 **Einfügen**  
 Fügt die zuvor mithilfe der Option **Ausschneiden** entfernten Elemente direkt hinter dem ausgewählten Element ein.  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn der Rückschreibemodus aktiviert ist.  
  
 **Löschen**  
 Entfernt die ausgewählten Elemente aus der Hierarchie.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn ein anderes als das Element Alle ausgewählt ist.  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn der Rückschreibemodus aktiviert ist.  
  
 **Benen**  
 Wählen Sie diese Option aus, um den Namen des ausgewählten Elements zu bearbeiten.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn ein anderes als das Element Alle ausgewählt ist.  
  
> [!NOTE]  
>  Diese Option wird nur angezeigt, wenn der Rückschreibemodus aktiviert ist.  
  
 **Elemente filtern**  
 Zeigt das Dialogfeld **Elemente filtern** an, mit dessen Hilfe Elemente gefiltert werden können, die unter **Ebene und Elemente** für die ausgewählte Hierarchie angezeigt werden. Weitere Informationen zum Dialogfeld **Elemente filtern** finden Sie unter [Dialogfeld „Elemente filtern“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).  
  
 **Alle erweitern**  
 Erweitert alle Elemente unter **Struktur**.  
  
> [!NOTE]  
>  Diese Option ist nur verfügbar, wenn ein Element auf einer anderen Ebene als der untersten ausgewählt ist.  
  
 **Alle reduzieren**  
 Reduziert alle Elemente unter **Struktur**.  
  
 **Element erweitern**  
 Erweitert das ausgewählte Element unter **Struktur**.  
  
 **Element reduzieren**  
 Reduziert das ausgewählte Element unter **Struktur**.  
  
 **Rück schreibe**  
 Wählen Sie diese Option aus, um den Rückschreibemodus zu aktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Symbolleiste &#40;Registerkarte "Browser", Dimensions-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)   
 [Browser &#40;Dimensions-Designer&#41; &#40;Analysis Services Mehrdimensionale Daten&#41;](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
