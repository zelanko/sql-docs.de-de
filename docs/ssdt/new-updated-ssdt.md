---
title: 'Aktualisiert: Dokumentation zu SSDT für SQL Server | Microsoft-Dokumentation'
description: Anzeigen von Codeausschnitten für aktualisierten Inhalt für kürzliche Änderungen in der Dokumentation zu SQL Server Data Tools (SSDT) für Microsoft SQL Server
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.prod_service: sql-non-specified
ms.component: ssdt
ms.date: 04/28/2018
ms.openlocfilehash: 99b0844803e1ce95bd6f73b0d45a2baf867428ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="new-and-recently-updated-sql-server-data-tools-ssdt"></a>Neu und zuletzt kürzlich aktualisiert: SQL Server Data Tools (SSDT)



Beinahe jeden Tag aktualisiert Microsoft einige der vorhandenen Artikel auf der Dokumentationswebsite [Docs.Microsoft.com](http://docs.microsoft.com/). In diesem Artikel werden Auszüge aus den zuletzt aktualisierten Artikeln wiedergegeben. Links zu den neuen Artikel werden ggf. ebenfalls aufgeführt.

Dieser Artikel wurde im Rahmen eines Programms erstellt, das in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug mit falscher Formatierung oder als Markdown aus dem Quellartikel angezeigt werden. Bilder werden hier nie wiedergegeben.

Neueste Updates werden für den folgenden Datumsbereich und Themenbereich gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Themenbereich:* &nbsp; **SQL Server Data Tools (SSDT)**.




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt wurden

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


1. [Azure Active Directory-Unterstützung in SQL Server Data Tools (SSDT)](azure-active-directory.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszügen

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die Auszüge hier werden getrennt vom richtigen semantischen Kontext angezeigt. Darüber hinaus wird ein Auszug manchmal getrennt von der wichtigen Markdownsyntax wiedergegeben, die ihn im ursprünglichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Anhand dieser Auszüge sollen Sie nur entscheiden können, ob Sie sich die Zeit nehmen und den eigentlichen Artikel besuchen möchten.

Kopieren Sie aus diesem und anderen Gründen auf gar keinen Fall Code aus diesen Auszügen, und gehen Sie bei keinem Textauszug von einer 100-prozentigen Richtigkeit der Informationen aus. Besuchen Sie stattdessen den eigentlichen Artikel.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Kompakte Liste der Artikel, die vor Kurzem aktualisiert wurden

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

1. [Änderungsprotokoll für SQL Server Data Tools (SSDT)](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-changelog-for-sql-server-data-tools-ssdtchangelog-for-sql-server-data-tools-ssdtmd"></a>1. &nbsp; [Änderungsprotokoll für SQL Server Data Tools (SSDT)](changelog-for-sql-server-data-tools-ssdt.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 29.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 de18314845cffa197b3fd2ed868f2c330760bedb 5487de1ed57c16a6517a3a8849f412c208f1889f  (PR=5676  ,  Filename=changelog-for-sql-server-data-tools-ssdt.md  ,  Dirpath=docs\ssdt\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->





**SSDT für Visual Studio 2017 (15.6.0)**

Buildnummer: 14.0.16162.0 Veröffentlichungsdatum: 10 April 2018

**Neuigkeiten**


**SSIS:**

1.  Korrigiert: Die AS-Verarbeitungsaufgabe protokolliert keine Verarbeitungsschritte für SQL Server 2016 und SQL Server 2017.
2.  Korrigiert: Zugriffsverletzung während des Öffnens von DTSX mit sehr langen, nicht englischsprachigen Aufgabennamen in SSDT.
3.  Korrigiert: Variablenliste von ScriptTask verschwindet manchmal in der Benutzeroberfläche des Tasks.
4.  Korrigiert: Das Hinzufügen einer Kopie vorhandener Pakete schlägt fehl, wenn das Paket in SQL Server gespeichert ist.
5.  Korrigiert: Der Fokus bleibt beim Zugriff auf das Kombinationsfeld in einigen Dialogfeldern des Editors hängen.
6.  Korrigiert: Der Hintergrund ändert sich beim Wechseln ins VS-Design nicht.
7.  Korrigiert: Anmerkungs- und Ladebezeichnung sind im dunklen Design nicht sichtbar.
8.  Korrigiert: Die Statuseigenschaft wird für deaktivierte Elemente der SSIS-Toolbox nicht ordnungsgemäß definiert.
9.  Korrigiert: Fehler bei der Ausführung von WebServiceTask.
10. Korrigiert: Die Paketbereitstellung schlägt fehl, wenn die Verbindungszeichenfolge auf eine Variable festgelegt wird, die über einen Ausdruck verfügt, der von den Projektparametern abhängig ist.

**Installationsprogramm:**

1.  Fügen Sie den Link zum „Programm zur Verbesserung der Benutzerfreundlichkeit für SQL Server Data Tools“ in den Datenschutzbestimmungen hinzu.
2.  Korrigiert: Das Visual Studio-Installer-Fenster erscheint bei der Auswahl von „Neue SQL Server Data Tools für Visual Studio 2017-Instanz installieren“.

**Bekannte Probleme:**

1.  Der SSIS-Task zum Ausführen eines Pakets unterstützt kein Debugging, wenn „ExecuteOutOfProcess“ auf TRUE festgelegt ist. Dieses Problem gilt nur für das Debuggen. Das Speichern, Bereitstellen und Ausführen über „DTExec.exe“ oder den SSIS-Katalog wird nicht beeinträchtigt.



**SSDT für Visual Studio 2017 (15.5.2)**

Buildnummer: 14.0.16156.0

**Neuigkeiten**


**SSIS**
1.  Korrigiert: Bei der Migration von SSIS 2008-Projekten tritt ein Fehler auf, wenn SSAS und SSIS auf der gleichen VS 2017-Instanz installiert sind.
2.  Korrigiert: RDLC-Projekte können nicht erstellt werden, wenn sowohl der RDLC-Bericht-Designer als auch SSIS auf der gleichen VS 2017-Instanz installiert sind.







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

