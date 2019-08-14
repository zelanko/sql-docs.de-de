---
title: Verwenden von Erkenntniswidgets in Azure Data Studio zum Überwachen von Servern und Datenbanken
titleSuffix: Azure Data Studio
description: Weitere Informationen zu Erkenntniswidgets in Azure Data Studio
ms.custom: seodec18, sqlfreshmay19
ms.date: 05/14/2019
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
ms.openlocfilehash: c1ab90efa97878676b1adc2a62579527407d6ba6
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959523"
---
# <a name="manage-servers-and-databases-with-insight-widgets-in-includename-sosincludesname-sos-shortmd"></a>Verwalten von Servern und Datenbanken mit Erkenntniswidgets in [!INCLUDE[name-sos](../includes/name-sos-short.md)]

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

[!INCLUDE[name-sos](../includes/name-sos-short.md)] versucht, die Einführung noch einer anderen Sprache oder großen Benutzeroberfläche zu vermeiden, also wird versucht, T-SQL so weit wie möglich mit minimaler JSON-Konfiguration zu verwenden. Das Konfigurieren von Erkenntniswidgets mit T-SQL nutzt die zahlreichen vorhandenen Quellen nützlicher T-SQL-Abfragen, die in aufschlussreiche Widgets umgewandelt werden können.

Erkenntniswidgets bestehen aus einer oder zwei T-SQL-Abfragen:
* Die *Erkenntniswidgetabfrage* ist obligatorisch und gibt die Daten zurück, die im Widget angezeigt werden.
* Die *Erkenntnisdetailsabfrage* ist nur erforderlich, wenn Sie eine Erkenntnisdetailsseite erstellen.

Eine Erkenntniswidgetabfrage definiert ein Dataset, das eine Anzahl, ein Diagramm oder einen Graphen rendert. Die Erkenntnisdetailsabfrage wird verwendet, um relevante Erkenntnisdetailinformationen im Erkenntnisdetailsbereich in einem Tabellenformat aufzulisten. 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] führt Erkenntniswidgetabfragen aus, ordnet das Abfrageresultset dem Dataset eines Diagramms zu und rendert es. Wenn Benutzer Details einer Erkenntnis öffnen, wird die Erkenntnisdetailsabfrage ausgeführt und das Ergebnis in einer Rasteransicht innerhalb des Dialogfelds ausgegeben.

Die grundlegende Idee ist, eine T-SQL-Abfrage so zu schreiben, dass sie als Dataset eines Anzahl-, Diagramm- und Graphwidgets verwendet werden kann. 

## <a name="summary"></a>Zusammenfassung

Die T-SQL-Abfrage und ihr Resultset bestimmen das Verhalten des Erkenntniswidgets. Das Schreiben einer Abfrage für einen Diagrammtyp oder die Zuordnung eines richtigen Diagrammtyps für eine vorhandene Abfrage ist der wichtigste Aspekt beim Erstellen eines effektiven Erkenntniswidgets.



## <a name="additional-resources"></a>Weitere Ressourcen
- [Abfrage-Editor](tutorial-sql-editor.md)

