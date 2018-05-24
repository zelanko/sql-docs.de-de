---
title: 'Aktualisiert: Transact-SQL-Dokumente | Microsoft-Dokumentation'
description: Anzeigen von Codeausschnitten aktualisierten Inhalts in zuletzt geänderter Dokumentation für Transact-SQL.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: t-sql
ms.date: 04/28/2018
ms.openlocfilehash: b1bc891bf7edc4cd82c38c8d647c279828190298
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-transact-sql-docs"></a>Neu und zuletzt aktualisiert: Transact-SQL-Dokumente



Beinahe jeden Tag aktualisiert Microsoft einige der vorhandenen Artikel auf der Dokumentationswebsite [Docs.Microsoft.com](http://docs.microsoft.com/). In diesem Artikel werden Auszüge aus den zuletzt aktualisierten Artikeln wiedergegeben. Links zu den neuen Artikel werden ggf. ebenfalls aufgeführt.

Dieser Artikel wurde im Rahmen eines Programms erstellt, das in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug mit falscher Formatierung oder als Markdown aus dem Quellartikel angezeigt werden. Bilder werden hier nie wiedergegeben.

Neueste Updates werden für den folgenden Datumsbereich und Themenbereich gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Themenbereich:* &nbsp; **Transact-SQL**.




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt wurden

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


***Dieses Mal sind keine neuen Artikel aufgeführt.***



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszügen

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die Auszüge hier werden getrennt vom richtigen semantischen Kontext angezeigt. Darüber hinaus wird ein Auszug manchmal getrennt von der wichtigen Markdownsyntax wiedergegeben, die ihn im ursprünglichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Anhand dieser Auszüge sollen Sie nur entscheiden können, ob Sie sich die Zeit nehmen und den eigentlichen Artikel besuchen möchten.

Kopieren Sie aus diesem und anderen Gründen auf gar keinen Fall Code aus diesen Auszügen, und gehen Sie bei keinem Textauszug von einer 100-prozentigen Richtigkeit der Informationen aus. Besuchen Sie stattdessen den eigentlichen Artikel.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Kompakte Liste der Artikel, die vor Kurzem aktualisiert wurden

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

1. [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](#TitleNum_1)
2. [RESTORE-Anweisungen (Transact-SQL)](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-alter-database-scoped-configuration-transact-sqlstatementsalter-database-scoped-configuration-transact-sqlmd"></a>1. &nbsp; [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](statements/alter-database-scoped-configuration-transact-sql.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Weiter](#TitleNum_2))

<!-- Source markdown line 150.  ms.author= "carlrab".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 f6833910b664d0059a9073589807b195052325b3 bf969f123b22e6ebc650380a6905156f26ed6ca6  (PR=0  ,  Filename=alter-database-scoped-configuration-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



XTP_PROCEDURE_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**Gilt für** :  *{hier stehen enthaltene Inhalte}*

Aktiviert oder deaktiviert die Sammlung von Ausführungsstatistiken auf Modulebene für nativ kompilierte T-SQL-Module in der aktuellen Datenbank. Der Standardwert ist OFF. Die Ausführungsstatistiken werden in [sys.dm_exec_procedure_stats] wiedergegeben.

Ausführungsstatistiken auf Modulebene für nativ kompilierte T-SQL-Module werden gesammelt, wenn diese Option auf „ON“ festgelegt ist, oder die Sammlung von Statistiken durch [sp_xtp_control_proc_exec_stats] aktiviert ist.

XTP_QUERY_EXECUTION_STATISTICS  **=** { ON | **OFF** }

**Gilt für** :  *{hier stehen enthaltene Inhalte}*

Aktiviert oder deaktiviert die Sammlung von Ausführungsstatistiken auf Anweisungsebene für nativ kompilierte T-SQL-Module in der aktuellen Datenbank. Der Standardwert ist OFF. Die Ausführungsstatistik wird in [sys.dm_exec_query_stats] und im [Abfragespeicher] wiedergegeben.

Ausführungsstatistiken auf Anweisungsebene für nativ kompilierte T-SQL-Module werden gesammelt, wenn diese Option auf „ON“ festgelegt ist, oder die Sammlung von Statistiken durch [sp_xtp_control_query_exec_stats] aktiviert ist.

Weitere Informationen über die Leistungsüberwachung von nativ kompilierten T-SQL-Modulen finden Sie unter [Überwachen der Leistung von systemintern kompilierten gespeicherten Prozeduren].



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-restore-statements-transact-sqlstatementsrestore-statements-transact-sqlmd"></a>2. &nbsp; [RESTORE-Anweisungen (Transact-SQL)](statements/restore-statements-transact-sql.md)

*Aktualisiert: 13.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Zurück](#TitleNum_1))

<!-- Source markdown line 339.  ms.author= "barbkess".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2902efb58bb964d3e9a0660956690d37f0397c00 36186a7cffd26ffa54a83e383ffd752dbc568a4d  (PR=0  ,  Filename=restore-statements-transact-sql.md  ,  Dirpath=docs\t-sql\statements\  ,  MergeCommitSha40=f70f24bff1677b33c661abd13726f491ce32b305) -->



**Allgemeine Hinweise zur verwalteten SQL-Datenbank-Instanz**


Für eine asynchrone Wiederherstellung wird die Wiederherstellung fortgesetzt, selbst wenn die Verbindung zum Client unterbrochen wird. Wenn Ihre Verbindung getrennt wird, können Sie die Ansicht [sys.dm_operation_status] auf den Status eines Wiederherstellungsvorgangs überprüfen (sowie für CREATE und DROP von Datenbanken).

Die folgenden Datenbankoptionen werden festgelegt oder überschrieben und können später nicht geändert werden:

- NEW_BROKER (wenn der Broker nicht in der BAK-Datei aktiviert ist)
- ENABLE_BROKER (wenn der Broker nicht in der BAK-Datei aktiviert ist)
- AUTO_CLOSE=OFF (wenn für eine Datenbank in der BAK-Datei AUTO_CLOSE=ON festgelegt ist)
- RECOVERY FULL (wenn eine Datenbank in der BAK-Datei über den Wiederherstellungsmodus SIMPLE oder BULK_LOGGED verfügt)
- Eine arbeitsspeicheroptimierte Dateigruppe wird hinzugefügt und hat XTP aufgerufen, wenn sie nicht in der BAK-Quelldatei war. Alle vorhandenen arbeitsspeicheroptimierten Dateigruppen werden in XTP umbenannt.
- Die Optionen SINGLE_USER und RESTRICTED_USER werden in MULTI_USER konvertiert.

**Einschränkungen bei verwalteten SQL-Datenbank-Instanzen**

Diese Einschränkungen gelten:

- BAK-Dateien, die mehrere Sicherungssätze enthalten, können nicht wiederhergestellt werden.
- BAK-Dateien, die mehrere Protokolldateien enthalten, können nicht wiederhergestellt werden.
- Die Wiederherstellung schlägt fehl, wenn die BAK-Datei FILESTREAM-Daten enthält.
- Sicherungen, die Datenbanken enthalten, die über aktive In-Memory-Objekte verfügen, können derzeit nicht wiederhergestellt werden.
- Sicherungen, die Datenbanken enthalten, in denen In-Memory-Objekte existiert haben, können derzeit nicht wiederhergestellt werden.
- Sicherungen, die Datenbanken im schreibgeschützten Modus enthalten, können derzeit nicht wiederhergestellt werden. Diese Einschränkung wird bald entfernt.

Weitere Informationen finden Sie unter [verwaltete Instanz].







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
- [Neu und aktualisiert (0+0): Dokumente zu **Beispielen für SQL**](../samples/new-updated-samples.md)
- [Neu + Aktualisiert (0+0): Dokumente zu **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Neu und aktualisiert (0+0): Dokumente zu **XQuery für SQL**](../xquery/new-updated-xquery.md)

