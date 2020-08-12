---
title: Systemanforderungen (ODBC-Treiber für SQL Server)
description: In diesem Artikel werden die Systemanforderungen für den ODBC-Treiber für SQL Server für Linux und macOS-Betriebssysteme aufgeführt.
ms.custom: ''
ms.date: 03/18/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- prerequisites
- system requirements
- requirements
ms.assetid: f03b7fdd-0e9d-4e74-958d-e8c87e027348
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01a5dd44d111fd72d76db244c8135d3bdde00ec8
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391755"
---
# <a name="system-requirements-linux-and-macos"></a>Systemanforderungen (Linux und macOS)

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel werden die Anforderungen für die Verwendung von [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS aufgelistet.

## <a name="sql-version-compatibility"></a>SQL-Versionskompatibilität

Die Kompatibilität der Treiber unter Linux und macOS mit der SQL-Version ist identisch mit der [SQL-Versionskompatibilität unter Windows](../windows/system-requirements-installation-and-driver-files.md#sql-version-compatibility).

## <a name="operating-system-support"></a>Betriebssystemunterstützung

Die Versionen 17, 13.1 und 13 der Linux- und macOS-Treiber werden für die x64-Architektur der folgenden Betriebssysteme unterstützt:

|Unterstützte Betriebssysteme     |17,5|17.4|17.3|17.2|17.1|17.0|Version 13.1|13|
|-------------------------------|----|----|----|----|----|----|----|--|
|Apple OS X 10.11 (El Capitan)  | |J|J|J|J|J|J|J|
|Apple macOS 10.12 (Sierra)     | |J|J|J|J|J|J|J|
|Apple macOS 10.13 (High Sierra)|J|J|J|J|J|J|J|J|
|Apple macOS 10.14 (Mojave)     |J|J|J| | | | | |
|Apple macOS 10.15 (Catalina)   |J| | | | | | | |
|Alpine Linux 3.11              |J| | | | | | | |
|Debian Linux 8                 | |J|J|J|J|J|J|J|
|Debian Linux 9                 |J|J|J|J|J|J|J|J|
|Debian Linux 10                |J|J| | | | | | |
|Oracle Linux 8                 |J| | | | | | | |
|Red Hat Enterprise Linux 6      |J|J|J|J|J|J|J|J|
|Red Hat Enterprise Linux 7      |J|J|J|J|J|J|J|J|
|Red Hat Enterprise Linux 8      |J|J| | | | | | |
|SUSE Linux Enterprise Server 11<sup>1</sup>|J|J|J|J|J|J|J|J|
|SUSE Linux Enterprise Server 12|J|J|J|J|J|J|J|J|
|SUSE Linux Enterprise Server 15|J|J|J| | | | | |
|Ubuntu Linux 14.04             | |J|J|J|J|J|J|J|
|Ubuntu Linux 16.04             |J|J|J|J|J|J|J|J|
|Ubuntu Linux 18.04             |J|J|J|J| | | | |
|Ubuntu Linux 19.10             |J| | | | | | | |

<sup>1</sup> ODBC Driver 17 unterstützt nur SUSE Linux Enterprise Server 11 SP4.

Die Installationspakete für die [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC-Treiber 13, 13.1, und 17 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS lösen die Abhängigkeiten des Treibers bei der Installation mithilfe des Paketverwaltungssystems Ihrer Verteilung automatisch auf, wie unter [Installation von Microsoft ODBC Driver for SQL Server (Linux)](installing-the-microsoft-odbc-driver-for-sql-server.md) und [Installation von Microsoft ODBC Driver for SQL Server (macOS)](install-microsoft-odbc-driver-sql-server-macos.md) beschrieben.

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 für SQL Server  
  
* 64-Bit UnixODBC 2.3.0 Treiber-Manager, der für 64-Bit SQLLEN/SQLULEN erstellt wurde. Höhere Versionen des 64-Bit UnixODBC-Treiber-Managers werden nicht vom ODBC-Treiber unter Linux unterstützt. Weitere Informationen finden Sie unter [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) .  
  
* Der ODBC-Treiber für **Red Hat Enterprise Linux 5 (64-Bit)** erfordert die folgenden Pakete und kann hier heruntergeladen werden: [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321).  
  * `glibc`  
  * `libgcc`  
  * `libstdc++`  
  * `e2fsprogs-libs`  
  * `krb5-libs`  
  * `openssl`  
  
* Der ODBC-Treiber für **Red Hat Enterprise Linux 6 (64-Bit)** erfordert die folgenden Pakete und kann hier heruntergeladen werden: [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321).  
  * `glibc`  
  * `libgcc`  
  * `libstdc++`  
  * `libuuid`  
  * `krb5-libs`  
  * `openssl`  
  
* Der ODBC-Treiber für **SUSE Linux Enterprise 11 Service Pack 2 (64-Bit)** erfordert die folgenden Pakete und kann hier heruntergeladen werden: [Microsoft ODBC Driver 11 Preview for SQL Server – SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916).  
  * `glibc`  
  * `libstdc++46`  
  * `libgcc46`  
  * `libuuid1`  
  * `krb5`  
  * `libopenssl0_9_8`  
  
## <a name="see-also"></a>Weitere Informationen

[Installieren des Treiber-Managers](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)  
[Bekannte Probleme in dieser Version des Treibers](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  
[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  
