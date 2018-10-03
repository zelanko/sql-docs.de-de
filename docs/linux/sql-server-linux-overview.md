---
title: Übersicht über SQLServer unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie SQL Server unter Linux ausgeführt wird und erläutert, wie Sie mehr zu erfahren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: 8b8ee30d255382981a65a661ed0a080e39e4577a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47617108"
---
# <a name="sql-server-on-linux"></a>SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

::: moniker range="= sql-server-2017 || = sqlallproducts-allversions"
SQL Server ab SQL Server 2017 unter Linux ausgeführt werden. Es ist die gleiche SQL Server-Datenbankmodul, viele ähnliche Features und-Dienste unabhängig von Ihrem Betriebssystem.
::: moniker-end

::: moniker range=">= sql-server-ver15 || >= sql-server-linux-ver15"
SQL Server 2019 CTP 2.0 unter Linux ausgeführt wird. Es ist die gleiche SQL Server-Datenbankmodul, viele ähnliche Features und-Dienste unabhängig von Ihrem Betriebssystem. Weitere Informationen zu dieser Version finden Sie unter [Neuigkeiten in SQL Server 2019 CTP 2.0 für Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux).
::: moniker-end

::: moniker range="= sql-server-2017"
> [!TIP]
> [SQL Server 2019 CTP 2.0](sql-server-linux-overview.md?view=sql-server-ver15) wurde veröffentlicht! Um herauszufinden, was für Linux in der aktuellen Version neu ist, finden Sie unter [Neuigkeiten in SQL Server 2019 CTP 2.0 für Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux).
::: moniker-end

::: moniker range="= sql-server-linux-2017"
> [!TIP]
> [SQL Server 2019 CTP 2.0](sql-server-linux-overview.md?view=sql-server-linux-ver15) wurde veröffentlicht! Um herauszufinden, was für Linux in der aktuellen Version neu ist, finden Sie unter [Neuigkeiten in SQL Server 2019 CTP 2.0 für Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-linux-ver15#sqllinux).
::: moniker-end

::: moniker range="= sqlallproducts-allversions"
> [!TIP]
> SQL Server 2019 CTP 2.0 wurde veröffentlicht! Um herauszufinden, was für Linux in der aktuellen Version neu ist, finden Sie unter [Neuigkeiten in SQL Server 2019 CTP 2.0 für Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux).
::: moniker-end

## <a name="install"></a>Install

Installieren von SQL Server unter Linux mit einer der folgenden schnellstartanleitungen zum Einstieg:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installieren unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-docker.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker selbst wird ausgeführt auf mehreren Plattformen, was bedeutet, dass Sie das Docker-Image unter Linux, Mac und Windows ausführen können.

## <a name="connect"></a>Verbinden

Verbinden Sie nach der Installation mit SQL Server-Instanz auf Ihrem Linux-Computer. Sie können lokal oder Remote und mit einer Vielzahl von Tools und Treiber verbinden. Die Schnellstarts veranschaulichen, wie die [Sqlcmd](sql-server-linux-setup-tools.md) -Befehlszeilentool. Andere Tools umfassen Folgendes:

| Tool | Lernprogramm |
|-----|-----|
| Visual Studio-Code (VS Code) | [Verwenden von VS Code mit SQLServer unter Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Verwenden von SSMS unter Windows zur Verbindung mit SQL Server unter Linux](sql-server-linux-manage-ssms.md) |
| SQL Server Data Tools (SSDT) | [Verwenden von SSDT mit SQLServer unter Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Erkunden

<!--SQL Server 2017 on Linux-->
::: moniker range="= sql-server-linux-2017 || = sql-server-2017"

SQL Server 2017 hat die gleiche zugrunde liegende Datenbank-Engine auf allen unterstützten Plattformen, einschließlich Linux. Aus diesem Grund werden die zahlreichen vorhandenen Features und Funktionen die gleiche Weise unter Linux. Dieser Teil der Dokumentation stellt einige dieser Features vom Standpunkt der Linux. Es ruft auch Bereiche, die besonderen Anforderungen für Linux verfügen.

Wenn Sie bereits mit SQL Server vertraut sind, überprüfen Sie die [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md) allgemeine Richtlinien und bekannte Probleme in dieser Version. Sehen Sie sich [Neuigkeiten für SQL Server unter Linux](sql-server-linux-whats-new.md) sowie [Neuigkeiten für SQL Server 2017 insgesamt](../sql-server/what-s-new-in-sql-server-2017.md).

::: moniker-end
<!--SQL Server 2019 on Linux-->
::: moniker range=">= sql-server-linux-ver15 || >= sql-server-ver15"

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] verfügt über die gleiche zugrunde liegende Datenbank-Engine auf allen unterstützten Plattformen, einschließlich Linux aus. Aus diesem Grund werden die zahlreichen vorhandenen Features und Funktionen die gleiche Weise unter Linux. Dieser Teil der Dokumentation stellt einige dieser Features vom Standpunkt der Linux. Es ruft auch Bereiche, die besonderen Anforderungen für Linux verfügen.

Wenn Sie bereits mit SQL Server unter Linux vertraut sind, überprüfen Sie die [Anmerkungen zu dieser Version](sql-server-linux-release-notes-2019.md) allgemeine Richtlinien und bekannte Probleme in dieser Version. Sehen Sie sich [Neuigkeiten für SQL Server-2019-Vorschauversion unter Linux](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15).

::: moniker-end

<!--SQL Server All Versions-->
::: moniker range="=sqlallproducts-allversions"

SQL Server 2017 und [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] haben die gleiche zugrunde liegende Datenbank-Engine auf allen unterstützten Plattformen, einschließlich Linux. Aus diesem Grund werden die zahlreichen vorhandenen Features und Funktionen die gleiche Weise unter Linux. Dieser Teil der Dokumentation stellt einige dieser Features vom Standpunkt der Linux. Es ruft auch Bereiche, die besonderen Anforderungen für Linux verfügen.

Wenn Sie bereits mit SQL Server unter Linux vertraut sind, überprüfen Sie die Anmerkungen zu dieser Version:

- [SQL Server 2017 release notes (Versionsanmerkungen zu SQL Server 2017)](sql-server-linux-release-notes.md)
- [SQL Server-2019 Anmerkungen zur Vorschauversion](sql-server-linux-release-notes-2019.md)

Sehen Sie sich die neuerungen:

- [Was ist neu in SQL Server 2017](sql-server-linux-whats-new.md)
- [What's new for SQL Server-2019-Vorschauversion unter Linux](../sql-server/what-s-new-in-sql-server-ver15.md#sqllinux)

::: moniker-end

> [!TIP]
> Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
