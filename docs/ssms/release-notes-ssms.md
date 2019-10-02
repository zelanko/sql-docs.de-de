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
ms.custom: ''
ms.date: 09/24/2019
ms.openlocfilehash: 776f251e574ae2fa8165e4dd4d4feee6a5cf9968
ms.sourcegitcommit: 4c7151f9f3f341f8eae70cb2945f3732ddba54af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71326084"
---
# <a name="release-notes-for-sql-server-management-studio-ssms"></a>Versionshinweise zu SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Dieser Artikel enthält Details zu Updates, Verbesserungen und Fehlerbehebungen für die aktuellen und früheren Versionen von SSMS.

<!--
The latest ## H2 section of this Release Notes article has been reformatted to match the new standard.
The new standard replaces the use of bullet lists with the 2-column markdown table format.
Please use the new 2-column table format going forward.
And please do include the final blank row of "| &nbsp;| &nbsp;|".

The ## H2 titles are also being shortened, by the removal of unnecessary repetitive strings.
In this case, "## SSMS 17.9" is being shortened to "## 17.9" (as one standard actual example).
Also, we are appending the 'Month yyyy.'

Also, this file has been renamed to the new standard, which calls for the file name to be with "release-notes-[techAreaName].md."
The old name for this file was 'sql-server-management-studio-changelog-ssms.md'.
But today the new file name is 'release-notes-ssms.md' (still in 'docs/ssms/').

Thank you.
GeneMi. 2019/04/02.
-->

## <a name="ssms-183"></a>SSMS 18.3 

Herunterladen: [SSMS 18.3 herunterladen](download-sql-server-management-studio-ssms.md)  
Buildnummer: 15.0.18178.0  
Releasedatum: 23. September 2019

