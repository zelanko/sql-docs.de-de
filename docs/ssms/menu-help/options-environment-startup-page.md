---
title: " SQL Server-Optionsseite – Umgebung – Start | Microsoft-Dokumentation"
ms.date: 11/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 80fff1e8db1fb9dabe6ed12d425bd844e954dac9
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68257273"
---
# <a name="options-environment---startup-page"></a>Optionen (Umgebung – Startseite)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Im Dialogfeld **Optionen** können Sie die Startaktionen, Optionen für die Fensterverwaltung und andere allgemeine Optionen für [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] konfigurieren. Klicken Sie im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Umgebung**, und klicken Sie dann auf **Start**.

## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente

**Beim Start**

Wählen Sie die Aktion aus, die [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] beim Start ausführen soll. Folgende Optionen sind verfügbar:

- Mit**Objekt-Explorer öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, und der Objekt-Explorer wird aufgerufen.

- Mit**Neues Abfragefenster öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, und der SQL-Abfrage-Editor wird aufgerufen.

- Mit **Objekt-Explorer und Abfragefenster öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, anschließend werden sowohl der Objekt-Explorer sowie der SQL-Abfrage-Editor geöffnet.

- **Objekt-Explorer und Aktivitätsmonitor öffnen**.

- Mit**Leere Umgebung öffnen** wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aufgerufen, ohne dass das Fenster des SQL-Abfrage-Editors geöffnet oder eine Objekt-Explorer-Verbindung zu einem Server hergestellt wird.

**Systemobjekte im Objekt-Explorer ausblenden**

Aktivieren Sie dieses Kontrollkästchen, um Systemdatenbanken, Systemtabellen, Systemsichten und gespeicherte Systemprozeduren aus der Struktursicht des Objekt-Explorers zu entfernen. Systemfunktionen und Systemdatentypen werden nicht ausgeblendet. Diese Option betrifft nur Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , d. h., sie wirkt sich nicht auf Server aus, die im Objekt-Explorer bereits verbunden wurden.

## <a name="see-also"></a>Siehe auch

- [Optionen (Dialogfelder, F1-Hilfe)](options-dialog-boxes-f1-help.md)
- [Optionen (Umgebung – Seite „Allgemein“)](options-environment-general-page.md)
