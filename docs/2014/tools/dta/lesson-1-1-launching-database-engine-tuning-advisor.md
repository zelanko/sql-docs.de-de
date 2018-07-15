---
title: Starten des Datenbankoptimierungsratgebers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tuning databases [SQL Server]
- Database Engine Tuning Advisor [SQL Server], starting
ms.assetid: 4abc0e10-96fd-4e46-93d6-d7ee03eec844
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed2001ff159681f78a9287be8e1931ee5d432948
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37282286"
---
# <a name="launching-database-engine-tuning-advisor"></a>Starten des Datenbankoptimierungsratgebers
  Zunächst öffnen Sie die grafische Benutzeroberfläche des Datenbankoptimierungsratgebers (Graphical User Interface, GUI). Bei der ersten Verwendung muss ein Mitglied der festen Serverrolle **sysadmin** den Datenbankoptimierungsratgeber starten, um die Anwendung zu initialisieren. Nach der Initialisierung können Mitglieder der festen Datenbankrolle **db_owner** mit dem Datenbankoptimierungsratgeber eigene Datenbanken optimieren. Weitere Informationen zum Initialisieren des Datenbankoptimierungsratgebers finden Sie unter [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/database-engine-tuning-advisor.md).  
  
### <a name="open-the-database-engine-tuning-advisor-gui"></a>Öffnen der grafischen Benutzeroberfläche des Datenbankoptimierungsratgebers  
  
1.  Zeigen Sie im Windows-Menü **Start** auf **Alle Programme**und dann auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]und **Leistungstools**, und klicken Sie anschließend auf **Datenbankoptimierungsratgeber**.  
  
2.  Überprüfen Sie im Dialogfeld **Verbindung mit dem Server herstellen** die Standardeinstellungen, und klicken Sie dann auf **Verbinden**.  
  
 Standardmäßig wird der Datenbankoptimierungsratgeber mit der in der folgenden Abbildung gezeigten Konfiguration geöffnet:  
  
 ![Database Engine Tuning Advisor-Standardfenster](media/defaultdtagui.gif "Standardfenster des Datenbankoptimierungsratgebers")  
  
> [!NOTE]  
>  Auf der Registerkarte und im Feld **Sitzungsname** werden der Name des Computers und der Instanz angezeigt, mit der Sie verbunden sind. Außerdem werden das aktuelle Datum und die aktuelle Uhrzeit auf der Registerkarte und im Feld angezeigt.  
  
 Beim ersten Öffnen der grafischen Benutzeroberfläche des Datenbankoptimierungsratgebers werden zwei Hauptbereiche angezeigt.  
  
-   Im linken Bereich befindet sich der Sitzungsmonitor, in dem alle Optimierungssitzungen aufgelistet werden, die auf dieser [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz durchgeführt wurden. Wenn Sie den Datenbankoptimierungsratgeber öffnen, wird oben im Anzeigebereich eine neue Sitzung angezeigt. Sie können diese Sitzung im daneben liegenden Bereich benennen. Zu Beginn wird nur eine Standardsitzung aufgeführt. Dies ist die Standardsitzung, die der Datenbankoptimierungsratgeber automatisch für Sie anlegt. Wenn Sie Datenbanken optimiert haben, werden alle Optimierungssitzungen für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz, mit der Sie verbunden sind, unter der neuen Sitzung aufgelistet. Wenn Sie mit der rechten Maustaste auf eine Optimierungssitzung klicken, können Sie diese umbenennen, schließen, löschen oder klonen. Wenn Sie mit der rechten Maustaste auf die Liste klicken, können Sie die Sitzungen nach Name, Status oder Erstellungszeit sortieren oder aber eine neue Sitzung anlegen. Im unteren Abschnitt des Bereichs werden Detailinformationen zur ausgewählten Optimierungssitzung angezeigt. Mit der Schaltfläche **Nach Kategorien** können Sie festlegen, dass die Details nach Kategorien angezeigt werden sollen. Mit der Schaltfläche **Alphabetisch** können Sie sie in einer alphabetisch sortierten Liste anzeigen. Sie können den Sitzungsmonitor auch ausblenden, indem Sie den rechten Rand des Bereichs auf die linke Seite des Fensters ziehen. Wenn Sie ihn wieder anzeigen möchten, ziehen Sie den Bereichsrand wieder nach rechts. Der Sitzungsmonitor ermöglicht das Anzeigen früherer Optimierungssitzungen, die Sie verwenden können, um neue Sitzungen mit ähnlichen Definitionen zu erstellen. Sie können den Sitzungsmonitor auch einsetzen, um Optimierungsempfehlungen auszuwerten. Weitere Informationen finden Sie unter [Anzeigen und Verwenden der Ausgabe des Datenbankoptimierungsratgebers](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md). Mit der Schaltfläche **Zurück** des Browsers kehren Sie zu diesem Tutorial zurück.  
  
-   Der rechte Bereich umfasst die Registerkarten **Allgemein** und **Optimierungsoptionen** . Hier können Sie die Sitzung im Datenbankoptimierungsratgeber definieren. Auf der Registerkarte **Allgemein** können Sie den Namen für Ihre Optimierungssitzung eingeben, die Arbeitsauslastungsdatei oder Tabelle angeben, die verwendet werden soll, und die Datenbanken und Tabellen auswählen, die in dieser Sitzung optimiert werden sollen. Die Arbeitsauslastung besteht aus einer Reihe von [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen, die für eine oder mehrere Datenbanken ausgeführt werden, die Sie optimieren möchten. Beim Optimieren von Datenbanken werden im Datenbankoptimierungsratgeber Ablaufverfolgungsdateien, Ablaufverfolgungstabellen, [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skripts oder XML-Dateien als Eingabe für die Arbeitsauslastung verwendet. Auf der Registerkarte **Optimierungsoptionen** können Sie die physischen Entwurfsstrukturen (Indizes oder indizierte Sichten) und die Partitionierungsstrategie auswählen, die vom Datenbankoptimierungsratgeber bei der Analyse berücksichtigt werden sollen. Auf dieser Registerkarte können Sie auch angeben, wie lange die Optimierung einer Arbeitsauslastung durch den Datenbankoptimierungsratgeber maximal dauern soll. Standardmäßig dauert das Optimieren einer Arbeitsauslastung durch den Datenbankoptimierungsratgeber maximal eine Stunde.  
  
> [!NOTE]  
>  Der Datenbankoptimierungsratgeber kann auch eine XML-Datei als Eingabe annehmen, wenn ein [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript aus dem Abfrage-Editor von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] importiert wird. Weitere Informationen finden Sie im Abschnitt zum Datenbankoptimierungsratgeber im Abfrage-Editor von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] in [Starten und Verwenden des Datenbankoptimierungsratgebers](../../relational-databases/performance/database-engine-tuning-advisor.md).  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Festlegen von Optionen und Layout](lesson-1-2-setting-tool-options-and-layout.md)  
  
  
