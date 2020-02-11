---
title: Rück Schreiben von Dimensionen aktivieren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6051f62caac2878b689a50e5773b047cb8df7afe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076850"
---
# <a name="enable-dimension-writeback"></a>Rückschreiben von Dimensionen aktivieren
  Fügen Sie einem Cube oder einer Dimension die Erweiterung zum Rückschreiben von Dimensionen hinzu, um Benutzern das manuelle Ändern der Dimensionsstruktur und -elemente zu ermöglichen. Updates für eine Dimension mit aktiviertem Schreibzugriff werden direkt in der Dimensionstabelle aufgezeichnet. Durch diese Erweiterung wird die Einstellung der `WriteEnabled`-Eigenschaft für eine Dimension geändert.  
  
 Verwenden Sie den Business Intelligence-Assistenten, um das Rückschreiben von Dimensionen zu aktivieren, und wählen Sie auf der Seite **Erweiterung auswählen** die Option **Rückschreiben von Dimensionen aktivieren** aus. Anschließend führt Sie der Assistent durch die Schritte zum Auswählen einer Dimension, für die Sie das Rückschreiben von Dimensionen anwenden möchten, und zum Festlegen dieser Option für die ausgewählte Dimension.  
  
> [!NOTE]  
>  Das Rückschreiben wird nur für relationale SQL Server-Datenbanken und Data Marts unterstützt.  
  
## <a name="selecting-a-dimension"></a>Auswählen einer Dimension  
 Auf der ersten Seite **Rückschreiben von Dimensionen aktivieren** des Assistenten geben Sie die Dimension an, auf die Sie das Rückschreiben von Dimensionen anwenden möchten. Die Erweiterung zum Rückschreiben von Dimensionen, die dieser ausgewählten Dimension hinzugefügt wurde, führt zu Änderungen an der Dimension. Diese Änderungen werden an alle Cubes vererbt, die die ausgewählte Dimension enthalten.  
  
## <a name="setting-dimension-writeback-capability"></a>Festlegen des Features zum Rückschreiben von Dimensionen  
 Auf der zweiten Seite **Rückschreiben von Dimensionen aktivieren** des Assistenten findet das eigentliche Festlegen der Option **Rückschreiben in der Dimension aktivieren** statt. Durch Auswählen dieser Option wird die `WriteEnabled`-Eigenschaft der Dimension automatisch auf `True` festgelegt. Durch Deaktivieren dieser Option wird die Eigenschaft automatisch auf `False` festgelegt.  
  
## <a name="remarks"></a>Bemerkungen  
 Beim Erstellen eines neuen Elements müssen Sie jedes Attribut in einer Dimension angeben. Sie können kein Element einfügen, ohne dabei einen Wert für das Schlüsselattribut der Dimension anzugeben. Deshalb unterliegt das Erstellen von Elementen allen Beschränkungen (z.&#160;B. von NULL verschiedene Schlüsselwerte), die für die Dimensionstabelle definiert sind. Sie sollten auch Spalten berücksichtigen, die optional durch Dimensionseigenschaften angegeben werden, z. B. Spalten, die in den Dimensionseigenschaften `CustomRollupColumn`, `CustomRollupPropertiesColumn` oder `UnaryOperatorColumn` angegeben werden.  
  
> [!WARNING]  
>  Wenn Sie SQL Azure als Datenquelle verwenden, um einen Rückschreibevorgang in eine Analysis Services-Datenbank auszuführen, schlägt der Vorgang fehl. Dies ist programmbedingt, da die Anbieteroption, durch die mehrere aktive Resultsets (MARS) aktiviert werden, standardmäßig deaktiviert ist.  
>   
>  Als Problemumgehung fügen Sie der Verbindungszeichenfolge folgende Einstellung hinzu, damit MARS unterstützt und Rückschreibvorgänge aktiviert werden:  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  Weitere Informationen finden [Sie unter Verwenden von mehreren aktiven Resultsets &#40;Mars&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Dimensionen mit aktiviertem Schreibzugriff](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
