---
title: Definieren Beziehung (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.f1
helpviewer_keywords:
- Define Relationship dialog box
ms.assetid: 0fcee7f1-f138-4c2e-ae8c-245395ee0fe8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2bc1ab86373fc7c3b4b32cdfdbc87f5d5dd4acf8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62732086"
---
# <a name="define-relationship-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Beziehung definieren' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Beziehung definieren** können Sie im Cube-Designer eine Beziehung zwischen einer Cubedimension und einer Measuregruppe definieren. Sie können das Dialogfeld **Beziehung definieren** anzeigen, indem Sie auf die Schaltfläche mit den Auslassungspunkten ( **...** ) in einer Zelle im Bereich **Raster** der Registerkarte **Dimensionsverwendung** im Cube-Designer klicken.  
  
## <a name="options"></a>Optionen  
 **Beziehungstyp auswählen**  
 Wählen Sie den Typ der Dimensionsbeziehung aus, die zum Erstellen der Beziehung zwischen Cubedimension und Measuregruppe verwendet wird. Durch Auswahl eines Dimensionsbeziehungstyps ändert sich der Inhalt im Bereich **Detail** .  
  
 Bei Auswahl der Option **Keine Beziehung** wird keine Dimensionsbeziehung erstellt.  
  
 **Detail**  
 Zeigt die für den unter **Beziehungstyp auswählen**ausgewählten Dimensionsbeziehungstyp verfügbaren Optionen an.  
  
## <a name="detail-pane-options"></a>Optionen im Bereich Detail  
 Die folgenden Optionen werden in Abhängigkeit von dem unter **Beziehungstyp auswählen** ausgewählten Beziehungstyp im Bereich **Detail**angezeigt:  
  
|Beziehungstyp|Description|Option|  
|-----------------------|-----------------|------------|  
|**Keine Beziehung**|Es ist keine Beziehung definiert. Im Bereich **Detail** werden keine Optionen angezeigt.||  
|**Regulär**|Gibt eine reguläre Dimensionsbeziehung an. Die folgenden Optionen werden im Bereich **Detail** angezeigt:|**Granularitätsattribut**: <br />                      Wählen Sie das Attribut aus, das die Granularität der Measuregruppe unter Berücksichtigung der Dimension definiert. Dieses Attribut ist normalerweise das Schlüsselattribut der Dimension.|  
|||**Dimensionstabelle** : Zeigt die Haupttabelle für die Dimension an.|  
|||**Measuregruppentabelle** : Zeigt die Faktentabelle für die Measuregruppe an.|  
|||**Beziehung**: Zeigt ein Raster aus Dimensionsspalten und Measuregruppenspalten an denen der Beziehung zugrunde liegen. Das Raster enthält die folgenden Spalten:<br /><br /> **Dimensionsspalten**: Zeigt die mit dem ausgewählten Granularitätsattribut verknüpften Spalten an. Hinweis: Wenn die Dimension noch nicht generiert wurde, wird diese Option festgelegt, um **generieren**.<br />**Measuregruppenspalten** :<br />                              Wählen Sie die Spalten in der Measuregruppe aus, die mit den Dimensionsspalten verbunden sind.|  
|||**Erweitert**:<br />                      Klicken Sie auf diese Option, um das Dialogfeld **Measuregruppenbindungen** anzuzeigen und erweiterte Eigenschaften, z.B. die NULL-Verarbeitung, für die Beziehungen zwischen Attributen und Measuregruppenspalten zu bearbeiten. Weitere Informationen zum Dialogfeld **Measuregruppenbindungen** finden Sie unter [Dialogfeld „Measuregruppenbindung“ &#40;Analysis Services – Mehrdimensionale Daten&#41;](measure-group-bindings-dialog-box-analysis-services-multidimensional-data.md).|  
|**Faktentabelle**|Gibt eine Faktendimensionsbeziehung an. Die folgenden Optionen werden im Bereich **Detail** angezeigt:|**Granularitätsattribut**: Wählen Sie das Attribut aus, das die Granularität der Measuregruppe unter Berücksichtigung der Dimension definiert. Dieses Attribut ist normalerweise das Schlüsselattribut der Dimension.|  
|||**Dimensionstabelle**: Zeigt die primäre Dimensionstabelle an.|  
|||**Measuregruppentabelle**: <br />                      Zeigt die der Measuregruppe zugrunde liegende Tabelle an.|  
|**Auf die verwiesen wird**|Gibt eine referenzierte Dimensionsbeziehung an. Die folgenden Optionen werden im Bereich **Detail** angezeigt:|**Bezugsdimension**: <br />                      Zeigt die ausgewählte Dimension an.|  
|||**Zwischendimension**: <br />                      Wählen Sie die Zwischendimension aus.|  
|||**Bezugsdimensionsattribut**: <br />                      Wählen Sie das Attribut in der Bezugsdimension aus, das mit dem unter **Zwischendimensionsattribut**angegebenen Zwischendimensionsattribut verbunden ist.|  
|||**Zwischendimensionsattribut**: <br />                      Wählen Sie das Attribut in der Zwischendimension aus, das mit dem Attribut in der unter **Bezugsdimension**angegebenen Bezugsdimension verbunden ist.|  
|||**Materialisieren**: <br />                      Aktivieren Sie dieses Kontrollkästchen, damit das Attributelement in der Zwischendimension gespeichert wird, die das Attribut in der Bezugsdimension mit der Faktentabelle in der MOLAP-Struktur verknüpft. Das Materialisieren der Beziehung ist das Standardverhalten zum Maximieren der Abfrageleistung, bringt jedoch eine Erhöhung der Verarbeitungszeit und des erforderlichen Speicherplatzes mit sich.|  
|**M: N**|Gibt eine m:n-Dimensionsbeziehung an Die folgenden Optionen werden im Bereich **Detail** angezeigt:|**Dimension** : Zeigt die ausgewählte Dimension an.|  
|||**Zwischenmeasuregruppe** : <br />                      Wählen Sie die verknüpfte Zwischenmeasuregruppe aus.<br /><br /> Hinweis: Die Zwischenmeasuregruppe muss mindestens eine Dimension mit der ausgewählten Measuregruppe gemein haben. Außerdem muss die Granularität der Beziehung zwischen der Zwischenmeasuregruppe und der gemeinsamen Dimension größer oder gleich der Granularität zwischen der gemeinsamen Dimension und der ausgewählten Measuregruppe sein.|  
|**Data Mining**|Gibt eine Data Mining-Dimensionsbeziehung an. Die folgenden Optionen werden im Bereich **Detail** angezeigt:|**Zieldimension**: Zeigt die ausgewählte Datamining-Dimension an.<br /><br /> Hinweis: Sie müssen eine Datamining-Dimension um eine Data mining-dimensionsbeziehung zu erstellen, auswählen.|  
|||**Quelldimension**: Wählen Sie die Dimension aus, für die die Data Mining-Dimension Vorhersageanalysen bereitstellt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionsbeziehungen](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [Dimensionsverwendung &#40;Cube-Designer&#41; &#40;Analysis Services – mehrdimensionale Daten&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md)   
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
