---
title: Microsoft Drivers for PHP for SQLServer-Supportmatrix | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: genemi
manager: ''
ms.openlocfilehash: 0790d2cc0497ef2912f96cd4679e4541fc9b2262
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63180272"
---
# <a name="microsoft-php-drivers-for-sql-server-support-matrix"></a>Microsoft PHP-Treiber für SQL Server-Supportmatrix

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Auf dieser Seite finden Sie die Unterstützungsmatrix und die Support Lifecycle-Richtlinie für die Microsoft PHP-Treiber für SQL Server.

## <a name="microsoft-php-drivers-support-lifecycle-matrix-and-policy"></a>Microsoft PHP Treiber Unterstützungsmatrix und Support Lifecycle-Richtlinie

Die Microsoft Support Lifecycle-Richtlinie (MLS) bietet transparente, vorhersagbare Informationen hinsichtlich der Supportdauer bei Microsoft-Produkten. Für die Versionen 3.x, 4.x und 5.x des PHP-Treibers wird ab dem Veröffentlichungsdatum fünf Jahre grundlegender Support (Mainstream-Support) geleistet. Die Definition für den grundlegenden Support finden Sie auf der [Website der Microsoft Support Lifecycle-Richtlinie](https://support.microsoft.com/lifecycle).

Erweiterte und benutzerdefinierte Support-Optionen sind für die Microsoft PHP-Treiber nicht verfügbar.

Die folgenden Microsoft PHP-Treiber werden bis zum angegebenen Supportende unterstützt.

|Treibername|Version des Treiberpakets|Ende des grundlegenden Supports|
|-|:-:|-|
|Microsoft PHP-Treiber 5.6 für SQL Server|5.6|21. Februar 2024|
|Microsoft PHP-Treiber 5.3 für SQL Server|5.3|20. Juli 2023|
|Microsoft PHP-Treiber 5.2 für SQL Server|5.2|9\. Februar 2023|
|Microsoft PHP-Treiber 4.3 für SQL Server|4.3|6\. Juli 2022|
|Microsoft PHP-Treiber 4.0 für SQL Server|4.0|11. Juli 2021|
|Microsoft PHP-Treiber 3.2 für SQL Server|3.2|9 März 2020|
|Microsoft PHP-Treiber 3.1 für SQL Server|3.1|12. Dezember 2019|
| &nbsp; | &nbsp; | &nbsp; |

Die folgenden Microsoft PHP-Treiber werden nicht mehr unterstützt.

|Treibername|Version des Treiberpakets|Ende des grundlegenden Supports|
|-|:-:|-|
|Microsoft PHP-Treiber 3.0 für SQL Server|3.0|6\. März 2017|
|Microsoft PHP-Treiber 2.0 für SQL Server|2.0|Am 10. August 2015|
|Microsoft PHP-Treiber 1.0 für SQL Server|1,0|28. August 2014|
| &nbsp; | &nbsp; | &nbsp; |

## <a name="sql-server-version-certified-compatibility"></a>SQL Server-Version, die Zertifizierung der Kompatibilität
 Die folgende Matrix enthält SQL Server-Versionen, die getestet und als kompatibel mit der entsprechenden Treiberversion zertifiziert wurden. Wir bemühen uns um die Abwärtskompatibilität mit vorherigen Treiberversionen, aber nur die neueste unterstützte Treiber wird getestet und zertifiziert mit neuen Versionen von SQL Server wie SQL Server veröffentlicht wird.

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595; SQL Server-Version|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3.0|2.0|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Verwaltete Azure SQL-Instanz<br/> (Die private Vorschau wurde verlängert)|J|J|J|J| | | | | |
|Azure SQL Data Warehouse|J|J|J|J| | | | | |
|SQL Server 2017         |J|J|J|J| | | | | |
|SQL Server 2016         |J|J|J|J|J| | | | |
|SQLServer 2014         |J|J|J|J|J|J|J| | |
|SQL Server 2012         |J|J|J|J|J|J|J|J| |
|SQL Server 2008 R2      |J|J|J|J|J|J|J|J|J|
|SQL Server 2008         | | | | |J|J|J|J|J|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="php-version-support"></a>Unterstützung von PHP-Versionen

Die folgenden Versionen von PHP werden mit die aufgeführte Version von Microsoft PHP-Treiber unterstützt:

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595; PHP-Version|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3.0|2.0|
|:---:|---|---|---|---|---|---|---|---|---|
|7.3|7.3.0+          |                |                |       |       | | | | |
|7.2|7.2+<sup>1</sup>|7.2+<sup>1</sup>|7.2+<sup>1</sup>|       |       | | | | |
|7.1|7.1.0+          |7.1.0+          |7.1.0+          |7.1.0+ |       |        |        |        |        |
|7.0|                |7.0.0+          |7.0.0+          |7.0.0+ |7.0.0+ |        |        |        |        |
|5.6|                |                |                |       |       |5.6.4+  |        |        |        |
|5.5|                |                |                |       |       |5.5.16+ |5.5.16+ |        |        |
|5.4|                |                |                |       |       |5.4.32  |5.4.32  |5.4.32  |        |
|5.3|                |                |                |       |       |        |        |5.3.0   |5.3.0   |
|5.2|                |                |                |       |       |        |        |        |5.2.4<br />5.2.13|
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

1. Versionen 7.2.1 und höher auf Windows, unterstützt werden, während Versionen 7.2.0 und höher unter Linux und MacOS unterstützt.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Die folgenden Versionen des Windows-Betriebssystem werden mit die aufgeführte Version von Microsoft PHP-Treiber unterstützt:

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595; Betriebssystem|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3.0|2.0|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Windows Server 2016                 |J  |J  |J  |J  |   |   |   |   |   |
|Windows Server 2012 R2              |J  |J  |J  |J  |J  |J  |J  |   |   |
|Windows Server 2012                 |J  |J  |J  |J  |J  |J  |J  |   |   |
|Windows Server 2008 R2 SP1          |   |   |   |   |J  |J  |J  |J  |   |
|Windows Server 2008 R2              |   |   |   |   |   |   |   |   |J  |
|Windows Server 2008 SP2             |   |   |   |   |J  |J  |J  |J  |   |
|Windows Server 2008                 |   |   |   |   |   |   |   |   |J  |
|Windows Server 2003 SP1             |   |   |   |   |   |   |   |   |J  |
|Windows 10                          |J  |J  |J  |J  |J  |   |   |   |   |
|Windows 8.1                         |J  |J  |J  |J  |J  |J  |J  |   |   |
|Windows 8                           |   |   |   |J  |J  |J  |J  |   |   |
|Windows 7 SP1                       |   |   |   |   |J  |J  |J  |J  |   |
|Windows Vista SP2                   |   |   |   |   |J  |J  |J  |J  |J  |
|Windows XP SP3                      |   |   |   |   |   |   |   |   |J  |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

Die folgenden Linux und Mac-Betriebssystemversionen (nur 64-Bit) werden mit die aufgeführte Version von Microsoft PHP-Treiber unterstützt:

|PHP für SQL Server-Treiberversion&#8594;<br />&#8595; Betriebssystem|5.6|5.3|5.2|4.3|4.0|3.2|3.1|3.0|2.0|
|--|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Ubuntu 18.10 (64 Bit)               |J  |   |   |   |   |   |   |   |   |
|Ubuntu 18.04 (64 Bit)               |J  |J  |   |   |   |   |   |   |   |
|Ubuntu 17.10 (64 Bit)               |   |J  |J  |   |   |   |   |   |   |
|Ubuntu 16.04 (64 Bit)               |J  |J  |J  |J  |J  |   |   |   |   |
|Ubuntu 15.10 (64 Bit)               |   |   |   |J  |   |   |   |   |   |
|Ubuntu 15.04 (64 Bit)               |   |   |   |   |J  |   |   |   |   |
|Debian 9 (64-Bit)                   |J  |J  |J  |   |   |   |   |   |   |
|Debian 8 (64-Bit)                   |J  |J  |J  |J  |   |   |   |   |   |
|Red Hat Enterprise Linux 7 (64-Bit) |J  |J  |J  |J  |J  |   |   |   |   |
|SuSE Enterprise Linux 15 (64-Bit)   |J  |   |   |   |   |   |   |   |   |
|SuSE Enterprise Linux 12 (64-Bit)   |J  |J  |J  |   |   |   |   |   |   |
|MacOS Mojave (64-Bit)               |J  |   |   |   |   |   |   |   |   |
|MacOS High Sierra (64-Bit)          |J  |J  |   |   |   |   |   |   |   |
|MacOS Sierra (64-Bit)               |J  |J  |J  |J  |   |   |   |   |   |
|MacOS El Capitan (64-Bit)           |   |J  |J  |J  |   |   |   |   |   |
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |

## <a name="see-also"></a>Weitere Informationen

[Versionsanmerkungen](../../connect/php/release-notes-php-sql-driver.md)

[Supportressourcen](../../connect/php/support-resources-for-the-php-sql-driver.md)

[Systemanforderungen](../../connect/php/system-requirements-for-the-php-sql-driver.md)
