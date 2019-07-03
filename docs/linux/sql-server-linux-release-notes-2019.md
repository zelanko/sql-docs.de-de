---
title: Versionsanmerkungen zu SQL Server-2019-Vorschauversion unter Linux | Microsoft-Dokumentation
description: Dieser Artikel enthält die Anmerkungen zu dieser Version und die unterstützten Funktionen für SQL Server-2019 Vorschau unter Linux ausgeführt wird. Anmerkungen zu dieser Version sind für die neueste Version und früheren Versionen enthalten.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 07/02/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: f172cf3b4ab72fe413cbc639c3e880edef311e9e
ms.sourcegitcommit: eacc2d979f1f13cfa07e0aa4887eb9d48824b633
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67533845"
---
# <a name="release-notes-for-sql-server-2019-preview-on-linux"></a>Versionshinweise für SQL Server-2019-Vorschauversion unter Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Die folgenden Versionshinweise gelten für SQL Server-2019 Vorschau unter Linux ausgeführt wird. In diesem Artikel wird für jede Version in Abschnitte unterteilt. Jede Version verfügt über einen Link zu einer Support-Artikel beschreiben die CU Änderungen sowie Links zu den Paketdownloads Linux.

> [!TIP]
> Weitere Informationen zu neuen Linux-Funktionen in SQL Server-2019 finden Sie unter [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

## <a name="supported-platforms"></a>Unterstützte Plattformen

| Platform | Dateisystem | Installationshandbuch |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, 7.4, 7.5 oder 7.6 Server | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-ubuntu.md) | 
| Docker-Engine 1.8 und höher unter Windows, Mac oder Linux | Nicht zutreffend | [Installationshandbuch](quickstart-install-connect-docker.md) | 

