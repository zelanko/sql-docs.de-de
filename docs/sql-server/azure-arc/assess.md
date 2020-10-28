---
title: Konfigurieren der bedarfsgesteuerten SQL-Bewertung für eine Azure Arc-fähige SQL Server-Instanz
description: Konfigurieren der bedarfsgesteuerten SQL-Bewertung für eine Azure Arc-fähige SQL Server-Instanz
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 459a49a4f2ed41b8e9d95c805431ff2c29a770fa
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92258002"
---
# <a name="configure-sql-assessment-on-an-azure-arc-enabled-sql-server-instance"></a>Konfigurieren der SQL-Bewertung für eine Azure Arc-fähige SQL Server-Instanz

Die SQL-Bewertung bietet eine Möglichkeit, Ihre Konfiguration von SQL Server zu bewerten. In diesem Artikel finden Sie Anweisungen für die Verwendung der SQL-Bewertung in einer Azure Arc-fähigen SQL Server-Instanz.

## <a name="prerequisites"></a>Voraussetzungen

* Ihre SQL Server-Instanz muss mit Azure Arc verbunden sein. Anweisungen finden Sie im Artikel [Herstellen einer Verbindung zwischen Ihrer SQL Server-Instanz und Azure Arc](connect.md).

* Die MMA-Erweiterung (Microsoft Monitoring Agent) muss auf dem Computer installiert und konfiguriert sein. Anweisungen finden Sie im Artikel [Installieren von MMA](configure-advanced-data-security.md#install-microsoft-monitoring-agent-mma). Weitere Informationen finden Sie auch im Artikel zum [Log Analytics-Agent](/azure/azure-monitor/platform/log-analytics-agent).

* Für Ihre SQL Server-Instanz muss das [TCP/IP-Protokoll aktiviert](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md) sein.

* Der [SQL Server-Browserdienst](../../tools/configuration-manager/sql-server-browser-service.md) muss ausgeführt werden, wenn Sie eine benannte SQL Server-Instanz ausführen.

* Lesen Sie unbedingt das SQL Server-Dokument unter [Voraussetzungen für On-Demand-Bewertungen im Diensthub](/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents).

## <a name="run-on-demand-sql-assessment"></a>Ausführen der bedarfsgesteuerten SQL-Bewertung

1. Öffnen Sie Ihre SQL Server-Ressource mit Azure Arc-Aktivierung, und wählen Sie im linken Bereich die Option **Umgebungsintegrität** aus.

   > [!div class="mx-imgBorder"]
   > [ ![Screenshot des Bildschirms „Umgebungsintegrität“ einer SQL Server-Ressource mit Azure Arc-Aktivierung](media/assess/sql-assessment-heading-sql-server-arc.png) ](media/assess/sql-assessment-heading-sql-server-arc.png#lightbox)

1. Geben Sie ein Arbeitsverzeichnis auf dem Computer für die Datensammlung an. Standardmäßig wird `C:\sql_assessment\work_dir` verwendet. Während der Sammlung und Analyse werden die Daten vorrübergehend in diesem Ordner gespeichert. Wenn der Ordner nicht vorhanden ist, wird er automatisch erstellt.

1. Wählen Sie **Konfigurationsskript laden** aus. Kopieren Sie das heruntergeladene Skript auf den Zielcomputer.

1. Öffnen Sie eine Administratoreninstanz von **powershell.exe** , und führen Sie einen der folgenden Codeblöcke aus:

   * _Domänenkonto:_  Sie werden zur Eingabe von Benutzerkonto und Kennwort aufgefordert.

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1'
      ```

   * _Verwaltetes Dienstkonto (MSA)_

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1' -ManagedServiceAccountName <MSA account name>
      ```

> [!NOTE]
> Das Skript plant eine Aufgabe mit dem Namen *SQLAssessment* , die die Datensammlung auslöst. Diese Aufgabe wird innerhalb einer Stunde nach dem Ausführen des Skripts ausgeführt. Anschließend wird sie alle sieben Tage wiederholt.

> [!TIP]
> Sie können die Aufgabe so ändern, dass sie an einem anderen Datum und einer anderen Uhrzeit ausgeführt wird, und Sie können auch eine sofortige Ausführung erzwingen. Suchen Sie in der Aufgabenplanungsbibliothek nach **Microsoft** > **Operations Management Suite** > **AOI\*\*\***  > **Bewertungen** > **SQLAssessment** .

## <a name="view-sql-assessment-results"></a>Anzeigen der Ergebnisse der SQL-Bewertung

* Wählen Sie im Bereich _Umgebungsintegrität_ die Schaltfläche **View SQL Assessment results** (Ergebnisse der SQL-Bewertung anzeigen) aus.

   > [!NOTE]
   > Die Schaltfläche **View SQL Assessment result** (Ergebnisse der SQL-Bewertung anzeigen) ist solange deaktiviert, bis die Ergebnisse in Log Analytics bereitstehen. Dies kann bis zu zwei Stunden dauern, nachdem die Datendateien auf dem Zielcomputer verarbeitet wurden.

   > [!div class="mx-imgBorder"]
   > [ ![Screenshot der Ergebnisse der SQL-Bewertung](media/assess/sql-assessment-results.png) ](media/assess/sql-assessment-results.png#lightbox)

* Sie können den Status der Datenverarbeitung auf dem Sammlungscomputer sehen, indem Sie die Dateien im Arbeitsordner überprüfen. Nachdem die geplante Aufgabe abgeschlossen ist, sollten mehrere Dateien mit dem Präfix _new._ im Arbeitsverzeichnis angezeigt werden.

   > [!div class="mx-imgBorder"]
   > [ ![Screenshot eines Datei-Manager-Fensters mit neuen Datendateien im Arbeitsordner](media/assess/sql-assessment-data-files-ready.png) ](media/assess/sql-assessment-data-files-ready.png#lightbox)

* Der Microsoft Monitoring Agent scannt den Arbeitsordner alle 15 Minuten. Er sucht nach Dateien mit dem Präfix _new.*_ und sendet die Daten an den Log Analytics-Arbeitsbereich. Nachdem MMA die Datei hochgeladen hat, wird das Präfix von _new._ in _processed._ geändert.

   > [!div class="mx-imgBorder"]
   > ![Screenshot eines Datei-Manager-Fensters mit verarbeiteten Datendateien](media/assess/sql-assessment-data-files-processed.png)

## <a name="next-steps"></a>Nächste Schritte

* Weitere Informationen finden Sie in den Dokumenten zu den Voraussetzungen unter [Voraussetzungen für On-Demand-Bewertungen im Diensthub](/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents).

* Um eine umfassende Unterstützung des Features zur bedarfsgesteuerten SQL-Bewertung zu erhalten, ist ein Premier- oder Unified Support-Abonnement erforderlich. Weitere Informationen finden Sie unter [Azure Premier Support](https://azure.microsoft.com/support/plans/premier).
