---
title: Anmerkungen zu dieser Version von SQL Server 2017 unter Linux
description: Dieser Artikel enthält die Anmerkungen zu dieser Version und unterstützten Funktionen für SQL Server 2017 unter Linux. Anmerkungen zu dieser Version sind in der neuesten Version und in einigen früheren Versionen enthalten.
author: VanMSFT
ms.author: vanto
ms.date: 06/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: 5b6fce0bdde7e320eea0371125a61627652de80d
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388409"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Anmerkungen zu dieser Version von SQL Server 2017 unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Die folgenden Anmerkungen zu dieser Version [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] gelten für die Ausführung unter Linux. Dieser Artikel ist für jede Version in Abschnitte unterteilt. Die allgemein verfügbare Version bietet ausführliche Unterstützung und bekannte Probleme. Jedes kumulative Update (Cu) oder die General Distribution Release (DDR) enthält einen Link zu einem Support Artikel, in dem die CU-Änderungen beschrieben werden, sowie Links zu den Downloads für Linux-Pakete.

> [!TIP]
> Diese Anmerkungen zu dieser Version gelten [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] speziell für Releases. Weitere Informationen zum neuen [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]finden Sie in den Anmerkungen zu dieser Version von [SQL Server 2019 Preview unter Linux](sql-server-linux-release-notes-2019.md?view=sql-server-ver15).

## <a name="supported-platforms"></a>Unterstützte Plattformen

| Platform | Dateisystem | Installationshandbuch |
|-----|-----|-----|
| Red Hat Enterprise Linux 7,3, 7,4, 7,5 oder 7,6 Server | XFS oder ext4 | [Installationshandbuch](quickstart-install-connect-red-hat.md) | 
| SuSE Enterprise Linux Server V12 SP2 | XFS oder ext4 | [Installationshandbuch](quickstart-install-connect-suse.md) |
| Ubuntu 16.04 LTS | XFS oder ext4 | [Installationshandbuch](quickstart-install-connect-ubuntu.md) | 
| Docker-Engine 1.8 und höher unter Windows, Mac oder Linux | Nicht zutreffend | [Installationshandbuch](quickstart-install-connect-docker.md) | 

