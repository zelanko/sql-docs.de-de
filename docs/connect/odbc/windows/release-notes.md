---
title: Versionshinweise (OLE DB-Treiber für SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: cc1321ac161923499d57ab69374b8ed603d272e0
ms.sourcegitcommit: 2ab79765e51913f1df6410f0cd56bf2a13221f37
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2019
ms.locfileid: "56955771"
---
# <a name="release-notes"></a>Versionsanmerkungen
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Versionsanmerkungen für Microsoft ODBC Driver for SQL Server on Windows.  


## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-173-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Neuigkeiten beim [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows

**Funktionen, die hinzugefügt**:

- Azure Active Directory verwalteten Dienstidentität (System und Benutzer zugewiesene)-Authentifizierungsmodus, Weitere Informationen finden Sie unter [mithilfe von Azure Active Directory mit dem ODBC-Treiber](../using-azure-active-directory.md)
- Möglichkeit zum Streamen von Eingabeparametern für Always Encrypted-Spalten, Weitere Informationen finden Sie unter [Einschränkungen des ODBC-Treibers bei Verwendung von Always Encrypted](../using-always-encrypted-with-the-odbc-driver.md#limitations-of-the-odbc-driver-when-using-always-encrypted)
- Für verteilte XA-Transaktionen, für die Weitere Informationen finden Sie unter [mithilfe der XA-Transaktionen](../use-xa-with-dtc.md)

[Behebung von Programmfehlern](../bug-fixes.md)

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-172-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.2 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows

**Funktionen, die hinzugefügt**:

Datenklassifizierung für Azure SQL-Datenbank und SQL Server, Weitere Informationen finden Sie unter [Klassifizierung von Daten](../data-classification.md)

Unterstützung für UTF-8-Codierung-server

[Behebung von Programmfehlern](../bug-fixes.md)

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-171-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows

**Funktionen, die hinzugefügt**:

Unterstützung für `SQL_COPT_SS_CEKCACHETTL` und `SQL_COPT_SS_TRUSTEDCMKPATHS` Verbindungsattribute (Weitere Informationen finden Sie unter [Using Always Encrypted, mit dem ODBC-Treiber für SQL Server](../using-always-encrypted-with-the-odbc-driver.md))
- `SQL_COPT_SS_CEKCACHETTL` Ermöglicht das Steuern der Zeit, die der lokale Cache von Spaltenverschlüsselungsschlüsseln vorhanden ist, sowie es leeren
- `SQL_COPT_SS_TRUSTEDCMKPATHS` Ermöglicht es der Anwendung zum Einschränken der AE-Vorgänge, um nur die angegebene Liste der Spaltenhauptschlüssel verwenden


Unterstützung der interaktiven Azure Active Directory-Authentifizierung

[Behebung von Programmfehlern](../bug-fixes.md)


## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows

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
  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows  
 ODBC-Treiber 13.1 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bietet Unterstützung für [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) und [Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) bei Verwendung in Verbindung mit Microsoft SQL Server 2016.  Entsprechende Connection pooling Schlüsselwörter bzw. Attribute finden Sie unter [Treiber Aware Connection Pooling in der ODBC-Treiber für SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).

 ## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-13-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows  
 ODBC Driver 13 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vorherige Funktionalität von ODBC Driver 11 für SQL Server enthält, und bietet Unterstützung für Microsoft SQL Server 2016.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Neuigkeiten in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows  
 ODBC Driver 11 for SQL Server enthält einerseits neue [Features](./features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md) sowie andererseits sämtliche Features, die im Lieferumfang von ODBC in SQL Server 2012 Native Client enthalten sind.  
