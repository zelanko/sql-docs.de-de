---
title: Anzeigen von Analyseberichten für SQL Server Upgrades
description: Anzeigen von Analyseberichten in Assistent für Datenbankexperimente
ms.custom: seo-lt-2019
ms.date: 02/04/2020
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: 2a6d027c1fb1834e4033a11a498bfc8cdad4561f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "76977583"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Anzeigen von Analyseberichten in Assistent für Datenbankexperimente

Nachdem Sie mit Assistent für Datenbankexperimente (DEA) [einen Analysebericht erstellt](database-experimentation-assistant-create-report.md)haben, können Sie den Bericht basierend auf dem von Ihnen durchgeführten A/B-Test auf Leistungs Einblicke überprüfen.

## <a name="open-an-existing-analysis-report"></a>Öffnen eines vorhandenen Analyse Berichts

1. Wählen Sie in der ddea das Listen Symbol aus, geben Sie den Servernamen und den Authentifizierungstyp an, aktivieren bzw. deaktivieren Sie die Kontrollkästchen **Verbindung verschlüsseln** und **Serverzertifikat vertrauen** entsprechend ihren Szenarios, und wählen Sie dann **verbinden**aus.

   ![Herstellen einer Verbindung mit dem Server mit dem Bericht](./media/database-experimentation-assistant-view-report/dea-connect-to-server-with-report-files.png)

2. Wählen Sie auf dem Bildschirm **Analyseberichte** auf der linken Seite den Eintrag für den Bericht aus, den Sie anzeigen möchten.

   ![Öffnen einer vorhandenen Berichtsdatei](./media/database-experimentation-assistant-view-report/dea-select-report-to-view.png)

## <a name="view-and-understand-the-analysis-report"></a>Anzeigen und verstehen des Analyse Berichts

In diesem Abschnitt werden Sie durch den Analysebericht geführt.

Auf der ersten Seite des Berichts werden Informationen zu Version und Buildinformationen für die Zielserver, auf denen das Experiment ausgeführt wurde, angezeigt. Mithilfe des Schwellenwerts können Sie die Empfindlichkeit oder Toleranz Ihrer A/B-Test Analyse anpassen. Standardmäßig ist der Schwellenwert auf 5% festgelegt. alle Verbesserungen bei der Leistung >= 5% werden als "verbessert" kategorisiert.  Mithilfe der Dropdown Liste können Sie den Bericht mit unterschiedlichen Leistungs Schwellenwerten auswerten.

Sie können die Daten im Bericht in eine CSV-Datei exportieren, indem Sie auf die Schaltfläche **exportieren** klicken.  Auf jeder Seite des Analyse Berichts können Sie **Drucken** auswählen, um zu diesem Zeitpunkt zu drucken, was auf dem Bildschirm sichtbar ist.

### <a name="query-distribution"></a>Abfrage Verteilung

- Wählen Sie verschiedene Slices der Kreis Diagramme aus, um nur die Abfragen anzuzeigen, die zu dieser Kategorie gehören.

   ![Berichtskategorien als Kreissegmente](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

  - Herunter **gestuft: Abfragen**, die auf Ziel 2 schlechter ausgeführt wurden als auf Ziel 1.
  - **Fehler**: Abfragen, die mindestens einmal Fehler in mindestens einem der Ziele angezeigt haben.
  - **Verbessert**: Abfragen, die auf Ziel 2 bessere Ergebnisse als auf Ziel 1 durchgeführt haben.
  - **Auswerten nicht**möglich: Abfragen mit einer Stichprobengröße zu klein für statistische Analysen. Für eine/B-Test Analyse benötigt DEA die gleichen Abfragen, damit für jedes Ziel mindestens 15 Ausführungen vorhanden sind.
  - **Identisch**: Abfragen ohne statistischen Unterschied Zwischenziel 1 und Ziel 2.

  Fehler Abfragen werden ggf. in separaten Diagrammen angezeigt. ein Balkendiagramm, das Fehler nach Typ klassifiziert, und ein Kreis Diagramm, in dem Fehler nach Fehler-ID klassifiziert werden.

   ![Fehler Abfrage Diagramme](./media/database-experimentation-assistant-view-report/dea-error-query-charts.png)

  Es gibt vier mögliche Arten von Fehlern:

  - **Vorhandene Fehler**: Fehler, die auf Ziel 1 und Ziel 2 vorhanden sind.
  - **Neue Fehler**: neue Fehler in Ziel 2.
  - Behobene **Fehler**: Fehler, die auf Ziel 1 vorhanden sind, aber auf Ziel 2 aufgelöst werden.
  - **Upgradeblockierer**: Fehler, die ein Upgrade auf den Zielserver blockieren.

  Wenn Sie in den Diagrammen auf eine beliebige Leiste oder einen Kreis Abschnitt klicken, wird ein Drilldown in **die Kategorie durch** führt und die Leistungsmetriken angezeigt, auch wenn die Kategorie

  Außerdem zeigt das Dashboard die fünf wichtigsten und herunter gestuften Abfragen an, um eine schnelle Leistungsübersicht zu bieten.

### <a name="individual-query-drill-down"></a>Drilldown für einzelne Abfragen

Sie können Abfrage Vorlagen Links für ausführlichere Informationen zu bestimmten Abfragen auswählen.

![Drilldown in eine bestimmte Abfrage](./media/database-experimentation-assistant-view-report/dea-query-drill-down-report.png)

- Wählen Sie eine bestimmte Abfrage aus, um die Verwandte Vergleichs Zusammenfassung zu öffnen.

   ![Zusammenfassender Vergleich](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

   Sie finden Zusammenfassungs Statistiken für diese Abfrage, z. b. die Anzahl der Ausführungen, die durchschnittliche Dauer, die mittlere CPU, durchschnittliche Lese-/Schreibvorgänge und Fehler Anzahl.  Wenn es sich bei der Abfrage um eine Fehler Abfrage handelt, werden auf der Registerkarte **Fehlerinformationen** weitere Details zum Fehler angezeigt.  Auf der Registerkarte **Abfrage Plan Informationen** finden Sie Informationen zu den Abfrage Plänen, die für die Abfrage in Ziel 1 und Ziel 2 verwendet werden.

   > [!NOTE]
   > Wenn Sie das erweiterte Ereignis () analysieren. XEL-Dateien, Abfrageplan Informationen werden nicht erfasst, um die Arbeitsspeicher Auslastung auf dem Computer des Benutzers einzuschränken.

## <a name="see-also"></a>Weitere Informationen:

- Informationen zum Generieren eines Analyse Berichts an einer Eingabeaufforderung finden Sie unter [Ausführen an der Eingabeaufforderung](database-experimentation-assistant-run-command-prompt.md).
