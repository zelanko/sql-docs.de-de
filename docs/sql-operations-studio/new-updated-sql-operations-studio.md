---
title: 'Aktualisiert: SQL Operations Studio-Dokumentation | Microsoft-Dokumentation'
description: Anzeigen von Codeausschnitten für aktualisierten Inhalt für kürzliche Änderungen in der Dokumentation für SQL Operations Studio.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 84ee3d7d346c8cddbf5251e0d63bb2ae222defb3
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083452"
---
# <a name="new-and-recently-updated-sql-operations-studio-docs"></a>Neu und zuletzt aktualisiert: SQL Operations Studio-Dokumentation



Beinahe jeden Tag Microsoft updates einige vorhandene Artikel auf dessen [Docs.Microsoft.com](http://docs.microsoft.com/) Dokumentationswebsite. Dieser Artikel zeigt Auszüge aus den zuletzt aktualisierten Artikel. Links zu den neuen Artikel, möglicherweise ebenfalls aufgeführt.

In diesem Artikel wird von einem Programm generiert, die in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug aus dem Quellartikel mit sich Formatierung oder als Markdown angezeigt. Bilder werden hier nicht angezeigt.

Neueste Updates werden für folgenden Datumsbereich und Betreff gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Themenbereich:* &nbsp; **SQL Operations Studio**.




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


- [Erweitern der Funktionalität von SQL Operations Studio (Vorschau)](extensions.md)

<!-- GeneMi:  I MANUALLY replace the ugly !INCLUDE with the name from inside the includes file. -->


&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszüge

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die hier angezeigten Auszüge werden getrennt vom richtigen semantische kontextabhängig angezeigt. Darüber hinaus wird manchmal ein Auszug vom wichtige Markdown-Syntax getrennt, die sie in den tatsächlichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Die Auszüge können nur Sie wissen, ob Ihre Interessen dauert rechtfertigen, klicken Sie auf, und besuchen den tatsächlichen Artikel.

Kopieren Sie für diese und andere Gründe Code nicht von diesen verwendet, und nehmen Sie nicht als genaue Wahrheit alle Textauszug. Besuchen Sie stattdessen den tatsächlichen Artikel aus.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Compact Liste von Artikeln, die vor kurzem aktualisiert

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

1. [Herunterladen Sie und installieren Sie SQL Operations Studio (Vorschau)](#TitleNum_1)
2. [Anmerkungen zur Version von SQL Operations Studio (Vorschau)](#TitleNum_2)
3. [Tutorial: Hinzufügen der *fünf langsamsten Abfragen* Beispiel Widget aus, das die Datenbank-Dashboard](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-download-and-install-sql-operations-studio-previewdownloadmd"></a>1. &nbsp; [Herunterladen Sie und installieren Sie SQL Operations Studio (Vorschau)](download.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Weiter](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 6b4f80ad54c599e4354303a736f62e9715f99a32 18b22f464bbd8676348248ba5717b71acbab1c0d  (PR=5676  ,  Filename=download.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



   **Debian-Installation:**
```
   cd ~
   sudo dpkg -i ./Downloads/sqlops-linux-<version string>.deb

   sqlops
```

   **u/Min Installation:**
```
   cd ~
   yum install ./Downloads/sqlops-linux-<version string>.rpm

   sqlops
```

   **".TAR.gz" Installation:**



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-sql-operations-studio-preview-release-notesrelease-notesmd"></a>2. &nbsp; [Anmerkungen zur Version von SQL Operations Studio (Vorschau)](release-notes.md)

*Aktualisiert: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([vorherigen](#TitleNum_1) | [Weiter](#TitleNum_3))

<!-- Source markdown line 20.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 e2901d8a197f375f7d10ec93cbc9320362bf9278 0dde1aceceb339cb4cacd744e469f3d85d589668  (PR=5676  ,  Filename=release-notes.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**[April Public Preview herunterladen]**


**April 2018 (April-öffentliche Vorschau)**


Veröffentlichungsdatum: 25 April 2018-Version: 0.28.6

Die *Public Preview-Version April* enthält Fehlerbehebungen und Verbesserungen.

- Verbesserungen an der Vorschau von SQL-Agent-Erweiterung.
- Verbesserte dateiunterstützung für große und geschützte für das Speichern geschützter Administrator und > 256M-Dateien in SQL Operations Studio.
- Integriertes Terminal aufteilen, um mit mehreren open Terminals auf einmal zu arbeiten.
- Reduzierte Installation Datei auf dem Datenträger Anzahl Foot für schnellere Installationen und Startzeiten drucken.
- Weiter mit GitHub-Probleme zu beheben:
   - Beheben [ausgeben 37](https://github.com/Microsoft/sqlopsstudio/issues/37): bei der Diagramm-Viewer auf einen Fehler ausgibt, unerwartetes Verhalten auftritt.
   - Beheben Sie [ausgeben 462](https://github.com/Microsoft/sqlopsstudio/issues/462): Feature wünschen: Option für Server-Gruppen werden standardmäßig erweitert werden.
   - Beheben Sie [ausgeben 606](https://github.com/Microsoft/sqlopsstudio/issues/606): Intellisense - ungültige Vorschlag für Befehl 'update'.
   - Beheben Sie [ausgeben 967](https://github.com/Microsoft/sqlopsstudio/issues/967): erwarten, dass der Abfrageplan Wenn XML-Showplan im Ergebnisraster auswählen.
   - Beheben Sie [ausgeben 1023](https://github.com/Microsoft/sqlopsstudio/issues/1023): Hinzufügen von eckigen Klammern für Ms_foreachdb Aufruf aus Flyfishingdba.
   - Beheben Sie [ausgeben 1048](https://github.com/Microsoft/sqlopsstudio/issues/1048): vor der Anmeldung SSL/TLS-Handshake-Fehler.
   - Beheben Sie [ausgeben 1050](https://github.com/Microsoft/sqlopsstudio/issues/1050): klar Einblicke vor dem Fehler anzeigen.
   - Beheben Sie [1057 ausgeben](https://github.com/Microsoft/sqlopsstudio/issues/1057): Restore "und" neue Abfrageaktionen in der Explorer-Widget werden unterbrochen.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboardtutorial-qds-sql-servermd"></a>3. &nbsp; [Tutorial: Hinzufügen der *fünf langsamsten Abfragen* Beispiel Widget aus, das die Datenbank-Dashboard](tutorial-qds-sql-server.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Zurück](#TitleNum_2))

<!-- Source markdown line 94.  ms.author= "erickang".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 bc128acd966898cafc04381d7d83187d28466052 a47bf93ea4165618e0e514d7900ce1461f691aae  (PR=5676  ,  Filename=tutorial-qds-sql-server.md  ,  Dirpath=docs\sql-operations-studio\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



       },
       {
           "name": "Tasks",
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 1
           },
           "widget": {
               "tasks-widget": {}
           }
       },
       {
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 2
           },
           "widget": {
               "explorer-widget": {}
           }







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
- [Neue und aktualisierte (0 + 0): **Data Mining Extensions (DMX) für SQL** Docs](../dmx/new-updated-dmx.md)
- [New + Updated (0+0): **Master Data Services (MDS) for SQL** docs (Neu + Aktualisiert (0+0): Dokumentation zu Master Data Services (MDS) für SQL)](../master-data-services/new-updated-master-data-services.md)
- [Neue und aktualisierte (0 + 0): **MDX (Multidimensional Expressions) für SQL** Docs](../mdx/new-updated-mdx.md)
- [Neu und aktualisiert (0+0): Dokumente zu **ODBC (Open Database Connectivity) für SQL**](../odbc/new-updated-odbc.md)
- [Neu + Aktualisiert (0+0): **PowerShell für SQL-Dokumente**](../powershell/new-updated-powershell.md)
- [Neue und aktualisierte (0 + 0): **Samples for SQL** Docs](../samples/new-updated-samples.md)
- [Neu + Aktualisiert (0+0): Dokumente zu **SQL Server Migration Assistant (SSMA)**](../ssma/new-updated-ssma.md)
- [Neue und aktualisierte (0 + 0): **XQuery für SQL** Docs](../xquery/new-updated-xquery.md)

