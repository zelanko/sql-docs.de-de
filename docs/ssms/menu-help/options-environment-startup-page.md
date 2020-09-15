---
description: Optionen (Umgebung – Startseite)
title: " SQL Server-Optionsseite – Umgebung – Start"
ms.date: 11/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 85d0b99d0929f7fb7ae642c5b0673fdc7b9b185b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88417906"
---
# <a name="options-environment---startup-page"></a>Optionen (Umgebung – Startseite)

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Im Dialogfeld **Optionen** können Sie die Startaktionen, Optionen für die Fensterverwaltung und andere allgemeine Optionen für [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] konfigurieren. Klicken Sie im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Umgebung**, und klicken Sie dann auf **Start**.

## <a name="ui-element-list"></a>Liste der Benutzeroberflächenelemente

**Beim Start**

Wählen Sie die Aktion aus, die [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] beim Start ausführen soll. Die Optionen sind:

- Mit**Objekt-Explorer öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, und der Objekt-Explorer wird aufgerufen.

- Mit**Neues Abfragefenster öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, und der SQL-Abfrage-Editor wird aufgerufen.

- Mit **Objekt-Explorer und Abfragefenster öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, anschließend werden sowohl der Objekt-Explorer sowie der SQL-Abfrage-Editor geöffnet.

- **Objekt-Explorer und Aktivitätsmonitor öffnen**.

- Mit**Leere Umgebung öffnen** wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aufgerufen, ohne dass das Fenster des SQL-Abfrage-Editors geöffnet oder eine Objekt-Explorer-Verbindung zu einem Server hergestellt wird.

**Systemobjekte im Objekt-Explorer ausblenden**

Aktivieren Sie dieses Kontrollkästchen, um Systemdatenbanken, Systemtabellen, Systemsichten und gespeicherte Systemprozeduren aus der Struktursicht des Objekt-Explorers zu entfernen. Systemfunktionen und Systemdatentypen werden nicht ausgeblendet. Diese Option betrifft nur Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , d. h., sie wirkt sich nicht auf Server aus, die im Objekt-Explorer bereits verbunden wurden.

## <a name="see-also"></a>Weitere Informationen

- [Optionen (Dialogfelder, F1-Hilfe)](options-dialog-boxes-f1-help.md)
- [Optionen (Umgebung – Seite „Allgemein“)](options-environment-general-page.md)