SSMS 18.3 ist das neueste Release von SSMS mit allgemeiner Verfügbarkeit (GA). Frühere Versionen von SSMS finden Sie weiter unten im Abschnitt [Vorgängerversionen von SSMS](release-notes-ssms.md#previous-ssms-releases).

18.3 ist ein Update von 18.2 mit den folgenden neuen Elementen und Fehlerbehebungen.

## <a name="whats-new-in-183"></a>Neues in Version 18.3

| Neues Element | Details |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Datenklassifizierung | Hinzufügen von Datenklassifizierungsinformationen zur Spalteneigenschaften-Benutzeroberfläche (*Informationstyp*, *Informationstyp-ID*, *Vertraulichkeitsbezeichnung* und *Vertraulichkeitsbezeichnungs-ID* werden auf der Benutzeroberfläche von SSMS nicht verfügbar gemacht). |
| IntelliSense/Editor | Aktualisierte Unterstützung für vor Kurzem zu SQL Server 2019 hinzugefügte Features (Beispiel: „ALTER SERVER CONFIGURATION“). | 
| Integration Services | Fügen Sie ein neues Auswahlmenü „itemr `Tools > Migrate to Azure > Configure Azure-enabled DTExec`“ hinzu, das Ausführungen von SSIS-Paketen in der Azure-SSIS Integration Runtime als SSIS-Paket ausführen-Aktivitäten in ADF-Pipelines aufruft. |
| SMO/Skripterstellung | Hinzugefügte Unterstützung für Supportskripts der UNIQUE-Einschränkung von Azure SQL DW. |
| SMO/Skripterstellung | Datenklassifizierung </br> Hinzugefügte Unterstützung für SQL Version 10 (SQL 2008) und höher. </br> Neues Vertraulichkeitsattribut ‚rank‘ für SQL Version 15 (SQL 2019) und höher sowie Azure SQL DB. |
| SMO/Skripterstellung | [SQL-Bewertungs-API](../sql-assessment-api/sql-assessment-api-overview.md): Hinzugefügte Versionsverwaltung zum Regelsatzformat. |
| SMO/Skripterstellung | [SQL-Bewertungs-API](../sql-assessment-api/sql-assessment-api-overview.md): Neue Überprüfungen hinzugefügt. |
| SMO/Skripterstellung | [SQL-Bewertungs-API](../sql-assessment-api/sql-assessment-api-overview.md): Hinzugefügte Unterstützung für verwaltete Azure SQL Datenbank-Instanzen. |
| SMO/Skripterstellung | [SQL-Bewertungs-API](../sql-assessment-api/sql-assessment-api-overview.md): Aktualisierte Standardansicht von Cmdlets zum Anzeigen von Ergebnissen als Tabelle. |

## <a name="bug-fixes-in-183"></a>Fehlerkorrekturen in Version 18.3

| Neues Element | Details |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Analysis Services | Behobenes Skalierungsproblem im MDX-Abfrage-Editor|
| Analysis Services | Es wurde ein Problem in der XEvent-Benutzeroberfläche behoben, das verhindert, dass Benutzer eine neue Sitzung erstellen können. |
| Datenbankbereitstellung in SQL Azure | Es wurde ein Problem behoben (in DacFx), das zu fehlender Funktion dieses Features führte.|
| SSMS allgemein | Es wurde ein Problem behoben, das zu einem Absturz von SSMS beim Verwenden der Sortierfunktion in der XEvent-Anzeige führte. |
| SSMS allgemein | Es wurden lange ausstehende Probleme behoben, die zu einem unbegrenzten Hängen beim der SSMS-Datenbankwiederherstellung führen konnte. </br></br> Weitere Details finden Sie in den UserVoice-Beiträgen:  </br> [Datenbank wiederherstellen: Langsames Laden von ausgewählten Sicherungsmedien](https://feedback.azure.com/forums/908035/suggestions/32899099/).  </br> [SSMS 2016 reagiert in den Dialogfeldern zur Datenwiederherstellung sehr langsam](https://feedback.azure.com/forums/908035/suggestions/32900767/). </br> [Die Wiederherstellung von Datenbanken erfolgt langsam](https://feedback.azure.com/forums/908035/suggestions/32900224/).  </br> [Die Wiederherstellung von Datenbanken von einem Medium hängt sich beim Klicken auf „...“ auf](https://feedback.azure.com/forums/908035/suggestions/34281658/).  |
| SSMS allgemein | Es wurde ein Problem behoben, bei dem die Standardsprache für alle Anmeldungen arabisch war. </br></br> Weitere Details finden Sie im UserVoice-Beitrag: [SSMS 18.2 default language display bug](https://feedback.azure.com/forums/908035/suggestions/38236363) (SSMS 18.2-Anzeigefehler der Standardsprache). |
| SSMS allgemein | Das schlecht zu sehende Dialogfeld für *Abfrageoptionen* (wenn der Benutzer auf das T-SQL-Editor-Fenster klickt) wurde korrigiert, indem seine Größe veränderlich gemacht wurde.|
| SSMS allgemein | Die im Ergebnisraster bzw. in der Datei angezeigte Meldung *Abschlusszeit* (in SSMS 18.2 eingeführt) ist jetzt unter „Extras“ > „Optionen“ > „Abfrageausführung“ > „SQL Server“ > „Erweitert“ > „Abschlusszeit anzeigen“ konfigurierbar. |
| SSMS allgemein | Im Verbindungsdialogfeld wurden *Active Directory – Kennwort* und *Active Directory – Integriert* durch *Azure Active Directory – Kennwort* bzw. *Azure Active Directory – Integriert* ersetzt. |
| SSMS allgemein | Es wurde ein Problem behoben, das Benutzer daran hindert, SSMS zum Konfigurieren der Ablaufverfolgung für von Azure verwaltete SQL-Instanzen zu verwenden, die sich in einer Zeitzone mit negativem UTC-Versatz befinden. |
| SSMS allgemein | Es wurde ein Problem in der XEvent-Benutzeroberfläche behoben, bei dem das Zeigen auf das Raster die Auswahl von Zeilen bewirkte. </br></br> Weitere Details finden Sie im UserVoice-Beitrag: [Die Benutzeroberfläche für erweiterte Ereignisse von SSMS wählt beim Draufzeigen Aktionen aus](https://feedback.azure.com/forums/908035/suggestions/38262124). |
| Importieren von Flatfiles | Das Problem wurde behoben, dass „Flatfile importieren“ nicht alle Daten importierte, da dem Benutzer die Wahl zwischen der Erkennung einfacher und Rich-Datentypen gegeben wurde.</br></br> Weitere Details finden Sie im UserVoice-Beitrag: [SSMS Import Flat File fails to import all data](https://feedback.azure.com/forums/908035/suggestions/38096989) (SSMS-Befehl „Flatfile importieren“ importiert nicht alle Daten). |
| Integration Services | Neuer Vorgangstyp *StartNonCatalogExecution* für den SSIS-Vorgangsbericht wurde hinzugefügt.|
| SMO/Skripterstellung | Es wurde ein Problem behoben, das bewirkte, dass SMO beim Abrufen von Eigenschaften Fehler auslöste, wenn **SMO.Server.SetDefaultInitFields(true)** verwendet wurde.|
| Benutzeroberfläche des Abfragespeichers | Es wurde ein Problem behoben, bei dem die Y-Achse nicht skalierte, wenn in der Ansicht *Nachverfolgte Abfrage* die *Ausführungsanzahl* ausgewählt war. |
| Sicherheitsrisikobewertung | Das Löschen und Genehmigen der Basislinie für Azure SQL DBs wurde deaktiviert.|

### <a name="known-issues-183"></a>Bekannte Probleme (18.3)

- Das Datenbankdiagramm, das von einem auf Computer A ausgeführten SSMS erstellt wurde, kann nicht auf Computer B geändert werden (SSMS stürzt ab). Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37992649).

- Es gibt Neuzeichnungsprobleme beim Wechseln zwischen mehreren Abfragefenstern. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37474042). Um dieses Problem zu umgehen, können Sie die Hardwarebeschleunigung unter „Extras“ > „Optionen“ deaktivieren.

Sie können für andere bekannte Probleme auf [UserVoice](https://feedback.azure.com/forums/908035-sql-server) verweisen, und um dem Produktteam Feedback zu geben.

## <a name="previous-ssms-releases"></a>Vorgängerversionen von SSMS

Laden Sie die Vorgängerversionen von SSMS herunter, indem Sie die Titellinks in den folgenden Abschnitten anklicken:

## <a name="downloadssdtmediadownloadpng-ssms-182httpsgomicrosoftcomfwlinklinkid2099720"></a>[SSMS 18.2](https://go.microsoft.com/fwlink/?linkid=2099720) ![herunterladen](../ssdt/media/download.png)

Releasenummer: 18.2  
Buildnummer: 15.0.18142.0  
Releasedatum: 25. Juli 2019

18.2 ist ein Update von 18.1 mit den folgenden neuen Elementen und Fehlerbehebungen.

## <a name="whats-new-in-182"></a>Neues in Version 18.2

|  Neues Element  |  Details  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Integration Services (SSIS) | Leistungsoptimierung für SSIS-Paketplaner in Azure. |
| IntelliSense/Editor | Unterstützung für die Datenklassifizierung wurde hinzugefügt. |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | IntelliSense-Unterstützung wurde hinzugefügt. |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | Diese Option aktiviert eine Optimierung in der Datenbank-Engine, die den Durchsatz für Einfügevorgänge mit hoher Parallelität in den Index verbessert. Diese Option ist für Indizes vorgesehen, die anfällig für Konflikte durch Einfügevorgänge auf der letzten Seite sind. Dieser Fall tritt häufig bei Indizes mit fortlaufendem Schlüssel auf. Dazu zählen beispielsweise Identitätsspalten, Sequenzspalten oder Spalten für Datum und Uhrzeit. Weitere Informationen finden Sie unter [CREATE INDEX](../t-sql/statements/create-index-transact-sql.md#sequential-keys). |
| Abfrageausführung oder Ergebnisse | In den Meldungen wurde eine *Abschlusszeit* hinzugefügt, um nachzuverfolgen, wann die Ausführung einer bestimmten Abfrage abgeschlossen wurde. |
| Abfrageausführung oder Ergebnisse | Ermöglicht, mehr Daten anzuzeigen (Ergebnis in Text) und in Zellen zu speichern (Ergebnis in Raster). SSMS erlaubt nun bis zu 2 Mio. Zeichen für beides (Steigerung von 256 bzw. 64 Tausend). Damit ist auch das Problem gelöst, dass Benutzer nicht in der Lage waren, mehr als 43.680 Zeichen aus den Zellen des Rasters abzurufen. |
| Showplan | In QueryPlan wurde ein neues Attribut hinzugefügt für den Fall, dass das [Inlining benutzerdefinierter Skalarfunktionen](../relational-databases/performance/intelligent-query-processing.md#scalar-udf-inlining) aktiviert ist (ContainsInlineScalarTsqludfs). |
| SMO | Unterstützung für die *SQL-Bewertungs-API* wurde hinzugefügt. Weitere Informationen finden Sie unter [SQL-Bewertungs-API](https://docs.microsoft.com/sql/sql-assessment-api/sql-assessment-api-overview). |
|  |  |

## <a name="bug-fixes-in-182"></a>Fehlerkorrekturen in Version 18.2

|  Neues Element  |  Details  |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Barrierefreiheit | Die XEvent-Benutzeroberfläche (das Raster) wurde aktualisiert, sodass sie mit F3 sortiert werden kann. |
| Always On | Es wurde das Problem behoben, dass SSMS beim Versuch, eine Verfügbarkeitsgruppe (AG) zu löschen, einen Fehler ausgelöst hat. |
| Always On | Es wurde das Problem behoben, das SSMS den falschen Failover-Assistenten anzeigte, wenn Replikate bei Verwendung von Verfügbarkeitsgruppen mit Leseskalierung (Clustertyp=None) als synchron konfiguriert waren. Nun zeigt SSMS den Assistenten für die Force_Failover_Allow_Data_Loss-Option an, der einzige, der für den Clustertyp mit der Verfügbarkeit „NONE“ zulässig ist. |
| Always On | Es wurde das Problem behoben, dass der Assistent die Anzahl zulässiger Synchronisierungen auf drei beschränkte. |
| Datenklassifizierung | Es wurde das Problem behoben, dass SSMS den Fehler *Index (basierend auf 0) muss größer als oder gleich null (0) sein* meldete, wenn versucht wurde, Datenklassifizierungsberichte zu Datenbanken mit einem kleineren CompatLevel als 150 anzuzeigen. |
| SSMS allgemein | Es wurde das Problem behoben, dass der Benutzer im Ergebnisbereich nicht horizontal mit dem Mausrad scrollen konnte. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/34145641). |
| SSMS allgemein | *Aktivitätsmonitor* wurde aktualisiert, um unschädliche Wartetypen SQLTRACE_WAIT_ENTRIES zu ignorieren. |
| SSMS allgemein | Das Problem wurde behoben, dass einige Farboptionen *(Text-Editor > Registerkarte „Editor“ und Statusleiste)* nicht persistent gespeichert wurden. Siehe [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37924165).
| SSMS allgemein | Im Verbindungsdialogfeld wurde *Azure Active Directory: universell mit MFA-Unterstützung* durch *Azure Active Directory: universell mit MFA* ersetzt (die Funktionalität ist identisch, aber dies ist hoffentlich nicht verwirrend). |
| SSMS allgemein | SSMS wurde aktualisiert, um beim Erstellen einer Azure SQL-Datenbank-Instanz richtige Standardwerte zu verwenden. |
| SSMS allgemein | Es wurde das Problem behoben, dass der Benutzer von einem Knoten in [Registrierte Server](register-servers/register-servers.md) nicht *PowerShell starten* konnte, wenn der Server ein [SQL Linux-Container](../linux/quickstart-install-connect-docker.md) war. |
| Importieren einer Flatfile | Es wurde das Problem behoben, dass *Flatfile importieren* nach dem Upgrade von SSMS 18.0 auf 18.1 nicht funktioniert hat. Siehe [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37912636). |
| Importieren einer Flatfile | Es wurde das Problem behoben, das der *Assistent zum Importieren von Flatfiles eine doppelte oder ungültige Spalte* in einer CSV-Datei mit Headern mit Unicode-Zeichen meldete. |
| Objekt-Explorer | Es wurde das Problem behoben, dass einige Menüelemente (z.B. SQL Server-*Import/Export-Assistent*) fehlten oder deaktiviert waren, wenn eine Verbindung mit SQL Express bestand. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37500016). |
| Objekt-Explorer | Es wurde ein Problem behoben, das zu einem Absturz von SSMS geführt hat, wenn ein Objekt aus dem Objekt-Explorer in den Editor gezogen wurde. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37887988). |
| Objekt-Explorer | Es wurde das Problem behoben, dass beim Umbenennen von Datenbanken im Objekt-Explorer falsche Datenbanknamen angezeigt wurden. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37638472). |
| Objekt-Explorer | Das seit langem bestehende Problem wurde behoben, dass bei dem Versuch, den Knoten *Tabellen* im Objekt-Explorer für eine Datenbank zu erweitern, die so eingestellt ist, dass sie eine Sortierung verwendet, die nicht mehr von Windows unterstützt wird, einen Fehler auslöst (und Benutzer ihre Tabellen nicht erweitern können). Ein Beispiel für eine solche Sortierung wäre Korean_Wansung_Unicode_CI_AS. |
| [Registrieren von Servern](register-servers/register-servers.md) | Es wurde das Problem behoben, dass der Versuch, eine Abfrage auf mehreren Servern (unter einer *Gruppe* in „Registrierte Server“) durchzuführen, wenn der „Registrierte Server“ entweder *Active Directory: integriert* oder *Active Directory: universell mit MFA* verwendete, nicht funktionierte, weil SSMS keine Verbindung herstellen konnte. |
| [Registrieren von Servern](register-servers/register-servers.md) | Es wurde das Problem behoben, dass der Versuch, eine Abfrage auf mehreren Servern (unter einer *Gruppe* in „Registrierte Server“) durchzuführen, wenn der „Registrierte Server“ entweder *Active Directory: Kennwort* oder *SQL Auth* verwendete, und der Benutzer wählte, dass das Kennwort nicht gemerkt werden sollte, zum Absturz von SSMS führte. |
| Berichte | Es wurde ein Problem bei den *Datenträgerverwendung*-Berichten behoben, wobei bei dem Bericht ein Fehler auftrat, wenn Datendateien eine große Anzahl von Erweiterungen aufwiesen. |
| Replikationstools | Es wurde ein Problem behoben, bei dem der Replikationsmonitor nicht mit der Herausgeber-DB in der Verfügbarkeitsgruppe und dem Verteiler in der Verfügbarkeitsgruppe funktionierte (wurde zuvor in SSMS 17.x behoben). |
| SQL-Agent | Es wurde ein Problem behoben, dass beim Hinzufügen, Einfügen, Bearbeiten oder Entfernen von Auftragsschritten dazu führte, dass der Fokus auf die erste Zeile anstelle der aktiven Zeile zurückgesetzt wurde. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/38070892). |
| SMO/Skripterstellung | Es wurde ein Problem behoben, dass *CREATE OR ALTER* keine Skripts für Objekte mit erweiterten Eigenschaften erstellte. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035-sql-server/suggestions/37236748). |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem SSMS kein korrektes Skript für CREATE EXTERNAL LIBRARY erstellen konnte. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37868089). |
| SMO/Skripterstellung | Ein Problem wurde behoben, bei dem der Versuch, für eine Datenbank mit einigen Tausend Tabellen *Skripts zu generieren*, dazu führte, dass das Statusdialogfeld hängenzubleiben schien. |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem die Skripterstellung einer *externen Tabelle* in SQL 2019 nicht funktionierte. |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem die Skripterstellung einer *externen Datenquelle* in SQL 2019 nicht funktionierte. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/34295080). |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem für *erweiterte Eigenschaften* in Spalten für Azure SQL-Datenbank kein Skript erstellt wurde. Weitere Informationen finden Sie unter [StackOverflow](https://stackoverflow.com/questions/56952337/how-can-i-script-the-descriptions-of-columns-in-ms-sql-server-management-studio). |
| SMO/Skripterstellung | Letzte Seite einfügen: SMO: Eigenschaft *Index.IsOptimizedForSequentialKey* |
|**SSMS-Setup**| **Es wurde ein Problem behoben, bei dem das SSMS-Setup fälschlicherweise die Installation von SSMS mit Meldung nicht übereinstimmender Sprachen blockiert hat. Dies hätte in einigen anormalen Situationen wie z.B. einem abgebrochenen Setup oder einer fehlerhaften Deinstallation einer früheren Version von SSMS ein Problem sein können. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37483594/)** . |
| XEvent-Profiler | Der Viewer stürzt beim Schließen nicht mehr ab. |

