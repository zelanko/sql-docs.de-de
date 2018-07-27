---
title: SQL Operations Studio (Vorschau) SQL Server-Agent-Erweiterung | Microsoft-Dokumentation
description: SQL Server-Agent-Erweiterung für SQL Operations Studio (Vorschau)
ms.custom: tools|sos
ms.date: 07/19/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 0da107a9f5dab0a9eb468bc3570788cff816b24a
ms.sourcegitcommit: 4b21840f20195d70f255465666f7b409ba839d18
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39147020"
---
# <a name="sql-server-agent-extension"></a>SQL Server-Agent-Erweiterung

Die SQL Server-Agent-Erweiterung ist eine Erweiterung für die Verwaltung und Problembehandlung von SQL Agent-Aufträge und die Konfiguration. Diese Erweiterung ist derzeit in der Vorschau.

Wichtige Aktionen zählen:
- Liste SQL Server-Agent-Aufträge auf einem SQLServer konfiguriert
- Auftragsverlauf anzeigen, mit den Ergebnissen der auftragsausführung
- Grundlegende Auftrag-Steuerelement zum Starten und Beenden von Aufträgen

## <a name="install-the-sql-server-agent-extension"></a>Installieren Sie die SQL Server-Agent-Erweiterung

1. Um Erweiterungs-Manager öffnen und den Zugriff auf die verfügbaren Erweiterungen, wählen Sie das Symbol für Erweiterungen oder **Erweiterungen** in die **Ansicht** Menü.
2. Wählen Sie eine verfügbare Erweiterung, um dessen Details anzuzeigen.

   ![Agentinstallation](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Wählen Sie die gewünschte Erweiterung und **installieren** es.
2. Wählen Sie **Reload** zum Aktivieren der Erweiterung (nur beim ersten eine Erweiterung der Installation erforderlich).
1. Navigieren Sie zu Ihrem Management-Dashboard, indem mit der rechten Maustaste den Server oder die Datenbank, und wählen **verwalten**.
2. Installierte Erweiterungen werden als Registerkarten auf dem Management-Dashboard angezeigt:

   ![Agent anzeigen](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Anzeigen von Aufträgen

Wenn Sie mit der SQL Server-Agent-Erweiterung verbinden, ist als Erstes sehen Sie eine Liste aller Agentaufträge.

   ![Anzeigen von Aufträgen](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server-Agent [finden Sie in unserer Dokumentation.](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017)


