---
title: Treiberfähiges Verbindungspooling im ODBC Driver for SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3cc9428f84db56675dbf58c977078fa4dcca6ae
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38060008"
---
# <a name="driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server"></a>Treiberfähiges Verbindungspooling im ODBC-Treiber für SQL Server.
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Der ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] unterstützt [treiberfähiges Verbindungspooling](http://msdn.microsoft.com/library/hh405031(VS.85).aspx). In diesem Artikel wird die Erweiterungen der Funktion „Treiberfähiges Verbindungspooling“ im Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] on Windows beschrieben:  
  
-   Unabhängig von den Verbindungseigenschaften wechseln Verbindungen, die `SQLDriverConnect` verwenden, in einen separaten Pool von Verbindungen, die `SQLConnect` verwenden.
- Bei Verwendung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]-Authentifizierung und des treiberfähigen Verbindungspoolings verwendet der Treiber nicht den Sicherheitskontext des Windows-Benutzers für den aktuellen Thread, um Verbindungen im Pool zu trennen. Das bedeutet, wenn Verbindungen in ihren Parametern für Identitätswechsel-Szenarien unter Windows mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] -Authentifizierung äquivalent sind und die gleichen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] -Anmeldeinformationen zur Verbindung mit dem Back-End verwenden, können andere Windows-Benutzer möglicherweise den gleichen Pool aus Verbindungen verwenden. Bei Verwendung der Windows-Authentifizierung und des treiberfähigen Verbindungspoolings verwendet der Treiber den aktuellen Sicherheitkontext des Windows-Benutzers für den aktuellen Thread, um Verbindungen im Pool zu trennen. D. h. für Windows-Identitätswechsel-Szenarios teilen sich verschiedene Windows-Benutzer keine Verbindungen, auch wenn die Verbindungen dieselben Parameter verwenden.
- Bei Verwendung von Azure Active Directory und treiberfähiges Verbindungspooling verwendet der Treiber auch den Wert um die Mitgliedschaft in einem Verbindungspool zu bestimmen.
  
-   Treiberfähiges Verbindungspooling verhindert, dass eine fehlerhafte Verbindung aus dem Pool zurückgegeben wird.  
  
-   Treiberfähiges Verbindungspooling erkennt treiberspezifische Verbindungsattribute. Wenn also eine Verbindung einen schreibgeschützten SQL`SQL_COPT_SS_APPLICATION_INTENT`COPTSSAPPLICATIONINTENT-Satz verwendet, erhält diese Verbindung ihren eigenen Verbindungspool.
-   Festlegen der `SQL_COPT_SS_ACCESS_TOKEN` Attribut bewirkt, dass eine Verbindung getrennt gepoolt werden sollen 
  
Wenn eine der folgenden Verbindungsattribut-IDs oder eines der Schlüsselwörter für Verbindungszeichenfolgen zwischen Ihrer Verbindungszeichenfolge und der in einem Pool zusammengefassten Verbindungszeichenfolge abweicht, verwendet der Treiber eine gepoolte Verbindung. Allerdings ist die Leistung besser, wenn alle Verbindungsattribut-IDs oder Schlüsselwörter für Verbindungszeichenfolgen übereinstimmen. (Um eine Übereinstimmung einer Verbindung im Pool herzustellen, setzt der Treiber das Attribut zurück. Die Leistung wird beeinträchtigt, da ein zusätzlicher Netzwerkaufruf notwendig ist, um die folgenden Parameter zurückzusetzen.)  
  
-    Wenn sich zwei oder mehr der folgenden Verbindungsattribute oder Verbindungsschlüsselwörter unterscheiden, wird keine gepoolte Verbindung verwendet.  
  
  - `Language`  
  - `QuoteId`  
  - `SQL_ATTR_TXN_ISOLATION` 
  - `SQL_COPT_SS_QUOTED_IDENT`  
  
-   Gibt es einen Unterschied in einem der folgenden Verbindungsschlüsselwörter zwischen Ihrer Verbindungszeichenfolge und einer gepoolten Verbindungszeichenfolge, wird keine gepoolte Verbindung verwendet.  
  
    |Schlüsselwort|ODBC-Treiber 13|ODBC-Treiber 11|
    |-|-|-|
    |`Address`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`AnsiNPW`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`App`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`ApplicationIntent`|Benutzerkontensteuerung|Benutzerkontensteuerung|  
    |`Authentication`|Benutzerkontensteuerung|nein|
    |`ColumnEncryption`|Benutzerkontensteuerung|nein|
    |`Database`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`Encrypt`|Benutzerkontensteuerung|Benutzerkontensteuerung|  
    |`Failover_Partner`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`FailoverPartnerSPN`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`MARS_Connection`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`Network`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`PWD`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`Server`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`ServerSPN`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`TransparentNetworkIPResolution`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`Trusted_Connection`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`TrustServerCertificate`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`UID`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`WSID`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    
