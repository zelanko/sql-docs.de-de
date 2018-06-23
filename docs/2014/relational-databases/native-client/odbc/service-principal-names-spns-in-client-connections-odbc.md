---
title: Dienstprinzipalnamen (SPN) in Clientverbindungen (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1d60cb30-4c46-49b2-89ab-701e77a330a2
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c8fdc4c20be572ec2f4ce3d502201a72fead81f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150336"
---
# <a name="service-principal-names-spns-in-client-connections-odbc"></a>Dienstprinzipalnamen (SPN) in Clientverbindungen (ODBC)
  In diesem Thema werden ODBC-Attribute und Funktionen beschrieben, die Dienstprinzipalnamen (SPN) in Clientanwendungen unterstützen. Weitere Informationen zu SPNs in Clientanwendungen finden Sie unter [Service Principal Name &#40;SPN&#41; -Unterstützung in Clientverbindungen](../features/service-principal-name-spn-support-in-client-connections.md) und [gegenseitige Kerberos-Authentifizierung erhalten](../../native-client-odbc-how-to/get-mutual-kerberos-authentication.md).  
  
## <a name="connection-string-keywords"></a>Schlüsselwörter für Verbindungszeichenfolgen  
 Die folgenden Schlüsselwörter für Verbindungszeichenfolgen ermöglichen Clientanwendungen, einen SPN anzugeben.  
  
|Schlüsselwort|value|  
|-------------|-----------|  
|`ServerSPN`|Der SPN für den Server. Der Standardwert ist eine leere Zeichenfolge und bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
|`FailoverPartnerSPN`|Der SPN für den Failoverpartner. Der Standardwert ist eine leere Zeichenfolge und bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.|  
  
## <a name="connection-attributes"></a>Verbindungsattribute  
 Die folgenden Verbindungsattribute ermöglichen es Clientanwendungen, einen SPN anzugeben und eine Authentifizierungsmethode abzufragen.  
  
|Name|Typ|Verwendung|  
|----------|----------|-----------|  
|SQL_COPT_SS_SERVER_SPN<br /><br /> SQL_COPT_SS_FAILOVER_PARTNER_SPN|SQLTCHAR, read/write|Gibt den SPN für den Server an. Der Standardwert ist eine leere Zeichenfolge und bewirkt, dass [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den vorgegebenen, vom Treiber generierten SPN verwendet.<br /><br /> Dieses Attribut kann nur abgefragt werden, nachdem es programmgesteuert festgelegt wurde oder nachdem eine Verbindung geöffnet wurde. Wenn versucht wird, dieses Attribut für eine Verbindung abzufragen, die nicht geöffnet ist, und wenn dieses nicht programmgesteuert festgelegt wurde, dann wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState 08003 und der Meldung "Verbindung nicht geöffnet" protokolliert.<br /><br /> Wenn versucht wird, dieses Attribut festzulegen, wenn eine Verbindung geöffnet ist, dann wird SQL_ERROR zurückgegeben, und es wird ein Diagnosedatensatz mit SQLState HY011 und der Meldung "Der Vorgang ist zu diesem Zeitpunkt nicht gültig" protokolliert.|  
|SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD|SQLTCHAR, read-only|Gibt die für die aktuelle Verbindung verwendete Authentifizierungsmethode zurück. Der zurückgegebene Wert für die Anwendung ist der Wert, der an Windows zurückgibt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Folgende Werte sind möglich:<br /><br /> -"NTLM" wird zurückgegeben, wenn eine Verbindung mit der NTLM-Authentifizierung geöffnet wird.<br />-"Kerberos" wird zurückgegeben, wenn eine Verbindung mit der Kerberos-Authentifizierung geöffnet wird.<br /><br /> Dieses Attribut kann nur für eine geöffnete Verbindung gelesen werden, die Windows-Authentifizierung verwendet. Wenn versucht wird, dieses Attribut zu lesen, bevor eine Verbindung geöffnet wurde, dann wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState 08003 und der Meldung "Verbindung nicht geöffnet" protokolliert.<br /><br /> Wenn dieses Attribut für eine Verbindung abgefragt wird, für die nicht die Windows-Authentifizierung verwendet wurde, wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState HY092 und der Meldung "Attribut/Optionsbezeichner ungültig (SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD ist nur für vertrauenswürdige Verbindungen verfügbar)" protokolliert.<br /><br /> Wenn die Authentifizierungsmethode nicht ermittelt werden kann,dann wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState HY000 und der Meldung "Allgemeiner Fehler" protokolliert.|  
|SQL_COPT_SS_MUTUALLY_AUTHENTICATED|SQLSMALLINT, read-only|Gibt SQL_TRUE zurück, wenn der Server in der Verbindung gegenseitig authentifiziert wurde; andernfalls wird SQL_FALSE zurückgegeben.<br /><br /> Dieses Attribut kann nur für eine geöffnete Verbindung gelesen werden. Wenn versucht wird, dieses Attribut zu lesen, bevor eine Verbindung geöffnet wurde, dann wird SQL_ERROR zurückgegeben, und es wird ein Fehler mit SQLState 08003 und der Meldung "Verbindung nicht geöffnet" protokolliert.<br /><br /> Wenn dieses Attribut für eine Verbindung abgefragt wird, für die keine Windows-Authentifizierung verwendet wurde, wird SQL_FALSE zurückgegeben.|  
  
## <a name="odbc-function-support-for-specifying-spns"></a>ODBC-Funktionsunterstützung zum Angeben von SPN  
 Die folgenden ODBC-Funktionen unterstützen Clientanwendungen und SPN:  
  
-   [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md)  
  
-   [SQLConnect](../../native-client-odbc-api/sqlconnect.md)  
  
-   [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md)  
  
-   [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md)  
  
-   [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  