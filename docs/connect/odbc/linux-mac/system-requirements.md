---
title: Systemanforderungen (ODBC-Treiber für SQL Server)
description: In diesem Artikel werden die Systemanforderungen für den ODBC-Treiber für SQL Server für Linux und macOS-Betriebssysteme aufgeführt.
ms.custom: ''
ms.date: 08/06/2020
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
ms.openlocfilehash: 74b7bf1680dd956dfca85917939ad24a3559d7de
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934459"
---
# <a name="system-requirements-linux-and-macos"></a>Systemanforderungen (Linux und macOS)

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel werden die Anforderungen für die Verwendung von [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS aufgelistet.

## <a name="sql-version-compatibility"></a>SQL-Versionskompatibilität

Die Kompatibilität der Treiber unter Linux und macOS mit der SQL-Version ist identisch mit der [SQL-Versionskompatibilität unter Windows](../windows/system-requirements-installation-and-driver-files.md#sql-version-compatibility).

## <a name="operating-system-support"></a>Betriebssystemunterstützung

Die Versionen 17, 13.1 und 13 der Linux- und macOS-Treiber werden für die x64-Architektur der folgenden Betriebssysteme unterstützt:

|Treiberversion&nbsp;&#8594;<br />&#8595; Betriebssystem     |17.6|17,5|17.4|17.3|17.2|17.1|17.0|Version 13.1|13|
|-------------------------------|----|----|----|----|----|----|----|----|---|
|Apple OS X 10.11 (El Capitan)  |    |    |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Apple macOS 10.12 (Sierra)     |    |    |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Apple macOS 10.13 (High Sierra)|Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Apple macOS 10.14 (Mojave)     |Ja |Ja |Ja |Ja |    |    |    |    |   |
|Apple macOS 10.15 (Catalina)   |Ja |Ja |    |    |    |    |    |    |   |
|Alpine Linux 3.11              |Ja |Ja |    |    |    |    |    |    |   |
|Debian Linux 8                 |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Debian Linux 9                 |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Debian Linux 10                |Ja |Ja |Ja |    |    |    |    |    |   |
|Oracle Linux 8                 |Ja |Ja |    |    |    |    |    |    |   |
|Red Hat Enterprise Linux 6      |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Red Hat Enterprise Linux 7      |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Red Hat Enterprise Linux 8      |Ja |Ja |Ja |    |    |    |    |    |   |
|SUSE Linux Enterprise Server 11<sup>1</sup>|Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|SUSE Linux Enterprise Server 12|Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|SUSE Linux Enterprise Server 15|Ja |Ja |Ja |Ja |    |    |    |    |   |
|Ubuntu Linux 14.04             |    |    |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Ubuntu Linux 16.04             |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja |Ja|
|Ubuntu Linux 18.04             |Ja |Ja |Ja |Ja |Ja |    |    |    |   |
|Ubuntu Linux 20.04             |Ja |    |    |    |    |    |    |    |   |

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
