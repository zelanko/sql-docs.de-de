---
title: Verwenden von Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
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
ms.openlocfilehash: f52afcfdaa7de33d83d64a049f9a350f0463b4c6
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062346"
---
# <a name="using-reports"></a>Verwenden von Berichten
  Für jede Komponente wird ein separater Bericht generiert und bei Bedarf für jede Instanz, die der Analyse-Assistent des Upgrade Advisors auf einem Server analysiert. Der Bericht enthält Details über bekannte Probleme, die eine Aktualisierung beeinflussen. Er enthält zudem Links zu Informationen und Maßnahmenvorschlägen zur Behebung der identifizierten Probleme.  
  
> [!NOTE]  
>  Wenn der Berichts-Viewer des Upgrade Advisors keine Berichte im Standardverzeichnis für Berichte findet, können Sie einen Bericht mithilfe des Links **Bericht öffnen** aus einem anderen Verzeichnis laden.  
  
## <a name="viewing-reports"></a>Anzeigen von Berichten  
 Mit dem Berichts-Viewer des Upgrade Advisors zeigen Sie Berichte des Upgrade Advisors an. Klicken Sie zum Anzeigen von Berichten auf der Startseite des Upgrade Advisors auf Berichts-Viewer des Upgrade **Advisors starten**.  
  
 Nachdem Sie einen Bericht für einen Server geladen haben, können Sie eine Komponente wählen, deren Updateprobleme Sie anzeigen möchten. Sie können einen Filter aus dem Feld **Filtern nach** anwenden, um Folgendes anzuzeigen:  
  
-   Alle Probleme  
  
-   Alle Ugradeprobleme  
  
-   Probleme vor dem Upgrade  
  
-   Alle Migrationsprobleme  
  
-   Behobene Probleme  
  
-   Ungelöste Probleme  
  
 Wenn für den Bericht mehr als 20 Probleme vorliegen, können Sie zur nächsten oder vorherigen Gruppe von Problemen wechseln, indem Sie oben oder unten in der Liste Probleme auf **weiter 20** oder **vorherige 20** klicken.  
  
 Sie können bis zu fünf gespeicherte Berichte anzeigen, indem Sie im Dropdown-Listenfeld **Bericht** die Berichte auswählen. Die Berichte werden nach dem Zeitstempel für ihren Generierungszeitpunkt aufgeführt.  
  
## <a name="report-format"></a>Berichtformat  
 Der Berichts-Viewer zeigt Berichtsprobleme in drei Spalten an. Jedes Problem ist reduzierbar, damit Sie die Beschreibung ausblenden können, um nur die Schlüsselinformationen zu sehen.  
  
 Die erste Spalte ist die Spalte **Wichtigkeit** . Symbole geben die Wichtigkeit jedes Problems an: Ein roter Kreis mit einem X steht für blockierende oder wichtige Probleme und ein gelbes Dreieck mit einem Ausrufungszeichen für Warnungen oder Informationen. Die zweite Spalte gibt **an**, wann das Problem behoben werden muss. Sie können den Bericht entweder nach der **Wichtigkeit** oder **nach dem Zeitpunkt der Korrektur** der Spalte sortieren. In der dritten Spalte, **Beschreibung**, wird der Titel des Problems aufgelistet.  
  
 Sie können die Anzeige eines Problems erweitern, um zusätzliche Informationen, einen Link zu detaillierten Informationen über Abhilfe und einen Link zu Problemdetails einzublenden. Wenn Sie den Link anklicken, um detaillierte Informationen über das Problem zu erhalten, wird ein Hilfethema mit Informationen darüber und Anweisungen zur Behebung des Problems angezeigt. Nachdem Sie ein Problem behoben oder die Aktions Elemente verwaltet haben, können Sie die Probleme als abgeschlossen markieren, indem Sie das Kontrollkästchen **dieses Problem wurde gelöst** auswählen. Wenn Sie die aufgelösten Probleme aus der Liste der Upgradeprobleme entfernen möchten, klicken Sie auf **Aktualisieren**. Das Problem wird erst wieder angezeigt, wenn Sie den Analyse-Assistenten des Upgrade Advisors für dieselbe Komponente ausführen oder den Filter für **aufgelöste Probleme** aus der Option **Filtern nach** anwenden.  
  
## <a name="report-files"></a>Berichtsdateien  
 Der Analyse-Assistent des Upgrade Advisors erstellt Berichte im Verzeichnis My Documents \\ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Upgrade advisor\110\reports und erstellt ein Unterverzeichnis für jeden Server, den Sie analysieren. Die Berichtdateien sind XML-Dateien, die einer bestimmten Benennungskonvention entsprechen. Wenn Sie den Berichts-Viewer des Upgrade Advisors starten, werden die Berichtsdateien im Standardverzeichnis angezeigt. Wenn Sie Berichtsdateien in diesen Ordner kopieren, müssen sie der Benennungskonvention entsprechen, da der Berichts-Viewer sie sonst nicht automatisch anzeigt.  
  
 Wenn Sie die Informationen an andere Personen weitergeben möchten, können Sie ihnen den XML-Bericht senden. Wenn Sie eine andere Anwendung verwenden möchten, können Sie den Bericht alternativ in eine Datei im CSV-Format exportieren, anhand derer Sie eine Kalkulationstabelle, eine Textdatei oder eine E-Mail-Nachricht erstellen können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: Anzeigen eines Berichts des Upgrade Advisors](../../../2014/sql-server/install/how-to-view-an-upgrade-advisor-report.md)   
 [Vorgehensweise: Exportieren von Berichten](../../../2014/sql-server/install/how-to-export-reports.md)   
 [Vorgehensweise: Filtern von Berichten](../../../2014/sql-server/install/how-to-filter-reports.md)   
 [Beheben von Upgradeproblemen](../../../2014/sql-server/install/resolving-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neuen&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
