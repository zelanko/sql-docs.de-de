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
manager: craigg
ms.openlocfilehash: 24bf2d56bda17378dcc45a464fd46f95c9664936
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47790448"
---
# <a name="microsoft-odbc-driver-for-sql-server-on-windows"></a>Microsoft ODBC Driver for SQL Server on Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Die Microsoft ODBC-Treiber für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sind eigenständige ODBC-Treiber, die eine Anwendungsprogrammierschnittstelle (API), der Implementierung der ODBC-Standardschnittstellen für Microsoft bereitstellen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].

Der Microsoft ODBC Driver for SQL Server kann verwendet werden, um neue Anwendungen zu erstellen. Außerdem können Sie Ihre älteren Anwendungen, die zurzeit einen älteren ODBC-Treiber verwenden, aktualisieren. Der ODBC Driver for SQL Server unterstützt Verbindungen zur Azure SQL-Datenbank, Azure SQL Data Warehouse, SQL Server 2017, SQL Server 2016, SQL Server 2014, SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 und SQL Server 2005.  

## <a name="summary"></a>Zusammenfassung

| Versionsoptionen       | Unterstützte Funktionen      |
| ------------- |---------------| 
| Microsoft ODBC Driver 17 for SQL Server | <ul><li>Unterstützung von Always Encrypted für BCP-API</li><li>Neues Verbindungszeichenfolgen-Attribut UseFMTONLY bewirkt, dass ältere Metadaten in besonderen Fällen erfordern der temporäre Tabellen zu verwendenden Treiber</li>
| Microsoft ODBC Driver 13.1 for SQL Server     | <ul><li>Always Encrypted</li><li>Azure AD-Authentifizierung</li><li>Always On-Verfügbarkeitsgruppen (Availability Groups, AG)</li></ul>   | 
| Microsoft ODBC Driver 13 for SQL Server      | <ul><li>Internationaler Domänenname (IDN)</li></ul> |
| Microsoft ODBC Driver 11 for SQL Server | <ul><li>Treiberfähiges Verbindungspooling</li><li>Verbindungsstabilität</li><li>Asynchrone Ausführung (Abrufmethode)</li></ul> |    

## <a name="documentation"></a>Dokumentation  
Diese Dokumentation für den Microsoft ODBC Driver für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enthält:  
  
-   [Versionsanmerkungen](../../../connect/odbc/windows/release-notes.md)  
-   [Funktionen von Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md)  
-   [Systemanforderungen, Installation und Treiberdateien](../../../connect/odbc/windows/system-requirements-installation-and-driver-files.md)  
-   [Treiberfähiges Verbindungspooling im ODBC-Treiber für SQL Server.](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md)  
-   [Beispiel für asynchrone Ausführung &#40;Benachrichtigungsmethode&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md)  
-   [Verbindungsresilienz im Windows ODBC-Treiber](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md)  
-   [Verwenden von Always Encrypted mit dem ODBC-Treiber](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
-   [Verwenden von Azure Active Directory mit dem ODBC-Treiber](../../../connect/odbc/using-azure-active-directory.md) 
-   [Verwenden der transparenten Netzwerk-IP-Adressauflösung](../../../connect/odbc/using-transparent-network-ip-resolution.md)   

## <a name="community"></a>Community  
- [Microsoft ODBC Driver for SQL Server Teamblog](http://blogs.msdn.com/sqlnativeclient/default.aspx)  
- [SQL Server-Datenzugriffsforum](http://social.technet.microsoft.com/Forums/en/sqldataaccess/threads)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
- [Informationen zu SQL Server Native Client](https://msdn.microsoft.com/sqlserver/ff658532.aspx)   
- [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)   
- [FAQ zu SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937707.aspx)   
- [ODBC-Programmierreferenz](../../../odbc/reference/odbc-programmer-s-reference.md)   
- [SQL Server Native Client (ODBC)](../../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
