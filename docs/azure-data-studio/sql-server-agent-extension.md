---
title: Azure Data Studio SQL Server-Agent-Erweiterung | Microsoft-Dokumentation
description: SQL Server-Agent-Erweiterung (Vorschauversion) für Azure Data Studio
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 5804aa146ddf79f6c3c4ccba48edd86d297c5c72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038587"
---
# <a name="sql-server-agent-extension-preview"></a>SQL Server-Agent-Erweiterung (Vorschau)

Die SQL Server-Agent-Erweiterung (Vorschauversion) ist eine Erweiterung für die Verwaltung und Problembehandlung von SQL Agent-Aufträge und die Konfiguration. Diese Erweiterung ist derzeit in der Vorschau.

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


