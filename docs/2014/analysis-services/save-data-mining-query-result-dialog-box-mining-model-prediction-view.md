---
title: Speichern Sie die Data Mining-Ergebnis (Dialogfeld) (Miningmodell-Vorhersageansicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b6b5c5f74ba8951bae27193b6796f09dcbdb8302
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62748002"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a>Ergebnis der Data Mining-Abfrage speichern (Dialogfeld - Miningmodellvorhersage-Sicht)
  Verwenden Sie das Dialogfeld **Ergebnis der Data Mining-Abfrage speichern** , um die Ergebnisse einer Data Mining-Abfrage in einer neuen Tabelle zu speichern.  
  
 Die neue Tabelle wird in der durch die Datenquelle definierten Datenbank erstellt.  
  
## <a name="options"></a>Optionen  
 **Data Source**  
 Wählen Sie eine Datenquelle aus dem aktuellen Projekt aus. Wenn die richtige Datenquelle nicht vorhanden ist, klicken Sie auf **Neu** , um eine neue Datenquelle zu erstellen.  
  
 **Neu**  
 Öffnet den **Datenquellen-Assistenten**.  
  
 **Tabellenname**  
 Geben Sie einen Namen für die neue Tabelle ein.  
  
 **Überschreiben, falls vorhanden**  
 Aktivieren Sie diese Option, wenn eine vorhandene Tabelle mit demselben Namen überschrieben werden soll.  
  
 In folgenden Fällen muss die vorhandene Tabelle überschrieben werden:  
  
-   Sie haben der Vorhersageabfrage Spalten hinzugefügt.  
  
-   Sie haben die Namen oder Datentypen von Spalten in der Vorhersageabfrage geändert.  
  
-   Sie haben eine ALTER-Anweisung für die Zieltabelle ausgeführt.  
  
 Wenn mehrere Spalten denselben Namen aufweisen (wenn mehrere abgeleitete Spalten z.B. über den standardmäßigen Spaltennamen **Ausdruck**verfügen), müssen Sie für jede Spalte mit einem doppelten Namen einen Alias erstellen. Wenn die Spalten keine eindeutigen Namen aufweisen, tritt ein Fehler auf, wenn der Designer versucht, die Ergebnisse in SQL Server zu speichern, da Spalten in einer Tabelle über eindeutige Namen verfügen müssen.  
  
 **Zur Datenquellensicht hinzufügen**  
 (Optional) Wählen Sie eine im Projekt enthaltene Datenquellensicht aus, wenn Sie die Tabelle einer vorhandenen Datenquelle hinzufügen möchten.  
  
 Diese Option ist nützlich, wenn Sie alle verknüpfte Tabellen für beibehalten möchten ein Modell wie z. B. Trainingsdaten, vorhersagequelldaten und Abfrage Ergebnisse – die gleiche Datenquelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Generator für Vorhersageabfragen &#40;Data Mining&#41;](prediction-query-builder-data-mining.md)   
 [Data Mining Abfrageschnittstellen](data-mining/data-mining-query-tools.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
