---
title: Verwenden von Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- displaying reports
- overriding reports
- Upgrade Advisor Report Viewer
- reports [Upgrade Advisor], about reports
- formatting reports
- resolved issues [Upgrade Advisor]
- distributing reports [Reporting Services]
- filtering reports [Reporting Services]
- removing report items
- viewing reports
- rerunning analysis
- information issues [Upgrade Advisor]
- deleting report items
- icons [Upgrade Advisor]
- Upgrade Advisor [SQL Server], reports
- sending reports
- blocking issues [Upgrade Advisor]
- sharing reports
- reports [Upgrade Advisor]
- SQL Server Upgrade Advisor, reports
- modifying reports
- distributing reports [Reporting Services], about report distribution
- warnings [Upgrade Advisor]
- analyzing system [Upgrade Advisor], reports
ms.assetid: 4a3cb94a-a7ac-4cec-94c7-db26fcf6d161
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb2537af2539854f0f66e3f6c39c3b6e5315ec6f
ms.sourcegitcommit: 46a2c0ffd0a6d996a3afd19a58d2a8f4b55f93de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59581925"
---
# <a name="using-reports"></a>Verwenden von Berichten
  Für jede Komponente wird ein separater Bericht generiert und bei Bedarf für jede Instanz, die der Analyse-Assistent des Upgrade Advisors auf einem Server analysiert. Der Bericht enthält Details über bekannte Probleme, die eine Aktualisierung beeinflussen. Er enthält zudem Links zu Informationen und Maßnahmenvorschlägen zur Behebung der identifizierten Probleme.  
  
> [!NOTE]  
>  Wenn der Upgrade Advisor-Berichts-Viewer keine Berichte im standardberichtsverzeichnis findet, können Sie einen Bericht aus einem anderen Verzeichnis laden, indem Sie mit der **geöffneten Bericht** Link.  
  
## <a name="viewing-reports"></a>Anzeigen von Berichten  
 Mit dem Berichts-Viewer des Upgrade Advisors zeigen Sie Berichte des Upgrade Advisors an. Klicken Sie zum Anzeigen von Berichten auf der Startseite des Upgrade Advisors **Viewer des Upgrade Advisors Bericht starten**.  
  
 Nachdem Sie einen Bericht für einen Server geladen haben, können Sie eine Komponente wählen, deren Updateprobleme Sie anzeigen möchten. Sie können einen Filter Anwenden der **Filtern nach** Feld, um Folgendes anzuzeigen:  
  
-   Alle Probleme  
  
-   Alle Ugradeprobleme  
  
-   Probleme vor dem Upgrade  
  
-   Alle Migrationsprobleme  
  
-   Behobene Probleme  
  
-   Ungelöste Probleme  
  
 Wenn der Bericht mehr als 20 Probleme enthält, können Sie wechseln zur nächsten oder vorherigen Gruppe von Problemen durch Klicken auf **nächsten 20** oder **vorherige 20** oben oder unteren Rand der Liste der Probleme.  
  
 Sie können bis zu fünf gespeicherte Berichte anzeigen, indem Sie die Berichte aus der **Bericht** im Dropdown Listenfeld. Die Berichte werden nach dem Zeitstempel für ihren Generierungszeitpunkt aufgeführt.  
  
## <a name="report-format"></a>Berichtsformat  
 Der Berichts-Viewer zeigt Berichtsprobleme in drei Spalten an. Jedes Problem ist reduzierbar, damit Sie die Beschreibung ausblenden können, um nur die Schlüsselinformationen zu sehen.  
  
 Die erste Spalte ist der **Wichtigkeit** Spalte. Symbole geben die Wichtigkeit jedes Problems an: Ein roter Kreis mit einem X steht für blockierende oder wichtige Probleme und ein gelbes Dreieck mit einem Ausrufungszeichen für Warnungen oder Informationen. Die zweite Spalte, **Zeitpunkt der Behebung**, gibt an, wenn das Problem behoben werden muss. Sie können den Bericht nach sortieren die **Wichtigkeit** oder **Zeitpunkt der Behebung** Spalte. Die dritte Spalte **Beschreibung**, wird der Titel des Problems.  
  
 Sie können die Anzeige eines Problems erweitern, um zusätzliche Informationen, einen Link zu detaillierten Informationen über Abhilfe und einen Link zu Problemdetails einzublenden. Wenn Sie den Link anklicken, um detaillierte Informationen über das Problem zu erhalten, wird ein Hilfethema mit Informationen darüber und Anweisungen zur Behebung des Problems angezeigt. Nachdem Sie ein Problem behoben haben, oder um Ihre maßnahmenelemente zu verwalten, Sie Probleme, die als abgeschlossen, durch Auswählen markieren können der **dieses Problem wurde behoben** Kontrollkästchen. Wenn Sie die gelösten Probleme aus der Liste der Upgradeprobleme entfernen möchten, klicken Sie auf **aktualisieren**. Das Problem wird nicht erneut angezeigt, bis Sie entweder den Analyse-Assistenten für dieselbe Komponente ausführen oder Anwenden der **behobene Probleme** aus dem Filtern der **Filtern nach** Option.  
  
## <a name="report-files"></a>Berichtsdateien  
 Analyse Assistent von Upgrade Advisor erzeugt Berichte im die eigene\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade Advisor\110\Reports-Verzeichnis und erstellt ein Unterverzeichnis für jeden Server, den Sie analysieren. Die Berichtdateien sind XML-Dateien, die einer bestimmten Benennungskonvention entsprechen. Wenn Sie den Berichts-Viewer des Upgrade Advisors starten, werden die Berichtsdateien im Standardverzeichnis angezeigt. Wenn Sie Berichtsdateien in diesen Ordner kopieren, müssen sie der Benennungskonvention entsprechen, da der Berichts-Viewer sie sonst nicht automatisch anzeigt.  
  
 Wenn Sie die Informationen an andere Personen weitergeben möchten, können Sie ihnen den XML-Bericht senden. Wenn Sie eine andere Anwendung verwenden möchten, können Sie den Bericht alternativ in eine Datei im CSV-Format exportieren, anhand derer Sie eine Kalkulationstabelle, eine Textdatei oder eine E-Mail-Nachricht erstellen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Zeigen Sie einen der Upgrade Advisor-Bericht](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)   
 [Vorgehensweise: Exportieren von Berichten](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Vorgehensweise: Filterberichte](../../../2014/sql-server/install/how-to-filter-reports.md)   
 [Beheben von Upgradeproblemen](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
