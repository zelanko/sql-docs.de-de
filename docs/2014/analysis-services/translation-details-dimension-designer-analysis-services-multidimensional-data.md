---
title: Übersetzungsdetails (Registerkarte Übersetzungen, Dimensions-Designer) (Analysis Services – mehrdimensionale Daten) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dimensiondesigner.translations.translationpane.tranlationdetails.f1
ms.assetid: 0aa61df3-f2b0-4703-a63b-124da672dcc3
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c3fea9b837915fff37bad632780544bcf7ebb1a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162355"
---
# <a name="translation-details-translations-tab-dimension-designer-analysis-services---multidimensional-data"></a>Übersetzungsdetails (Registerkarte Übersetzungen, Dimensions-Designer) (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Bereichs **Übersetzungsdetails** auf der Registerkarte **Übersetzungen** im Dimensions-Designer können Sie Übersetzungen für die aktuell ausgewählte Dimension definieren und verwalten.  
  
 **Um den Bereich Übersetzungsdetails anzuzeigen.**  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]das [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Projekt, und öffnen Sie dann die gewünschte Dimension.  
  
2.  Klicken Sie auf die Registerkarte **Übersetzungen** .  
  
## <a name="options"></a>Tastatur  
 **Standardsprache**  
 Legt die Namen der Dimensionsobjekte in der Standardsprache fest.  
  
 **Objekttyp**  
 Zeigt die Eigenschaft an, die übersetzt wird. Es können nur Objekte und Eigenschaften übersetzt werden, für die Werte angegeben wurden. Die folgenden Eigenschaften können übersetzt werden:  
  
-   Dimension  
  
     `Caption` und `AttributeAllMember` Eigenschaften  
  
-   attribute  
  
     `Caption`, `AttributeHierarchyDisplayFolder`, und `NamingTemplate` Eigenschaften  
  
    > [!NOTE]  
    >  Die `NamingTemplate`-Eigenschaft ist nur für übergeordnete Attribute verfügbar.  
  
-   Hierarchy  
  
     `Caption` und `AllMemberName` Eigenschaften  
  
-   Ebene  
  
     `Caption` Eigenschaft  
  
 **\<Language >**  
 Geben Sie den Eigenschaftswert des Dimensionsobjekts in der ausgewählten Sprache an, oder wählen Sie ihn aus. In Abhängigkeit von der bearbeiteten Eigenschaft werden zusätzliche Dialogfelder geöffnet, wenn Sie auf die Schaltfläche mit den Auslassungspunkten (**...**) klicken:  
  
-   `NamingTemplate` Eigenschaft  
  
     Zeigt das [Dialogfeld „Vorlage zur Ebenenbenennung“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](level-naming-template-dialog-box-analysis-services-multidimensional-data.md) an.  
  
-   `Caption` -Eigenschaft (für Attribute)  
  
     Zeigt das [Dialogfeld „Attributdatenübersetzung“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="shortcut-menu"></a>Kontextmenü  
 Die folgenden Optionen sind im Kontextmenü verfügbar, das angezeigt wird, wenn Sie im Bereich **Übersetzungsdetails** mit der rechten Maustaste auf eine Übersetzung klicken:  
  
 **Neue Übersetzung**  
 Wählen Sie diese Option aus, um das Dialogfeld **Sprache auswählen** anzuzeigen und um eine neue Übersetzung zu erstellen. Die Übersetzung wird im Raster **Übersetzungsdetails** als neue Spalte angezeigt.  
  
 **Übersetzung löschen**  
 Wählen Sie diese Option aus, um die ausgewählte Übersetzung zu löschen.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn Sie mit der rechten Maustaste auf eine Zelle geklickt haben, um die Übersetzung zu löschen.  
  
 **Neue Beschriftungsspalte**  
 Wählen Sie diese Option aus, um das Dialogfeld **Attributdatenübersetzung** anzuzeigen und um eine neue Beschriftungsspalte zu definieren, wenn Sie im Raster **Übersetzungsdetails** ein Attribut ändern. Zum Aktivieren dieser Option müssen Sie im Raster der **Übersetzungsdetails** eine Zelle in der Übersetzungsspalte eines Attributs auswählen.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn Sie mit der rechten Maustaste auf eine Zelle geklickt haben, um die Übersetzungsspalte eines Attributs zu löschen.  
  
 **Beschriftungsspalte bearbeiten**  
 Wählen Sie diese Option aus, um das Dialogfeld **Attributdatenübersetzung** anzuzeigen und um eine vorhandene Beschriftungsspalte zu bearbeiten, wenn Sie im Raster **Übersetzungsdetails** ein Attribut ändern.  
  
> [!NOTE]  
>  Die Option ist nur aktiviert, wenn im Raster **Übersetzungsdetails** eine Zelle in einer Übersetzungsspalte ausgewählt werden muss, die eine Beschriftungsspalte für ein Attribut enthält.  
  
 **Beschriftungsspalte löschen**  
 Wählen Sie diese Option aus, um im Raster **Übersetzungsdetails** die Beschriftungsspalte für das ausgewählte Attribut zu löschen.  
  
> [!NOTE]  
>  Diese Option ist nur aktiviert, wenn Sie in einer Übersetzungsspalte, die eine Beschriftungsspalte für ein Attribut enthält, mit der rechten Maustaste auf eine Zelle geklickt haben.  
  
 **Alle Attribute anzeigen**  
 Wählen Sie diese Option aus, um alle für die ausgewählte Dimension definierten Attribute anzuzeigen, einschließlich der Attribute, deren Attributhierarchien deaktiviert wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersetzungen &#40;Dimensions-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  