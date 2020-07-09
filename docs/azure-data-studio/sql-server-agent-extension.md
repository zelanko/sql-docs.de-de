---
title: SQL Server-Agent-Erweiterung
description: Installieren und Verwenden der SQL Server-Agent-Erweiterung (Vorschau) für Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 3cdbfc4adc32156f838ee3aeca726c2ebd92bd0c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758359"
---
# <a name="sql-server-agent-extension-preview"></a>SQL Server-Agent-Erweiterung (Vorschau)

Die SQL Server-Agent-Erweiterung (Vorschau) ist eine Erweiterung zur Verwaltung und Problembehandlung von SQL Agent-Aufträgen und -Konfiguration. Diese Erweiterung befindet sich zurzeit in der Vorschau.

Zu den wichtigsten Aktionen gehören:
- Auflisten von SQL Server-Agent-Aufträgen, die auf einem SQL Server-Computer konfiguriert sind
- Anzeigen eines Auftragsverlaufs mit Auftragsausführungsergebnissen
- Grundlegende Auftragssteuerung, um Aufträge zu starten und zu stoppen

## <a name="install-the-sql-server-agent-extension"></a>Installieren der SQL Server-Agent-Erweiterung

1. Um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen, klicken Sie auf das Symbol für Erweiterungen, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus.
2. Wählen Sie eine verfügbare Erweiterung aus, um deren Details anzuzeigen.

   ![Agent installieren](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.
2. Klicken Sie auf **Erneut laden**, um die Erweiterung zu aktivieren (nur bei der Erstinstallation einer Erweiterung erforderlich).
1. Navigieren Sie zu Ihrem Management-Dashboard, indem Sie mit der rechten Maustaste auf Ihren Server oder Ihre Datenbank klicken und **Verwalten** auswählen.
2. Die installierten Erweiterungen werden als Registerkarten auf dem Management-Dashboard angezeigt:

   ![Agent anzeigen](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Anzeigen von Aufträgen

Wenn Sie eine Verbindung mit der SQL Server-Agent-Erweiterung herstellen, wird als erstes eine vollständige Liste Ihrer Agent-Aufträge angezeigt.

   ![Anzeigen von Aufträgen](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum SQL Server-Agent finden Sie in dessen [Dokumentation](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017).


