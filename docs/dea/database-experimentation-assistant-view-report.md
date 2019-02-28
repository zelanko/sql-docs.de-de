---
title: Anzeigen der Analyseberichte im Datenbank-experimentieren-Assistenten für SQL Server-upgrades
description: Anzeigen der Analyseberichte im Datenbank-experimentieren-Assistenten
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: 49758d367f5ec22ffe3893896ab607917f28bf31
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "56987766"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Anzeigen der Analyseberichte im Datenbank-experimentieren-Assistenten

Nach dem [erstellen Sie den Analysebericht](database-experimentation-assistant-create-report.md) in Datenbank experimentieren-Assistenten (DEA), führen die Schritte in diesem Artikel zum Anzeigen des Berichts und Leistung Einblicke bereitgestellt, die von Ihrem A / B-Tests.

## <a name="select-a-server"></a>Wählen Sie einen server

Wählen Sie in DEA das Symbol "Menü" ein. Wählen Sie im erweiterten Menü **Analyseberichte** neben dem Symbol Checkliste zum Öffnen des Fensters in Berichten.

Klicken Sie unter **Analyseberichte**, geben Sie den Namen eines Computers mit SQL Server mit einer Analysis-Datenbank. Wählen Sie **Verbinden**. 

![Verbinden Sie mit einem vorhandenen Bericht](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

Wenn Sie alle Abhängigkeiten, fehlen die **Voraussetzungen** Seite werden Sie aufgefordert, mit Links, diese zu installieren. Installieren der erforderlichen Komponenten, und wählen Sie dann **wiederholen**.

![Seite "Voraussetzungen"](./media/database-experimentation-assistant-view-report/dea-view-report-prereq.png)

## <a name="select-an-analysis-report-to-view"></a>Wählen Sie einen Analysebericht zur anzeigen

Doppelklicken Sie in der Liste der Analyseberichte auf einen Bericht zu öffnen.

![Anzeigen von vorhandenen Bericht](./media/database-experimentation-assistant-view-report/dea-view-report-view-existing.png)

Erhalten Sie Einblicke, wie gut Ihre Workload dargestellt wird, wie in diesem Beispieldiagramm dargestellt:

![Workload-Rep-Diagramme](./media/database-experimentation-assistant-view-report/dea-view-report-workload-compare.png)

## <a name="view-and-understand-the-analysis-report"></a>Anzeigen und Verstehen des Analyseberichts

Dieser Abschnitt führt Sie durch den Analysebericht.

### <a name="query-categories"></a>Abfrage-Kategorien

Wählen Sie verschiedene Slices des Kreisdiagramms nach links um nur die Abfragen anzuzeigen, die in diese Kategorie fallen.

![Bericht Slices im Kreis](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

- **Heruntergestuft Abfragen**: Abfragen, die besser in ein als in b ausgeführt  
- **Fehler**: Abfragen, die Fehler in der Instanz B, aber nicht in der Instanz a anzeigen  
- **Verbessert die Abfragen**: Abfragen, die in der Instanz B als in der Instanz a besser ausgeführt  
- **Unbestimmt Abfragen**: Abfragen mit einer unbestimmten Leistung ändern.  
- **Gleiche**: Abfragen, die in denen Leistung der gleichen über Instanzen A und b geblieben

### <a name="individual-query-drill-down"></a>Einzelne Abfrage Drilldown

Sie können die Vorlagenlinks Abfrage, um ausführlichere Informationen zu bestimmten Abfragen finden Sie unter auswählen.

![Drilldown-Abfragen](./media/database-experimentation-assistant-view-report/dea-view-report-drilldown.png)

Wählen Sie eine bestimmte Abfrage um eine Zusammenfassung für die Abfrage des Vergleichs zu öffnen.

![Zusammenfassung](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

Sie können die Instanzen A und B sehen, die die Abfrage ausgeführt wurde, auf. Sie können auch sehen, dass eine Vorlage von die Abfrage könnte folgendermaßen aussehen. Eine Tabelle zeigt die spezifische Abfrageinformationen für Instanzen A und B.

### <a name="error-queries"></a>Fehler beim Abfragen

Der Zusammenfassungsbericht Vergleich ist erweiterbar **Fehlerinformationen** und **Informationen zum Planen der** Abschnitte. Die Abschnitte zeigen die Fehler, und Planen Sie die Informationen für beide Instanzen.

Wählen Sie den Kreis Fehler (Rot), um diese Arten von Fehlern anzuzeigen:
- **Vorhandenen Fehler**: Fehler, die in a wurden
- **Neue Fehler**: Fehler, die in der b wurden
- **Fehler aufgelöst**: Fehler, die in ein, aber nicht in B.

![Fehler-Diagramme](./media/database-experimentation-assistant-view-report/dea-view-report-error-charts.png)

## <a name="next-steps"></a>Nächste Schritte

- Gewusst wie: Generieren Sie einen Analysebericht an einer Eingabeaufforderung finden Sie unter [führen Sie an der Eingabeaufforderung](database-experimentation-assistant-run-command-prompt.md).

- Für einen 19-minütige Einführung in DEA und Demonstrationen im folgenden Video:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
