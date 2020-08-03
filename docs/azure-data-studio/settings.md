---
title: Benutzer- und Arbeitsbereichseinstellungen
description: Erfahren Sie, wie Sie die Einstellungen zum Anpassen des Editors, der Benutzeroberfläche und des funktionalen Verhaltens von Azure Data Studio entsprechend Ihrer Vorlieben verwenden.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: azure-data-studio
ms.technology: ''
ms.reviewer: alayu, maghan, sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 71f1f27bc58f64d3a1bcf8bcc3f8e96594e2e771
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411206"
---
# <a name="modify-user-and-workspace-settings"></a>Ändern von Benutzer- und Arbeitsbereichseinstellungen

Es ist einfach, Azure Data Studio mittels Einstellungen nach Ihren Wünschen zu konfigurieren. Nahezu jeder Teil des Editors von Azure Data Studio, Benutzeroberfläche und funktionales Verhalten bieten Optionen, die Sie ändern können.

Azure Data Studio bietet zwei unterschiedliche Bereiche für Einstellungen:

* **Benutzer** Diese Einstellungen gelten global für jede Instanz von Azure Data Studio, die Sie öffnen.
* **Arbeitsbereich** Arbeitsbereichseinstellungen sind spezifische Einstellungen für einen Ordner auf Ihrem Computer und nur verfügbar, wenn der Ordner in der Explorer-Randleiste geöffnet ist. Für diesen Bereich definierte Einstellungen überschreiben den Benutzerbereich.

## <a name="creating-user-and-workspace-settings"></a>Erstellen von Benutzer- und Arbeitsbereichseinstellungen

Der Menübefehl **Datei** > **Einstellungen** > **Einstellungen**(**Code** > **Einstellungen** > **Einstellungen** auf Mac) stellt den Einstiegspunkt zum Konfigurieren von Benutzer- und Arbeitsbereichseinstellungen bereit. Ihnen wird eine Liste der Standardeinstellungen bereitgestellt. Kopieren Sie jede Einstellung, die Sie ändern möchten, in die entsprechende `settings.json`-Datei. Mit den Registerkarten auf der rechten Seite können Sie schnell zwischen den Einstellungsdateien für Benutzer- und Arbeitsbereich wechseln.

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

Azure Data Studio speichert nicht gespeicherte Änderungen an Dateien, wenn Sie die Anwendung standardmäßig beenden. Dies entspricht der Hot-Exit-Funktion in Visual Studio Code.

Standardmäßig ist Hot-Exit deaktiviert. Aktivieren Sie Hot-Exit, indem Sie die `files.hotExit`-Einstellung bearbeiten. Weitere Informationen finden Sie unter [Hot-Exit (in der Visual Studio Code-Dokumentation)](https://code.visualstudio.com/docs/editor/codebasics#_hot-exit).


## <a name="tab-color"></a>Registerkartenfarbe

Um mühelos zu erkennen, mit welchen Verbindungen Sie arbeiten, können Sie die Farben der geöffneten Registerkarten im Editor so festlegen, dass sie mit der Farbe der Servergruppe übereinstimmen, zu denen die Verbindung gehört. Standardmäßig sind Registerkartenfarben deaktiviert. Aktivieren Sie Registerkartenfarben, indem Sie die `sql.tabColorMode`-Einstellung bearbeiten.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

Da Azure Data Studio die Funktionalität von Benutzer- und Arbeitsbereichseinstellungen von Visual Studio Code erbt, finden Sie ausführliche Informationen zu den Einstellungen im Artikel [Benutzer- und Arbeitsbereichseinstellungen](https://code.visualstudio.com/docs/getstarted/settings).
