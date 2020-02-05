---
title: Neuigkeiten zu SQL Server 2017 für Linux
description: In diesem Artikel sind die Neuigkeiten für SQL Server 2017 für Linux zusammengestellt.
author: VanMSFT
ms.author: vanto
ms.date: 10/23/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 6874c34c70b562ef726bda5abbda2aebe615cc08
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "72890543"
---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Neuigkeiten zu SQL Server 2017 für Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel sind die wichtigsten Features und Dienste beschrieben, die für SQL Server 2017 für Linux verfügbar sind.

> [!NOTE]
> Zusätzlich zu diesen Funktionen in diesem Artikel werden kumulative Updates in regelmäßigen Abständen veröffentlicht. Diese kumulativen Updates enthalten viele Verbesserungen und Fehlerbehebungen. Detaillierte Informationen zu den neuesten kumulativen Updates finden Sie unter [https://aka.ms/sql2017cu](https://aka.ms/sql2017cu). Informationen über Paketdownloads und bekannte Probleme finden Sie unter [Versionshinweise](sql-server-linux-release-notes.md).

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

- [Installation unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installation unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installation unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Ausführung in Docker](quickstart-install-connect-docker.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)

Antworten auf häufig gestellte Fragen finden Sie unter [Häufig gestellte Fragen zu SQL Server für Linux](sql-server-linux-faq.md). Weitere Verbesserungen, die in SQL Server 2017 eingeführt wurden, finden Sie unter [Neues in SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
