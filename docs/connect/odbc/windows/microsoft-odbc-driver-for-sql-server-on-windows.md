---
title: Microsoft ODBC Driver for SQL Server unter Windows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b10cfc22-6a2c-4707-a456-0dcec317982b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c075c7adcc7eeae3ae7a83676256e72b4b86d187
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989427"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server on Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Microsoft ODBC-Treiber für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sind eigenständige ODBC-Treiber, die eine Anwendungsprogrammierschnittstelle (Application Programming Interface, API) bieten, die die ODBC-Standardschnittstellen für Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implementiert.

Der Microsoft ODBC Driver for SQL Server kann verwendet werden, um neue Anwendungen zu erstellen. Außerdem können Sie Ihre älteren Anwendungen, die zurzeit einen älteren ODBC-Treiber verwenden, aktualisieren. Der ODBC Driver for SQL Server unterstützt Verbindungen zur Azure SQL-Datenbank, Azure SQL Data Warehouse, SQL Server 2017, SQL Server 2016, SQL Server 2014, SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 und SQL Server 2005.  

## <a name="summary"></a>Zusammenfassung

| Versionsoptionen       | Unterstützte Features      |
| ------------- |---------------| 
| Microsoft ODBC Driver 17 for SQL Server | <ul><li>Always Encrypted-Unterstützung für die BCP-API</li><li>Das neue Verbindungszeichenfolgenattribut „UseFMTONLY“ bewirkt, dass der Treiber in besonderen Fällen ältere Metadaten verwendet, die temporäre Tabellen erfordern.</li>
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Always Encrypted</li><li>Azure AD-Authentifizierung</li><li>Always On-Verfügbarkeitsgruppen (Availability Groups, AG)</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>Internationaler Domänenname (IDN)</li></ul> |
| Microsoft ODBC Driver 11 für SQL Server | <ul><li>Treiberfähiges Verbindungspooling</li><li>Verbindungsstabilität</li><li>Asynchrone Ausführung (Abrufmethode)</li></ul> |    

## <a name="documentation"></a>Dokumentation  
Diese Dokumentation für den Microsoft ODBC Driver für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enthält:  
  
-   [Release Notes for ODBC to SQL Server on Windows (Versionshinweise zu ODBC für SQL Server unter Windows)](../../../connect/odbc/windows/release-notes-odbc-sql-server-windows.md)  
-   [Funktionen von Microsoft ODBC Driver for SQL Server unter Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Systemanforderungen, Installation und Treiberdateien](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Treiberfähiges Verbindungspooling im ODBC-Treiber für SQL Server.](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Beispiel für asynchrone Ausführung &#40;Benachrichtigungsmethode&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Verbindungsresilienz im Windows ODBC-Treiber](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Verwenden von Always Encrypted mit dem ODBC-Treiber](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [Verwenden von Azure Active Directory mit dem ODBC-Treiber](../../../connect/odbc/using-azure-active-directory.md) 
-   [Verwenden der transparenten Netzwerk-IP-Adressauflösung](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>Community  
- [Microsoft ODBC Driver for SQL Server Teamblog](https://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server-Datenzugriffsforum](https://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>Weitere Informationen  
- [Informationen zu SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [FAQ zu SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [ODBC-Programmierreferenz](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
