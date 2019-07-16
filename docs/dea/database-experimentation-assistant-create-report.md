---
title: Erstellen von Analyseberichten im Datenbank-experimentieren-Assistenten für SQL Server-upgrades
description: Erstellen von Analyseberichten in Datenbankexperimente
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: d53d8734e0c01fa2056b9d560f3bc65b7f64d9a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058974"
---
# <a name="create-analysis-reports-in-database-experimentation-assistant"></a>Erstellen von Analyseberichten im Datenbank-experimentieren-Assistenten

Nachdem Sie die Quell-Ablaufverfolgung auf Zielservern wiedergeben, können Sie einen Analysebericht in Datenbank experimentieren-Assistenten (DEA) generieren. Analyseberichte können Sie die Erkenntnisse über die Auswirkungen auf die Leistung der vorgeschlagenen Änderungen zu erhalten.

## <a name="create-an-analysis-report"></a>Erstellen Sie einen Analysebericht

Wählen Sie in DEA das Symbol "Menü" ein. Wählen Sie im erweiterten Menü **Analyseberichte** neben dem Prüflistensymbol.

![Menü "Analyse"](./media/database-experimentation-assistant-create-report/dea-create-reports-menu.png)

Klicken Sie unter **Analyseberichte**Option **neue Analysebericht**.

![Neuen Bericht im Menü](./media/database-experimentation-assistant-create-report/dea-create-reports-new-report.png)

Geben Sie ein, oder wählen Sie die folgende Informationen:

- **Name des Berichts**: Geben Sie einen Namen für den Bericht aus. Den Namen des Berichts wird verwendet, sowohl für A und B-Datenbanken. Beispiel: *Ein (oder B)*  + *Berichtsnamen* + *Eindeutiger Bezeichner*. 
- **Servername**: Geben Sie den Namen des Servercomputers, die in A, enthalten sein sollen B und Analysedatenbanken.
- **SQL Server-Instanzname**: Geben Sie den Namen der SQL Server-Instanz, die für den Bericht verwendet werden soll.
- **Ablaufverfolgung für den Quellserver**: Geben Sie die erste Ablaufverfolgungs-(.trc)-Optimierungs-arbeitsauslastungsdateien-Datei von SQL Server (2008 R2).
- **Ablaufverfolgung für den Zielserver**: Geben Sie die SQL Server (2014) ersten trc Zieldatei aus.

![Neue Analysis-Berichtsseite](./media/database-experimentation-assistant-create-report/dea-create-reports-inputs.png)

## <a name="generate-a-report"></a>Generieren eines Berichts

Nach dem eingeben oder Auswählen der erforderlichen Informationen auf der **neue Analysebericht** Seite **starten** mit dem Erstellen des Berichts beginnen. Wenn die Informationen, die Sie eingegeben haben, gültig ist, wird der Bericht erstellt. Andernfalls werden die Textfelder, die ungültige Informationen mit roten hervorgehoben. Stellen Sie sicher, dass die richtigen Werte eingeben, und wählen Sie dann **starten**. 

Ein neuer Bericht wird generiert. Die Analysedatenbank folgt das Benennungsschema Analysis + *Name des benutzerdefinierten Berichts* + *Eindeutiger Bezeichner*.

## <a name="frequently-asked-questions-about-analysis-reports"></a>Häufig gestellte Fragen zu Berichten

### <a name="what-does-my-analysis-report-tell-me"></a>Was teilt meinen Bericht mir?
    
DEA verwendet statistische Tests Ihrer arbeitsauslastung zu analysieren und zu bestimmen, wie jede Abfrage von Ziel 1 zum Ziel 2 ausgeführt wurde. Er bietet Details zu der Leistung für jede Abfrage. Erfahren Sie mehr über DEA in [Einstieg](database-experimentation-assistant-get-started.md).
    
### <a name="can-i-create-a-new-analysis-report-while-another-report-is-being-generated"></a>Kann ich einen neuen Bericht erstellen, während einem anderen Bericht generiert wird?
    
Nein.  Derzeit kann jeweils nur einen Bericht zu einem Zeitpunkt, um Konflikte zu vermeiden generiert werden. Allerdings können mehr als eine Erfassung ausgeführt und gleichzeitig wiedergeben.

### <a name="i-upgraded-dea-to-version-20-can-i-still-view-and-use-my-old-reports"></a>Ich aktualisiert DEA auf Version 2.0. Kann ich weiterhin anzeigen und Verwenden von meine alte Berichte?
    
Ja. Um zuvor generierte Berichte anzuzeigen, müssen Sie das Schema des Berichts aktualisieren. Weitere Informationen finden Sie unter [DEA 2.0: Update-Datenbankschema für Analysebericht in DEA](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-updating-db-schema-for-analysis-report-in-the-database-experimentation-assistant/).
    
