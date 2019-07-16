---
title: Entfernen von Spalten aus einer Miningstruktur | Microsoft-Dokumentation
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd8691d8ec0cc1546e27e8195e7d0bbc20709f59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209686"
---
# <a name="remove-columns-from-a-mining-structure"></a>Entfernen von Spalten aus einer Miningstruktur
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Sie können mit dem Data Mining-Designer Spalten aus einer Miningstruktur entfernen, nachdem die Struktur bereits erstellt worden ist. Folgende Gründe könnten dafür sprechen, eine Miningstrukturspalte zu entfernen:  
  
-   Die Miningstruktur enthält mehrere Kopien einer Spalte, und Sie möchten die Verwendung doppelter Daten in einem Modell vermeiden.  
  
-   Die Daten sollten geschützt werden, doch Drillthrough wurde aktiviert.  
  
-   Die Daten werden nicht für Modellierungen verwendet und sollten nicht verarbeitet werden.  
  
 Durch Löschen einer Spalte aus der Miningstruktur wird die Spalte in der Datenquellensicht oder in den externen Daten nicht geändert. Nur Metadaten werden gelöscht. Wenn Sie jedoch die Spalten ändern, die in einer Miningstruktur verwendet werden, müssen Sie die Struktur und alle darauf basierenden Modelle erneut verarbeiten.  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>So entfernen Sie eine Spalte aus der Miningstruktur  
  
1.  Wählen Sie im Data Mining-Designer die Registerkarte **Miningstruktur** aus.  
  
2.  Erweitern Sie die Struktur für die Miningstruktur, um alle Spalten anzuzeigen.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Spalte, die Sie löschen möchten, und wählen Sie anschließend **Löschen**aus.  
  
4.  Klicken Sie im Dialogfeld **Objekte löschen** auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks und Anweisungen für Miningstrukturen](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
