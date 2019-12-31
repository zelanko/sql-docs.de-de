---
title: Erstellen von Analyseberichten
description: Erstellen von Analyseberichten in Assistent für Datenbankexperimente
ms.date: 11/21/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.custom: seo-lt-2019
ms.openlocfilehash: 4d3f057ffcfb1030b473b69f96b7204b3a975613
ms.sourcegitcommit: aaa42f26c68abc2de10eb58444fe6b490c174eab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74307974"
---
# <a name="create-analysis-reports-in-database-experimentation-assistant-sql-server"></a>Erstellen von Analyseberichten in Assistent für Datenbankexperimente (SQL Server)

Nachdem Sie die Quell Ablauf Verfolgung auf beiden Ziel Servern wiedergegeben haben, können Sie in Assistent für Datenbankexperimente (DEA) einen Analysebericht generieren. Mithilfe von Analyseberichten erhalten Sie Einblicke in die Auswirkungen auf die Leistung von vorgeschlagenen Änderungen.

## <a name="create-an-analysis-report"></a>Erstellen eines Analyse Berichts

Wählen Sie in der DEA das Menü Symbol aus. Wählen Sie im erweiterten Menü neben dem Prüfliste-Symbol die Option **Analyseberichte** aus.

![Menü "Analyse"](./media/database-experimentation-assistant-create-report/dea-create-reports-menu.png)

Wählen Sie unter **Analyseberichte**die Option **neuer Analysebericht**aus.

![Menü "neuer Analysebericht"](./media/database-experimentation-assistant-create-report/dea-create-reports-new-report.png)

Geben Sie folgende Informationen ein, oder wählen Sie Sie aus:

- **Berichts Name**: Geben Sie einen Namen für den Bericht ein. Der Berichts Name wird sowohl für A-als auch für B-Datenbanken verwendet. Beispiel: der*eindeutige Bezeichner* *(oder B)* + des*Berichts namens* + .
- **Servername**: Geben Sie den Namen des Server Computers ein, den Sie in den Datenbanken a, B und Analysis einschließen möchten.
- **SQL Server Instanzname**: Geben Sie den Namen der SQL Server Instanz ein, die für den Bericht verwendet werden soll.
- Ablauf **Verfolgung für Quell Server**: Geben Sie die erste (2008 R2) erste Ablauf Verfolgungs Datei (. trc) für SQL Server ein.
- Ablauf **Verfolgung für Zielserver**: Geben Sie den Ziel SQL Server (2014) First. TRC-Datei ein.

![Seite "neuer Analysebericht"](./media/database-experimentation-assistant-create-report/dea-create-reports-inputs.png)

## <a name="generate-a-report"></a>Generieren eines Berichts

Nachdem Sie die erforderlichen Informationen auf der Seite **neuer Analysebericht** eingegeben oder ausgewählt haben, klicken Sie auf **starten** , um mit dem Erstellen des Berichts zu beginnen. Wenn die eingegebenen Informationen gültig sind, wird der Analysebericht erstellt. Andernfalls werden die Textfelder mit ungültigen Informationen rot hervorgehoben. Stellen Sie sicher, dass Sie die richtigen Werte eingeben, und klicken Sie dann auf **starten**.

Es wird ein neuer Analysebericht generiert. Die Analysedatenbank folgt den*eindeutigen Bezeichner*Namensschema Analyse + *Benutzerdefinierte Berichts Name* + .

## <a name="frequently-asked-questions-about-analysis-reports"></a>Häufig gestellte Fragen zu Analyseberichten

**F: Wie kann ich meinen Analysebericht erzählen?**

Von der DEA werden statistische Tests verwendet, um die Arbeitsauslastung zu analysieren und zu bestimmen, wie die einzelnen Abfragen von Ziel 1 auf Ziel 2 ausgeführt Es enthält Leistungsdetails für jede Abfrage. Weitere Informationen zu DEA [finden](database-experimentation-assistant-get-started.md)Sie in den ersten Schritten.

**F: kann ich einen neuen Analysebericht erstellen, während ein anderer Bericht generiert wird?**

Nein  Derzeit kann jeweils nur ein Bericht generiert werden, um Konflikte zu verhindern. Sie können jedoch mehr als eine Erfassung und Wiedergabe gleichzeitig ausführen.

**F: Ich habe ein Upgrade von DEA auf Version 2,0 ausgeführt. Kann ich meine alten Berichte weiterhin anzeigen und verwenden?**

