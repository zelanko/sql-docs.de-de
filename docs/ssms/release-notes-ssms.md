---
title: Versionshinweise zu SQL Server Management Studio (SSMS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3dc76cc1-3b4c-4719-8296-f69ec1b476f9
author: markingmyname
ms.author: maghan
manager: craigg
ms.custom: ''
ms.date: 06/12/2019
ms.openlocfilehash: 0be9bae60c46aa43c6f0acb5de5204d33a318450
ms.sourcegitcommit: 65ceea905030582f8d89e75e97758abf3b1f0bd6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67399668"
---
# <a name="release-notes-for-sql-server-management-studio-ssms"></a>Versionshinweise zu SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Dieser Artikel enthält Details zu Updates, Verbesserungen und Fehlerbehebungen für die aktuellen und früheren Versionen von SSMS.

<!--
The latest ## H2 section of this Release Notes article has been reformatted to match the new standard.
The new standard replaces the use of bullet lists with the 2-column markdown table format.
Please use the new 2-column table format going forward.
And please do include the final blank row of "| &nbsp;| &nbsp;|".

The ## H2 titles are also being shortened, by the removal of unnecessary repetitive strings.
In this case, "## SSMS 17.9" is being shortened to "## 17.9" (as one standard actual example).
And we are appending the 'Month yyyy'.

Also, this file has been renamed to the new standard, which calls for the file name to be with "release-notes-[techAreaName].md".
The old name for this file was 'sql-server-management-studio-changelog-ssms.md'.
But today the new file name is 'release-notes-ssms.md' (still in 'docs/ssms/').

Thank you.
GeneMi. 2019/04/02.
-->

## <a name="ssms-181"></a>SSMS 18.1

Herunterladen: &nbsp; &nbsp; [SSMS 18.1 herunterladen](download-sql-server-management-studio-ssms.md)<br/>
Buildnummer: &nbsp; &nbsp; 15.0.18131.0<br/>
Releasedatum: &nbsp; &nbsp; 11. Juni 2019

SSMS 18.1 ist das neueste Release von SSMS mit allgemeiner Verfügbarkeit (GA). Frühere Versionen von SSMS finden Sie weiter unten im Abschnitt [Vorgängerversionen von SSMS](release-notes-ssms.md#previous-ssms-releases).

Im Vergleich zu Version 18.0 ist Version 18.1 ein kleines Update mit den folgenden neuen Elementen und Fehlerbehebungen:

## <a name="whats-new-in-181"></a>Neues in Version 18.1

| Neues Element| Details|
| :-------| :------|
| Datenbankdiagramme | [In SSMS wurden wieder Datenbankdiagramme hinzugefügt.](https://feedback.azure.com/forums/908035/suggestions/37507828)
| SSBDIAGNOSE.EXE |Dem SSMS-Paket wurde wieder die SQL Server-Diagnose (Befehlszeilentool) hinzugefügt.|
| Integration Services (SSIS) | Unterstützung für die Zeitplanung des SSIS-Pakets in Azure, das sich entweder im SSIS-Katalog in Azure oder im Dateisystem befindet. Es gibt drei Einträge für das Starten des Dialogfelds „Neuer Zeitplan“: Das Menüelement *Neuer Zeitplan...* wird angezeigt, wenn Sie mit der rechten Maustaste auf das SSIS-Paket im SSIS-Katalog in Azure klicken. Die zweite Option erreichen Sie über das Menüelement *Schedule SSIS Package in Azure* (Zeitplan für das SSIS-Paket in Azure) unter dem Menüelement *Migrate to Azure* (Migrieren zu Azure) unter *Tools*. Die dritte Option „Schedule SSIS“ (SSIS-Zeitplan in Azure) wird angezeigt, wenn Sie mit der rechten Maustaste auf den Auftragsordner unter dem SQL Server-Agent der verwalteten Azure SQL-Datenbank-Instanz klicken.|

## <a name="bug-fixes-in-181"></a>Fehlerkorrekturen in Version 18.1

| Neues Element | Detail: |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Barrierefreiheit | Verbesserte Barrierefreiheit der Benutzeroberfläche des Agent-Auftrags. |
| Barrierefreiheit | Verbesserte Barrierefreiheit auf der Seite „Stretch Datenbank-Monitor“ durch Hinzufügen eines barrierefreien Namens für die Schaltfläche *Automatisch aktualisieren* und eines Namens zur Verwendung von Screenreader-Software, der Benutzer darüber informiert, um welche Schaltfläche es sich handelt und welche Auswirkungen es hat, wenn diese gedrückt wird. |
| ADS-Integration| Es wurde ein Problem behoben, bei dem es bei der Verwendung von ADS-registrierten Servern zu Abstürzen kam.|
| Datenbank-Designer | Unterstützung für die „Latin1_General_100_BIN2_UTF8“-Sortierung (verfügbar in SQL Server 2019 CTP 3.0). |
| Datenklassifizierung | Es wird verhindert, dass Spalten in Verlaufstabellen Vertraulichkeitsbezeichnungen hinzugefügt werden, was nicht unterstützt wird. |
| Datenklassifizierung | Es wurde ein Problem behoben, bei dem der Kompatibilitätsgrad falsch behandelt wurde (Server im Vergleich zur Datenbank). |
| Datenbank-Designer | Unterstützung für die „Latin1_General_100_BIN2_UTF8“-Sortierung (verfügbar in SQL 2019 CTP 3.0). |
| SSMS allgemein | Es wurde ein Problem behoben, bei dem die Skripterstellung von Pseudospalten in einem Index fehlerhaft war. |
| SSMS allgemein | Es wurde ein Problem auf der Seite „Anmeldungseigenschaften“ behoben, bei dem das Klicken auf die Schaltfläche *Anmeldeinformationen hinzufügen* eine Nullverweisausnahme zur Folge hatte. |
| SSMS allgemein | Es wurde ein Problem hinsichtlich der Größenanzeige der Spalte „money“ auf der Seite „Indexeigenschaften“ behoben. |
| SSMS allgemein | Es wurde ein Problem behoben, bei dem SSMS die IntelliSense-Einstellung von *Tools/Extras* im SQL-Editor-Fenster nicht berücksichtigt hat. |
| SSMS allgemein | Es wurde ein Problem behoben, bei dem SSMS die Hilfeeinstellungen nicht berücksichtigt hat (online im Vergleich zu offline). |
| Hohe DPI-Werte | Das Layout von Steuerelementen in Fehlerdialogen für nicht unterstützte Abfrageoptionen wurde korrigiert. |
| Hohe DPI-Werte | Das Layout von Steuerelementen auf der Seite *Neue Verfügbarkeitsgruppe* wurde korrigiert, |
| Hohe DPI-Werte | Das Layout der Seite *Neuer Auftragszeitplan* wurde korrigiert. Weitere Details finden Sie im [Feedbackforum](https://feedback.azure.com/forums/908035/suggestions/37632094). |
| Importieren von Flatfiles | Es wurde ein Problem behoben, bei dem Zeilen beim Import verloren gingen.|
| IntelliSense/Editor | Der SMO-basierte Datenverkehr von Abfragen zu Azure SQL-Datenbanken für IntelliSense wurde reduziert. |
| IntelliSense/Editor | Es wurden grammatikalische Fehler in der QuickInfo behoben, die beim Eingeben von T-SQL zum Erstellen eines Benutzers angezeigt wurden. Außerdem wurde die Fehlermeldung zum Unterscheiden zwischen Benutzern und Anmeldungen behoben. |
| Protokollanzeige | Es wurde ein Problem behoben, bei dem SSMS selbst nach einem Doppelklick auf ein älteres Archivzeichen im Objekt-Explorer immer das aktuelle Server- oder Agent-Protokoll öffnete. Weitere Details finden Sie im [Feedbackforum](https://feedback.azure.com/forums/908035/suggestions/37633648). |
| SSMS-Setup | Es wurde ein Problem behoben, bei dem das SSMS-Setup fehlschlug, wenn im Setup des Protokollpfads Leerzeichen enthalten waren. Weitere Details finden Sie im [Feedbackforum](https://feedback.azure.com/forums/908035/suggestions/37496110). |
| SSMS-Setup | Ein Problem wurde behoben, bei dem SSMS nach Anzeigen des Begrüßungsbildschirms sofort beendet wurde. </br> Auf den folgenden Websites erhalten Sie weitere Informationen: [Feedback](https://feedback.azure.com/forums/908035/suggestions/37502512), [SSMS startet nicht](https://dba.stackexchange.com/questions/238609/ssms-refuses-to-start) und [Datenbankadministratoren](https://dba.stackexchange.com/questions/237086/sql-server-management-studio-18-wont-open-only-splash-screen-pops-up). |
| Objekt-Explorer | Es wurden Einschränkungen bei der Aktivierung von *PowerShell starten* beseitigt, die bei einer Verbindung mit SQL unter Linux auftraten. |
| Objekt-Explorer | Es wurde ein Problem behoben, bei dem SSMS beim Erweitern des Knotens „PolyBase/Erweiterungsgruppe“ abstürzte (bei einer Verbindung mit einem Computeknoten). |
| Objekt-Explorer | Es wurde ein Problem behoben, bei dem das Menüelement *Deaktiviert* auch nach dem Deaktivieren eines bestimmten Indexes weiterhin aktiviert war. Weitere Details finden Sie im [Feedbackforum](https://feedback.azure.com/forums/908035/suggestions/37735375). |
| Berichte | Korrigieren des Berichts, um tatsächlich „GrantedQueryMemory“ in KB anzuzeigen (Bericht „SQL Performance Dashboard“). Weitere Details finden Sie im [Feedbackforum](https://feedback.azure.com/forums/908035/suggestions/37167289). |
| Berichte | Verbesserte Ablaufverfolgung des Protokollblocks in Always On-Szenarios. |
| Showplan | Das neue Showplanelement *SpillOccurred* wurde zum Showplanschema hinzugefügt. |
| Showplan | Es wurden Remotelesevorgänge (*ActualPageServerReads*, *ActualPageServerReadAheads*, *ActualLobPageServerReads* und *ActualLobPageServerReadAheads*) zum Showplanschema hinzugefügt. |
| SMO/Skripterstellung | Das Abfragen von Edgeeinschränkungen während der Skripterstellung wird für nicht graphische Tabellen vermieden. |
| SMO/Skripterstellung | Einschränkungen hinsichtlich der Vertraulichkeitsklassifizierung bei der Skripterstellung von Spalten mit der *Datenklassifizierung* wurden aufgehoben. |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem „Skript generieren“ in einer Graphtabelle fehlschlägt, wenn Daten generiert werden. Weitere Details finden Sie im [Feedbackforum](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898466). |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem die „EnumObjects()“-Methode keine Schemanamen für ein Synonym abgerufen haben. |
| SMO/Skripterstellung | Es wurde ein Problem in „UIConnectionInfo.LoadFromStream()“ behoben, bei dem der Abschnitt *AdvancedOptions* nicht gelesen werden konnte (wenn kein Kennwort angegeben wurde). |
| SQL-Agent | Es wurde ein Problem behoben, bei dem SSMS bei der Arbeit mit dem Fenster „Auftragseigenschaften“ fehlschlug. Weitere Details finden Sie im [Feedbackforum](https://feedback.azure.com/forums/908035/suggestions/37164244). |
| SQL-Agent | Es wurde ein Problem behoben, bei dem die Schaltfläche „Anzeigen“ in den *Auftragsschritt-Eigenschaften* nicht immer aktiviert war und somit das Anzeigen der Ausgabe eines bestimmten Auftragsschritts verhindert wurde. |
| XEvent-Benutzeroberfläche | Die Spalte „Paket“ wurde zu XEvents-Listen hinzugefügt, um Ereignisse mit identischem Namen zu unterscheiden. |
| XEvent-Benutzeroberfläche | Der fehlende Klassentyp „EXTERNAL LIBRARY“ wurde hinzugefügt, der „XEventUI“ zugeordnet ist. |

### <a name="known-issues-181"></a>Bekannte Probleme (18.1)

- Benutzern kann ein Fehler angezeigt werden, wenn ein Tabellenobjekt aus dem Objekt-Explorer in den Abfrage-Editor gezogen wird. Dieser Fehler ist bekannt, und der Fix ist für das nächste Release geplant.

- Die Farboptionen für *Verbindungen gruppieren* und *Einzelne Serververbindungen* unter „Optionen > Text-Editor > Registerkarte „Editor“ und Statusleiste > Layout und Farben der Statusleiste“ werden nach Schließen von SSMS 18.1 nicht beibehalten. Sobald Sie SSMS wieder öffnen, wird die Option „Layout und Farben der Statusleiste“ auf die Standardeinstellung zurückgesetzt.

## <a name="previous-ssms-releases"></a>Vorgängerversionen von SSMS

Laden Sie die Vorgängerversionen von SSMS herunter, indem Sie die Titellinks in den folgenden Abschnitten anklicken:

## <a name="downloadssdtmediadownloadpng-ssms-180httpsgomicrosoftcomfwlinklinkid2088649"></a>![Download](../ssdt/media/download.png) [SSMS 18.0](https://go.microsoft.com/fwlink/?linkid=2088649)

- Releasenummer: 18.0<br>
- Buildnummer: 15.0.18118.0<br>
- Releasedatum: 24. April 2019

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=2088649&clcid=0x40a)

### <a name="whats-new-in-180"></a>Neues in 18.0

| Neues Element| Details|
| :-------| :------|
|Unterstützung für SQL Server 2019|SSMS 18.0 ist das erste Release, bei dem SQL Server 2019 (CompatLevel 150) vollständig *berücksichtigt* wird.|
|Unterstützung für SQL Server 2019|Unterstützung für „BATCH_STARTED_GROUP“ und „BATCH_COMPLETED_GROUP“ in SQL Server 2019 und der verwalteten SQL-Instanz.|
|Unterstützung für SQL Server 2019|SMO: Unterstützung für Inlining benutzerdefinierter Funktionen wurde hinzugefügt.|
|Unterstützung für SQL Server 2019|GraphDB: Ein Flag im Showplan für TC-Sequenz in Graph wurde hinzugefügt.|
|Unterstützung für SQL Server 2019|Always Encrypted: Unterstützung für AEv2/Enclave wurde hinzugefügt.|
|Unterstützung für SQL Server 2019|Always Encrypted: Das Verbindungsdialogfeld verfügt über eine neue Registerkarte „Always Encrypted“, wenn der Benutzer auf die Schaltfläche „Optionen“ klickt, um Enclave-Unterstützung zu aktivieren/konfigurieren.|
|Geringere Downloadgröße in SSMS| Die aktuelle Downloadgröße beträgt ca. 500 MB, was ungefähr der Hälfte des SSMS-Bündels 17.x entspricht.
|SSMS basiert auf Visual Studio 2017 Isolated Shell|Die neue Shell (SSMS basiert auf Visual Studio 2017, Version 15.9.11) enthält die neuesten Sicherheitspatches, und mit ihr werden alle Fehlerkorrekturen bei Barrierefreiheitsproblemen entsperrt.|
|Verbesserungen für die Barrierefreiheit in SSMS| Ein Schwerpunkt lag in der Behebung von Problemen mit der Barrierefreiheit in allen Tools (SSMS, DTA und Profiler).|
|SSMS kann jetzt in einem benutzerdefinierten Ordner installiert werden| Diese Option ist über die Befehlszeile (nützlich bei einer unbeaufsichtigten Installation) und die Setup-Benutzeroberfläche verfügbar. Übergeben Sie über die Befehlszeile dieses zusätzliche Argument an die Datei „SSMS-Setup-ENU.exe“:<br> SSMSInstallRoot=C:\MySSMS18<br> Der neue Standardspeicherort für die Installation von SSMS lautet: „%ProgramFiles(x86)%\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe“.<br>Das bedeutet nicht, dass SSMS mehrere Instanzen besitzt.|
|SSMS kann in einer anderen Sprache als der Betriebssystemsprache installiert werden|Das Einrichten gemischter Sprachen wird nicht mehr blockiert. Sie können z. B. die deutsche Version von SSMS unter der französischen Windows-Version installieren. Stimmt die Sprache des Betriebssystems nicht mit der Sprache von SSMS überein, muss der Benutzer die Sprache folgendermaßen ändern: **Extras** > **Optionen** > **Internationale Einstellungen**. Andernfalls wird in SSMS die englische Benutzeroberfläche angezeigt.|
|SSMS verwendet keine gemeinsamen Komponenten mehr mit SQL Engine|Ein Schwerpunkt lag in der Vermeidung von gemeinsamen Komponenten mit SQL Engine, da dies häufig zu Wartungsproblemen (durch unbeabsichtigtes gegenseitiges Überschreiben der installierten Dateien) führte.|
|SSMS erfordert NetFx 4.7.2 oder höher.|Wir haben die Mindestanforderung von NetFx 4.6.1 auf NetFx 4.7.2 erhöht, damit die neuen Funktionen genutzt werden können, die vom neuen Framework bereitgestellt werden.|
|Möglichkeit zum Migrieren von SSMS-Einstellungen| Beim ersten Starten von SSMS 18 wird der Benutzer dazu aufgefordert, die Einstellungen aus 17.x zu migrieren. Die Dateien für Benutzereinstellungen werden jetzt als XML-Textdatei gespeichert, wodurch die Portabilität verbessert und eine Bearbeitung ermöglicht werden.|
|Unterstützung für hohe DPI-Werte| Hohe DPI-Werte sind nun standardmäßig aktiviert.|
|SSMS wird mit dem Microsoft OLE DB-Treiber geliefert| Informationen hierzu finden Sie unter [Herunterladen des Microsoft OLE DB-Treibers für SQL Server](https://docs.microsoft.com/sql/connect/oledb/download-oledb-driver-for-sql-server).|
|SSMS wird unter Windows 8 nicht unterstützt. Windows 10 und Windows Server 2016 erfordern Version 1607 (10.0.14393) oder höher|Aufgrund der neuen Abhängigkeit von NetFx 4.7.2 wird SSMS 18.0 nicht unter Windows 8 und älteren Versionen von Windows 10 und Windows Server 2016 installiert. Das SSMS-Setup wird bei diesen Systemen blockiert. Windows 8.1 wird weiterhin unterstützt.|
|SSMS wird nicht mehr der PATH-Umgebungsvariable hinzugefügt|Der Pfad zu SSMS.EXE (und Tools im Allgemeinen) wird nicht mehr zum Pfad hinzugefügt. Benutzer können diesen entweder manuell hinzufügen oder bei einem modernen Windows-Computer das Startmenü verwenden.|
|Paket-IDs sind zum Entwickeln von SSMS-Erweiterungen nicht mehr erforderlich| In der Vergangenheit wurden in SSMS nur bekannte Pakete selektiv geladen, sodass Entwickler ihr eigenes Paket registrieren mussten. Das ist nicht mehr der Fall.|
|SSMS allgemein|Die Konfigurationsoption „AUTOGROW_ALL_FILES“ wurde für Dateigruppen in SSMS bereitgestellt.|
|SSMS allgemein|Die riskanten Optionen „Lightweightpooling“ und „Prioritätserhöhung“ wurden von der grafischen SSMS-Benutzeroberfläche entfernt. Weitere Informationen finden Sie unter [Priority boost details – and why it’s not recommended (Informationen zur Prioritätserhöhung und Gründe, die dagegen sprechen)](https://blogs.msdn.microsoft.com/arvindsh/2010/01/26/priority-boost-details-and-why-its-not-recommended/).
|SSMS allgemein|Neues Menü und Tastenkombinationen zum Erstellen von Dateien: **STRG+ALT+N**. Mit **STRG+N** wird weiterhin eine neue Abfrage erstellt.|
|SSMS allgemein|Das Dialogfeld **Neue Firewallregel** ermöglicht dem Benutzer nun das Angeben eines Regelnamens anstelle der automatischen Generierung.|
|SSMS allgemein|IntelliSense im Editor wurde insbesondere für Version v140+ von T-SQL verbessert.|
|SSMS allgemein|Unterstützung für UTF-8 wurde im Dialogfeld für die Sortierung auf der SSMS-Benutzeroberfläche hinzugefügt.|
|SSMS allgemein|Es wurde für MRU-Kennwörter des Verbindungsdialogfelds zur „Windows-Anmeldeinformationsverwaltung“ gewechselt. Dadurch wird das lange bestehende Problem der nicht immer zuverlässigen Persistenz von Kennwörtern behoben.|
|SSMS allgemein|Verbesserte Unterstützung für Systeme mit mehreren Monitoren, indem sichergestellt wird, dass immer mehr Dialogfelder und Fenster auf dem erwarteten Monitor eingeblendet werden.|
|SSMS allgemein|Die Serverkonfiguration „Standardeinstellung der Sicherungsprüfsumme“ wurde auf der neuen Seite „Datenbankeinstellungen“ im Dialogfeld „Servereigenschaften“ bereitgestellt. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/08035-sql-server/suggestions/34634974](https://feedback.azure.com/forums/08035-sql-server/suggestions/34634974).|
|SSMS allgemein|Die Einstellung „maximum size for error log files“ (Maximale Größe von Fehlerprotokolldateien) wurde unter „SQL Server-Fehlerprotokolle konfigurieren“ zur Verfügung gestellt. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/33624115](https://feedback.azure.com/forums/908035/suggestions/33624115).|
|SSMS allgemein|„Zu Azure migrieren“ wurde im Menü „Extras“ hinzugefügt: Für einen schnellen und einfachen Zugriff und schnellere Migrationen zu Azure wurden der Datenmigrations-Assistent sowie Azure Database Migration Service integriert.|
|SSMS allgemein|Logik wurde hinzugefügt, um den Benutzer dazu aufzufordern, für offene Transaktionen einen Commit auszuführen, wenn „Change connection“ (Verbindung ändern) verwendet wird.|
|Integration in Azure Data Studio|Ein Menüelement zum Starten/Downloaden von Azure Data Studio wurde hinzugefügt.|
|Integration in Azure Data Studio|Das Menüelement „Start Azure Data Studio (Azure Data Studio starten)“ wurde im Objekt-Explorer hinzugefügt.|
|Integration in Azure Data Studio|Durch Klicken mit der rechten Maustaste auf einen Datenbankknoten im Objekt-Explorer werden dem Benutzer Kontextmenüs angezeigt, mit denen entweder eine Abfrage ausgeführt oder ein neues Notebook in Azure Data Studio erstellt werden kann.|
|Unterstützung für Azure SQL| Die Datenbankeigenschaften „SLO“, „Edition“ und „MaxSize“ akzeptieren jetzt benutzerdefinierte Namen und vereinfachen dadurch die Unterstützung zukünftiger Editionen von Azure SQL-Datenbanken.|
|Unterstützung für Azure SQL| Unterstützung für kürzlich hinzugefügte V-Kern-SKUs (universell und unternehmenskritisch) wurde hinzugefügt: Gen4_24 und alle Gen5.|
|Verwaltete Azure SQL-Instanz|„Anmeldungen mit AAD“ wurde als neue Anmeldemethode in SMO und SSMS hinzugefügt, wenn eine Verbindung zu einer verwalteten Azure SQL-Instanz besteht.|
|Always On|RTO (geschätzte Wiederherstellungszeit) und RPO (geschätzter Datenverlust) wurden im Always on-Dashboard von SSMS mit einem neuen Hashwert versehen. Die aktualisierte Dokumentation finden Sie unter [https://docs.microsoft.com/sql/database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups](../database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups.md).|
|Always Encrypted| Im Dialogfeld „Mit Server verbinden“ bietet das Kontrollkästchen „Always Encrypted aktivieren“ in der Registerkarte „Always Encrypted“ jetzt eine einfache Möglichkeit zum Aktivieren/Deaktivieren von Always Encrypted für eine Datenbankverbindung.|
|Always Encrypted mit Secure Enclaves| Die folgenden Verbesserungen zur Unterstützung von Always Encrypted mit Secure Enclaves wurden in der Vorschauversion von SQL Server 2019 vorgenommen:<br>Ein Textfeld zum Angeben der Enclave-Nachweis-URL im Dialogfeld „Mit Server verbinden“ (die neue Registerkarte „Always Encrypted“).<br>Das neue Kontrollkästchen im Dialogfeld „Neuer Spaltenhauptschlüssel“, um zu steuern, ob ein neuer Spaltenhauptschlüssel Enclave-Berechnungen zulässt.<br>Weitere Dialogfelder für die Always Encrypted-Schlüsselverwaltung stellen nun Informationen dazu bereit, welche Spaltenhauptschlüssel Enclave-Berechnungen zulassen.|
|Überwachungsdateien|Die Authentifizierungsmethode wurde von der Authentifizierung auf Basis des Speicherkontoschlüssel in die Azure AD-basierte Authentifizierung geändert.|
|Überwachungsdateien|Die Liste bekannter Überwachungsaktionen wurde aktualisiert, sodass diese nun FEATURE RESTRICTION ADD/CHANGE GROUP/DROP enthält.|
|Datenklassifizierung| Das Aufgabenmenü für die Datenklassifizierung wurde neu organisiert: Dem Datenbankaufgabenmenü wurde ein Untermenü hinzugefügt sowie eine Option zum Öffnen des Berichts aus dem Menü, ohne zuerst das Fenster „Daten klassifizieren“ öffnen zu müssen.|
|Datenklassifizierung|In SMO wurde die neue Funktion „Datenklassifizierung“ hinzugefügt. Spaltenobjekt macht neue Eigenschaften verfügbar: SensitivityLabelName, SensitivityLabelId, SensitivityInformationTypeName, SensitivityInformationTypeId und IsClassified (schreibgeschützt). Weitere Informationen finden Sie unter [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql).|
|Datenklassifizierung|Das neue Menüelement „Klassifizierungsbericht“ wurde dem Flyout „Datenklassifizierung“ hinzugefügt.|
|Datenklassifizierung| Empfehlungen wurden aktualisiert.|
|Upgrade des Datenbank-Kompatibilitätsgrads|Eine neue Option wurde unter **<Database name>**  > **Tasks** > **Datenbankupgrade** hinzugefügt. Mit ihr wird der neue **Abfrageoptimierungs-Assistent** gestartet, der den Benutzer durch folgende Prozesse führt:<br>Sammeln einer Leistungsbaseline, bevor ein Upgrade des Datenbank-Kompatibilitätsgrads durchgeführt wird<br>Durchführen eines Upgrades auf den gewünschten Datenbank-Kompatibilitätsgrad<br>Sammeln eines zweiten Durchlaufs von Leistungsdaten der gesamten Arbeitsauslastung<br>Ermitteln von Regressionen der Arbeitsauslastung und Bereitstellen getesteter Empfehlungen zur Verbesserung der Arbeitsauslastungsleistung<br>Dies ähnelt dem unter [Verwendungsszenarios für den Abfragespeicher](https://docs.microsoft.com/sql/relational-databases/performance/query-store-usage-scenarios#CEUpgrade) beschriebenen Datenbankupgrade mit Ausnahme des letzten Schritts, bei dem der Abfrageoptimierungs-Assistent sich nicht auf den letzten als funktionierend bekannten Zustand beruft, um Empfehlungen zu generieren.|
|Datenschichtanwendungs-Assistent|Hinzugefügt: Unterstützung für das Importieren/Exportieren von Datenschichtanwendungen mit Graphtabellen.|
|Assistent zum Importieren von Flatfiles|Logik zum Benachrichtigen des Benutzers, dass der Import möglicherweise zu einer Umbenennung der Spalten geführt hat, wurde hinzugefügt.|
|Integration Services (SSIS)|Unterstützung wurde hinzugefügt, durch die Kunden SSIS-Pakete für Azure-SSIS Integration Runtime planen können, die sich in einer Azure Government-Cloud befinden.|
|Integration Services (SSIS)|Wenn Sie den SQL-Agent der verwalteten Azure SQL-Instanz über SSMS verwenden, können Sie die Parameter und den Verbindungs-Manager im Auftragsschritt für den SSIS-Agent konfigurieren.|
|Integration Services (SSIS)|Beim Herstellen einer Verbindung mit Azure SQL-Datenbank oder einer verwalteten Azure SQL-Instanz können Sie *Standard* als Anfangsdatenbank verwenden.|
|Integration Services (SSIS)|Das neue Eintragselement **Try SSIS in Azure Data Factory (SSIS in Azure Data Factory ausprobieren)** wurde im Knoten „Integration Services-Kataloge“ hinzugefügt, mit dem Sie den „Assistenten zum Erstellen einer Integration Runtime“ starten und schnell eine „Azure-SSIS Integration Runtime“ erstellen können.
|Integration Services (SSIS)|Die Schaltfläche **Create SSIS IR (SSIS IR erstellen)** wurde im „Assistent für die Katalogerstellung“ hinzugefügt. Darüber können Sie den „Assistenten zum Erstellen einer Integration Runtime“ starten und schnell eine „Azure-SSIS Integration Runtime“ erstellen.|
|Integration Services (SSIS)|„ISDeploymentWizard“ unterstützt jetzt die SQL-Authentifizierung, die integrierte Azure Active Directory-Authentifizierung und die Azure Active Directory-Kennwortauthentifizierung im Befehlszeilenmodus.|
|Integration Services (SSIS)|Der Bereitstellungs-Assistent unterstützt jetzt das Erstellen und Bereitstellen für die SSIS Integration Runtime in Azure Data Factory.|
|Skripterstellung für Objekte|Neue Menüelemente wurden für „CREATE OR ALTER“ bei der Skripterstellung hinzugefügt.|
|Abfragespeicher|Die Nutzbarkeit einiger Berichte wurde verbessert (gesamter Ressourcenverbrauch), indem Tausendertrennzeichen zu Zahlen auf der Y-Achse der Diagramme hinzugefügt wurde.|
|Abfragespeicher|Ein neuer Bericht mit einer Statistik der Abfragewartezeit wurde hinzugefügt.|
|Abfragespeicher|Die Metrik „Execution Count (Anzahl der Ausführungen)“ wurde der Ansicht „Tracked Query (Nachverfolgte Abfrage)“ hinzugefügt.|
|Replikationstools|Unterstützung für die nicht standardmäßige Funktion der Portspezifikation im Replikationsmonitor und in SSMS wurde hinzugefügt.|
|Showplan|Tatsächlich verstrichene Zeit und tatsächliche Zeilen gegenüber geschätzten Zeilen wurden bei Verfügbarkeit unter dem Knoten „Showplanoperator“ hinzugefügt. Dadurch weist der tatsächliche Plan ein konsistenteres Aussehen mit dem Plan der Live-Abfragestatistik auf.|
|Showplan|Die QuickInfo beim Klicken auf die Schaltfläche „Abfrage bearbeiten“ für einen Showplan wurde geändert und ein Kommentar hinzugefügt, um dem Benutzer anzugeben, dass der Showplan möglicherweise von der SQL Engine abgeschnitten wurde, wenn die Abfrage mehr als 4000 Zeichen umfasst.|
|Showplan|Eine Logik zum Anzeigen von „Materializer-Operator (externer SELECT)“ wurde hinzugefügt.|
|Showplan|Ein neues Showplan-Attribut „BatchModeOnRowStoreUsed“ wurde hinzugefügt, um Abfragen leicht erkennen zu können, bei denen die Funktion zur Überprüfung von Zeilenspeichern im Batchmodus verwendet wird. Jedes Mal, wenn eine Abfrage die Überprüfung von Zeilenspeichern im Batchmodus ausführt, wird ein neues Attribut (BatchModeOnRowStoreUsed="true") zum StmtSimple-Element hinzugefügt.|
|Showplan|Showplan-Unterstützung für das RelOp-Element in „LocalCube“ für ROLLUP und CUBE wurde hinzugefügt.|
|Showplan|Der neue Operator „LocalCube“ für die neuen Aggregationsfunktionen ROLLUP und CUBE wurde in Azure SQL Data Warehouse hinzugefügt.|
|SMO| Die SMO-Unterstützung für die Erstellung eines fortsetzbaren Index wurde erweitert.|
|SMO| Ein neues Ereignis für SMO-Objekte (PropertyMissing) wurde hinzugefügt, damit Anwendungsautoren SMO-Leistungsprobleme früher erkennen können.|
|SMO| Die neue Eigenschaft „DefaultBackupChecksum“ für das Konfigurationsobjekt wurde bereitgestellt, die der Serverkonfiguration „Standardeinstellung der Sicherungsprüfsumme“ zugeordnet ist.|
|SMO| Die neue Eigenschaft „ProductUpdateLevel“ wurde für das Serverobjekt bereitgestellt, die der Wartungsebene für die verwendete SQL-Version zugeordnet ist (z. B. CU12, RTM).|
|SMO| Die neue LastGoodCheckDbTime-Eigenschaft wurde für das Datenbankobjekt zur Verfügung gestellt. Diese Eigenschaft wird der Datenbankeigenschaft „lastgoodcheckdbtime“ zugeordnet. Wenn diese Eigenschaft nicht verfügbar ist, wird der Standardwert 1.1.1900 12:00:00 Uhr zurückgegeben.|
|SMO|Der Speicherort für die Datei „RegSrvr.xml“ (Konfigurationsdatei für den registrierten Server) wurde in „%AppData%\Microsoft\SQL Server Management Studio“ verschoben (ohne Version, sodass eine gemeinsame Nutzung in allen SSMS-Versionen möglich ist).|
|SMO|„Cloudzeugen“ wurde als neuer Quorumtyp und als neuer Ressourcentyp hinzugefügt.|
|SMO|Unterstützung für „Edgeeinschränkungen“ wurde in SMO und SSMS hinzugefügt.|
|SMO|Die Unterstützung des kaskadierenden Deletes wurde in SMO und SSMS zu den „Edgeeinschränkungen“ hinzugefügt.|
|SMO|Für die Datenklassifizierung wurde die Unterstützung von Lese-/Schreibzugriffsberechtigungen hinzugefügt.|
|Sicherheitsrisikobewertung| In Azure SQL Data Warehouse wurde ein Aufgabenmenü für die Sicherheitsrisikobewertung aktiviert.|
|Sicherheitsrisikobewertung|Die Regeln für die Bewertung von Sicherheitsrisiken, die in Servern der verwalteten Azure SQL-Instanz ausgeführt werden, wurden geändert, damit die Überprüfungsergebnisse der Sicherheitsrisikobewertung mit denjenigen in Azure SQL-Datenbank übereinstimmen.|
|Sicherheitsrisikobewertung| Die „Sicherheitsrisikobewertung“ unterstützt jetzt Azure SQL-Datenbank.|
|Sicherheitsrisikobewertung|Eine neue Funktion zum Exportieren von Überprüfungsergebnissen der Sicherheitsrisikobewertung nach Excel wurde hinzugefügt.|
|XEvent-Viewer|In XEvent-Viewer wurde das Showplan-Fenster aktiviert, um mehr XEvents anzuzeigen.|

### <a name="bug-fixes-in-180"></a>Fehlerkorrekturen in 18.0

| Neues Element| Details|
| :-------| :------|
|Abstürze und Einfrieren|Eine Ursache häufiger SSMS-Abstürze im Zusammenhang mit GDI-Objekten wurde behoben.|
|Abstürze und Einfrieren|Eine häufige Ursache für das Hängenbleiben und eine schlechte Leistung beim Auswählen eines Skripts zum Erstellen/Aktualisieren/Löschen wurde behoben (unnötige Abrufe von SMO-Objekten wurden entfernt).|
|Abstürze und Einfrieren|Ein Hängenbleiben beim Herstellen einer Verbindung mit einer Azure SQL-Datenbank mithilfe von MFA bei aktivierten ADAL-Ablaufverfolgungen wurde behoben.|
|Abstürze und Einfrieren|Ein Hängen (bzw. empfundenes Hängen) in der Live-Abfragestatistik beim Aufrufen über den Aktivitätsmonitor wurde behoben (das Problem trat bei Verwendung der SQL Server-Authentifizierung ohne Festlegung von „Sicherheitsinformationen permanent speichern“ auf).|
|Abstürze und Einfrieren|Ein Hängen bei Auswahl von „Berichte“ im Objekt-Explorer wurde behoben, das bei Verbindungen mit hoher Latenzzeit oder temporär nicht vorhandenem Zugriff der Ressourcen auftreten konnte.|
|Abstürze und Einfrieren|Ein Absturz bei der Verwendung des zentralen Verwaltungsservers und von Azure SQL-Servern in SSMS wurde behoben. Weitere Informationen finden Sie unter [SMSS 17.5 application error and crash when using Central Management Server (Anwendungsfehler in SMSS 17.5 und Absturz bei Verwendung eines zentralen Verwaltungsservers)](https://feedback.azure.com/forums/908035/suggestions/33374884).|
|Abstürze und Einfrieren|Eine Verzögerung im Objekt-Explorer wurde behoben, indem die Methode zum Abrufen der IsFullTextEnabled-Eigenschaft optimiert wurde.|
|Abstürze und Einfrieren|Ein Hängenbleiben beim „Assistenten zum Kopieren von Datenbanken“ wurde behoben, indem keine überflüssigen Abfragen zum Abrufen von Datenbankeigenschaften erstellt werden.|
|Abstürze und Einfrieren|Ein Problem wurde behoben, durch das SSMS beim Bearbeiten von T-SQL nicht mehr reagiert hat/abgestürzt ist.|
|Abstürze und Einfrieren|Ein Problem wurde behoben, durch das SSMS beim Bearbeiten großer T-SQL-Skripts nicht mehr reagiert hat.|
|Abstürze und Einfrieren|Ein Problem wurde behoben, durch das SSMS beim Verarbeiten großer Datasets, die von Abfragen zurückgegeben wurden, nicht genügend Arbeitsspeicher zur Verfügung hatte.|
|SSMS allgemein|Ein Problem wurde behoben, bei dem „ApplicationIntent“ in Verbindungen in „Registrierte Server“ nicht übergeben wurde.|
|SSMS allgemein|Ein Problem wurde behoben, bei dem das Formular „New XEvent Session Wizard UI“ (Neue Benutzeroberfläche für XEvent-Sitzungs-Assistent) auf Monitoren mit hohem DPI-Wert nicht richtig gerendert wurde.|
|SSMS allgemein|Ein Problem beim Importieren einer BACPAC-Datei wurde behoben.|
|SSMS allgemein|Ein Problem beim Anzeigen der Eigenschaften einer Datenbank (mit FILEGROWTH > 2048 GB), das zu einem Fehler mit arithmetischem Überlauf geführt hat, wurde behoben.|
|SSMS allgemein|Ein Fehler wurde behoben, durch den der Bericht für das Leistungsdashboard PAGELATCH- und PAGEIOLATCH-Wartevorgänge gemeldet hat, die nicht in Unterberichten enthalten waren.|
|SSMS allgemein|Mehrere Fehler wurden behoben, damit SSMS besser mit mehreren Monitoren zurechtkommt und Dialogfelder im richtigen Monitor geöffnet werden.|
|Analysis Services (AS)|Ein Problem wurde behoben, bei dem die Option „Erweiterte Einstellungen“ für die AS XEvent-Benutzeroberfläche abgeschnitten wurde.|
|Analysis Services (AS)|Ein Fehler wurde behoben, bei dem die DAX-Analyse die Ausnahme „Datei nicht gefunden“ ausgelöst hat.|
|Azure SQL-Datenbank|Ein Problem wurde behoben, bei dem die Datenbankliste für das Abfragefenster in Azure SQL-Datenbank während der Verbindung mit einer Benutzerdatenbank in Azure SQL-Datenbank anstatt mit dem Master nicht ordnungsgemäß aufgefüllt wurde.|
|Azure SQL-Datenbank|Ein Problem wurde behoben, bei dem es nicht möglich war, eine „temporale Tabelle“ zu einer Azure SQL-Datenbank hinzuzufügen.|
|Azure SQL-Datenbank|Die Untermenüoption „Statistics properties“ (Statistikeigenschaften) im Menü „Statistics“ (Statistik) in Azure wurde aktiviert, da sie nun schon eine Zeit lang voll unterstützt wird.|
|Azure SQL: Allgemeine Unterstützung|Probleme der allgemeinen Azure-Benutzeroberflächensteuerung wurden behoben, durch die der Benutzer daran gehindert wurde, Azure-Abonnements anzuzeigen (falls mehr als 50 vorhanden waren). Darüber hinaus wurde die Sortierung in eine Sortierung nach Name und nicht nach Abonnement-ID geändert. Dies konnte für den Benutzer z.B. beim Wiederherstellen einer Sicherung aus einer URL auftreten.|
|Azure SQL: Allgemeine Unterstützung|Ein Problem der allgemeinen Azure-Benutzeroberflächensteuerung beim Aufzählen von Abonnements wurde behoben, durch das ein Fehler „Der Index lag außerhalb des Bereichs. Er darf nicht negativ und kleiner als die Sammlung sein.“ auftreten konnte, wenn der Benutzer über keine Abonnements in einigen Mandanten verfügte. Dies konnte für den Benutzer z.B. beim Wiederherstellen einer Sicherung aus einer URL auftreten.|
|Azure SQL: Allgemeine Unterstützung|Ein Problem wurde behoben, bei dem Servicelevel-Zielpunkte (SLOs) hartcodiert wurden, wodurch die SSMS-Unterstützung neuerer Azure SQL-SLOs erschwert wurde. Benutzer können sich nun bei Azure anmelden und SSMS die Berechtigung erteilen, alle anwendbaren SLO-Daten („Edition“ und „Max Size“) abzurufen.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Verbesserte Unterstützung für verwaltete Instanzen: Nicht unterstützte Optionen auf der Benutzeroberfläche wurden deaktiviert und eine Fehlerbehebung für die Option „Überwachungsprotokolle anzeigen“ zur Handhabung des URL-Überwachungsziels wurde vorgenommen.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Der Assistent zum Generieren und Veröffentlichen von Skripts erstellt Scripts mit nicht unterstützten CREATE DATABASE-Klauseln.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Live-Abfragestatistik für verwaltete Instanzen wurde aktiviert.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Mit „Datenbankeigenschaften“ -> „Dateien“ wurden falsche Skripts für ALTER DB ADD FILE erstellt.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Eine Regression beim SQL-Agent-Planer wurde behoben, bei der die ONIDLE-Planung auch bei Auswahl eines anderen Planungstyps ausgewählt wurde.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Anpassung von MAXTRANSFERRATE, MAXBLOCKSIZE für Sicherungen in Azure Storage.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Problem, bei dem für die Sicherung des Protokollfragments vor dem Wiederherstellungsvorgang ein Skript erstellt wird (dies wird auf CL nicht unterstützt).|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Der Assistent zum Erstellen einer Datenbank erstellt keine korrekten Skripts für die CREATE DATABASE-Anweisung.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|SSIS-Pakete werden in SSMS besonders behandelt, wenn eine Verbindung mit verwalteten Instanzen besteht.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Ein Problem wurde behoben, durch das bei dem Versuch, „Aktivitätsmonitor“ während der Verbindung mit verwalteten Instanzen zu verwenden, ein Fehler angezeigt wurde.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Die Unterstützung für AAD-Anmeldungen im SSMS-Explorer wurde verbessert.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Die Skripterstellung für FileGroups-Objekte in SMO wurde verbessert.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Die Benutzeroberfläche für Anmeldeinformationen wurde verbessert.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Die Unterstützung der logischen Replikation wurde hinzugefügt|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Ein Problem wurde behoben, bei dem durch das Klicken mit der rechten Maustaste auf eine Datenbank und das Auswählen von „Datenschichtanwendung importieren“ ein Fehler auftrat.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Ein Problem wurde behoben, bei dem durch das Klicken mit der rechten Maustaste auf „TempDB“ Fehler aufgetreten sind.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Ein Problem wurde behoben, bei dem bei der Skripterstellung der Anweisung „ALTER DB ADD FILE“ in SMO ein leeres T-SQL-Skript generiert wurde.|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Die Anzeige von Eigenschaften spezifisch für Server mit verwalteten Instanzen wurde verbessert (Hardwaregeneration, Dienstebene, verwendeter und reservierter Speicher).|
|Unterstützung verwalteter Azure SQL-Datenbank-Instanzen|Ein Problem wurde behoben, bei dem bei der Skripterstellung einer Datenbank keine Skripterstellung zusätzlicher Dateigruppen und Dateien ausgeführt wurde. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/37326799](https://feedback.azure.com/forums/908035/suggestions/37326799). |
|Sichern/Wiederherstellen/Anfügen/Trennen einer Datenbank|Ein Problem wurde behoben, bei dem der Benutzer eine Datenbank nicht anfügen konnte, wenn der physische Dateiname der MDF-Datei nicht dem ursprünglichen Dateinamen entsprach.|
|Sichern/Wiederherstellen/Anfügen/Trennen einer Datenbank|Ein Problem wurde behoben, bei dem SSMS keinen gültigen Wiederherstellungsplan oder einen nicht optimalen Plan finden konnte. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897752). |
|Sichern/Wiederherstellen/Anfügen/Trennen einer Datenbank|Ein Fehler wurde behoben, bei dem der Assistent zum Anfügen von Datenbanken sekundäre Dateien, die umbenannt wurden, nicht angezeigt hat. Jetzt wird die Datei, einschließlich eines Kommentars, angezeigt (z. B. „nicht gefunden“). Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/32897434](https://feedback.azure.com/forums/908035/suggestions/32897434). |
|Assistent zum Kopieren von Datenbanken|Der Versuch des Assistenten zum Generieren von Skripts/Übertragen/Kopieren von Datenbanken, eine Tabelle mit einer In-Memory-Tabelle zu erstellen, erzwingt nicht die Einstellung ON für ANSI_PADDINGTON.|
|Assistent zum Kopieren von Datenbanken|Übertragung von Datenbankaufgabe/Assistent zum Kopieren von Datenbanken unterbrochen auf SQL Server 2017 und SQL Server 2019.|
|Assistent zum Kopieren von Datenbanken|Der Assistent zum Generieren von Skripts/Übertragen/Kopieren von Datenbanken erstellt ein Skript für die Tabellenerstellung vor der Erstellung von zugeordneten externen Datenquellen.|
|Verbindungsdialogfeld|Das Entfernen von Benutzernamen aus der vorherigen Benutzernamenliste durch Drücken der ENTF-Taste wurde aktiviert. Weitere Informationen finden Sie unter [Allow deletion of users from SSMS login window (Löschen von Benutzern aus dem SSMS-Anmeldefenster zulassen)](https://feedback.azure.com/forums/908035/suggestions/32897632).|
|DAC-Import-Assistent|Ein Fehler wurde behoben, bei dem der DAC-Import-Assistent bei einer Verbindung über AAD nicht funktioniert hat.|
|Datenklassifizierung|Ein Problem wurde behoben, das beim Speichern von Klassifizierungen im Datenklassifizierungbereich aufgetreten ist, während gleichzeitig andere Datenklassifizierungsbereiche in anderen Datenbanken geöffnet waren.|
|Datenschichtanwendungs-Assistent|Ein Fehler wurde behoben, durch den Benutzer aufgrund des eingeschränkten Zugriffs auf den Server (z. B. fehlender Zugriff auf alle Datenbanken auf einem Server) keine Datenschichtanwendung (.dacpac) importieren konnten.|
|Datenschichtanwendungs-Assistent|Ein Fehler wurde behoben, durch den der Importvorgang sehr langsam war, wenn viele Datenbanken auf der gleichen Azure SQL Server-Instanz gehostet wurden.|
|Externe Tabellen|Unterstützung für „Rejected_Row_Location“ in der Vorlage, in SMO, IntelliSense, und im Eigenschaftenraster wurde hinzugefügt.|
|Assistent zum Importieren von Flatfiles|Ein Problem wurde behoben, bei dem der Assistent zum Importieren von Flatfiles doppelte Anführungszeichen nicht ordnungsgemäß verarbeitete (mit Escapezeichen versah). Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/32897998](https://feedback.azure.com/forums/908035/suggestions/32897998). |
|Assistent zum Importieren von Flatfiles|Ein Problem in Bezug auf die fehlerhafte Handhabung von Gleitkommatypen (bei Gebietsschemas, die ein anderes Trennzeichen für Gleitkommawerte verwenden) wurde behoben.|
|Assistent zum Importieren von Flatfiles|Ein Problem im Zusammenhang mit dem Importieren von Bits, wenn Werte 0 oder 1 sind, wurde behoben. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535). |
|Assistent zum Importieren von Flatfiles|Ein Problem wurde behoben, bei dem float-Elemente als NULL-Werte eingegeben wurden.|
|Assistent zum Importieren von Flatfiles|Es wurde ein Problem behoben, bei dem der Import-Assistent keine negativen Dezimalwerte verarbeiten konnte.|
|Assistent zum Importieren von Flatfiles|Es wurde ein Problem behoben, bei dem der Assistent keine Importvorgänge aus CSV-Dateien mit einer Spalte durchführen konnte.|
|Assistent zum Importieren von Flatfiles|[Gilt für SSMS 17.9] Ein Problem wurde behoben, bei dem der Import von Flatfiles die Änderung der Zieltabelle nicht erlaubte, wenn die Tabelle bereits vorhanden war. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186](https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186). |
|Help Viewer|Logik zur Berücksichtigung der Online-/Offlinemodi wurde verbessert (möglicherweise müssen noch weitere Probleme behoben werden).|
|Help Viewer|Es wurde eine Korrektur für „Hilfe anzeigen“ zur Berücksichtigung der Online/Offline-Einstellung vorgenommen. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897791). |
|Hochverfügbarkeit und Notfallwiederherstellung (HADR)<BR> Verfügbarkeitsgruppen (AG)|Ein Fehler wurde behoben, bei dem im Assistenten für „Failover für Verfügbarkeitsgruppen“ für Rollen immer der Status „Wird aufgelöst“ angezeigt wurde.|
|Hochverfügbarkeit und Notfallwiederherstellung (HADR)<BR> Verfügbarkeitsgruppen (AG)|Ein Fehler wurde behoben, durch den SSMS abgeschnittene Warnungen im „Dashboard für Verfügbarkeitsgruppen“ angezeigt hat.|
|Integration Services (IS)|Ein SxS-Problem wurde behoben, bei dem der Bereitstellungs-Assistent keine Verbindung mit SQL Server herstellen konnte, wenn SQL Server 2019 und SSMS 18.0 auf demselben Computer installiert waren.|
|Integration Services (IS)|Ein Fehler wurde behoben, durch den der Wartungsplantask beim Entwerfen des Wartungsplans nicht bearbeitet werden konnte.|
|Integration Services (IS)|Ein Problem wurde behoben, bei dem der Bereitstellungs-Assistent nicht fortgesetzt wurde, wenn das Projekt während der Bereitstellung umbenannt wurde.|
|Integration Services (IS)|Die Umgebungseinstellung im Zeitplanfeature von Azure-SSIS IR wurde aktiviert.|
|Integration Services (IS)|Ein Problem wurde behoben, bei dem der Assistent zum Erstellen einer SSIS Integration Runtime nicht mehr reagierte, wenn das Kundenkonto mehr als einem Mandanten gehörte.|
|Auftragsaktivitätsmonitor|Der Absturz beim Verwenden des Auftragsaktivitätsmonitors (mit Filtern) wurde behoben.|
|Objekt-Explorer|Ein Problem wurde behoben, bei dem SSMS die Ausnahme „Ein Objekt kann nicht von DBNull in andere Typen umgewandelt werden“ auslöste, wenn der Knoten „Verwaltung“ im Objekt-Explorer (falsch konfigurierter DataCollector) erweitert wurde.|
|Objekt-Explorer|Ein Problem wurde behoben, bei dem Objekt-Explorer vor dem Aufrufen von „Die ersten n bearbeiten...“ keine Escapezeichen für Anführungszeichen einfügte, wodurch der Entwurf verfälscht wurde.|
|Objekt-Explorer|Ein Problem wurde behoben, bei dem der Assistent zum Importieren der Datenebenenanwendung nicht aus der Azure Storage-Struktur gestartet wurde.|
|Objekt-Explorer|Ein Problem in der Konfiguration von Datenbank-E-Mail wurde behoben, bei dem der Status des Kontrollkästchens „SSL“ nicht beibehalten wurde. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895541). |
|Objekt-Explorer|Ein Problem wurde behoben, bei dem für SSMS die Option zum Schließen vorhandener Verbindungen beim Wiederherstellen der Datenbank mit „is_auto_update_stats_async_on“ ausgeblendet war.|
|Objekt-Explorer|Ein Problem wurde behoben, durch das beim Rechtsklick auf Knoten im Objekt-Explorer, z. B. „Tabellen“ beim Ausführen einer Aktion wie dem Filtern von Tabellen über Filter > Filtereinstellungen, das Formular für Filtereinstellungen auf einem anderen Bildschirm angezeigt werden kann, als dem, auf dem SSMS derzeit aktiv ist. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106](https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106). |
|Objekt-Explorer|Ein lange bestehendes Problem wurde behoben, bei dem die ENTF-TASTE im Objekt-Explorer beim Umbenennen eines Objekts nicht funktionierte. Weitere Informationen finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510](https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510), [https://feedback.azure.com/forums/908035/suggestions/32910247](https://feedback.azure.com/forums/908035/suggestions/32910247) und bei anderen Duplikaten.|
|Objekt-Explorer|Beim Anzeigen der Eigenschaften vorhandener Datenbankdateien wird die Größe in einer Spalte „Größe (MB)“ anstelle von „Anfangsgröße (MB)“ angezeigt, was der Anzeige beim Erstellen einer neuen Datenbank entspricht. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024](https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024). |
|Objekt-Explorer|Der Kontextmenüeintrag „Entwurf“ für „Graph-Tabellen“ wurde deaktiviert, da in der aktuellen Version von SSMS keine Unterstützung für diese Art von Tabelle besteht.|
|Objekt-Explorer|Ein Problem wurde behoben, bei dem das Dialogfeld „Neuer Auftragszeitplan“ auf Monitoren mit hohem DPI-Wert nicht ordnungsgemäß angezeigt wurde. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/admin/v3/suggestions/35541262](https://feedback.azure.com/admin/v3/suggestions/35541262). |
|Objekt-Explorer|Ein Problem wurde behoben bzw. verbessert, bei dem eine Datenbankgröße („Größe (MB)“) in den Details zum Objekt-Explorer angezeigt wurde: Es wurden nur zwei Dezimalstellen angezeigt, und der Wert wurde mithilfe von Tausendertrennzeichen formatiert. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/34379308](https://feedback.azure.com/forums/908035/suggestions/34379308).|
|Objekt-Explorer|Ein Problem wurde behoben, bei dem die Erstellung von „räumlichen Indizes“ zu einem Fehler wie „To accomplish this action, set property PartitionScheme (Legen Sie die Eigenschaft „PartitionScheme“ fest, um diese Aktion auszuführen)“ führte.|
|Objekt-Explorer|Kleine Leistungsverbesserungen wurden am Objekt-Explorer vorgenommen, um weitere Abfragen nach Möglichkeit zu vermeiden.|
|Objekt-Explorer|Logik zum Anfordern einer Bestätigung beim Umbenennen einer Datenbank für alle Schemaobjekte wurde erweitert (die Einstellung kann konfiguriert werden).|
|Objekt-Explorer|Die richtigen Escapezeichen wurden in die Filterung des Objekt-Explorers hinzugefügt. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/36678803](https://feedback.azure.com/forums/908035/suggestions/36678803). |
|Objekt-Explorer|Die Ansicht in den Details zum Objekt-Explorer wurde verbessert bzw. Fehler wurden behoben, um Zahlen mit geeigneten Trennzeichen anzuzeigen. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/32900944](https://feedback.azure.com/forums/908035/suggestions/32900944). |
|Objekt-Explorer|Ein Problem innerhalb des Kontextmenüs im Knoten „Tabellen“ bei einer Verbindung mit SQL Express wurde behoben, bei dem das Flyoutmenü „Neu“ fehlte, Graph-Tabellen fehlerhaft aufgelistet wurden und die Tabelle mit Systemversionsverwaltung fehlte. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/37245529](https://feedback.azure.com/forums/908035/suggestions/37245529). |
|Skripterstellung für Objekte|Allgemeine Leistungsverbesserungen: Das Generieren von Skripts von „WideWorldImporters“ dauert nur die Hälfte die Zeit im Vergleich zu SSMS 17.7.|
|Skripterstellung für Objekte|Bei der Skripterstellung für Objekte wird die datenbankbezogene Konfiguration, die Standardwerte aufweist, ausgelassen.|
|Skripterstellung für Objekte|Generieren Sie bei der Skripterstellung kein dynamisches T-SQL. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898391). |
|Skripterstellung für Objekte|Lassen Sie die Graph-Syntax „as edge“ und „as node“ bei der Skripterstellung für eine Tabelle unter SQL Server 2016 und früheren Versionen aus.|
|Skripterstellung für Objekte|Ein Problem wurde behoben, bei dem die Skripterstellung von Datenbankobjekten beim Verbinden mit einer Azure SQL-Datenbank über AAD mit MFA fehlschlug.|
|Skripterstellung für Objekte|Ein Problem wurde behoben, bei dem bei der Skripterstellung eines räumlichen Index mit „GEOMETRY_AUTO_GRID/GEOGRAPHY_AUTO_GRID“ in einer Azure SQL-Datenbank ein Fehler ausgelöst wurde.|
|Skripterstellung für Objekte|Ein Problem wurde behoben, bei dem die Skripterstellung einer (Azure SQL-)Datenbank immer lokale SQL-Instanzen als Ziel verwendete, auch wenn die Skripteinstellungen im Objekt-Explorer mit der Quelle übereinstimmten.|
|Skripterstellung für Objekte|Ein Problem bei der Skripterstellung einer Tabelle in einer Azure SQL Data Warehouse-Datenbank mit gruppierten und nicht gruppierten Indizes wurde behoben, das zu fehlerhaften T-SQL-Anweisungen geführt hat.|
|Skripterstellung für Objekte|Ein Problem bei der Skripterstellung einer Tabelle in einer Azure SQL Data Warehouse-Datenbank mit gruppierten Columnstore-Indizes und gruppierten Indizes wurde behoben, das zu fehlerhaften T-SQL-Anweisungen geführt hat (doppelte Anweisungen).|
|Skripterstellung für Objekte|Ein Problem bei der Skripterstellung von Partitionstabellen ohne Bereichswerte (Azure SQL Data Warehouse-Datenbanken) wurde behoben.|
|Skripterstellung für Objekte|Ein Problem wurde behoben, bei dem der Benutzer kein Skript für die Überwachung/Überwachungsspezifikation „SERVER_PERMISSION_CHANGE_GROUP“ erstellen konnte.|
|Skripterstellung für Objekte|Ein Problem wurde behoben, bei dem der Benutzer kein Skript für Statistiken aus Azure SQL Data Warehouse erstellen konnte. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32897296](https://feedback.azure.com/forums/908035-sql-server/suggestions/32897296). |
|Skripterstellung für Objekte|Ein Problem wurde behoben, bei dem der Assistent zum Generieren von Skripts eine fehlerhafte Tabelle mit Skriptfehlern anzeigte, wenn „Skripterstellung bei einem Fehler fortsetzen“ auf FALSE festgelegt war.|
|Skripterstellung für Objekte|Die Skriptgenerierung in SQL Server 2019 wurde verbessert.|
|Profiler|Das Ereignis „Aggregate Table Rewrite Query“ (Abfrage zum erneuten Generieren von Aggregattabellen) wurde den Profiler-Ereignissen hinzugefügt.|
|Abfragedatenspeicher|Ein Problem wurde behoben, bei dem eine Ausnahme „DocumentFrame (SQLEditors)“ ausgelöst werden konnte.|
|Abfragedatenspeicher|Ein Problem wurde behoben, das bei dem Versuch aufgetreten ist, ein benutzerdefiniertes Zeitintervall in dem integrierten Abfragespeicher festzulegen, und bei dem der Benutzer AM oder PM für das Start/Ende-Intervall nicht auswählen konnte.|
|Ergebnisraster|Ein Problem wurde behoben, durch das der Modus für hohen Kontrast ausgelöst wurde (ausgewählte Zeilennummern nicht sichtbar).|
|Ergebnisraster|Ein Fehler wurde behoben, durch den die Ausnahme „Der Index liegt außerhalb des Bereichs“ ausgelöst wurde, wenn auf das Raster geklickt wurde.|
|Ergebnisraster|Ein Fehler wurde behoben, durch den die Hintergrundfarbe des Ergebnisrasters ignoriert wurde. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/32895916](https://feedback.azure.com/forums/908035/suggestions/32895916). |
|Showplan|Neue Operatoreigenschaften für die Speicherzuweisung werden nicht korrekt angezeigt, wenn es mehr als einen Thread gibt.|
|Showplan|Fügen Sie die folgenden 4 Attribute im RunTimeCountersPerThread-Element eines tatsächlichen XML-Ausführungsplans hinzu: HpcRowCount (Anzahl der vom HPC-Gerät verarbeiteten Zeilen), HpcKernelElapsedUs (verstrichene Wartezeit für die aktive Kernelausführung), HpcHostToDeviceBytes (Bytes die vom Host an das Gerät übertragen werden) und HpcDeviceToHostBytes (Bytes die vom Gerät an den Host übertragen werden).|
|Showplan|Ein Problem wurde behoben, bei dem die Knoten für ähnliche Pläne an der falschen Stelle markiert wurden.|
|SMO|Ein Problem wurde behoben, bei dem SMO/ServerConnection SqlCredential-basierte Verbindungen nicht richtig verarbeitete. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941](https://feedback.azure.com/forums/908035-sql-server/suggestions/33698941). |
|SMO|Ein Problem wurde behoben, bei dem in einer mit SMO geschriebenen Anwendung ein Fehler auftrat bei dem Versuch, Datenbanken vom gleichen Server in mehreren Threads aufzulisten, obwohl sie separate SqlConnection-Instanzen in jedem Thread verwendet.|
|SMO|Der Leistungsverlust beim Übertragen aus externen Tabellen wurde behoben.|
|SMO|Ein Problem mit ServerConnection bei der Threadsicherheit wurde behoben, das dazu geführt hat, dass SMO SqlConnection-Instanzen freigegeben hat, wenn Azure als Ziel verwendet wurde.|
|SMO|Ein Problem wurde behoben, das beim Wiederherstellen einer Datenbank mit geschweiften Klammern im Namen zum Fehler „StringBuilder.FormatError“ geführt hat.|
|SMO|Ein Problem wurde behoben, bei dem Azure-Datenbanken in SMO standardmäßig die Sortierung ohne Beachtung von Groß-/Kleinschreibung für alle Zeichenfolgenvergleiche anstelle der für die Datenbank festgelegte Sortierung verwendeten.|
|SSMS-Editor|Ein Problem in „SQL-Systemtabelle“ wurde behoben, bei dem beim Wiederherstellen der Standardfarben die Farbe in Limonengrün anstelle von Standardgrün geändert wurde, wodurch Text auf weißen Hintergrund nur schwer lesbar war. Weitere Informationen finden Sie unter [Restoring wrong default color for SQL System Table (Wiederherstellen der falschen Standardfarbe in SQL-Systemtabellen)](https://feedback.azure.com/forums/908035-sql-server/suggestions/32896906). Das Problem besteht weiterhin in nicht englischsprachigen SSMS-Versionen.|
|SSMS-Editor|Es wurde ein Problem behoben, durch das IntelliSense während der Verbindung mit Azure SQL Data Warehouse mithilfe der AAD-Authentifizierung nicht funktioniert hat.|
|SSMS-Editor|Ein Problem für IntelliSense in Azure wurde behoben, wenn der Benutzer keinen Zugriff auf die **Masterdatenbank** besitzt.|
|SSMS-Editor|Codeausschnitte zum Erstellen „temporaler Tabellen“ wurden behoben, die fehlerhaft waren, wenn die Groß-/Kleinschreibung bei der Sortierung der Zieldatenbank beachtet wurde.|
|SSMS-Editor|Die neue TRANSLATE-Funktion wird nun von IntelliSense erkannt. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898430). |
|SSMS-Editor|IntelliSense wurde für die integrierte FORMAT-Funktion verbessert. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898676). |
|SSMS-Editor|LAG und LEAD werden nun als integrierte Funktionen erkannt. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898757). |
|SSMS-Editor|Ein Problem wurde behoben, bei dem IntelliSense bei der Verwendung von „ALTER TABLE...ADD CONSTRAINT...WITH(ONLINE=ON)“ eine Warnung ausgab.|
|SSMS-Editor|Ein Fehler wurde behoben, durch den mehrere Systemsichten und Tabellenwertfunktionen nicht ordnungsgemäß farbig hervorgehoben wurden.|
|SSMS-Editor|Ein Problem wurde behoben, bei dem durch Klicken auf Editor-Registerkarten die Registerkarte geschlossen wurde anstatt den Fokus zu erhalten. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/37291114](https://feedback.azure.com/forums/908035/suggestions/37291114). |
|SSMS-Optionen|Ein Problem wurde behoben, bei dem die Größe der Seite **Extras** > **Optionen** > **SQL Server-Objekt-Explorer** > **Befehle** nicht ordnungsgemäß geändert wurde.|
|SSMS-Optionen|SSMS deaktiviert nun standardmäßig das automatische Herunterladen von Dokumenttypdefinitionen (DTD) im XMLA-Editor: Der XMLA-Skript-Editor (der den XML-Sprachdienst verwendet) verhindert nun standardmäßig das automatische Herunterladen von DTD für potenziell schädliche XMLA-Dateien. Dies wird gesteuert durch Deaktivieren der Einstellung „DTDs und Schemas automatisch herunterladen“, die unter **Extras** > **Optionen** > **Umgebung** > **Text-Editor** > **XML** > **Sonstiges** festgelegt wird.|
|SSMS-Optionen|Die Funktion der Tastenkombination **STRG+D** aus früheren Versionen von SSMS wurde wiederhergestellt. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/35544754](https://feedback.azure.com/forums/908035/suggestions/35544754). |
|Tabellen-Designer|Ein Absturz bei „200 Zeilen bearbeiten“wurde behoben.|
|Tabellen-Designer|Ein Problem wurde behoben, bei dem der Designer es zuließ, dass eine Tabelle während der Verbindung mit einer Azure SQL-Datenbank hinzugefügt wurde.|
|Sicherheitsrisikobewertung|Ein Problem wurde behoben, bei dem die Überprüfungsergebnisse nicht ordnungsgemäß geladen wurden.|
|XEvent|Die beiden Spalten „action_name“ und „class_type_desc“ wurden hinzugefügt, in denen die Felder für Aktions-ID und Klassentyp als lesbare Zeichenfolgen angezeigt werden.|
|XEvent|Die Obergrenze in XEvent-Viewer von 1.000.000 Ereignissen wurde entfernt.|
|XEvent-Profiler|Ein Problem wurde behoben, bei dem der XEvent-Profiler während der Verbindung mit einem 96-Kern-SQL-Server nicht starten konnte.|
|XEvent-Viewer|Ein Problem wurde behoben, bei dem XEvent-Viewer abgestürzt ist, wenn die Ereignisse mit den „erweiterten Symbolleistenoptionen für Ereignisse“ gruppiert wurden.|

### <a name="deprecated-and-removed-features-in-180"></a>Veraltete und entfernte Funktionen in Version 18.0

Veraltete/entfernte Funktionen
- T-SQL-Debugger
- Datenbankdiagramme
- Die folgenden Tools werden nicht mehr mit SSMS installiert:
  - OSQL.EXE
  - DReplay.exe
  - SQLdiag.exe
  - SSBDiagnose.exe
  - bcp.exe
  - sqlcmd.exe
- Konfigurations-Manager-Tools:
  - Sowohl SQL Server-Konfigurations-Manager als auch Reporting Server-Konfigurations-Manager sind nicht mehr Teil des SSMS-Setups.
- DMF-Standardrichtlinien
  - Die Richtlinien werden nicht mehr mit SSMS installiert. Sie werden in Git verschoben. Benutzer können auf Wunsch daran mitwirken und sie herunterladen/installieren.
- Die SSMS-Befehlszeilenoption „-P“ wurde entfernt.
  - Aus Sicherheitsgründen wurde die Option zum Angeben von Klartextkennwörtern in der Befehlszeile entfernt.
- Die Funktion „Skripts generieren“ > „In Webdienst veröffentlichen“ wurde entfernt.
  - Diese veraltete Funktion wurde von der SSMS-Benutzeroberfläche entfernt.
- Der Knoten „Wartung“ > „Legacy“ im Objekt-Explorer wurde entfernt.
  - Auf die alten Knoten „Datenbank-Wartungsplan“ und „SQL Mail“ kann nicht mehr zugegriffen werden. Die zeitgemäßen Knoten „Datenbank-E-Mail“ und „Wartungspläne“ funktionieren weiterhin wie gewohnt.

### <a name="known-issues-180"></a>Bekannte Probleme (18.0)

- Bei der Installation von Version 18.0 tritt möglicherweise ein Probleme auf, durch das Sie SQL Server Management Studio nicht ausführen können. Führen Sie die im Artikel [SSMS2018 – Installed, but will not run (SSMS 2018 – Installiert, kann aber nicht ausgeführt werden)](https://feedback.azure.com/forums/908035-sql-server/suggestions/37502512-ssms2018-installed-but-will-not-run) beschriebenen Schritte aus, wenn dieses Problem auftritt.

## <a name="downloadssdtmediadownloadpng-ssms-1791httpsgomicrosoftcomfwlinklinkid2043154clcid0x409"></a>![Herunterladen von](../ssdt/media/download.png) [SSMS 17.9.1](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)

- Releasenummer: 17.9.1<br>
- Buildnummer: 14.0.17289.0<br>
- Releasedatum: 21. November 2018

17.9.1 ist ein kleines Update für 17.9 mit die folgenden Fehlerbehebungen:

- Korrektur für folgenden Fehler: Bei Verwendung des Authentifizierungstyps „Active Directory: Universell mit MFA-Unterstützung“ für den SQL-Abfrage-Editor stellen Benutzer möglicherweise fest, dass die Verbindung bei jedem Aufruf der Abfrage geschlossen und erneut geöffnet wird. Nebeneffekte eines solchen Schließens der Verbindung sind u. a., dass globale temporäre Tabellen unerwartet gelöscht werden und mitunter der Verbindung eine neue SPID gegeben wird.
- Ein seit langem bestehendes Problem wurde behoben, bei dem der Wiederherstellungsplan keinen Wiederherstellungsplan finden konnte oder unter bestimmten Bedingungen einen ineffizienten Wiederherstellungsplan generieren konnte.
- Ein Problem im Assistenten „Datenschichtanwendung importieren“ wurde behoben, das bei der Verbindung mit einer Azure SQL-Datenbank einen Fehler verursachen konnte.

> [!NOTE]
> In andere Sprachen als Englisch lokalisierte Releases von SSMS 17.x benötigen das [KB 2862966-Sicherheitsupdatepaket](https://support.microsoft.com/kb/2862966) für die Installation unter den folgenden Windows-Systemen: Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2.

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)

## <a name="downloadssdtmediadownloadpng-ssms-179httpsgomicrosoftcomfwlinklinkid2014306clcid0x409"></a>![Download](../ssdt/media/download.png) [SSMS 17.9](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)

Buildnummer: 14.0.17285.0<br>
Releasedatum: 4. September 2018

> [!NOTE]
> In andere Sprachen als Englisch lokalisierte Releases von SSMS 17.x benötigen das [KB 2862966-Sicherheitsupdatepaket](https://support.microsoft.com/kb/2862966) für die Installation unter den folgenden Windows-Systemen: Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2.

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=2014306&clcid=0x40a)

### <a name="whats-new"></a>Neues

**SSMS Allgemein**

Showplan:

- Der grafische Showplan zeigt jetzt die Attribute des Feedbacks zur Speicherzuweisung im Zeilenmodus an, wenn die Funktion für einen bestimmten Plan aktiviert ist: Dem Abfrageplan-XML-Element „MemoryGrantInfo“ wurde „IsMemoryGrantFeedbackAdjusted“ und „LastRequestedMemory“ hinzugefügt. Weitere Informationen zum Feedback zur Speicherzuweisung im Zeilenmodus finden Sie unter [Adaptive Abfrageverarbeitung in SQL-Datenbanken](https://docs.microsoft.com/sql/relational-databases/performance/adaptive-query-processing).

Azure SQL:

- Unterstützung für V-Kern-SKUs bei der Erstellung von Azure-Datenbanken hinzugefügt. Weitere Informationen finden Sie unter [Auf virtuellen Kernen basierendes Erwerbsmodell](https://docs.microsoft.com/azure/sql-database/sql-database-service-tiers#vcore-based-purchasing-model).
 

### <a name="bug-fixes"></a>Behebung von Programmfehlern

**SSMS Allgemein**

Replikationsmonitor:

- Ein Fehler, der den Start des Replikationsmonitors (SqlMonitor.exe) verhindert hat, wurde behoben (Zugehöriges Benutzerfeedback: https://feedback.azure.com/forums/908035-sql-server/suggestions/34791079).

Assistent zum Importieren von Flatfiles:

- Der Link zur Hilfeseite für das Dialogfeld des Flatfile-Assistenten wurde korrigiert. 
- Ein Problem, durch das der Assistent das Ändern der Zieltabelle untersagte, wenn diese bereits vorhanden war, wurde behoben. Auf diese Weise können Benutzer den Vorgang wiederholen und müssen den Assistenten nicht beenden, die fehlerhafte Tabelle löschen und die Informationen erneut im Assistenten eingeben. (Zugehöriges Benutzerfeedback: https://feedback.azure.com/forums/908035-sql-server/suggestions/32896186).

Importieren/Exportieren einer Datenebenenanwendung:

- Ein Problem (in DacFx), das zu einem Fehler beim Import einer BACPAC-Datei mit der folgenden Meldung geführt hat, wurde behoben: „Error SQL72014: .Net SqlClient Data Provider: Msg 9108, Level 16, State 10, Line 1 This type of statistics is not supported to be incremental.“ (Fehler SQL72014: .NET SqlClient-Datenanbieter: Meldung 9108, Ebene 16, Zustand 10, Zeile 1: Dieser Statistiktyp wird nicht als inkrementell unterstützt. Das Problem trat bei Tabellen auf, für die Partitionen definiert waren, aber die keine Indizes für die Tabelle umfassten.

IntelliSense:

- Ein Problem, das bei der Verwendung von AAD mit MFA zu einer nicht funktionierenden IntelliSense-Vervollständigung führte, wurde behoben.

Objekt-Explorer:

- Ein Problem, das zur Anzeige des Filterdialogfelds auf willkürlichen Monitoren anstelle des Monitors mit Ausführung von SSMS führte, wurde behoben (Systeme mit mehreren Monitoren).

Azure SQL:

- Ein Problem in Bezug auf die Auflistung von Datenbanken in „Verfügbare Datenbanken“, durch das „master“ während der Verbindung mit einer bestimmten Datenbank nicht in der Dropdownliste angezeigt wurde, wurde behoben.
- Ein Problem, durch das ein Skript („Daten“ oder „Schema und Daten“) während der Verbindung mit der Azure SQL-Datenbank über AAD mit MFA nicht generiert werden konnte, wurde behoben.
- Ein Problem im Sicht-Designer (Ansichten), durch das während der Verbindung mit einer Azure SQL-Datenbank eine Auswahl von „Tabellen hinzufügen“ aus der Benutzeroberfläche nicht möglich war, wurde behoben.
- Ein Problem, durch das der SSMS-Abfrage-Editor Verbindungen während der MFA-Tokenerneuerung automatisch schloss und wieder öffnete, wurde behoben. Dadurch werden Nebeneffekte vermieden, die vom Benutzer unbemerkt auftreten (z.B. das Schließen einer Transaktion, ohne sie erneut zu öffnen). Mit der Änderung wird die Tokenablaufzeit zum Eigenschaftenfenster hinzugefügt. 
- Ein Problem, durch das SSMS keine Kennwortaufforderungen für importierte MSA-Konten für AAD mit MFA-Anmeldung erzwang, wurde behoben. 

Aktivitätsmonitor:

- Ein Problem, durch das die „Live-Abfragestatistik“ einfror, wenn sie über den Aktivitätsmonitor gestartet und mit der SQL-Authentifizierung verwendet wurde, wurde behoben. 

Microsoft Azure-Integration: 

- Ein Problem wurde behoben, bei dem SSMS nur die ersten fünfzig Abonnements anzeigte (Always Encrypted-Dialogfelder, Dialogfelder zur Sicherung/Wiederherstellung aus einer URL und weitere Dialogfelder).
- Ein Problem wurde behoben, das (im Dialogfeld zur Sicherung/Wiederherstellung aus einer URL) beim Versuch der Anmeldung mit einem Microsoft Azure-Konto ohne Speicherkonto zu einer SSMS-Ausnahme („Index außerhalb des gültigen Bereichs“) führte. 

Skripterstellung für Objekte:

- Bei der Skripterstellung mit DROP und CREATE vermeidet SSMS jetzt das Generieren von dynamischem T-SQL.
- Bei der Skripterstellung für ein Datenbankobjekt generiert SSMS ab sofort kein Skript zum Festlegen von datenbankweiten Konfigurationen, wenn die Standardwerte verwendet werden.

Help:

- Ein lange bestehendes Problem, durch das die „Hilfe zur Hilfe“ den Online-/Offlinemodus nicht berücksichtigte, wurde behoben.
- Wenn Sie auf „Hilfe | Community-Projekte und Beispiele“ klicken, öffnet SSMS jetzt den Standardbrowser, der auf eine Git-Seite zeigt, und es werden keine Fehler/Warnungen aufgrund der Verwendung eines alten Browsers anzeigt.

### <a name="known-issues"></a>Bekannte Probleme

> [!IMPORTANT]
> Bei Verwendung des Authentifizierungstyps *Active Directory: Universell mit MFA-Unterstützung* für den SQL-Abfrage-Editor stellen Benutzer möglicherweise fest, dass die Verbindung bei jedem Aufruf der Abfrage geschlossen und erneut geöffnet wird. Nebeneffekte eines solchen Schließens sind unter anderem, dass globale temporäre Tabellen unerwartet gelöscht werden und manchmal der Verbindung eine neue SPID gegeben wird. Ein solches Schließen tritt nicht auf, wenn die Verbindung eine offene Transaktion aufweist. Um dieses Problem zu umgehen, können Benutzer `persist security info=true` in den Verbindungsparametern festlegen.

## <a name="downloadssdtmediadownloadpng-ssms-1781httpsgomicrosoftcomfwlinklinkid875802"></a>![Herunterladen von](../ssdt/media/download.png) [SSMS 17.8.1](https://go.microsoft.com/fwlink/?linkid=875802)
*In der Version 17.8 wurde im Zusammenhang mit der Bereitstellung von SQL-Datenbanken ein Fehler festgestellt. Daher wird die Version 17.8 durch SSMS 17.8.1 ersetzt.*

Buildnummer: 14.0.17277.0<br>
Releasedatum: 26. Juni 2018

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=875802&clcid=0x40a)

### <a name="whats-new"></a>Neues

**SSMS Allgemein**

Datenbankeigenschaften:

- Durch diese Verbesserung wird die Konfigurationsoption **AUTOGROW_ALL_FILES** für Dateigruppen verfügbar gemacht. Diese neue Konfigurationsoption wurde unter „Datenbankeigenschaften“ > Fenster „Dateigruppen“ hinzugefügt und zwar in Form einer neuen Spalte („Autogrow All Files“) mit Kontrollkästchen für jede verfügbare Dateigruppe (mit Ausnahme der Dateigruppen „Filestream“ und „Speicheroptimiert“). Der Benutzer kann AUTOGROW_ALL_FILES für eine bestimmte Dateigruppe über das entsprechende Kontrollkästchen unter „Autogrow_All_Files“ aktivieren oder deaktivieren. Dementsprechend wird für die Option **AUTOGROW_ALL_FILES** ordnungsgemäß ein Skript erstellt, wenn Skripts für die Datenbank für CREATE erstellt oder Skripts für die Datenbank (SQL 2016 und höher) generiert werden.

SQL-Editor:

- Die Benutzeroberfläche wurde durch IntelliSense-Funktionen in Azure SQL-Datenbank verbessert, wenn der Benutzer keinen Masterzugriff besitzt.

Skripterstellung:

- Es wurden allgemeine Leistungsverbesserungen vorgenommen, insbesondere über Verbindungen mit hoher Latenz.

**Analysis Services (AS)**

- Analysis Services-Clientbibliotheken und -Datenanbieter wurden auf die neuste Version aktualisiert, die um Unterstützung für die neue Azure Government-AAD-Autorität (login.microsoftonline.us) erweitert wurden.

### <a name="bug-fixes"></a>Behebung von Programmfehlern

**SSMS Allgemein**

Wartungspläne:

- Das Problem, dass beim Task „Operator benachrichtigen“ mit SQL-Authentifizierung ein Fehler auftrat, wenn Wartungspläne mit SQL-Authentifizierung bearbeitet wurden, wurde behoben.
    
Skripterstellung:

- Das Problem, dass PostProcess-Aktionen in SMO zur Ressourcenauslastung und zu Fehlern bei der SQL-Anmeldung führen, wurde behoben.
    
SMO:

- Das Problem, dass bei Verwendung von Table.Alter() ein Fehler auftritt, wenn eine Spalte mit einer DEFAULT-Einschränkung hinzugefügt wird und die Tabelle bereits Daten enthält, wurde behoben. Einzelheiten finden Sie im Forenbeitrag zu der [in SQL Server Management Objects generierten DEFAULT-Inlineeinschränkung beim Hinzufügen einer Spalte zu einer Tabelle mit Daten](https://feedback.azure.com/forums/908035-sql-server/suggestions/32895625).
    
Always Encrypted:

- Das Problem, dass bei der Aktivierung von Always Encrypted für eine partitionierte Tabelle ein Sperrtimeoutfehler (in DACFx) verursacht wurde, wurde behoben.
    

**Analysis Services (AS)**

- Das Problem, dass beim Ändern einer OAuth-Datenquelle in einem tabellarischen Analysis Services-Modell mit einem Kompatibilitätsgrad von 1400 die Änderungen in den OAuth-Token nicht in der Datenquelle aktualisiert wurden, wurde behoben.
- Das Problem, dass SSMS eventuell abstürzte, wenn bestimmte ungültige Anmeldeinformationen für die Datenquelle verwendet oder Datenquellen ohne Unterstützung für die Migration mit „Datenquelle ändern“ in Power Query (z.B. Oracle) in tabellarischen Analysis Services-Modellen mit einem Kompatibilitätsgrad von 1400 bearbeitet wurden, wurde behoben.


### <a name="known-issues"></a>Bekannte Probleme

- Wenn Sie auf die Schaltfläche *Skript* klicken, nachdem eine der Dateigruppeneigenschaften im Fenster *Eigenschaften* geändert wurde, werden zwei Skripts generiert: ein Skript mit einer *USE <database>* -Anweisung und ein zweites Skript mit einer *USE master*-Anweisung.  Beim Generieren des Skripts mit *USE master* tritt ein Fehler auf. Es sollte daher verworfen werden. Führen Sie das Skript aus, das die *USE <database>* -Anweisung enthält.
- In einigen Dialogfeldern wird ein Fehler wegen ungültiger Edition angezeigt, wenn mit einer der neuen Azure SQL-Datenbank-Editionen *Allgemein* oder *Unternehmenskritisch* gearbeitet wird.
- Beim XEvents-Viewer lassen sich möglicherweise Latenzen feststellen. Dies ist ein [bekanntes Problem im .NET Framework](https://github.com/Microsoft/dotnet/blob/master/releases/net472/dotnet472-changes.md#sql). Erwägen Sie ein Upgrade auf NetFx 4.7.2.




## <a name="downloadssdtmediadownloadpng-ssms-177httpsgomicrosoftcomfwlinklinkid873126"></a>![SSMS 17.7](../ssdt/media/download.png) [herunterladen](https://go.microsoft.com/fwlink/?linkid=873126)

Buildnummer: 14.0.17254.0<br>
Releasedatum: 09. Mai 2018

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=873126&clcid=0x40a)


### <a name="whats-new"></a>Neues

**SSMS Allgemein**

Replikationsmonitor:   
- Der Replikationsmonitor unterstützt jetzt das Registrieren eines Listeners für Szenarien, in denen die Verlegerdatenbank und/oder die Verteilerdatenbank zur Verfügbarkeitsgruppe gehören. Sie können nun Replikationsumgebungen überwachen, in denen die Verlegerdatenbank und/oder die Verteilerdatenbank zu Always On gehören. 
 
Azure SQL Data Warehouse: 
- Unterstützung für „Speicherort abgelehnter Zeilen“ wurde für externe Tabellen in SQL Data Warehouse hinzugefügt. 

**Integration Services**

- Es wurde ein Planungsfeature für SSIS-Pakete hinzugefügt, die in Azure SQL-Datenbank bereitgestellt werden. Im Gegensatz zu lokaler SQL Server-Infrastruktur und zur verwalteten Azure SQL-Datenbank-Instanz, die SQL Server-Agent als erstklassigen Auftragsplaner umfassen, hat SQL-Datenbank keinen integrierten Planer. Dieses neue SSMS-Feature bietet eine vertraute Benutzeroberfläche, die SQL Server-Agent sehr ähnlich ist, zum Planen von Paketen, die in SQL-Datenbank bereitgestellt werden. Wenn Sie die SSIS-Katalogdatenbank (SSISDB) mit SQL-Datenbank hosten, können Sie dieses SSMS-Feature verwenden, um die Data Factory-Pipelines, -Aktivitäten und -Trigger zu generieren, die zum Planen von SSIS-Paketen erforderlich sind. Sie können diese Objekte dann in Data Factory bearbeiten und erweitern. Weitere Informationen finden Sie unter [Planen der Ausführung eines SSIS-Pakets in Azure SQL-Datenbank mit SQL Server Management Studio (SSMS)](../integration-services/lift-shift/ssis-azure-schedule-packages-ssms.md). Weitere Informationen zu Azure Data Factory-Pipelines, -Aktivitäten und -Triggern finden Sie unter [Pipelines und Aktivitäten in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipelines-activities) und [Pipelineausführung und Trigger in Azure Data Factory](https://docs.microsoft.com/azure/data-factory/concepts-pipeline-execution-triggers).
- Unterstützung für SSIS-Paketplanung in SQL-Agent in verwalteter SQL-Instanz. Es ist jetzt möglich, SQL-Agent-Aufträge zu erstellen, um SSIS-Pakete für die verwaltete Instanz auszuführen. 

### <a name="bug-fixes"></a>Behebung von Programmfehlern

**SSMS Allgemein** 

Wartungsplan:   
- Beheben eines Problems, bei dem bei dem Versuch, den Zeitplan für einen vorhandenen Wartungsplan zu ändern, eine Ausnahme ausgelöst wurde. Ausführlichere Informationen finden Sie unter [SSMS 17.6 crashes when clicking on a schedule in a maintenance plan](https://feedback.azure.com/forums/908035-sql-server/suggestions/33712924).

Always On: 
- Es wurde ein Problem behoben, bei dem das Always On-Dashboard für Latenzzeit nicht mit SQL Server 2012 funktioniert hat.
 
Skripterstellung: 
- Beheben eines Problems, bei dem ein Nicht-Administratorbenutzer gespeicherte Prozeduren für Azure SQL Data Warehouse nicht als Skripts erstellen konnte.
- Es wurde ein Fehler behoben, bei dem bei der Skripterstellung einer Datenbank für Azure SQL-Datenbank die *SCOPED CONFIGURATION*-Eigenschaften nicht einbezogen wurden.
 
Telemetrie: 
- Beheben eines Problems, bei dem SSMS abstürzt, wenn das Herstellen einer Verbindung mit einem Server versucht wird, nachdem das Abonnement für Senden von Telemetriedaten gekündigt wurde.
 
Azure SQL-Datenbank: 
- Es wurde ein Problem behoben, bei dem der Benutzer den Kompatibilitätsgrad weder festlegen noch oder ändern konnte (die Dropdownliste war leer). Der Benutzer muss weiterhin die Schaltfläche *Skript* verwenden und das Skript manuell bearbeiten, um den Kompatibilitätsgrad auf 150 festzulegen. 
 
SMO: 
- Verfügbar gemachte Einstellung für Fehlerprotokollgröße in SMO. Ausführliche Informationen finden Sie unter [Set the Maximum Size of the SQL Server Error Logs](https://feedback.azure.com/forums/908035-sql-server/suggestions/33624115).  
- Korrigieren von Zeilenvorschub bei der Skripterstellung in SMO unter Linux.
- Verschiedene Leistungsverbesserungen für das Abrufen von selten verwendeten Eigenschaften.  

IntelliSense: 
- Leistungsverbesserung: Verringerte Menge von IntelliSense-Abfragen für Spaltendaten. Dies ist besonders nützlich, wenn mit Tabellen gearbeitet wird, die eine sehr große Anzahl von Spalten haben. 

SSMS-Benutzereinstellungen:
- Es wurde ein Problem behoben, bei dem die Größenänderung der Seite für Optionen nicht ordnungsgemäß funktionierte.

Verschiedenes:  
- Verbesserung der Art und Weise, wie Text auf Seite für *Statistikdetails* angezeigt wird. 

**Integration Services**

- Bessere Unterstützung für die verwaltete Azure SQL-Datenbank-Instanz.
- Beheben eines Problems, bei dem der Benutzer keinen Katalog für SQL Server 2014 oder früher erstellen konnte.
- Beheben von zwei Probleme mit Berichten:
   - Die Computernamen für Azure-Server wurden entfernt.
   - Die Verarbeitung von lokalisierten Objektnamen wurde verbessert.


### <a name="known-issues"></a>Bekannte Probleme

In einigen Dialogfeldern wird ein Fehler wegen ungültiger Edition angezeigt, wenn mit einer der neuen Azure SQL-Datenbank-Editionen *Allgemein* oder *Unternehmenskritisch* gearbeitet wird.

## <a name="downloadssdtmediadownloadpng-ssms-176httpsgomicrosoftcomfwlinklinkid870039"></a>![Herunterladen](../ssdt/media/download.png) [SSMS 17.6](https://go.microsoft.com/fwlink/?linkid=870039)

Buildnummer: 14.0.17230.0<br>
Releasedatum: 20. März 2018

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=870039&clcid=0x40a)

### <a name="whats-new"></a>Neues

**SSMS Allgemein**

Verwaltete SQL-Datenbank-Instanz:

- Unterstützung für die [verwaltete Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance). Die verwaltete Azure SQL-Datenbank-Instanz bietet nahezu 100 % Kompatibilität mit SQL Server in einer lokalen Umgebung. Außerdem sorgt sie für Konformität mit einer nativen [VNet](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)-Implementierung (Azure Virtual Network), die Lösungen für allgemeine Sicherheitsprobleme bereitstellt, und mit einem [Geschäftsmodell](https://azure.microsoft.com/pricing/details/sql-database/), das für Kunden von SQL Server in einer lokalen Umgebung geeignet ist.
- Unterstützung für folgende geläufige Verwaltungsszenarios:
   - Erstellen und Ändern von Datenbanken
   - Sichern und Wiederherstellen von Datenbanken
   - Importieren, Exportieren, Extrahieren und Veröffentlichen von Datenschichtanwendungen
   - Aufrufen und Ändern von Servereigenschaften
   - Vollständige Unterstützung des Objekt-Explorers
   - Erstellen von Skripts für Datenbankobjekte
   - Unterstützung von SQL-Agentaufträgen
   - Unterstützung von Verbindungsservern
- Weitere Informationen zu [verwalteten Instanzen](https://azure.microsoft.com/blog/migrate-your-databases-to-a-fully-managed-service-with-azure-sql-database-managed-instance/)

Objekt-Explorer:
- neue Einstellungen, durch die verhindert wird, dass Klammern am Anfang und Ende von Namen gesetzt werden, wenn Elemente per Drag & Drop vom Objekt-Explorer in das Abfragefenster verschoben werden (siehe Benutzervorschläge [32911933](https://feedback.azure.com/forums/908035-sql-server/suggestions/32911933) und [32671051](https://feedback.azure.com/forums/908035-sql-server/suggestions/32671051))

Datenklassifizierung:
- allgemeine Verbesserungen und Fehlerbehebungen

**Integration Services**

- Unterstützung für die Bereitstellung von Paketen in einer [verwalteten SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)

### <a name="bug-fixes"></a>Behebung von Programmfehlern

**SSMS Allgemein**

Datenklassifizierung:

- Ein Problem in der *Datenklassifizierung* wurde behoben. Durch dieses wurden für neu hinzugefügte Klassifizierungen ein veralteter *Informationstyp* und eine veraltete *Vertraulichkeitsbezeichnung* angezeigt.
- Ein Problem wurde behoben, durch das die *Datenklassifizierung* bei Servern nicht funktionierte, für die eine Sortierung unter Berücksichtigung der Groß-/Kleinschreibung verwendet wurde.
        
Always On:

- Ein Problem im Zusammenhang mit der Option „Dashboard anzeigen“ für Verfügbarkeitsgruppen wurde behoben. Durch dieses wurde in einigen Fällen beim Klicken auf *Latenzdaten erfassen* ein Fehler ausgelöst, wenn für den Server eine Sortierung unter Berücksichtigung der Groß-/Kleinschreibung verwendet wurde.
- Ein Fehler wurde behoben, durch den SSMS fälschlicherweise für eine Verfügbarkeitsgruppe den Status *Verteilt* meldete, wenn der Clusterdienst beendet wurde.
- Ein Problem wurde behoben, durch das beim Erstellen einer Verfügbarkeitsgruppe über das Dialogfeld *Verfügbarkeitsgruppe erstellen* das Festlegen von *ReadOnlyRoutingUrl* erforderlich war.
- Ein Problem wurde behoben, durch das eine NullReferenceException ausgelöst wurde, wenn das Primärelement ausgefallen war und ein manuelles Failover auf das Sekundärelement ausgeführt wurde.
- Ein Problem wurde behoben, durch das beim Erstellen einer Verfügbarkeitsgruppe mit der Sicherungs-/Wiederherstellungsfunktion zum Initialisieren einer Datenbank die Datenbankdateien auf den sekundären Replikaten im Standardverzeichnis erstellt wurden. Bei der Lösung des Problems ist Folgendes zu beachten:
   - Fügen Sie das Validierungssteuerelement für das Daten-oder Protokollverzeichnis hinzu.
   - Verschieben Sie Dateien nur, wenn das Replikat auf einem anderen Betriebssystem als das primäre Replikat ausgeführt wird.
- Ein Problem wurde behoben, durch das der SSMS-Assistent keine *CLUSTER_TYPE*-Option erstellte, wodurch der sekundäre Join fehlschlug.

Setup:
- Ein Problem wurde behoben, durch das ein Upgrade von SSMS mithilfe der Installation des Upgradepakets fehlschlug, wenn SSMS nicht an einem Standardspeicherort installiert wurde.

SMO:
- Ein Leistungsproblem wurde behoben, durch das die Skripterstellung für Tabellen auf SQL Server 2016 oder einer neueren Version bis zu 30 Sekunden dauern konnte (aktuell weniger als eine Sekunde).

Objekt-Explorer:
- Ein Problem wurde behoben, durch das SSMS beispielsweise die Ausnahme "Object cannot be cast from DBNull to other types" (Das Objekt kann nicht von DBNull in einen anderen Typ umgewandelt werden) auslöste, wenn der Knoten *Verwaltung* im Objekt-Explorer erweitert wurde.
- Ein Problem wurde behoben, durch das die Option *PowerShell starten* das SQLServer-Modul bei der Ausgabe eines benutzerdefinierten PS-Profils nicht erkannte.
- Ein Problem wurde behoben, durch das der Objekt-Explorer zeitweilig nicht reagierte, wenn in diesem mit der rechten Maustaste auf einen Tabellen- oder Indexknoten geklickt wurde.

Datenbank-E-Mail:
- Ein Problem wurde behoben, durch das der *Assistent zum Konfigurieren von Datenbank-E-Mail* eine Ausnahme auslöste, wenn mehr als 16 Profile angezeigt oder verwaltet werden sollten.


**Analysis Services (AS)**

- Ein Problem wurde behoben, durch das beim Ändern einer Datenquelle für Modelle mit Kompatibilitätsgrad 1400 in SSMS die Änderungen nicht auf dem Server gespeichert wurden.

**Integration Services**

- Ein Problem wurde behoben, durch das in SSMS keine SSIS-Katalogknoten oder -Berichte bei einer Verbindung mit einer verwalteten SQL-Datenbank-Instanz angezeigt wurden.

### <a name="known-issues"></a>Bekannte Probleme

> [!WARNING]
> Es gibt ein bekanntes Problem, bei dem SSMS 17.6 instabil wird und abstürzt, wenn [Wartungspläne](../relational-databases/maintenance-plans/maintenance-plans.md) verwendet werden. Wenn Sie Wartungspläne verwenden, installieren Sie nicht SSMS 17.6. Führen Sie ein Downgrade auf SSMS 17.5 durch, falls Sie bereits 17.6 installiert haben und von diesem Problem betroffen sind. 



## <a name="downloadssdtmediadownloadpng-ssms-175httpsgomicrosoftcomfwlinklinkid867670"></a>![Herunterladen](../ssdt/media/download.png) [SSMS 17.5](https://go.microsoft.com/fwlink/?linkid=867670)
Allgemein verfügbar | Buildnummer: 14.0.17224.0

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=867670&clcid=0x40a)

### <a name="whats-new"></a>Neues

**SSMS Allgemein**

Datenermittlung und -klassifizierung:

- Ein neues Feature für die SQL-Datenermittlung und -klassifizierung zum Ermitteln, Klassifizieren, Kennzeichnen und Melden von sensiblen Daten in Ihren Datenbanken wurde hinzugefügt. 
- Die automatische Ermittlung und Klassifizierung Ihrer vertraulichsten Daten (z. B. geschäftliche, finanzielle, gesundheitliche oder personenbezogene Daten) kann im Information Protection-Status Ihres Unternehmens eine entscheidende Rolle spielen.
- Weitere Informationen finden Sie unter [SQL Data Discovery & Classification (SQL-Datenermittlung und -klassifizierung)](../relational-databases/security/sql-data-discovery-and-classification.md).

Abfrage-Editor:

- Die Unterstützung für die Option „SkipRows“ wurde dem externen Dateiformat für Text, der durch Trennzeichen getrennt ist, für Azure SQL DW hinzugefügt. Diese Funktion ermöglicht Benutzern, eine angegebene Anzahl von Zeilen zu überspringen, wenn sie durch Trennzeichen getrennte Textdateien in SQL DW laden. Ebenfalls wurde die entsprechende Unterstützung für das Schlüsselwort FIRST_ROW in IntelliSense bzw. SMO hinzugefügt. 

Showplan:

- Das Anzeigen der Schaltfläche für den geschätzten Plan in SQL Data Warehouse wurde aktiviert.
- Das neue Showplan-Attribut *EstimateRowsWithoutRowGoal* wurde hinzugefügt, und *QueryTimeStats* wurden Showplan-Attribute hinzugefügt: *UdfCpuTime* und *UdfElapsedTime*. Weitere Informationen finden Sie unter [Optimizer row goal information in query execution plan added in SQL Server 2017 CU3 (Zeilenzielinformationen für den Optimierer im Abfrageausführungsplan, die in SQL Server 2017 CU3 hinzugefügt wurden)](https://support.microsoft.com/help/4051361).



### <a name="bug-fixes"></a>Behebung von Programmfehlern

**SSMS Allgemein**

Showplan:

- Die verstrichene Zeit der Live-Abfragestatistik wurde behoben, sodass sie die Ausführungszeit der Engine anstelle der verstrichenen Zeit der LQS-Verbindung anzeigt.
- Ein Problem wurde behoben, bei dem Showplan „Apply logical operators“ (Logische Operatoren anwenden), wie z. B. GbApply und InnerApply, nicht erkennen konnte.
- Ein Problem im Zusammenhang mit ExchangeSpill wurde behoben.

Abfrage-Editor:

- Ein Problem im Zusammenhang mit SPIDs wurde behoben, bei dem SSMS einen Fehler wie "Input string wasn't in a correct format. (mscorlib)" (mscorlib)“ beim Ausführen einer einfachen Abfrage mit vorangestellten „SET SHOWPLAN_ALL ON“ auslöst. 


SMO:

- Ein Problem wurde behoben, bei dem SMO AvailabilityReplica-Eigenschaften nicht abrufen konnte, wenn die Serversortierung die Groß-/Kleinschreibung beachtet hat (daher konnte SSMS eine Fehlernachricht wie "The multi-part identifier ‚a.delimited‘ could not be bound." (Der mehrteilige Bezeichner ‚a.delimited‘ konnte nicht gebunden werden.) anzeigen).
- Ein Problem in der Klasse „DatabaseScopedConfigurationCollection“ wurde behoben, bei dem Sortierungen nicht ordnungsgemäß behandelt wurden (daher konnte SSMS auf Computern mit dem Gebietsschema Türkisch Fehler wie "legacy cardinality estimation isn't valid scoped configuration" (Legacy-Kardinalitätsschätzung ist keine gültige Konfiguration) anzeigen, wenn ein Rechtsklick auf eine Datenbank ausgeführt wird, die auf einem Server mit einer Groß-/Kleinschreibung beachtenden Sortierung ausgeführt wird).
- Ein Problem in der Klasse „JobServer“ wurde behoben, bei dem SMO SQL Agent-Eigenschaften nicht von einem SQL 2005-Server abrufen konnte (daher hat SSMS einen Fehler wie "Einer lokalen Variable kann kein Standardwert zugewiesen werden. Die \@ServiceStartMode-Skalarvariable muss deklariert werden" ausgelöst und den SQL Agent-Knoten im Objekt-Explorer letztlich nicht angezeigt).

Vorlagen: 

- „Datenbank-E-Mail“: mehrere Rechtschreibfehler wurden verbessert [(https://feedback.azure.com/forums/908035/suggestions/33143512)](https://feedback.azure.com/forums/908035/suggestions/33143512).  

Objekt-Explorer:
- Ein Problem wurde behoben, durch das die verwaltete Komprimierung bei Indizes fehlschlug (https://feedback.azure.com/forums/908035-sql-server/suggestions/32610058-ssms-17-4-error-when-enabling-page-compression-o).

Überwachung:
- Ein Problem mit dem Feature *Überwachungsdateien zusammenführen* wurde behoben.
<br>

### <a name="known-issues"></a>Bekannte Probleme

Datenklassifizierung:
- Das Entfernen einer Klassifizierung und das anschließende manuelle Hinzufügen einer neuen Klassifizierung in der gleichen Spalte führt dazu, dass der alte Informationstyp und die Vertraulichkeitsbezeichnung der Spalte in der Hauptansicht zugewiesen wird.<br>
*Problemumgehung*: Weisen Sie den neuen Informationstyp und die Vertraulichkeitsbezeichnung nach dem Hinzufügen der Klassifizierung zur Hauptansicht und vor dem Speichern zu.


## <a name="downloadssdtmediadownloadpng-ssms-174httpsgomicrosoftcomfwlinklinkid864329"></a>![Herunterladen](../ssdt/media/download.png) [SSMS 17.4](https://go.microsoft.com/fwlink/?linkid=864329)
Allgemein verfügbar | Buildnummer: 14.0.17213.0

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=864329&clcid=0x40a)


### <a name="whats-new"></a>Neues

**SSMS Allgemein**

Sicherheitsrisikobewertung:
- Es wurde ein neuer SQL-Risikoanalysedienst hinzugefügt, der Ihre Datenbanken auf potentielle Sicherheitsrisiken und Abweichungen von bewährten Methoden untersuchen kann, wie etwa Fehlkonfigurationen, übermäßige Berechtigungen und unzureichend geschützte vertrauliche Daten. 
- Zu den Ergebnissen der Bewertung zählen Aktionsschritte zum Beheben der jeweiligen Probleme und ggf. benutzerdefinierte Skripts zur Wiederherstellung. Der Bewertungsbericht kann für die verschiedenen Umgebungen und an spezifische Anforderungen angepasst werden. Weitere Informationen finden Sie unter [SQL-Sicherheitsrisikobewertung](https://docs.microsoft.com/sql/relational-databases/security/sql-vulnerability-assessment).

SMO:
- Ein Problem wurde behoben, bei dem unter Azure Ausnahmen von *HasMemoryOptimizedObjects* ausgelöst wurden.
- Unterstützung für die neue CATALOG_COLLATION-Funktion wurde hinzugefügt.

AlwaysOn-Dashboard:
- Verbesserungen an der Latenzanalyse in Verfügbarkeitsgruppen.
- Zwei neue Berichte: *AlwaysOn\_Latency\_Primary* und *AlwaysOn\_Latency\_Secondary*.

Showplan:
- Aktualisierte Links verweisen auf die korrekte Dokumentation.
- Die Analyse von Einzelplänen ist direkt aus dem generierten eigentlichen Plan heraus möglich.
- Neuer Symbolsatz.
- Unterstützung für die Erkennung von „Logische Operatoren anwenden“, wie GbApply, InnerApply.

XE-Profiler:
- In XEvent Profiler umbenannt.
- Die Menübefehle „Stopp“/„Start“ führen jetzt standardmäßig zum Beenden/Starten der Sitzung.
- Tastenkombinationen (z. B. **STRG-F** zum Suchen) wurden aktiviert.
- Hinzugefügte Aktionen ‚database\_name‘ und ‚client\_hostname‘ zu den entsprechenden Ereignissen in XEvent Profiler-Sitzungen. Damit die Änderung wirksam wird, müssen Sie möglicherweise vorhandene QuickSessionStandard- oder QuickSessionTSQL-Instanzen auf den Servern löschen – [Connect 3142981](https://connect.microsoft.com/SQLServer/feedback/details/3142981)

Befehlszeile:
- Neue Befehlszeilenoption („-G“), die verwendet werden kann, um SSMS automatisch eine Verbindung mit einem Server/einer Datenbank mithilfe von Active Directory-Authentifizierung (wahlweise „Integrated“ oder „Password“) herstellen zu lassen. Weitere Informationen finden Sie unter [Ssms-Hilfsprogramm](ssms-utility.md).

Assistent zum Importieren von Flatfiles:
- Neue Möglichkeit zur Auswahl eines anderen als des Standardschemanamens („dbo“) beim Erstellen der Tabelle.

Abfragespeicher:
- Der Bericht „Rückläufige Abfragen“ beim Erweitern der Liste der verfügbaren Berichte im Abfragespeicher wurde wiederhergestellt.

**Integration Services**
- Neue Funktion zur Paketüberprüfung im Bereitstellungs-Assistenten, die dem Benutzer hilft, Komponenten innerhalb von SSIS-Paketen zu erkennen, die in Azure-SSIS IR nicht unterstützt werden.

### <a name="bug-fixes"></a>Behebung von Programmfehlern

**SSMS Allgemein**

- Objekt-Explorer: Ein Problem wurde behoben, bei dem der Tabellenwertfunktionsknoten in Datenbankmomentaufnahmen nicht angezeigt wurde – [Connect 3140161](https://connect.microsoft.com/SQLServer/feedback/details/3140161).
Verbesserte Leistung beim Erweitern der Knotens *Datenbanken*, wenn der Server über AUTOCLOSE-Datenbanken verfügt.
- Abfrage-Editor: Ein Problem wurde behoben, bei dem IntelliSense für Benutzer nicht verfügbar war, die keinen Zugriff auf die Masterdatenbank besitzen.
Es wurde ein Problem behoben, das in manchen Fällen zu Abstürzen von SSMS führte, wenn die Verbindung mit einem Remotecomputer geschlossen wurde – [Connect 3142557](https://connect.microsoft.com/SQLServer/feedback/details/3142557).
- XEvent-Viewer: Die Funktionalität zum Exportieren nach XEL wurde wieder aktiviert.
Es wurden Probleme behoben, bei denen der Benutzer manchmal nicht in der Lage war, eine gesamte XEL-Datei zu laden.
- XEvent-Profiler: Es wurde ein Problem behoben, das zu Abstürzen von SSMS führte, wenn der Benutzer nicht über die *VIEW SERVER STATE*-Berechtigungen verfügte.
Es wurde ein Problem behoben, bei dem das Schließen des XE Profiler-Livedatenfensters nicht zum Beendigen der zugrundeliegenden Sitzung führte.
- Registrierte Server: Das Problem, dass der Befehl „Verschieben nach…“ ([Connect-ID 3142862](https://connect.microsoft.com/SQLServer/feedback/details/3142862) und [Connect-ID 3144359](https://connect.microsoft.com/SQLServer/feedback/details/3144359/)) nicht mehr funktionierte, wurde behoben.
- SMO: Es wurde ein Problem behoben, bei dem die TransferData-Methode für das Transfer-Objekt nicht funktionierte.
Es wurde ein Problem behoben, bei dem die Serverdatenbanken eine Ausnahme für angehaltene SQL DW-Datenbanken auslösten.
Es wurde ein Problem behoben, bei dem Skripts für die SQL-Datenbank in SQL Data Warehouse zur Erzeugung falscher T-SQL-Parameterwerte führte.
Es wurde ein Problem behoben, bei dem Skripts für eine Stretchingdatenbank fälschlicherweise zur Ausgabe der Option *DATA\_COMPRESSION* führten.
- Auftragsaktivitätsmonitor: Es wurde ein Problem behoben, bei dem der Benutzer einen Fehler „Der Index lag außerhalb des Bereichs. Er darf nicht negativ und kleiner als die Sammlung sein. 
      Parametername: Index (System.Windows.Forms)“ erhielt, wenn er versuchte, nach der Kategorie zu filtern – [Connect 3138691](https://connect.microsoft.com/SQLServer/feedback/details/3138691).
- Verbindungsdialogfeld: Es wurde ein Problem behoben, bei dem Benutzer ohne Zugriff auf einen Domänencontroller mit Lese-/Schreibzugriff sich nicht mithilfe von SQL-Authentifizierung bei einem SQL-Server anmelden konnte: [Connect 2373381](https://connect.microsoft.com/SQLServer/feedback/details/2373381).
- Replikation: Es wurde ein Problem behoben, bei dem beim Anzeigen der Eigenschaften eines Pullabonnements in SQL Server ein Fehler der Art „Der Wert ‚NULL‘ kann nicht auf die Eigenschaft ServerInstance angewendet werden“ angezeigt wurde.
- SSMS-Setup: Es wurde ein Problem behoben, bei dem das SSMS-Setup fälschlicherweise zu einer Neukonfiguration aller auf dem Computer installierten Produkte führte.
- Benutzereinstellungen:
   - Mit dieser Problembehebung erhalten Benutzer von Azure Government ununterbrochenen Zugriff auf ihre Azure SQL-Datenbank- und Azure Resource Manager-Ressourcen mithilfe von SSMS über universelle Authentifizierung und Azure Active Directory-Anmeldung.  Benutzer früherer Versionen von SSMS müssen „Extras“ > „Optionen“ > „Azure-Dienste“ öffnen und unter „Ressourcenmanagement“ die Konfiguration der Eigenschaft „Active Directory-Autorität“ in https://login.microsoftonline.us ändern.

**Analysis Services (AS)**

- Profiler: Es wurde ein Problem beim Herstellen von Verbindungen unter Verwendung von Windows-Authentifizierung für Azure AS behoben.
- Es wurde ein Problem behoben, das beim Stornieren von Verbindungsdetails für ein Modell 1400 zu einem Absturz führen konnte.
- Wenn beim Aktualisieren von Anmeldeinformationen ein Azure-Blob-Schlüssel im Verbindungseigenschaften-Dialogfeld festgelegt wird, wird er jetzt visuell maskiert.
- Es wurde ein Problem im Azure Analysis Services-Dialogfeld zur Benutzerauswahl behoben, bei dem bei der Suche die GUID der Anwendungs-ID anstelle der Objekt-ID angezeigt wurde.
- Es wurde ein Problem in der Symbolleiste des Datenbank durchsuchen\MDX-Abfrage-Designers behoben, das für einige Schaltflächen zu einer fehlerhaften Zuordnung der Symbole führte.
- Es wurde ein Problem behoben, das ein Herstellen von Verbindungen mit SSAS mithilfe von IIS-Http/Https-Adressen von msmdpump verhinderte.
- Mehrere Zeichenfolgen im Benutzerauswahl-Dialogfeld von Azure Analysis Services wurden jetzt für weitere Sprachen übersetzt.
- Die Eigenschaft „MaxConnections“ ist jetzt für Datenquellen in Tabellenmodellen sichtbar.
- Der Bereitstellungs-Assistent generiert jetzt korrekte JSON-Definitionen für Mitglieder der Azure AS-Rolle.
- Es wurde ein Problem in SQL Profiler behoben, bei dem das Auswählen von Windows-Authentifizierung für Azure AS trotzdem zur Anmeldeaufforderung führte.



## <a name="downloadssdtmediadownloadpng-ssms-173httpsgomicrosoftcomfwlinklinkid858904"></a>![download (Herunterladen von)](../ssdt/media/download.png) [SSMS 17.3](https://go.microsoft.com/fwlink/?linkid=858904)
Allgemein verfügbar | Buildnummer: 14.0.17199.0

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)


### <a name="enhancements"></a>Erweiterungen

- Es wurde ein neuer Assistent zum Importieren von Flatfiles hinzugefügt, um den Import von CSV-Dateien mithilfe eines intelligenten Frameworks zu optimieren, wozu minimaler Benutzereingriff oder spezielles Domänenwissen erforderlich ist. Weitere Informationen finden Sie unter [Import Flat File to SQL Wizard (Importieren einer Flat File zum SQL-Assistenten)](../relational-databases/import-export/import-flat-file-wizard.md).
- Hinzugefügter „XEvent Profiler“-Knoten zum Objekt-Explorer. Weitere Informationen finden Sie unter [Use the SSMS XEvent Profiler (Verwenden des SSMS XEvent Profiler)](../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Aktualisierte Wartevorgangsfilterung und -kategorisierung in historischen Wartevorgangsberichten des Performance Dashboards.
- Die Syntaxprüfung der „Predict“-Funktion wurde hinzugefügt.
- Die Syntaxprüfung der Abfragen der externen Bibliotheksverwaltung wurde hinzugefügt.
- SMO-Unterstützung für die externe Bibliotheksverwaltung wurde hinzugefügt.
- Die Unterstützung „PowerShell starten“ wurde dem Fenster „Registrierte Server“ hinzugefügt (erfordert ein neues SQL PowerShell-Modul).
- Always On: [die schreibgeschützte Routingunterstützung](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) für Verfügbarkeitsgruppen wurde hinzugefügt.
- Eine Option zum Senden von Ablaufverfolgungsdetails an das Ausgabefenster für „Active Directory: universell mit MFA-Unterstützung“-Logins wurde hinzugefügt (standardmäßig deaktiviert, muss in den Benutzereinstellungen unter „Tools > Optionen > Azure-Dienste > Azure Cloud > Ablaufverfolgungsebene für ADAL-Ausgabefenster“ aktiviert werden). 
- Abfragespeicher: 
  - Es kann auf die Abfragespeicher-Benutzeroberfläche zugegriffen werden, auch wenn QDS deaktiviert ist, solange QDS Daten aufgezeichnet hat.
  - Die Abfragespeicher-Benutzeroberfläche macht die Kategorisierung von Wartevorgängen in allen vorhandenen Berichten verfügbar. Dadurch können Kunden die Szenarios der wichtigsten wartenden Abfragen und vieles mehr entsperren.
- Inklusionen der Header von Skriptparametern sind jetzt optional (standardmäßig deaktiviert, kann in den Benutzereinstellungen unter „Tools > Optionen > SQL Server-Objekt-Explorer > Skripts > Header für Skriptparameter einbeziehen“ aktiviert werden) – [Connect-Artikel 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).
- Das „RC“-Branding wurde entfernt.

### <a name="bug-fixes"></a>Fehlerbehebungen

**SSMS Allgemein**

- XEvent: 
   - Problem wurde behoben, bei dem SSMS nur einen Teil der Ereignisse in der XEL-Datei öffnet.
   - Verbesserte Option „Anzeigen von Livedaten“, wenn die Standarddatenbank nicht die Bezeichnung „Master“ hat – [Connect-Artikel 1222582](https://connect.microsoft.com/SQLServer/feedback/details/1222582).
- Always On: Problem wurde behoben, bei dem „Wiederherstellen von Protokollsicherungen“ möglicherweise mit folgendem Fehler fehlschlägt: „The log in this backup set terminates at LSN x, which is too early to apply to the database“ (Das Protokoll in diesem Sicherungssatz endet bei LSN x. Dies ist zu früh für die Anwendung des Sicherungssatzes auf die Datenbank).
- Auftragsaktivitätsmonitor: inkonsistente Symbole wurden berichtigt – [Connect-Artikel 3133100](https://connect.microsoft.com/SQLServer/feedback/details/3133100).
- Abfragespeicher: Ein Problem wurde behoben, bei dem der Benutzer den Datumsbereich „benutzerdefiniert“ für Abfragespeicherberichte nicht auswählen konnte. Weitere Informationen finden Sie in den folgenden Artikeln.
   - [Connect-Artikel 3139842](https://connect.microsoft.com/SQLServer/feedback/details/3139842)
   - [Connect-Artikel 3139399](https://connect.microsoft.com/SQLServer/feedback/details/3139399)
- Problem wurde behoben, bei dem das Verbindungsdialogfeld die kürzlich verwendete Datenbank nicht „löscht“, wenn gespeicherte Informationen eine benannte Datenbank besitzt, und der Benutzer „Standard“ auswählt.
- Skripterstellung für Objekte: Problem wurde behoben, bei dem „Datenbankskript generieren“ nicht funktioniert und ein Fehler ausgelöst wird, wenn der Benutzer eine angehaltene DW-Datenbank auf dem Server hat, jedoch eine andere Nicht-DW-Datenbank ausgewählt hat und versucht hat, für diese ein Skript zu erstellen.
Es wurde ein Problem behoben, bei dem der Header für skriptbasierte gespeicherte Prozeduren nicht mit den Skripteinstellungen übereingestimmt hat, was zu einem irreführenden Skript geführt hat – [Connect-Artikel 3139784](https://connect.microsoft.com/SQLServer/feedback/details/3139784).
Die Schaltfläche „Skript“ wurde für Azure SQL-Objekte erneut aktiviert.
  Es wurde ein Problem behoben, bei dem SSMS die Skripterstellung für „Alter“ oder „Execute“ für einige Objekte (UDF, View, SP, Trigger) beim Herstellen einer Verbindung mit einer Azure SQL-Datenbank nicht zugelassen hat – [Connect-Artikel 3136386](https://connect.microsoft.com/SQLServer/feedback/details/3136386).
- Abfrage-Editor:
  - Verbesserte IntelliSense-Funktion beim Nutzen von Azure SQL-Datenbanken.
  - Problem wurde behoben, bei dem Abfragen aufgrund eines abgelaufenen Authentifizierungstokens (Universelle Authentifizierung) fehlgeschlagen sind.
  - Verbesserte IntelliSense-Funktion beim Arbeiten mit Azure SQL-Datenbanken (besonders, wenn eine Verbindung zu Azure SQL-Datenbank hergestellt wird, wird die neueste T-SQL-Grammatik (140) verwendet).
  - Problem wurde behoben, bei dem das Öffnen eines Abfragefensters mit einer Verbindung zu einer Nicht-DataWarehouse-Datenbank auf einem Server veranlassen würde, dass alle nachfolgenden Abfragefenster für diesen Server für DataWarehouse-Datenbanken mehrere Fehler zu nicht unterstützen Typen/Optionen ausgeben würden.
- Always On:
   - Spalte im Seedingmodus wurde dem Always On-Dashboard und den AG-Eigenschaftenseiten hinzugefügt.
   - Es wurde ein Problem behoben, bei dem es nicht möglich war, eine Linux-AG zu erstellen, wenn sich das primäre Element unter Windows befindet – [Connect-Artikel 3139856](https://connect.microsoft.com/SQLServer/feedback/details/3139856).
- Mehrere Probleme mit „Nicht genügend Arbeitsspeicher.“ wurden in SSMS beim Ausführen von Abfragen behoben – [Connect-Artikel 2845190](https://connect.microsoft.com/SQLServer/feedback/details/2845190), [Connect-Artikel 3123864](https://connect.microsoft.com/SQLServer/feedback/details/3123864).
- Profiler: 
   - Es wurde ein Problem behoben, bei dem der Profiler nicht funktioniert hat, als er für SQL 2005 benutzt wurde.
   - Es wurde ein Problem behoben, bei dem der Profiler die Verbindungsoption „Serverzertifikat vertrauen“ nicht berücksichtigt hat.
- Aktivitätsmonitor: Problem wurde behoben, bei dem der Aktivitätsmonitor nicht funktioniert, wenn er auf einen Server von SQL Server unter Linux gezeigt wird.
- Problem mit der SMO-Übertragungsklasse wurde behoben, bei dem External Data Source- oder externe File Format-Objekte nicht übertragen wurden. Diese Art Objekte sollten nun ordnungsgemäß in der Übertragung enthalten sein.
- Registrierte Server:
   - Aktivierte Multiserverabfrage für UA-Server (es wird versucht, das gleiche Token für jeden UA-Server in der Gruppe zu verwenden).
- Universelle AD-Authentifizierung:
   - Es wurde ein Problem behoben, bei dem die Azure AD-Authentifizierung nicht unterstützt wurde.
   - Es wurde ein Problem behoben, bei dem der Tabellen/Sicht-Designer nicht funktioniert hat.
   - Problem wurde behoben, bei dem „Die ersten 1000 Zeilen auswählen“ und „Die ersten 200 Zeilen bearbeiten“ nicht funktioniert haben.
- Datenbankwiederherstellung: Problem wurde behoben, bei dem die Wiederherstellung den letzten Ordner im Pfad bei der Verschiebung von Dateien zu einem anderen Speicherort ausgelassen hat.
- Assistent für die Komprimierung:
   - Ein Problem bei der Verwaltung des Assistenten für die Komprimierung für Indizes wurde behoben. Ein weiteres Problem wurde behoben, bei dem Assistenten zum Komprimieren von Daten für SQL 2016 und früher fehlerhaft waren.
        https://connect.microsoft.com/SQLServer/feedback/details/3139342
   - Assistent zum Komprimieren wurde den Azure-Tabellen und -Indizes hinzugefügt.
- Showplan: 
   - Problem wurde behoben, bei dem PDW-Operatoren nicht erkannt wurden.
- Servereigenschaften:
   - Problem wurde behoben, bei dem nicht möglich war, die Prozessoraffinität des Servers zu ändern.


**Analysis Services (AS)**

- Eine Reihe von Problemen wurden mit dem Assistent für die Bereitstellung behoben, um den tabellarischen 1400-Kompatibilitätsgradmodus und Power Query-Datenquellen zu unterstützen.
- Der Assistent für die Bereitstellung kann nun auf AS Azure bereitstellen, wenn er auf einer Befehlszeile ausgeführt wird.
- Bei Verwendung von Windows Auth in AS Azure wird dem Benutzer nun der Namen des Benutzerkontos im Objekt-Explorer korrekt angezeigt.


### <a name="known-issues-in-this-173-release"></a>Bekannte Probleme in dieser Version 17.3:

**SSMS Allgemein**

- Die folgende SSMS-Funktion wird für die Azure AD-Authentifizierung nicht unterstützt, wenn die universelle Authentifizierung mit MFA verwendet wird:
   - Der Datenbankoptimierungsratgeber wird für die Azure AD-Authentifizierung nicht unterstützt. Es liegt ein bekanntes Problem vor, für das dem Benutzer die eher unverständliche Fehlermeldung „Die Datei oder Assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory' konnte nicht geladen werden,…“ angezeigt wird statt der erwarteten Fehlermeldung "Die Microsoft Azure SQL-Datenbank wird vom Datenbankoptimierungsratgeber nicht unterstützt. (DTAClient)“ (Die Microsoft Azure SQL-Datenbank wird vom Datenbankoptimierungsratgeber nicht unterstützt).
- Bei dem Versuch, eine Abfrage in DTA zu analysieren entsteht folgender Fehler: "Object must implement IConvertible. (mscorlib)“ (Objekt muss IConvertible implementieren).
- *Rückläufige Abfragen* fehlen in der Liste der Berichte im Abfragespeicher im Objekt-Explorer.
   - Problemumgehung: Klicken Sie mit der rechten Maustaste auf den Knoten **Abfragespeicher**, und wählen Sie **View Regressed Queries (Rückläufige Abfragen anzeigen)** aus.

**Integration Services**

- Der [Ausführungspfad] in [Katalog].[Ereignismeldungen] ist für Paketausführungen in Scale Out falsch. Der [Ausführungspfad] beginnt mit „\Package“ anstelle des Objektnamens des ausführbaren Pakets. Beim Anzeigen der Übersichtsberichte von Paketausführungen in SSMS kann der Link zum „Ausführungspfad“ in der Übersicht über die Ausführung nicht funktionieren. Klicken Sie im Übersichtsbericht auf „Nachrichten anzeigen“, um alle Ereignismeldungen zu prüfen.


## <a name="downloadssdtmediadownloadpng-ssms-172httpsgomicrosoftcomfwlinklinkid854085"></a>![download (Herunterladen von)](../ssdt/media/download.png) [SSMS 17.2](https://go.microsoft.com/fwlink/?linkid=854085)
Allgemein verfügbar | Buildnummer: 14.0.17177.0

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

### <a name="enhancements"></a>Erweiterungen

- Multi-Factor Authentication (MFA)
  - Azure AD-Authentifizierung für mehrere Benutzer für eine universelle Authentifizierung mit Multi-Factor Authentication (UA mit MFA)
  - Ein neues Eingabefeld für Benutzeranmeldeinformationen wurde der universellen Authentifizierung mit MFA hinzugefügt, um die Authentifizierung für mehrere Benutzer zu unterstützen.
- Das Dialogfeld „Verbindung“ unterstützt nun die folgenden fünf Authentifizierungsmethoden:
  - Windows-Authentifizierung
  - SQL Server-Authentifizierung
  - Active Directory: Universell mit MFA-Unterstützung
  - Active Directory: Kennwort
  - Active Directory: Integriert

- Verwenden der universellen Authentifizierung mit MFA durch den Assistenten für Datenbankimport und -export für DacFx.
- Informationen zur API-Unterstützung finden Sie unter [IUniversalAuthProvider-Schnittstelle](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- Die von ADAL verwaltete Bibliothek, die von der universellen Authentifizierung mit MFA in Azure AD verwendet wird, wurde auf Version 3.13.9 aktualisiert.
- Darüber hinaus wurde eine neue CLI-Schnittstelle bereitgestellt, die Azure AD-Administratoreinstellungen für SQL-Datenbank und SQL Data Warehouse unterstützt.

 Weitere Informationen zu den Authentifizierungsmethoden in Active Directory finden Sie unter [Universal Authentication with SQL Database and SQL Data Warehouse (SSMS support for MFA) (Universelle Authentifizierung mit SQL-Datenbank und SQL Data Warehouse (SSMS-Unterstützung für MFA))](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) und [Configure Azure SQL Database multi-factor authentication for SQL Server Management Studio (Konfigurieren der mehrstufigen Authentifizierung in Azure SQL-Datenbank für SQL Server Management Studio)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- Das Ausgabefenster enthält Einträge für Abfragen, die während der Erweiterung der Objekt-Explorer-Knoten ausgeführt wurden
- Aktivierter Sicht-Designer für Azure SQL-Datenbanken
- Die Standardoptionen für die Skripterstellung für Skripterstellungsobjekte aus dem Objekt-Explorer in SSMS haben sich geändert:
  - Zuvor war das generierte Skript bei einer neuen Installation standardmäßig auf die neueste Version von SQL Server (aktuell SQL Server 2017) ausgerichtet.
  - In SSMS 17.2 wurde eine neue Option hinzugefügt: *Skripteinstellungen mit Quelle abgleichen*. Mit der Einstellung *TRUE* ist das generierte Skript auf dieselbe Version, denselben Engine-Typ und dieselbe Engine-Edition wie die des Servers, von dem aus das Skript für das Objekt erstellt wird, ausgerichtet.
  - Der Wert für *Skripteinstellungen mit Quelle abgleichen* ist standardmäßig auf *TRUE* festgelegt. Neue Installationen von SSMS verfügen somit automatisch über die Standardeinstellung, dass die Skripte von Objekten an dasselbe Ziel wie das des Originalservers gerichtet werden.
  - Wenn der Wert für *Skripteinstellungen mit Quelle abgleichen* auf *FALSE* festgelegt ist, werden die normalen Zieloptionen für die Skripterstellung aktiviert und funktionieren wie bisher.
Zusätzlich wurden alle Skripterstellungsoptionen in ihren eigenen Abschnitt verschoben: *Versionsoptionen*. Sie befinden sich nicht länger unter*Allgemeine Skriptoptionen*.

- Unterstützung für nationale Clouds in „Wiederherstellen aus URL“
- QueryStoreUI-Berichte unterstützen nun zusätzliche Metriken (z. B. RowCount, DOP, CLR Time) aus „sys.query_store_runtime_stats“.
- IntelliSense wird nun für die Azure SQL-Datenbank unterstützt https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Sicherheit: Das Verbindungsdialogfeld stuft Serverzertifikate standardmäßig als nicht vertrauenswürdig ein und fordert Verschlüsselung für Azure SQL-Datenbankverbindungen an
- Allgemeine Verbesserungen für die Unterstützung von SQL Server unter Linux:
 - Der Knoten „Datenbank-E-Mail“ ist zurück
 - Verschiedene auf Pfade bezogene Probleme wurden behoben
 - Der Aktivitätsmonitor ist stabiler
 - Das Dialogfeld „Verbindungseigenschaften“ zeigt die korrekte Plattform an
- Der Leistungsdashboard-Serverbericht ist nun als Standardbericht verfügbar:
  - Verbindung zu SQL Server 2008 und höheren Versionen möglich.
  - Der Unterbericht zu fehlenden Indizes verwendet Bewertungen, um das Identifizieren der nützlichsten Indizes zu unterstützen.
  - Der Unterbericht zum Verlauf der Wartezustände aggregiert die Wartevorgänge nun nach Kategorie. Wartevorgänge, die sich im Leerlauf oder Ruhezustand befinden, werden standardmäßig herausgefiltert.
  - Ein neuer Unterbericht für den Verlauf von Latches.
- Die Showplan-Knotensuche ermöglicht die Suche in Planeigenschaften. Einfache Suche nach beliebigen Operatoreigenschaften wie z.B. Tabellennamen. Das Verwenden dieser Option beim Anzeigen eines Plans:
  - Klicken Sie mit der rechten Maustaste auf „Plan“ und im Kontextmenü auf die Option „Knoten finden“
  - Drücken Sie **STRG+F**.


**Analysis Services (AS)**

- Neue AAD-Rollenmemberauswahl für Benutzer ohne E-Mail-Adressen in AS Azure-Modellen in SSMS

**Integration Services**

- Eine neue Spalte („Anzahl von Ausführungen“) wurde dem Ausführungsbericht für SSIS hinzugefügt

### <a name="known-issues-in-this-release"></a>Bekannte Probleme in dieser Version:

- Bei Abfragefenstern, die die universelle Active Directory-Authentifizierung mit MFA-Unterstützung verwenden, kann ein Fehler ähnlich dem Folgenden auftreten, wenn versucht wird, eine Abfrage durchzuführen, nachdem das Fenster für eine Stunde geöffnet war:

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery isn't possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of ConnectRetryCount to increase the number of recovery attempts.`

   Ein erneutes Ausführen der Abfrage sollte den Fehler überwinden und erfolgreich sein.

- Die folgenden SSMS-Funktionalitäten werden für die Azure AD-Authentifizierung nicht unterstützt, wenn die universelle Authentifizierung mit MFA verwendet wird:
  - Der Designer **Neue Tabelle/Sicht** zeigt die Anmeldeaufforderung im alten Format an, außerdem funktioniert die Azure AD-Authentifizierung nicht.
  - Das Feature **Die ersten 200 Zeilen bearbeiten** unterstützt die Azure AD-Authentifizierung nicht.
  - Die Komponente **Registrierter Server** unterstützt die Azure AD-Authentifizierung nicht.
  - Der **Datenbankoptimierungsratgeber** wird für die Azure AD-Authentifizierung nicht unterstützt. Es liegt ein bekanntes Problem vor, bei dem dem Benutzer die eher unverständliche Fehlermeldung *Could not load file or assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory,...* (Die Datei oder Assembly 'Microsoft.IdentityModel.Clients.ActiveDirectory' konnte nicht geladen werden,…) angezeigt wird statt der erwarteten Fehlermeldung *Die Microsoft Azure SQL-Datenbank wird vom Datenbankoptimierungsratgeber nicht unterstützt. (DTAClient)* .

**Analysis Services (AS)**

- Der Objekt-Explorer in SSAS zeigt den Benutzernamen der Windows-Authentifizierung nicht in den AS Azure-Verbindungseigenschaften an.

### <a name="bug-fixes"></a>Behebung von Programmfehlern

- Ein Problem behoben, das beim Versuch auftrat, die Ergebnisse einer Abfrage als Text zu drucken.  https://connect.microsoft.com/SQLServer/feedback/details/3055225/
- Ein Problem wurde behoben, bei dem SSMS Tabellen und andere Objekte falsch gelöscht hat, wenn ein Skript für die Löschung dieser Objekte in einer Azure SQL-Datenbank erstellt wurde.
- Es wurde ein Problem behoben, bei dem SSMS gelegentlich den Start verweigert hat mit einem Fehler wie: „Eine oder mehrere Komponenten können nicht gefunden werden. Bitte installieren Sie die Anwendung neu“
- Ein Problem wurde behoben, durch das die SPID auf der SSMS-Benutzeroberfläche nicht aktualisiert und nicht mehr synchron angezeigt werden konnte (https://connect.microsoft.com/SQLServer/feedback/details/1898875 ).
- Es wurde ein Problem bei der automatischen Installation von SSMS behoben, bei dem das Argument /passive als /quiet behandelt wurde.
- Es wurde ein Problem behoben, bei dem SSMS beim Start gelegentlich den Fehler „Objektverweis ist nicht auf eine Instanz des Objekts festgelegt“ ausgegeben hat. https://connect.microsoft.com/SQLServer/feedback/details/3134698
- Es wurde ein Problem mit dem „Datenkomprimierungs-Assistenten“ behoben, das einen Absturz von SSMS verursacht hat, wenn auf der Graph-Tabelle ‚Berechnen‘ angeklickt wurde
- Es wurde ein Leistungsproblem behoben, das beim Rechtsklicken auf einen Index für eine Tabelle (bei einer langsamen Internetverbindung) auftrat. https://connect.microsoft.com/SQLServer/feedback/details/3120783
- Es wurde ein Problem behoben, bei dem es SSMS nicht möglich war, Sicherungsdateien auf Servern mit einer Sammlung, bei der nach Groß- und Kleinschreibung unterschieden wird, aufzulisten. https://connect.microsoft.com/SQLServer/feedback/details/3134787 und https://connect.microsoft.com/SQLServer/feedback/details/3137000
- Showplan und Showplan vergleichen verschiedene Problembehebungen
- Es wurde ein Problem behoben, bei dem das Verbindungsdialogfeld dem Benutzer nicht gestattet hat, das „Netzwerkprotokoll“ anzugeben, das für die Verbindung verwendet werden soll, falls SQL Server nicht auf dem Computer installiert ist, auf dem SSMS ausgeführt wird. https://connect.microsoft.com/SQLServer/feedback/details/3134997
- Verbesserte Unterstützung für die Konfigurationen für mehrere Monitore, bei denen manche SSMS-Dialogfelder an zufälligen Orten angezeigt wurden. Die neue Option „Aufgabendialogfelder“ wurde unter den Benutzereinstellungen von „SQL Server-Objekt-Explorer | Befehle“ hinzugefügt, durch die es ermöglicht wird, die Position eines Aufgabendialogfelds oder Eigenschaftsblatts zu speichern, wenn es geschlossen wird. https://connect.microsoft.com/SQLServer/feedback/details/889169 , https://connect.microsoft.com/SQLServer/feedback/details/1158271, https://connect.microsoft.com/SQLServer/feedback/details/3135260 
- Es wurde ein Problem behoben, bei dem SSMS keine Datenbankeigenschaften für verschlüsselte Azure SQL-Datenbanken ändern konnte.
- Die Option „Ergebnisse nach der Ausführung verwerfen“ wurde verbessert. https://connect.microsoft.com/SQLServer/feedback/details/1196581
- Es wurde ein Problem behoben bzw. verbessert, bei dem es Benutzern nicht möglich war, auf Azure-Abonnements zuzugreifen, für die sie keine Administratorrechte besitzen.
- Der Assistent für die Datenbankwiederherstellung wurde verbessert, damit die Zieldatenbank in OE unabhängig von der Auswahl der Quelldatenbank ausgewählt bleibt. https://connect.microsoft.com/SQLServer/feedback/details/3118581
- Es wurde ein Problem behoben, bei dem der Objekt-Explorer neu hinzugefügte „nativ kompilierte gespeicherte Prozeduren“ nicht korrekt sortiert hat. https://connect.microsoft.com/SQLServer/feedback/details/3133365
- Es wurde ein Problem behoben, bei dem „SELECT TOP N ROWS“ die Klausel „TOP“ nicht enthalten hat. Für Azure SQLDW. https://connect.microsoft.com/SQLServer/feedback/details/3133551 und https://connect.microsoft.com/SQLServer/feedback/details/3135874
- QueryStoreUI: Es wurde ein Problem behoben, bei dem nicht benutzerdefinierte Zeitintervalle nicht bei allen Berichten ordnungsgemäß funktioniert haben.
- Always Encrypted: Verbessertes Messaging für den AKV-Berechtigungsstatus im neuen CMK-Dialogfenster. Zur CEK-Dropdownliste wurde QuickInfo hinzugefügt, um die Unterscheidung von CEKs mit langen Namen zu erleichtern. Es wurde ein Problem behoben, bei dem einige CNG-Schlüsselspeicheranbieter nicht im Dialogfeld „Neuer Spaltenhauptschlüssel“ für Always Encrypted angezeigt wurden
- Inkonsistenz bei „Anwendungsname“ für SSMS-Verbindungen wurde behoben. https://connect.microsoft.com/SQLServer/feedback/details/3135115
- Ein Problem wurde behoben, bei dem SSMS inkorrekte Skripts für Azure SQL generiert hat (Tabellen und Indizes mit der Option „DATA_COMPRESSIONS“). https://connect.microsoft.com/SQLServer/feedback/details/3133148
- Ein Problem wurde behoben, bei dem es dem Benutzer nicht möglich war, die Tastenkombination **STRG+Q** zu verwenden, um den Schnellstart auszuführen. Die neuen Tastenkombinationen zum Umschalten der Option „IntelliSense aktiviert“ im Abfrage-Editor lauten nun **STRG+B** und **STRG+I**. https://connect.microsoft.com/SQLServer/feedback/details/3131968
- Es wurde ein Problem in „Datenbank wiederherstellen“ behoben, bei dem SSMS eine Ausnahme beim Versuch ausgelöst hat, ein Speicherkonto aus einem Abonnement auszuwählen, in dem sich Konten mit benutzerdefinierten Domänen befinden
- Es wurde ein Problem in „Datenbankdiagramm“ behoben, bei dem SSMS den Fehler "Der Index war außerhalb des Arraybereichs." ausgelöst hat. Außerdem war es dem Benutzer nicht möglich, die „Tabellenansicht“ in eine andere Einstellung als „Standard“ zu ändern. https://connect.microsoft.com/SQLServer/feedback/details/3133792 und https://connect.microsoft.com/SQLServer/feedback/details/3135326
- Es wurde ein Problem in „Sicherung/Wiederherstellung in die URL“ behoben, bei dem SSMS keine klassischen Speicherkonten aufgelistet hat.
- Es wurde ein Problem behoben, bei dem eine Ausnahme bei dem Versuch ausgelöst wurde, schemagebundene sicherungsfähige Elemente zu den Datenbankrollen hinzuzufügen. https://connect.microsoft.com/SQLServer/feedback/details/3118143
- Es wurde ein Problem behoben, bei dem SSMS gelegentlich folgenden Fehler angezeigt hat: „‘Data‘ ist NULL. Diese Methode oder Eigenschaft kann nicht für NULL-Werte aufgerufen werden.“ wenn ein Tabellenknoten erweitert wird (https://connect.microsoft.com/SQLServer/feedback/details/3136283 ).
- DTA: Es wurde ein Problem behoben, bei dem „DTAEngine.exe“ mit Heapbeschädigung beendet wurde, wenn die Partitionsfunktion mit bestimmten Begrenzungswerten ausgewertet wurde.


**Analysis Services (AS)**

- Es wurde ein Problem behoben, bei dem „Datenbank wiederherstellen“ in AS zu einem Fehler führt, wenn die Datenbank einen anderen Namen als die ID trägt
- Es wurde ein Problem behoben, bei dem das DAX-Abfragefenster die Menüoption zum Umschalten von „IntelliSense aktiviert“ ignoriert hat
- Es wurde ein Problem behoben, bei dem die Verbindung zu SSAS durch IIS-Adressen (http/https) verhindert wurde, die „msmdpump“ enthalten
- Die Verbindung zu AS Azure mit einem Kennwort, das einen Semikolon enthält, ist nun möglich
- Das Ausgeben des AS-Befehls „Datenbank wiederherstellen“ mit der Option „Mitgliedschaft auslassen“ schließt die neue entsprechende JSON-Option ein, wenn SQL Server 2017, AS Server oder AS Azure verwendet wird
- Es wurde ein sehr seltenes Problem behoben, bei dem das Dialogfeld „Datenbank löschen“ beim Laden einen Fehler auslösen konnte
- Es wurde ein Problem behoben, das beim Versuch auftreten konnte, Partitionen im Modell mit Kompatibilitätsgrad 1400 anzuzeigen, die eine Mischung aus SQL-Abfragen und Partitionsdefinitionen enthalten

**Integration Services**
- Es wurde ein Problem behoben, bei dem die Berichte zu Ausführungsinformationen des SSISDB-Katalogs nicht angezeigt werden konnten
- Es wurde ein Problem in SSMS behoben, bei dem eine große Anzahl von Projekten/Paketen zu Leistungsproblemen führen konnte

## <a name="downloadssdtmediadownloadpng-ssms-171httpsgomicrosoftcomfwlinklinkid849819"></a>![download (Herunterladen von)](../ssdt/media/download.png) [SSMS 17.1](https://go.microsoft.com/fwlink/?linkid=849819)
Allgemein verfügbar | Buildnummer: 14.0.17119.0

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

### <a name="enhancements"></a>Erweiterungen

- Profiler: „Hilfe“ > „Info“ zeigt jetzt die Versionsnummer (z. B. 17.1) an.
- Benutzer von Analysis Services können die Anmeldeinformationen für ihre Datenquellen für 1200 TM-Modelle und höher über das Kontextmenü auf der Datenquelle aktualisieren
- Integrierte SSIS-Berichte zeigen nun Protokolle der Ausführung der SSIS-Horizontalskalierung in CTP 2.1 an
- Verwaltungsanwendung der SSIS-Horizontalskalierung
  - Anzeigen grundlegender Informationen zum Master für horizontales Skalieren
  - Einfaches Hinzufügen eines Workers zur Bereitstellung für horizontales Skalieren
  - Anzeigen aller Worker für horizontales Skalieren und grundlegender Informationen zu diesen sowie deren einfache Aktivierung oder Deaktivierung

### <a name="bug-fixes"></a>Behebung von Programmfehlern
- Always On:
  - Ein Problem wurde behoben, bei dem die Eigenschaften eines Verfügbarkeitsreplikats immer im Modus „Automatisches Failover“ für WSFC-Verfügbarkeitsgruppen angezeigt wurden.
  - Ein Problem wurde behoben, bei dem die schreibgeschützte Routingliste beim Aktualisieren der Verfügbarkeitsgruppe überschrieben wurde
- Always Encrypted: Ein Problem wurde behoben, bei dem in der generierten Protokolldatei die Informationen von DacFx fehlten.
- ShowPlan: Ein Problem wurde behoben, bei dem auf der Benutzeroberfläche immer das tatsächliche Jointyp-Attribut für nichtadaptive Verknüpfungsoperatoren angezeigt wurde.
- Setup:
  - Ein Problem wurde behoben, bei dem SSMS 17.0 SSDT auf Visual Studio 2013 unterbrach [Microsoft Connect-Artikel 3133479]
  - Ein Problem wurde behoben, bei dem das Klicken auf „Neustart“ am Ende des Setups nicht zu einem Neustart des Computers führte.
- Skripterstellung: Es wird vorübergehend verhindert, dass SSMS versehentlich Azure-Datenbankobjekte löscht, wenn versucht wird, ein Skript für den Löschvorgang zu erstellen, indem diese Option deaktiviert wird.  Dies wird in einer zukünftigen Version von SSMS behoben.
- Objekt-Explorer: Ein Problem wurde behoben, bei dem der Knoten „Datenbanken“ nicht erweitert wurde, wenn er mit einer Azure-Datenbank verbunden wurde, die mit „AS COPY“ erstellt wurde.

## <a name="downloadssdtmediadownloadpng-ssms-170httpsgomicrosoftcomfwlinklinkid847722"></a>![download (Herunterladen von)](../ssdt/media/download.png) [SSMS 17.0](https://go.microsoft.com/fwlink/?LinkID=847722)
Allgemein verfügbar | Buildnummer: 14.0.17099.0

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=847722&clcid=0x40a)

### <a name="enhancements"></a>Erweiterungen 

- Upgradepaket und Windows Software Update Services (WSUS): Zukünftige 17.X-Versionen enthalten ein kleineres, kumulatives Updatepaket 
  - Das Updatepaket wird auch im WSUS-Katalog veröffentlicht werden  
- Symbolupdates: Symbole wurden aktualisiert, sind nun mit den von VS Shell bereitgestellten Symbolen konsistent und unterstützen hohe DPI-Auflösungen - Neue SSMS- und Profiler-Programmsymbole zur Unterscheidung zwischen 16.X und 17.X-Versionen
- SQL PowerShell-Modul
  - Das SQL Server PowerShell-Modul wurde aus SSMS entfernt und wird nun über den PowerShell-Katalog geliefert (PowerShell 5.0 ist nun erforderlich, um die Modulversionsverwaltung zu unterstützen)
  - Verschiedene Verbesserungen der Darstellung (Formatierung) einiger SMO-Objekte (z.B. zeigen Datenbanken nun die Größe und den verfügbaren Speicherplatz an und Tabellen zeigen Zeilenanzahl und Speicherplatznutzung an)
  - Eine neu hinzugefügte farbliche Kennzeichnung beim Aufrufen der PowerShell-Eingabeaufforderung im Menü „PowerShell starten“ in Outlook Express
  - Parameter -ClusterType und -RequiredCopiesToCommit zu VG-Cmdlets hinzugefügt (Cmdlets New-SqlAvailabilityGroup, Join-SqlAvailabilityGroup und Set-SqlAvailabilityGroup)
  - Parameter -ActiveDirectoryAuthority und -AzureKeyVaultResourceId zu Cmdlet Add-SqlAzureAuthenticationContext hinzugefügt
  - Die Cmdlets „Revoke-SqlAvailabilityGroupCreateAnyDatabase“, „Grant-SqlAvailabilityGroupCreateAnyDatabase“ und „Set-SqlAvailabilityReplicaRoleToSecondary“ wurden hinzugefügt
  - Der Parameter „SeedingMode“ wurde zu den Cmdlets „Set-SqlAvailabilityReplica“ und „New-SqlAvailabilityReplica“ hinzugefügt
  - Der Parameter „-ConnectionString“ wurde zu „Get-SqlDatabase“ hinzugefügt
- SQL Server unter Linux: Allgemeine Verbesserungen und Fehlerbehebungen für den Protokollversand
  - Unterstützung für die nativen Linux-Pfade „Datenbank anfügen“, „Datenbank wiederherstellen“ und „Datenbank sichern“ wurde hinzugefügt
  - Unterstützung für native Linux-Pfade für den Zielordner von Überwachungsprotokollen wurde hinzugefügt
- Analysis Services
  - DAX-Abfragefenster:
    - Im Editor übereinstimmende Klammern
    - Syntaxunterstützung von DEFINE MEASURE und DEFINE VAR
    - Verschiedene IntelliSense-Verbesserungen
  - Universelle Authentifizierung
    - Ermöglicht Benutzern das Festlegen eines Benutzernamens ohne Kennwort und das Azure-Anmeldedialogfeld kümmert sich um die Verbindung
  - SSMS-PQ-Integration: 
    - Skripterstellung für strukturierte Datenquellen funktioniert 
    - Anzeigen und Bearbeiten strukturierter Datenquellen auf der PQ-Benutzeroberfläche
- Neue Vorlage für „Add Unique Constraint“ (Eindeutige Einschränkung hinzufügen)
- Showplan: Im Eigenschaftenfenster für verstrichene Zeit über alle Threads hinweg „max“ statt „sum“ anzeigen - Neue Mem Grant Operator-Eigenschaften verfügbar machen - Schaltfläche „Abfrage bearbeiten“ in der Live-Abfragestatistik wurde aktiviert - Unterstützung für verschachtelte Ausführung
  - Neue Option bei „Tatsächlichen Ausführungsplan analysieren“
  - Allgemeine Verbesserungen beim Showplan-Vergleich
  - Eine neu eingeführte Funktion im Feature „Showplan-Vergleich“, die es ermöglicht, Unterschiede der Kardinalitätsschätzung zwischen abgeglichenen Knoten zweier Abfragepläne zu erkennen und grundlegende Analysen möglicher Hauptursachen durchzuführen
- Configuration Manager wurde vom Registrierte Server-Explorer entfernt
- Lesen von Überwachungsprotokollen vom Azure-Blobspeicher aktivieren
- Zusätzliche Parametrisierung für „Always Encrypted“; weitere Informationen finden Sie [hier](https://blogs.msdn.microsoft.com/sqlsecurity/2016/12/13/parameterization-for-always-encrypted-using-ssms-to-insert-into-update-and-filter-by-encrypted-columns/) 
- AUTH-Verbindung von AAD Universal zur Azure SQL-Datenbank unterstützt benutzerdefinierte Mandanten-ID 
- „Skripts generieren“ für die Azure SQL-Datenbank skriptet jetzt Volltext, Regeln und Datenbanken
- Korrekturen beim Branding auf dem Begrüßungsbildschirm von SSMS und Profiler
- Die Benutzeroberfläche des Steuerungspunkts für Hilfsprogramme wurde aus SSMS entfernt
- SSMS kann nun Azure SQL-Datenbanken der PremiumRS-Edition erstellen.
- Always On-Verfügbarkeitsgruppen
  - Unterstützung für neue Clustertypen wurde hinzugefügt: EXTERNE und KEINE: Unterstützung für SQL Server unter Linux wurde hinzugefügt. Automatisches Seeding wurde als Option für die anfängliche Datensynchronisierung hinzugefügt. Einige Mängel z. B. beim Umgang mit der Endpunkt-URL, bei der Datenbankaktualisierung und beim Layout der Benutzeroberfläche wurden behoben. Mit Azure-Replikaten verbundene Funktionen wurden entfernt
  - IntelliSense wurde für mehrere Schlüsselwörter von Verfügbarkeitsgruppen verbessert
- Aktivitätsmonitor
  - Im SSMS-Ausgabefenster wurde der neue Bereich „Aktivitätsmonitor“ hinzugefügt
  - Die Meldung zu Verbindungsfehler/Timeout wurde so geändert, dass sie Informationen an das Ausgabefenster und nicht an eine Popupmeldung protokolliert
  - Das leere Diagramm (5. Diagramm) im Abschnitt „Übersicht“ wurde entfernt
  - Beim Titel in „Übersicht“ wird nun „(angehalten)“ angezeigt, wenn die Datensammlung für den Aktivitätsmonitor angehalten wird
  - Graph-Erweiterungen für SQL Server: Neue Symbole für Diagrammknoten und Rahmentabellen - Diagrammknoten und Rahmentabelle werden im Ordner „Graph-Tabellen“ angezeigt - Vorlagen für das Erstellen von Diagrammknoten und Rahmentabellen sind verfügbar
- Darstellungsmodus: 3 neue Aufgaben, die über Schnellstart (STRG-Q) verfügbar sind - PresentOn: Präsentationsmodus aktivieren - PresentEdit: Präsentationsschriftgrade für Präsentationsmodus bearbeiten.  „Text Editor font“ (Text Editor-Schriftart) für den Abfrageeditor.  „Environment font“ (Umgebungsschriftart) für andere Komponenten.
RestoreDefaultFonts – Auf Standardeinstellungen zurücksetzen. Der Befehl „PresentOff“ ist derzeit nicht verfügbar. Verwenden „Sie RestoreDefaultFonts“, um den Präsentationsmodus* zu deaktivieren.

### <a name="bug-fixes"></a>Behebung von Programmfehlern

- Ein Problem wurde behoben, bei dem SSMS abstürzte, wenn Showplan über das Touchpad des Surface Books gescrollt wurde
- Ein Problem wurde behoben, bei dem SSMS für lange Zeit hing, während die Eigenschaften einer Datenbank abgerufen wurden, die wiederhergestellt wurde oder offline war 
- Ein Problem wurde behoben, bei dem „Help Viewer“ in RC-Builds nicht geöffnet werden konnte
- Ein Problem wurde behoben, bei dem Elemente der Toolbox „Wartungsplantasks“ in SSMS fehlten
- Ein Problem in SSMS wurde behoben, bei dem ein Benutzer eine Datenbank nicht verkleinern konnte, wenn deren Name geschweifte Klammern enthielt [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3122618)
- Ein Problem wurde behoben, bei dem SSMS versuchte, ein Skript für den Löschvorgang einer Azure-Datenbank zu erstellen, dabei aber die Datenbank selbst löschte [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3131458/)
- Ein Problem wurde behoben, bei dem für Standardwerte für benutzerdefinierte Tabellentypen kein Skript erstellt wurde. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3119027)
- Eine weitere Runde von Leistungsverbesserungen um das Kontextmenü für Indizes. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3120783)
- Ein Problem wurde behoben, das übermäßiges Flimmern verursachte, wenn der Mauszeiger auf einen fehlenden Index im Ausführungsplan zeigte. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3118510)
- Ein Problem wurde behoben, bei dem SSMS die Datenbank beim Erstellen des Skripts [Connect Item (Connect-Artikel)](https://connect.microsoft.com/SQLServer/feedback/details/3118550) offline schaltete
- Verschiedene UI-Fehlerbehebungen auf lokalisierten (nicht englischen) Versionen von SSMS.
- Ein Problem wurde behoben, bei dem der Knoten „Always Encrypted Keys“ (Always Encrypted-Schlüssel) beim Adressieren von SQL 2016 SP1 Standard Edition fehlte.
- Always Encrypted: Das Menü „Always Encrypted“ wurde beim Adressieren von SQL 2016 RTM Standard Edition oder eines beliebigen SQL 2014-Servers (und früherer Versionen) falsch aktiviert. Ein Problem wurde behoben, bei dem IntelliSense einen Fehler meldet, wenn die Syntax CREATE OR ALTER verwendet wird. Ein Problem wurde behoben, bei dem die Verschlüsselung versagt, falls CMK/CEK Zeichen enthalten, die mit Escapezeichen versehen (d. h. in Klammern eingeschlossen) werden sollten. Tritt eine Ausnahme in SSMS auf, dass nicht genügend Arbeitsspeicher vorhanden ist, wird dem Benutzer ein Fehler angezeigt, der stattdessen die Verwendung der nativen (64 Bit) PowerShell vorschlägt.
Ein Problem wurde behoben, bei dem der AE-Assistent einen Fehler verursacht hat, wenn der Benutzer Resource Group Manager-Abonnements anstelle von klassischen Azure-Abonnements verwendete - Ein Problem wurde behoben, bei dem der AE-Assistent einen falschen Fehler anzeigte, wenn der Benutzer keine Berechtigungen in Abonnements hatte oder in diesen nicht über Azure Key Vault verfügte.
Ein Problem im AE-Assistenten wurde behoben, bei dem im Fall von mehreren AADs die Azure-Abonnements nicht auf der Azure Key Vault-Anmeldeseite angezeigt wurden – Ein Problem im AE-Assistent wurde behoben, bei dem die Azure-Abonnements, für die der Benutzer über eine Leseberechtigung verfügt, nicht auf der Azure Key Vault-Anmeldeseite angezeigt wurden
  - Ein Problem wurde behoben, bei dem Ressourcendateien nicht ordnungsgemäß geladen werden, was zu ungenauen Fehlermeldungen führte
- Verbesserter Kontrast von Hyperlinks auf SSMS-Setup-Seite
- Problem der Nichtanzeige von PolyBase-Knoten beim Verbinden mit SQL Server Express (2016 SP1) behoben
- Ein Problem wurde behoben, bei dem SSMS den Kompatibilitätsgrad einer Azure-Datenbank nicht auf v140 ändern konnte
- Verbesserte Leistung von Objekt-Explorer beim Erweitern der Liste der Azure-Datenbanken [Connect Item (Connect-Artikel)](https://connect.microsoft.com/SQLServer/feedback/details/3100675)
- Ein Problem wurde behoben, bei dem das Kontextmenüelement „View SQL Server Log“ (SQL Server-Protokoll anzeigen) für nicht-relationale Servertypen (AS\RS\IS) nicht ordnungsgemäß angezeigt wurde 
- Ein Problem wurde behoben, bei dem das Prüfen der Syntax einer Analysis Services-Partitionsabfrage mithilfe von SQL-Authentifizierung zu einer Benachrichtigung führen konnte, dass die Anmeldung fehlgeschlagen ist
- Ein Problem wurde behoben, bei dem das Umbenennen eines mit Preview 1400 kompatiblen Tabellenmodells der Ebene AS in SSMS fehlschlug
- Ein Problem vom Typ „operation failed on model” (Fehler beim Vorgang auf Modell), das in seltenen Fällen nach dem Versuch auftreten konnte, eine ungültige Operation auf dem AS-Server durchzuführen, lokale Änderungen nach nicht erfolgreichem Speichern auf dem Modell zurücksetzen
- Ein Tippfehler im Popup-Dialogfeld „Analysis Services Synchronize Database“ wurde verbessert
- Dialogfelder von „Backup/Restore container“ (Container sichern/wiederherstellen) werden bei mehreren Bildschirmeinstellungen abseits des Bildschirms angezeigt. 
- „SecurityPolicy create“ (Sicherheitsrichtlinie erstellen) schlägt fehl, wenn das Zielobjekt eine eckige Klammer (`]`) im Namen hat.
- Das Menü „Zuletzt verwendete öffnen“ in SSMS 2016 zeigt keine zuletzt gespeicherten Dateien an. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)
- Das Zurücksetzen der Benutzereinstellungen nach einem VS-Shell Update wurde behoben.
- Ein Problem wurde behoben, das einen Benutzer daran hinderte, den Kompatibilitätsgrad einer Datenbank in SQL Server 2017 anzupassen
- Abfragefenster, die die Authentifizierung mit AAD Universal verwenden, können die Abfrage nach einer Stunde nicht mehr aktualisieren.
- Die Benutzeroberfläche des Steuerungspunkts für Hilfsprogramme wurde aus SSMS entfernt.
- Verbindungen, die mit der Authentifizierung von AD Universal hergestellt wurden, können Daten nach Ablauf das anfänglichen Tokens nicht mehr abfragen.
- Das Skripten von Regeln von der Azure SQL-Datenbank in die Azure SQL-Datenbank ist nicht möglich.
- Das Problem wurde behoben, das dazu führte, dass SQL PowerShell keine Legacy-SQL-Instanzen verbinden konnte (2014 und frühere Versionen). [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/1138754/sql-server-sqlps-powershell-module-fails-connection-to-sql-2012-instance)
- Das Problem wurde behoben, das zum Absturz von SSMS geführt hat, wenn das Importieren registrierter Server fehlgeschlagen war.
- Ein Problem wurde behoben, das zum Absturz von SSMS geführt hat, wenn ein Benutzer bestimmte Berechtigungen in einer Datenbank hatte.
- SSMS – Tabellen verschwinden beim Prüfen der Sichten von der Entwurfsoberfläche. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/2946125/ssms-tables-disappears-from-design-surface-while-reviewing-views) 
- Der Benutzer kann mit der Bildlaufleiste einer Tabelle nicht durch den Tabelleninhalt scrollen – dies ist nur mit den Nach-Oben/Nach-unten-Pfeiltasten möglich. Außerdem ist es möglich, durch den Tabelleninhalt zu scrollen, nachdem versucht wurde, mithilfe der Scrollleiste zu scrollen – das ist ein Programmfehler. [Microsoft Connect-Artikel](
https://connect.microsoft.com/SQLServer/feedback/details/3106561/sql-server-manager-2016-bug-in-design-view) 
- Registrierte Server zeigen keine Symbole mehr an, nachdem der Stammknoten aktualisiert wurde.
- Die Skript-Schaltfläche für „Datenbank erstellen“ auf Servern von Azure v12 führt ein Skript aus und zeigt anschließend die Meldung „No action to be scripted“ (Keine Aktion für das Skript vorhanden) an.
- Das Dialogfeld „Verbindung mit Server herstellen“ in SSMS löscht die Registerkarte „Weitere Eigenschaften“ nicht für jede neue Verbindung.
- „Task-Skript generieren“ generiert keine Skripts für „Datenbank erstellen“ in der Azure SQL-Datenbank.
- Die Bildlaufleiste im Sicht-Designer scheint deaktiviert zu sein.
- AVK-Schlüsselpfade „Always Encrypted“ enthalten keine Versions-IDs.
- Verminderte Anzahl der Engine-Editionsabfragen im Abfragefenster. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3113387)
- Fehler bei „Always Encrypted“ durch das Aktualisieren von Modulen nach der Verschlüsselung werden falsch verarbeitet.
- Verändertes Standardverbindungstimeout für OLTP und OLAP zwischen 15 und 30 Sekunden, um eine Klasse ignorierter Verbindungsfehler zu korrigieren. 
- Der Absturz von SSMS nach dem Starten eines benutzerdefinierten Berichts wurde behoben. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3118856)
- Das Problem, das bei der Ausführung von „Skript generieren...“ bei Azure SQL-Datenbank-Instanzen zu Fehlern geführt hat, wurde behoben.
- „Script As“ und der „Assistent zum Generieren von Skripts“ wurden korrigiert, sodass keine zusätzlichen Zeilenvorschübe mehr eingefügt werden, wenn Objekte wie z.B. gespeicherte Prozeduren geskriptet werden. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3115850)
- Der SQLAS PowerShell-Anbieter: Hinzufügen der Eigenschaft „Add LastProcessed“ (Zuletzt verarbeitet) in die Ordner „Dimension“ (Dimension) und „MeasureGroup“ (Measuregruppe). [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3111879)
- Live-Abfragestatistik: das Problem wurde behoben, dass nur die erste Abfrage in einem Batch angezeigt wurde. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3114221)  
- Showplan: im Eigenschaftenfenster über alle Threads hinweg „max“ statt „sum“ anzeigen.
- Abfragespeicher: einen neuen Bericht in Abfragen mit hoher Ausführungsvariation hinzufügen.
- Leistungsprobleme des Objekt-Explorers: [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3114074) Das Tabellenkontextmenü hängt vorübergehend. SSMS ist sehr langsam, wenn mit der rechten Maustaste auf den Tabellenindex geklickt wurde (über eine Remote(internet)verbindung). Tabellenabfragen, bei denen die Sortierung auf dem Server stattfindet, vermeiden
- Azure Bereitstellungsassistent (Datenbank in Azure VM bereitstellen) wurde aus SSMS entfernt
- Das Problem wurde behoben, dass fehlende Indices nicht im Ausführungsplan von SSMS angezeigt wurden [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3114194)
- Häufig auftretende Probleme beim Beenden von SSMS (Absturz) wurden behoben.
- Problem beim Öffnen des Kontextmenüs auf den Knoten der PolyBase- und Erweiterungsgruppen im Objekt-Explorer behoben ([Microsoft Connect](https://connect.microsoft.com/SQLServer/feedback/details/3115128))
- Problem beim Anzeigen der Berechtigungen einer Datenbank (Absturz) behoben
- Abfragespeicher: allgemeine Erweiterungen von Kontextmenüelementen für Ergebnisrastern von Abfragespeicherberichten
- Konfigurieren von „Always Encrypted“ schlägt für eine vorhandene Tabelle fehl mit Fehlern für nicht verknüpfte Objekte. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3103181)
- Konfigurieren von „Always Encrypted“ funktioniert nicht für eine vorhandene Datenbank mit mehreren Schemas. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3109591)
- Der Assistent für „Always Encrypted“ und „Verschlüsselte Spaltendaten“ versagt, wenn die Datenbank Sichten enthält, die auf Systemsichten verweisen. [Microsoft Connect-Artikel](https://connect.microsoft.com/SQLServer/feedback/details/3111925)
- Bei der Verschlüsselung mit „Always Encrypted“ werden Fehler durch das Aktualisieren von Modulen nach der Verschlüsselung falsch verarbeitet.
- Probleme mit dem Absturz der Benutzeroberfläche im Dialogfeld „Neue Serverregistrierung“ wurden behoben
- Beheben eines DMF-Problems, die Benutzeroberfläche aktualisiert Ausdrücke inkorrekt, die konstante Zeichenfolgewerte mit Anführungszeichen enthalten
- Das Problem wurde behoben, das zum Absturz von SSMS beim Ausführen von benutzerdefinierten Berichten geführt hat
- Menüelement „Execution in Scale Out...“ (Ausführung in horizontaler Hochskalierung) in den Ordnerknoten einfügen
- Ein Problem mit der Funktion zum Erstellen einer Liste zugelassener IP-Adressen für die Firewall einer Azure SQL-Datenbank wurde behoben.
- Ein Problem in SSMS wurde behoben, bei dem beim Bearbeiten der Source einer multidimensionalen AS-Partition die Ausnahme ausgelöst wurde, dass der Objektverweis nicht festgelegt ist
- Ein Problem in SSMS wurde behoben, bei dem beim Löschen einer Kundenassembly von einem multidimensionalen AS-Server die Ausnahme ausgelöst wurde, dass der Objektverweis nicht festgelegt ist
- Ein Problem wurde behoben, bei dem das Umbenennen einer tabellarischen AS-Datenbank 1400 fehlschlug
- Ein Problem bei der Skripterstellung für eine tabellarische AS-Datenquelle mit Kompatibilitätsgrad 1400 aus dem Dialogfeld „Verbindungseigenschaften“ wurde behoben
- Die Annahme wurde entfernt, dass Tabellen im AS-Modell mit Kompatibilitätsgrad 1400 mindestens eine Partition aufweisen
- Mit CTRL+R kann nun der Ergebnisbereich im DAX-Abfrage-Editor von SSMS umgeschaltet werden


## <a name="downloadssdtmediadownloadpng-ssms-1653httpsgomicrosoftcomfwlinklinkid840946"></a>![download (Herunterladen von)](../ssdt/media/download.png) [SSMS 16.5.3](https://go.microsoft.com/fwlink/?LinkID=840946)
Allgemein verfügbar | Buildnummer: 13.0.16106.4

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=840946&clcid=0x40a)

In dieser Version wurden folgende Probleme behoben:

* Das seit SSMS 16.5.2 auftretende Problem wurde behoben, das die Erweiterung des Knotens „Tabelle“ verursacht hat, wenn die Tabelle mindestens eine Sparsespalte aufwies.

* Benutzer können SSIS-Pakete bereitstellen, die den OData-Verbindungs-Manager enthalten und die eine AX/CRM-Onlineressource von Microsoft Dynamix mit dem SSIS-Katalog verbinden. Weitere Informationen finden Sie unter [OData-Verbindungs-Manager](../integration-services/connection-manager/odata-connection-manager.md).

* Konfigurieren von „Always Encrypted“ schlägt für eine vorhandene Tabelle fehl mit Fehlern für nicht verknüpfte Objekte. [Connect-ID 3103181](https://connect.microsoft.com/SQLServer/feedback/details/3103181/setting-up-always-encrypted-on-an-existing-table-fails-with-errors-on-unrelated-objects)

* Konfigurieren von „Always Encrypted“ funktioniert nicht für eine vorhandene Datenbank mit mehreren Schemas. [Connect-ID 3109591](https://connect.microsoft.com/SQLServer/feedback/details/3109591/sql-server-2016-always-encrypted-against-existing-database-with-multiple-schemas-doesnt-work)

* Der Assistent für „Always Encrypted“ und „Verschlüsselte Spaltendaten“ versagt, wenn die Datenbank Sichten enthält, die auf Systemsichten verweisen. [Connect-ID 3111925](https://connect.microsoft.com/SQLServer/feedback/details/3111925/sql-server-2016-always-encrypted-encrypted-column-wizard-failed-task-failed-due-to-following-error-cannot-save-package-to-file-the-model-has-build-blocking-errors)

* Bei der Verschlüsselung mit „Always Encrypted“ werden Fehler durch das Aktualisieren von Modulen nach der Verschlüsselung falsch verarbeitet.

* Das Menü *Zuletzt verwendete öffnen* zeigt keine zuletzt gespeicherten Dateien an. [Connect-ID 3113288](https://connect.microsoft.com/SQLServer/feedback/details/3113288/ssms-2016-open-recent-menu-doesnt-show-recently-saved-files)

* SSMS ist sehr langsam, wenn mit der rechten Maustaste auf den Tabellenindex geklickt wurde (über eine Remote(internet)verbindung). [Connect-ID 3114074](https://connect.microsoft.com/SQLServer/feedback/details/3114074/ssms-slow-when-right-clicking-an-index-for-a-table-over-a-remote-internet-connection)

* Ein Problem mit der Bildlaufleiste von SQL Designer wurde behoben. [Connect-ID 3114856](https://connect.microsoft.com/SQLServer/feedback/details/3114856/bug-in-scrollbar-on-sql-desginer-in-ssms-2016)

* Das Tabellenkontextmenü hängt vorübergehend 
 
* SSMS löst gelegentlich Ausnahmen auf dem Aktivitätsmonitor aus und stürzt anschließen ab. [Connect-ID 697527](https://connect.microsoft.com/SQLServer/feedback/details/697527/)

* SSMS 2016 stürzt ab mit der Fehlermeldung „The process was terminated due to an internal error in the .NET Runtime at IP 71AF8579 (71AE0000) with exit code 80131506“ (Der Vorgang wurde aufgrund eines internen Fehlers in der .NET-Laufzeit in der IP 71AF8579 (71AE0000) mit dem Exitcode 80131506 beendet).


## <a name="uninstall-and-reinstall-ssms-17x"></a>Deinstallation und Neuinstallation von SSMS 17.x

Wenn Sie Probleme bei der SSMS-Installation haben und die Standarddeinstallation und erneute Installation diese nicht lösen können, können Sie zunächst versuchen, Visual Studio 2015 IsoShell zu [reparieren](https://support.microsoft.com/help/4028054/windows-10-repair-or-remove-programs). Falls die Reparatur von Visual Studio 2015 IsoShell das Problem nicht behebt, können womöglich die folgenden bewährten Lösungen helfen:

1. Deinstallieren Sie SSMS so, wie Sie auch jede andere Anwendung deinstallieren würden (je nach Windows-Version über *Apps & Features* oder *Programme und Funktionen*).

2. Deinstallieren Sie Visual Studio 2015 IsoShell **über eine erweiterte CMD-Aufforderung**:

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```

    ```vs_isoshell.exe /Uninstall /Force /PromptRestart```

3. Deinstallieren Sie Microsoft Visual C++ 2015 Redistributable genau so, wie Sie auch jede andere Anwendung deinstallieren würden. Deinstallieren Sie jeweils x86 und x64, falls sich diese Versionen auf Ihrem Computer befinden.

4. Installieren Sie Visual Studio 2015 IsoShell erneut **über eine erweiterte CMD-Aufforderung**:  

    ```PUSHD "C:\ProgramData\Package Cache\FE948F0DAB52EB8CB5A740A77D8934B9E1A8E301\redist"```  

    ```vs_isoshell.exe /PromptRestart```

5. Installieren Sie SSMS erneut.

6. Führen Sie ein Upgrade auf die [neueste Version von Visual C++ 2015 Redistributable](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) aus, wenn Sie diese noch nicht besitzen.

## <a name="additional-downloads"></a>Weitere Downloads

Eine Liste aller SQL Server Management Studio-Downloads finden Sie im [Microsoft Download Center](https://www.microsoft.com/download/search.aspx?q=sql%20server%20management%20studio&p=0&r=10&t=&s=Relevancy~Descending).  
  
Das aktuelle Release von SQL Server Management Studio finden Sie unter [Herunterladen von SQL Server Management Studio &#40;SSMS&#41;](../ssms/download-sql-server-management-studio-ssms.md).  
