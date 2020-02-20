---
title: Versionshinweise zu ODBC for SQL Server unter Windows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/27/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
ms.reviewer: v-chojas
author: v-makouz
ms.author: v-chojas
manager: kenvh
ms.openlocfilehash: c53832e40b055792d98b9bffea368d156d535545
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76910933"
---
# <a name="release-notes-for-odbc-to-sql-server-on-windows"></a>Release Notes for ODBC to SQL Server on Windows (Versionshinweise zu ODBC für SQL Server unter Windows)

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel mit Versionshinweisen werden die Neuerungen für Microsoft ODBC Driver for SQL Server unter Windows beschrieben.

<!--
PLEASE USE THE STANDARD 2-COLUMN TABLE FORMAT!

For all our Release Notes articles (What's New too?), we are standardizing on the 2-column format that you see here for version "## 17.3".

Going forward, all new additions to this article must use the 2-column format.

Also, use the shorter ## H2 title format, which eliminates all the redundant constants, and appends the date-added.
One beneift of shortness is the avoidance of the annoying wrapping of unnecessarily long H2 titles in the rightNav.
- OLD H2:  ## What's New in the [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 17.3 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Windows
- NEW H2:  ## 17.3, February 2019

By the way, in GitHub, the file name is changing today 2019/03/30:
- FROM:  docs/connect/odbc/windows/release-notes.md
- TO  :  docs/connect/odbc/windows/release-notes-odbc-sql-server-windows.md

Thank you.
GeneMi (and CraigG).  2019/03/30.
-->

## <a name="175-january-2020"></a>Version 17.5, Januar 2020

| Neues Feature | Details |
| :------------ | :------ |
| SQL_COPT_SS_SPID-Verbindungsattribut zum Abrufen der SPID ohne Roundtrip zum Server | Siehe [Schlüsselwörter und Attribute von DNS- und Verbindungszeichenfolgen](../dsn-connection-string-attribute.md) |
| Fehlerbehebungen. | Siehe [Fehlerbehebungen](../bug-fixes.md) |
| &nbsp; | &nbsp; |

## <a name="1742-october-2019"></a>17.4.2, Oktober 2019

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung für zusätzliche Azure Key Vault-Endpunkte | Siehe [Verwenden von Always Encrypted mit dem ODBC-Treiber](../using-always-encrypted-with-the-odbc-driver.md). |
| Unterstützung für das Festlegen der Datenklassifizierungsversion | Siehe [Data Classification (Datenklassifizierung)](../data-classification.md#bkmk-version) |
| Die Active Directory-Authentifizierungsbibliothek (adal.dll) wurde zum Installer hinzugefügt | Dieses Feature ist nun Teil der Installation des Basistreibers. Dadurch wird ein Upgrade für bestehende Installationen der Microsoft Active Directory-Authentifizierungsbibliothek für SQL Server durchgeführt und die Bibliothek wird aus der Liste mit installierten Anwendung in Windows entfernt. |
| Fehlerbehebungen. | Siehe [Fehlerbehebungen](../bug-fixes.md) |
| &nbsp; | &nbsp; |

## <a name="174-july-2019"></a>17.4, Juli 2019

| Neues Feature | Details |
| :------------ | :------ |
| Always Encrypted mit Secure Enclaves. | Siehe [Verwenden von Always Encrypted mit dem ODBC-Treiber](../using-always-encrypted-with-the-odbc-driver.md). |
| Konfigurierbare TCP-Keep-Alive-Einstellungen. | Siehe [Herstellen einer Verbindung mit SQL Server](../linux-mac/connection-string-keywords-and-data-source-names-dsns.md). |
| Fehlerbehebungen. | Siehe [Fehlerbehebungen](../bug-fixes.md) |
| &nbsp; | &nbsp; |

## <a name="173-february-2019"></a>Februar 2019: Version 17.3

| Neues Feature | Details |
| :------------ | :------ |
| Authentifizierungsmodus für (systemweite und benutzerseitig zugewiesene) verwaltete Azure Active Directory-Dienstidentitäten | Siehe [Using Azure Active Directory with the ODBC Driver (Verwenden von Azure Active Directory mit dem ODBC-Treiber)](../using-azure-active-directory.md) |
| Übermitteln von Eingabeparametern für Always Encrypted-Spalten | Siehe [Limitations of the ODBC driver when using Always Encrypted (Einschränkungen des ODBC-Treibers bei Verwendung von Always Encrypted)](../using-always-encrypted-with-the-odbc-driver.md#limitations-of-the-odbc-driver-when-using-always-encrypted) |
| Verteilte XA-Transaktionen | Siehe [Using XA Transactions (Verwenden von XA-Transaktionen)](../use-xa-with-dtc.md) |
| Fehlerbehebungen. | Siehe [Fehlerbehebungen](../bug-fixes.md) |
| &nbsp; | &nbsp; |

## <a name="172-july-2018"></a>Juli 2018: Version 17.2

| Neues Feature | Details |
| :------------ | :------ |
| Datenklassifizierung für Azure SQL-Datenbank und SQL Server | Siehe [Data Classification (Datenklassifizierung)](../data-classification.md) |
| Unterstützung der UTF-8-Servercodierung | &nbsp; |
| Fehlerbehebungen. | Siehe [Fehlerbehebungen](../bug-fixes.md) |
| &nbsp; | &nbsp; |

## <a name="171-march-2018"></a>März 2018: Version 17.1

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung der Verbindungsattribute `SQL_COPT_SS_CEKCACHETTL` und `SQL_COPT_SS_TRUSTEDCMKPATHS` | &bull; &nbsp; `SQL_COPT_SS_CEKCACHETTL`<br/>Ermöglicht das Steuern und Leeren der Zeit, für die der lokale Cache von Spaltenverschlüsselungsschlüsseln vorhanden ist<br/><br/>&bull; &nbsp; `SQL_COPT_SS_TRUSTEDCMKPATHS`<br/>Ermöglicht der Anwendung das Einschränken von Always Encrypted-Vorgängen, sodass diese nur die festgelegte Liste von Spaltenhauptschlüsseln nutzen<br/><br/> Weitere Informationen finden Sie unter [Using Always Encrypted with the ODBC Driver for SQL Server (Verwenden von Always Encrypted mit dem ODBC Driver for SQL Server)](../using-always-encrypted-with-the-odbc-driver.md). |
| Unterstützung der interaktiven Azure Active Directory-Authentifizierung | &nbsp; |
| Fehlerbehebungen. | Siehe [Fehlerbehebungen](../bug-fixes.md) |
| &nbsp; | &nbsp; |

## <a name="17-february-2018"></a>Februar 2018: Version 17

| Neues Feature | Details |
| :------------ | :------ |
| Always Encrypted-Unterstützung für die BCP-API | &nbsp; |
| Neues Verbindungszeichenfolgenattribut `UseFMTOnly` | Bewirkt, dass der Treiber in speziellen Fällen ältere Metadaten verwendet, die temporäre Tabellen erfordern |
| Unterstützung verwalteter Azure SQL-Datenbank-Instanzen | Die private Vorschau wurde verlängert<br/><br/>Weitere Informationen finden Sie in der folgenden [Liste der Unterschiede bei der Verwendung verwalteter Instanzen (ODBC-Version 17)](#diffs-managed-instance-17) |
| &nbsp; | &nbsp; |

| Geänderte Abhängigkeit | Details |
| :------------ | :------ |
| Der Anmeldeassistent für Microsoft-Onlinedienste wurde entfernt | Die Abhängigkeit wurde entfernt |
| &nbsp; | &nbsp; |

### <a name="diffs-managed-instance-17"></a> Unterschiede bei der Verwendung verwalteter Instanzen (ODBC-Version 17)

Diese Version von ODBC umfasst Unterstützung für verwaltete Azure SQL-Instanzen (verlängerte private Vorschau) In der folgenden Liste werden die Unterschiede bei der Verwendung von verwalteten Instanzen aufgeführt.

> [!NOTE]
> Bei der Verwendung verwalteter Instanzen gibt es einige Unterschiede:
>
> - FILESTREAM wird nicht unterstützt
> - Der Zugriff auf das lokale Dateisystem wird nicht unterstützt, ist jedoch für Dinge wie Ablaufverfolgungsdateien erforderlich
> - Das Erstellen von benutzerdefinierten Typen aus lokalen Pfaden wird nicht unterstützt
> - Die integrierte Windows-Authentifizierung wird nicht unterstützt
> - DTC wird nicht unterstützt
> - Das `sa`-Konto ist nicht vorhanden (Standardkonto: `cloudSA`).
> - Fehler beim TDS-Token (0xAA) gibt einen falschen Servernamen zurück
> - Sonderzeichen werden im Datenbanknamen nicht unterstützt
> - ALTER DATABASE [dbname1] MODIFY NAME = [dbname2] wird nicht unterstützt
> - Fehlermeldungen werden unabhängig von Ihren Spracheinstellungen immer in englischer Sprache angezeigt (wie bei Azure)

## <a name="131"></a>Version 13.1

| Neues Feature | Details |
| :------------ | :------ |
| Mit dem ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wurden [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) und [Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) hinzugefügt | Diese hinzugefügten Unterstützungen stehen zur Verfügung, wenn eine Verbindung mit Microsoft SQL Server 2016 oder einer höheren Version hergestellt wird |
| Es wurden Schlüsselwörter und Attribute für das Verbindungspooling hinzugefügt, die den Unterstützungen für Always Encrypted und Azure Active Directory entsprechen | Diese Schlüsselwörter und Attribute werden unter [Driver Aware Connection Pooling in the ODBC Driver for SQL Server (Treiberfähiges Verbindungspooling im ODBC Driver for SQL Server)](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md) beschrieben |
| &nbsp; | &nbsp; |

## <a name="13"></a>13

| Neues Feature | Details |
| :------------ | :------ |
| Die Unterstützung von Microsoft SQL Server 2016 wurde hinzugefügt | Die Funktionalität der Version 11 des ODBC-Treibers wird beibehalten |
| &nbsp; | &nbsp; |

## <a name="11"></a>11

| Neues Feature | Details |
| :------------ | :------ |
| Enthält neue Features | Siehe [Features of the Microsoft ODBC Driver for SQL Server on Windows (Features des Microsoft ODBC Driver for SQL Server unter Windows)](features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md) |
| Enthält alle Features des nativen Clients für ODBC in SQL Server 2012 | &nbsp; |
| &nbsp; | &nbsp; |