> [!TIP]
> Weitere Informationen finden Sie in den [Systemanforderungen](sql-server-linux-setup.md#system) für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux. Die neueste Unterstützungs Richtlinie für [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]finden Sie in der [technischen Support Richtlinie für Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Tools

Die meisten vorhandenen-Client Tools [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] abzielen, können unter Linux nahtlos ausgeführt werden. Einige Tools verfügen möglicherweise über eine bestimmte Versions Anforderung für eine gute Zusammenarbeit mit Linux. Eine vollständige Liste der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Tools finden Sie unter [SQL-Tools und-Hilfsprogramme für SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Releaseverlauf

In der folgenden Tabelle wird der releaseverlauf für [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]aufgelistet.

| Release               | Version       | Veröffentlichungsdatum |
|-----------------------|---------------|--------------|
| [CU15](#CU15)         | 14.0.3162.1   | 2019-05-23   |
| [CU14](#CU14)         | 14.0.3076.1   | 2019-03-25   |
| [CU13](#CU13)         | 14.0.3048.4   | 2018-12-18   |
| [CU12](#CU12)         | 14.0.3045.24  | 2018-10-24   |
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9-GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [CU7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [GAS](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a>Installieren von Updates

Wenn Sie das Cu-Repository (**MSSQL-Server-2017**) konfiguriert haben, erhalten Sie bei der Durchführung neuer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Installationen die neuesten Cu-Pakete. Das CU-Repository ist die Standardeinstellung für alle Paket Installations [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Artikel für unter Linux. Wenn Sie das DDR-Repository (**MSSQL-Server-2017-DDR**) konfiguriert haben, erhalten Sie nur wichtige Sicherheitsupdates, die seit der allgemeinen Verfügbarkeit veröffentlicht wurden. Wenn Sie docker-Container-Cu-oder DDR-Updates benötigen, lesen Sie die offiziellen Images für [Microsoft SQL Server für Linux für die Docker-Engine](https://hub.docker.com/r/microsoft/mssql-server). Weitere Informationen zur Konfiguration des Repository finden Sie unter [Konfigurieren von Repository für SQL Server für Linux](sql-server-linux-change-repo.md).

Wenn Sie vorhandene [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Pakete aktualisieren, führen Sie den entsprechenden Update-Befehl für jedes Paket aus, um das neueste Cu zu erhalten. Spezifische Update Anweisungen für jedes Paket finden Sie in den folgenden Installations Handbüchern:

- [Installieren SQL Server Pakets](sql-server-linux-setup.md#upgrade)
- [Voll Text suchpaket installieren](sql-server-linux-setup-full-text-search.md)
- [Install SQL Server Integration Services (Installieren von SQL Server Integration Services)](sql-server-linux-setup-ssis.md)
- [Aktivieren von SQL Server-Agent](sql-server-linux-setup-sql-agent.md)

## <a id="CU15"></a>CU15 (2019)

Dies ist das kumulative Update 15 (CU15) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3162.1. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/en-us/help/4498951](https://support.microsoft.com/en-us/help/4498951)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3162.1-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3162.1-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3162.1-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3162.1-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3162.1-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3162.1-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU14"></a>CU14 (2019)

Dies ist das kumulative Update 14 (CU14) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3076.1. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4484710](https://support.microsoft.com/help/4484710)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3076.1-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3076.1-2 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3076.1-2 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3076.1-2_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3076.1-2_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3076.1-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU13"></a>CU13 (Dec 2018)

Dies ist das kumulative Update 13 (CU13) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3048.4. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4466404](https://support.microsoft.com/help/4466404)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3048.4-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3048.4-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3048.4-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3048.4-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3048.4-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3048.4-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU12"></a>CU12 (Okt 2018)

Dies ist das kumulative Update 12 (CU12) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3045.24. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4464082](https://support.microsoft.com/help/4464082)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3045.24-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3045.24-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3045.24-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a>CU11 (September 2018)

Dies ist das kumulative Update 11 (CU11) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3038.14. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4462262](https://support.microsoft.com/help/4462262)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3038.14-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3038.14-2 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3038.14-2 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a>CU10 (Aug 2018)

Dies ist das kumulative Update 10 (CU10) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3037.1. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4342123](https://support.microsoft.com/help/4342123)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3037.1-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3037.1-2 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3037.1-2 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a>CU9-GDR2 (Aug 2018)

Dabei handelt es sich um ein Sicherheitsupdate, das auch die zuvor veröffentlichte Cu ( [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]CU9) für enthält. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3035.2. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4293805](https://support.microsoft.com/help/4293805)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3035.2-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| SLES RPM-Paket | 14.0.3035.2-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3035.2-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a>GDR2 (Aug 2018)

Hierbei handelt es sich um ein Sicherheitsupdate, das nur die GDR2-Sicherheitskorrekturen ( [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]und GDR1) für enthält.  Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.2002.14. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4293803](https://support.microsoft.com/help/4293803)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.2002.14-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.2002.14-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.2002.14-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a>CU9 (Jul 2018)

Dies ist das kumulative Update 9-Release (CU9 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]) von. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3030.27. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4341265](https://support.microsoft.com/help/4341265)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3030.27-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3030.27-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3030.27-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a>CU8 (Jun 2018)

Dies ist die kumulative Update 8-Version (CU8 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]) von. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3029.16. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4338363](https://support.microsoft.com/help/4338363)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3029.16-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3029.16-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3029.16-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a>CU7 (2018)

Dies ist das kumulative Update 7 (CU7) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3026.27. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4229789](https://support.microsoft.com/help/4229789)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3026.27-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3026.27-2 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3026.27-2 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a>CU6 (Apr 2018)

Dies ist das kumulative Update 6 (CU6) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3025.34. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3025.34-3 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3025.34-3 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3025.34-3 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a>CU5 (2018)

Dies ist das kumulative Update 5 (CU5) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3023.8. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4092643](https://support.microsoft.com/help/4092643)Sie unter.

### <a name="known-upgrade-issue"></a>Bekanntes Upgradeproblem

Wenn Sie ein Upgrade von einer früheren Version auf CU5 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] durchführen, kann möglicherweise nicht gestartet werden. der folgende Fehler wird angezeigt:

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Um diesen Fehler zu beheben, aktivieren Sie SQL Server-Agent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , und starten Sie ihn mit den folgenden Befehlen neu:

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3023.8-5 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3023.8-5 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3023.8-5 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a>CU4 (Feb 2018)

Dies ist die kumulative Update 4 (CU4)- [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]Version von. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3022.28. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4056498](https://support.microsoft.com/help/4056498)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

> [!NOTE]
> Ab CU4 wird SQL Server-Agent nicht mehr als separates Paket installiert. Sie wird mit dem-Engine-Paket installiert und muss für die Verwendung von aktiviert werden.

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3022.28-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3022.28-2 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3022.28-2 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a>GDR1 (2018)

Hierbei handelt es sich um ein Sicherheitsupdate, das nur die GDR1 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]-Sicherheitskorrekturen für umfasst. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.2000.63. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4057122](https://support.microsoft.com/help/4057122)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.2000.63-3 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.2000.63-3 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.2000.63-3 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a>CU3 (2018)

Dies ist das kumulative Update 3 (CU3) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3015.40. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4052987](https://support.microsoft.com/help/4052987)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3015.40-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3015.40-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3015.40-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[SQL Server-Agent Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a>Cu2 (2017)

Dies ist das kumulative Update 2 (Cu2) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3008.27. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3008.27-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3008.27-1 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3008.27-1 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[SQL Server-Agent Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a>CU1 (Okt 2017)

Dies ist das kumulative Update 1 (CU1) von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.3006.16. Informationen zu den Korrekturen und Verbesserungen in dieser Version finden [https://support.microsoft.com/help/KB4053439](https://support.microsoft.com/help/4038634)Sie unter.

### <a name="package-details"></a>Paket Details

Bei manuellen oder offline-Paketinstallationen können Sie die RPM-und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.3006.16-3 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.3006.16-3 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.3006.16-3 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[SQL Server-Agent Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a>GA (Okt 2017)

Dies ist die allgemein verfügbare Version von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Die [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Version für diese Version ist 14.0.1000.169.

### <a name="package-details"></a>Paket Details

In der folgenden Tabelle sind die Paket Details und die Download Speicherorte für die RPM-und Debian-Pakete aufgeführt. Beachten Sie, dass Sie diese Pakete nicht direkt herunterladen müssen, wenn Sie die Schritte in den folgenden Installations Handbüchern ausführen:

- [Installieren SQL Server Pakets](sql-server-linux-setup.md)
- [Voll Text suchpaket installieren](sql-server-linux-setup-full-text-search.md)
- [Installieren SQL Server-Agent Pakets](sql-server-linux-setup-sql-agent.md)
- [Install SQL Server Integration Services (Installieren von SQL Server Integration Services)](sql-server-linux-setup-ssis.md)

| Package | Paketversion | Downloads |
|-----|-----|-----|
| Red hat RPM-Paket | 14.0.1000.169-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM-Paket | 14.0.1000.169-2 | [MSSQL-Server-Engine (RPM-Paket)](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Hoch Verfügbarkeits-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[RPM-Paket für die Volltextsuche](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server-Agent RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Ubuntu 16,04 Debian-Paket | 14.0.1000.169-2 | [Engine Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Hochverfügbarkeit des Debian-Pakets](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Debian-Paket für die Volltextsuche](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[SQL Server-Agent Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a>Nicht unterstützte Funktionen & Services

Die folgenden Features und Dienste sind unter Linux zum Zeitpunkt der GA-Version nicht verfügbar. Die Unterstützung dieser Funktionen wird im Laufe der Zeit immer mehr aktiviert.

| Bereich | Nicht unterstütztes Feature oder Dienst |
|-----|-----|
| **Datenbank-Engine** | Transaktionsreplikation |
| &nbsp; | Mergereplikation |
| &nbsp; | Change Data Capture (siehe SQL Server-Agent) |
| &nbsp; | Stretch-DB |
| &nbsp; | PolyBase |
| &nbsp; | Verteilte Abfrage mit Verbindungen von Drittanbietern |
| &nbsp; | Verbindungs Server mit anderen Datenquellen als[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  |
| &nbsp; | Erweiterte gespeicherte Prozeduren für das System (XP_CMDSHELL usw.) |
| &nbsp; | FILETABLE, FileStream |
| &nbsp; | CLR-Assemblys mit dem Berechtigungs Satz EXTERNAL_ACCESS oder unsicher |
| &nbsp; | Pufferpoolerweiterung |
| **SQL Server-Agent** |  Subsysteme CmdExec, PowerShell, Warteschlangen Leser, SSIS, SSAS, SSRS |
| &nbsp; | Benachrichtigungen |
| &nbsp; | Protokolllese-Agent |
| &nbsp; | Change Data Capture (CDC) |
| &nbsp; | Verwaltete Sicherung |
| **High Availability (Hohe Verfügbarkeit)** | Datenbankspiegelung  |
| **Sicherheit** | Erweiterbare Schlüsselverwaltung |
| &nbsp; | AD-Authentifizierung für Verbindungs Server | 
| &nbsp; | AD-Authentifizierung für Verfügbarkeits Gruppen (AGS) | 
| &nbsp; | Drittanbieter-Ad-Tools (Centrify, Vintela, PowerBroker) | 
| **Dienste** | SQL Server-Browser |
| &nbsp; | SQL Server R Services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |
| &nbsp; | Distributed Transaction Coordinator (DTC) |

## <a name="known-issues"></a>Bekannte Probleme

In den folgenden Abschnitten werden bekannte Probleme mit der allgemein verfügbaren Version von [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] unter Linux beschrieben.

#### <a name="general"></a>Allgemein

- Die Länge des Host namens, bei [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dem installiert wird, muss höchstens 15 Zeichen lang sein. 

    - **Lösung**: Ändern Sie den Namen in/etc/hostname in etwas, das höchstens 15 Zeichen lang ist.

- Die manuelle Festlegung der Systemzeit in der Zeit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] führt dazu, dass die Aktualisierung der internen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Systemzeit in nicht mehr dauert.

    - **Lösung**: Starten Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]neu.

- Nur einzelinstanzinstallationen werden unterstützt.

    - **Lösung**: Wenn Sie mehr als eine Instanz auf einem bestimmten Host verwenden möchten, sollten Sie die Verwendung von VMS oder docker-Containern in Erwägung gezogen. 

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Configuration Manager kann unter Linux [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keine Verbindung herstellen.

- Die Standardsprache der **sa** -Anmeldung ist Englisch.

    - **Lösung**: Ändern Sie die Sprache der **sa** -Anmeldung mit der **Alter Login** -Anweisung.

#### <a name="databases"></a>Datenbanken

- Die Master-Datenbank kann nicht mit dem Hilfsprogramm "MSSQL-conf" verschoben werden. Andere System Datenbanken können mit MSSQL-conf verschoben werden.

- Beim Wiederherstellen einer Datenbank, die unter Windows [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gesichert wurde, müssen Sie die **with Move** -Klausel in der Transact-SQL-Anweisung verwenden.

- Verteilte Transaktionen, die den Microsoft Distributed Transaction Coordinator-Dienst erfordern, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] werden bei der Ausführung unter Linux nicht unterstützt. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Verbindungs Server werden unterstützt, es sei denn, Sie umfassen den DTC. Weitere Informationen finden Sie unter [verteilte Transaktionen, die erfordern, dass der Microsoft Distributed Transaction Coordinator-Dienst auf SQL Server unter Linux nicht unterstützt](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/)wird.

- Bestimmte Algorithmen (Verschlüsselungs Sammlungen) für Transport Layer Security (TLS) funktionieren unter Linux nicht ordnungsgemäß [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Dies führt zu Verbindungsfehlern beim Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]sowie beim Herstellen von Verbindungen zwischen Replikaten in hoch Verfügbarkeits Gruppen.

   - **Lösung**: Ändern Sie das Konfigurationsskript **MSSQL. conf** für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unter Linux, um problematische Verschlüsselungs Sammlungen zu deaktivieren, indem Sie die folgenden Schritte ausführen:

      1. Fügen Sie Folgendes zu/var/opt/MSSQL/MSSQL.conf. hinzu:

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Starten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Sie mit dem folgenden Befehl neu.

      ```bash
      sudo systemctl restart mssql-server
      ```

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]Datenbanken unter Windows, die in-Memory OLTP verwenden, können [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] unter Linux unter Linux nicht wieder hergestellt werden. Zum Wiederherstellen [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] einer Datenbank, die in-Memory-OLTP verwendet, aktualisieren Sie [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] zuerst [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] die Datenbanken auf oder unter [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows, bevor Sie Sie über Backup/Restore oder Detach/Attach auf Linux verschieben.

- Die Benutzer Berechtigung zum **Verwalten von Massen Vorgängen** wird unter Linux zurzeit nicht unterstützt.

#### <a name="networking"></a>Netzwerk

Funktionen, die ausgehende TCP-Verbindungen aus dem sqlservr-Prozess einschließen, wie z. b. Verbindungs Server oder Verfügbarkeits Gruppen, funktionieren möglicherweise nicht, wenn beide der folgenden Bedingungen erfüllt sind:

1. Der Zielserver wird als Hostname und nicht als IP-Adresse angegeben.

1. In der Quell Instanz ist IPv6 im Kernel deaktiviert. Um zu überprüfen, ob für das System IPv6 im Kernel aktiviert ist, müssen alle folgenden Tests bestanden werden:

   - `cat /proc/cmdline`druckt die Start-cmdline des aktuellen Kernels. Die Ausgabe darf nicht enthalten `ipv6.disable=1`.
   - Das Verzeichnis/proc/sys/net/IPv6/muss vorhanden sein.
   - Ein C-Programm, `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` das aufruft, sollte erfolgreich sein. "syscall" muss ein "FD! =-1" zurückgeben, und "eafnosupport" schlägt fehl.

Der genaue Fehler hängt von der Funktion ab. Für Verbindungs Server stellt dies einen Fehler beim Anmeldungs Timeout dar. Bei Verfügbarkeits Gruppen schlägt `ALTER AVAILABILITY GROUP JOIN` die DDL auf dem sekundären Replikat nach fünf Minuten mit einem Timeout Fehler beim Herunterladen fehl.

Um dieses Problem zu umgehen, führen Sie einen der folgenden Schritte aus:

1. Verwenden Sie IPS anstelle von Hostnamen, um das Ziel der TCP-Verbindung anzugeben.

1. Aktivieren Sie IPv6 im Kernel, indem `ipv6.disable=1` Sie aus der Start-cmdline entfernen. Die Vorgehensweise ist abhängig von der Linux-Distribution und dem Bootloader, wie z. b. grub. Wenn Sie möchten, dass IPv6 deaktiviert wird, können Sie es dennoch deaktivieren, indem `net.ipv6.conf.all.disable_ipv6 = 1` Sie in `sysctl` der Konfiguration ( `/etc/sysctl.conf`z. b.) festlegen. Dadurch wird weiterhin verhindert, dass der Netzwerkadapter des Systems eine IPv6-Adresse erhält, aber die sqlservr-Funktionen funktionieren.

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
Wenn Sie NFS-Remote Freigaben **(Network File System)** in der Produktion verwenden, beachten Sie die folgenden Supportanforderungen:

- Verwenden Sie die NFS-Version **4,2 oder höher**. Ältere Versionen von NFS bieten keine Unterstützung für erforderliche Features, wie z. b. die Erstellung von Zuordnungen und die Erstellung von Dateien mit geringer Dichte.
- Suchen Sie nur die **/var/opt/MSSQL** -Verzeichnisse in der NFS-einreitung. Andere Dateien, z. b [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . die System Binärdateien, werden nicht unterstützt.
- Stellen Sie sicher, dass NFS-Clients die Option "NOLOCK" verwenden, wenn Sie die Remote Freigabe einbinden.

#### <a name="localization"></a>Lokalisierung

- Wenn Ihr Gebiets Schema während des Setups nicht Englisch (en_US) ist, müssen Sie die UTF-8-Codierung in ihrer bash-Sitzung/dem Terminal verwenden. Wenn Sie die ASCII-Codierung verwenden, wird möglicherweise ein Fehler wie der folgende angezeigt:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Wenn Sie die UTF-8-Codierung nicht verwenden können, führen Sie Setup mithilfe der MSSQL_LCID-Umgebungsvariablen aus, um Ihre Sprachauswahl anzugeben.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Wenn Sie das MSSQL-conf-Setup ausführen und eine nicht englische Installation von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ausführen, werden falsche erweiterte Zeichen nach dem lokalisierten Text "Konfigurieren von SQL Server..." angezeigt. Für nicht auf Latein basierende Installationen könnte der Satz möglicherweise vollständig fehlen. Der fehlende Satz sollte die folgende lokalisierte Zeichenfolge anzeigen: "Die Lizenzierungs-PID wurde erfolgreich verarbeitet. Die neue Edition ist [\<Name\> Edition] ". Diese Zeichenfolge wird nur zu Informationszwecken ausgegeben, und das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nächste kumulative Update adressiert dies für alle Sprachen. Dies hat keine Auswirkung auf die erfolgreiche Installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] von in irgendeiner Weise. 

#### <a name="full-text-search"></a>Volltextsuche

- In dieser Version sind nicht alle Filter verfügbar, einschließlich der Filter für Office-Dokumente. Eine Liste der unterstützten Filter finden Sie unter [installieren SQL Server voll Text Suche unter Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- Das **MSSQL-Server-is-** Paket wird in dieser Version in SuSE nicht unterstützt. Sie wird derzeit unter Ubuntu und auf Red Hat Enterprise Linux (RHEL) unterstützt.

- Mit [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on Linux CTP 2,1 Refresh und höher können [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Pakete ODBC-Verbindungen unter Linux verwenden. Diese Funktion wurde mit dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] und den MySQL-ODBC-Treibern getestet, aber es wird auch erwartet, dass Sie mit jedem Unicode-ODBC-Treiber funktioniert, der die ODBC-Spezifikation beachtet. Zur Entwurfszeit können Sie entweder einen DSN oder eine Verbindungs Zeichenfolge angeben, um eine Verbindung mit den ODBC-Daten herzustellen. Sie können auch die Windows-Authentifizierung verwenden. Weitere Informationen finden Sie im [Blogbeitrag ankündigen der ODBC-Unterstützung unter Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Die folgenden Funktionen werden in dieser Version nicht unterstützt, wenn Sie SSIS-Pakete unter Linux ausführen:
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]Katalog Datenbank
  - Geplante Paket Ausführung durch SQL-Agent
  - Windows-Authentifizierung
  - Komponenten von Drittanbietern
  - Change Data Capture (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]Scale Out
  - Azure Feature Pack für SSIS
  - Hadoop-und HDFS-Unterstützung
  - Microsoft Connector for SAP BW

Eine Liste der integrierten SSIS-Komponenten, die derzeit nicht unterstützt werden oder mit Einschränkungen unterstützt werden, finden Sie unter [Einschränkungen und bekannte Probleme für SSIS unter Linux](sql-server-linux-ssis-known-issues.md#components).

Weitere Informationen zu SSIS unter Linux finden Sie in den folgenden Artikeln:
-   [Blog Beitrag zur Ankündigung der SSIS-Unterstützung für Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installieren von SQL Server Integration Services (SSIS) unter Linux](sql-server-linux-setup-ssis.md)
-   [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](sql-server-linux-migrate-ssis.md)

#### <a id="ssms"></a> SQL Server Management Studio (SSMS)

Die folgenden Einschränkungen gelten für [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] unter Windows, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] das mit unter Linux verbunden ist.

- Wartungspläne werden nicht unterstützt.

- Management Data Warehouse (MDW) und der Datensammler in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] werden nicht unterstützt. 

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]UI-Komponenten mit Windows-Authentifizierung oder Windows-Ereignisprotokoll Optionen funktionieren nicht mit Linux. Diese Features können weiterhin mit anderen Optionen verwendet werden, wie z. b. SQL-Anmeldungen. 

- Die Anzahl der zu beibehaltenden Protokolldateien kann nicht geändert werden.

## <a name="next-steps"></a>Nächste Schritte

Informationen zu den ersten Schritten finden Sie in den folgenden Schnellstarts:

- [Auf Red Hat Enterprise Linux installieren](quickstart-install-connect-red-hat.md)
- [Auf SuSE Linux Enterprise Server installieren](quickstart-install-connect-suse.md)
- [Installation unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Auf docker ausführen](quickstart-install-connect-ubuntu.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Ausführen und Verbinden – Cloud](quickstart-install-connect-clouds.md)

Antworten auf häufig gestellte Fragen finden Sie in den [SQL Server für Linux FAQ](sql-server-linux-faq.md).
