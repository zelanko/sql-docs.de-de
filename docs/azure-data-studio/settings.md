---
title: Azure Data Studio-Benutzer und Arbeitsbereichseinstellungen | Microsoft-Dokumentation
description: 'Vorgehensweise: Ändern von Azure Data Studio-Benutzer und Arbeitsbereichseinstellungen.'
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: e446d117bd56cb0c3607eeaf40522800d82e8a7e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038473"
---
# <a name="user-and-workspace-settings"></a>Benutzer und -Arbeitsbereichseinstellungen

Es ist leicht zu konfigurierender [!INCLUDE[name-sos](../includes/name-sos-short.md)] an Ihre vorstellungen über die Einstellungen an. Fast jeder Teil [!INCLUDE[name-sos](../includes/name-sos-short.md)]des Editor-Benutzeroberfläche und Verhalten verfügt über Optionen können Sie ändern.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] bietet zwei unterschiedliche Gültigkeitsbereiche für die Einstellungen an:

* **Benutzer** diese Einstellungen gelten global für eine beliebige Instanz von [!INCLUDE[name-sos](../includes/name-sos-short.md)] öffnen.
* **Arbeitsbereich** arbeitsbereichseinstellungen sind Einstellungen, die spezifisch für einen Ordner auf Ihrem Computer, und sind nur verfügbar, wenn der Ordner in der Randleiste Explorer geöffnet ist. In diesem Bereich definierte Einstellungen überschreiben den Benutzerbereich an.

## <a name="creating-user-and-workspace-settings"></a>Erstellen von Benutzer- und Arbeitsbereichseinstellungen

Der Menübefehl **Datei** > **Voreinstellungen** > **Einstellungen** (**Code**  >  **Voreinstellungen** > **Einstellungen** auf Mac) stellt den Einstiegspunkt zum Konfigurieren von Einstellungen für Benutzer und -Arbeitsbereich bereit. Sie werden eine Liste mit den Standardeinstellungen bereitgestellt. Kopieren Sie jede Einstellung, die Sie in den entsprechenden ändern möchten `settings.json` Datei. Die Registerkarten auf der rechten Seite können Sie schnell zwischen den Einstellungen für Benutzer und -Arbeitsbereich zu wechseln.

Sie können auch die Einstellungen für Benutzer und -Arbeitsbereich aus öffnen die **Befehlspalette** (**STRG + UMSCHALT + P**) mit **Voreinstellungen: Öffnen von Benutzereinstellungen** und  **Einstellungen: Öffnen des Arbeitsbereichseinstellungen** oder verwenden Sie die Tastenkombination (**STRG +,**).

Das folgende Beispiel deaktiviert die Zeilennummern im Editor und Codezeilen automatisch eingezogen werden konfiguriert.

![Beispieleinstellungen](media/settings/sample-settings.png)

Änderungen an den Einstellungen werden neu geladen, indem [!INCLUDE[name-sos](../includes/name-sos-short.md)] nach geänderten `settings.json` -Datei wird gespeichert.

>**Hinweis:** arbeitsbereichseinstellungen eignen sich für die Freigabe von projektspezifische Einstellungen innerhalb eines Teams.

## <a name="settings-file-locations"></a>Von Dateispeicherorten

Je nach Plattform befindet sich die Datei mit den Benutzer hier:

* **Windows** `%APPDATA%\sqlops\User\settings.json`
* **Mac** `$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux** `$HOME/.config/sqlops/User/settings.json`

Die Arbeitsbereich-Einstellungsdatei befindet sich unter dem `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` -Ordner des Projekts.

## <a name="hot-exit"></a>"Hot" Beenden

Azure Data Studio speichert nicht gespeicherte Änderungen auf Dateien, beim Beenden des standardmäßig. Dies ist identisch mit den "Hot" Exit-Funktion in Visual Studio Code.

Standardmäßig ist die "Hot" Beenden aus. Aktivieren von "Hot" Beenden durch Bearbeiten der `files.hotExit` festlegen. Weitere Informationen finden Sie unter ["Hot" Beenden (in der Dokumentation zu Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Der Farbe

Zur Vereinfachung der Identifizierung von Verbindungen mit dem Sie arbeiten, haben die geöffneten Registerkarten in den Editor ihre Farbe festlegen, die die Farbe des der Servergruppe übereinstimmen, die die Verbindung zu gehört. Sind standardmäßig registerkartenfarben standardmäßig deaktiviert. Aktivieren der registerkartenfarben durch Bearbeiten der `sql.tabColorMode` festlegen.

## <a name="additional-resources"></a>Weitere Ressourcen

Da [!INCLUDE[name-sos](../includes/name-sos-short.md)] erbt die Benutzer- und Arbeitsbereich-Einstellungen, die von Visual Studio Code, der detaillierte Informationen zu Einstellungen, die die Funktion in ist der [Einstellungen für Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) Artikel.
