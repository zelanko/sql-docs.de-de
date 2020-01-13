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
ms.openlocfilehash: 4fcb16d2ec3c267dc2927f22a029709a434416c9
ms.sourcegitcommit: 76fb3ecb79850a8ef2095310aaa61a89d6d93afd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776511"
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

1. Um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen, klicken Sie auf das Symbol für Erweiterungen, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus.
2. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.

   ![Profiler-Erweiterungs-Manager](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.
2. Klicken Sie auf **Erneut laden**, um die Erweiterung zu aktivieren (nur bei der Erstinstallation einer Erweiterung erforderlich).

## <a name="start-profiler"></a>Starten des Profilers

1. Um den Profiler zu starten, stellen Sie zunächst eine Verbindung mit einem Server auf der Registerkarte „Server“ her.
2. Nachdem Sie eine Verbindung hergestellt haben, drücken Sie **ALT+P**, um den Profiler zu starten.
3. Um den Profiler zu starten, drücken Sie **ALT+S**. Ab jetzt können Sie beginnen, erweiterte Ereignisse anzuzeigen.
    ![Profiler-Erweiterungs-Manager](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Um den Profiler zu stoppen, drücken Sie **ALT+S**. Diese Tastenkombination ist ein Umschalter.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Profiler und erweiterten Ereignissen finden Sie unter [Erweiterte Ereignisse](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).





