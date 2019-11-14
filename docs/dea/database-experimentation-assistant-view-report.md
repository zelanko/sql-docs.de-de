---
title: Anzeigen von Analyseberichten für SQL Server Upgrades
description: Anzeigen von Analyseberichten in Assistent für Datenbankexperimente
ms.custom: seo-lt-2019
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: fddc71bf7cdf7686154b4f9b5612cf671ca64fce
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056665"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Anzeigen von Analyseberichten in Assistent für Datenbankexperimente

Nachdem Sie den [Analysebericht](database-experimentation-assistant-create-report.md) in Assistent für Datenbankexperimente (DEA) erstellt haben, führen Sie die in diesem Artikel beschriebenen Schritte aus, um den Bericht anzuzeigen und Leistungsinformationen zu erhalten, die von Ihrem A/B-Test bereitgestellt werden.

## <a name="select-a-server"></a>Auswählen eines Servers

Wählen Sie in der DEA das Menü Symbol aus. Wählen Sie im erweiterten Menü neben dem Prüfliste-Symbol die Option **Analyseberichte** aus, um das Fenster Analyseberichte zu öffnen.

Geben Sie unter **Analyseberichte**den Namen eines Computers ein, auf dem SQL Server mit einer Analysedatenbank ausgeführt wird. Wählen Sie **Verbinden**. 

![Herstellen einer Verbindung mit einem vorhandenen Bericht](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

Wenn keine Abhängigkeiten vorhanden sind, werden Sie auf der Seite **Voraussetzungen** zur Installation von Links zur Installation aufgefordert. Installieren Sie die erforderlichen Komponenten, und wählen Sie dann **erneut versuchen**.

![Seite für erforderliche Komponenten](./media/database-experimentation-assistant-view-report/dea-view-report-prereq.png)

## <a name="select-an-analysis-report-to-view"></a>Wählen Sie einen Analysebericht zum Anzeigen aus.

Doppelklicken Sie in der Liste der Analyseberichte auf einen Bericht, um ihn zu öffnen.

![Vorhandenen Bericht anzeigen](./media/database-experimentation-assistant-view-report/dea-view-report-view-existing.png)

Sie erhalten Einblicke in die Darstellung der Arbeitsauslastung, wie in diesem Beispiel Diagramm gezeigt:

![Funktions Diagramme für Arbeitsauslastung](./media/database-experimentation-assistant-view-report/dea-view-report-workload-compare.png)

## <a name="view-and-understand-the-analysis-report"></a>Anzeigen und verstehen des Analyse Berichts

In diesem Abschnitt werden Sie durch den Analysebericht geführt.

### <a name="query-categories"></a>Abfrage Kategorien

Wählen Sie verschiedene Slices des linken Kreis Diagramms aus, um nur die Abfragen anzuzeigen, die in diese Kategorie fallen.

![Berichts Kreis Slices](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

- Heruntergestufte **Abfragen**: Abfragen, die in einer besser ausgeführt werden als in B.  
- **Fehler**: Abfragen, die Fehler in Instanz B, aber nicht in Instanz A anzeigen.  
- **Verbesserte Abfragen**: Abfragen, die in der Instanz B besser ausgeführt wurden als in Instanz a.  
- **Unbestimmte Abfragen**: Abfragen mit einer unbestimmten Leistungsänderung.  
- **Identisch**: Abfragen, bei denen die Leistung in den Instanzen A und B gleich geblieben ist.

### <a name="individual-query-drill-down"></a>Drilldown für einzelne Abfragen

Sie können die Links für die Abfrage Vorlage auswählen, um ausführlichere Informationen zu bestimmten Abfragen anzuzeigen.

![Drilldown für Abfrage](./media/database-experimentation-assistant-view-report/dea-view-report-drilldown.png)

Wählen Sie eine bestimmte Abfrage aus, um eine Vergleichs Zusammenfassung für die Abfrage zu öffnen.

![Vergleichs Zusammenfassung](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

Sie sehen die A-und B-Instanzen, für die die Abfrage ausgeführt wurde. Sie können auch eine Vorlage sehen, wie die Abfrage aussehen könnte. In einer Tabelle werden die Abfrage Informationen angezeigt, die für die Instanzen A und B spezifisch sind.

### <a name="error-queries"></a>Fehler Abfragen

Der Zusammenfassungs Bericht enthält erweiterbare **Fehlerinformationen** und Abschnitte zu **Abfrage Plan Informationen** . In den Abschnitten werden die Fehler und Plan Informationen für beide Instanzen angezeigt.

Wählen Sie den Kreis "Fehler" (rot) aus, um diese Arten von Fehlern anzuzeigen:
- **Vorhandene Fehler**: Fehler, die sich in einem befanden.
- **Neue Fehler**: Fehler in B.
- Behobene **Fehler**: Fehler in einer, aber nicht in B.

![Fehler Diagramme](./media/database-experimentation-assistant-view-report/dea-view-report-error-charts.png)

## <a name="next-steps"></a>Nächste Schritte

- Informationen zum Generieren eines Analyse Berichts an einer Eingabeaufforderung finden Sie unter [Ausführen an der Eingabeaufforderung](database-experimentation-assistant-run-command-prompt.md).

- Sehen Sie sich das folgende Video an, um die Einführung von DEA und Demo in 19 Minuten zu demonstrieren:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
