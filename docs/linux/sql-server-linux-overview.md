---
title: Übersicht über SQLServer unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie SQL Server unter Linux ausgeführt wird und erläutert, wie Sie mehr zu erfahren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 06/20/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.openlocfilehash: 16ea8b69f1d55e5b338931f0531bdf8a2e037707
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020138"
---
# <a name="sql-server-on-linux"></a>SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server 2017 wird jetzt unter Linux ausgeführt. Es ist die gleiche SQL Server-Datenbankmodul, viele ähnliche Features und-Dienste unabhängig von Ihrem Betriebssystem.

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

SQL Server 2017 hat die gleiche zugrunde liegende Datenbank-Engine auf allen unterstützten Plattformen, einschließlich Linux. Arbeiten so viele vorhandenen Features und Funktionen die gleiche Weise unter Linux. Dieser Teil der Dokumentation stellt einige dieser Features vom Standpunkt der Linux. Es ruft auch Bereiche, die besonderen Anforderungen für Linux verfügen.

Wenn Sie bereits mit SQL Server vertraut sind, überprüfen Sie die [Anmerkungen zu dieser Version](sql-server-linux-release-notes.md) allgemeine Richtlinien und bekannte Probleme in dieser Version. Sehen Sie sich [Neuigkeiten für SQL Server unter Linux](sql-server-linux-whats-new.md) sowie [Neuigkeiten für SQL Server 2017 insgesamt](../sql-server/what-s-new-in-sql-server-2017.md). 

> [!TIP]
> Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).

[!INCLUDE[Get Help Options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]