Ja. Um zuvor generierte Berichte anzuzeigen, müssen Sie das Schema des Berichts aktualisieren. Weitere Informationen finden Sie unter " [DEA 2,0: Update Database Schema for Analysis Report in DEA](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-updating-db-schema-for-analysis-report-in-the-database-experimentation-assistant/)".

**F: kann ich mithilfe der Eingabeaufforderung einen Analysebericht generieren?**

Ja. An der Eingabeaufforderung können Sie einen Analysebericht generieren. Anschließend können Sie den Bericht in der Benutzeroberfläche anzeigen. Weitere Informationen finden Sie [unter Ausführen an der Eingabeaufforderung](database-experimentation-assistant-run-command-prompt.md).

## <a name="troubleshoot-analysis-reports"></a>Problembehandlung bei Analyseberichten

**F: welche Sicherheits Berechtigungen benötige ich, um einen Analysebericht auf meinem Server zu generieren und anzuzeigen?**

Der Benutzer, der bei DEA angemeldet ist, muss über sysadmin-Rechte auf dem Analysis-Server verfügen. Wenn der Benutzer zu einer Gruppe gehört, stellen Sie sicher, dass die Gruppe über sysadmin-Rechte verfügt.

|Mögliche Fehler|Lösung|  
|---|---|  
|Es kann keine Verbindung mit der Datenbank hergestellt werden. Stellen Sie sicher, dass Sie über Systemadministrator Rechte zum Analysieren und Anzeigen der Berichte verfügen.|Sie verfügen möglicherweise nicht über Zugriffs-oder sysadmin-Rechte für den Server oder die Datenbank. Bestätigen Sie Ihre Anmelde Rechte, und versuchen Sie es erneut.|  
|Der **Berichts Name** kann nicht auf dem Server **Servernamen**generiert werden. Weitere Informationen finden Sie im Bericht Berichts **Name** .|Möglicherweise verfügen Sie nicht über die sysadmin-Rechte, die zum Generieren eines neuen Berichts erforderlich sind. Wenn Sie ausführliche Fehler anzeigen möchten, wählen Sie den Bericht mit dem Fehlerbericht aus, und überprüfen\\Sie die Protokolle in% Temp% Dea.|  
|Der aktuelle Benutzer verfügt nicht über die erforderlichen Berechtigungen zum Ausführen des Vorgangs. Stellen Sie sicher, dass Sie über Systemadministrator Rechte zum Durchführen der Ablauf Verfolgung und zum Analysieren der Berichte verfügen.|Sie verfügen nicht über die sysadmin-Rechte, die erforderlich sind, um einen neuen Bericht zu generieren.|  

**F: Ich kann keine Verbindung mit dem Computer herstellen, auf dem SQL Server**

- Vergewissern Sie sich, dass der Name des Computers, der SQL Server ausgeführt wird, gültig ist. Versuchen Sie, eine Verbindung mit dem Server herzustellen, indem Sie SQL Server Management Studio (SSMS) verwenden.
- Vergewissern Sie sich, dass Ihre Firewallkonfiguration keine Verbindungen mit dem Computer blockiert, der SQL Server ausgeführt wird
- Vergewissern Sie sich, dass der Benutzer über die erforderlichen Benutzerrechte verfügt.

Weitere Details finden Sie in den Protokollen unter% Temp%\\Dea. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.

**F: Ich sehe einen Fehler beim Generieren eines Analyse Berichts.**

Der Internet Zugriff ist erforderlich, wenn Sie zum ersten Mal nach der Installation von DEA einen Analysebericht generieren. Zum Herunterladen von Paketen, die für statistische Analysen erforderlich sind, ist ein Internet Zugriff erforderlich.

Wenn beim Erstellen des Berichts ein Fehler auftritt, wird auf der Seite Status der jeweilige Schritt angezeigt, bei dem die Analyse nicht erfolgreich war. Weitere Details finden Sie in den Protokollen unter% Temp%\\Dea. Stellen Sie sicher, dass Sie über eine gültige Verbindung mit dem Server mit den erforderlichen Benutzerrechten verfügen, und versuchen Sie es erneut. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.