### <a name="known-issues-182"></a>Bekannte Probleme (18.2)

- Das Datenbankdiagramm, das von einem auf Computer A ausgeführten SSMS erstellt wurde, kann nicht auf Computer B geändert werden (SSMS würde abstürzen). Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37992649).

- Es gibt Neuzeichnungsprobleme beim Wechseln zwischen mehreren Abfragefenstern. Siehe [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37474042). Um dieses Problem zu umgehen, können Sie die Hardwarebeschleunigung unter **Extras** > **Optionen** deaktivieren.

- Es gibt eine Einschränkung hinsichtlich der Größe der Daten, die aus den SSMS-Ergebnissen im Raster, im Text oder in einer Datei angezeigt werden.

- Beim Löschen einer Azure SQL-Datenbank im Objekt-Explorer wird ein Fehler ausgegeben, obwohl der Vorgang erfolgreich war.

- Im Dialogfeld „Anmeldungseigenschaften“ wird die Standardsprache für SQL-Anmeldungen möglicherweise als „Arabisch“ angezeigt – unabhängig von der tatsächlich für die Anmeldung festgelegten Standardsprache. Verwenden Sie zum Anzeigen der tatsächlichen Standardsprache für eine bestimmte Anmeldung T-SQL, um **default_language_name** aus **master.sys.server_principles** für die Anmeldung auszuwählen.

