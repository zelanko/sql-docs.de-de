---
title: Speichern von Data Mining-Abfrage Ergebnis (Dialogfeld) (Miningmodell-Vorhersageansicht) | Microsoft Docs
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
- sql12.asvs.dm.savedataminingqueryresult.f1
helpviewer_keywords:
- Save Data Mining Query Result dialog box
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 709c3364ac5b4d6bc159af4ec6db40663d21fcbf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049312"
---
# <a name="save-data-mining-query-result-dialog-box-mining-model-prediction-view"></a>Ergebnis der Data Mining-Abfrage speichern (Dialogfeld - Miningmodellvorhersage-Sicht)
  Verwenden Sie das Dialogfeld **Ergebnis der Data Mining-Abfrage speichern** , um die Ergebnisse einer Data Mining-Abfrage in einer neuen Tabelle zu speichern.  
  
 Die neue Tabelle wird in der durch die Datenquelle definierten Datenbank erstellt.  
  
## <a name="options"></a>Tastatur  
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
  
 Diese Option ist hilfreich, wenn Sie alle verknüpften Tabellen für ein Modell – z. B. Trainingsdaten, Vorhersagequelldaten und Abfrageergebnisse – in derselben Datenquelle beibehalten möchten.  
  
## <a name="see-also"></a>Siehe auch  
 [Generator für Vorhersageabfragen &#40;Datamining&#41;](prediction-query-builder-data-mining.md)   
 [Data Mining Abfrageschnittstellen](data-mining/data-mining-query-tools.md)   
 [Data Mining-Erweiterungen &#40;DMX&#41; – Anweisungsreferenz](/sql/dmx/data-mining-extensions-dmx-statements)  
  
  
