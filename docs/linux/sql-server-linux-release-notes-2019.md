---
title: Versionshinweise für SQL Server 2019 für Linux
description: Dieser Artikel enthält Versionshinweise und Beschreibungen der unterstützten Features für SQL Server 2019 für Linux. Es werden sowohl Versionshinweise zum neuesten Release als auch zu einigen früheren Releases aufgeführt.
author: VanMSFT
ms.author: vanto
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: af3b6f82e3b76e2dd2b11403bccf4b3e0885912e
ms.sourcegitcommit: cbbb210c0315f9e2be2b9cd68db888ac53429814
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69890899"
---
# <a name="release-notes-for-sql-server-2019-on-linux"></a>Versionshinweise für SQL Server 2019 für Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Die folgenden Versionshinweise gelten für SQL Server 2019 bei Ausführung unter Linux. Dieser Artikel ist in Abschnitte für jedes einzelne Release unterteilt. Jede Version verfügt über einen Link zu einem Supportartikel, in dem die Änderungen der Kapazitätseinheit und Links zu herunterladbaren Linux-Paketen enthalten sind.

> [!TIP]
> Weitere Informationen zu neuen Linux-Funktionen in SQL Server 2019 finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

## <a name="supported-platforms"></a>Unterstützte Plattformen

| Platform | Dateisystem | Installationshandbuch |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3-, 7.4-, 7.5- oder 7.6-Server | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-suse.md) |
| Ubuntu 16.04 LTS | XFS oder EXT4 | [Installationshandbuch](quickstart-install-connect-ubuntu.md) | 
| Docker-Engine 1.8+ für Windows, Mac oder Linux | – | [Installationshandbuch](quickstart-install-connect-docker.md) | 

