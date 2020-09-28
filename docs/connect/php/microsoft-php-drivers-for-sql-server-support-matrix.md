---
title: Unterstützungsmatrix für Microsoft-Treiber für PHP
description: Auf dieser Seite finden Sie die Unterstützungsmatrix und die Support Lifecycle-Richtlinie für die Microsoft PHP-Treiber für SQL Server.
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 778d9aa4ee666ba3719095508d5f5e28516f954d
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87942159"
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>Unterstützungsmatrix für Microsoft-PHP-Treiber für SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Auf dieser Seite finden Sie die Unterstützungsmatrix und die Support Lifecycle-Richtlinie für die Microsoft PHP-Treiber für SQL Server.

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Support Lifecycle-Matrix und -Richtlinie für Microsoft PHP-Treiber

Die Microsoft Support Lifecycle-Richtlinie (MLS) bietet transparente, vorhersagbare Informationen hinsichtlich der Supportdauer bei Microsoft-Produkten. Für die Versionen 3.x, 4.x und 5.x des PHP-Treibers wird ab dem Veröffentlichungsdatum fünf Jahre grundlegender Support (Mainstream-Support) geleistet. Die Definition für den grundlegenden Support finden Sie auf der [Website der Microsoft Support Lifecycle-Richtlinie](https://support.microsoft.com/lifecycle).

Erweiterte und benutzerdefinierte Support-Optionen sind für die Microsoft PHP-Treiber nicht verfügbar.

Die folgenden Microsoft PHP-Treiber werden bis zum angegebenen Supportende unterstützt.

|Treibername|Version des Treiberpakets|Ende des grundlegenden Supports|
|-|:-:|-|
|Microsoft PHP-Treiber 5.8 für SQL Server|5.8|31. Januar 2025|
|Microsoft PHP-Treiber 5.6 für SQL Server|5.6|21. Februar 2024|
|Microsoft PHP-Treiber 5.3 für SQL Server|5.3|20. Juli 2023|
|Microsoft PHP-Treiber 5.2 für SQL Server|5,2|9\. Februar 2023|
|Microsoft PHP-Treiber 4.3 für SQL Server|4.3|6\. Juli 2022|
|Microsoft PHP-Treiber 4.0 für SQL Server|4,0|11. Juli 2021|
|Microsoft PHP-Treiber 3.2 für SQL Server|3.2|9\. März 2020|
| &nbsp; | &nbsp; | &nbsp; |

Die folgenden Microsoft PHP-Treiber werden nicht mehr unterstützt.

|Treibername|Version des Treiberpakets|Ende des grundlegenden Supports|
|-|:-:|-|
|Microsoft PHP-Treiber 3.1 für SQL Server|3.1|12. Dezember 2019|
|Microsoft PHP-Treiber 3.0 für SQL Server|3.0|6\. März 2017|
|Microsoft PHP-Treiber 2.0 für SQL Server|2.0|10. August 2015|
|Microsoft PHP-Treiber 1.0 für SQL Server|1.0|28. August 2014|
| &nbsp; | &nbsp; | &nbsp; |

## <a name="sql-server-version-certified-compatibility"></a>Zertifizierte Kompatibilität mit SQL Server-Version
 In der folgenden Matrix sind Datenbankversionen aufgelistet, die als kompatibel mit der entsprechenden Treiberversion getestet und zertifiziert wurden. Wir streben an, die Abwärtskompatibilität mit früheren Treiberversionen aufrechtzuerhalten, aber nur der neueste unterstützte Treiber wird mit neuen SQL Server-Versionen getestet und zertifiziert, wenn diese veröffentlicht werden.

|Treiberversion&nbsp;&#8594;<br />&#8595; Datenbankversion|5.8|5.6|5.3|5,2|4.3|4,0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Azure SQL-Datenbank        |Ja|Ja|Ja|Ja|Ja|   |   |
|Verwaltete Azure SQL-Instanz|Ja|Ja|Ja|Ja|Ja|   |   |
|Azure Synapse Analytics   |Ja|Ja|Ja|Ja|Ja|   |   |
|SQL Server 2019           |Ja|   |   |   |   |   |   |
|SQL Server 2017           |Ja|Ja|Ja|Ja|Ja|   |   |
|SQL Server 2016           |Ja|Ja|Ja|Ja|Ja|Ja|   |
|SQL Server 2014           |Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|SQL Server 2012           |Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|SQL Server 2008 R2        |   |Ja|Ja|Ja|Ja|Ja|Ja|
|SQL Server 2008           |   |   |   |   |   |Ja|Ja|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

Weitere Informationen zur Verwendung von PHP mit Azure SQL-Datenbank finden Sie unter [Herstellen einer Verbindung mit einer Microsoft Azure SQL-Datenbank](connecting-to-microsoft-azure-sql-database.md).

## <a name="php-version-support"></a>Unterstützung von PHP-Versionen

Die folgenden PHP-Versionen werden mit der aufgelisteten Version der Microsoft PHP-Treiber unterstützt:

|Treiberversion&nbsp;&#8594;<br />&#8595; PHP-Version|5.8|5.6|5.3|5,2|4.3|4,0|3.2|
|:---:|---|---|---|---|---|---|---|
|7.4|7.4.0+          |                |                |                |       |        |        |
|7.3|7.3.0+          |7.3.0+          |                |                |       |        |        |
|7.2|7.2+<sup>1</sup>|7.2+<sup>1</sup>|7.2+<sup>1</sup>|7.2+<sup>1</sup>|       |        |        |
|7.1|                |7.1.0+          |7.1.0+          |7.1.0+          |7.1.0+ |        |        |
|7.0|                |                |7.0.0+          |7.0.0+          |7.0.0+ |7.0.0+  |        |
|5.6|                |                |                |                |       |        |5.6.4+  |
|5.5|                |                |                |                |       |        |5.5.16+ |
|5.4|                |                |                |                |       |        |5.4.32  |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

1. Versionen 7.2.1 und höher werden unter Windows unterstützt, während Versionen 7.2.0 und höher unter Linux und macOS unterstützt werden.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Die folgenden Versionen des Windows-Betriebssystems werden mit der aufgelisteten Version der Microsoft PHP-Treiber unterstützt:

|Treiberversion&nbsp;&#8594;<br />&#8595; Betriebssystem|5.8|5.6|5.3|5,2|4.3|4,0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Windows Server 2019                 |Ja|Ja|   |   |   |   |   |
|Windows Server 2016                 |Ja|Ja|Ja|Ja|Ja|   |   |
|Windows Server 2012 R2              |Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|Windows Server 2012                 |Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|Windows Server 2008 R2 SP1          |   |   |   |   |   |Ja|Ja|
|Windows Server 2008 R2              |   |   |   |   |   |   |   |
|Windows Server 2008 SP2             |   |   |   |   |   |Ja|Ja|
|Windows 10                          |Ja|Ja|Ja|Ja|Ja|Ja|   |
|Windows 8.1                         |Ja|Ja|Ja|Ja|Ja|Ja|Ja|
|Windows 8                           |   |   |   |   |Ja|Ja|Ja|
|Windows 7 SP1                       |   |   |   |   |   |Ja|Ja|
|Windows Vista SP2                   |   |   |   |   |   |Ja|Ja|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

Die folgenden Versionen des Linux- und macOS-Betriebssystems (nur 64-Bit) werden mit der aufgelisteten Version der Microsoft PHP-Treiber unterstützt:

|Treiberversion&nbsp;&#8594;<br />&#8595; Betriebssystem|5.8|5.6|5.3|5,2|4.3|4,0|3.2|
|--|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Ubuntu 20.04 (64 Bit)               |Ja|   |   |   |   |   |   |
|Ubuntu 19.10 (64-Bit)               |Ja|   |   |   |   |   |   |
|Ubuntu 18.10 (64 Bit)               |   |Ja|   |   |   |   |   |
|Ubuntu 18.04 (64 Bit)               |Ja|Ja|Ja|   |   |   |   |
|Ubuntu 17.10 (64 Bit)               |   |   |Ja|Ja|   |   |   |
|Ubuntu 16.04 (64 Bit)               |Ja|Ja|Ja|Ja|Ja|Ja|   |
|Ubuntu 15.10 (64 Bit)               |   |   |   |   |Ja|   |   |
|Ubuntu 15.04 (64 Bit)               |   |   |   |   |   |Ja|   |
|Debian 10 (nur 64-Bit)                  |Ja|   |   |   |   |   |   |
|Debian 9 (nur 64-Bit)                   |Ja|Ja|Ja|Ja|   |   |   |
|Debian 8 (nur 64-Bit)                   |Ja|Ja|Ja|Ja|Ja|   |   |
|Red Hat Enterprise Linux 8 (64-Bit) |Ja|   |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64-Bit) |Ja|Ja|Ja|Ja|Ja|Ja|   |
|Suse Enterprise Linux 15 (64-Bit)   |Ja|Ja|   |   |   |   |   |
|Suse Enterprise Linux 12 (64-Bit)   |Ja|Ja|Ja|Ja|   |   |   |
|Alpine Linux 3.11 (64-Bit)<sup>1</sup>|Ja|   |   |   |   |   |   |
|macOS Catalina (64-Bit)             |Ja|   |   |   |   |   |   |
|macOS Mojave (64-Bit)               |Ja|Ja|   |   |   |   |   |
|macOS High Sierra (64-Bit)          |Ja|Ja|Ja|   |   |   |   |
|macOS Sierra (64-Bit)               |   |Ja|Ja|Ja|Ja|   |   |
|macOS El Capitan (64-Bit)           |   |   |Ja|Ja|Ja|   |   |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

<sup>1</sup> Experimentelle Unterstützung von Alpine Linux in Version 5.80. Produktionssupport seit Version 5.8.1.

## <a name="see-also"></a>Weitere Informationen

[Versionsanmerkungen](release-notes-php-sql-driver.md)

[Supportressourcen](support-resources-for-the-php-sql-driver.md)

[Systemanforderungen](system-requirements-for-the-php-sql-driver.md)
