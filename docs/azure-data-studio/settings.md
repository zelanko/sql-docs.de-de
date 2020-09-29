---
title: Benutzer- und Arbeitsbereichseinstellungen
description: Erfahren Sie, wie Sie die Einstellungen zum Anpassen des Editors, der Benutzeroberfläche und des funktionalen Verhaltens von Azure Data Studio entsprechend Ihrer Vorlieben verwenden.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 06e9efa72ef82d8335db4b7ec6b8941c95501790
ms.sourcegitcommit: 63aef5a96905f0b026322abc9ccb862ee497eebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91364181"
---
# <a name="modify-user-and-workspace-settings"></a>Ändern von Benutzer- und Arbeitsbereichseinstellungen

Es ist einfach, Azure Data Studio über die Einstellungen nach Ihren Wünschen zu konfigurieren. Nahezu jeder Teil des Editors von Azure Data Studio, Benutzeroberfläche und funktionales Verhalten bieten Optionen, die Sie ändern können.

Azure Data Studio bietet zwei unterschiedliche Bereiche für Einstellungen:

* **Benutzer**: Diese Einstellungen gelten global für jede Instanz von Azure Data Studio, die Sie öffnen.
* **Arbeitsbereich**: Arbeitsbereichseinstellungen sind für einen Ordner spezifische Einstellungen auf Ihrem Computer und nur verfügbar, wenn der Ordner in der Explorer-Randleiste geöffnet ist. Für diesen Bereich definierte Einstellungen überschreiben den Benutzerbereich.

## <a name="creating-user-and-workspace-settings"></a>Erstellen von Benutzer- und Arbeitsbereichseinstellungen

Der Menübefehl **Datei** > **Einstellungen** > **Einstellungen**(**Code** > **Einstellungen** > **Einstellungen** auf Mac) stellt den Einstiegspunkt zum Konfigurieren von Benutzer- und Arbeitsbereichseinstellungen bereit. Eine Liste der Standardeinstellungen wird angezeigt. Kopieren Sie jede Einstellung, die Sie ändern möchten, in die entsprechende `settings.json`-Datei. Mit den Registerkarten auf der rechten Seite können Sie schnell zwischen den Einstellungsdateien für Benutzer- und Arbeitsbereich wechseln.

Sie können die Benutzer- und Arbeitsbereichseinstellungen auch über die **Befehlspalette** (**STRG+UMSCHALT+P**) mit **Einstellungen: Benutzereinstellungen öffnen** und **Einstellungen: Arbeitsbereichseinstellungen öffnen** aufrufen oder die Tastenkombination (**STRG+,** ) verwenden.

Im folgenden Beispiel werden die Zeilennummern im Editor deaktiviert und Codezeilen so konfiguriert, dass sie automatisch eingezogen werden.

![Beispieleinstellungen](media/settings/sample-settings.png)

Änderungen an den Einstellungen werden von Azure Data Studio neu geladen, nachdem die geänderte `settings.json`-Datei gespeichert wurde.

> [!NOTE]
> Arbeitsbereichseinstellungen sind nützlich für die gemeinsame Nutzung von projektspezifischen Einstellungen in einem Team.

## <a name="settings-file-locations"></a>Speicherorte für Einstellungsdateien

Abhängig von Ihrer Plattform befindet sich die Datei mit den Benutzereinstellungen hier:

* **Windows** `%APPDATA%\azuredatastudio\User\settings.json`
* **Mac** `$HOME/Library/Application Support/azuredatastudio/User/settings.json`
* **Linux** `$HOME/.config/azuredatastudio/User/settings.json`

Die Datei mit den Arbeitsbereichseinstellungen befindet sich unter dem `.Azure Data Studio`-Ordner in Ihrem Projekt.

## <a name="hot-exit"></a>Hot-Exit

Azure Data Studio speichert nicht gespeicherte Änderungen an Dateien, wenn Sie die Anwendung standardmäßig beenden. In Visual Studio Code entspricht dies dem Feature „Hot Exit“.

Standardmäßig ist der Hot Exit deaktiviert. Aktivieren Sie Hot-Exit, indem Sie die `files.hotExit`-Einstellung bearbeiten. Weitere Informationen finden Sie unter [Hot-Exit (in der Visual Studio Code-Dokumentation)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).

## <a name="tab-color"></a>Registerkartenfarbe

Damit Sie mühelos erkennen können, mit welchen Verbindungen Sie arbeiten, können Sie die Farben der geöffneten Registerkarten im Editor so festlegen, dass sie mit der Farbe der Servergruppe übereinstimmen, zu der die Verbindung gehört. Standardmäßig sind Registerkartenfarben deaktiviert. Aktivieren Sie Registerkartenfarben, indem Sie die `sql.tabColorMode`-Einstellung bearbeiten.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

Da Azure Data Studio die Funktionalität von Benutzer- und Arbeitsbereichseinstellungen von Visual Studio Code erbt, finden Sie ausführliche Informationen zu den Einstellungen im Artikel [Benutzer- und Arbeitsbereichseinstellungen](https://code.visualstudio.com/docs/getstarted/settings).