|Mögliche Fehler|Lösung|  
|---|---|  
|Fehler beim Starten von rinterop. Überprüfen Sie rinterop-Protokolle, und versuchen Sie es erneut|Die DEA benötigt Internet Zugriff, um abhängige R-Pakete herunterzuladen. Überprüfen Sie die rinterop-Protokolle\\in% Temp% rinterop-und DEA\\-Protokollen in% Temp% Dea. Wenn rinterop nicht ordnungsgemäß initialisiert wurde oder ohne die richtigen R-Pakete initialisiert wurde, wird möglicherweise nach dem initializerinterop-Schritt in den DEA-Protokollen die Ausnahme "Fehler beim Generieren eines neuen Analyse Berichts" angezeigt.<br><br>Die rinterop-Protokolle enthalten möglicherweise einen Fehler ähnlich dem "Es ist kein jsonlite-Paket verfügbar". Wenn Ihr Computer nicht über Internetzugang verfügt, können Sie das erforderliche jsonlite R-Paket manuell herunterladen:<br><br><li>Wechseln Sie im Dateisystem des Computers\\zum Ordner "% User Profile% dearpackages". Dieser Ordner besteht aus den Paketen, die von R für die DEA verwendet werden.</li><br><li>Wenn der Ordner "jsonlite" in der Liste der installierten Pakete fehlt, benötigen Sie einen Computer mit Internet Zugriff, um die Releaseversion von jsonlite\_1.4. [https://cran.r-project.org/web/packages/jsonlite/index.html](https://cran.r-project.org/web/packages/jsonlite/index.html)zip aus herunterzuladen.</li><br><li>Kopieren Sie die ZIP-Datei auf den Computer, auf dem Sie die Datei "DEA" ausführen.  Extrahieren Sie den Ordner "jsonlite", und kopieren Sie ihn\\in "% User Profile% dearpackages". In diesem Schritt wird das jsonlite-Paket automatisch in R installiert. Der Ordner sollte mit dem Namen " **jsonlite** " benannt werden, und der Inhalt sollte sich direkt innerhalb des Ordners befinden, nicht eine Ebene unten.</li><br><li>Schließen Sie die Analyse, öffnen Sie Sie erneut, und versuchen Sie erneut,</li><br>Sie können auch die rgui verwenden. Wechseln Sie zu **Pakete** > **Installieren von ZIP**. Wechseln Sie zu dem zuvor heruntergeladenen Paket, und installieren Sie.<br><br>Wenn rinterop initialisiert und ordnungsgemäß eingerichtet wurde, sollte in den rinterop-Protokollen "jsonlite der abhängigen R-Pakete installieren" angezeigt werden.|  
|Es kann keine Verbindung mit der SQL Server Instanz hergestellt werden. Stellen Sie sicher, dass der Server Name richtig ist, und überprüfen Sie den erforderlichen Zugriff für den angemeldeten Benutzer.|Möglicherweise verfügen Sie nicht über Zugriffs-oder Benutzerrechte auf dem Server, oder der Servername ist falsch.|
|Timeout bei rinterop-Prozess. Überprüfen Sie die Protokolle "DEA" und "rinterop", und führen Sie den rinterop-Prozess im Task-Manager aus.<br><br>oder<br><br>Rinterop weist einen fehlerhaften Status auf. Unterbinden Sie den rinterop-Prozess im Task-Manager, und wiederholen Sie dann den Vorgang.|Überprüfen Sie die Protokolle in\\% Temp% rinterop, um den Fehler zu bestätigen. Entfernen Sie den rinterop-Prozess vom Task-Manager, bevor Sie es erneut versuchen. Wenn das Problem weiterhin besteht, wenden Sie sich an das Produktteam.|

**F: der Bericht wird generiert, aber die Daten fehlen.**

Überprüfen Sie die Datenbank auf dem Analysis-Computer, auf dem SQL Server ausgeführt wird, um zu bestätigen, dass Daten vorhanden sind Überprüfen Sie, ob die Analysis-Datenbank vorhanden ist, und überprüfen Sie Überprüfen Sie beispielsweise die folgenden Tabellen: tblbatchesa, tblbatchesb und tblsummarystats.

Wenn keine Daten vorhanden sind, wurden die Daten möglicherweise nicht ordnungsgemäß kopiert, oder die Datenbank ist möglicherweise beschädigt. Wenn nur einige Daten fehlen, haben die in der Erfassung oder Wiedergabe erstellten Ablauf Verfolgungs Dateien möglicherweise die Arbeitsauslastung nicht exakt aufgezeichnet. Wenn die Daten vorhanden sind, überprüfen Sie die Protokolldateien in%\\Temp% DEA, um festzustellen, ob Fehler protokolliert wurden. Versuchen Sie dann erneut, den Analysebericht zu generieren.

Weitere Fragen oder Feedback? Übermitteln Sie Ihr Feedback über das Tool "DEA", indem Sie in der unteren linken Ecke das Smiley-Symbol auswählen. 

## <a name="see-also"></a>Siehe auch

- Weitere Informationen zum Anzeigen des Analyse Berichts finden Sie unter [Anzeigen von Berichten](database-experimentation-assistant-view-report.md).
