---
title: Verwenden von Berichten | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d71bcb0f6c695f540f1d38b1418c2c3282afea58
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047750"
---
# <a name="using-reports"></a>Verwenden von Berichten
  Für jede Komponente wird ein separater Bericht generiert und bei Bedarf für jede Instanz, die der Analyse-Assistent des Upgrade Advisors auf einem Server analysiert. Der Bericht enthält Details über bekannte Probleme, die eine Aktualisierung beeinflussen. Er enthält zudem Links zu Informationen und Maßnahmenvorschlägen zur Behebung der identifizierten Probleme.  
  
> [!NOTE]  
>  Wenn der Upgrade Advisor-Berichts-Viewer keine Berichte im standardberichtsverzeichnis findet, können Sie einen Bericht aus einem anderen Verzeichnis laden, indem Sie mit der **geöffneten Bericht** Link.  
  
## <a name="viewing-reports"></a>Anzeigen von Berichten  
 Mit dem Berichts-Viewer des Upgrade Advisors zeigen Sie Berichte des Upgrade Advisors an. Um Berichte, auf der Startseite des Upgrade Advisors anzuzeigen, klicken Sie auf **Viewer des Upgrade Advisors Bericht starten**.  
  
 Nachdem Sie einen Bericht für einen Server geladen haben, können Sie eine Komponente wählen, deren Updateprobleme Sie anzeigen möchten. Sie können einen Filter aus Anwenden der **Filtern nach** Feld, um Folgendes anzuzeigen:  
  
-   Alle Probleme  
  
-   Alle Ugradeprobleme  
  
-   Probleme vor dem Upgrade  
  
-   Alle Migrationsprobleme  
  
-   Behobene Probleme  
  
-   Ungelöste Probleme  
  
 Wenn der Bericht mehr als 20 Probleme enthält, können Sie wechseln zur nächsten oder vorherigen Gruppe von Problemen durch Klicken auf **nächste 20** oder **vorherige 20** die oberen oder unteren Rand der Liste der Probleme.  
  
 Sie können bis zu fünf gespeicherte Berichte anzeigen, indem Sie die Berichte auswählen der **Bericht** Dropdown Listenfeld aus. Die Berichte werden nach dem Zeitstempel für ihren Generierungszeitpunkt aufgeführt.  
  
## <a name="report-format"></a>Berichtsformat  
 Der Berichts-Viewer zeigt Berichtsprobleme in drei Spalten an. Jedes Problem ist reduzierbar, damit Sie die Beschreibung ausblenden können, um nur die Schlüsselinformationen zu sehen.  
  
 Die erste Spalte ist der **Wichtigkeit** Spalte. Symbole geben die Wichtigkeit jedes Problems an: Ein roter Kreis mit einem X steht für blockierende oder wichtige Probleme und ein gelbes Dreieck mit einem Ausrufungszeichen für Warnungen oder Informationen. Die zweite Spalte **Zeitpunkt der Behebung**, gibt an, wenn das Problem behoben werden muss. Sie können den Bericht nach Sortieren der **Wichtigkeit** oder **Zeitpunkt der Behebung** Spalte. Die dritte Spalte **Beschreibung**, wird der Titel des Problems.  
  
 Sie können die Anzeige eines Problems erweitern, um zusätzliche Informationen, einen Link zu detaillierten Informationen über Abhilfe und einen Link zu Problemdetails einzublenden. Wenn Sie den Link anklicken, um detaillierte Informationen über das Problem zu erhalten, wird ein Hilfethema mit Informationen darüber und Anweisungen zur Behebung des Problems angezeigt. Nachdem Sie ein Problem behoben haben, oder um Ihre maßnahmenelemente zu verwalten, Sie Probleme als abgeschlossen, durch Auswählen markieren können der **dieses Problem wurde behoben** Kontrollkästchen. Wenn Sie die gelösten Probleme aus der Liste der Upgradeprobleme entfernen möchten, klicken Sie auf **aktualisieren**. Das Problem wird nicht erneut angezeigt, bis Sie die Upgrade Advisor-Analyse-Assistenten für dieselbe Komponente ausführen oder Anwenden der **behobene Probleme** aus dem Filtern der **Filtern nach** Option.  
  
## <a name="report-files"></a>Berichtsdateien  
 Der Analyse-Assistenten Upgrade Advisors erzeugt Berichte im Meine Dokumente\\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Directory Upgrade Advisor\110\Reports und erzeugt ein Unterverzeichnis für jeden Server, den Sie analysieren. Die Berichtdateien sind XML-Dateien, die einer bestimmten Benennungskonvention entsprechen. Wenn Sie den Berichts-Viewer des Upgrade Advisors starten, werden die Berichtsdateien im Standardverzeichnis angezeigt. Wenn Sie Berichtsdateien in diesen Ordner kopieren, müssen sie der Benennungskonvention entsprechen, da der Berichts-Viewer sie sonst nicht automatisch anzeigt.  
  
 Wenn Sie die Informationen an andere Personen weitergeben möchten, können Sie ihnen den XML-Bericht senden. Wenn Sie eine andere Anwendung verwenden möchten, können Sie den Bericht alternativ in eine Datei im CSV-Format exportieren, anhand derer Sie eine Kalkulationstabelle, eine Textdatei oder eine E-Mail-Nachricht erstellen können.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anzeigen eines Berichts der Upgrade Advisor](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)   
 [Vorgehensweise: Exportieren von Berichten](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Vorgehensweise: Filtern von Berichten](../../../2014/sql-server/install/how-to-filter-reports.md)   
 [Beheben von Upgradeproblemen](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
