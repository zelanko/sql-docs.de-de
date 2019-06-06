---
title: Installieren von SQL Server-Volltextsuche unter Linux | Microsoft-Dokumentation
description: In diesem Artikel wird beschrieben, wie die SQL Server-Volltextsuche unter Linux installiert wird.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: bb42076f-e823-4cee-9281-cd3f83ae42f5
ms.openlocfilehash: 40b2e50932994644ce5e49237adbef08b825b513
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705047"
---
# <a name="install-sql-server-full-text-search-on-linux"></a>Installieren von SQL Server-Volltextsuche unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Installieren Sie die folgenden Schritte aus [SQL Server-Volltextsuche](../relational-databases/search/full-text-search.md) (**Mssql-Server-Volltextsuche**) unter Linux. Volltextsuche können Sie sämtliche Volltextabfragen für zeichenbasierte Daten in SQL Server-Tabellen ausgeführt werden. Bekannte Probleme in dieser Version finden Sie unter den [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md).

> [!NOTE]
> Vor der Installation von SQL Server-Volltext-Suchdienst, zuerst [Installieren von SQL Server](sql-server-linux-setup.md#platforms). Dadurch wird konfiguriert, die Schlüssel und Repositorys, mit denen Sie bei der Installation der **Mssql-Server-Volltextsuche** Paket.

Installieren Sie SQL Server-Volltextsuche für Ihre Plattform:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">Installation unter RHEL</a>

Verwenden Sie die folgenden Befehle zum Installieren der **Mssql-Server-Volltextsuche** unter Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-fts
```

Wenn Sie bereits verfügen **Mssql-Server-Volltextsuche** installiert haben, können Sie auf die neueste Version mit den folgenden Befehlen aktualisieren:

```bash
sudo yum check-update
sudo yum update mssql-server-fts
```

Eine offline-Installation, suchen Sie nach der Paketdownload "Volltextsuche" in der [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md). Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

## <a name="ubuntu">Installation unter Ubuntu</a>

Verwenden Sie die folgenden Befehle zum Installieren der **Mssql-Server-Volltextsuche** unter Ubuntu. 

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts
```

Wenn Sie bereits verfügen **Mssql-Server-Volltextsuche** installiert haben, können Sie auf die neueste Version mit den folgenden Befehlen aktualisieren:

```bash
sudo apt-get update 
sudo apt-get install -y mssql-server-fts 
```

Eine offline-Installation, suchen Sie nach der Paketdownload "Volltextsuche" in der [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md). Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

## <a name="SLES">Installation unter SLES</a>

Verwenden Sie die folgenden Befehle zum Installieren der **Mssql-Server-Volltextsuche** unter SUSE Linux Enterprise Server. 

```bash
sudo zypper install mssql-server-fts
```

Wenn Sie bereits verfügen **Mssql-Server-Volltextsuche** installiert haben, können Sie auf die neueste Version mit den folgenden Befehlen aktualisieren:

```bash
sudo zypper refresh
sudo zypper update mssql-server-fts
```

Eine offline-Installation, suchen Sie nach der Paketdownload "Volltextsuche" in der [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md). Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

## <a name="supported-languages"></a>Unterstützte Sprachen

Volltext-Suchdienst verwendet [wörtertrennungen](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) feststellen, dass einzelne Wörter, die abhängig von Sprache zu identifizieren. Sie erhalten eine Liste der registrierten wörtertrennungen durch Abfragen der **Sys. fulltext_languages** -Katalogsicht angezeigt. Wörtertrennungen für den folgenden Sprachen, die mit SQL Server installiert sind:

| Sprache | Sprach-ID |
|---|---|
| Neutral | 0 |
| Arabisch | 1025 |
| Bangla (Indien) | 1093 |
| Bokmål | 1044 |
| Brasilianisch | 1046 |
| Englisch (britisch) | 2057 |
| Bulgarisch | 1026 |
| Katalanisch | 1027 |
| Chinesisch (Hongkong SAR, VR China) | 3076 |
| Chinesisch (Macao SAR) | 5124 |
| Chinesisch (Singapur) | 4100 |
| Kroatisch | 1050 |
| Tschechisch | 1029 |
| Dänisch | 1030 |
| Niederländisch | 1043 |
| Englisch | 1033 |
| Französisch | 1036 |
| Deutsch | 1031 |
| Griechisch | 1032 |
| Gujarati | 1095 |
| Hebräisch | 1037 |
| Hindi | 1081 |
| Isländisch | 1039 |
| Indonesisch | 1057 |
| Italienisch | 1040 |
| Japanisch | 1041 |
| Kannada | 1099 |
| Koreanisch | 1042 |
| Lettisch | 1062 |
| Litauisch | 1063 |
| Malaiisch (Malaysia) | 1086 |
| Malayalam | 1100 |
| Marathi | 1102 |
| Polnisch | 1045 |
| Portugiesisch | 2070 |
| Punjabi | 1094 |
| Rumänisch | 1048 |
| Russisch | 1049 |
| Serbisch (Kyrillisch) | 3098 |
| Serbisch (Lateinisch) | 2074 |
| Chinesisch (vereinfacht) | 2052 |
| Slowakisch | 1051 |
| Slowenisch | 1060 |
| Spanisch | 3082 |
| Schwedisch | 1053 |
| Tamil | 1097 |
| Telugu | 1098 |
| Thai | 1054 |
| Chinesisch (traditionell) | 1028 |
| Türkisch | 1055 |
| Ukrainisch | 1058 |
| Urdu | 1056 |
| Vietnamesisch | 1066 |

## <a id="filters"></a> Filter

Volltextsuche funktioniert auch mit dem Text in binäre Dateien gespeichert. Aber in diesem Fall ein installierter Filter zum Verarbeiten der Datei erforderlich ist. Weitere Informationen zu filtern, finden Sie unter [konfigurieren und Verwalten von Filtern für die Suche](../relational-databases/search/configure-and-manage-filters-for-search.md).

Sie sehen eine Liste der installierten Filter durch den Aufruf **Sp_help_fulltext_system_components 'Filter'** . Für SQL Server werden die folgenden Filter installiert:

| Komponentenname | Klassen-ID | Version |
|---|---|---|
|a | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ans | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ASC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|ASCX | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|ASM | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|ASP | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|aspx | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.asx | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.bas | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|BAT | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|bcp | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.c | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|CLS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|cmd | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.cpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|cs | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.csa | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|CSS | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.csv | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.cxx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.DBS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.def | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|".dic" | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.dos | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|DSP | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.dsw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|ext | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.FAQ | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.fky | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.h | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.hhc | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hpp | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.hta | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.HTML | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htt | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.htw | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|HTX | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.hxx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.i | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.ibq | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|ICS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|IDL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.idq | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.Inc | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.ini | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.inl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.INX | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|".jav" | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|Java | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.js | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.kci | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.lgN | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.log | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|lst | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.m3u | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|MAK | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.mk | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|ODC | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.odh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|ODL | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgdef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.pkgundef | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|PL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.PRC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|RC | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rc2 | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|RCT | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.reg | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|RGS | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.rtf | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.rul | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.s | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.SCC | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.shtm | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|sHTML | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|Snippet | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.SOL | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.Sor | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.srf | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|STM | E0CA5340-4534-11CF-B952-00AA0051FE20 | 12.0.6828.0 |
|.TAB | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tdl | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tlh | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.tli | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.trg | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|TXT | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.udf | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.UDT | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|auch URL | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.usr | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vbs | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.viw | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsct | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsixlangpack | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|vsixmanifest | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vspscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vsscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.vssscc | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wri | C1243CA0-BF96-11CD-B579-08002B30BFEB | 12.0.6828.0 |
|.wtx | C7310720-AC80-11D1-8DF3-00C04FB6EF4F | 12.0.6828.0 |
|.xml | 41B9BE05-B3AF-460C-BF0B-2CDD44A093B1 | 12.0.9735.0 |

## <a name="semantic-search"></a>Semantische Suche
[Semantische Suche](../relational-databases/search/semantic-search-sql-server.md) baut auf die Volltext-Suchfunktion zu extrahieren und zu indizieren statistisch relevante *Schlüsselausdrücke*. Dadurch können Sie die Bedeutung innerhalb von Dokumenten in der Datenbank Abfragen. Außerdem können Dokumente zu identifizieren, die ähnlich sind.

Um der semantischen Suche zu verwenden, müssen Sie zuerst die Semantic Language Statistics-Datenbank auf Ihrem Computer wiederherstellen.

1. Verwenden Sie ein Tool wie z. B. [Sqlcmd](sql-server-linux-setup-tools.md), um den folgenden Transact-SQL-Befehl für Ihre virtuellen SQL Server-Instanz ausführen. Durch diesen Befehl wird die Language Statistics-Datenbank.

   ```sql
   RESTORE DATABASE [semanticsdb] FROM
   DISK = N'/opt/mssql/misc/semanticsdb.bak' WITH FILE = 1,
   MOVE N'semanticsdb' TO N'/var/opt/mssql/data/semanticsDB.mdf',
   MOVE N'semanticsdb_log' TO N'/var/opt/mssql/data/semanticsdb_log.ldf', NOUNLOAD, STATS = 5
   GO
   ```

   > [!NOTE]
   > Aktualisieren Sie bei Bedarf die Pfade in der vorherigen RESTORE-Befehl, um für Ihre Konfiguration anzupassen.

1. Führen Sie den folgenden Transact-SQL-Befehl, um die semantic Language Statistics-Datenbank zu registrieren.

    ```sql
    EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
    GO
    ```

## <a name="next-steps"></a>Nächste Schritte

Informationen zur Volltextsuche finden Sie unter [SQL Server-Volltextsuche](../relational-databases/search/full-text-search.md). 
