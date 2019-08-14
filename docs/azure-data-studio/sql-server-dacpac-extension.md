---
title: Die DACPAC-Erweiterung für SQL Server
titleSuffix: Azure Data Studio
description: Installieren und Verwenden der DACPAC-Erweiterung für SQL Server (Vorschauversion) für Azure Data Studio
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: e40e377310b33034b4abecdc5e58eab17d39695d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959199"
---
# <a name="sql-server-dacpac-extension-preview"></a>DACPAC-Erweiterung für SQL Server (Vorschauversion)

**Der Assistent für die Datenschichtanwendung** macht die Bereitstellung und Extrahierung von DACPAC-Dateien und das Importieren und Exportieren von BACPAC-Dateien einfach.

Diese Funktion befindet sich derzeit in der ersten Vorschauversion. Probleme und Featureanforderungen können Sie [hier](https://github.com/microsoft/azuredatastudio/issues) mitteilen.

![data-actions](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>Anforderungen
 * Zum Starten erfordert der Assistent eine aktive Verbindung zu einer SQL Server-Instanz.

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>Wie wird der Assistent für Datenschichtanwendungen gestartet?
 * Der Haupteinstiegspunkt für den Assistenten ist ein Rechtsklick auf eine Datenbank im Objekt-Explorer. Klicken Sie anschließend auf **Data-tier Application wizard** (Assistent für die Datenschichtanwendung).
 * Wenn ein Benutzer mit einer SQL Server-Instanz verbunden ist, kann dieser den Assistenten auch über die Befehlspalette (STRG+UMSCHALT+P) starten, indem er nach dem **Assistenten für die Datenschichtanwendung** sucht.

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>Warum sollte ich den Assistent für Datenschichtanwendungen verwenden?
 Dieser Assistent wurde erstellt, um die Möglichkeit zum Extrahieren und Bereitstellen von DACPAC-Dateien sowie zum Importieren und Exportieren von BACPAC-Dateien in Azure Data Studio hinzuzufügen.

## <a name="install-the-sql-server-dacpac-extension"></a>Installieren der DACPAC-Erweiterung für SQL Server

1. Wählen Sie das Symbol für Erweiterungen aus, oder wählen Sie im Menü **Ansicht** den Befehl **Erweiterungen** aus, um den Erweiterungs-Manager zu öffnen und auf die verfügbaren Erweiterungen zuzugreifen.
2. Wählen Sie die DACPAC-Erweiterung für SQL Server aus, und klicken Sie auf **Installieren**.
1. Klicken Sie auf **Reload** (Erneut laden), um die Erweiterung zu aktivieren (nur bei der ersten Installation einer Erweiterung erforderlich).
2. Navigieren Sie zu Ihrem Management-Dashboard, indem Sie mit der rechten Maustaste auf Ihren Server oder Ihre Datenbank klicken und **Verwalten** auswählen.
3. Die installierten Erweiterungen werden als Registerkarten auf dem Management-Dashboard angezeigt:

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu DACBAC-Erweiterungen finden Sie in der zugehörigen [Dokumentation](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017).