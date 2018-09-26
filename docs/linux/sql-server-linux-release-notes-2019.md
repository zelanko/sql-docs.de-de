---
title: Versionsanmerkungen zu SQL Server-2019-Vorschauversion unter Linux | Microsoft-Dokumentation
description: Dieser Artikel enthält die Versionshinweise und unterstützte Funktionen für 2019 CTP für SQL Server unter Linux ausgeführt wird. Anmerkungen zu dieser Version sind für die neueste Version und früheren Versionen enthalten.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 54b955609941e1c4f5921486fc5c67716120a499
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049418"
---
# <a name="release-notes-for-sql-server-2019-preview-on-linux"></a>Versionshinweise für SQL Server-2019-Vorschauversion unter Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Die folgenden Versionshinweise gelten für 2019 CTP für SQL Server unter Linux ausgeführt wird. In diesem Artikel wird für jede Version in Abschnitte unterteilt. Jede Version verfügt über einen Link zu einer Support-Artikel beschreiben die CU Änderungen sowie Links zu den Paketdownloads Linux.

> [!TIP]
> Weitere Informationen zu neuen Linux-Funktionen in SQL Server-2019 finden Sie unter [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sqllinux).

## <a name="supported-platforms"></a>Unterstützte Plattformen

| Platform | Dateisystem | Installationshandbuch |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 oder 7.4 Workstation, Server und Desktop | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-ubuntu.md) | 
| Docker-Engine 1.8 und höher unter Windows, Mac oder Linux | – | [Installationshandbuch](quickstart-install-connect-docker.md) | 

> [!TIP]
> Weitere Informationen finden Sie in der [Systemanforderungen](sql-server-linux-setup.md#system) für SQL Server unter Linux. Die neuesten Supportrichtlinie für SQL Server 2017 finden Sie unter den [technischer Support-Richtlinie für Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Tools

Die meisten vorhandenen Clienttools für SQL Server können nahtlos abzielen, SQL Server unter Linux ausgeführt wird. Einige Tools möglicherweise eine bestimmte versionsanforderung funktioniert gut mit Linux. Eine vollständige Liste der SQL Server-Tools finden Sie unter [SQL Tools und Hilfsprogramme für SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Revisionsverlauf

Die folgende Tabelle enthält die Versionsgeschichte für CTPs für SQL Server 2019.

| Release               | Version       | Veröffentlichungsdatum |
|-----------------------|---------------|--------------|
| [CTP 2.0](#CTP20) | 15.0.1000.34   | 2018-09-24   |

## <a id="cuinstall"></a> Installieren von updates

Wenn Sie die Vorschau-Repository konfiguriert haben (**Mssql-Server-Preview**), und klicken Sie dann die aktuelle CTP-Version von SQL Server-Pakete erhalten Sie, wenn Sie neue Installationen ausführen. Wenn Sie Docker-Container-Images benötigen, finden Sie offizielle-Images für [Microsoft SQL Server unter Linux für Docker-Engine](https://hub.docker.com/r/microsoft/mssql-server/). Weitere Informationen zur Konfiguration des buildrepositorys finden Sie unter [Repositorys für SQL Server unter Linux konfigurieren](sql-server-linux-change-repo.md).

Wenn Sie vorhandene SQL Server-Pakete aktualisieren, führen Sie den entsprechende Update-Befehl für jedes Paket, um die neueste CU zu erhalten. Bestimmte updateanweisungen für jedes Paket finden Sie unter den folgenden Handbüchern zur Installation:

- [Installieren Sie SQL Server-Paket](sql-server-linux-setup.md#upgrade)
- [Installationspaket für die Volltextsuche](sql-server-linux-setup-full-text-search.md)
- [Install SQL Server Integration Services (Installieren von SQL Server Integration Services)](sql-server-linux-setup-ssis.md)
- [Installieren von SQL Server-2019 Vorschau Machine Learning-Dienste-R und Python-Unterstützung unter Linux](sql-server-linux-setup-machine-learning.md)
- [SQL Server-Agent aktivieren](sql-server-linux-setup-sql-agent.md)

## <a id="CTP20"></a> CTP-Version 2.0 (September 2018)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme für die CTP-Version 2.0-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1000.34-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1000.34-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1000.34-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Einstieg finden Sie in der folgenden Schnellstarts:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installieren unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-ubuntu.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [Ausführen und Verbinden – Cloud](quickstart-install-connect-clouds.md)

Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).