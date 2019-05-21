---
title: Attributbeziehungsdiagramm (Registerkarte Attributbeziehungs-Designer, Dimensions-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.ardiagram.f1
ms.assetid: 320989ad-bd95-43f4-a2e7-b262d66dbda7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1255cbcaffe114a47b4c7d251c37e5b3d50d6b2b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62650601"
---
# <a name="attribute-relationship-diagram-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a>Attributbeziehungsdiagramm (Registerkarte Attributbeziehungs-Designer, Dimensions-Designer) (Analysis Services – Mehrdimensionale Daten)
  Verwenden Sie den Bereich unmittelbar unter der Symbolleiste auf der Registerkarte **Attributbeziehungen** , um das Attributbeziehungsdiagramm anzuzeigen und um Attributbeziehungen zu erstellen, zu ändern und zu löschen.  
  
 **So zeigen Sie den Bereich an, der das Attributbeziehungsdiagramm enthält**  
  
-   Doppelklicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im Projektmappen-Explorer auf eine Dimension, um den Dimensions-Designer zu öffnen, und klicken Sie dann auf die Registerkarte **Attributbeziehung** .  
  
## <a name="using-the-attribute-relationship-diagram"></a>Verwenden des Attributbeziehungsdiagramms  
 Verwenden Sie das Attributbeziehungsdiagramm, um Attributbeziehungen zu erstellen, zu ändern oder zu löschen. Im Attributbeziehungsdiagramm werden auch problematische Attributbeziehungen hervorgehoben und in einer QuickInfo eine Problembeschreibung angezeigt.  
  
 Im Diagramm sind drei verschiedene Kontextmenüs verfügbar: das Diagrammkontextmenü, das Attributkontextmenü und das Beziehungskontextmenü.  
  
### <a name="diagram-shortcut-menu"></a>Diagrammkontextmenü  
 Um das Kontextmenü für das Attributbeziehungsdiagramm zu öffnen, klicken Sie mit der rechten Maustaste auf den Hintergrund des Diagramms. Das Kontextmenü für das Diagramm enthält die folgenden Befehle:  
  
 **Neue Attributbeziehung**  
 Öffnet das Dialogfeld **Attributbeziehung erstellen** , in dem Sie eine neue Attributbeziehung erstellen können.  
  
 Weitere Informationen finden Sie unter [Dialogfelder „Attributbeziehung erstellen“ und „Attributbeziehung bearbeiten“ &#40;Registerkarte „Attributbeziehungs-Designer“ im Dimensions-Designer&#41; &#40;Analysis Services – Mehrdimensionale Daten&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) und [Definieren von Attributbeziehungen](multidimensional-models/attribute-relationships-define.md).  
  
 **Formen anordnen**  
 Ordnet die Formen nach dem Layoutalgorithmus an, den der Dimensions-Designer verwendet.  
  
 **Formen automatisch anordnen**  
 Ordnet die Formen im Diagramm automatisch nach dem Layoutalgorithmus an, den der Dimensions-Designer verwendet. Standardmäßig ist die Option **Form automatisch anordnen** aktiviert.  
  
 **Listenansichten anzeigen**  
 Zeigt die Listen **Attribute** und **Attributbeziehungen** an oder blendet sie aus. Diese Listen werden jeweils in eigenen Bereichen unmittelbar unter dem Bereich angezeigt, der das Attributbeziehungsdiagramm enthält.  
  
 **Alle Formen erweitern**  
 Zeigt die gruppierten Attribute an, die den Attributen der obersten Ebene zugeordnet sind. Gruppierte Attribute sind nur sichtbar, wenn die Formen im Attributbeziehungsdiagramm erweitert werden.  
  
> [!NOTE]  
>  Wenn Sie auf diese Option klicken, gibt der Dimensions-Designer die Formen im Attributbeziehungsdiagramm wieder in dem vom Designer verwendeten Standardlayout aus.  
  
 **Alle Formen reduzieren**  
 Verbirgt die gruppierten Attribute, die den Attributen der obersten Ebene zugeordnet sind.  
  
> [!NOTE]  
>  Wenn Sie auf diese Option klicken, gibt der Dimensions-Designer die Formen im Attributbeziehungsdiagramm wieder in dem vom Designer verwendeten Standardlayout aus.  
  
 **Zoom**  
 Zeigt eine Liste verfügbarer Zoomoptionen an.  
  
### <a name="attribute-shortcut-menu"></a>Attributkontextmenü  
 Um das Attributkontextmenü zu öffnen, klicken Sie im Attributbeziehungsdiagramm mit der rechten Maustaste auf das Attribut. Das Attributkontextmenü enthält die folgenden Befehle:  
  
 **Neue Attributbeziehung**  
 Öffnet das Dialogfeld **Attributbeziehung erstellen** , in dem Sie eine neue Attributbeziehung erstellen können.  
  
 Weitere Informationen finden Sie unter [Dialogfelder „Attributbeziehung erstellen“ und „Attributbeziehung bearbeiten“ &#40;Registerkarte „Attributbeziehungs-Designer“ im Dimensions-Designer&#41; &#40;Analysis Services – Mehrdimensionale Daten&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) und [Definieren von Attributbeziehungen](multidimensional-models/attribute-relationships-define.md).  
  
 **Eigenschaften**  
 Zeigt die Eigenschaften des Attributs im Fenster **Eigenschaften** an.  
  
### <a name="relationship-shortcut-menu"></a>Beziehungskontextmenü  
 Um das Beziehungskontextmenü zu öffnen, klicken Sie mit der rechten Maustaste auf den Pfeil, der die Beziehung zwischen zwei Attributen identifiziert. Das Beziehungskontextmenü enthält die folgenden Befehle:  
  
 **Attributbeziehung bearbeiten**  
 Öffnet das Dialogfeld **Attributbeziehung bearbeiten**, in dem Sie die Attributbeziehung bearbeiten können.  
  
 Weitere Informationen finden Sie unter [Dialogfelder „Attributbeziehung erstellen“ und „Attributbeziehung bearbeiten“ &#40;Registerkarte „Attributbeziehungs-Designer“ im Dimensions-Designer&#41; &#40;Analysis Services – Mehrdimensionale Daten&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) und [Definieren von Attributbeziehungen](multidimensional-models/attribute-relationships-define.md).  
  
 **Beziehungstyp**  
 Legt den Beziehungstyp entweder auf **Flexibel** oder **Fest**fest. In einer flexiblen Beziehung ändern sich die Beziehungen zwischen Elementen. In einer festen Beziehung ändern sich die Beziehungen zwischen Elementen nicht.  
  
 **Löschen**  
 Löscht die Attributbeziehung.  
  
 **Eigenschaften**  
 Zeigt die Eigenschaften der Beziehung im Fenster **Eigenschaften** an.  
  
## <a name="see-also"></a>Siehe auch  
 [Attributbeziehungen &#40;Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md)   
 [Symbolleiste &#40;Attribut Registerkarte Attributbeziehungs-Designer, Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md)   
 [Attribute &#40;Attribut Registerkarte Attributbeziehungs-Designer, Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)   
 [Attributbeziehungen &#40;Attribut Registerkarte Attributbeziehungs-Designer, Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](attribute-relationships-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