### <a name="can-i-generate-an-analysis-report-by-using-the-command-prompt"></a>Kann ich einen Bericht generieren, über die Eingabeaufforderung?
    
Ja. Sie können einen Analysebericht an der Eingabeaufforderung generieren. Sie können den Bericht dann in der Benutzeroberfläche anzeigen. Weitere Informationen finden Sie unter [führen Sie an der Eingabeaufforderung](database-experimentation-assistant-run-command-prompt.md).
    
## <a name="troubleshoot-analysis-reports"></a>Problembehandlung bei Analyseberichten

###  <a name="what-security-permissions-do-i-need-to-generate-and-view-an-analysis-report-on-my-server"></a>Was Sicherheitsberechtigungen benötige ich, zum Generieren und einen Analysebericht auf meinem Server anzeigen zu können?
    
Der Benutzer, die DEA angemeldet ist, muss auf dem Analyseserver über Systemadministratorrechte verfügen. Wenn der Benutzer Mitglied einer Gruppe ist, stellen Sie sicher, dass die Gruppe über Systemadministratorrechte verfügt.

|Mögliche Fehler|Lösung|  
|---|---|  
|Kann nicht mit der Datenbank hergestellt werden. Stellen Sie sicher, dass Sie über Systemadministratorrechte für die Analyse und Anzeigen der Berichte verfügen.|Sie verfügen nicht über Zugriff oder Sysadmin-Rechte an den Server oder Datenbank. Bestätigen Sie Ihre-Anmeldeberechtigungen verfügt, und versuchen Sie es erneut.|  
|Kann nicht generiert werden **Berichtsnamen** auf dem Server **Servernamen**. Einzelheiten finden Sie in der **Berichtsnamen** Bericht.|Sie möglicherweise nicht die Sysadmin-Rechte erforderlich, um einen neuen Bericht erstellen. Um detaillierte Fehlerinformationen anzuzeigen, wählen Sie die fehlerhafte-Bericht aus, und überprüfen Sie die Protokolle im % temp %\\DEA.|  
|Der aktuelle Benutzer nicht über die erforderlichen Berechtigungen zum Ausführen des Vorgangs verfügen. Stellen Sie sicher, dass Sie über Systemadministratorrechte für die Ablaufverfolgung ausführen und Analysieren der Berichte verfügen.|Sie verfügen nicht über die Sysadmin-Rechte erforderlich, um einen neuen Bericht erstellen.|  

### <a name="i-cant-connect-to-the-computer-running-sql-server"></a>Ich kann keine Verbindung zum Computer mit SQL Server herstellen
    
- Vergewissern Sie sich, dass der Name der SQL Server-Computers gültig ist. Versuchen Sie, mit dem Server hergestellt werden soll, mithilfe von SQL Server Management Studio (SSMS), um zu bestätigen.
- Vergewissern Sie sich, dass es sich bei Ihrer Konfiguration der Firewall Verbindungen mit dem Computer mit SQL Server nicht blockiert.
- Vergewissern Sie sich, dass der Benutzer die erforderlichen Benutzerrechte verfügt. 

Sehen Sie weitere Informationen in den Protokollen im % temp %\\DEA. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.

### <a name="i-see-an-error-when-i-generate-an-analysis-report"></a>Ich eine Fehlermeldung angezeigt, wenn ich einen Analysebericht erstellt
    
Zugriff auf das Internet ist bei der ersten, die Sie einen Bericht generieren, nach der Installation von DEA erforderlich. Zugriff auf das Internet ist erforderlich, um Pakete herunterzuladen, die für die statistische Analyse erforderlich sind.

Wenn ein Fehler auftritt, während der Bericht erstellt wird, zeigt die Seite "Status" den spezifischen Schritt, mit der Analyse Fehler bei der Generierung. Sehen Sie weitere Informationen in den Protokollen im % temp %\\DEA. Stellen Sie sicher, dass Sie eine gültige Verbindung an den Server mit den erforderlichen Benutzerrechten, und wiederholen Sie dann. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.

