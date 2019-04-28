---
title: Entfernen von Spalten aus einer Miningstruktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5c48f659931fc1329df0a25afd74ff1e7bcc38cf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62733092"
---
# <a name="remove-columns-from-a-mining-structure"></a>Entfernen von Spalten aus einer Miningstruktur
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
 [Tasks und Anweisungen für Miningstrukturen](mining-structure-tasks-and-how-tos.md)  
  
  
