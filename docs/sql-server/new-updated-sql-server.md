---
title: Aktualisiert – Dokumentation zu SQL Server | Microsoft-Dokumentation
description: Codeausschnitte anzeigen aktualisierter Inhalt in zuletzt geänderten Dokumentation für SQL Server.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 3575f65c751d91e2a32cf0acbf76665b42378d6a
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084432"
---
# <a name="new-and-recently-updated-sql-server-docs"></a>Neu und zuletzt kürzlich aktualisiert: Dokumentation zu SQL Server Data Tools



Beinahe jeden Tag aktualisiert Microsoft einige der vorhandenen Artikel auf der Dokumentationswebsite [Docs.Microsoft.com](http://docs.microsoft.com/). In diesem Artikel werden Auszüge aus den zuletzt aktualisierten Artikeln wiedergegeben. Links zu den neuen Artikel werden ggf. ebenfalls aufgeführt.

Dieser Artikel wurde im Rahmen eines Programms erstellt, das in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug mit falscher Formatierung oder als Markdown aus dem Quellartikel angezeigt werden. Bilder werden hier nie wiedergegeben.

Neueste Updates werden für den folgenden Datumsbereich und Themenbereich gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Themenbereich*: &nbsp; **SQL Server**




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt wurden

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


1. [Mitwirken an der SQL Server-Dokumentation](sql-server-docs-contribute.md)
2. [Ergänzende Datenschutzbestimmungen zu SQL Server](sql-server-privacy.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszügen

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die Auszüge hier werden getrennt vom richtigen semantischen Kontext angezeigt. Darüber hinaus wird ein Auszug manchmal getrennt von der wichtigen Markdownsyntax wiedergegeben, die ihn im ursprünglichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Anhand dieser Auszüge sollen Sie nur entscheiden können, ob Sie sich die Zeit nehmen und den eigentlichen Artikel besuchen möchten.

Kopieren Sie aus diesem und anderen Gründen auf gar keinen Fall Code aus diesen Auszügen, und gehen Sie bei keinem Textauszug von einer 100-prozentigen Richtigkeit der Informationen aus. Besuchen Sie stattdessen den eigentlichen Artikel.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Kompakte Liste der Artikel, die vor Kurzem aktualisiert wurden

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

1. [SQL Server 2012 Service Pack – Anmerkungen zu dieser Version](#TitleNum_1)
2. [Versionsanmerkungen zu SQL Server 2016](#TitleNum_2)
3. [SQL Server Documentation (SQL Server-Dokumentation)](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-sql-server-2012-service-pack-release-notessql-server-2012-sp4-release-notesmd"></a>1. &nbsp; [SQL Server 2012 Service Pack – Anmerkungen zu dieser Version](sql-server-2012-sp4-release-notes.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Weiter](#TitleNum_2))

<!-- Source markdown line 57.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 ce108992ea942b4a11f30d67a1a52d7f26868caa a6269ba2cb2d3b3b54aebf5087dc4d513e476a96  (PR=5676  ,  Filename=sql-server-2012-sp4-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- **Partitionierung mit der automatischen Soft-NUMA**: Mit der Version SQL 2014 SP2 wird die Partitionierung mit der automatischen [Soft-NUMA](https://msdn.microsoft.com/library/ms345357(SQL.120).aspx) eingeführt, wenn das Ablaufverfolgungsflag 8079 auf Serverebene aktiviert ist. Wenn das Ablaufverfolgungsflag 8079 beim Starten aktiviert ist, fragt SQL Server 2014 SP2 das Hardwarelayout ab und konfiguriert soft-NUMA automatisch auf Systemen, die mindestens acht CPU pro NUMA-Knoten vermelden. Die automatische soft-NUMA ist Hyperthread-fähig (HT/logischer Prozessor). Durch die Partitionierung und Erstellung von weiteren Knoten wird die Hintergrundverarbeitung skaliert, indem die Anzahl von Listenern, Skalierungen sowie Netzwerk- und Verschlüsselungsfunktionen erhöht wird. Wir empfehlen Ihnen, die Leistung der Arbeitsauslastung mit der automatischen soft-NUMA vor der Aktivierung im Rahmen der Produktion zunächst zu testen.

**Versionsanmerkungen zu Service Pack 3**


**Downloadseiten**

- [SQL Server 2012 SP3 Feature Pack](http://go.microsoft.com/fwlink/?linkid=615935)
- [SQL Server 2012 SP3 Express](http://go.microsoft.com/fwlink/?linkid=692144)

Genauere Informationen zum Identifizieren des Speicherorts und Namens der basierend auf Ihrer aktuell installierten Version zu herunterladenden Datei finden Sie im Abschnitt „Select the correct file to download“ (Auswählen der richtigen Datei zum Herunterladen) unter [SQL Server 2012 Service Pack 3 release information (Versionsinformationen zu SQL Server 2012 Service Pack 3)](https://support.microsoft.com/help/3072779/sql-server-2012-service-pack-3-release-information).

**Versionsanmerkungen zu Service Pack 2**


**Downloadseiten**

- [SQL Server 2012 SP2 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=401008)
- [SQL Server 2012 SP2 Express](http://go.microsoft.com/fwlink/?LinkID=401007)

Identifizieren Sie anhand der unten stehenden Tabelle und entsprechend der derzeit installierten Version den Speicherort und den Namen der herunterzuladenden Datei. Downloadseiten enthalten Systemanforderungen und grundlegende Installationsanweisungen.

|Wenn dies Ihre aktuell installierte Version ist:...|Und Sie dies möchten:...|Herunterladen und installieren...|



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-server-2016-release-notessql-server-2016-release-notesmd"></a>2. &nbsp; [Versionsanmerkungen zu SQL Server 2016](sql-server-2016-release-notes.md)

*Aktualisiert: 27.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Vorheriger](#TitleNum_1) | [Nächster](#TitleNum_3))

<!-- Source markdown line 25.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 a15210866acf524dae49f3a7fd7957c9ffa6a78a 7257cb2017779242cbb8fa2b562f4b102502e942  (PR=5695  ,  Filename=sql-server-2016-release-notes.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->



  Im folgenden Artikel werden Einschränkungen und Probleme mit Releases von SQL Server 2016, Service Packs inbegriffen, beschrieben. Informationen zu Neuerungen finden Sie unter [Neues im Berichts-Generator für SQL Server 2016](https://docs.microsoft.com/sql/sql-server/what-s-new-in-sql-server-2016).

- Laden Sie SQL Server 2016 aus dem **[Evaluierungscenter](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)** herunter.
- Azure Virtual Machine (klein) Haben Sie ein Azure-Konto?  Wechseln Sie anschließend **[hierhin](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** , um einen virtuellen Computer zu starten, auf dem SQL Server 2016 SP1 bereits installiert ist.
- SSMS herunterladen: Wechseln Sie zu **[Herunterladen von SQL Server Management Studio (SSMS)]**, um die neueste Version von SQL Server Management Studio abzurufen.

**<a name="bkmk_2016sp2"></a>SQL Server 2016 Service Pack 2 (SP2)**


SQL Server 2016 SP2 enthält alle kumulativen Updates bis einschließlich CU8, die nach SQL Server 2016 SP1 veröffentlicht wurden.

- [Microsoft Download SQL Server 2016 Service Pack 2 (SP2)](https://go.microsoft.com/fwlink/?linkid=869608)
- Eine vollständige Liste der Updates finden Sie unter [SQL Server 2016 Service Pack 2 release information (Releaseinformationen zu SQL Server 2016 Service Pack 2)](https://support.microsoft.com/help/4052908/sql-server-2016-service-pack-2-release-information).



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-sql-server-documentationsql-server-technical-documentationmd"></a>3. &nbsp; [SQL Server-Dokumentation](sql-server-technical-documentation.md)

*Aktualisiert: 27.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Zurück](#TitleNum_2))

<!-- Source markdown line 77.  ms.author= craigg.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 0262010ba39785a6d46b42f8469fb17701f13008 c69a83236391d039381a93c65ebbb2efa53e11b8  (PR=5695  ,  Filename=sql-server-technical-documentation.md  ,  Dirpath=docs\sql-server\  ,  MergeCommitSha40=d1c114b98fea55d2d4829dffdb25daf1b3f73dc2) -->




<!-- : : : m-r -->
**Testen Sie SQL Server!**
- Download aus dem Evaluierungscenter: [SQL Server für Windows herunterladen](http://go.microsoft.com/fwlink/?LinkID=829477)
- Download aus dem Evaluierungscenter: SQL Server Management Studio (SSMS) herunterladen
- Download aus dem Evaluierungscenter: SQL Server Data Tools (SSDT) herunterladen
- Erstellen eines virtuellen Computers: [Abrufen eines virtuellen Computers mit SQL Server](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)





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
- [Neu und aktualisiert (0+0): Dokumente zu **Data Quality Services für SQL**](../data-quality-services/new-updated-data-quality-services.md)
- [Neu und aktualisiert (0+0): Dokumente zu **Data Mining-Erweiterungen (DMX) für SQL**](../dmx/new-updated-dmx.md)
- [Neu und aktualisiert (0+0): Dokumente zu **Master Data Services (MDS) für SQL**](../master-data-services/new-updated-master-data-services.md)
- [Neu und aktualisiert (0+0): Dokumente zu **mehrdimensionalen Ausdrücken (MDX) für SQL**](../mdx/new-updated-mdx.md)
- [Neu und aktualisiert (0+0): Dokumente zu **ODBC (Open Database Connectivity) für SQL**](../odbc/new-updated-odbc.md)
- [Neu + Aktualisiert (0+0): **PowerShell für SQL-Dokumente**](../powershell/new-updated-powershell.md)
- [Neu und aktualisiert (0+0): **Dokumente zu Beispielen für SQL**](../samples/new-updated-samples.md)
- [Neu + Aktualisiert (0+0): **Dokumente zu SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Neu und aktualisiert (0+0): **Dokumente zu XQuery für SQL**](../xquery/new-updated-xquery.md)