## <a name="downloadssdtmediadownloadpng-ssms-181httpsgomicrosoftcomfwlinklinkid2094583"></a>![ ](../ssdt/media/download.png) [SSMS 18.1 herunterladen](https://go.microsoft.com/fwlink/?linkid=2094583)

- Releasenummer: 18.1  
- Buildnummer: 15.0.18131.0  
- Releasedatum: 11. Juni 2019  

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40a)

Im Vergleich zu Version 18.0 ist Version 18.1 ein kleines Update mit den folgenden neuen Elementen und Fehlerbehebungen:

## <a name="whats-new-in-181"></a>Neues in Version 18.1

| Neues Element| Details|
| :-------| :------|
| Datenbankdiagramme | [In SSMS wurden wieder Datenbankdiagramme hinzugefügt.](https://feedback.azure.com/forums/908035/suggestions/37507828)
| SSBDIAGNOSE.EXE |Dem SSMS-Paket wurde wieder die SQL Server-Diagnose (Befehlszeilentool) hinzugefügt.|
| Integration Services (SSIS) | Unterstützung für die Zeitplanung des SSIS-Pakets in Azure, das sich entweder im SSIS-Katalog in Azure oder im Dateisystem befindet. Es gibt drei Einträge für das Starten des Dialogfelds „Neuer Zeitplan“: Das Menüelement *Neuer Zeitplan...* wird angezeigt, wenn Sie mit der rechten Maustaste auf das SSIS-Paket im SSIS-Katalog in Azure klicken. Die zweite Option erreichen Sie über das Menüelement *Schedule SSIS Package in Azure* (Zeitplan für das SSIS-Paket in Azure) unter dem Menüelement *Migrate to Azure* (Migrieren zu Azure) unter *Tools* (Extras). Die dritte Option „Schedule SSIS“ (SSIS-Zeitplan in Azure) wird angezeigt, wenn Sie mit der rechten Maustaste auf den Auftragsordner unter dem SQL Server-Agent der verwalteten Azure SQL-Datenbank-Instanz klicken.|

## <a name="bug-fixes-in-181"></a>Fehlerkorrekturen in Version 18.1

| Neues Element | Details |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Barrierefreiheit | Verbesserte Barrierefreiheit der Benutzeroberfläche des Agent-Auftrags. |
| Barrierefreiheit | Verbesserte Barrierefreiheit auf der Seite „Stretch Datenbank-Monitor“ durch Hinzufügen eines barrierefreien Namens für die Schaltfläche *Automatisch aktualisieren* und eines Namens zur Verwendung von Screenreader-Software, der Benutzer darüber informiert, um welche Schaltfläche es sich handelt und welche Auswirkungen es hat, wenn diese gedrückt wird. |
| ADS-Integration| Es wurde ein Problem behoben, bei dem es bei der Verwendung von ADS-registrierten Servern zu Abstürzen kam.|
| Datenbank-Designer | Unterstützung für die „Latin1_General_100_BIN2_UTF8“-Sortierung (verfügbar in SQL Server 2019 CTP 3.0). |
| Datenklassifizierung | Es wird verhindert, dass Spalten in der Verlaufstabelle Vertraulichkeitsbezeichnungen hinzugefügt werden, was nicht unterstützt wird. |
| Datenklassifizierung | Es wurde ein Problem behoben, bei dem der Kompatibilitätsgrad falsch behandelt wurde (Server im Vergleich zur Datenbank). |
| Datenbank-Designer | Unterstützung für die „Latin1_General_100_BIN2_UTF8“-Sortierung (verfügbar in SQL 2019 CTP 3.0). |
| SSMS allgemein | Es wurde ein Problem behoben, bei dem die Skripterstellung von Pseudospalten in einem Index fehlerhaft war. |
| SSMS allgemein | Es wurde ein Problem auf der Seite „Anmeldungseigenschaften“ behoben, bei dem das Klicken auf die Schaltfläche *Anmeldeinformationen hinzufügen* eine Nullverweisausnahme zur Folge hatte. |
| SSMS allgemein | Es wurde ein Problem hinsichtlich der Größenanzeige der Spalte „money“ auf der Seite „Indexeigenschaften“ behoben. |
| SSMS allgemein | Es wurde ein Problem behoben, bei dem SSMS die IntelliSense-Einstellung von *Tools/Extras* im SQL-Editor-Fenster nicht berücksichtigt hat. |
| SSMS allgemein | Es wurde ein Problem behoben, bei dem SSMS die Hilfeeinstellungen nicht berücksichtigt hat (online im Vergleich zu offline). |
| Hohe DPI-Werte | Das Layout von Steuerelementen in Fehlerdialogen für nicht unterstützte Abfrageoptionen wurde korrigiert. |
| Hohe DPI-Werte | Das Layout von Steuerelementen auf der Seite *Neue Verfügbarkeitsgruppe* wurde korrigiert, die in einigen lokalisierten Versionen von SSMS enthalten ist. |
| Hohe DPI-Werte | Das Layout der Seite *Neuer Auftragszeitplan* wurde korrigiert. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37632094). |
| Importieren von Flatfiles | Es wurde ein Problem behoben, bei dem Zeilen beim Import unbemerkt verloren gingen.|
| IntelliSense/Editor | Der SMO-basierte Datenverkehr von Abfragen zu Azure SQL-Datenbanken für IntelliSense wurde reduziert. |
| IntelliSense/Editor | Es wurden grammatikalische Fehler in der QuickInfo behoben, die beim Eingeben von T-SQL zum Erstellen eines Benutzers angezeigt wurden. Außerdem wurde die Fehlermeldung zum Unterscheiden zwischen Benutzern und Anmeldungen behoben. |
| Protokollanzeige | Es wurde ein Problem behoben, bei dem SSMS selbst nach einem Doppelklick auf ein älteres Archivzeichen im Objekt-Explorer immer das aktuelle Server- oder Agent-Protokoll öffnete. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37633648). |
| SSMS-Setup | Es wurde ein Problem behoben, bei dem das SSMS-Setup fehlschlug, wenn im Setup des Protokollpfads Leerzeichen enthalten waren. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37496110). |
| SSMS-Setup | Ein Problem wurde behoben, bei dem SSMS nach Anzeigen des Begrüßungsbildschirms sofort beendet wurde. </br> Weitere Informationen finden Sie auf diesen Websites: [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37502512), [SSMS Refuses to Start](https://dba.stackexchange.com/questions/238609/ssms-refuses-to-start) (SSMS startet nicht) und [Database Administrators](https://dba.stackexchange.com/questions/237086/sql-server-management-studio-18-wont-open-only-splash-screen-pops-up) (Datenbankadministratoren). |
| Objekt-Explorer | Es wurden Einschränkungen bei der Aktivierung von *PowerShell starten* beseitigt, die bei einer Verbindung mit SQL unter Linux auftraten. |
| Objekt-Explorer | Es wurde ein Problem behoben, bei dem SSMS beim Erweitern des Knotens „PolyBase/Erweiterungsgruppe“ abstürzte (bei einer Verbindung mit einem Computeknoten). |
| Objekt-Explorer | Es wurde ein Problem behoben, bei dem das Menüelement *Deaktiviert* auch nach dem Deaktivieren eines bestimmten Indexes weiterhin aktiviert war. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37735375). |
| Berichte | Korrigieren des Berichts, um „GrantedQueryMemory“ in KB anzuzeigen (Bericht „SQL Performance Dashboard“). Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37167289). |
| Berichte | Verbesserte Ablaufverfolgung des Protokollblocks in Always On-Szenarios. |
| Showplan | Das neue Showplanelement *SpillOccurred* wurde zum Showplanschema hinzugefügt. |
| Showplan | Es wurden Remotelesevorgänge (*ActualPageServerReads*, *ActualPageServerReadAheads*, *ActualLobPageServerReads* und *ActualLobPageServerReadAheads*) zum Showplanschema hinzugefügt. |
| SMO/Skripterstellung | Das Abfragen von Edgeeinschränkungen während der Skripterstellung wird für nicht graphische Tabellen vermieden. |
| SMO/Skripterstellung | Einschränkungen hinsichtlich der Vertraulichkeitsklassifizierung bei der Skripterstellung von Spalten mit der *Datenklassifizierung* wurden aufgehoben. |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem „Skript generieren“ in einer Graphtabelle fehlschlägt, wenn Daten generiert werden. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898466). |
| SMO/Skripterstellung | Es wurde ein Problem behoben, bei dem die „EnumObjects()“-Methode keine Schemanamen für ein Synonym abgerufen haben. |
| SMO/Skripterstellung | Es wurde ein Problem in „UIConnectionInfo.LoadFromStream()“ behoben, bei dem der Abschnitt *AdvancedOptions* nicht gelesen werden konnte (wenn kein Kennwort angegeben wurde). |
| SQL-Agent | Es wurde ein Problem behoben, bei dem SSMS bei der Arbeit mit dem Fenster „Auftragseigenschaften“ fehlschlug. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37164244). |
| SQL-Agent | Es wurde ein Problem behoben, bei dem die Schaltfläche „Anzeigen“ in den *Auftragsschritt-Eigenschaften* nicht immer aktiviert war und somit das Anzeigen der Ausgabe eines bestimmten Auftragsschritts verhindert wurde. |
| XEvent-Benutzeroberfläche | Die Spalte „Paket“ wurde zu XEvents-Listen hinzugefügt, um Ereignisse mit identischem Namen zu unterscheiden. |
| XEvent-Benutzeroberfläche | Der fehlende Klassentyp „EXTERNAL LIBRARY“ wurde hinzugefügt, der „XEventUI“ zugeordnet ist. |

