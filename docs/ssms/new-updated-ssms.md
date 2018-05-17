---
title: 'Aktualisiert: Dokumentation zu SSMS für SQL Server | Microsoft-Dokumentation'
description: Anzeigen von Codeausschnitten für aktualisierten Inhalt für kürzliche Änderungen in der Dokumentation zu SQL Server Management Studio (SSMS) für Microsoft SQL Server
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssms
ms.date: 04/28/2018
ms.openlocfilehash: 1ce446219f71baca0f4cdedc835fca929b572a0f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-server-management-studio-ssms-for-sql-server"></a>Neu und kürzlich aktualisiert: SQL Server Management Studio (SSMS) für SQL Server



Beinahe jeden Tag aktualisiert Microsoft einige der vorhandenen Artikel auf der Dokumentationswebsite [Docs.Microsoft.com](http://docs.microsoft.com/). In diesem Artikel werden Auszüge aus den zuletzt aktualisierten Artikeln wiedergegeben. Links zu den neuen Artikel werden ggf. ebenfalls aufgeführt.

Dieser Artikel wurde im Rahmen eines Programms erstellt, das in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug mit falscher Formatierung oder als Markdown aus dem Quellartikel angezeigt werden. Bilder werden hier nie wiedergegeben.

Neueste Updates werden für den folgenden Datumsbereich und Themenbereich gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Themenbereich:* &nbsp; **SQL Server Management Studio (SSMS)**




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt wurden

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


1. [Tutorial: Herstellen einer Verbindung mit und Abfragen von einer SQL Server-Instanz über SQL Server Management Studio](tutorials/connect-query-sql-server.md)
2. [Tutorial: Erstellen von Skripts für Objekte in SQL Server Management Studio](tutorials/scripting-ssms.md)
3. [Tutorial: SQL Server Management Studio-Komponenten und -Konfiguration](tutorials/ssms-configuration.md)
4. [Tutorial: Additional Tips and Tricks for using SSMS (Tutorial: Zusätzliche Tipps und Tricks für die Verwendung von SSMS)](tutorials/ssms-tricks.md)
5. [Tutorial: Verwenden von Vorlagen in SQL Server Management Studio](tutorials/templates-ssms.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszügen

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die Auszüge hier werden getrennt vom richtigen semantischen Kontext angezeigt. Darüber hinaus wird ein Auszug manchmal getrennt von der wichtigen Markdownsyntax wiedergegeben, die ihn im ursprünglichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Anhand dieser Auszüge sollen Sie nur entscheiden können, ob Sie sich die Zeit nehmen und den eigentlichen Artikel besuchen möchten.

Kopieren Sie aus diesem und anderen Gründen auf gar keinen Fall Code aus diesen Auszügen, und gehen Sie bei keinem Textauszug von einer 100-prozentigen Richtigkeit der Informationen aus. Besuchen Sie stattdessen den eigentlichen Artikel.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Kompakte Liste der Artikel, die vor Kurzem aktualisiert wurden

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

1. [SQL Server Management Studio – Änderungsprotokoll (SSMS)](#TitleNum_1)
2. [Tutorials zu SQL Server Management Studio (SSMS)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-management-studio---changelog-ssmssql-server-management-studio-changelog-ssmsmd"></a>1. &nbsp; [SQL Server Management Studio – Änderungsprotokoll (SSMS)](sql-server-management-studio-changelog-ssms.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Weiter](#TitleNum_2))

<!-- Source markdown line 27.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 eb641ac39386a26a76dc303f5bd55eb3f9f4c78d f560f09b51ea30b255c10f7eb86857c3090881d9  (PR=5676  ,  Filename=sql-server-management-studio-changelog-ssms.md  ,  Dirpath=docs\ssms\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[SSMS 17.6]**


Releasenummer: 17.6<br>
Buildnummer: 14.0.17230.0<br>
Releasedatum: 20. März 2018

**Neuigkeiten**


**SSMS Allgemein**

Verwaltete SQL-Datenbank-Instanz:

- Unterstützung für die [verwaltete Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance). Diese neue Bereitstellungsoption (aktuell in der Vorschauversion) in Azure SQL-Datenbank gewährleistet nahezu 100 % Kompatibilität mit SQL Server in einer lokalen Umgebung. Außerdem sorgt sie für Konformität mit einer nativen [VNet](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview)-Implementierung (Azure Virtual Network), die Lösungen für allgemeine Sicherheitsprobleme bereitstellt, und mit einem [Geschäftsmodell](https://azure.microsoft.com/pricing/details/sql-database/), das für Kunden von SQL Server in einer lokalen Umgebung geeignet ist.
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

- Unterstützung für die Bereitstellung von Paketen in einer [verwalteten SQL-Datenbank-Instanz](docs/ssms/https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-tutorials-for-sql-server-management-studio-ssmstutorialstutorial-sql-server-management-studiomd"></a>2. &nbsp; [Tutorials zu SQL Server Management Studio (SSMS)](tutorials/tutorial-sql-server-management-studio.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Zurück](#TitleNum_1))

<!-- Source markdown line 49.  ms.author= "mathoma".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b272c75bab04912ebb706098cf6b6a6c80d9e2b8 d453ebc8251fb83ffcb1af58c9a08bb65b3e9fa2  (PR=5676  ,  Filename=tutorial-sql-server-management-studio.md  ,  Dirpath=docs\ssms\tutorials\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- Tutorial: Connect & Query SQL Server using SSMS (Tutorial: Herstellen einer Verbindung mit und Abfragen von SQL Server über SSMS)

    In diesem Tutorial erfahren Sie, wie Sie eine Verbindung mit einer SQL Server-Instanz herstellen. Außerdem lernen Sie einige grundlegende T-SQL-Befehle (Transact-SQL) kennen, mit denen Sie eine neue Datenbank erstellen und anschließend abfragen.

- Tutorial: Scripting Objects in SSMS (Tutorial: Erstellung von Skripts für Objekte in SSMS)

    In diesem Tutorial erfahren Sie, wie Sie Skripts für verschiedene Objekte wie Datenbanken und Abfragen in SSMS erstellen.

- Tutorial: Using Templates in SSMS (Tutorial: Verwenden von Vorlagen in SSMS)

    In diesem Tutorial erfahren Sie, wie Sie mit bereits vorhandenen Vorlagen in SSMS arbeiten können. Vorlagen sind ein wenig bekanntes Feature, das eine Reihe von Transact-SQL-Codeausschnitten für unterschiedliche Datenbankadministrationsaufgaben speichert.

- Tutorial: SSMS Configuration (Tutorial: SSMS-Konfiguration)

    In diesem Tutorial lernen Sie die Grundlagen zum Konfigurieren Ihrer SSMS-Umgebung kennen, z.B. die Änderung des Umgebungslayouts. Es werden ebenso die unterschiedlichen SSMS-Komponenten erklärt.


- Tutorial: Zusätzliche Tipps und Tricks für die Verwendung von SSMS

    In diesem Tutorial lernen Sie zusätzliche Tipps und Tricks zur Nutzung von SSMS kennen. Folgende Themen werden dabei behandelt:
    - Kommentieren von Text und Aufheben von Auskommentierungen
    - Verwenden von Texteinzügen
    - Filtern von Objekten im Objekt-Explorer
    - Zugreifen auf das SQL Server-Fehlerprotokoll
    - Suchen eines Instanznamens








## <a name="similar-articles-about-new-or-updated-articles"></a>Ähnliche Artikel zu neuen oder aktualisierten Artikeln

Dieser Abschnitt enthält sehr ähnliche Artikel für zuletzt aktualisierte Artikel in anderen Themenbereichen innerhalb des gleichen GitHub-Repositorys: [MicrosoftDocs/sql-docs-pr](https://github.com/MicrosoftDocs/sql-docs/).



#### <a name="subject-areas-that-do-have-new-or-recently-updated-articles"></a>Themenbereiche, die *über* neue oder kürzlich aktualisierte Artikel verfügen

- [Neu und aktualisiert (11+6):&nbsp; Dokumente zu &nbsp;**Advanced Analytics für SQL**](../advanced-analytics/new-updated-advanced-analytics.md)
- [Neu und aktualisiert (18+0):&nbsp; Dokumente zu &nbsp;**Analysis Services für SQL**](../analysis-services/new-updated-analysis-services.md)
- [Neu und aktualisiert (218+14):**Dokumente zum**Herstellen einer Verbindung mit SQL](../connect/new-updated-connect.md)
- [Neu und aktualisiert (14+0):&nbsp; Dokumente zur &nbsp;**Datenbank-Engine für SQL**](../database-engine/new-updated-database-engine.md)
- [Neu und aktualisiert (3+2):&nbsp; Dokumente zu &nbsp;**Integration Services für SQL**](../integration-services/new-updated-integration-services.md)
- [Neu und aktualisiert (3+3):&nbsp; Dokumente zu &nbsp;**Linux für SQL**](../linux/new-updated-linux.md)
- [Neu und aktualisiert (7+10):&nbsp; Dokumente zu &nbsp;**relationalen Datenbanken für SQL**](../relational-databases/new-updated-relational-databases.md)
- [Neu und aktualisiert (0+2):&nbsp; Dokumente zu &nbsp;**Reporting Services für SQL**](../reporting-services/new-updated-reporting-services.md)
- [Neu und aktualisiert (1+3):&nbsp; Dokumente zu &nbsp;**SQL Operations Studio**](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [Neu und aktualisiert (2+3):&nbsp; Dokumente zu &nbsp;**Microsoft SQL Server**](../sql-server/new-updated-sql-server.md)
- [Neu und aktualisiert (1+1):&nbsp; Dokumente zu &nbsp;**SQL Server Data Tools (SSDT)**](../ssdt/new-updated-ssdt.md)
- [Neu und aktualisiert (5+2):&nbsp; Dokumente zu &nbsp;**SQL Server Management Studio (SSMS)**](../ssms/new-updated-ssms.md)
- [Neu und aktualisiert (0+2):&nbsp; Dokumente zu &nbsp;**Transact-SQL**](../t-sql/new-updated-t-sql.md)
- [Neu + Aktualisiert (1+1):&nbsp; Dokumente zu &nbsp;**Tools für SQL**](../tools/new-updated-tools.md)



#### <a name="subject-areas-that-do-not-have-any-new-or-recently-updated-articles"></a>Themenbereiche, die *nicht* über neue oder kürzlich aktualisierte Artikel verfügen

- [Neu und aktualisiert (0+0): Dokumente zum **Analytics Platform System für SQL**](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [New + Updated (0+0): **Data Quality Services for SQL** docs (Neu + Aktualisiert (0+0): Data Quality Services für SQL-Dokumente)](../data-quality-services/new-updated-data-quality-services.md)
- [New + Updated (0+0): **Data Mining Extensions (DMX) for SQL** docs (Neu + Aktualisiert (0+0): Data Mining-Erweiterungen (DMX) für SQL)](../dmx/new-updated-dmx.md)
- [New + Updated (0+0): **Master Data Services (MDS) for SQL** docs (Neu + Aktualisiert (0+0): Dokumentation zu Master Data Services (MDS) für SQL)](../master-data-services/new-updated-master-data-services.md)
- [New + Updated (0+0): **Multidimensional Expressions (MDX) for SQL** docs (Neu + Aktualisiert (0+0): Mehrdimensionale Ausdrücke für SQL)](../mdx/new-updated-mdx.md)
- [New + Updated (0+0): **ODBC (Open Database Connectivity) for SQL** docs (Neu + Aktualisiert (0+0): Open Database Connectivity für SQL-Dokumente)](../odbc/new-updated-odbc.md)
- [New + Updated (0+0): **PowerShell for SQL** docs (Neu + Aktualisiert (0+0): PowerShell für SQL-Dokumente)](../powershell/new-updated-powershell.md)
- [New + Updated (0+0): **Samples for SQL** docs (Neu + Aktualisiert (0+0): Beispiele für SQL-Dokumente)](../samples/new-updated-samples.md)
- [New + Updated (0+0): **SQL Server Migration Assistant (SSMA)** docs (Neu + Aktualisiert (0+0): SQL Server Migration Assistant-Dokumente (SSMA))](../ssma/new-updated-ssma.md)
- [New + Updated (0+0): **XQuery for SQL** docs (Neu + Aktualisiert (0+0): XQuery für SQL-Dokumente)](../xquery/new-updated-xquery.md)

