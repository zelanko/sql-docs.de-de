---
title: SQL Server-Dacpac-Erweiterung
titleSuffix: Azure Data Studio
description: Installieren Sie und verwenden Sie die Erweiterung für SQL Server-DACPAC-Datei (Vorschau) für Azure Data Studio
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: jroth
ms.openlocfilehash: 70b06749d1cbecc2127c70fee28b60f49583d5ce
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66797988"
---
# <a name="sql-server-dacpac-extension-preview"></a>DACPAC-Erweiterung für SQL Server (Vorschauversion)

**Der Datenebenen-Anwendungs-Assistent** bietet eine benutzerfreundliche Funktionen zum Bereitstellen und DACPAC-Dateien zu extrahieren und importieren und Exportieren der bacpac-Dateien.

Diese Benutzeroberfläche befindet sich derzeit in der ersten Vorschauversion. Bitte melden Sie Probleme und Funktionsanfragen [hier.](https://github.com/microsoft/azuredatastudio/issues)

![Data-Aktionen](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>Anforderungen
 * Dieser Assistent benötigt eine aktive Verbindung mit SQL Server-Instanz zu starten.

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>Wie beginne ich mit der der Datenebenen-Anwendungs-Assistent?
 * Der Haupteinstiegspunkt für den Assistenten ist, klicken Sie mit der rechten Maustaste auf eine Datenbank im Objekt-Explorer, und klicken Sie auf **Datenebenen-Anwendungs-Assistent**.
 * Wenn ein Benutzer mit einer SQL Server-Instanz verbunden ist, die Benutzer kann den Assistenten auch starten über die befehlspalette (STRG + UMSCHALT + P) durch Suchen nach **Datenebenen-Anwendungs-Assistenten.**

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>Warum sollte ich der Datenebenen-Anwendungs-Assistent verwenden?
 Dieser Assistent wurde erstellt, um die Möglichkeit, extrahieren und Bereitstellen von DACPAC-Dateien importieren und Exportieren der bacpac-Dateien in Azure Data Studio hinzuzufügen.

## <a name="install-the-sql-server-dacpac-extension"></a>Installieren der Erweiterung der SQL Server-DACPAC-Datei

1. Um Erweiterungs-Manager öffnen und den Zugriff auf die verfügbaren Erweiterungen, wählen Sie das Symbol für Erweiterungen oder **Erweiterungen** in die **Ansicht** Menü.
2. Wählen Sie die SQL Server-Erweiterung DACPAC-Datei, und klicken Sie auf **installieren**.
1. Wählen Sie **Reload** zum Aktivieren der Erweiterung (nur beim ersten eine Erweiterung der Installation erforderlich).
2. Navigieren Sie zu Ihrem Management-Dashboard, indem mit der rechten Maustaste den Server oder die Datenbank, und wählen **verwalten**.
3. Installierte Erweiterungen werden als Registerkarten auf dem Management-Dashboard angezeigt:

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Dacpac [finden Sie in unserer Dokumentation.](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)