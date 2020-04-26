---
title: 'Auftrags Schritt-Eigenschaften: neuer Auftrags Schritt (Seite "Allgemein") | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.job.stepgeneral.f1
ms.assetid: 8d1885ba-4386-4528-8f2b-68c16852720c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8a957e2032f3be0e48d5bcfa4ed4508775e04477
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62510954"
---
# <a name="job-step-properties-new-job-step-general-page"></a>Auftragsschritteigenschaften: Neuer Auftragsschritt (Seite „Allgemein“)
  Mithilfe dieser Seite können Sie die Eigenschaften eines [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Auftrags Schritts anzeigen und ändern oder einen neuen Auftrags Schritt definieren.  
  
 Erweitern Sie im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent, klicken Sie mit der rechten Maustaste auf **Aufträge**, klicken Sie auf **Neuer Auftrag**, wählen Sie die Seite **Schritte** aus, und klicken Sie auf **Neu**, um zu dieser Seite zu navigieren. Sie können auch zu dieser Seite navigieren, indem Sie mit der rechten Maustaste auf einen Auftrag im Objekt-Explorer klicken, auf **Eigenschaften**klicken, die Seite **Schritte** auswählen, und auf **Neu**, **Einfügen**oder **Bearbeiten**klicken.  
  
## <a name="options"></a>Optionen  
 **Schrittname**  
 Legt den Namen des Auftrags fest.  
  
 **Type**  
 Legt das durch den Auftrag verwendete Subsystem fest. Basierend auf dem von Ihnen ausgewählten Subsystem ändern sich die für das Definieren des Auftragsschritts angezeigten Optionen.  
  
 **Ausführen als**  
 Legt das Proxykonto für den Auftragsschritt fest. Mitglieder der festen Serverrolle „sysadmin“ können auch das **SQL-Agent-Dienstkonto**angeben.  
  
 **Datenbank**  
 Legt die Datenbank fest, in der der Auftragsschritt ausgeführt wird. Diese Option ist nicht für alle Auftragsschritttypen verfügbar.  
  
 **Befehl**  
 Legt den durch den Auftrag ausgeführten Befehl fest.  
  
## <a name="options-for-transact-sql-job-steps"></a>Optionen für Transact-SQL-Auftragsschritte  
 **Öffnen**  
 Lädt den Befehl aus einer Datei.  
  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den ausgewählten Text in die Zwischenablage.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
 **Parse**  
 Überprüft die Syntax des Befehls.  
  
## <a name="options-for-activex-script-job-steps"></a>Optionen für Auftragsschritte von ActiveX-Skript  
  
> [!IMPORTANT]  
>  Das ActiveX Scripting-Subsystem wird in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus dem [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.  
  
 **VBScript**  
 Gibt [!INCLUDE[msCoName](../../includes/msconame-md.md)] VBScript als Sprache für die Auftragsschritte an.  
  
 **JScript**  
 Gibt JScript als Sprache für die Auftragsschritte an.  
  
 **Andere**  
 Geben Sie den Namen der Sprache für Auftragsschritte ein, die in einer anderen Skriptsprache geschrieben wurden.  
  
 **Öffnen**  
 Lädt den Befehl aus einer Datei.  
  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-operating-system-cmdexec-job-steps"></a>Optionen für Auftragsschritte des Betriebssystems (CmdExec)  
 **Prozessexitcode eines erfolgreichen Befehls**  
 Geben Sie den Exitcode ein, den der Befehl zurückgibt, um einen Erfolg zu melden.  
  
 **Öffnen**  
 Lädt den Befehl aus einer Datei.  
  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-powershell-job-steps"></a>Optionen für PowerShell-Auftragsschritte  
 **Öffnen**  
 Lädt das Skript aus einer Datei.  
  
 **Alle auswählen**  
 Markiert den Text des Skripts.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-distributor-job-steps"></a>Optionen für Replikationsverteiler-Auftragsschritte  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-merge-job-steps"></a>Optionen für Replikationsmerge-Auftragsschritte  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-queue-reader-job-steps"></a>Optionen für Auftragsschritte des Replikation-Warteschlangenlesers  
 **Datenbank**  
 Die Datenbank, die für den Auftragsschritt verwendet werden soll.  
  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-snapshot-job-steps"></a>Optionen für Replikationsmomentaufnahme-Auftragsschritte  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-replication-transaction-log-reader-job-steps"></a>Optionen für Auftragsschritte des Replikationstransaktionsprotokoll-Lesers  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-sql-server-analysis-services-command-job-steps"></a>Optionen für Auftragsschritte von SQL Server Analysis Services-Befehlen  
 **Server**  
 Wählt den Server aus, auf dem der Auftragsschritt ausgeführt wird.  
  
 **Öffnen**  
 Lädt den Befehl aus einer Datei.  
  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-sql-server-analysis-services-query-job-steps"></a>Optionen für Auftragsschritte von SQL Server Analysis Services-Abfragen  
 **Server**  
 Wählt den Server aus, auf dem der Auftragsschritt ausgeführt wird.  
  
 **Datenbank**  
 Die Datenbank, die für den Auftragsschritt verwendet werden soll.  
  
 **Öffnen**  
 Lädt den Befehl aus einer Datei.  
  
 **Alle auswählen**  
 Markiert den Text des Befehls.  
  
 **Kopieren**  
 Kopiert den markierten Text.  
  
 **Einfügen**  
 Fügt die Inhalte aus der Zwischenablage ein.  
  
## <a name="options-for-integration-services-package-execution-job-steps"></a>Optionen für Auftragsschritte von Integration Services-Paketausführungen  
  
### <a name="general-tab"></a>Registerkarte Allgemein  
 Gibt den Speicherort des [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ([!INCLUDE[ssIS](../../includes/ssis-md.md)])-Pakets an, und welche Authentifizierungsmethode verwendet werden soll. Die folgenden Optionen sind verfügbar, wenn Sie diese Registerkarte auswählen.  
  
 **Paketquelle**  
 Gibt den Speicherort des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Pakets an. Wählen Sie eine der folgenden Optionen aus:  
  
-   **SQL Server**  
  
-   **Dateisystem**  
  
-   **SSIS-Paket Speicher**  
  
 **Server**  
 Geben Sie den Namen des Servers ein, auf dem das [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paket gespeichert ist. Diese Option ist nur verfügbar, wenn **SQL Server** oder **SSIS-Paketspeicher** für **Paketquelle**angegeben ist.  
  
 **Windows-Authentifizierung verwenden**  
 Für Anmeldungen bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung verwendet.  
  
 **SQL Server Authentifizierung verwenden**  
 Für Anmeldungen an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung verwendet. Wenn diese Authentifizierungsmethode ausgewählt wurde, geben Sie entsprechend **Benutzername** und **Kennwort**ein.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung wird aus Gründen der Abwärtskompatibilität bereitgestellt. Aus Sicherheitsgründen sollte möglichst die Windows-Authentifizierung verwendet werden.  
  
 **Pakete**  
 Geben Sie den Speicherort des Pakets ein.  
  
> [!IMPORTANT]  
>  Klicken Sie für kennwortgeschützte [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Pakete auf die Registerkarte **Konfigurationen** , um das Kennwort im Dialogfeld **Paketkennwort** einzugeben. Andernfalls erzeugt der Auftrag des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, der das kennwortgeschützte Paket ausführt, einen Fehler.  
  
### <a name="configurations-tab"></a>Registerkarte Konfigurationen  
 Gibt Konfigurationsoptionen für das [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Paket an. Wenn Sie diese Registerkarte auswählen, sind die folgenden Optionen verfügbar.  
  
 **Konfigurationsdateien**  
 Führt die Konfigurationsdateien für das Paket in einer Liste auf.  
  
 **Add (Hinzufügen)**  
 Fügt eine Konfigurationsdatei für das Paket hinzu.  
  
 **Remove**  
 Entfernt eine Konfigurationsdatei für das Paket.  
  
 **Nach oben**  
 Verschiebt die ausgewählte Konfigurationsdatei nach oben.  
  
 **Nach unten**  
 Verschiebt die ausgewählte Konfigurationsdatei nach unten.  
  
### <a name="command-files-tab"></a>Registerkarte Befehlsdateien  
 Wählt Befehlsdateien für das Paket aus. Befehlsdateien werden entsprechend ihrer Reihenfolge in der Liste verarbeitet. Die folgenden Optionen sind verfügbar, wenn Sie diese Registerkarte auswählen.  
  
 **Befehlsdateien**  
 Führt die Befehlsdateien für das Paket in einer Liste auf.  
  
 **Add (Hinzufügen)**  
 Fügt eine Befehlsdatei hinzu.  
  
 **Remove**  
 Entfernt die ausgewählte Befehlsdatei.  
  
 **Nach oben**  
 Verschiebt die ausgewählte Befehlsdatei nach oben.  
  
 **Nach unten**  
 Verschiebt die ausgewählte Befehlsdatei nach unten.  
  
### <a name="data-sources-tab"></a>Registerkarte Datenquellen  
 Zeigt die im Paket angegebenen Datenquellen auf dieser Registerkarte an.  
  
 **Verbindungs-Manager**  
 Zeigt den Namen der Datenquelle an.  
  
 **Beschreibung**  
 Zeigt die Beschreibung der Datenquelle an.  
  
 **Verbindungs Zeichenfolge**  
 Zeigt die Verbindungszeichenfolge für die Datenquelle an.  
  
### <a name="execution-options-tab"></a>Registerkarte Ausführungsoptionen  
 Zeigt die Ausführungsoptionen für das Paket auf dieser Registerkarte an oder ändert die Werte.  
  
 **Paket bei Überprüfungswarnungen fehlschlagen lassen**  
 Wählen Sie diese Option aus, wenn die Paketausführung bei Überprüfungswarnungen fehlschlagen soll.  
  
 **Paket ohne Ausführung überprüfen**  
 Wählen Sie diese Option für den Auftragsschritt aus, wenn das Paket überprüft, nicht jedoch ausgeführt werden soll.  
  
 **Maximale Anzahl von gleichzeitig ausführbaren Dateien**  
 Die maximale Anzahl der gleichzeitig ausführbaren Dateien.  
  
 **Paketprüfpunkte aktivieren**  
 Wählen Sie diese Option für den Auftragsschritt aus, wenn Paketprüfpunkte verwendet werden sollen.  
  
 **Prüfpunktdatei**  
 Geben Sie den Namen der Prüfpunktdatei des Pakets ein.  
  
 **...**  
 Sucht nach der Prüfpunktdatei des Pakets.  
  
 **Neustartoptionen überschreiben**  
 Wenn Sie diese Option auswählen, können Sie für diesen Auftragsschritt Neustartoptionen angeben, die von den im Paket angegebenen Optionen abweichen.  
  
 **Neustartoption**  
 Wählt die Aktion aus, die bei einem Neustart des Pakets durchgeführt werden soll.  
  
### <a name="logging-tab"></a>Registerkarte Protokollierung  
 Zeigt die Protokollanbieter für das Paket auf dieser Registerkarte an oder ändert diese.  
  
 **Protokoll Anbieter**  
 Wählt die ClassID für den Protokollanbieter aus.  
  
 **Konfigurations Zeichenfolge**  
 Geben Sie die Konfigurationszeichenfolge für den Protokollanbieter ein.  
  
 **Remove**  
 Entfernt den Protokollanbieter.  
  
### <a name="set-values-tab"></a>Registerkarte Werte festlegen  
 Zeigt die Eigenschaftswerte für das Paket auf dieser Registerkarte an oder ändert die Werte.  
  
 **Eigenschaftspfad**  
 Zeigt einen Pfad für die Eigenschaft an oder ändert diese.  
  
 **Wert**  
 Zeigt einen Wert für die Eigenschaft an oder ändert diesen.  
  
 **Remove**  
 Entfernt die Eigenschaft.  
  
### <a name="verification-tab"></a>Registerkarte Überprüfung  
 Wählt die Überprüfungsoptionen für den Auftragsschritt auf dieser Registerkarte aus.  
  
 **Nur signierte Pakete ausführen**  
 Führt nur Pakete aus, die signiert wurden. Bei Auswahl dieser Option schlägt der Auftragsschritt fehlt, wenn das Paket nicht signiert ist.  
  
 **Paketbuild überprüfen**  
 Führt nur Pakete aus, die eine bestimmte Buildnummer besitzen. Bei Auswahl dieser Option schlägt der Auftragsschritt fehl, wenn das Paket nicht die angegebene Buildnummer besitzt.  
  
 **Build**  
 Geben Sie die Buildnummer des Pakets ein.  
  
 **Paket-ID überprüfen**  
 Führt nur Pakete aus, die eine bestimmte ID besitzen. Bei Auswahl dieser Option schlägt der Auftragsschritt fehl, wenn das Paket nicht die angegebene ID besitzt.  
  
 **Paket-ID**  
 Geben Sie die Paket-ID ein.  
  
 **Versions-ID überprüfen**  
 Führt nur Pakete mit einer bestimmten Versions-ID aus. Bei Auswahl dieser Option schlägt der Auftragsschritt fehl, wenn das Paket nicht die angegebene Versions-ID besitzt.  
  
 **Versions-ID**  
 Geben Sie die Versions-ID ein.  
  
### <a name="command-line-tab"></a>Registerkarte Befehlszeile  
 Gibt die Befehlszeilenoptionen für das Paket an. Wenn Sie diese Registerkarte auswählen, sind die folgenden Optionen verfügbar.  
  
 **Die ursprünglichen Optionen wiederherstellen**  
 Verwendet die in diesem Dialogfeld festgelegten Befehlszeilenoptionen.  
  
 **Befehlszeile manuell bearbeiten**  
 Gibt die Optionen im Befehlszeilenfenster an.  
  
 **Befehlszeile**  
 Geben Sie die für dieses Paket zu verwendenden Befehlszeilenoptionen ein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Auftrags Schritten](manage-job-steps.md)   
 [SQL Server-Agent Aufträge für Pakete](../../integration-services/packages/sql-server-agent-jobs-for-packages.md)   
 [Replikations-Agent-Verwaltung](../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
