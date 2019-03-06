---
title: Anmerkungen zu dieser Version – Microsoft ODBC Driver for SQL Server unter Linux und macOS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/29/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 12f45cd1014a312eec7854685d8c7fe2e64b9714
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662754"
---
# <a name="release-notes-for-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Versionshinweise zu Microsoft ODBC Driver for SQL Server unter Linux und macOS
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS

**Neue unterstützte Distributionen**: 15 von SuSE, Ubuntu-18.10 MacOS 10.14

**Funktionen, die hinzugefügt**:

- Azure Active Directory verwalteten Dienstidentität (System und Benutzer zugewiesen) den Authentifizierungsmodus
- AE-Eingabeparameter streaming
- XA DTC

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS

**Neue unterstützte Distributionen**: Ubuntu 18.04

**Funktionen, die hinzugefügt**:

Datenklassifizierung für Azure SQL-Datenbank und SQL Server, Weitere Informationen finden Sie unter [Klassifizierung von Daten](../data-classification.md)

Unterstützung von UTF-8-Codierung-server

SQLBrowseConnect

Dynamische Abhängigkeit `libcurl`:
- Ab dieser Version, die `libcurl` Paket ist kein expliziter Abhängigkeiten. Die `libcurl` -Paket für OpenSSL oder NSS erforderlich ist, wenn Sie Azure Key Vault oder Azure Active Directory-Authentifizierung verwenden. Wenn ein Fehler aufgetreten ist im Hinblick auf `libcurl`, sicherzustellen, dass es installiert ist.

Idle Connection Resiliency mit ConnectRetryCount und ConnectRetryInterval Schlüsselwörtern in der Verbindungszeichenfolge angegeben (Weitere Informationen finden Sie unter [Verbindungsresilienz im Windows ODBC-Treiber](../windows/connection-resiliency-in-the-windows-odbc-driver.md)):
- Verwendung `SQL_COPT_SS_CONNECT_RETRY_COUNT`(schreibgeschützt) zum Abrufen der Anzahl der Verbindungsversuche.
- Verwendung `SQL_COPT_SS_CONNECT_RETRY_INTERVAL`(schreibgeschützt) zum Abrufen der Länge des Intervalls für Verbindungsversuche.
- Verbindung wird standardmäßig einmal wiederholt.


