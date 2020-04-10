---
title: Features des Microsoft ODBC Driver for SQL Server unter Windows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: v-makouz
ms.author: v-daenge
ms.openlocfilehash: 2143be3396e16eb61fd36ac5956c11626363bcf5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928268"
---
# <a name="features-of-the-microsoft-odbc-driver-for-sql-server-on-windows"></a>Funktionen von Microsoft ODBC Driver for SQL Server on Windows
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

    
## <a name="microsoft-odbc-driver-174-for-sql-server-on-windows"></a>Microsoft ODBC Driver 17.4 for SQL Server unter Windows

Der ODBC Driver 17.4 bietet die Möglichkeit, Keep-Alive-Einstellungen für TCP anzupassen. Diese können durch Hinzufügen von Werten zu den Registrierungsschlüsseln für Treiber oder DSN geändert werden. Die Schlüssel befinden sich für Systemdatenquellen in `HKEY_LOCAL_MACHINE\Software\ODBC\` und für Benutzerdatenquellen in `HKEY_CURRENT_USER\Software\ODBC\`. Für DSN müssen die Werte zu `...\Software\ODBC\ODBC.INI\<DSN Name>` hinzugefügt werden, für den Treiber zu `...\Software\ODBC\ODBCINST.INI\ODBC Driver 17 for SQL Server`.

Weitere Informationen finden Sie unter [Registrierungseinträge für ODBC-Komponenten](../../../odbc/reference/install/registry-entries-for-odbc-components.md).

Die `REG_SZ`-Werte lauten wie folgt:

- `KeepAlive` steuert, wie häufig TCP ein Keep-Alive-Paket sendet, um zu überprüfen, ob eine Verbindung im Leerlauf noch reagiert. Der Standardwert ist 30 Sekunden.

- `KeepAliveInterval` bestimmt das Intervall, das zwischen den erneuten Keep-Alive-Übertragungen liegt, bis eine Antwort empfangen wird. Der Standardwert beträgt 1 Sekunde.



## <a name="microsoft-odbc-driver-131-for-sql-server-on-windows"></a>Microsoft ODBC Driver 13.1 for SQL Server unter Windows

Der ODBC Driver 13.1 for SQL Server enthält alle Funktionen der vorherigen Version (11) und bietet bei gemeinsamer Verwendung mit Microsoft SQL Server 2016 Unterstützung für Always Encrypted sowie für die Azure Active Directory-Authentifizierung.  
  
„Immer verschlüsselt“ ermöglicht es Clients, sensible Daten in Clientanwendungen zu verschlüsseln und die Verschlüsselungsschlüssel niemals an SQL Server weiterzugeben. Ein auf dem Clientcomputer installierter Treiber, bei dem „Immer verschlüsselt“ aktiviert ist, erreicht dies durch die automatische Ver- und Entschlüsselung von sensiblen Daten in der SQL Server-Clientanwendung. Der Treiber verschlüsselt die Daten in vertraulichen Spalten, bevor er sie an SQL Server weitergibt, und schreibt Abfragen automatisch neu, sodass die Semantik der Anwendung beibehalten wird. Auf ähnliche Weise entschlüsselt der Treiber transparent Daten in verschlüsselten Datenbankspalten, die in Abfrageergebnissen enthalten sind. Weitere Informationen finden Sie unter [Using Always Encrypted with the ODBC Driver (Verwenden von Always Encrypted mit dem ODBC-Treiber)](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md).
 
Azure Active Directory ermöglicht es Benutzern, Datenbankadministratoren und Anwendungsprogrammierern, die Azure Active Directory-Authentifizierung als Mechanismus zu verwenden, mit dem unter Verwendung von Identitäten in Azure Active Directory (Azure AD) eine Verbindung mit Microsoft Azure SQL-Datenbank und Microsoft SQL Server 2016 hergestellt werden kann. Weitere Informationen finden Sie unter [Verwenden von Azure Active Directory mit dem ODBC Driver](../../../connect/odbc/using-azure-active-directory.md) und [Herstellen einer Verbindung mit SQL-Datenbank oder SQL Data Warehouse unter Verwendung der Azure Active Directory-Authentifizierung](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/).   
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-windows"></a>Microsoft ODBC Driver 11 für SQL Server unter Windows  

Der ODBC-Treiber für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enthält die gesamte Funktionalität des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treibers, der im Lieferumfang von [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]enthalten ist. Weitere Informationen finden Sie unter [SQL Server Native Client-Programmierung](../../../relational-databases/native-client/sql-server-native-client-programming.md). Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber basiert auf dem ODBC-Treiber, der im Lieferumfang des Betriebssystems von Windows enthalten ist. Weitere Informationen finden Sie unter [Windows Data Access Components SDK](https://msdn.microsoft.com/library/aa968814(VS.85).aspx).  
  
Diese Version des ODBC-Treibers für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enthält die folgenden neuen Features:  
  
### <a name="bcpexe--l-option-for-specifying-a-login-timeout"></a>bcp.exe -l – Option zur Angabe eines Anmeldetimeouts
 
Die Option „-I“ gibt an, wie viele Sekunden beim Herstellen einer Verbindung mit einem Server verstreichen dürfen, bevor für eine `bcp.exe`-Anmeldung bei [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ein Timeout eintritt. Das Standardanmeldetimeout beträgt 15 Sekunden. Der Timeoutwert für den Anmeldungszeitraum muss eine Zahl zwischen 0 und 65534 sein. Wenn der angegebene Wert kein numerischer Wert ist oder außerhalb dieses Bereichs liegt, generiert `bcp.exe` eine Fehlermeldung. Der Wert 0 steht für ein unendliches Timeout. Ein Anmeldungstimeout von weniger als 10 Sekunden ist nicht zuverlässig.  
  
### <a name="driver-aware-connection-pooling"></a>Treiberfähiges Verbindungspooling  
Der ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt [treiberfähiges Verbindungspooling](https://msdn.microsoft.com/library/hh405031(VS.85).aspx). Weitere Informationen finden Sie unter [Driver-Aware Connection Pooling in the ODBC Driver for SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).  
  
### <a name="asynchronous-execution-notification-method"></a>Asynchrone Ausführung (Benachrichtigungsmethode)  
Der ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt die [asynchrone Ausführung (Benachrichtigungsmethode)](https://msdn.microsoft.com/library/hh405038(VS.85).aspx). Ein Verwendungsbeispiel finden Sie unter [Beispiel für asynchrone Ausführung &#40;Benachrichtigungsmethode&#41;](../../../connect/odbc/windows/asynchronous-execution-notification-method-sample.md).  
  
### <a name="connection-resiliency"></a>Verbindungsstabilität
Um sicherzustellen, dass die Anwendungen mit einer Microsoft Azure SQL-Datenbank verbunden sind, kann der ODBC-Treiber unter Windows Verbindungen im Leerlauf wiederherstellen. Weitere Informationen finden Sie unter [Connection Resiliency in the Windows ODBC Driver](../../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md).  
  
## <a name="behavior-changes"></a>Verhaltensänderungen

In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client führte die Option `-y0` für `sqlcmd.exe` dazu, dass die Ausgabe bei 1 MB abgeschnitten wurde, wenn die Anzeigebreite auf 0 festgelegt war.
  
Beginnend mit dem ODBC-Treiber 11 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt es keine Beschränkung für die Menge der Daten, die in einer einzelnen Spalte abgerufen werden, wenn `-y0` angegeben ist. `sqlcmd.exe` streamt jetzt Spalten bis zu 2 GB (Maximum für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen).  
  
Ein weiterer Unterschied ist, dass die Angabe sowohl von `-h` als auch von `-y0` nun einen Fehler erzeugt, der meldet, dass die Optionen inkompatibel sind. `-h`, wodurch die Anzahl der Zeilen angegeben wird, die zwischen den Spaltenüberschriften gedruckt werden sollen, war noch nie mit `-y0` kompatibel und wurde ignoriert, obwohl keine Überschriften gedruckt wurden.
  
Beachten Sie, dass `-y0` je nach Größe der zurückgegebene Daten zu Leistungsproblemen auf dem Server und im Netzwerk führen kann.

## <a name="see-also"></a>Weitere Informationen  
[Microsoft ODBC Driver for SQL Server unter Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
