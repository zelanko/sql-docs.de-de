---
title: Treiberfähiges Verbindungspooling im ODBC Driver for SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 455ab165-8e4d-4df9-a1d7-2b532bfd55d6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97ddd5aa4abf926ecd4e68e89bef63b8f25ce323
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "68009974"
---
# <a name="driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server"></a>Treiberfähiges Verbindungspooling im ODBC-Treiber für SQL Server.
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Der ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt [treiberfähiges Verbindungspooling](https://msdn.microsoft.com/library/hh405031(VS.85).aspx). In diesem Artikel wird die Erweiterungen der Funktion „Treiberfähiges Verbindungspooling“ im Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Windows beschrieben:  
  
-   Unabhängig von den Verbindungseigenschaften wechseln Verbindungen, die `SQLDriverConnect` verwenden, in einen separaten Pool von Verbindungen, die `SQLConnect` verwenden.
- Bei Verwendung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung und des treiberfähigen Verbindungspoolings verwendet der Treiber nicht den Sicherheitskontext des Windows-Benutzers für den aktuellen Thread, um Verbindungen im Pool zu trennen. Das bedeutet, wenn Verbindungen in ihren Parametern für Identitätswechsel-Szenarien unter Windows mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung äquivalent sind und die gleichen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anmeldeinformationen zur Verbindung mit dem Back-End verwenden, können andere Windows-Benutzer möglicherweise den gleichen Pool aus Verbindungen verwenden. Bei Verwendung der Windows-Authentifizierung und des treiberfähigen Verbindungspoolings verwendet der Treiber den aktuellen Sicherheitkontext des Windows-Benutzers für den aktuellen Thread, um Verbindungen im Pool zu trennen. D. h. für Windows-Identitätswechsel-Szenarios teilen sich verschiedene Windows-Benutzer keine Verbindungen, auch wenn die Verbindungen dieselben Parameter verwenden.
- Wenn Sie Azure Active Directory und treiberfähiges Verbindungspooling verwenden, verwendet der Treiber ebenfalls den Authentifizierungswert, um die Mitgliedschaft beim Verbindungspool zu ermitteln.
  
-   Treiberfähiges Verbindungspooling verhindert, dass eine fehlerhafte Verbindung aus dem Pool zurückgegeben wird.  
  
-   Treiberfähiges Verbindungspooling erkennt treiberspezifische Verbindungsattribute. Wenn eine Verbindung also ein schreibgeschütztes `SQL_COPT_SS_APPLICATION_INTENT`-Attribut verwendet, erhält diese einen eigenen Verbindungspool.
-   Wenn das `SQL_COPT_SS_ACCESS_TOKEN`-Attribut festgelegt wird, wird die Verbindung in einen separaten Pool aufgenommen. 
  
Wenn eine der folgenden Verbindungsattribut-IDs oder eines der Schlüsselwörter für Verbindungszeichenfolgen zwischen Ihrer Verbindungszeichenfolge und der in einem Pool zusammengefassten Verbindungszeichenfolge abweicht, verwendet der Treiber eine gepoolte Verbindung. Allerdings ist die Leistung besser, wenn alle Verbindungsattribut-IDs oder Schlüsselwörter für Verbindungszeichenfolgen übereinstimmen. (Um eine Übereinstimmung einer Verbindung im Pool herzustellen, setzt der Treiber das Attribut zurück. Die Leistung wird beeinträchtigt, da ein zusätzlicher Netzwerkaufruf notwendig ist, um die folgenden Parameter zurückzusetzen.  
  
-    Wenn sich zwei oder mehr der folgenden Verbindungsattribute oder Verbindungsschlüsselwörter unterscheiden, wird keine gepoolte Verbindung verwendet.  
  
  - `Language`  
  - `QuoteId`  
  - `SQL_ATTR_TXN_ISOLATION` 
  - `SQL_COPT_SS_QUOTED_IDENT`  
  
-   Gibt es einen Unterschied in einem der folgenden Verbindungsschlüsselwörter zwischen Ihrer Verbindungszeichenfolge und einer gepoolten Verbindungszeichenfolge, wird keine gepoolte Verbindung verwendet.  
  
    |Schlüsselwort|ODBC-Treiber 13|ODBC-Treiber 11|
    |-|-|-|
    |`Address`|Ja|Ja|
    |`AnsiNPW`|Ja|Ja|
    |`App`|Ja|Ja|
    |`ApplicationIntent`|Ja|Ja|  
    |`Authentication`|Ja|Nein|
    |`ColumnEncryption`|Ja|Nein|
    |`Database`|Ja|Ja|
    |`Encrypt`|Ja|Ja|  
    |`Failover_Partner`|Ja|Ja|
    |`FailoverPartnerSPN`|Ja|Ja|
    |`MARS_Connection`|Ja|Ja|
    |`Network`|Ja|Ja|
    |`PWD`|Ja|Ja|
    |`Server`|Ja|Ja|
    |`ServerSPN`|Ja|Ja|
    |`TransparentNetworkIPResolution`|Ja|Ja|
    |`Trusted_Connection`|Ja|Ja|
    |`TrustServerCertificate`|Ja|Ja|
    |`UID`|Ja|Ja|
    |`WSID`|Ja|Ja|
    
- Gibt es einen Unterschied in einem der folgenden Verbindungsattribute zwischen Ihrer Verbindungszeichenfolge und einer gepoolten Verbindungszeichenfolge, wird keine gepoolte Verbindung verwendet.  
  
    |attribute|ODBC-Treiber 13|ODBC-Treiber 11|  
    |-|-|-|  
    |`SQL_ATTR_CURRENT_CATALOG`|Ja|Ja|
    |`SQL_ATTR_PACKET_SIZE`|Ja|Ja|
    |`SQL_COPT_SS_ANSI_NPW`|Ja|Ja|
    |`SQL_COPT_SS_ACCESS_TOKEN`|Ja|Nein|
    |`SQL_COPT_SS_AUTHENTICATION`|Ja|Nein|
    |`SQL_COPT_SS_ATTACHDBFILENAME`|Ja|Ja|
    |`SQL_COPT_SS_BCP`|Ja|Ja|
    |`SQL_COPT_SS_COLUMN_ENCRYPTION`|Ja|Nein|
    |`SQL_COPT_SS_CONCAT_NULL`|Ja|Ja|
    |`SQL_COPT_SS_ENCRYPT`|Ja|Ja|
    |`SQL_COPT_SS_FAILOVER_PARTNER`|Ja|Ja|
    |`SQL_COPT_SS_FAILOVER_PARTNER_SPN`|Ja|Ja|
    |`SQL_COPT_SS_INTEGRATED_SECURITY`|Ja|Ja|
    |`SQL_COPT_SS_MARS_ENABLED`|Ja|Ja|
    |`SQL_COPT_SS_OLDPWD`|Ja|Ja|
    |`SQL_COPT_SS_SERVER_SPN`|Ja|Ja|
    |`SQL_COPT_SS_TRUST_SERVER_CERTIFICATE`|Ja|Ja|
    |`SSPROP_AUTH_REPL_SERVER_NAME`|Ja|Ja|
    |`SQL_COPT_SS_TNIR`|Ja|Nein|
 
-   Der Treiber kann die folgenden Verbindungsschlüsselwörter und Attribute zurücksetzen und anpassen, ohne einen zusätzlichen Netzwerkaufruf durchzuführen. Der Treiber setzt diese Parameter zurück, um sicherzustellen, dass die Verbindung keine falschen Informationen enthält.  
  
     Diese Schlüsselwörter werden nicht berücksichtigt, wenn der Treiber-Manager versucht, eine Übereinstimmung zwischen Ihrer Verbindung und einer Verbindung im Pool zu erzielen. (Auch wenn Sie einen dieser Parameter ändern, kann eine vorhandene Verbindung wiederverwendet werden. Der Treiber setzt die Optionen nach Bedarf zurück.) Diese Attribute können clientseitig ohne einen zusätzliche Netzwerkaufruf zurückgesetzt werden.  
  
    |Schlüsselwort|ODBC-Treiber 13|ODBC-Treiber 11|  
    |-|-|-|  
    |`AutoTranslate`|Ja|Ja|
    |`Description`|Ja|Ja|
    |`MultisubnetFailover`|Ja|Ja|  
    |`QueryLog_On`|Ja|Ja|
    |`QueryLogFile`|Ja|Ja|
    |`QueryLogTime`|Ja|Ja|
    |`Regional`|Ja|Ja|
    |`StatsLog_On`|Ja|Ja|
    |`StatsLogFile`|  Ja|Ja|
  
     Wenn Sie eine der folgenden Verbindungsattribute ändern, kann eine vorhandene Verbindung wiederverwendet werden.  Der Treiber wird je nach Bedarf den Wert zurücksetzen. Der Treiber kann diese Attribute clientseitig ohne einen zusätzliche Netzwerkaufruf zurücksetzen  
  
    |attribute|ODBC-Treiber 13|ODBC-Treiber 11|  
    |-|-|-|  
    |Alle Anweisungsattribute|Ja|Ja|
    |`SQL_ATTR_AUTOCOMMIT`|Ja|Ja|
    |`SQL_ATTR_CONNECTION_TIMEOUT`|  Ja|Ja|
    |`SQL_ATTR_DISCONNECT_BEHAVIOR SQL_ATTR_CONNECTION_TIMEOUT`|Ja|Ja|
    |`SQL_ATTR_LOGIN_TIMEOUT`|Ja|Ja|
    |`SQL_ATTR_ODBC_CURSORS`|  Ja|Ja|
    |`SQL_COPT_SS_PERF_DATA`|Ja|Ja|
    |`SQL_COPT_SS_PERF_DATA_LOG`|Ja|Ja|
    |`SQL_COPT_SS_PERF_DATA_LOG_NOW`| Ja|Ja| 
    |`SQL_COPT_SS_PERF_QUERY`|Ja|Ja|
    |`SQL_COPT_SS_PERF_QUERY_INTERVAL`|Ja|Ja|
    |`SQL_COPT_SS_PERF_QUERY_LOG`|  Ja|Ja|
    |`SQL_COPT_SS_PRESERVE_CURSORS`|Ja|Ja|
    |`SQL_COPT_SS_TRANSLATE`|Ja|Ja|
    |`SQL_COPT_SS_USER_DATA`|  Ja|Ja|
    |`SQL_COPT_SS_WARN_ON_CP_ERROR`|Ja|Ja|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft ODBC Driver for SQL Server unter Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
