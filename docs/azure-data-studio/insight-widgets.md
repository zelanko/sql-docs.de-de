---
title: Verwenden von Erkenntniswidgets zum Überwachen von Servern und Datenbanken
description: Erfahren Sie, wie Sie Erkenntniswidgets von Azure Data Studio verwenden, um Abfragen zum Überwachen von Servern und Datenbanken in erkenntnisreiche Visualisierungen umzuwandeln.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein
ms.custom: seodec18, sqlfreshmay19, seo-lt-2019
ms.date: 05/14/2019
ms.openlocfilehash: c93cd3ea16b87a23dac96c1f21f3720d169e8c19
ms.sourcegitcommit: 63aef5a96905f0b026322abc9ccb862ee497eebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91364013"
---
# <a name="manage-servers-and-databases-with-insight-widgets-in-azure-data-studio"></a>Verwalten von Servern und Datenbanken mit Erkenntniswidgets in Azure Data Studio

Erkenntniswidgets führen die Transact-SQL-Abfragen (T-SQL) aus, die Sie zum Überwachen von Servern und Datenbanken verwenden, und wandeln sie in aufschlussreiche Visualisierungen um.

Erkenntnisse sind anpassbare Diagramme und Graphen, die Sie den Dashboards für die Server- und Datenbanküberwachung hinzufügen. Zeigen Sie auf einen Blick Erkenntnisse zu Ihren Servern und Datenbanken an, gehen Sie dann weiter ins Detail, und starten Sie Verwaltungsaktionen, die Sie definieren.

Sie können beeindruckende Dashboards für die Server- und Datenbankverwaltung erstellen, ähnlich wie im folgenden Beispiel:

![Datenbankdashboard](media/insight-widgets/database-dashboard.png)

In den folgenden Tutorials erfahren Sie, wie Sie damit beginnen, verschiedene Arten von Erkenntniswidgets zu erstellen:

- [Erstellen eines benutzerdefinierten Erkenntniswidgets](tutorial-build-custom-insight-sql-server.md)
- *Aktivieren integrierter Erkenntniswidgets*
  - [Aktivieren der Leistungsüberwachungserkenntnis](tutorial-qds-sql-server.md)
  - [Aktivieren der Tablespacenutzungs-Erkenntnis](tutorial-table-space-sql-server.md)

## <a name="sql-queries"></a>SQL-Abfragen

Azure Data Studio versucht, die Einführung einer weiteren Sprache oder eine große Benutzeroberfläche zu vermeiden. Deshalb wird versucht, so viel wie möglich T-SQL mit minimaler JSON-Konfiguration zu verwenden. Das Konfigurieren von Erkenntniswidgets mit T-SQL nutzt die zahlreichen vorhandenen Quellen nützlicher T-SQL-Abfragen, die in aufschlussreiche Widgets umgewandelt werden können.

Erkenntniswidgets bestehen aus einer oder zwei T-SQL-Abfragen:
* Die *Erkenntniswidgetabfrage* ist obligatorisch und gibt die Daten zurück, die im Widget angezeigt werden.
* Die *Erkenntnisdetailsabfrage* ist nur erforderlich, wenn Sie eine Erkenntnisdetailsseite erstellen.

Eine Erkenntniswidgetabfrage definiert ein Dataset, das eine Anzahl, ein Diagramm oder einen Graphen rendert. Die Erkenntnisdetailsabfrage wird verwendet, um relevante Erkenntnisdetailinformationen im Erkenntnisdetailsbereich in einem Tabellenformat aufzulisten. 

Azure Data Studio führt Erkenntniswidgetabfragen aus, ordnet das Abfrageresultset dem Dataset eines Diagramms zu und rendert es. Wenn Benutzer Details einer Erkenntnis öffnen, wird die Erkenntnisdetailsabfrage ausgeführt und das Ergebnis in einer Rasteransicht innerhalb des Dialogfelds ausgegeben.

Die grundlegende Idee ist, eine T-SQL-Abfrage so zu schreiben, dass sie als Dataset eines Anzahl-, Diagramm- und Graphwidgets verwendet werden kann. 

## <a name="summary"></a>Zusammenfassung

Die T-SQL-Abfrage und ihr Resultset bestimmen das Verhalten des Erkenntniswidgets. Das Schreiben einer Abfrage für einen Diagrammtyp oder die Zuordnung eines richtigen Diagrammtyps für eine vorhandene Abfrage ist der wichtigste Aspekt beim Erstellen eines effektiven Erkenntniswidgets.



## <a name="additional-resources"></a>Zusätzliche Ressourcen
- [Abfrage-Editor](tutorial-sql-editor.md)

