---
title: Planen von SSIS-Pakete auf Linux mit Cron | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie Sie SQL Server Integration Services (SSIS)-Pakete für Linux mit dem Cron-Dienst zu planen.
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 2e3c9f6ee7a02fcdfe1bb2888832b156669cbc11
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66015003"
---
# <a name="schedule-sql-server-integration-services-package-execution-on-linux-with-cron"></a>Zeitplan SQL Server Integration Services-paketausführung unter Linux mit cron

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Beim Ausführen von SQL Server Integration Services (SSIS) und SQL Server unter Windows können Sie die Ausführung von SSIS-Paketen mit SQL Server-Agent automatisieren. Beim Ausführen von SQL Server- und SSIS auf Linux ist jedoch nicht, das SQL Server-Agent-Hilfsprogramm zum Planen von Aufträgen unter Linux verfügbar. Stattdessen verwenden Sie den Cron-Diensts, die häufig auf Linux-Plattformen zum Automatisieren der paketausführung verwendet wird.

Dieser Artikel enthält Beispiele, die zeigen, wie Sie die Ausführung von SSIS-Paketen zu automatisieren. In den Beispielen werden geschrieben, auf Red Hat Enterprise ausgeführt wird. Der Code ist ähnlich für andere Linux-Distributionen wie Ubuntu.

## <a name="prerequisites"></a>Erforderliche Komponenten

Bevor Sie den Cron-Dienst zum Ausführen von Aufträgen verwenden, überprüfen Sie, ob sie auf Ihrem Computer ausgeführt wird.

Um den Status des Cron-Diensts zu überprüfen, verwenden Sie den folgenden Befehl: `systemctl status crond.service`.

Wenn der Dienst nicht aktiv ist (d. h. es wird nicht ausgeführt), wenden Sie sich an Ihren Administrator, um das Einrichten und konfigurieren Sie den Cron-Dienst ordnungsgemäß.

## <a name="create-jobs"></a>Erstellen von Aufträgen

Ein Cron-Auftrag ist eine Aufgabe, die Sie konfigurieren können, um regelmäßig in einem angegebenen Intervall ausgeführt. Der Auftrag kann so einfach wie ein Befehl sein, die Sie normalerweise Geben Sie direkt in der Konsole oder als ein Shell-Skript ausführen würden.

Einfache Verwaltung und zu Wartungszwecken empfehlen wir, dass Sie die paketausführung Befehle in einem Skript einfügen, die einen beschreibenden Namen enthält.

Hier ist ein Beispiel für ein einfaches Shell-Skript zum Ausführen eines Pakets aus. Enthält nur einen einzelnen Befehl, aber Sie können weitere Befehle hinzufügen, wie erforderlich.

```bash
# A simple shell script that contains a simple package execution command
# Script name: SSISpackageName.daily

/opt/ssis/bin/dtexec /F yourSSISpackageName.dtsx >> $HOME/tmp/out 2>&1
```

## <a name="schedule-jobs-with-the-cron-service"></a>Planen von Aufträgen mit den Cron-Diensts

Nachdem Sie Ihre Aufträge definiert haben, können Sie sie mithilfe des Cron-Diensts automatisch ausgeführt. planen.

Fügen Sie zum Hinzufügen des Auftrags für Cron, führen Sie den Auftrag in der Datei "crontab" hinzu. Um die Datei "crontab" in einem Editor zu öffnen, in dem Sie hinzufügen oder Aktualisieren des Auftrags können, verwenden Sie den folgenden Befehl: `crontab -e`.

Fügen Sie zum Planen des zuvor beschriebenen Auftrags täglich um 2:10 Uhr ausgeführt. die folgende Zeile in die Datei "crontab":

```
# run <SSIS package name> at 2:10 AM every day
10 2 \* \* \* $/HOME/SSIS/jobs/SSISpackageName.daily
```

Speichern Sie die Datei "crontab", und beenden Sie den Editor.

Überprüfen Sie die Informationen im folgenden Abschnitt, um das Format des beispielbefehls zu verstehen.
 
## <a name="format-of-a-crontab-file"></a>Format der Datei "crontab"

Die folgende Abbildung zeigt die Format-Beschreibung der Auftrag an, das die Datei "crontab" hinzugefügt wird.

![Format-Beschreibung für den Eintrag in "crontab"-Datei](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-job-definition.png)

Rufen Sie eine ausführlichere Beschreibung des Dateiformats "crontab" mit den folgenden Befehl: `man 5 crontab`.

Hier ist eine partielle Beispiel der Ausgabe, die hilft, die im Beispiel in diesem Artikel wird erläutert:

![Ausführliche teilweise Beschreibung des Formats von "crontab"](media/sql-server-linux-schedule-ssis-packages/ssis-linux-cron-crontab-format.png)

## <a name="related-content-about-ssis-on-linux"></a>Verwandte Inhalte zu SSIS unter Linux
-   [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](sql-server-linux-migrate-ssis.md)
-   [Installieren von SQL Server Integration Services (SSIS) unter Linux](sql-server-linux-setup-ssis.md)
-   [Konfigurieren von SQL Server Integration Services unter Linux mit Ssis-conf](sql-server-linux-configure-ssis.md)
-   [Einschränkungen und bekannte Probleme für SSIS unter Linux](sql-server-linux-ssis-known-issues.md)
