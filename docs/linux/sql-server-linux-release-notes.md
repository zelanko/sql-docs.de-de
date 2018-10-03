---
title: Versionshinweise für SQL Server 2017 unter Linux | Microsoft-Dokumentation
description: Dieser Artikel enthält die Versionshinweise und unterstützte Funktionen für SQL Server 2017 unter Linux ausgeführt wird. Anmerkungen zu dieser Version sind für die neueste Version und früheren Versionen enthalten.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 08/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: d21f9edbc35ecf8f13d6f96f1d4f3ec9c85f31e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752448"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Anmerkungen zu dieser Version von SQL Server 2017 unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Die folgenden Versionshinweise gelten für SQL Server 2017 unter Linux ausgeführt wird. In diesem Artikel wird für jede Version in Abschnitte unterteilt. Die GA-Version verfügt über ausführliche unterstützbarkeit und bekannte Probleme aufgeführt. Jede Kumulatives Update (CU) oder die allgemeine Vertriebsversion (GDR) verfügt über einen Link zu einer Support-Artikel beschreiben die CU Änderungen sowie Links zu den Paketdownloads Linux aus.

> [!TIP]
> Diese Anmerkungen zu dieser Version sind speziell für SQL Server 2017 frei. Weitere Informationen zu dem neuen previewrelease der SQL Server-2019, finden Sie unter [Versionsanmerkungen zu SQL Server-2019-Vorschauversion unter Linux](sql-server-linux-release-notes-2019.md?view=sql-server-ver15).

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

Die folgende Tabelle enthält die Versionsgeschichte für SQL Server 2017.