### <a name="known-issues-181"></a>Bekannte Probleme (18.1)

- Benutzern kann ein Fehler angezeigt werden, wenn ein Tabellenobjekt aus dem Objekt-Explorer in den Abfrage-Editor gezogen wird. Dieser Fehler ist bekannt, und der Fix ist für das nächste Release geplant.

- Die Farboptionen für *Verbindungen gruppieren* und *Einzelne Serververbindungen* unter „Optionen > Text-Editor > Registerkarte „Editor“ und Statusleiste > Layout und Farben der Statusleiste“ werden nach Schließen von SSMS 18.1 nicht beibehalten. Sobald Sie SSMS erneut öffnen, wird die Option „Layout und Farben der Statusleiste“ auf die Standardeinstellung zurückgesetzt.

- Es gibt eine Einschränkung hinsichtlich der Größe der Daten, die aus den SSMS-Ergebnissen im Raster, im Text oder in einer Datei angezeigt werden.

- Das Datenbankdiagramm, das von einem auf Computer A ausgeführten SSMS erstellt wurde, kann nicht auf Computer B geändert werden (SSMS stürzt ab). Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37992649).

## <a name="downloadssdtmediadownloadpng-ssms-180httpsgomicrosoftcomfwlinklinkid2088649"></a>![Download](../ssdt/media/download.png) [SSMS 18.0](https://go.microsoft.com/fwlink/?linkid=2088649)

