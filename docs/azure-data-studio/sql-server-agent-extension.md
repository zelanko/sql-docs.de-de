---
title: SQL Server-Agent-Erweiterung
titleSuffix: Azure Data Studio
description: Installieren und Verwenden der SQL Server-Agent-Erweiterung (Vorschau) für Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 05356cc815fdba22d55ee339d60994f2c9423373
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "67959186"
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


