---
title: Systemanforderungen (ODBC-Treiber für SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/15/2018
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2b4aca8fcd4f18f6e70c9e6f98b415402e19621
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59042319"
---
# <a name="system-requirements"></a>Systemanforderungen
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel werden die Anforderungen für die Verwendung von [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS aufgelistet.


## <a name="microsoft-odbc-driver-13-131-and-17-for-sql-server"></a>Microsoft ODBC Driver 13, 13.1, 17 for SQL Server

Die Linux und macOS-Treiber sind nur für die 64-Bit-Versionen der folgenden Betriebssysteme verfügbar:

|Betriebssystem|Unterstützte Treiberversionen|
|------------------------------------|--------------------------------|
|Apple OS X 10.11 (El Capitan)|13, 13.1, 17|
|Apple macOS 10.12 (Sierra)|13, 13.1, 17|
|Apple macOS 10.13 (High Sierra)|17| 
|Apple macOS 10.14 (Mojave)|17| 
|Debian Linux 8|13, 13.1, 17|
|Debian Linux 9|17|
|Red Hat Enterprise Linux 6|13, 13.1, 17|
|Red Hat Enterprise Linux 7|13, 13.1, 17|
|SUSE Linux Enterprise Server 11|13, 13.1, 17 <br /><br /> **HINWEIS:** Der ODBC-Treiber 17 unterstützt nur SuSE Linux Enterprise Server 11 SP4.|
|SUSE Linux Enterprise Server 12|13, 13.1, 17|
|SUSE Linux Enterprise Server 15|17|
|Ubuntu Linux 14.04|13, 13.1, 17|
|Ubuntu Linux 15.10|13, 13.1|
|Ubuntu Linux 16.04|13, 13.1, 17|
|Ubuntu Linux 16.10|13, 13.1|
|Ubuntu Linux 17.04|17| 
|Ubuntu Linux 17.10|17|
|Ubuntu Linux 18.04|17| 
|Ubuntu Linux 18.10|17| 

Die Installationspakete für die [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC-Treiber 13, 13.1, und 17 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS lösen die Abhängigkeiten des Treibers bei der Installation mithilfe des Paketverwaltungssystems Ihrer Verteilung automatisch auf, wie in [Installing the Driver (Installieren des Treibers)](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) beschrieben.

## <a name="microsoft-odbc-driver-11-for-sql-server"></a>Microsoft ODBC Driver 11 für SQL Server  
  
-   64-Bit UnixODBC 2.3.0 Treiber-Manager, der für 64-Bit SQLLEN/SQLULEN erstellt wurde. Höhere Versionen des 64-Bit UnixODBC-Treiber-Managers werden nicht vom ODBC-Treiber unter Linux unterstützt. Weitere Informationen finden Sie unter [Installing the Driver Manager](../../../connect/odbc/linux-mac/installing-the-driver-manager.md) .  
  
-   Der ODBC-Treiber für **Red Hat Enterprise Linux 5 (64-Bit)** erfordert die folgenden Pakete und kann hier heruntergeladen werden: [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321).  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `e2fsprogs-libs`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Der ODBC-Treiber für **Red Hat Enterprise Linux 6 (64-Bit)** erfordert die folgenden Pakete und kann hier heruntergeladen werden: [Microsoft ODBC Driver 11 for SQL Server – Red Hat Linux](https://go.microsoft.com/fwlink/?LinkId=267321).  
    -   `glibc`  
    -   `libgcc`  
    -   `libstdc++`  
    -   `libuuid`  
    -   `krb5-libs`  
    -   `openssl`  
  
-   Der ODBC-Treiber für **SUSE Linux Enterprise 11 Service Pack 2 (64-Bit)** erfordert die folgenden Pakete und kann hier heruntergeladen werden: [Microsoft ODBC Driver 11 Preview for SQL Server – SUSE Linux](https://go.microsoft.com/fwlink/?LinkId=264916).  
    -   `glibc`  
    -   `libstdc++46`  
    -   `libgcc46`  
    -   `libuuid1`  
    -   `krb5`  
    -   `libopenssl0_9_8`  
  
## <a name="see-also"></a>Weitere Informationen
[Installieren des Treiber-Managers](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[Bekannte Probleme in dieser Version des Treibers](../../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)  

[Versionsanmerkungen](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)  
