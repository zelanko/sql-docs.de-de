---
title: SQLDriverConnect | Microsoft-Dokumentation
description: Erfahren Sie mehr über SQLDriverConnect-Verbindungs Attribute und Unterstützung für hohe Verfügbarkeit/Notfall Wiederherstellung und SPNs im SQL Server Native Client ODBC-Treibers.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d136c48efad1a0a888bcce2650db4596954643b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85789286"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber definiert Verbindungsattribute, die entweder Schlüsselwörter für Verbindungszeichenfolgen ersetzen oder verbessern. Mehrere Schlüsselwörter für Verbindungszeichenfolgen verfügen über vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber angegebene Standardwerte.  
  
 Eine Liste der Schlüsselwörter, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verfügbar sind, finden [Sie unter Verwenden von Verbindungs Zeichenfolgen-Schlüsselwörtern mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungs Attributen und Standardverhalten von Treibern finden Sie unter [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Eine Erläuterung der Schlüsselwörter für Verbindungs Zeichenfolgen, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client gültig sind, finden [Sie unter Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Wenn der Wert für den_DriverCompletion_ -Parameter von **SQLDriverConnect**SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruft der Native Client-ODBC-Treiber Schlüsselwort Werte aus dem angezeigten Dialogfeld ab. Wenn der Schlüsselwortwert in der Verbindungszeichenfolge übergeben wird und der Benutzer den Schlüsselwortwert nicht im Dialogfeld ändert, verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber den Wert aus der Verbindungszeichenfolge. Wenn der Wert in der Verbindungszeichenfolge nicht festgelegt wird und der Benutzer keine Zuweisung im Dialogfeld vornimmt, verwendet der Treiber den Standardwert.  
  
 **SQLDriverConnect** muss ein gültiges *WindowHandle* zugewiesen werden, wenn ein *DriverCompletion* -Wert die Anzeige des Verbindungs Dialogfelds des Treibers erfordert (oder möglicherweise erfordert). Ein ungültiges Handle gibt SQL_ERROR zurück.  
  
 Geben Sie entweder das Schlüsselwort DRIVER oder DSN an. ODBC gibt an, dass ein Treiber das äußere linke dieser beiden Schlüsselwörter verwendet und das andere ignoriert, wenn beide Schlüsselwörter angegeben sind. Wenn der Treiber angegeben ist oder der äußteste der beiden ist und der Wert des Parameters **SQLDriverConnect**_DriverCompletion_ SQL_DRIVER_NOPROMPT ist, sind das Server Schlüsselwort und ein entsprechender Wert erforderlich.  
  
 Wenn SQL_DRIVER_NOPROMPT angegeben wird, müssen Schlüsselwörter für die Benutzerauthentifizierung mit Werten vorhanden sein. Der Treiber stellt sicher, dass entweder die Zeichenfolge "Trusted_Connection=yes" oder sowohl das UID- als auch das PWD-Schlüsselwort vorhanden sind.  
  
 Wenn der Wert für den *DriverCompletion* -Parameter SQL_DRIVER_NOPROMPT oder SQL_DRIVER_COMPLETE_REQUIRED ist und die Sprache oder Datenbank aus der Verbindungs Zeichenfolge stammt und beide ungültig sind, gibt **SQLDriverConnect** SQL_ERROR zurück.  
  
 Wenn der Wert für den *DriverCompletion* -Parameter SQL_DRIVER_NOPROMPT oder SQL_DRIVER_COMPLETE_REQUIRED ist und die Sprache oder Datenbank aus den ODBC-Datenquellen Definitionen stammt und entweder ungültig ist, verwendet **SQLDriverConnect** die Standardsprache oder-Datenbank für die angegebene Benutzer-ID und gibt SQL_SUCCESS_WITH_INFO zurück.  
  
 Wenn der Wert für den *DriverCompletion* -Parameter SQL_DRIVER_COMPLETE oder SQL_DRIVER_PROMPT ist und die Sprache oder Datenbank ungültig ist, wird das Dialogfeld von **SQLDriverConnect** erneut angezeigt.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall  
 Weitere Informationen zur Verwendung von **SQLDriverConnect** zum Herstellen einer Verbindung mit einem [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] Cluster finden Sie [unter SQL Server Native Client-Unterstützung für hohe Verfügbarkeit und Notfall Wiederherstellung](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>SQLDriverConnect-Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPNs)  
 SQLDDriverConnect verwendet das ODBC-Anmelde Dialogfeld, wenn die Eingabeaufforderung aktiviert ist. Damit können SPNs sowohl für den Prinzipalserver als auch für seinen Failoverpartner eingegeben werden.  
  
 SQLDriverConnect akzeptiert die neuen Verbindungs Zeichenfolgen-Schlüsselwörter **ServerSPN** und **FailoverPartnerSPN**und erkennt die neuen Verbindungs Attribute SQL_COPT_SS_SERVER_SPN und SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Wenn ein Wert für ein Verbindungsattribut mehrfach angegeben wird, hat ein programmgesteuert festgelegter Wert Vorrang vor dem Wert in einem DSN und einem Wert in einer Verbindungszeichenfolge. Ein Wert in einem DSN hat Vorrang vor einem Wert in einer Verbindungszeichenfolge.  
  
 Wenn eine Verbindung hergestellt wird, legt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client für SQL_COPT_SS_MUTUALLY_AUTHENTICATED und SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD die für das Herstellen der Verbindung zu verwendende Authentifizierungsmethode fest.  
  
 Weitere Informationen zu SPNs finden Sie unter [Dienst Prinzipal Namen &#40;SPNs&#41; in Client Verbindungen &#40;ODBC-&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Beispiele  
 Der folgende-Befehl veranschaulicht die geringste Menge an Daten, die für **SQLDriverConnect**erforderlich ist:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Die folgenden Verbindungs Zeichenfolgen veranschaulichen die minimal erforderlichen Daten, wenn der Wert für den *DriverCompletion* -Parameter SQL_DRIVER_NOPROMPT ist:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLDriverConnect-Funktion](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [Details zur ODBC-API-Implementierung](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Festlegen ANSI_NULLS &#40;Transact-SQL-&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [Festlegen ANSI_PADDING &#40;Transact-SQL-&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
