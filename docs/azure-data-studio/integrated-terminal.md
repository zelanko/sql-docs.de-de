---
title: Integriertes terminal
titleSuffix: Azure Data Studio
description: Lernen Sie das integrierte Terminal in Azure Data Studio aus.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: cfb635287a0baa2d3a9e8f59d9590c278cbf28b2
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66010952"
---
# <a name="integrated-terminal"></a>Integriertes Terminal

In [!INCLUDE[name-sos](../includes/name-sos-short.md)], Sie können ein integriertes Terminal öffnen, der anfänglich im Stammverzeichnis des Arbeitsbereichs ab. Dies kann praktisch sein, da Sie keine Windows wechseln, oder ändern den Status einer vorhandenen Terminal aus, um eine schnelle Befehlszeilenaufgabe ausführen.

So öffnen Sie das Terminal:

* Verwenden der **STRG +'** Tastenkombination mit Akzentzeichen.
* Verwenden der **Ansicht** | **integriertes Terminal** Menübefehl.
* Aus der **Befehlspalette** (**STRG + UMSCHALT + P**), verwenden Sie die **: ein/aus integrierten Terminal** Befehl.

![Terminaldienste](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> Sie können weiterhin eine externe Shell mit dem Explorer öffnen **in Eingabeaufforderung öffnen** Befehl (**in Terminal öffnen** unter Mac oder Linux), wenn Sie lieber außerhalb arbeiten [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="managing-multiple-terminals"></a>Verwalten von mehreren Terminals

Sie erstellen mehrere Terminals für unterschiedliche Speicherorte und problemlos zwischen diesen navigieren. Terminaldienste-Instanzen können hinzugefügt werden, indem Sie auf das plus-Symbol auf der oberen rechten Ecke der der **TERMINAL** panel oder durch Auslösen der **STRG + UMSCHALT +'** Befehl. Dies erstellt einen weiteren Eintrag in der Dropdownliste aus, die verwendet werden kann, um zwischen diesen wechseln.

![Mehrere Terminals](media/integrated-terminal/terminal-multiple-instances.png)

Entfernen Sie die Terminaldienste Hostinstanzen durch Drücken der Papierkorb können auf die Schaltfläche.

> [!TIP]
> Wenn Sie mehrere Terminals häufig verwenden, können Sie tastenzuordnungen für Hinzufügen der `focusNext`, `focusPrevious` und `kill` Befehle beschrieben, die in der [Tastenbindungen Abschnitt](#key-bindings) um Navigation zwischen ihnen die Verwendung der Tastatur zu ermöglichen.

## <a name="configuration"></a>Konfiguration

Die Shell verwendet standardmäßig `$SHELL` unter Linux und MacOS, PowerShell unter Windows 10 und cmd.exe in früheren Versionen von Windows. Dies können durch Festlegen von manuell überschrieben werden `terminal.integrated.shell.*` in [Einstellungen](settings.md). Argumente für die terminal-Shell unter Linux und MacOS verwenden, übergeben werden können die `terminal.integrated.shellArgs.*` Einstellungen.

### <a name="windows"></a>Windows

Ordnungsgemäße Konfiguration der Shell auf Windows, ist eine Frage, suchen die richtige ausführbare Datei, und aktualisieren die Einstellung. Im folgenden finden Sie eine Liste der allgemeinen ausführbare Shelldateien und ihren Standardspeicherorten an:

```json
// 64-bit cmd if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\cmd.exe"
// 64-bit PowerShell if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\WindowsPowerShell\\v1.0\\powershell.exe"
// Git Bash
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe"
// Bash on Ubuntu (on Windows)
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\bash.exe"
```

> [!NOTE]
> Als ein integriertes Terminal verwendet werden soll, muss die Shell ausführbare Datei eine Konsolenanwendung, damit `stdin/stdout/stderr` können umgeleitet werden.

> [!TIP]
> Die integrierte terminal-Shell ausgeführt wird, mit den Berechtigungen des [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Wenn Sie einen Shell-Befehl mit erhöhten Berechtigungen (Administrator) oder andere Berechtigungen ausführen müssen, können Plattform-Dienstprogramme wie z. B. `runas.exe` in einem Terminal aus.

### <a name="shell-arguments"></a>Shell-Argumente

Sie können Argumente an die Shell übergeben, wenn er gestartet wird.

Beispielsweise, um das Aktivieren von Bash als Anmeldeshell ausführen (führt `.bash_profile`), übergeben Sie die `-l` Argument (mit doppelten Anführungszeichen):

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>Der Terminalserver-Anzeigeeinstellungen

Sie können die integrierten terminal Schriftart und die Zeilenhöhe mit den folgenden Einstellungen anpassen:

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>Der Terminalserver Tastenbindungen

Die **anzeigen: Integriertes Terminal umschalten** Befehl gebunden ist **STRG +'** zum Umschalten der im integrierten terminal-Bereichs ein-und schnell.

Im folgenden sind die Tastenkombinationen, um schnell in das integrierte Terminal zu navigieren:

|Key|Befehl|  
|---|---|  
|**STRG +\`**|Integriertes Terminal anzeigen|  
|**STRG + UMSCHALT +\`**|Erstellen Sie neues terminal|  
|**STRG + nach-oben**|Bildlauf nach oben|  
|**STRG + nach-unten**|Scrollen Sie nach unten|  
|**Strg + Bild**|Seite nach oben Scrollen|  
|**Strg + Bild-ab**|Seite nach unten scrollen|  
|**STRG + POS1**|Bildlauf zur obersten Zeile|  
|**STRG + Ende**|Führen Sie einen Bildlauf nach unten|  
|**STRG + K**|Deaktivieren Sie das terminal|  

Andere Terminalbefehle stehen und an die bevorzugten Tastenkombinationen gebunden werden können.

Die Überladungen sind:

* `workbench.action.terminal.focus`: Das Terminal zu konzentrieren. Dies ist wie ein/aus, aber der Schwerpunkt liegt das Terminal nicht ausgeblendet, wenn es sichtbar ist.
* `workbench.action.terminal.focusNext`: Geht es um die nächste Terminaldienste-Instanz.
* `workbench.action.terminal.focusPrevious`: Liegt der Schwerpunkt der vorherigen Terminaldienste-Instanz.
* `workbench.action.terminal.kill`: Entfernen Sie die aktuelle Instanz des Terminalserver.
* `workbench.action.terminal.runSelectedText`: Führen Sie den markierten Text in der terminal-Instanz.
* `workbench.action.terminal.runActiveFile`: Führen Sie die aktive Datei in der terminal-Instanz.

### <a name="run-selected-text"></a>Ausführen von ausgewähltem Text

Verwenden der `runSelectedText` Befehl, markieren Sie Text in einem Editor, und führen Sie den Befehl **Terminal: Ausführen von ausgewähltem Text in aktiven Terminal** über die **Befehlspalette** (**STRG + UMSCHALT + P**). Das Terminal wird versucht, den markierten Text ausführen:

![Ausführen von ausgewähltem text](media/integrated-terminal/terminal_run_selected.png)

Wenn kein Text im aktiven Editor ausgewählt ist, wird die Zeile, der der Cursor befindet im Terminal ausgeführt.

### <a name="copy--paste"></a>Kopieren und einfügen

Die tastenzuordnungen zum Kopieren und Einfügen führen Sie die Plattform-Standards:

* Linux: **STRG + UMSCHALT + C** und **STRG + UMSCHALT + V**
* Mac: **Cmd + C** und **Cmd + V**
* Windows: **STRG + C** und **STRG + V**

### <a name="find"></a>Suchen

Das integrierte Terminal hat grundlegende Suchfunktionen, die mit ausgelöst werden, kann **STRG + F**.

Wenn Sie möchten **STRG + F** um mit der Shell nicht das Widget "Suchen" unter Linux und Windows gestartet fortzufahren, müssen Sie die tastenzuordnung entfernen wie folgt:

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>Benennen Sie terminalsitzungen

Integrierte terminalsitzungen können nun umbenannt werden mithilfe der **Terminal: Benennen Sie** (`workbench.action.terminal.rename`) Befehl. Der neue Name wird in der terminal Auswahl-Dropdownliste angezeigt.

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>Erzwingen die Tastenkombinationen, um über das Terminal zu übergeben.

Während der Fokus im integrierten Terminal ist, funktionieren viele tastenzuordnungen nicht daran, dass die Tastatureingaben zu übergeben und von Terminal selbst genutzt werden. Die `terminal.integrated.commandsToSkipShell` Einstellung kann verwendet werden, um dieses Problem umgehen. Sie enthält ein Array von Befehlsnamen, deren tastenzuordnungen Verarbeitung von der Shell zu überspringen und stattdessen vom verarbeitet werden, die [!INCLUDE[name-sos](../includes/name-sos-short.md)] Bindungssystem Schlüssel. Standardmäßig schließt dies alle Terminalserver tastenzuordnungen zusätzlich zu einer auf einige häufig verwendete tastenzuordnungen.