> [!TIP]
> Weitere Informationen finden Sie in den [Systemanforderungen](sql-server-linux-setup.md#system) für SQL Server für Linux. Die neuesten Richtlinien zur Unterstützung für SQL Server 2017 finden Sie unter [Technical support policy for Microsoft SQL Server (Richtlinien für die technische Unterstützung von Microsoft SQL Server)](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Tools

Die meisten Clienttools für SQL Server können mühelos für SQL Server für Linux verwendet werden. Für einige Tools muss womöglich eine spezifische Versionsanforderung erfüllt werden, damit ihr volles Potential mit Linux genutzt werden kann. Eine vollständige Liste der SQL Server-Tools finden Sie unter [SQL Tools and Utilities for SQL Server (SQL-Tools und Hilfsprogramme für SQL Server)](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Releaseverlauf

In der folgenden Tabelle wird der Releaseverlauf für die Vorschauversionen von SQL Server 2019 aufgelistet.

| Release                   | Versionsoptionen       | Veröffentlichungsdatum |
|---------------------------|---------------|--------------|
| [Release Candidate](#rc)  | 15.0.1900.25  | 2019-8-21    |
| [CTP 3.2](#CTP32)         | 15.0.1800.32  | 24.07.2019    |
| [CTP 3.1](#CTP31)         | 15.0.1700.37  | 26.06.2019    |
| [CTP 3.0](#CTP30)         | 15.0.1600.8   | 22.05.2019    |
| [CTP 2.5](#CTP25)         | 15.0.1500.28  | 24.02.2019    |
| [CTP 2.4](#CTP24)         | 15.0.1400.75  | 27.03.2019    |
| [CTP 2.3](#CTP23)         | 15.0.1300.359 | 01.03.2019    |
| [CTP 2.2](#CTP22)         | 15.0.1200.24  | 11.12.2018   |
| [CTP 2.1](#CTP21)         | 15.0.1100.94  | 06.11.2018   |
| [CTP 2.0](#CTP20)         | 15.0.1000.34  | 24.09.2018   |

## <a id="cuinstall"></a> Installieren der Updates

Wenn Sie das Vorschauversionsrepository (**mssql-server-preview**) konfiguriert haben, erhalten Sie bei der Durchführung neuer Installationen die neuesten SQL Server-CTP-Pakete. Wenn Sie Docker-Containerimages benötigen, verwenden Sie die offiziellen Images für [Microsoft SQL Server für Linux für die Docker-Engine](https://hub.docker.com/r/microsoft/mssql-server/). Weitere Informationen zur Repositorykonfiguration finden Sie unter [Configure repositories for SQL Server on Linux (Konfigurieren von Repositorys für SQL Server für Linux)](sql-server-linux-change-repo.md).

Führen Sie den entsprechenden Updatebefehl für jedes Paket durch, wenn Sie vorhandene SQL Server-Pakete aktualisieren, um das neueste kumulative Update zu erhalten. Spezifische Updateanweisungen für die einzelnen Pakete finden Sie in den folgenden Installationshandbüchern:

- [Installieren des SQL Server-Pakets](sql-server-linux-setup.md#upgrade)
- [Installieren des Volltextsuchepakets](sql-server-linux-setup-full-text-search.md)
- [Install SQL Server Integration Services (Installieren von SQL Server Integration Services)](sql-server-linux-setup-ssis.md)
- [Installieren von SQL Server 2019 Machine Learning Services (Vorschauversion) unter Linux (R und Python)](sql-server-linux-setup-machine-learning.md)
- [Installieren des PolyBase-Pakets](../relational-databases/polybase/polybase-linux-setup.md)
- [Aktivieren des SQL Server-Agents](sql-server-linux-setup-sql-agent.md)

## <a id="rc"></a> Release Candidate (August 2019)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der RC-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1900.25-1 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1900.25-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1900.25-1.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1900.25-1 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1900.25-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1900.25-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1900.25-1.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1900.25-1 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1900.25-1_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1900.25-1_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1900.25-1_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1900.25-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1900.25-1_amd64.deb)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1900.25-1_amd64.deb)|

## <a id="CTP32"></a> CTP 3.2 (Juli 2019)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 3.2-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1800.32-1 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1800.32-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1800.32-1.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1800.32-1 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1800.32-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1800.32-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1800.32-1.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1800.32-1 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1800.32-1_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1800.32-1_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1800.32-1_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1800.32-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1800.32-1_amd64.deb)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1800.32-1_amd64.deb)|

## <a id="CTP31"></a> CTP 3.1 (Juni 2019)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 3.1-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1700.37-2 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1700.37-2 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1700.37-2 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1700.37-2_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1700.37-2_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1700.37-2_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1700.37-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1700.37-2_amd64.deb)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1700.37-2_amd64.deb)|

## <a id="CTP30"></a> CTP 3.0 (Mai 2019)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 3.0-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1600.8-1 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1600.8-1 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1600.8-1 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1600.8-1_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1600.8-1_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1600.8-1_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1600.8-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1600.8-1_amd64.deb)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1600.8-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Zurzeit erfordert MSDTC, dass Transaktionen nicht authentifiziert werden. Wenn Sie beispielsweise einen Verbindungsserver von SQL Server unter Windows zu SQL Server für Linux oder eine Windows-Clientanwendung zum Starten einer verteilten Transaktion für SQL Server für Linux verwenden, muss für den MS DTC auf dem Windows-Server/Client die Option „No Authentification Required“ (Keine Authentifizierung erforderlich) verwendet werden.

## <a id="CTP25"></a> CTP 2.5 (April 2019)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 2.5-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1500.28-1 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1500.28-1 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1500.28-1 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1500.28-1_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1500.28-1_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1500.28-1_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1500.28-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1500.28-1_amd64.deb)</br>[RPM-PolyBase-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1500.28-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Zurzeit erfordert MSDTC, dass Transaktionen nicht authentifiziert werden. Wenn Sie beispielsweise einen Verbindungsserver von SQL Server unter Windows zu SQL Server für Linux oder eine Windows-Clientanwendung zum Starten einer verteilten Transaktion für SQL Server für Linux verwenden, muss für den MS DTC auf dem Windows-Server/Client die Option „No Authentification Required“ (Keine Authentifizierung erforderlich) verwendet werden.

## <a id="CTP24"></a> CTP 2.4 (März 2019)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 2.4-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1400.75-2 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1400.75-2 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1400.75-2 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1400.75-2_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1400.75-2_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1400.75-2_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1400.75-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1400.75-2_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Zurzeit erfordert MSDTC, dass Transaktionen nicht authentifiziert werden. Wenn Sie beispielsweise einen Verbindungsserver von SQL Server unter Windows zu SQL Server für Linux oder eine Windows-Clientanwendung zum Starten einer verteilten Transaktion für SQL Server für Linux verwenden, muss für den MS DTC auf dem Windows-Server/Client die Option „No Authentification Required“ (Keine Authentifizierung erforderlich) verwendet werden.

## <a id="CTP23"></a> CTP 2.3 (Februar 2019)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 2.3-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1300.359-1 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1300.359-1 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1300.359-1 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1300.359-1_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1300.359-1_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1300.359-1_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1300.359-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1300.359-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Zurzeit erfordert MSDTC, dass Transaktionen nicht authentifiziert werden. Wenn Sie beispielsweise einen Verbindungsserver von SQL Server unter Windows zu SQL Server für Linux oder eine Windows-Clientanwendung zum Starten einer verteilten Transaktion für SQL Server für Linux verwenden, muss für den MS DTC auf dem Windows-Server/Client die Option „No Authentification Required“ (Keine Authentifizierung erforderlich) verwendet werden.

## <a id="CTP22"></a> CTP 2.2 (Dezember 2018)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 2.2-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1200.24-2 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1200.24-2 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1200.24-2 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1200.24-2_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1200.24-2_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1200.24-2_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1200.24-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1200.24-2_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Zurzeit erfordert MSDTC, dass Transaktionen nicht authentifiziert werden. Wenn Sie beispielsweise einen Verbindungsserver von SQL Server unter Windows zu SQL Server für Linux oder eine Windows-Clientanwendung zum Starten einer verteilten Transaktion für SQL Server für Linux verwenden, muss für den MS DTC auf dem Windows-Server/Client die Option „No Authentification Required“ (Keine Authentifizierung erforderlich) verwendet werden.

## <a id="CTP21"></a> CTP 2.1 (November 2018)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 2.1-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1100.94-1 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1100.94-1 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1100.94-1 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Zurzeit erfordert MSDTC, dass Transaktionen nicht authentifiziert werden. Wenn Sie beispielsweise einen Verbindungsserver von SQL Server unter Windows zu SQL Server für Linux oder eine Windows-Clientanwendung zum Starten einer verteilten Transaktion für SQL Server für Linux verwenden, muss für den MS DTC auf dem Windows-Server/Client die Option „No Authentification Required“ (Keine Authentifizierung erforderlich) verwendet werden.

## <a id="CTP20"></a> CTP 2.0 (September 2018)

In den folgenden Abschnitten werden Paketspeicherorte und bekannte Probleme bezüglich der CTP 2.0-Version bereitgestellt. Weitere Informationen zu den neuen Funktionen für SQL Server 2019 unter Linux finden Sie unter [Neues in SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Paketdetails

Für manuelle oder offline durchgeführte Paketinstallationen können Sie die RPM- und Debian-Pakete herunterladen, die in der folgenden Tabelle aufgeführt werden:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat RPM-Paket | 15.0.1000.34-2 | [RPM-Engine-Paket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| SLES RPM-Paket | 15.0.1000.34-2 | [RPM-Engine-Paket (mssql-server)](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Hochverfügbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Paket für Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Erweiterbarkeitspaket](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[RPM-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Debian-Paket für Ubuntu 16.04 | 15.0.1000.34-2 | [Debian-Engine-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Debian-Hochverfügbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Debian-Paket für Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Debian-Erweiterbarkeitspaket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Debian-Paket für Java-Erweiterbarkeit](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Bekannte Probleme

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Zurzeit erfordert MSDTC, dass Transaktionen nicht authentifiziert werden. Wenn Sie beispielsweise einen Verbindungsserver von SQL Server unter Windows zu SQL Server für Linux oder eine Windows-Clientanwendung zum Starten einer verteilten Transaktion für SQL Server für Linux verwenden, muss für den MS DTC auf dem Windows-Server/Client die Option „No Authentification Required“ (Keine Authentifizierung erforderlich) verwendet werden.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Schnellstarts finden Sie Informationen zu den ersten Schritten:

- [Installieren unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installation unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installation unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Ausführen unter Docker](quickstart-install-connect-ubuntu.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Ausführen und Verbinden – Cloud](quickstart-install-connect-clouds.md)

Antworten auf häufig gestellte Fragen finden Sie unter [Häufig gestellte Fragen zu SQL Server unter Linux](sql-server-linux-faq.md).
