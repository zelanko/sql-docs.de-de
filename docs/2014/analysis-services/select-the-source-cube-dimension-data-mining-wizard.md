---
title: Quellcubedimension auswählen (Data Mining-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.selectsourcecube.f1
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bdb61763a49bad7eae1a49a01633ec8f45e27642
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66069229"
---
# <a name="select-the-source-cube-dimension-data-mining-wizard"></a>Quellcubedimension auswählen (Data Mining-Assistent)
  Mithilfe der Seite **Quellcubedimension auswählen** wählen Sie die Dimension des Cubes aus, die die zu analysierenden Fälle enthält. Wenn Sie beispielsweise ein Modell zur Analyse des Kaufverhaltens von Kunden auf der Grundlage von demografischen Daten erstellen, wählen Sie die Customer-Dimension aus, die in der Regel einen eindeutigen Datensatz für jeden Kunden und verschiedene Attribute mit demografischen Daten enthält, wie z. B. Geschlecht, Wohnsitz oder Einkommen. Zu einem späteren Zeitpunkt können Sie im Assistenten eine Tabelle hinzuzufügen, die sich auf diese Falltabelle bezieht. Sie können beispielsweise eine geschachtelte Tabelle hinzufügen, die anzeigt, welche Produkte der Kunde gekauft hat.  
  
> [!NOTE]  
>  Diese Seite wird nur dann angezeigt, wenn Sie auf der Seite **Definitionsmethode auswählen** des Assistenten **Aus vorhandenem Cube** ausgewählt haben.  
  
## <a name="options"></a>Tastatur  
 **Quellcubedimension auswählen**  
 Wählen Sie die Dimension des Cubes aus, der die Quelldaten für Ihre Miningstruktur bereitstellen wird.  
  
## <a name="choosing-a-dimension"></a>Auswählen einer Dimension  
 Da Sie nur eine Dimension zur Verwendung in Ihrem Modell auswählen können, ist es wichtig, dass Sie die Struktur des Cubes verstehen und die Dimension auswählen, die die besten Informationen für Ihr Modell bereitstellt. Wenn Sie nicht sicher sind, welche Dimension Sie verwenden sollen, könnte es hilfreich sein, den Cube zu durchsuchen und die Felder und Daten darin mit dem Dimensions-Designer zu überprüfen. Weitere Informationen finden Sie unter [Durchsuchen von Dimensionsdaten im Dimensions-Designer](multidimensional-models/database-dimensions-browse-dimension-data-in-dimension-designer.md).  
  
 Wenn Sie nicht mit Dimensionen vertraut sind, lesen Sie unter [Einführung in Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md) nach.  
  
 Weitere Informationen über den Informationstyp, der in der Regel in einer einzelnen Dimension enthalten ist, einschließlich Attributen und Measures, die möglicherweise für das Data Mining nützlich sind, finden Sie unter [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Wenn die Dimension, die Sie auswählen, nicht alle verknüpften Attribute enthält, die Sie benötigen, um das Data Mining-Modell zu erstellen, müssen Sie möglicherweise die Dimension ändern. Weitere Informationen finden Sie unter [Definieren von Datenbankdimensionen](multidimensional-models/define-database-dimensions.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Assistent (F1-Hilfe &#40;Analysis Services-Data Mining-&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Erstellen Sie die Data Mining-Struktur &#40;Data Mining-Assistenten&#41;](create-the-data-mining-structure-data-mining-wizard.md)   
 [Wählen Sie den Fall Schlüssel &#40;Data Mining-Assistenten aus&#41;](select-the-case-key-data-mining-wizard.md)  
  
  