|Mögliche Fehler|Lösung|  
|---|---|  
|RInterop erreicht einen Fehler beim Starten. RInterop in den Protokollen, und versuchen Sie es noch mal.|DEA erfordert eine Internetverbindung abhängige R-Pakete herunterzuladen. Überprüfen Sie im % temp %-RInterop Protokolle\\RInterop und DEA Protokolle im % temp %\\DEA. Wenn RInterop nicht ordnungsgemäß initialisiert wurde, oder wenn es, ohne die richtigen R-Pakete initialisiert, möglicherweise die Ausnahme "Fehler beim Generieren neuer Bericht" nach dem Schritt InitializeRInterop in den Protokollen DEA angezeigt.<br><br>RInterop zeigen die Protokolle können auch einen Fehler wie "ist kein Jsonlite Paket verfügbar." Wenn Ihr Computer nicht über Internetzugriff verfügt, können Sie manuell die erforderlichen Jsonlite R-Paket herunterladen:<br><br><li>Wechseln Sie zu dem % USERPROFILE%\\DEARPackages Ordner Dateisystem des Computers. In diesem Ordner umfasst die Pakete, die von R für DEA verwendet wird.</li><br><li>Ist der Ordner "Jsonlite" fehlt in der Liste der installierten Pakete, Sie benötigen Sie einen Computer mit Internetzugriff zum Herunterladen der endgültigen Produktversion von Jsonlite\_1.4.zip aus [ https://cran.r-project.org/web/packages/jsonlite/index.html ](https://cran.r-project.org/web/packages/jsonlite/index.html).</li><br><li>Kopieren Sie die ZIP-Datei mit dem Computer, auf dem Sie DEA ausgeführt werden.  Extrahieren Sie den Jsonlite-Ordner und kopieren Sie ihn in % USERPROFILE%\\DEARPackages. Dieser Schritt installiert automatisch das Paket Jsonlite in r Der Ordner heißen **Jsonlite** und der Inhalt sollte direkt in den Ordner nicht nächsttieferen Ebene aus.</li><br><li>Schließen Sie DEA, öffnen Sie es erneut und wiederholen Sie den Analyse erneut ein.</li><br>Sie können auch die RGUI verwenden. Wechseln Sie zu **Pakete** > **installieren aus Zip**. Rufen Sie das Paket, das Sie zuvor heruntergeladen haben, und installieren.<br><br>Wenn RInterop initialisiert und ordnungsgemäß eingerichtet wurde, sollte "Installieren von abhängigen R-Paket Jsonlite" in den Protokollen RInterop angezeigt werden.|  
|Kann nicht auf eine Verbindung mit SQL Server-Instanz herstellen, stellen Sie sicher, dass der Servername richtig ist, und überprüfen Sie die erforderlichen Zugriffsrechte für den Benutzer, der angemeldet ist.|Möglicherweise keinen Zugriff oder Benutzerrechte für den Server oder den Namen des Servers ist möglicherweise falsch.| 
|RInterop Prozess ist ein Timeout aufgetreten. In den Protokollen DEA und RInterop, beenden Sie den RInterop-Prozess im Task-Manager, und versuchen Sie es dann erneut.<br><br>oder<br><br>RInterop befindet sich im Zustand "faulted". Beenden Sie den RInterop-Prozess im Task-Manager, und versuchen Sie es dann erneut.|Überprüfen Sie in %TEMP% protokolliert\\RInterop, um den Fehler zu bestätigen. Entfernen Sie den Prozess RInterop Task-Manager, bevor Sie es erneut versuchen. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.| 

### <a name="the-report-is-generated-but-data-appears-to-be-missing"></a>Der Bericht wird generiert, aber Daten scheinbar fehlen
    
Überprüfen Sie die Datenbank auf dem Analysecomputer mit SQL Server, um sicherzustellen, dass Daten vorhanden sind. Überprüfen Sie, dass die Analysis-Datenbank vorhanden ist, und überprüfen Sie die Tabellen. Sehen Sie z. B. die folgenden Tabellen: TblBatchesA TblBatchesB und TblSummaryStats.

Wenn Daten nicht vorhanden ist, die Daten möglicherweise nicht ordnungsgemäß kopiert haben, oder die Datenbank ist möglicherweise beschädigt. Wenn nur einige Daten fehlen, die Ablaufverfolgungsdateien Capture-Vorgangs erstellt oder Wiedergabe möglicherweise nicht erfasst haben Ihre arbeitsauslastung präzise. Wenn die Daten vorhanden sind, überprüfen Sie die Protokolldateien im % temp %\\DEA, um festzustellen, ob Fehler protokolliert wurden. Klicken Sie dann versuchen Sie erneut, um den Bericht zu generieren.

Weitere Fragen oder Feedback? Übermitteln Sie Feedback über das Tool DEA, indem Sie auf das Smiley-Symbol der unteren linken Ecke.  

## <a name="next-steps"></a>Nächste Schritte

- Gewusst wie: Anzeigen den Analysebericht finden Sie unter [Anzeigen von Berichten](database-experimentation-assistant-view-report.md).

- Für einen 19-minütige Einführung in DEA und Demonstrationen im folgenden Video:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
