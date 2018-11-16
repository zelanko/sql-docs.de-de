---
title: Microsoft ODBC Driver for SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9f2ae91b-06af-4c9a-9d24-062df7bc4662
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4a36070adf041363953ddaaf08675a2b9d649feb
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51603730"
---
# <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

ODBC ist die primäre native Datenzugriffs-API für Anwendungen, die für SQL Server in C und C++ geschrieben wurden. Ein ODBC-Treiber bei den meisten Datenquellen ist vorhanden. Andere Sprachen, die ODBC verwenden können, enthalten COBOL, Perl, PHP und Python. ODBC wird häufig in von datenintegrationsszenarien verwendet werden.

Der ODBC-Treiber stellt Tools wie [**sqlcmd**](../../tools/sqlcmd-utility.md) und [**bcp**](../../tools/bcp-utility.md) bereit. Mit dem Hilfsprogramm **sqlcmd** können Sie Transact-SQL-Anweisungen, Systemprozeduren und SQL-Skripts ausführen. Mit dem Hilfsprogramm **bcp** werden Daten zwischen einer Microsoft SQL Server-Instanz und einer Datendatei in einem von Ihnen definierten Format massenkopiert. Mit **bcp** können Sie viele neue Zeilen in SQL Server-Tabellen importieren oder Daten aus Tabellen in Datendateien exportieren.  

## <a name="code-example-in-c"></a>Codebeispiel in C++

Das folgende C++-Beispiel veranschaulicht, wie die ODBC-APIs eine Verbindung herstellen und auf eine Datenbank zugreifen:

- [C++-Codebeispiel, mithilfe von ODBC](../../odbc/reference/sample-odbc-program.md)

## <a name="download"></a>Herunterladen

- ![Download-nach-unten-Eingekreiste](../../ssdt/media/download.png)[ODBC-Treiber herunterladen](download-odbc-driver-for-sql-server.md)

## <a name="documentation"></a>Dokumentation

### <a name="features"></a>Funktionen

- [Benutzerdefinierte Keystore-Anbieter](../../connect/odbc/custom-keystore-providers.md)
- [Schlüsselwörter und Attribute von DNS- und Verbindungszeichenfolgen](dsn-connection-string-attribute.md)
- [SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md) (die verfügbaren Funktionen auch anwenden, ohne die OLE DB verwenden, um den ODBC-Treiber für SQL Server)
- [Verwendung von Always Encrypted](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
- [Verwendung von Azure Active Directory](../../connect/odbc/using-azure-active-directory.md)
- [Verwenden der transparenten Netzwerk-IP-Adressauflösung](../../connect/odbc/using-transparent-network-ip-resolution.md)

### <a name="linux-and-macos"></a>Linux und macOS

- [Installieren des Treibers](../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [Connecting to SQL Server (Herstellen einer Verbindung mit SQL Server)](../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)
- [Herstellen einer Verbindung mit **bcp**](../../connect/odbc/linux-mac/connecting-with-bcp.md)
- [Herstellen einer Verbindung mit **sqlcmd**](../../connect/odbc/linux-mac/connecting-with-sqlcmd.md)
- [Datenzugriffsablaufverfolgung](../../connect/odbc/linux-mac/data-access-tracing-with-the-odbc-driver-on-linux.md)
- [Häufig gestellte Fragen](../../connect/odbc/linux-mac/frequently-asked-questions-faq-for-odbc-linux.md)
- [Installieren des Treiber-Managers](../../connect/odbc/linux-mac/installing-the-driver-manager.md)
- [Bekannte Probleme](../../connect/odbc/linux-mac/known-issues-in-this-version-of-the-driver.md)
- [Programmierrichtlinien](../../connect/odbc/linux-mac/programming-guidelines.md)
- [Versionsanmerkungen](../../connect/odbc/linux-mac/release-notes.md)
- [Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung](../../connect/odbc/linux-mac/odbc-driver-on-linux-support-for-high-availability-disaster-recovery.md)
- [Nutzung der Integrierten Authentifizierung (Kerberos)](../../connect/odbc/linux-mac/using-integrated-authentication.md)

### <a name="windows"></a>Windows

- [Beispiel für asynchrone Ausführung (Benachrichtigungsmethode)](../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)
- [Verbindungsresilienz im Windows ODBC-Treiber](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)
- [Treiberfähiges Verbindungspooling](../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)
- [Features und Verhaltensänderungen](../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)
- [Versionsanmerkungen](../../connect/odbc/windows/release-notes.md)
- [Systemanforderungen, Installation und Treiberdateien](../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)



## <a name="community"></a>Community  
- [Microsoft ODBC Driver for SQL Server Teamblog](https://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server-Datenzugriffsforum](https://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