- Gibt es einen Unterschied in einem der folgenden Verbindungsattribute zwischen Ihrer Verbindungszeichenfolge und einer gepoolten Verbindungszeichenfolge, wird keine gepoolte Verbindung verwendet.  
  
    |attribute|ODBC-Treiber 13|ODBC-Treiber 11|  
    |-|-|-|  
    |`SQL_ATTR_CURRENT_CATALOG`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_ATTR_PACKET_SIZE`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_ANSI_NPW`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_ACCESS_TOKEN`|Benutzerkontensteuerung|nein|
    |`SQL_COPT_SS_AUTHENTICATION`|Benutzerkontensteuerung|nein|
    |`SQL_COPT_SS_ATTACHDBFILENAME`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_BCP`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_COLUMN_ENCRYPTION`|Benutzerkontensteuerung|nein|
    |`SQL_COPT_SS_CONCAT_NULL`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_ENCRYPT`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_FAILOVER_PARTNER`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_FAILOVER_PARTNER_SPN`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_INTEGRATED_SECURITY`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_MARS_ENABLED`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_OLDPWD`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_SERVER_SPN`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_TRUST_SERVER_CERTIFICATE`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SSPROP_AUTH_REPL_SERVER_NAME`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_TNIR`|Benutzerkontensteuerung|nein|
 
-   Der Treiber kann die folgenden Verbindungsschlüsselwörter und Attribute zurücksetzen und anpassen, ohne einen zusätzlichen Netzwerkaufruf durchzuführen. Der Treiber setzt diese Parameter zurück, um sicherzustellen, dass die Verbindung keine falschen Informationen enthält.  
  
     Diese Schlüsselwörter werden nicht berücksichtigt, wenn der Treiber-Manager versucht, eine Übereinstimmung zwischen Ihrer Verbindung und einer Verbindung im Pool zu erzielen. (Auch wenn Sie einen dieser Parameter ändern, kann eine vorhandene Verbindung wiederverwendet werden. Der Treiber wird je nach Bedarf die Optionen zurücksetzen.) Diese Attribute können clientseitig ohne einen zusätzliche Netzwerkaufruf zurückgesetzt werden.  
  
    |Schlüsselwort|ODBC-Treiber 13|ODBC-Treiber 11|  
    |-|-|-|  
    |`AutoTranslate`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`Description`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`MultisubnetFailover`|Benutzerkontensteuerung|Benutzerkontensteuerung|  
    |`QueryLog_On`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`QueryLogFile`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`QueryLogTime`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`Regional`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`StatsLog_On`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`StatsLogFile`|  Benutzerkontensteuerung|Benutzerkontensteuerung|
  
     Wenn Sie eine der folgenden Verbindungsattribute ändern, kann eine vorhandene Verbindung wiederverwendet werden.  Der Treiber wird je nach Bedarf den Wert zurücksetzen. Der Treiber kann diese Attribute clientseitig ohne einen zusätzliche Netzwerkaufruf zurücksetzen  
  
    |attribute|ODBC-Treiber 13|ODBC-Treiber 11|  
    |-|-|-|  
    |Alle Anweisungsattribute|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_ATTR_AUTOCOMMIT`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_ATTR_CONNECTION_TIMEOUT`|  Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_ATTR_DISCONNECT_BEHAVIOR SQL_ATTR_CONNECTION_TIMEOUT`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_ATTR_LOGIN_TIMEOUT`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_ATTR_ODBC_CURSORS`|  Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_PERF_DATA`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_PERF_DATA_LOG`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_PERF_DATA_LOG_NOW`| Benutzerkontensteuerung|Benutzerkontensteuerung| 
    |`SQL_COPT_SS_PERF_QUERY`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_PERF_QUERY_INTERVAL`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_PERF_QUERY_LOG`|  Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_PRESERVE_CURSORS`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_TRANSLATE`|Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_USER_DATA`|  Benutzerkontensteuerung|Benutzerkontensteuerung|
    |`SQL_COPT_SS_WARN_ON_CP_ERROR`|Benutzerkontensteuerung|Benutzerkontensteuerung|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