- Releasenummer: 18.0  
- Buildnummer: 15.0.18118.0  
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
|SSMS kann jetzt in einem benutzerdefinierten Ordner installiert werden| Diese Option ist über die Befehlszeile (nützlich bei einer unbeaufsichtigten Installation) und die Setup-Benutzeroberfläche verfügbar. Übergeben Sie über die Befehlszeile dieses zusätzliche Argument an die Datei „SSMS-Setup-ENU.exe“:   SSMSInstallRoot=C:\MySSMS18  Der neue Standardspeicherort für die Installation von SSMS lautet: „%ProgramFiles(x86)%\Microsoft SQL Server Management Studio 18\Common7\IDE\ssms.exe“.  Das bedeutet nicht, dass SSMS mehrere Instanzen besitzt.|
|SSMS kann in einer anderen Sprache als der Betriebssystemsprache installiert werden|Das Einrichten gemischter Sprachen wird nicht mehr blockiert. Sie können z. B. die deutsche Version von SSMS unter der französischen Windows-Version installieren. Stimmt die Sprache des Betriebssystems nicht mit der Sprache von SSMS überein, muss der Benutzer die Sprache folgendermaßen ändern: **Extras** > **Optionen** > **Internationale Einstellungen**. Andernfalls wird in SSMS die englische Benutzeroberfläche angezeigt.|
|SSMS verwendet keine gemeinsamen Komponenten mehr mit SQL Engine|Ein Schwerpunkt lag in der Vermeidung von gemeinsamen Komponenten mit SQL Engine, da dies häufig zu Wartungsproblemen (durch unbeabsichtigtes gegenseitiges Überschreiben der installierten Dateien) führte.|
|SSMS erfordert NetFx 4.7.2 oder höher.|Wir haben die Mindestanforderung von NetFx 4.6.1 auf NetFx 4.7.2 erhöht, damit die neuen Funktionen genutzt werden können, die vom neuen Framework bereitgestellt werden.|
|Möglichkeit zum Migrieren von SSMS-Einstellungen| Beim ersten Starten von SSMS 18 wird der Benutzer dazu aufgefordert, die Einstellungen aus 17.x zu migrieren. Die Dateien für Benutzereinstellungen werden jetzt als XML-Textdatei gespeichert, wodurch die Portabilität verbessert und eine Bearbeitung ermöglicht werden.|
|Unterstützung für hohe DPI-Werte| Hohe DPI-Werte sind nun standardmäßig aktiviert.|
|SSMS wird mit dem Microsoft OLE DB-Treiber geliefert| Informationen hierzu finden Sie unter [Herunterladen des Microsoft OLE DB-Treibers für SQL Server](https://docs.microsoft.com/sql/connect/oledb/download-oledb-driver-for-sql-server).|
|SSMS wird unter Windows 8 nicht unterstützt. Windows 10 und Windows Server 2016 erfordern Version 1607 (10.0.14393) oder höher|Aufgrund der neuen Abhängigkeit von NetFx 4.7.2 wird SSMS 18.0 nicht unter Windows 8 und älteren Versionen von Windows 10 und Windows Server 2016 installiert. Diese Systeme werden vom SSMS-Setup blockiert. Windows 8.1 wird weiterhin unterstützt.|
|SSMS wird nicht mehr der PATH-Umgebungsvariable hinzugefügt|Der Pfad zu SSMS.EXE (und Tools im Allgemeinen) wird nicht mehr zum Pfad hinzugefügt. Benutzer können diesen entweder manuell hinzufügen oder bei einem modernen Windows-Computer das Startmenü verwenden.|
|Paket-IDs sind zum Entwickeln von SSMS-Erweiterungen nicht mehr erforderlich| In der Vergangenheit wurden in SSMS nur bekannte Pakete selektiv geladen, sodass Entwickler ihr eigenes Paket registrieren mussten. Das ist nicht mehr der Fall.|
|SSMS allgemein|Die Konfigurationsoption „AUTOGROW_ALL_FILES“ wurde für Dateigruppen in SSMS bereitgestellt.|
|SSMS allgemein|Die riskanten Optionen „Lightweightpooling“ und „Prioritätserhöhung“ wurden von der grafischen SSMS-Benutzeroberfläche entfernt. Weitere Informationen finden Sie unter [Priority boost details – and why it’s not recommended (Informationen zur Prioritätserhöhung und Gründe, die dagegen sprechen)](https://blogs.msdn.microsoft.com/arvindsh/2010/01/26/priority-boost-details-and-why-its-not-recommended/).
|SSMS allgemein|Neues Menü und Tastenkombinationen zum Erstellen von Dateien: **STRG+ALT+N**. Mit **STRG+N** wird weiterhin eine neue Abfrage erstellt.|
|SSMS allgemein|Das Dialogfeld **Neue Firewallregel** ermöglicht dem Benutzer nun das Angeben eines Regelnamens anstelle der automatischen Generierung.|
|SSMS allgemein|IntelliSense im Editor wurde insbesondere für Version v140 und höher von T-SQL verbessert.|
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
|Unterstützung für Azure SQL| Unterstützung für V-Kern-SKUs (universell und unternehmenskritisch) wurde hinzugefügt: Gen4_24 und alle Gen5.|
|Verwaltete Azure SQL-Datenbank-Instanz|„Anmeldungen mit AAD“ wurde als neue Anmeldemethode in SMO und SSMS hinzugefügt, wenn eine Verbindung zu einer verwalteten Azure SQL-Instanz besteht.|
|Always On|RTO (geschätzte Wiederherstellungszeit) und RPO (geschätzter Datenverlust) wurden im Always on-Dashboard von SSMS mit einem neuen Hashwert versehen. Die aktualisierte Dokumentation finden Sie unter [https://docs.microsoft.com/sql/database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups](../database-engine/availability-groups/windows/monitor-performance-for-always-on-availability-groups.md).|
|Always Encrypted| Im Dialogfeld „Mit Server verbinden“ bietet das Kontrollkästchen „Always Encrypted aktivieren“ in der Registerkarte „Always Encrypted“ jetzt eine einfache Möglichkeit zum Aktivieren/Deaktivieren von Always Encrypted für eine Datenbankverbindung.|
|Always Encrypted mit Secure Enclaves| Die folgenden Verbesserungen zur Unterstützung von Always Encrypted mit Secure Enclaves wurden in der Vorschauversion von SQL Server 2019 vorgenommen:  Ein Textfeld zum Angeben der Enclave-Nachweis-URL im Dialogfeld „Mit Server verbinden“ (die neue Registerkarte „Always Encrypted“).  Das neue Kontrollkästchen im Dialogfeld „Neuer Spaltenhauptschlüssel“, um zu steuern, ob ein neuer Spaltenhauptschlüssel Enclave-Berechnungen zulässt.  Weitere Dialogfelder für die Always Encrypted-Schlüsselverwaltung stellen nun Informationen dazu bereit, welche Spaltenhauptschlüssel Enclave-Berechnungen zulassen.|
|Überwachungsdateien|Die Authentifizierungsmethode wurde von der Authentifizierung auf Basis des Speicherkontoschlüssel in die Azure AD-basierte Authentifizierung geändert.|
|Datenklassifizierung| Das Aufgabenmenü für die Datenklassifizierung wurde neu organisiert: Dem Datenbankaufgabenmenü wurde ein Untermenü hinzugefügt sowie eine Option zum Öffnen des Berichts aus dem Menü, ohne zuerst das Fenster „Daten klassifizieren“ öffnen zu müssen.|
|Datenklassifizierung|In SMO wurde die neue Funktion „Datenklassifizierung“ hinzugefügt. Spaltenobjekt macht neue Eigenschaften verfügbar: SensitivityLabelName, SensitivityLabelId, SensitivityInformationTypeName, SensitivityInformationTypeId und IsClassified (schreibgeschützt). Weitere Informationen finden Sie unter [ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/add-sensitivity-classification-transact-sql).|
|Datenklassifizierung|Das neue Menüelement „Klassifizierungsbericht“ wurde dem Flyout „Datenklassifizierung“ hinzugefügt.|
|Datenklassifizierung| Empfehlungen wurden aktualisiert.|
|Upgrade des Datenbank-Kompatibilitätsgrads|Eine neue Option wurde unter ***Datenbankname*** > ***Tasks*** > ***Datenbankupgrade*** hinzugefügt. Mit ihr wird der neue **Abfrageoptimierungs-Assistent** gestartet, der den Benutzer durch folgende Prozesse führt: Sammeln einer Leistungsbaseline, bevor ein Upgrade des Datenbank-Kompatibilitätsgrads durchgeführt wird Durchführen eines Upgrades auf den gewünschten Datenbank-Kompatibilitätsgrad  Sammeln eines zweiten Durchlaufs von Leistungsdaten der gesamten Arbeitsauslastung Ermitteln von Regressionen der Arbeitsauslastung und Bereitstellen getesteter Empfehlungen zur Verbesserung der Arbeitsauslastungsleistung  Dies ähnelt dem unter [Verwendungsszenarios für den Abfragespeicher](https://docs.microsoft.com/sql/relational-databases/performance/query-store-usage-scenarios#CEUpgrade) beschriebenen Datenbankupgrade mit Ausnahme des letzten Schritts, bei dem der Abfrageoptimierungs-Assistent sich nicht auf den letzten als funktionierend bekannten Zustand beruft, um Empfehlungen zu generieren.|
|Datenschichtanwendungs-Assistent|Unterstützung für das Importieren/Exportieren von Datenschichtanwendungen mit Graphtabellen wurde hinzugefügt.|
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
|Showplan|Tatsächlich verstrichene Zeit und tatsächliche Zeilen gegenüber geschätzten Zeilen wurden bei Verfügbarkeit unter dem Knoten „Showplanoperator“ hinzugefügt. So wird gewährleistet, dass der tatsächliche Plan dem Plan der Liveabfragestatistik entspricht.|
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
|SSMS allgemein|Ein Problem beim Anzeigen der Eigenschaften einer Datenbank (mit FILEGROWTH > 2048 GB), das zu einem Fehler mit arithmetischem Überlauf geführt hat, wurde behoben.|
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
|Sichern/Wiederherstellen/Anfügen/Trennen einer Datenbank|Ein Fehler wurde behoben, bei dem der Assistent zum Anfügen von Datenbanken sekundäre Dateien, die umbenannt wurden, nicht angezeigt hat. Jetzt wird die Datei, einschließlich eines Kommentars, angezeigt (z.B. „nicht gefunden“). Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/32897434](https://feedback.azure.com/forums/908035/suggestions/32897434). |
|Assistent zum Kopieren von Datenbanken|Der Versuch des Assistenten zum Generieren von Skripts/Übertragen/Kopieren von Datenbanken, eine Tabelle mit einer In-Memory-Tabelle zu erstellen, erzwingt nicht die Einstellung ON für ANSI_PADDINGTON.|
|Assistent zum Kopieren von Datenbanken|Übertragung von Datenbankaufgabe/Assistent zum Kopieren von Datenbanken unterbrochen auf SQL Server 2017 und SQL Server 2019.|
|Assistent zum Kopieren von Datenbanken|Der Assistent zum Generieren von Skripts/Übertragen/Kopieren von Datenbanken erstellt ein Skript für die Tabellenerstellung vor der Erstellung von zugeordneten externen Datenquellen.|
|Verbindungsdialogfeld|Das Entfernen von Benutzernamen aus der vorherigen Benutzernamenliste durch Drücken der ENTF-Taste wurde aktiviert. Weitere Informationen finden Sie unter [Allow deletion of users from SSMS login window (Löschen von Benutzern aus dem SSMS-Anmeldefenster zulassen)](https://feedback.azure.com/forums/908035/suggestions/32897632).|
|DAC-Import-Assistent|Ein Fehler wurde behoben, bei dem der DAC-Import-Assistent bei einer Verbindung über AAD nicht funktioniert hat.|
|Datenklassifizierung|Ein Problem wurde behoben, das beim Speichern von Klassifizierungen im Datenklassifizierungbereich aufgetreten ist, während gleichzeitig andere Datenklassifizierungsbereiche in anderen Datenbanken geöffnet waren.|
|Datenschichtanwendungs-Assistent|Ein Fehler wurde behoben, durch den Benutzer aufgrund des eingeschränkten Zugriffs auf den Server (beispielsweise fehlender Zugriff auf alle Datenbanken auf einem Server) keine Datenschichtanwendung (.dacpac) importieren konnten.|
|Datenschichtanwendungs-Assistent|Ein Fehler wurde behoben, durch den der Importvorgang sehr langsam war, wenn viele Datenbanken in der gleichen Azure SQL Server-Instanz gehostet wurden.|
|Externe Tabellen|Unterstützung für „Rejected_Row_Location“ in der Vorlage, in SMO, IntelliSense, und im Eigenschaftenraster wurde hinzugefügt.|
|Assistent zum Importieren von Flatfiles|Ein Problem wurde behoben, bei dem der Assistent zum Importieren von Flatfiles doppelte Anführungszeichen nicht ordnungsgemäß verarbeitete (mit Escapezeichen versah). Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035/suggestions/32897998](https://feedback.azure.com/forums/908035/suggestions/32897998). |
|Assistent zum Importieren von Flatfiles|Ein Problem in Bezug auf die fehlerhafte Handhabung von Gleitkommatypen (bei Gebietsschemas, die ein anderes Trennzeichen für Gleitkommawerte verwenden) wurde behoben.|
|Assistent zum Importieren von Flatfiles|Ein Problem im Zusammenhang mit dem Importieren von Bits, wenn Werte 0 oder 1 sind, wurde behoben. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535](https://feedback.azure.com/forums/908035-sql-server/suggestions/32898535). |
|Assistent zum Importieren von Flatfiles|Ein Problem wurde behoben, bei dem *float*-Elemente als *NULL*-Werte eingegeben wurden.|
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
|Objekt-Explorer|Ein Fehler wurde behoben, bei dem ein Rechtsklick auf Knoten im Objekt-Manager (z.B. „Tabellen“) und das Ausführen einer Aktion wie dem Filtern von Tabellen über „Filter > Filtereinstellungen“ das Formular für Filtereinstellungen auf einem anderen Bildschirm angezeigt werden kann, als dem, auf dem SSMS derzeit aktiv ist. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106](https://feedback.azure.com/forums/908035-sql-server/suggestions/34284106). |
|Objekt-Explorer|Ein lange bestehendes Problem wurde behoben, bei dem die ENTF-TASTE im Objekt-Explorer beim Umbenennen eines Objekts nicht funktionierte. Weitere Informationen finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510](https://feedback.azure.com/forums/908035-sql-server/suggestions/33073510), [https://feedback.azure.com/forums/908035/suggestions/32910247](https://feedback.azure.com/forums/908035/suggestions/32910247) und bei anderen Duplikaten.|
|Objekt-Explorer|Beim Anzeigen der Eigenschaften vorhandener Datenbankdateien wird die Größe in einer Spalte „Größe (MB)“ anstelle von „Anfangsgröße (MB)“ angezeigt, was der Anzeige beim Erstellen einer neuen Datenbank entspricht. Einzelheiten dazu finden Sie unter [https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024](https://feedback.azure.com/forums/908035-sql-server/suggestions/32629024). |
|Objekt-Explorer|Der Kontextmenüeintrag „Entwurf“ für „Graph-Tabellen“ wurde deaktiviert, da in der aktuellen Version von SSMS keine Unterstützung für diese Tabellen besteht.|
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

- Es gibt eine Einschränkung hinsichtlich der Größe der Daten, die aus den SSMS-Ergebnissen im Raster, im Text oder in einer Datei angezeigt werden.

- Es gibt Neuzeichnungsprobleme beim Wechseln zwischen mehreren Abfragefenstern. Weitere Informationen finden Sie unter [UserVoice](https://feedback.azure.com/forums/908035/suggestions/37474042). Um dieses Problem zu umgehen, können Sie die Hardwarebeschleunigung unter „Extras“ > „Optionen“ deaktivieren.

## <a name="downloadssdtmediadownloadpng-ssms-1791httpsgomicrosoftcomfwlinklinkid2043154clcid0x409"></a>![Herunterladen von](../ssdt/media/download.png) [SSMS 17.9.1](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)

- Releasenummer: 17.9.1<br>
- Buildnummer: 14.0.17289.0<br>
- Releasedatum: 21. November 2018

17.9.1 ist ein kleines Update für 17.9 mit die folgenden Fehlerbehebungen:

- Korrektur für folgenden Fehler: Bei Verwendung des Authentifizierungstyps „Azure Active Directory: Universell mit MFA-Unterstützung“ für den SQL-Abfrage-Editor stellen Benutzer möglicherweise fest, dass die Verbindung bei jedem Aufruf der Abfrage geschlossen und erneut geöffnet wird. Nebeneffekte eines solchen Schließens der Verbindung sind u. a., dass globale temporäre Tabellen unerwartet gelöscht werden und mitunter der Verbindung eine neue SPID gegeben wird.
- Ein seit langem bestehendes Problem wurde behoben, bei dem der Wiederherstellungsplan keinen Wiederherstellungsplan finden konnte oder unter bestimmten Bedingungen einen ineffizienten Wiederherstellungsplan generieren konnte.
- Ein Problem im Assistenten „Datenschichtanwendung importieren“ wurde behoben, das bei der Verbindung mit einer Azure SQL-Datenbank einen Fehler verursachen konnte.

> [!NOTE]
> In andere Sprachen als Englisch lokalisierte Releases von SSMS 17.x benötigen das [KB 2862966-Sicherheitsupdatepaket](https://support.microsoft.com/kb/2862966) für die Installation unter den folgenden Windows-Systemen: Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2.

[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804)| [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404)| [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409)| [Französisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c)| [Deutsch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407)| [Italienisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410)| [Japanisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411)| [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412)| [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416)| [Russisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419)| [Spanisch](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)

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
