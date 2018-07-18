---
title: Aktualisiert – SQL Server on Linux Docs | Microsoft Docs
description: Aktualisierter Inhalt in zuletzt geänderten Dokumentation für Microsoft SQL Server on Linux Codeausschnitte anzeigen
manager: craigg
author: MightyPen
ms.author: genemi
ms.topic: article
ms.custom: UpdArt.exe
ms.suite: sql
ms.technology: release-landing
ms.prod: sql
ms.date: 04/28/2018
ms.openlocfilehash: 3b7ed71be06ee7e485236fa0e244e47bb77b3b70
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334014"
---
# <a name="new-and-recently-updated-sql-server-on-linux-docs"></a>Neue und zuletzt aktualisiert: SQL Server on Linux Docs



Beinahe jeden Tag Microsoft updates einige vorhandene Artikel auf dessen [Docs.Microsoft.com](http://docs.microsoft.com/) Dokumentationswebsite. Dieser Artikel zeigt Auszüge aus den zuletzt aktualisierten Artikel. Links zu den neuen Artikel, möglicherweise ebenfalls aufgeführt.

In diesem Artikel wird von einem Programm generiert, die in regelmäßigen Abständen erneut ausgeführt wird. Gelegentlich kann ein Auszug aus dem Quellartikel mit sich Formatierung oder als Markdown angezeigt. Bilder werden hier nicht angezeigt.

Neueste Updates werden für folgenden Datumsbereich und Betreff gemeldet:



- *Datumsbereich des Updates:* &nbsp; **03.02.2018** &nbsp; bis &nbsp; **28.04.2018**
- *Bereich für die Themenbereichsdatenbank:* &nbsp; **Microsoft SQL Server on Linux**.




&nbsp;

## <a name="new-articles-created-recently"></a>Neue Artikel, die vor kurzem erstellt

Die folgenden Links leiten Sie zu den neuen Artikeln weiter, die erst kürzlich erstellt wurden.


1. [Active Directory-Authentifizierung für SQL Server on Linux](sql-server-linux-active-directory-auth-overview.md)
2. [Configure SQL Server AlwaysOn-Verfügbarkeitsgruppe unter Windows und Linux (Cross-Platform)](sql-server-linux-availability-group-cross-platform.md)
3. [Betreiben Sie Always On-Verfügbarkeitsgruppen unter Linux](sql-server-linux-availability-group-operate-ha.md)



&nbsp;

## <a name="updated-articles-with-excerpts"></a>Aktualisierte Artikel mit Auszüge

In diesem Abschnitt werden die Auszüge der Updates aus den Artikeln dargestellt, die vor Kurzem umfassend aktualisiert wurden.

Die hier angezeigten Auszüge werden getrennt vom richtigen semantische kontextabhängig angezeigt. Darüber hinaus wird manchmal ein Auszug vom wichtige Markdown-Syntax getrennt, die sie in den tatsächlichen Artikel umgibt. Aus diesem Grund sind diese Auszüge nur allgemeine Anleitungen. Die Auszüge können nur Sie wissen, ob Ihre Interessen dauert rechtfertigen, klicken Sie auf, und besuchen den tatsächlichen Artikel.

Kopieren Sie für diese und andere Gründe Code nicht von diesen verwendet, und nehmen Sie nicht als genaue Wahrheit alle Textauszug. Besuchen Sie stattdessen den tatsächlichen Artikel aus.





&nbsp;

<a name="compactupdatedlist"/>

### <a name="compact-list-of-articles-updated-recently"></a>Compact Liste von Artikeln, die vor kurzem aktualisiert

Diese kompakte Liste enthält Links zu den aktualisierten Artikeln, die im Abschnitt Auszüge aufgeführt sind.

1. [Konfigurieren des Repositorys für die Installation und Upgrade von SQL Server on Linux](#TitleNum_1)
2. [Konfigurieren von SQL Server unter Linux mit dem Mssql-Conf-tool](#TitleNum_2)
3. [Versionshinweise für SQL Server-2017 unter Linux](#TitleNum_3)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### <a name="1-nbsp-configure-repositories-for-installing-and-upgrading-sql-server-on-linuxsql-server-linux-change-repomd"></a>1. &nbsp; [Konfigurieren des Repositorys für die Installation und Upgrade von SQL Server on Linux](sql-server-linux-change-repo.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Weiter](#TitleNum_2))

<!-- Source markdown line 72.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 b5ccaa0fcb8895f25c162e4e0494ad4872773de3 29a959be6ee7d58fe0c53e8f91bdd282fb2e6d29  (PR=5676  ,  Filename=sql-server-linux-change-repo.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- Druckt den Inhalt der Datei.

```
   sudo cat /etc/yum.repos.d/mssql-server.repo
```

- Die **Namen** Eigenschaft ist für die konfigurierten Repository. Sie können mit der Tabelle im Abschnitt [Repositorys] identifiziert werden.

**Entfernen Sie alte Repository (RHEL)**

Entfernen Sie ggf. das alte Repository mit dem folgenden Befehl.

```
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

Mit diesem Befehl wird davon ausgegangen, dass die Datei identifiziert, die im vorherigen Abschnitt benannt wurde **Mssql-server.repo**.

**Konfigurieren Sie neue Repository (RHEL)**

Konfigurieren Sie das neue Repository für SQL Server-Installationen und Upgrades verwenden. Verwenden Sie einen der folgenden Befehle aus, um das Repository Ihrer Wahl zu konfigurieren.

| Repository | Befehl |
|---|---|
| **CU** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

**<a id="sles"></a> SLES Repositorys konfigurieren**

Verwenden Sie die folgenden Schritte aus, um auf SLES Repositorys konfigurieren.

**Überprüfen Sie zuvor konfigurierten Repositorys (SLES)**

Überprüfen Sie zunächst, ob Sie bereits ein SQL Server-Repository registriert haben.

- Verwendung **Zypper Info** um Informationen über alle zuvor konfigurierten Repository abzurufen.

```
   sudo zypper info mssql-server
```

- Die **Repository** Eigenschaft ist für die konfigurierten Repository. Sie können mit der Tabelle im Abschnitt [Repositorys] identifiziert werden.

**Entfernen Sie alte Repository (SLES)**

Entfernen Sie ggf. das alte Repository. Verwenden Sie die folgenden Befehle, die basierend auf den zuvor konfigurierten Repository-Typ.

| Repository | Befehl zum Entfernen |
|---|---|
| **Vorschau** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### <a name="2-nbsp-configure-sql-server-on-linux-with-the-mssql-conf-toolsql-server-linux-configure-mssql-confmd"></a>2. &nbsp; [Konfigurieren von SQL Server unter Linux mit dem Mssql-Conf-tool](sql-server-linux-configure-mssql-conf.md)

*Aktualisiert: 2018-04-25* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([vorherigen](#TitleNum_1) | [Weiter](#TitleNum_3))

<!-- Source markdown line 151.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 3664c4d64ea4840dcbc718461ed04403cc486f30 89f708af45ce262057e967e9047f1328e19248ba  (PR=5676  ,  Filename=sql-server-linux-configure-mssql-conf.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->




**<a id="masterdatabasedir"></a> Ändern Sie das Standard-master-Datenbank-Dateiverzeichnis**


Die **filelocation.masterdatafile** und **filelocation.masterlogfile** Einstellung ändert sich den Speicherort, in dem die SQL Server-Datenbankmodul, für die master-Datenbank-Dateien sucht. Dieser Speicherort ist standardmäßig /var/opt/mssql/data.

Um diese Einstellungen zu ändern, verwenden Sie die folgenden Schritte aus:

- Erstellen Sie das Zielverzeichnis für neue Fehlerprotokolldateien. Das folgende Beispiel erstellt ein neues **/Tmp/Masterdatabasedir** Verzeichnis:

```
   sudo mkdir /tmp/masterdatabasedir
```

- Ändern Sie den Besitzer und die Gruppe des Verzeichnisses, das die **Mssql** Benutzer:

```
   sudo chown mssql /tmp/masterdatabasedir
   sudo chgrp mssql /tmp/masterdatabasedir
```

- Verwenden der Mssql-Conf so ändern Sie das Standardverzeichnis für die master-Datenbank für die master Daten und Protokolldateien mit den **festgelegt** Befehl:

```
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterdatafile /tmp/masterdatabasedir/master.mdf
   sudo /opt/mssql/bin/mssql-conf set filelocation.masterlogfile /tmp/masterdatabasedir/mastlog.ldf
```

- Beenden Sie den SQL Server-Dienst:

```
   sudo systemctl stop mssql-server
```

- Verschieben Sie die Dateien master.mdf und masterlog.ldf:

```
   sudo mv /var/opt/mssql/data/master.mdf /tmp/masterdatabasedir/master.mdf
   sudo mv /var/opt/mssql/data/mastlog.ldf /tmp/masterdatabasedir/mastlog.ldf
```

- Starten Sie den SQL Server-Dienst:

```
   sudo systemctl start mssql-server
```

> [!NOTE]
> Wenn SQL Server im angegebenen Verzeichnis die Dateien master.mdf und mastlog.ldf finden kann, eine Kopie vorlagenbasierte Systemdatenbanken werden automatisch im angegebenen Verzeichnis erstellt, und SQL Server wird erfolgreich gestartet. Metadaten wie etwa von Benutzerdatenbanken, Server-Anmeldungen, Serverzertifikate, Verschlüsselungsschlüssel, SQL Agent-Aufträge oder Kennwort für SA-Anmeldung wird jedoch nicht in die neue master-Datenbank aktualisiert werden. Sie müssen zum Beenden von SQL Server und verschieben Ihre alte Dateien master.mdf und mastlog.ldf an den neuen angegebenen Speicherort aus, und starten Sie SQL Server, um den Vorgang fortzusetzen, verwenden die vorhandene Metadaten.



&nbsp;

&nbsp;

---

<a name="TitleNum_3"/>

### <a name="3-nbsp-release-notes-for-sql-server-2017-on-linuxsql-server-linux-release-notesmd"></a>3. &nbsp; [Versionshinweise für SQL Server-2017 unter Linux](sql-server-linux-release-notes.md)

*Aktualisiert: 25.04.2018* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ([Zurück](#TitleNum_2))

<!-- Source markdown line 64.  ms.author= jroth.  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 367d112a9427bbdd18e0e52cc82264dd169c91ae 63a67be08fa39ece778cf9ca0b9746dd28694574  (PR=5676  ,  Filename=sql-server-linux-release-notes.md  ,  Dirpath=docs\linux\  ,  MergeCommitSha40=a85a46312acf8b5a59a8a900310cf088369c4150) -->



- [Aktivieren Sie SQL Server-Agent]

**<a id="CU6"></a> CU6 (April 2018)**


Dies ist der kumulativen Update 6 (CU6)-Version von SQL Server-2017. Die Version des SQL Server-Datenbankmodul für diese Version ist 14.0.3025.34. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

**Details zum Paket**


Für Paketinstallationen der manuellen oder offline-können Sie die RPM und Debian Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3025.34-3 | [Datenbankmodul-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Volltext-Suche RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) |
| SLES RPM-Paket | 14.0.3025.34-3 | [MSSQL-Server-Datenbankmodul-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Volltext-Suche RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) |
| Ubuntu 16.04 Debian-Paket | 14.0.3025.34-3 | [Modul Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Volltext-Suche Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |







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

