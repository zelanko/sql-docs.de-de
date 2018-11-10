---
title: Optionen (Umgebung – Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 80003c9bf964a094398256bf2f96a41fd2b3c579
ms.sourcegitcommit: af1d9fc4a50baf3df60488b4c630ce68f7e75ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2018
ms.locfileid: "51033027"
---
# <a name="options-environment-general-page"></a>Optionen (Seite „Umgebung“/„Allgemein“)
  Im Dialogfeld **Optionen** können Sie die Startaktionen, Optionen für die Fensterverwaltung und andere allgemeine Optionen für [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] konfigurieren. Klicken Sie im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Umgebung** , und klicken Sie anschließend auf **Allgemein**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Beim Start**  
 Wählen Sie die Aktion aus, die beim Start von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ausgeführt werden soll. Folgende Optionen sind verfügbar:  
  
-   Mit**Objekt-Explorer öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, und der Objekt-Explorer wird aufgerufen.  
  
-   Mit**Neues Abfragefenster öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, und der SQL-Abfrage-Editor wird aufgerufen.  
  
-   Mit**Objekt-Explorer und neue Abfrage öffnen** werden Sie aufgefordert, eine Verbindung anzugeben, und anschließend werden mit dieser Verbindung sowohl der Objekt-Explorer als auch der SQL-Abfrage-Editor geöffnet.  
  
-   Mit**Leere Umgebung öffnen** wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] aufgerufen, ohne dass das Fenster des SQL-Abfrage-Editors geöffnet oder eine Objekt-Explorer-Verbindung zu einem Server hergestellt wird.  
  
 **Systemobjekte im Objekt-Explorer ausblenden**  
 Aktivieren Sie dieses Kontrollkästchen, um Systemdatenbanken, Systemtabellen, Systemsichten und gespeicherte Systemprozeduren aus der Struktursicht des Objekt-Explorers zu entfernen. Systemfunktionen und Systemdatentypen werden nicht ausgeblendet. Diese Option betrifft nur Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , d. h., sie wirkt sich nicht auf Server aus, die im Objekt-Explorer bereits verbunden wurden.  
  
## <a name="environment-layout"></a>Umgebungslayout  
 Um zwischen den Umgebungsmodi MDI-Schnittstelle (Multiple Document Interface) und Dokumente im Registerformat wechseln zu können, müssen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] schließen und wieder öffnen.  
  
 **Dokumente im Registerformat**  
 Wählen Sie diese Option aus, um Dokumentfenster anzuzeigen, die in Editoren als Registerkarten zusammengefasst sind. Dokumentfenster im Registerformat werden verwendet, um mehrere offene Dokumente zu organisieren und problemlos zwischen den Dokumenten wechseln zu können.  
  
 **MDI-Umgebung**  
 Wählen Sie diese Option aus, um Dokumente in einer MDI-Umgebung zu öffnen. MDI-Dokumentfenster werden verwendet, um auf dem Bildschirm wieder Platz zu gewinnen, der andernfalls durch die Registerkarten der Dokumente im Registerformat belegt ist. Wenn Sie im MDI-Modus arbeiten und zwischen Dokumenten wechseln müssen, verwenden Sie die Tastenkombination STRG+TAB oder die im Menü **Fenster** verfügbaren Optionen zum Anordnen von Fenstern.  
  
## <a name="docked-tool-window-behavior"></a>Verhalten angedockter Toolfenster  
 **Die Schaltfläche 'Schließen' betrifft nur die aktive Registerkarte**  
 Wenn dieses Kontrollkästchen aktiviert wird, werden nicht alle Toolfenster im angedockten Satz, sondern nur das aktuell fokussierte Toolfenster geschlossen. Standardmäßig ist dieses Kontrollkästchen aktiviert.  
  
 **Die Schaltfläche zum automatischen Ausblenden betrifft nur die aktive Registerkarte**  
 Wenn dieses Kontrollkästchen aktiviert wird, werden nicht alle Toolfenster im angedockten Satz, sondern nur das aktuell fokussierte Toolfenster ausgeblendet. Standardmäßig ist dieses Kontrollkästchen deaktiviert.  
  
## <a name="display"></a>Anzeige  
 **Dateien in der Liste zuletzt verwendeter Dateien**  
 Passt die Anzahl zuletzt bearbeiteter Projekte und Dateien an, die im Menü **Datei** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Der Standardwert ist "4". Diese Option erleichtert das Abrufen kürzlich verwendeter Skriptprojekte und -dateien.  
  
  
