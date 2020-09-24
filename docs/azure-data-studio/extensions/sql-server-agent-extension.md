---
title: SQL Server-Agent-Erweiterung
description: Erfahren Sie, wie Sie die SQL Server-Agent-Erweiterung für Azure Data Studio installieren und verwenden, eine Erweiterung zur Verwaltung von SQL-Agent-Aufträgen und -Konfigurationen.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 3d00919c0967db12dfe678ad541a5a9ed9ecae61
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123122"
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

   ![Agent installieren](media/sql-server-agent-extension/install-sql-agent.png)

3. Wählen Sie die gewünschte Erweiterung aus, und **installieren** Sie diese.
4. Klicken Sie auf **Erneut laden**, um die Erweiterung zu aktivieren (nur bei der Erstinstallation einer Erweiterung erforderlich).
5. Navigieren Sie zu Ihrem Management-Dashboard, indem Sie mit der rechten Maustaste auf Ihren Server oder Ihre Datenbank klicken und **Verwalten** auswählen.
6. Die installierten Erweiterungen werden als Registerkarten auf dem Management-Dashboard angezeigt:

   ![Agent anzeigen](media/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Anzeigen von Aufträgen

Wenn Sie eine Verbindung mit der SQL Server-Agent-Erweiterung herstellen, wird als erstes eine vollständige Liste Ihrer Agent-Aufträge angezeigt.

   ![Anzeigen von Aufträgen](media/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum SQL Server-Agent finden Sie in dessen [Dokumentation](../../ssms/agent/sql-server-agent.md).
