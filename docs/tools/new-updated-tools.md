---
title: 'Aktualisiert: Dokumentation zu Tools für SQL Server | Microsoft-Dokumentation'
description: Sie können sich Codeausschnitte der kürzlich aktualisierten Inhalte in der Dokumentation zu Tools für Microsoft SQL Server anzeigen lassen.
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: conceptual
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 31df25173ad475c733bc7239366a6c2ce820289e
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088182"
---
# <a name="new-and-recently-updated-tools-for-sql-server"></a>Neu und kürzlich aktualisiert: Verwaltungstools für SQLServer



Beinahe jeden Tag aktualisiert Microsoft einige der vorhandenen Artikel auf der Dokumentationswebsite [Docs.Microsoft.com](http://docs.microsoft.com/). In diesem Artikel werden Auszüge aus den zuletzt aktualisierten Artikeln wiedergegeben. Links zu den neuen Artikel werden ggf. ebenfalls aufgeführt.

Dieser Artikel wurde im Rahmen eines Programms erstellt, das in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug mit falscher Formatierung oder als Markdown aus dem Quellartikel angezeigt werden. Bilder werden hier nie wiedergegeben.

Neueste Updates werden für den folgenden Datumsbereich und Themenbereich gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Themenbereich:* &nbsp; **-Tools für SQL Server**.




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt wurden

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


- [MSSQL-Cli-Befehlszeilenabfragetool für SQL Server](mssql-cli.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszügen

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die Auszüge hier werden getrennt vom richtigen semantischen Kontext angezeigt. Darüber hinaus wird ein Auszug manchmal getrennt von der wichtigen Markdownsyntax wiedergegeben, die ihn im ursprünglichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Anhand dieser Auszüge sollen Sie nur entscheiden können, ob Sie sich die Zeit nehmen und den eigentlichen Artikel besuchen möchten.

Kopieren Sie aus diesem und anderen Gründen auf gar keinen Fall Code aus diesen Auszügen, und gehen Sie bei keinem Textauszug von einer 100-prozentigen Richtigkeit der Informationen aus. Besuchen Sie stattdessen den eigentlichen Artikel.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Kompakte Liste der Artikel, die vor Kurzem aktualisiert wurden

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

- [bcp Utility](#TitleNum_1)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-bcp-utilitybcp-utilitymd"></a>1. &nbsp; [Hilfsprogramm bcp](bcp-utility.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 

<!-- Source markdown line 189.  ms.author= "sstein".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 c85e6c6ff13ad20f432ead67febfc48c784f3f9a 27de3822192fc64f0d99b4dbc21f05a3e4def186  (PR=5676  ,  Filename=bcp-utility.md  ,  Dirpath=docs\tools\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



**-G**<a name="G"></a>: Diese Option wird vom Client beim Herstellen einer Verbindung mit Azure SQL-Datenbank oder Azure SQL Data Warehouse verwendet, um anzugeben, dass der Benutzer mithilfe der Azure Active Directory-Authentifizierung authentifiziert werden soll. Der Schalter-G erfordert [Version 14.0.3008.27 oder höher](http://go.microsoft.com/fwlink/?LinkID=825643). Führen Sie „bcp -v“ aus, um die von Ihnen verwendete Version zu ermitteln. Weitere Informationen finden Sie unter [verwenden Azure Active Directory-Authentifizierung für die Authentifizierung mit SQL-Datenbank oder SQL Data Warehouse](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).

> [!TIP]
>  Zum Überprüfen, ob Ihre Version des Bcp-Unterstützung für Azure Active Directory-Authentifizierung (AAD)-Typ enthält **Bcp--** (Bcp\<Speicherplatz >\<Dash >\<Dash >) und stellen Sie sicher, dass: Password-g in der Liste angezeigt Verfügbare Argumente.

- **Azure Active Directory-Benutzername und -Kennwort:**

    Wenn Sie einen Azure Active Directory-Benutzernamen und das zugehörige Kennwort verwenden möchten, geben Sie die Option **-G** zusammen mit dem Benutzernamen und dem Kennwort an, indem Sie die Optionen **-U** und **-P** bereitstellen.

    Das folgende Beispiel exportiert die Daten mithilfe von Azure AD-Benutzername und Kennwort, in denen Benutzer und das Kennwort ist eine AAD-Anmeldeinformationen. Im Beispiel wird die Tabelle exportiert `bcptest` aus Datenbank `testdb` aus Azure-Server `aadserver.database.windows.net` und speichert die Daten in der Datei `c:\last\data1.dat`:
```
    bcp bcptest out "c:\last\data1.dat" -c -t -S aadserver.database.windows.net -d testdb -G -U alice@aadtest.onmicrosoft.com -P xxxxx
```

    The following example imports data using Azure AD Username and Password where user and password is an AAD credential. The example imports data from file `c:\last\data1.dat` into table `bcptest` for database `testdb` on Azure server `aadserver.database.windows.net` using Azure AD User/Password:
```
    bcp bcptest in "c:\last\data1.dat" -c -t -S aadserver.database.windows.net -d testdb -G -U alice@aadtest.onmicrosoft.com -P xxxxx
```



- **Integrierte Azure Active Directory-Authentifizierung**

    Wenn Sie die integrierte Azure Active Directory-Authentifizierung verwenden möchten, geben Sie die Option **-G** ohne Benutzername und Kennwort an. Diese Konfiguration wird davon ausgegangen, dass das aktuelle Windows-Benutzerkonto (das Konto, unter der Bcp-Befehl ausgeführt wird) in Azure AD verbunden ist:







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