| Release               | Version       | Veröffentlichungsdatum |
|-----------------------|---------------|--------------|
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9-GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [CU7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02: 20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [ALLGEMEIN VERFÜGBAR](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a> Installieren von updates

Wenn Sie das CU-Repository konfiguriert haben (**Mssql-Server-2017**), und klicken Sie dann die neueste CU von SQL Server-Pakete erhalten Sie, wenn Sie neue Installationen ausführen. Das CU-Repository ist die Standardeinstellung für alle Artikel der Paket-Installation für SQL Server unter Linux. Wenn Sie das GDR-Repository konfiguriert haben (**Mssql-Server-2017-Gdr**), erhalten Sie nur wichtige Sicherheitsupdates, die seit zur allgemeinen Verfügbarkeit veröffentlicht wurden Wenn Sie Docker-Container CU oder GDR-Updates benötigen, finden Sie offizielle-Images für [Microsoft SQL Server unter Linux für Docker-Engine](https://hub.docker.com/r/microsoft/mssql-server). Weitere Informationen zur Konfiguration des buildrepositorys finden Sie unter [Repositorys für SQL Server unter Linux konfigurieren](sql-server-linux-change-repo.md).

Wenn Sie vorhandene SQL Server-Pakete aktualisieren, führen Sie den entsprechende Update-Befehl für jedes Paket, um die neueste CU zu erhalten. Bestimmte updateanweisungen für jedes Paket finden Sie unter den folgenden Handbüchern zur Installation:

- [Installieren Sie SQL Server-Paket](sql-server-linux-setup.md#upgrade)
- [Installationspaket für die Volltextsuche](sql-server-linux-setup-full-text-search.md)
- [Install SQL Server Integration Services (Installieren von SQL Server Integration Services)](sql-server-linux-setup-ssis.md)
- [SQL Server-Agent aktivieren](sql-server-linux-setup-sql-agent.md)

## <a id="CU11"></a> CU11 (September 2018)

Dies ist das kumulative Update 11 (CU11) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3038.14. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4462262 ](https://support.microsoft.com/en-us/help/4462262).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3038.14-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3038.14-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3038.14-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a> CU10 (August 2018)

Dies ist die Kumulatives Update 10 (CU10) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3037.1. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4342123 ](https://support.microsoft.com/en-us/help/4342123).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3037.1-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3037.1-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3037.1-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a> CU9-GDR2 (August 2018)

Dies ist ein Sicherheitsupdate ausgeführt, die auch die zuvor veröffentlichte CU (CU9) für SQL Server 2017 enthält. SQL Server-Engine-Version für diese Version ist 14.0.3035.2. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4293805 ](https://support.microsoft.com/en-us/help/4293805).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3035.2-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| SLES-RPM-Paket | 14.0.3035.2-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3035.2-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a> GDR2 (August 2018)

Dies ist ein Sicherheitsupdate ausgeführt, der nur die Sicherheitskorrekturen GDR2 (und GDR1) für SQL Server 2017 enthält.  SQL Server-Engine-Version für diese Version ist 14.0.2002.14. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4293803 ](https://support.microsoft.com/en-us/help/4293803).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.2002.14-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.2002.14-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.2002.14-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a> CU9 (Juli 2018)

Dies ist die kumulativen Update 9 (CU9) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3030.27. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4341265 ](https://support.microsoft.com/en-us/help/4341265).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3030.27-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3030.27-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3030.27-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a> CU8 (Juni 2018)

Dies ist das kumulative Update 8 (CU8) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3029.16. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4338363 ](https://support.microsoft.com/en-us/help/4338363).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3029.16-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3029.16-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3029.16-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a> CU7 (Mai 2018)

Dies ist die Cumulative Update 7 (CU7) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3026.27. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4229789 ](https://support.microsoft.com/en-us/help/4229789).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3026.27-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3026.27-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3026.27-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (April 2018)

Dies ist die kumulativen Update 6 (CU6) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3025.34. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3025.34-3 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3025.34-3 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3025.34-3 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (März 2018)

Dies ist das kumulative Update 5 (CU5) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3023.8. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/help/4092643 ](https://support.microsoft.com/help/4092643).

### <a name="known-upgrade-issue"></a>Bekanntes Problem

Wenn Sie von einer früheren Version auf CU5 aktualisieren, kann SQL Server nicht mit dem folgenden Fehler gestartet:

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Um diesen Fehler zu beheben, aktivieren Sie SQL Server-Agent, und starten Sie SQL Server mit den folgenden Befehlen neu:

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3023.8-5 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3023.8-5 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3023.8-5 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a> CU4 (Februar 2018)

Dies ist die kumulativen Update 4 (CU4) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3022.28. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4056498 ](https://support.microsoft.com/en-us/help/4056498).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

> [!NOTE]
> Ab CU4 wird die SQL Server-Agent nicht mehr als ein separates Paket installiert. Es wird mit der Engine-Paket installiert und muss aktiviert werden, um verwenden.

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3022.28-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3022.28-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3022.28-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a> GDR1 (Januar 2018)

Dies ist ein Sicherheitsupdate ausgeführt, die nur die GDR1 für SQL Server 2017 Sicherheitsfixes. SQL Server-Engine-Version für diese Version ist 14.0.2000.63. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4057122 ](https://support.microsoft.com/en-us/help/4057122).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.2000.63-3 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.2000.63-3 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.2000.63-3 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a> CU3 (Januar 2018)

Dies ist das kumulative Update 3 (CU3) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3015.40. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/en-us/help/4052987 ](https://support.microsoft.com/en-us/help/4052987).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3015.40-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3015.40-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3015.40-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[Debian-Paket für SQL Server-Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> CU2 (November 2017)

Dies ist das kumulative Update 2 (CU2) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3008.27. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/help/4052574 ](https://support.microsoft.com/help/4052574).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3008.27-1 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3008.27-1 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3008.27-1 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Debian-Paket für SQL Server-Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (Oktober 2017)

Dies ist das kumulative Update 1 (CU1) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.3006.16. Weitere Informationen zu den Problembehebungen und Verbesserungen in dieser Version finden Sie unter [ https://support.microsoft.com/help/KB4053439 ](https://support.microsoft.com/help/4038634).

### <a name="package-details"></a>Paketdetails

Für die manuelle oder offline-Paketinstallationen können Sie die u/min und Debian-Pakete mit den Informationen in der folgenden Tabelle herunterladen:

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.3006.16-3 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.3006.16-3 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.3006.16-3 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Debian-Paket für SQL Server-Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> Bei allgemeiner Verfügbarkeit (Oktober 2017)

Dies ist der allgemeinen Verfügbarkeit (GA) Version von SQL Server 2017. SQL Server-Engine-Version für diese Version ist 14.0.1000.169.

### <a name="package-details"></a>Paketdetails

Paketdetails und Downloadspeicherorte für die u/min und Debian-Pakete werden in der folgenden Tabelle aufgeführt. Beachten Sie, dass Sie nicht benötigen, um diese Pakete direkt herunterzuladen, wenn Sie die Schritte in den folgenden Handbüchern zur Installation verwenden:

- [Installieren Sie SQL Server-Paket](sql-server-linux-setup.md)
- [Installationspaket für die Volltextsuche](sql-server-linux-setup-full-text-search.md)
- [Installieren Sie SQL Server-Agent-Paket](sql-server-linux-setup-sql-agent.md)
- [Install SQL Server Integration Services (Installieren von SQL Server Integration Services)](sql-server-linux-setup-ssis.md)

| Paket | Paketversion | Downloads |
|-----|-----|-----|
| Red Hat-RPM-Paket | 14.0.1000.169-2 | [Engine-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[SSIS-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES-RPM-Paket | 14.0.1000.169-2 | [MSSQL-Server-Engine-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Hohe Verfügbarkeit RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Volltext-Suche-RPM-Paket](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server-Agent-RPM-Paket](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian-Paket | 14.0.1000.169-2 | [Engine-Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Hohe Verfügbarkeit Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Full-Text Search Debian-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Debian-Paket für SQL Server-Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[SSIS-Paket](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a> Nicht unterstützte Features und-Dienste

Die folgenden Features und Dienste sind zum Zeitpunkt der GA-Version nicht unter Linux verfügbar. Die Unterstützung dieser Funktionen wird im Laufe der Zeit immer aktiviert.

| Bereich | Nicht unterstütztes Feature oder Dienst |
|-----|-----|
| **Datenbank-engine** | Transaktionsreplikation |
| &nbsp; | Mergereplikation |
| &nbsp; | Stretch-Datenbank |
| &nbsp; | Polybase |
| &nbsp; | Verteilte Abfragen mit 3rd-Party-Verbindungen |
| &nbsp; | Verbindungsserver für Datenquellen als SQL Server |
| &nbsp; | Erweiterte gespeicherte Systemprozeduren (XP_CMDSHELL usw.) |
| &nbsp; | Filetable FILESTREAM |
| &nbsp; | Legen Sie die CLR-Assemblys mit der EXTERNAL_ACCESS oder UNSAFE-Berechtigung |
| &nbsp; | Pufferpoolerweiterung |
| **SQL Server-Agent** |  Subsysteme: CmdExec, PowerShell, Warteschlangenleser, SSIS, SSAS, SSRS |
| &nbsp; | Warnungen |
| &nbsp; | Protokolllese-Agent |
| &nbsp; | Change Data Capture |
| &nbsp; | Verwaltete Sicherung |
| **High Availability (Hohe Verfügbarkeit)** | Datenbankspiegelung  |
| **Security** | Erweiterbare Schlüsselverwaltung |
| &nbsp; | AD-Authentifizierung für Verbindungsserver | 
| &nbsp; | AD-Authentifizierung für Verfügbarkeitsgruppen (Verfügbarkeitsgruppen) | 
| &nbsp; | 3. Drittanbietertools AD zur Verfügung (Centrify, Vintela, Powerbroker) | 
| **Dienste** | SQL Server-Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |
| &nbsp; | Distributed Transaction Coordinator (DTC) |

## <a name="known-issues"></a>Bekannte Probleme

Die folgenden Abschnitte beschreiben die bekannte Probleme mit der allgemeinen Verfügbarkeit (GA) Version von SQL Server 2017 unter Linux.

#### <a name="general"></a>Allgemein

- Upgrades für die GA-Version von SQL Server 2017 werden nur von der CTP-Version 2.1 oder höher unterstützt. 

- Die Länge des Hostnamens, in dem SQL Server muss installiert sein, mit 15 Zeichen oder kleiner ist. 

    - **Auflösung**: Ändern Sie den Namen in/Etc/Hostname, etwa 15 Zeichen enthalten.

- Manuell die Systemzeit rückwärts festlegen, in Zeit führt dazu, dass SQL Server nicht mehr aktualisiert die interne Systemzeit in SQL Server.

    - **Auflösung**: SQLServer neu starten.

- Nur die Einzelinstanz-Installationen werden unterstützt.

    - **Auflösung**: Wenn Sie mehr als eine Instanz für einen bestimmten Host verfügen, können Sie mithilfe von virtuellen Computern oder Docker-Containern. 

- SQL Server-Konfigurations-Manager Verbindung keine mit SQL Server unter Linux.

- Die Standardsprache der **sa** Anmeldung ist Englisch.

    - **Auflösung**: ändern die Sprache der **sa** melden Sie sich mit den **ALTER LOGIN** Anweisung.

#### <a name="databases"></a>Datenbanken

- Die master-Datenbank kann nicht mit dem Hilfsprogramm für die Mssql-Conf verschoben werden. Anderen Systemdatenbanken können mit der Mssql-conf verschoben werden

- Beim Wiederherstellen einer Datenbank, die für SQL Server unter Windows gesichert wurde, müssen Sie verwenden die **WITH MOVE** -Klausel in Transact-SQL-Anweisung.

- Verteilte Transaktionen, dass der Microsoft Distributed Transaction Coordinator-Dienst werden auf SQL Server unter Linux nicht unterstützt. SQL Server zu SQL Server-Verbindungsservern unterstützt werden, es sei denn, sie DTC umfassen. Weitere Informationen finden Sie unter [verteilte Transaktionen, dass der Microsoft Distributed Transaction Coordinator-Dienst werden nicht auf SQL Server unter Linux unterstützt](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Bestimmte Algorithmen (Verschlüsselungssammlungen) für Transport Layer Security (TLS) funktionieren nicht richtig mit SQL Server unter Linux. Dies führt zu Verbindungsfehlern, bei dem Versuch, eine Verbindung mit SQL Server herstellen, sowie Probleme herstellen von Verbindungen zwischen den Replikaten in Gruppen mit hoher Verfügbarkeit.

   - **Auflösung**: Ändern der **mssql.conf** Konfigurationsskript für SQL Server unter Linux verwendet, um problematische Verschlüsselungssammlungen zu deaktivieren, indem Sie den folgenden Schritten:

      1. Fügen Sie Folgendes, um /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Starten Sie SQL Server mit dem folgenden Befehl neu.

      ```bash
      sudo systemctl restart mssql-server
      ```

- SQL Server 2014-Datenbanken auf Windows, die In-Memory-OLTP verwenden können nicht auf SQL Server 2017 unter Linux nicht wiederhergestellt werden. Zum Wiederherstellen einer SQL Server 2014-Datenbank, die in-Memory OLTP verwendet, zunächst ein upgrade der Datenbanken auf SQL Server 2016 oder SQL Server 2017 unter Windows vor dem Verschieben sie in SQL Server unter Linux, über das Sichern/Wiederherstellen oder trennen/anfügen.

- Benutzerberechtigung **ADMINISTER BULK OPERATIONS** wird unter Linux zurzeit nicht unterstützt.

#### <a name="networking"></a>Netzwerk

Funktionen, die ausgehende TCP-Verbindungen aus dem Sqlservr-Prozess, z. B. auf Verbindungsservern oder Verfügbarkeitsgruppen zu umfassen, funktionieren möglicherweise nicht, wenn die beiden folgenden Bedingungen erfüllt sind:

1. Der Zielserver wird als einen Hostnamen und keine IP-Adresse angegeben.

1. Die Quellinstanz verfügt über IPv6, die in den Kernel deaktiviert. Um zu überprüfen, wenn IPv6 aktiviert ist, in den Kernel auf dem System sind, müssen alle folgenden Tests übergeben:

   - `cat /proc/cmdline` wird von der aktuellen Kernel Boot Cmdline ausgegeben werden. Die Ausgabe darf keinen `ipv6.disable=1`.
   - / Proc/Sys/net/IPv6-bzw. das Verzeichnis muss vorhanden sein.
   - Ein C-Programm, das Aufrufe `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` sollte erfolgreich sein – die Syscall muss eine fd zurückgeben! =-1, und nicht mit EAFNOSUPPORT fehl.

Der genaue Fehler hängt von der Funktion ab. Bei Verbindungsservern Folge hiervon ist, ein Login Timeout-Fehler. Für Verfügbarkeitsgruppen die `ALTER AVAILABILITY GROUP JOIN` DDL auf dem sekundären Replikat schlägt fehl, nach 5 Minuten mit einem Timeoutfehler des Download-Konfiguration.

Führen Sie eine der folgenden Schritte aus, um dieses Problem zu umgehen:

1. Verwenden Sie IP-Adressen anstelle von Hostnamen, um das Ziel der TCP-Verbindung anzugeben.

1. Aktivieren der IPv6-Umgebung in der Kernel durch das Entfernen `ipv6.disable=1` aus der Befehlszeile starten. Die Möglichkeit hierzu hängt davon ab, die Linux-Distribution und den Bootloader, z. B. GRUB-Konfiguration. Wenn sich IPv6 deaktiviert werden soll, können Sie dennoch deaktivieren sie durch Festlegen von `net.ipv6.conf.all.disable_ipv6 = 1` in die `sysctl` Konfiguration (z. B. `/etc/sysctl.conf`). Dies wird immer noch verhindern, dass die Systemvariable Netzwerkadapter eine IPv6-Adresse, aber die Sqlservr Features arbeiten können.

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
Bei Verwendung von **Network File System (NFS)** Remotefreigaben in der Produktion, beachten Sie die folgenden Anforderungen:

- Verwenden Sie NFS-Version **4.2 oder höher**. Ältere Versionen von NFS unterstützen keine erforderlichen Features, wie z. B. Fallocate und Datei mit geringer Dichte erstellen, die für moderne Dateisysteme.
- Suchen Sie nur die **/var/opt/mssql** Verzeichnisse auf die NFS-Bereitstellung. Andere Dateien, z. B. die SQL Server-System-Binärdateien werden nicht unterstützt.
- Stellen Sie sicher, dass die NFS-Clients die Option "Nolock" verwenden, beim Einbinden der Freigabe auf des Remotecomputer.

#### <a name="localization"></a>Lokalisierung

- Wenn Ihr Gebietsschema nicht Englisch ("en_US") während des Setups ist, müssen Sie die UTF-8-Codierung im Bash-Sitzung/Terminal verwenden. Wenn Sie die ASCII-Codierung verwenden, können Sie eine Fehlermeldung ähnlich der folgenden finden Sie unter:

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Wenn Sie die UTF-8-Codierung verwenden können, führen Sie Setup mithilfe der Umgebungsvariablen MSSQL_LCID Ihrer Sprachauswahl angeben.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Wenn Mssql-Conf Setup ausführen, und Durchführen einer nicht englischsprachigen Installations von SQL Server, falsche Sonderzeichen nach den lokalisierten Text, "Konfigurieren von SQL Server..." angezeigt werden. Oder, bei nicht-lateinische basierend Installationen des Satzes fehlt möglicherweise vollständig. Der fehlende Satz die folgende lokalisierte Zeichenfolge sollte angezeigt werden: "die lizenzierungs-PID wurde erfolgreich verarbeitet.  Die neue Edition lautet [\<Namen\> Edition] ". Diese Zeichenfolge wird nur zu Informationszwecken ausgeben, und der nächsten Instanz von kumulative Update für SQL Server wird dies für alle Sprachen lösen. Dies wirkt sich nicht auf die erfolgreiche Installation von SQL Server in keiner Weise. 

#### <a name="full-text-search"></a>Volltextsuche

- Nicht alle Filter sind in dieser Version, einschließlich Filter für Office-Dokumente verfügbar. Eine Liste der unterstützten filtern, finden Sie unter [installieren SQL Server-Volltextsuche für Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- Die **Mssql-Server ist** Paket wird in dieser Version nicht unter SUSE unterstützt. Es wird derzeit unter Ubuntu und auf Red Hat Enterprise Linux (RHEL) unterstützt.

- Mit SSIS unter Linux CTP 2.1 aktualisieren und höher können SSIS-Pakete auf Linux ODBC-Verbindungen. Diese Funktion wurde mit der SQL Server und MySQL-ODBC-Treiber getestet, aber es wird außerdem erwartet, dass alle Unicode-ODBC-Treiber zu arbeiten, die die ODBC-Spezifikation beobachtet. Zur Entwurfszeit können Sie einen DSN oder einer Verbindungszeichenfolge in die ODBC-Verbindung angeben; Sie können auch Windows-Authentifizierung verwenden. Weitere Informationen finden Sie in der [Blogbeitrag Ankündigung ODBC-Unterstützung für Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Die folgenden Funktionen werden in dieser Version nicht unterstützt, beim Ausführen von SSIS-Pakete für Linux:
  - SSIS-Katalogdatenbank
  - Geplante paketausführung vom SQL-Agent
  - Windows-Authentifizierung
  - Drittanbieter-Komponenten
  - Change Data Capture (CDC)
  - SSIS Scale Out-
  - Azure FeaturePack für SSIS
  - Hadoop und HDFS-Unterstützung
  - Microsoft Connector for SAP BW

Eine Liste der integrierten SSIS-Komponenten, die derzeit nicht unterstützt, oder mit Einschränkungen unterstützt werden, finden Sie unter [Einschränkungen und bekannte Probleme für SSIS für Linux](sql-server-linux-ssis-known-issues.md#components).

Weitere Informationen zu SSIS unter Linux finden Sie unter den folgenden Artikeln:
-   [Ankündigung von Blog-Beitrag SSIS-Unterstützung für Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installieren von SQL Server Integration Services (SSIS) unter Linux](sql-server-linux-setup-ssis.md)
-   [Extrahieren, Transformieren und Laden von Daten unter Linux mit SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="-a-idssmsa-sql-server-management-studio-ssms"></a>< eine Id = "Ssms" ></a> SQL Server Management Studio (SSMS)

Die folgenden Einschränkungen gelten für SSMS unter Windows, die mit SQL Server unter Linux verbunden sind.

- Wartungspläne werden nicht unterstützt.

- Management Data Warehouse (MDW) und der Datensammler in SSMS werden nicht unterstützt. 

- SSMS-UI-Komponenten, die Windows-Authentifizierung oder Windows-Ereignisprotokolloptionen funktionieren nicht mit Linux. Sie können diese Features noch mit anderen Optionen, z. B. SQL-Anmeldenamen verwenden. 

- Anzahl der Protokolldateien beibehalten werden sollen, kann nicht geändert werden.

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Einstieg finden Sie in der folgenden Schnellstarts:

- [Installieren Sie unter Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installieren Sie unter SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installieren unter Ubuntu](quickstart-install-connect-ubuntu.md)
- [Führen unter Docker aus](quickstart-install-connect-ubuntu.md)
- [Provision a SQL VM in Azure (Bereitstellen einer SQL-VM in Azure)](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [Ausführen und Verbinden – Cloud](quickstart-install-connect-clouds.md)

Antworten auf häufig gestellte Fragen finden Sie unter den [SQL Server unter Linux – häufig gestellte Fragen](sql-server-linux-faq.md).
