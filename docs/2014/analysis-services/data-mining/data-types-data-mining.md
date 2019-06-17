---
title: Datentypen (Datamining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data types [data mining]
- columns [data mining], data types
- data mining [Analysis Services], data types
ms.assetid: 4af5b7db-790b-459c-b2b4-00f0cf6b5ce4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc810f56d552fa17cb027598a25bde114a696375
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66084801"
---
# <a name="data-types-data-mining"></a>Datentypen (Data Mining)
  Beim Erstellen eines Miningmodells oder einer Miningstruktur in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]müssen Sie die Datentypen für die einzelnen Spalten in der Miningstruktur definieren. Anhand des Datentyps erkennt die Data Mining-Engine, ob es sich bei den Daten in der Datenquelle um numerische Daten oder um Text handelt und wie die Daten verarbeitet werden sollen. Wenn die Datenquelle beispielsweise numerische Daten enthält, können Sie angeben, ob die Zahlen als ganze Zahlen oder durch Verwendung von Dezimalstellen verarbeitet werden sollen.  
  
 Jeder Datentyp unterstützt einen oder mehrere Inhaltstypen. Durch Festlegen des Inhaltstyps können Sie die Methode anpassen, mit der Daten in den Spalten im Miningmodell verarbeitet oder berechnet werden.  
  
 Wenn beispielsweise numerische Daten in einer Spalte enthalten sind, können Sie entscheiden, diese als numerischen Datentyp oder als Textdatentyp zu behandeln. Wenn Sie den numerischen Datentyp wählen, können Sie mehrere Inhaltstypen festlegen: Sie können die Zahlen diskretisieren oder als kontinuierliche Werte behandeln. Eine Liste aller Inhaltstypen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](content-types-data-mining.md).  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt die folgenden Datentypen für Miningstrukturspalten:  
  
|Datentyp|Unterstützte Inhaltstypen|  
|---------------|-----------------------------|  
|`Text`|Zyklisch, Diskret, Diskretisiert, Key Sequence, Sortiert, Sequenz|  
|`Long`|Kontinuierlich, Zyklisch, Diskret, Diskretisiert, Schlüssel, Key Sequence, Key Time, Sortiert, Sequenz, Zeit<br /><br /> Classified|  
|`Boolean`|Zyklisch, Diskret, Sortiert|  
|`Double`|Kontinuierlich, Zyklisch, Diskret, Diskretisiert, Schlüssel, Key Sequence, Key Time, Sortiert, Sequenz, Zeit<br /><br /> Classified|  
|`Date`|Kontinuierlich, Zyklisch, Diskret, Diskretisiert, Schlüssel, Key Sequence, Key Time, Sortiert|  
  
> [!NOTE]  
>  Die Time- und Sequence-Inhaltstypen werden nur von Algorithmen von Drittanbietern unterstützt. Die Inhaltstypen Zyklisch und Sortiert  werden unterstützt, die meisten Algorithmen behandeln sie jedoch als diskrete Werte und führen keine spezielle Verarbeitung durch.  
  
## <a name="specifying-a-data-type"></a>Angeben eines Datentyps  
 Wenn Sie das Miningmodell direkt mithilfe der Data Mining-Erweiterungen (DMX) erstellen, können Sie den Datentyp für die einzelnen Spalten zusammen mit dem Modell definieren. Analysis Services erstellt dann gleichzeitig die entsprechende Miningstruktur mit den angegebenen Datentypen. Wenn Sie das Miningmodell oder die Miningstruktur mit einem Assistenten erstellen, schlägt Analysis Services einen Datentyp vor, oder Sie können einen Datentyp in einer Liste auswählen.  
  
## <a name="changing-a-data-type"></a>Ändern eines Datentyps  
 Wenn Sie den Datentyp einer Spalte ändern, müssen die Miningstruktur und alle auf dieser Struktur basierenden Miningmodelle neu verarbeitet werden. Beim Ändern des Datentyps kann es vorkommen, dass die jeweilige Spalte nicht mehr in einem bestimmten Modell verwendet werden kann. In diesem Fall gibt Analysis Services beim erneuten Verarbeiten entweder einen Fehler aus, oder das Modell wird unter Auslassung der Spalte verarbeitet.  
  
## <a name="see-also"></a>Siehe auch  
 [Inhaltstypen &#40;Data Mining&#41;](content-types-data-mining.md)   
 [Inhaltstypen &#40;DMX&#41;](/sql/dmx/content-types-dmx)   
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](mining-structures-analysis-services-data-mining.md)   
 [Datentypen &#40;DMX&#41;](/sql/dmx/data-types-dmx)   
 [Miningmodellspalten](mining-model-columns.md)   
 [Miningstrukturspalten](mining-structure-columns.md)  
  
  
