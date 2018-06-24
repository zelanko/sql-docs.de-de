---
title: Entwurfsbereich (Miningmodell-Vorhersageansicht) | Microsoft Docs
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
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f170ff6d780871a6ddbb9b1048fb0a521b4fb015
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050223"
---
# <a name="design-pane-mining-model-prediction-view"></a>Entwurfsbereich (Miningmodell-Vorhersageansicht)
  Der Bereich **Entwurf** enthält den Generator für Vorhersageabfragen, mit dem Sie Data Mining-Vorhersagen erstellen können. Sie können Vorhersageabfragen entwerfen, die Tabellen mit Eingabedaten einer Datenquellensicht verwenden, um Massenvorhersagen zu erstellen, oder Sie entwerfen Singleton-Vorhersageabfragen, bei denen Sie einzelne Werte angeben können.  
  
 Wechseln Sie zur Ergebnissicht, um die Abfrage auszuführen und die Ergebnisse anzuzeigen.  
  
 Die Ansicht **Abfrage** zeigt die vom Generator für Vorhersageabfragen erstellte DMX-Abfrage (DMX, Data Mining Extensions). Wenn Sie mit DMX vertraut sind, können Sie diese Abfrage anpassen.  
  
> [!NOTE]  
>  Wenn Sie die Abfrage manuell ändern, gehen diese Änderungen bei Rückkehr zur Entwurfssicht verloren. Wenn Sie die DMX-Abfrage speichern möchten, können Sie die Abfrage in die Windows-Zwischenablage kopieren und dann in eine Textdatei einfügen.  
  
 **Weitere Informationen finden Sie unter** [Data Mining-Abfrage](data-mining/data-mining-queries.md)  
  
## <a name="options"></a>Tastatur  
 **Zur abfrageergebnissicht wechseln**  
 Klicken Sie hier, um zwischen den Bereichen **Entwurf**, **Abfrage**und **Ergebnis** zu wechseln. Der Wechsel zum Bereich **Ergebnis** führt die Abfrage aus.  
  
 **Abfrageergebnis speichern**  
 Öffnet das Dialogfeld **Ergebnis der Data Mining-Abfrage speichern** .  
  
 **Singleton-Abfrage**  
 Ermöglicht das Erstellen einer SINGLETON-Abfrage, in der Sie die Werte direkt für die Abfrage bereitstellen können, statt eine Tabelle als Quelle der bekannten Daten bereitzustellen. Die Tabelle **Eingabetabelle(n) auswählen** wird durch die Tabelle **Singleton-Abfrageeingabe** ersetzt.  
  
 **Abfrageergebnis aktualisieren**  
 Verarbeitet die Vorhersageabfrage erneut. Diese Option ist nur im Bereich **Ergebnis** aktiviert.  
  
 **Miningmodell**  
 Zeigt das Miningmodell an, auf dem Sie die Vorhersagen aufbauen wollen.  
  
 **Modell auswählen**  
 Öffnet das Dialogfeld **Miningmodell auswählen** .  
  
 **Eingabetabelle(n) auswählen**  
 Zeigt die ausgewählten Eingabetabellen an, die die bekannten Daten enthalten, auf denen die Vorhersage aufgebaut werden soll.  
  
 **Tabelle löschen**  
 Löscht die ausgewählte Tabelle. Diese Schaltfläche ist deaktiviert, wenn keine Tabelle ausgewählt oder vorhanden ist.  
  
 **Falltabelle auswählen**  
 Öffnet das Dialogfeld **Tabelle auswählen** . Diese Schaltfläche wird nur angezeigt, wenn noch keine Falltabelle ausgewählt wurde.  
  
 **Geschachtelte Tabelle auswählen**  
 Öffnet das Dialogfeld **Tabelle auswählen** . Diese Schaltfläche wird nur angezeigt, wenn eine Falltabelle ausgewählt wurde. Wenn die entsprechende Miningstruktur keine geschachtelte Tabelle enthält, ist diese Schaltfläche deaktiviert.  
  
 **Join ändern**  
 Öffnet das Dialogfeld **Geschachtelten Join angeben** . Diese Schaltfläche ist nur aktiviert, wenn eine geschachtelte Tabelle ausgewählt ist.  
  
 **Singleton-abfrageeingabe**  
 Aktiviert, wenn Sie die Schaltfläche **SINGLETON-Abfrage** auswählen. Enthält die folgenden Spalten:  
  
|value|Description|  
|-----------|-----------------|  
|**Miningmodellspalte**|Listet die Miningmodellspalten auf, die in dem Miningmodell enthalten sind, das in der **Miningmodelle** -Spalte enhalten ist.|  
|**ReplTest1**|Wählen Sie einen Wert aus der Liste, die die verschiedenen Statusmöglichkeiten der ausgewählten Miningmodellspalte enthält.<br /><br /> Wenn es sich bei der Spalte um eine geschachtelte Tabellenspalte handelt, klicken Sie auf die Wertzelle, um das Dialogfeld **Eingabe für geschachtelte Tabelle** zu öffnen.|  
  
 **Quelle**  
 Wählen Sie die Quelle aus, die das Feld enthält, das Sie für die Spalte verwenden wollen. Sie können entweder das in der Tabelle **Miningmodell** ausgewählte Miningmodell, die in der Tabelle **Eingabetabelle(n) auswählen** ausgewählte(n) Eingabetabelle(n), eine Vorhersagefunktion oder einen benutzerdefinierten Ausdruck verwenden.  
  
 Spalten können aus den das Miningmodell enthaltenden Tabellen und den Eingabetabellen auf die Zelle gezogen werden.  
  
 **Feld**  
 Wählen Sie eine Spalte aus der Liste der aus der Quelltabelle abgeleiteten Spalten aus. Wenn Sie unter **Quelle** die **Vorhersagefunktion**ausgewählt haben, enthält diese Liste die für das ausgewählte Miningmodell verfügbare Vorhersagefunktion.  
  
 **Gruppieren**  
 Wird mit der **Und/Oder** -Spalte verwendet, um Ausdrücke zu gruppieren. Beispiel: `(expr1 Or expr2) And expr3`.  
  
 **Und/Oder**  
 Wird zum Erstellen einer logischen Abfrage verwendet. Beispiel: `(expr1 Or expr2) And expr3`.  
  
 **Kriterium/Argument**  
 Geben Sie eine Bedingung oder einen benutzerdefinierten Ausdruck an, der auf die Spalte angewendet wird. Spalten können aus den das Miningmodell enthaltenden Tabellen und den Eingabetabellen auf die Zelle gezogen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Erweiterungen &#40;DMX&#41; -Anweisungsreferenz](/sql/dmx/data-mining-extensions-dmx-statements)   
 [Data Mining Abfrageschnittstellen](data-mining/data-mining-query-tools.md)   
 [Generator für Vorhersageabfragen &#40;Datamining&#41;](prediction-query-builder-data-mining.md)  
  
  