[Behebung von Programmfehlern](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS

**Funktionen, die hinzugefügt**:

Unterstützung für `SQL_COPT_SS_CEKCACHETTL` und `SQL_COPT_SS_TRUSTEDCMKPATHS` Verbindungsattribute (Weitere Informationen finden Sie unter [Using Always Encrypted, mit dem ODBC-Treiber für SQL Server](../using-always-encrypted-with-the-odbc-driver.md))
- `SQL_COPT_SS_CEKCACHETTL` Ermöglicht das Steuern der Zeit, die der lokale Cache von Spaltenverschlüsselungsschlüsseln vorhanden ist, sowie es leeren
- `SQL_COPT_SS_TRUSTEDCMKPATHS` Ermöglicht es der Anwendung zum Einschränken der AE-Vorgänge, um nur die angegebene Liste der Spaltenhauptschlüssel verwenden



Unterstützung für das Laden der `.rll` aus Standardspeicherort (Weitere Informationen finden Sie unter [das Dokument für die Installation im Abschnitt "Ressourcen-Datei laden"](installing-the-microsoft-odbc-driver-for-sql-server.md#resource-file-loading))

[Behebung von Programmfehlern](../bug-fixes.md)



## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS

**Neue unterstützte Distributionen**: MacOS High Sierra und Ubuntu 17.10 

**Leistungsverbesserungen**: größer als 10 x leistungsverbesserung beim konvertiert der Treiber in und aus UTF-8/16.

**Funktionen, die hinzugefügt**:

Unterstützung von Always Encrypted für BCP-API

Neues Verbindungszeichenfolgen-Attribut UseFMTOnly bewirkt, dass ältere Metadaten in besonderen Fällen erfordern der temporäre Tabellen zu verwendenden Treiber.

Unterstützung für verwaltete Azure SQL-Instanz (Erweiterte Private Vorschau). 
> [!NOTE]
> Es gibt eine Reihe von Unterschieden bei Verwendung einer verwalteten Instanz:
> -   FILESTREAM wird nicht unterstützt. 
> -   Lokalen Dateisystem Zugriff wird nicht unterstützt, aber für Dinge wie Tracefiles erforderlich 
> -   Erstellen von UDTS aus lokalen Pfad wird nicht unterstützt. 
> -   Integrierte Windows-Authentifizierung wird nicht unterstützt. 
> -   DTC wird nicht unterstützt. 
> -   Konto "sa" ist nicht vorhanden (Standardkonto wird als "CloudSA" bezeichnet)
> -   TDS-token-Fehler (0xAA) gibt falsche Server-Namen zurück.
> -   Sonderzeichen im Datenbanknamen werden nicht unterstützt. 
> -   ALTER DATABASE [dbname1] MODIFY NAME = [dbname2] wird nicht unterstützt.
> -   Die Fehlermeldungen werden immer in englischer Sprache angezeigt, unabhängig von der Sprache Einstellungen (identisch mit Azure) 

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversion-mdmd-on-linux-and-macos"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux und macOS  

ODBC-Treiber 13.1 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bietet Unterstützung für Always Encrypted und Azure Active Directory bei der Verwendung in Verbindung mit Microsoft SQL Server 2016.

**Neue unterstützte Distributionen**: OS X 10.11 und MacOS 10.12 werden in der ersten Version des ODBC-Treibers unter MacOS unterstützt. Ubuntu 16.10 wird jetzt auch unterstützt, zusammen mit Red Hat 6, 7 und SUSE 12. Jede Plattform gibt es eine Plattform relevanten-Paket (RPM oder DEB), Installation und Konfiguration zu vereinfachen.  Finden Sie unter [der Treiberinstallation](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) installationsanweisungen.

**UnixODBC 2.3.1-Treiber-Manager-Unterstützungsänderungen**: die ODBC-Treiber hängt benutzerdefinierte Pakete für den UnixODBC Treiber-Manager nicht mehr (außer auf Red Hat 6), und stattdessen verwendet der Verteilungs-Paket-Manager, der UnixODBC-Abhängigkeit aufzulösen von der Distribution-Repositorys.

**BCP-API-Unterstützung**: die Linux und MacOS-ODBC-Treiber unterstützt jetzt die Verwendung von der [BCP-API-Funktionen (**Bcp_init**usw..)](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)

## <a name="whats-new-in-the-microsoft-odbc-driver-130-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Neuigkeiten in Microsoft ODBC Driver 13.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux  
Microsoft ODBC Driver 13.0 für SQL Server werden SQL Server 2014 und SQL Server 2016 jetzt ebenfalls unterstützt.  

**Neue unterstützte Distributionen**:

Ubuntu wird jetzt zusammen mit Red Hat und SUSE unterstützt. Jede Plattform gibt es eine Plattform relevanten-Paket (RPM oder DEB), Installation und Konfiguration zu vereinfachen.  Finden Sie unter [der Treiberinstallation](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md) installationsanweisungen.

**UnixODBC 2.3.1-Treiber-Manager-Unterstützung**: Zusätzlich zu einer neueren Treiber-Manager ist auch ein Paket für die Installation von dieser Abhängigkeit, die die Installation und Konfiguration vereinfacht.  

**Transparente Netzwerk-IP-Adressauflösung**: Transparente Netzwerk-IP-Adressauflösung ist eine Überarbeitung der vorhandenen Multisubnetz-Failover-Funktion, die der Verbindungssequenz des Treibers im Fall wirkt sich auf, in denen die erste behoben IP-Adresse den Hostnamen nicht, reagieren, und es gibt mehrere IP-Adressen, die den Hostnamen zugeordnet.

**TLS 1.2-Unterstützung**: der Microsoft ODBC Driver 13.0 for SQL Server unter Linux unterstützt nun TLS 1.2, wenn die sichere Kommunikation mit SQL Server verwendet werden.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversion-mdmd-on-linux"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Linux  
Der ODBC-Treiber unter SUSE Linux (Preview) unterstützt das 64-Bit-SUSE Linux Enterprise 11 Service Pack 2. Weitere Informationen finden Sie unter [System Requirements](../../../connect/odbc/linux-mac/system-requirements.md).  

Der ODBC-Treiber unter Linux unterstützt [!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]. Weitere Informationen finden Sie unter [ODBC-Treiber unter Linux-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md).  

Der ODBC-Treiber unter Linux unterstützt Verbindungen mit Microsoft Azure SQL-Datenbanken. Weitere Informationen finden Sie unter [Gewusst wie: Verbinden mit Microsoft Azure SQL-Datenbank mithilfe von ODBC](https://msdn.microsoft.com/library/hh974312.aspx).  

Die `-l` Option (Anmeldungstimeout) hinzugefügt wurde `bcp`. Weitere Informationen finden Sie unter [Connecting with **bcp** (Herstellen einer Verbindung mit bcp)](../../../connect/odbc/linux-mac/connecting-with-bcp.md).
