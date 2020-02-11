---
title: Optionen (Umgebung, Seite "Allgemein") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9a96b77c3f1243bc3d95cf38242463724348134b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68188500"
---
# <a name="options-environment-general-page"></a>Optionen (Seite „Umgebung“/„Allgemein“)
  Verwenden Sie das Dialogfeld **Optionen** , [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] um Start Aktionen, allgemeine Fenster Verwaltungs Optionen und andere allgemeine Einstellungen zu konfigurieren. Klicken Sie im Menü **Extras** auf **Optionen**, erweitern Sie den Ordner **Umgebung** , und klicken Sie anschließend auf **Allgemein**.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Beim Start**  
 Wählen Sie die Aktion aus, die beim Start von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ausgeführt werden soll. Die Optionen sind:  
  
-   **Öffnen Sie Objekt-Explorer** Eingabeaufforderung für eine Verbindung, und öffnen Sie dann Objekt-Explorer.  
  
-   **Öffnen Sie ein neues Abfragefenster** , und öffnen Sie dann den SQL-Abfrage-Editor.  
  
-   **Öffnen Sie Objekt-Explorer und neue Abfrage** fordert eine Verbindung an, und öffnet dann sowohl Objekt-Explorer als auch den SQL-Abfrage-Editor mit dieser Verbindung.  
  
-   **Leere Umgebung öffnen** wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ohne ein SQL-Abfrage-Editor-Fenster geöffnet, ohne dass Objekt-Explorer mit einem Server verbunden werden.  
  
 **Systemobjekte in Objekt-Explorer ausblenden**  
 Aktivieren Sie dieses Kontrollkästchen, um Systemdatenbanken, Systemtabellen, Systemsichten und gespeicherte Systemprozeduren aus der Struktursicht des Objekt-Explorers zu entfernen. Systemfunktionen und Systemdatentypen werden nicht ausgeblendet. Diese Option betrifft nur Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , d. h., sie wirkt sich nicht auf Server aus, die im Objekt-Explorer bereits verbunden wurden.  
  
## <a name="environment-layout"></a>Umgebungslayout  
 Um zwischen den Umgebungsmodi MDI-Schnittstelle (Multiple Document Interface) und Dokumente im Registerformat wechseln zu können, müssen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] schließen und wieder öffnen.  
  
 **Dokumente im Register Format**  
 Wählen Sie diese Option aus, um Dokumentfenster anzuzeigen, die in Editoren als Registerkarten zusammengefasst sind. Dokumentfenster im Registerformat werden verwendet, um mehrere offene Dokumente zu organisieren und problemlos zwischen den Dokumenten wechseln zu können.  
  
 **MDI-Umgebung**  
 Wählen Sie diese Option aus, um Dokumente in einer MDI-Umgebung zu öffnen. MDI-Dokumentfenster werden verwendet, um auf dem Bildschirm wieder Platz zu gewinnen, der andernfalls durch die Registerkarten der Dokumente im Registerformat belegt ist. Wenn Sie im MDI-Modus arbeiten und zwischen Dokumenten wechseln müssen, verwenden Sie die Tastenkombination STRG+TAB oder die im Menü **Fenster** verfügbaren Optionen zum Anordnen von Fenstern.  
  
## <a name="docked-tool-window-behavior"></a>Verhalten angedockter Toolfenster  
 **Schaltfläche "Schließen" betrifft nur aktive Registerkarte**  
 Wenn dieses Kontrollkästchen aktiviert wird, werden nicht alle Toolfenster im angedockten Satz, sondern nur das aktuell fokussierte Toolfenster geschlossen. Standardmäßig ist dieses Kontrollkästchen aktiviert.  
  
 **Schaltfläche "automatisch im Hintergrund" betrifft nur aktive Registerkarten**  
 Wenn dieses Kontrollkästchen aktiviert wird, werden nicht alle Toolfenster im angedockten Satz, sondern nur das aktuell fokussierte Toolfenster ausgeblendet. Standardmäßig ist dieses Kontrollkästchen deaktiviert.  
  
## <a name="display"></a>Anzeige  
 **N Dateien in der Liste zuletzt verwendeter Dateien anzeigen**  
 Passt die Anzahl zuletzt bearbeiteter Projekte und Dateien an, die im Menü **Datei** angezeigt werden. Geben Sie eine Zahl zwischen 1 und 24 ein. Der Standardwert ist 4. Diese Option erleichtert das Abrufen kürzlich verwendeter Skriptprojekte und -dateien.  
  
  
