---
title: Konfigurieren der bedarfsgesteuerten SQL-Bewertung für eine Azure Arc-fähige SQL Server-Instanz
description: Konfigurieren der bedarfsgesteuerten SQL-Bewertung für eine Azure Arc-fähige SQL Server-Instanz
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: c6f2a0989cb13253ef4a6a26e013a6b8c7a84ded
ms.sourcegitcommit: f888ac94c7b5f6b6f138ab75719dadca04e8284a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93294379"
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

> [!IMPORTANT]
> Wenn die MMA-Erweiterung nicht installiert ist, können Sie die bedarfsgesteuerte SQL-Bewertung nicht initiieren.

2. Wählen Sie den Kontotyp aus. Wenn Sie über ein verwaltetes Dienstkonto verfügen, können Sie die SQL-Bewertung direkt über das Portal initiieren. Geben Sie den Kontonamen an.

> [!NOTE]
> Wenn Sie ein *verwaltetes Dienstkonto* angeben, wird die Schaltfläche **Configure SQL Assessment** (SQL-Bewertung konfigurieren) aktiviert, damit Sie die Bewertung durch Bereitstellen einer benutzerdefinierten Skripterweiterung ( *CustomScriptExtension* ) über das Portal initiieren können. Da jeweils nur eine *benutzerdefinierte Skripterweiterung* bereitgestellt werden kann, wird die Skripterweiterung für die SQL-Bewertung automatisch nach der Ausführung entfernt. Wenn Sie bereits eine andere *benutzerdefinierte Skripterweiterung* auf dem Hostcomputer bereitgestellt haben, wird die Schaltfläche **SQL-Bewertung konfigurieren** nicht aktiviert.

3. Geben Sie ein Arbeitsverzeichnis auf dem Computer an, auf dem die Datensammlung erfolgt, wenn Sie das Standardverzeichnis ändern möchten. Standardmäßig wird `C:\sql_assessment\work_dir` verwendet. Während der Sammlung und Analyse werden die Daten vorrübergehend in diesem Ordner gespeichert. Wenn der Ordner nicht vorhanden ist, wird er automatisch erstellt.

4. Wenn Sie die SQL-Bewertung über das Portal initiieren, indem Sie auf **SQL-Bewertung konfigurieren** klicken, wird ein Standardbereitstellungspopup angezeigt.

> [!div class="mx-imgBorder"]
   > [ ![Screenshot: Bereitstellung der benutzerdefinierten Skripterweiterung](media/assess/sql-assessment-custom-script-deployment.png) ](media/assess/sql-assessment-custom-script-deployment.png#lightbox)

5. Wenn Sie die SQL-Bewertung lieber auf dem Zielcomputer initiieren möchten, klicken Sie auf **Konfigurationsskript laden** , kopieren Sie das heruntergeladene Skript auf den Zielcomputer, und führen Sie einen der folgenden Codeblöcke in einer Administratorinstanz von **powershell.exe** aus:

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
> Sie können den Task so ändern, dass sie an einem anderen Datum und einer anderen Uhrzeit ausgeführt wird. Sie können auch eine sofortige Ausführung erzwingen. Suchen Sie in der Aufgabenplanungsbibliothek nach **Microsoft** > **Operations Management Suite** > **AOI\*\*\***  > **Bewertungen** > **SQLAssessment**.

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