> [!TIP]
> Weitere Informationen finden Sie in der [Systemanforderungen](sql-server-linux-setup.md#system) für SQL Server unter Linux. Die neuesten Supportrichtlinie für SQL Server 2017 finden Sie unter den [technischer Support-Richtlinie für Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Tools

Die meisten vorhandenen Clienttools für SQL Server können nahtlos abzielen, SQL Server unter Linux ausgeführt wird. Einige Tools möglicherweise eine bestimmte versionsanforderung funktioniert gut mit Linux. Eine vollständige Liste der SQL Server-Tools finden Sie unter [SQL Tools und Hilfsprogramme für SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Revisionsverlauf

Die folgende Tabelle enthält die Versionsgeschichte für SQL Server-2019-Vorschauversionen von der CTP-Versionen.

| Release               | Version       | Veröffentlichungsdatum |
|-----------------------|---------------|--------------|
| [CTP 3.1](#CTP31)     | 15.0.1700.37  | 2019-6-26    |
| [CTP 3.0](#CTP30)     | 15.0.1600.8   | 2019-5-22    |
| [CTP 2.5](#CTP25)     | 15.0.1500.28  | 2019-4-24    |
| [CTP 2.4](#CTP24)     | 15.0.1400.75  | 2019-3-27    |
| [CTP 2.3](#CTP23)     | 15.0.1300.359 | 2019-3-01    |
| [CTP 2.2](#CTP22)     | 15.0.1200.24  | 2018-12-11   |
| [CTP 2.1](#CTP21)     | 15.0.1100.94  | 2018-11-06   |
| [CTP 2.0](#CTP20)     | 15.0.1000.34  | 2018-09-24   |

## <a id="cuinstall"></a> Installieren von updates

Wenn Sie die Vorschau-Repository konfiguriert haben (**Mssql-Server-Preview**), und klicken Sie dann die aktuelle CTP-Version von SQL Server-Pakete erhalten Sie, wenn Sie neue Installationen ausführen. Wenn Sie Docker-Container-Images benötigen, finden Sie offizielle-Images für [Microsoft SQL Server unter Linux für Docker-Engine](https://hub.docker.com/r/microsoft/mssql-server/). Weitere Informationen zur Konfiguration des buildrepositorys finden Sie unter [Repositorys für SQL Server unter Linux konfigurieren](sql-server-linux-change-repo.md).

Wenn Sie vorhandene SQL Server-Pakete aktualisieren, führen Sie den entsprechende Update-Befehl für jedes Paket, um die neueste CU zu erhalten. Bestimmte updateanweisungen für jedes Paket finden Sie unter den folgenden Handbüchern zur Installation:

- [Installieren Sie SQL Server-Paket](sql-server-linux-setup.md#upgrade)
- [Installationspaket für die Volltextsuche](sql-server-linux-setup-full-text-search.md)
- [Install SQL Server Integration Services (Installieren von SQL Server Integration Services)](sql-server-linux-setup-ssis.md)
- [Installieren von SQL Server-2019 Vorschau Machine Learning-Dienste-R und Python-Unterstützung unter Linux](sql-server-linux-setup-machine-learning.md)
- [Installieren Sie PolyBase-Paket](../relational-databases/polybase/polybase-linux-setup.md)
- [SQL Server-Agent aktivieren](sql-server-linux-setup-sql-agent.md)

## <a id="CTP31"></a> CTP 3.1 (Juni 2019)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme für die CTP 3.1-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1700.37-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1700.37-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1700.37-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1700.37-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1700.37-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1700.37-2_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1700.37-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1700.37-2_amd64.deb)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1700.37-2_amd64.deb)|

## <a id="CTP30"></a> CTP-Version 3.0 (Mai 2019)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme für die CTP-Version 3.0-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1600.8-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1600.8-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1600.8-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1600.8-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1600.8-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1600.8-1_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1600.8-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1600.8-1_amd64.deb)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1600.8-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a id="CTP25"></a> CTP 2.5 (Apr 2019)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme für die CTP-Version 2.5-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1500.28-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1500.28-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1500.28-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1500.28-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1500.28-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1500.28-1_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1500.28-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1500.28-1_amd64.deb)</br>[PolyBase-RPM-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1500.28-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a id="CTP24"></a> CTP 2.4 (Mar 2019)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme bei der CTP-Version 2.4-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1400.75-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1400.75-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1400.75-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1400.75-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1400.75-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1400.75-2_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1400.75-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1400.75-2_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a id="CTP23"></a> CTP 2.3 (Februar 2019)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme für die CTP-Version 2.3-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1300.359-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1300.359-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1300.359-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1300.359-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1300.359-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1300.359-1_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1300.359-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1300.359-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a id="CTP22"></a> CTP 2.2 (Dezember 2018)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme für die CTP-Version 2.2-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1200.24-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1200.24-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1200.24-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1200.24-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1200.24-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1200.24-2_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1200.24-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1200.24-2_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a id="CTP21"></a> CTP-Version 2.1 (November 2018)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme bei der CTP-Version 2.1 Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1100.94-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1100.94-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1100.94-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a id="CTP20"></a> CTP 2.0 (Sept 2018)

Die folgenden Abschnitte enthalten Paketspeicherorte und bekannte Probleme für die CTP-Version 2.0-Version. Weitere Informationen zu neuen Funktionen von SQL Server-2019 Linux finden Sie unter den [Neuigkeiten in SQL Server-2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 15.0.1000.34-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| SLES-RPM-Paket | 15.0.1000.34-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Java-Erweiterbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Ubuntu 16.04 Debian-Paket | 15.0.1000.34-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Erweiterbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Derzeit erfordert MSDTC Transaktionen nicht authentifiziert. Z. B. Wenn Sie einen Verbindungsserver von SQL Server auf Windows, SQL Server unter Linux verwenden oder eine Windows-Client-Anwendung verwenden, um eine verteilte Transaktion für SQL Server unter Linux zu starten, wird MS DTC ist auf Windows Server und Client erforderlich, um die Option "nicht verwenden Authentifizierung erforderlich".

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Einstieg finden Sie in der folgenden Schnellstarts:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installation unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-ubuntu.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Ausführen und Verbinden – Cloud](quickstart-install-connect-clouds.md)

Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).
