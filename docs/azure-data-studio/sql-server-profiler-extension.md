---
title: SQL Server Profiler-Erweiterung
titleSuffix: Azure Data Studio
description: Installieren und Verwenden der SQL Server Profiler-Erweiterung (Vorschau) für Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 26a448dc27ae2512256ffb1a2929dd8cacc3e31c
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959118"
---
# <a name="sql-server-profiler-extension-preview"></a>SQL Server Profiler-Erweiterung (Vorschau)

Die SQL Server Profiler-Erweiterung (Vorschauversion) bietet eine einfache SQL Server-Ablaufverfolgungslösung, die, abgesehen vom Erstellen mit erweiterten Ereignissen, sehr SQL Server Management Studio Profiler (SSMS Profiler) ähnelt. SQL Server Profiler ist sehr einfach zu verwenden und hat brauchbare Standardwerte für die gängigsten Ablaufverfolgungskonfigurationen. Die Umgebung ist für das Durchsuchen von Ereignissen und das Anzeigen des zugehörigen T-SQL-Texts (Transact-SQL) optimiert. Der SQL Server Profiler für Azure Data Studio hat außerdem brauchbare Standardwerte für die Erfassung von T-SQL-Ausführungsaktivitäten mit einer einfach zu bedienenden Umgebung. Diese Erweiterung befindet sich zurzeit in der Vorschau.

**Gängige Anwendungsfälle für SQL Server Profiler:**

- Schrittweises Untersuchen problematischer Abfragen, um die Ursache des Problems zu ermitteln.
- Suchen und Diagnostizieren von Abfragen, die sehr langsam ausgeführt werden.
- Erfassen der Reihe der Transact-SQL-Anweisungen, die zu einem Problem geführt haben.
- Überwachen der Leistung von SQL Server, um die Arbeitsauslastung zu optimieren.
- Korrelieren von Leistungsindikatoren zur Diagnose von Problemen.


## <a name="install-the-sql-server-profiler-extension"></a>Installieren der SQL Server Profiler-Erweiterung

1. Um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen, wählen Sie das Symbol für Erweiterungen aus, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus.
2. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.

   ![Profiler-Erweiterungs-Manager](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Wählen Sie die gewünschte Erweiterung aus, und **Installieren** Sie diese.
2. Wählen Sie **Neu laden** aus, um die Erweiterung zu aktivieren (nur bei der ersten Installation einer Erweiterung erforderlich).

## <a name="start-profiler"></a>Starten des Profilers

1. Um den Profiler zu starten, stellen Sie zunächst eine Verbindung mit einem Server auf der Registerkarte „Server“ her.
2. Nachdem Sie eine Verbindung hergestellt haben, drücken Sie **ALT+P**, um den Profiler zu starten.
3. Um den Profiler zu starten, drücken Sie **ALT+S**. Ab jetzt können Sie beginnen, erweiterte Ereignisse anzuzeigen.
    ![Profiler-Erweiterungs-Manager](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Um den Profiler zu stoppen, drücken Sie **ALT+S**. Diese Tastenkombination ist ein Umschalter.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Profiler und erweiterten Ereignissen finden Sie unter [Erweiterte Ereignisse](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).





