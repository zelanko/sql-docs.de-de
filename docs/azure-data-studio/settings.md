---
title: Benutzer und -Arbeitsbereichseinstellungen
titleSuffix: Azure Data Studio
description: Vorgehensweise zum Studio für Azure Data anpassen, indem Sie Benutzer und Arbeitsbereichseinstellungen ändern.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: a874aaf9ec136ff9ea27cbeaa92011a07f3718c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959270"
---
# <a name="modify-user-and-workspace-settings"></a>Benutzer und Arbeitsbereichseinstellungen ändern

Es ist leicht zu konfigurierender [!INCLUDE[name-sos](../includes/name-sos-short.md)] an Ihre vorstellungen über die Einstellungen an. Fast jeder Teil [!INCLUDE[name-sos](../includes/name-sos-short.md)]des Editor-Benutzeroberfläche und Verhalten verfügt über Optionen können Sie ändern.

[!INCLUDE[name-sos](../includes/name-sos-short.md)] bietet zwei unterschiedliche Gültigkeitsbereiche für die Einstellungen an:

* **Benutzer** diese Einstellungen gelten global für eine beliebige Instanz von [!INCLUDE[name-sos](../includes/name-sos-short.md)] öffnen.
* **Arbeitsbereich** arbeitsbereichseinstellungen sind Einstellungen, die spezifisch für einen Ordner auf Ihrem Computer, und sind nur verfügbar, wenn der Ordner in der Randleiste Explorer geöffnet ist. In diesem Bereich definierte Einstellungen überschreiben den Benutzerbereich an.

## <a name="creating-user-and-workspace-settings"></a>Erstellen von Benutzer- und Arbeitsbereichseinstellungen

Der Menübefehl **Datei** > **Voreinstellungen** > **Einstellungen** (**Code**  >  **Voreinstellungen** > **Einstellungen** auf Mac) stellt den Einstiegspunkt zum Konfigurieren von Einstellungen für Benutzer und -Arbeitsbereich bereit. Sie werden eine Liste mit den Standardeinstellungen bereitgestellt. Kopieren Sie jede Einstellung, die Sie in den entsprechenden ändern möchten `settings.json` Datei. Die Registerkarten auf der rechten Seite können Sie schnell zwischen den Einstellungen für Benutzer und -Arbeitsbereich zu wechseln.

Sie können auch die Einstellungen für Benutzer und -Arbeitsbereich aus öffnen die **Befehlspalette** (**STRG + UMSCHALT + P**) mit **Einstellungen: Öffnen Sie die Benutzereinstellungen** und **Einstellungen: Öffnen Sie die Einstellungen für Systemarbeitsbereich** oder verwenden Sie die Tastenkombination (**STRG +,** ).

Das folgende Beispiel deaktiviert die Zeilennummern im Editor und Codezeilen automatisch eingezogen werden konfiguriert.

![Beispieleinstellungen](media/settings/sample-settings.png)

Änderungen an den Einstellungen werden neu geladen, indem [!INCLUDE[name-sos](../includes/name-sos-short.md)] nach geänderten `settings.json` -Datei wird gespeichert.

>**Hinweis**: Arbeitsbereichseinstellungen eignen sich für die Freigabe von projektspezifische Einstellungen innerhalb eines Teams.

## <a name="settings-file-locations"></a>Von Dateispeicherorten

Je nach Plattform befindet sich die Datei mit den Benutzer hier:

* **Windows** `%APPDATA%\azuredatastudio\User\settings.json`
* **Mac** `$HOME/Library/Application Support/azuredatastudio/User/settings.json`
* **Linux** `$HOME/.config/azuredatastudio/User/settings.json`

Die Arbeitsbereich-Einstellungsdatei befindet sich unter dem `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` -Ordner des Projekts.

## <a name="hot-exit"></a>"Hot" Beenden

Azure Data Studio speichert nicht gespeicherte Änderungen auf Dateien, beim Beenden des standardmäßig. Dies ist identisch mit den "Hot" Exit-Funktion in Visual Studio Code.

Standardmäßig ist die "Hot" Beenden aus. Aktivieren von "Hot" Beenden durch Bearbeiten der `files.hotExit` festlegen. Weitere Informationen finden Sie unter ["Hot" Beenden (in der Dokumentation zu Visual Studio Code)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Der Farbe

Zur Vereinfachung der Identifizierung von Verbindungen mit dem Sie arbeiten, haben die geöffneten Registerkarten in den Editor ihre Farbe festlegen, die die Farbe des der Servergruppe übereinstimmen, die die Verbindung zu gehört. Sind standardmäßig registerkartenfarben standardmäßig deaktiviert. Aktivieren der registerkartenfarben durch Bearbeiten der `sql.tabColorMode` festlegen.

## <a name="additional-resources"></a>Weitere Ressourcen

Da [!INCLUDE[name-sos](../includes/name-sos-short.md)] erbt die Benutzer- und Arbeitsbereich-Einstellungen, die von Visual Studio Code, der detaillierte Informationen zu Einstellungen, die die Funktion in ist der [Einstellungen für Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) Artikel.
