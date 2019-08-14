---
title: Neuigkeiten zu SQL Server 2017 für Linux
description: In diesem Artikel sind die Neuigkeiten für SQL Server 2017 für Linux zusammengestellt.
author: VanMSFT
ms.author: vanto
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: 3f3f51716acf69368ae2554446c47d125b500e03
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032159"
---
# <a name="whats-new-for-sql-server-on-linux"></a>Neuigkeiten zu SQL Server für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel sind die wichtigsten Features und Dienste beschrieben, die für SQL Server 2017 für Linux verfügbar sind.

SQL Server 2019 (Vorschauversion) wurde freigegeben. In diesem Artikel geht es nicht um SQL Server 2019 (Vorschauversion). Wenn Sie mehr zu SQL Server 2019 (Vorschauversion) erfahren möchten, lesen Sie [Neuigkeiten zu SQL Server 2019 (Vorschauversion): SQL Server für Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

> [!NOTE]
> Zusätzlich zu diesen Funktionen in diesem Artikel werden kumulative Updates in regelmäßigen Abständen nach dem allgemein verfügbaren Release veröffentlicht. Diese kumulativen Updates enthalten viele Verbesserungen und Fehlerbehebungen. Informationen zu den neuesten kumulativen Updates finden Sie unter [https://aka.ms/sql2017cu](https://aka.ms/sql2017cu). Informationen über Paketdownloads und bekannte Probleme finden Sie unter [Versionshinweise](sql-server-linux-release-notes.md).

## <a name="sql-server-database-engine"></a>SQL Server-Datenbank-Engine

- Bereitstellen der Kernfunktionalität der SQL Server-Datenbank-Engine
- Unterstützung für native Linux-Pfade
- IPv6-Unterstützung
- Unterstützung für Datenbankdateien in NFS
- Aktivierte [Transport Layer Security](sql-server-linux-encrypted-connections.md)-Verschlüsselung (TLS)
- Aktivierte [Active Directory-Authentifizierung](sql-server-linux-active-directory-authentication.md)
- [Verfügbarkeitsgruppenfunktionalität](sql-server-linux-availability-group-overview.md) für hohe Verfügbarkeit
- Unterstützung für [Volltextsuche](sql-server-linux-setup-full-text-search.md)

## <a name="sql-server-agent"></a>SQL Server-Agent

- Aktivierte [SQL Server-Agent](sql-server-linux-setup-sql-agent.md)-Unterstützung für die folgenden Aufgaben:
  - [Transact-SQL-Aufträge](sql-server-linux-run-sql-server-agent-job.md)
  - [DB Mail](sql-server-linux-db-mail-sql-agent.md)
  - [Protokollversand](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Die Möglichkeit, SSIS-Pakete unter Linux auszuführen. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server Integration Services unter Linux mit ssis-conf](sql-server-linux-configure-ssis.md).

## <a name="other-improvements"></a>Sonstige Verbesserungen

- Befehlszeilen-Konfigurationstool [mssql-conf](sql-server-linux-configure-mssql-conf.md).
- Unterstützung für unbeaufsichtigte Installation mit [Umgebungsvariablen](sql-server-linux-configure-environment-variables.md).
- Plattformübergreifende [Visual Studio Code-Erweiterung mssql-server](sql-server-linux-develop-use-vscode.md).
- Plattformübergreifender Skript-Generator [mssql-scripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md).
- Plattformübergreifender Monitor für dynamische Verwaltungssicht (Dynamic Management View, DMV), [DBFS-Tool](https://github.com/Microsoft/dbfs).

## <a name="next-steps"></a>Nächste Schritte

Um SQL Server für Linux zu installieren, gehen Sie gemäß einem der folgenden Tutorials vor:

- [Installieren unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installation unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Ausführen unter Docker](quickstart-install-connect-docker.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Weitere Verbesserungen, die in SQL Server 2017 eingeführt wurden, finden Sie unter [Neues in SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

> [!TIP]
> Antworten auf häufig gestellte Fragen finden Sie unter [Häufig gestellte Fragen zu SQL Server für Linux](sql-server-linux-faq.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
