---
title: Konfigurieren der SQL-Bewertung für Azure Arc-fähige SQL Server-Instanzen
titleSuffix: ''
description: Konfigurieren der bedarfsgesteuerten SQL-Bewertung für Azure Arc-fähige SQL Server-Instanzen
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 09/10/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: f3d2051e7003407a4ba7cbb3fb2ff8682ec6ee8f
ms.sourcegitcommit: 8f062015c2a033f5a0d805ee4adabbe15e7c8f94
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91227323"
---
# <a name="configure-on-demand-sql-assessment-for-azure-arc-enabled-sql-server-instance"></a>Konfigurieren der bedarfsgesteuerten SQL-Bewertung für Azure Arc-fähige SQL Server-Instanzen

Sie können die SQL-Bewertung für Ihre SQL Server-Instanzen aktivieren, indem Sie die folgenden Schritte befolgen.

## <a name="prerequisites"></a>Voraussetzungen

* Ihre SQL Server-Instanz ist mit Azure Arc verbunden. Befolgen Sie diese Anleitung, um [ein Onboarding für Ihre SQL Server-Instanz für eine Arc-fähige SQL Server-Instanz durchzuführen](connect.md).

* Die MMA-Erweiterung ist auf dem Computer installiert und konfiguriert. Befolgen Sie diese Anleitung, um [Microsoft Monitoring Agent (MMA) zu installieren](configure-advanced-data-security.md#install-microsoft-monitoring-agent-mma). Weitere Informationen finden Sie unter [Log Analytics-Agent](https://docs.microsoft.com/azure/azure-monitor/platform/log-analytics-agent).

* Für Ihre SQL Server-Instanz wurde das [TCP/IP-Protokoll aktiviert](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).

* Der [SQL Server-Browser](../../tools/configuration-manager/sql-server-browser-service.md) wird ausgeführt, wenn Sie eine benannte Instanz von SQL Server ausführen.

* Sie haben sich das SQL Server-Dokument unter [Voraussetzungen für On-Demand-Bewertungen im Diensthub](https://docs.microsoft.com/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents) angesehen.

## <a name="enable-on-demand-sql-assessment"></a>Aktivieren der bedarfsgesteuerten SQL-Bewertung

1. Öffnen Sie Ihre SQL Server-Ressource mit Azure Arc-Aktivierung, und klicken Sie im linken Menü auf die Option __Umgebungsintegrität__.

   ![Auswahl der SQL-Bewertung](media/assess/sql-assessment-heading-sql-server-arc.png)

1. Geben Sie ein Arbeitsverzeichnis auf dem Computer für die Datensammlung an. Standardmäßig wird `C:\sql_assessment\work_dir` verwendet. Während der Sammlung und Analyse werden die Daten vorrübergehend in diesem Ordner gespeichert. Wenn der Ordner nicht vorhanden ist, wird er automatisch erstellt.

1. Klicken Sie auf __Konfigurationsskript herunterladen__, und kopieren Sie das heruntergeladene Skript auf den Zielcomputer.

1. Starten Sie eine Administratoreninstanz von __powershell.exe__, und führen Sie eine der folgenden Aktionen aus: 
   * Wenn Sie ein Domänenkonto nutzen, führen Sie die folgenden Befehle aus. Sie werden zur Eingabe des Benutzerkontos und Kennworts aufgefordert. 

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1'
      ```

    * Wenn Sie ein MSA-Konto nutzen, führen Sie die folgenden Befehle aus.

      ```powershell
      Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass -Force
      & '.\AddSqlAssessment.ps1' -ManagedServiceAccountName <MSA account name>
      ```

   > [!NOTE]
   > Das Skript plant eine Aufgabe namens *SQLAssessment*, die innerhalb einer Stunde nach Ausführung des vorherigen Skripts und dann alle sieben Tage ausgeführt wird. Die Aufgabe kann so bearbeitet werden, dass sie an einem anderen Datum und zu einer anderen Uhrzeit ausgeführt wird. Es kann auch eine sofortige Ausführung erzwungen werden. Navigieren Sie dazu in der Aufgabenplanungsbibliothek zu Microsoft > Operations Management Suite > AOI*** > Bewertungen > SQLAssessment Diese Aufgabe löst die Datensammlung aus.

## <a name="view-the-assessment-results"></a>Anzeigen der Bewertungsergebnisse

Die Schaltfläche __View SQL assessment result__ (SQL-Bewertungsergebnis anzeigen) auf dem Blatt _Umgebungsintegrität_ ist solange deaktiviert, bis die Ergebnisse in Log Analytics zur Verwendung bereit stehen. Sobald die Schaltfläche aktiv ist, können Sie darauf klicken, um die Ergebnisse anzuzeigen. Es kann bis zu zwei Stunden dauern, bis die Ergebnisse in Log Analytics angezeigt werden, nachdem die Datendateien auf dem Zielcomputer verarbeitet wurden.

![SQL-Bewertungsergebnisse](media/assess/sql-assessment-results.png)

Sie können den Status der Datenverarbeitung auf dem Sammlungscomputer sehen, indem Sie die Dateien im Arbeitsordner überprüfen. Nachdem die geplante Aufgabe abgeschlossen ist, sollten mehrere Dateien mit dem Präfix _new._ im Arbeitsverzeichnis angezeigt werden:

![Bereite Datendateien](media/assess/sql-assessment-data-files-ready.png)

Der Arbeitsordner wird von Microsoft Monitoring Agent alle 15 Minuten gescannt, um nach _new.*_ -Dateien zu suchen. Die Daten werden dann an den Arbeitsbereich in Log Analytics gesendet. Sobald die Datei hochgeladen wurde, ändert sich das Präfix von _new._ in _processed._ :

![Verarbeitete Datendateien](media/assess/sql-assessment-data-files-processed.png)

## <a name="next-steps"></a>Nächste Schritte

Sehen Sie sich das SQL Server-Dokument unter [Voraussetzungen für On-Demand-Bewertungen im Diensthub](https://docs.microsoft.com/services-hub/health/assessment-prereq-docs#on-demand-assessment-prerequisite-documents) an, um weitere Informationen zu erhalten.

Um eine umfassende Unterstützung der bedarfsgesteuerten SQL-Bewertung zu erhalten, ist ein Premier- oder Unified Support-Abonnement erforderlich. Weitere Informationen finden Sie unter [Azure Premier Support](https://azure.microsoft.com/support/plans/premier).
