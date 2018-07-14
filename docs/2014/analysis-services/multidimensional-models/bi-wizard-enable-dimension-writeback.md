---
title: Aktivieren des Rückschreibens | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- modifying dimensions
- writeback [Analysis Services], setting up
- dimensions [Analysis Services], Business Intelligence enhancements
- Business Intelligence enhancements [Analysis Services], writeback
- dimensions [Analysis Services], writeback
- writeback [Analysis Services]
- dimensions [Analysis Services], modifying
- manual dimension structure modifications
ms.assetid: a4b5eb5a-366d-4fc8-ad0d-5bdb8e7b4163
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0e7ee13d4fdfa021e050c4357dc8796289a3cd4d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247430"
---
# <a name="enable-dimension-writeback"></a>Rückschreiben von Dimensionen aktivieren
  Fügen Sie einem Cube oder einer Dimension die Erweiterung zum Rückschreiben von Dimensionen hinzu, um Benutzern das manuelle Ändern der Dimensionsstruktur und -elemente zu ermöglichen. Updates für eine Dimension mit aktiviertem Schreibzugriff werden direkt in der Dimensionstabelle aufgezeichnet. Durch diese Erweiterung wird die Einstellung der `WriteEnabled`-Eigenschaft für eine Dimension geändert.  
  
 Verwenden Sie den Business Intelligence-Assistenten, um das Rückschreiben von Dimensionen zu aktivieren, und wählen Sie auf der Seite **Erweiterung auswählen** die Option **Rückschreiben von Dimensionen aktivieren** aus. Anschließend führt Sie der Assistent durch die Schritte zum Auswählen einer Dimension, für die Sie das Rückschreiben von Dimensionen anwenden möchten, und zum Festlegen dieser Option für die ausgewählte Dimension.  
  
> [!NOTE]  
>  Das Rückschreiben wird nur für relationale SQL Server-Datenbanken und Data Marts unterstützt.  
  
## <a name="selecting-a-dimension"></a>Auswählen einer Dimension  
 Auf der ersten Seite **Rückschreiben von Dimensionen aktivieren** des Assistenten geben Sie die Dimension an, auf die Sie das Rückschreiben von Dimensionen anwenden möchten. Die Erweiterung zum Rückschreiben von Dimensionen, die dieser ausgewählten Dimension hinzugefügt wurde, führt zu Änderungen an der Dimension. Diese Änderungen werden an alle Cubes vererbt, die die ausgewählte Dimension enthalten.  
  
## <a name="setting-dimension-writeback-capability"></a>Festlegen des Features zum Rückschreiben von Dimensionen  
 Auf der zweiten Seite **Rückschreiben von Dimensionen aktivieren** des Assistenten findet das eigentliche Festlegen der Option **Rückschreiben in der Dimension aktivieren** statt. Durch das Auswählen dieser Option automatisch der `WriteEnabled` Eigenschaft der Dimension auf `True`. Legt die Eigenschaft wird auf das Deaktivieren dieser Option wird automatisch `False`.  
  
## <a name="remarks"></a>Hinweise  
 Beim Erstellen eines neuen Elements müssen Sie jedes Attribut in einer Dimension angeben. Sie können kein Element einfügen, ohne dabei einen Wert für das Schlüsselattribut der Dimension anzugeben. Deshalb unterliegt das Erstellen von Elementen allen Beschränkungen (z.&#160;B. von NULL verschiedene Schlüsselwerte), die für die Dimensionstabelle definiert sind. Sie sollten auch Spalten, die optional durch Dimensionseigenschaften, angegeben berücksichtigen, wie z. B. die Angabe von Spalten in der `CustomRollupColumn`, `CustomRollupPropertiesColumn` oder `UnaryOperatorColumn` Dimensionseigenschaften.  
  
> [!WARNING]  
>  Wenn Sie SQL Azure als Datenquelle verwenden, um einen Rückschreibevorgang in eine Analysis Services-Datenbank auszuführen, schlägt der Vorgang fehl. Dies ist programmbedingt, da die Anbieteroption, durch die mehrere aktive Resultsets (MARS) aktiviert werden, standardmäßig deaktiviert ist.  
>   
>  Als Problemumgehung fügen Sie der Verbindungszeichenfolge folgende Einstellung hinzu, damit MARS unterstützt und Rückschreibvorgänge aktiviert werden:  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Weitere Informationen finden Sie unter [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Dimensionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
