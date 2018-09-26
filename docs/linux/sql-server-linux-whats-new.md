---
title: Neues in SQLServer 2017 unter Linux | Microsoft-Dokumentation
description: In diesem Artikel werden die Neuigkeiten für SQL Server 2017 unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.openlocfilehash: 6ccb65aad24ca84f95bb1022c7f074450823e2e9
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049440"
---
# <a name="whats-new-for-sql-server-on-linux"></a>Was ist neu in SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt die wichtigsten Funktionen und-Dienste verfügbar für SQL Server 2017 unter Linux ausgeführt wird.

Vorschau der SQL Server-2019 wurde veröffentlicht. Dieser Artikel deckt nicht die Preview-Versionen von SQL Server-2019. Weitere Informationen zu SQL Server-2019 Preview finden Sie unter [Neuigkeiten in SQL Server-2019 Vorschauphase für Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux).

> [!NOTE]
> Abgesehen von diesen Funktionen in diesem Artikel werden die kumulativen Updates in regelmäßigen Abständen nach dem Allgemein verfügbaren Release veröffentlicht. Diese kumulativen Updates enthalten viele Verbesserungen und Fehlerbehebungen. Weitere Informationen über die neueste CU-Version finden Sie unter [ http://aka.ms/sql2017cu ](http://aka.ms/sql2017cu). Paketdownloads und bekannte Probleme finden Sie in der [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md).

## <a name="sql-server-database-engine"></a>SQL Server-Datenbank-Engine

- Aktiviert die Kernfunktionen von SQL Server-Datenbank-Engine.
- Unterstützung für native Linux-Pfade.
- IPv6-Unterstützung.
- Unterstützung für die Datenbankdateien auf NFS.
- Aktiviert [Transparent Layer Security](sql-server-linux-encrypted-connections.md) (TLS)-Verschlüsselung.
- Aktiviert [Active Directory-Authentifizierung](sql-server-linux-active-directory-authentication.md).
- [Gruppen-Funktionen für Verfügbarkeit](sql-server-linux-availability-group-overview.md) für hohe Verfügbarkeit.
- [Volltext-Suchdienst](sql-server-linux-setup-full-text-search.md) unterstützen.

## <a name="sql-server-agent"></a>SQL Server-Agent

- Aktiviert [SQL Server-Agent](sql-server-linux-setup-sql-agent.md) Unterstützung für die folgenden Aufgaben:
  - [Transact-SQL-Aufträge](sql-server-linux-run-sql-server-agent-job.md)
  - [Datenbank-e-Mails](sql-server-linux-db-mail-sql-agent.md)
  - [Protokollversand](sql-server-linux-use-log-shipping.md)

## <a name="sql-server-integration-services-ssis"></a>SQL Server Integration Services (SSIS)

- Fähigkeit zum Ausführen von SSIS-Pakete für Linux. Weitere Informationen finden Sie unter [Konfigurieren von SQL Server Integration Services unter Linux mit Ssis-Conf](sql-server-linux-configure-ssis.md).

## <a name="other-improvements"></a>Weitere Verbesserungen

- Befehlszeilen-Konfigurationstool [Mssql-Conf](sql-server-linux-configure-mssql-conf.md).
- Unterstützung der unbeaufsichtigten Installation mit [Umgebungsvariablen](sql-server-linux-configure-environment-variables.md).
- Plattformübergreifende [Mssql-Server-Erweiterung für Visual Studio Code](sql-server-linux-develop-use-vscode.md).
- Cross-Platform-Skript-Generator, [Mssql-Skripter](https://github.com/Microsoft/sql-xplat-cli/blob/dev/doc/usage_guide.md).
- Plattformübergreifende dynamische Ansicht (DMV) überwachen, [FileSystem, DBFS Tool](https://github.com/Microsoft/dbfs).

## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie zum Installieren von SQL Server unter Linux die folgenden Tutorials:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installieren unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-docker.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

Weitere Verbesserungen in SQL Server 2017 eingeführt wurden, finden Sie unter [Neuigkeiten in SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).

> [!TIP]
> Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
