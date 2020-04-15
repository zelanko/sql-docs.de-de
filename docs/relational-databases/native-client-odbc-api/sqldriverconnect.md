---
title: SQLDriverConnect | Microsoft Docs
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
ms.openlocfilehash: 8d1455f0b91313ea137ec9c13a2d318fba0807b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302551"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber definiert Verbindungsattribute, die entweder Schlüsselwörter für Verbindungszeichenfolgen ersetzen oder verbessern. Mehrere Schlüsselwörter für Verbindungszeichenfolgen verfügen über vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber angegebene Standardwerte.  
  
 Eine Liste der schlüsselwörter, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die im Native Client ODBC-Treiber verfügbar sind, finden Sie unter [Verwenden von Verbindungszeichenfolgenschlüsselwörtern mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Weitere Informationen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu Verbindungsattributen und Treiberstandardverhalten finden Sie unter [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Eine Erläuterung der Für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] den systemeigenen Client gültigen Schlüsselwörter für Verbindungszeichenfolgen finden Sie unter Verwenden von [Verbindungszeichenfolgenschlüsselwörtern mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Wenn der **Parameterwert SQLDriverConnect**_DriverCompletion_ SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL_DRIVER_COMPLETE_REQUIRED ist, ruft der native Client ODBC-Treiber Schlüsselwortwerte aus dem angezeigten Dialogfeld ab. Wenn der Schlüsselwortwert in der Verbindungszeichenfolge übergeben wird und der Benutzer den Schlüsselwortwert nicht im Dialogfeld ändert, verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber den Wert aus der Verbindungszeichenfolge. Wenn der Wert in der Verbindungszeichenfolge nicht festgelegt wird und der Benutzer keine Zuweisung im Dialogfeld vornimmt, verwendet der Treiber den Standardwert.  
  
 **SQLDriverConnect** muss ein gültiges *WindowHandle* erhalten, wenn ein *DriverCompletion-Wert* die Anzeige des Verbindungsdialogfelds des Treibers erfordert (oder erfordern könnte). Ein ungültiges Handle gibt SQL_ERROR zurück.  
  
 Geben Sie entweder das Schlüsselwort DRIVER oder DSN an. ODBC gibt an, dass ein Treiber das äußere linke dieser beiden Schlüsselwörter verwendet und das andere ignoriert, wenn beide Schlüsselwörter angegeben sind. Wenn DRIVER angegeben ist oder der linke teils der beiden ist und der **SqlDriverConnect**_DriverCompletion-Parameterwert_ SQL_DRIVER_NOPROMPT ist, sind das SCHLÜSSELwort SERVER und ein entsprechender Wert erforderlich.  
  
 Wenn SQL_DRIVER_NOPROMPT angegeben wird, müssen Schlüsselwörter für die Benutzerauthentifizierung mit Werten vorhanden sein. Der Treiber stellt sicher, dass entweder die Zeichenfolge "Trusted_Connection=yes" oder sowohl das UID- als auch das PWD-Schlüsselwort vorhanden sind.  
  
 Wenn der *Parameterwert DriverCompletion* SQL_DRIVER_NOPROMPT oder SQL_DRIVER_COMPLETE_REQUIRED ist und die Sprache oder Datenbank aus der Verbindungszeichenfolge stammt und entweder ungültig ist, gibt **SQLDriverConnect** SQL_ERROR zurück.  
  
 Wenn der *Parameterwert DriverCompletion* SQL_DRIVER_NOPROMPT oder SQL_DRIVER_COMPLETE_REQUIRED ist und die Sprache oder Datenbank aus den ODBC-Datenquellendefinitionen stammt und entweder ungültig ist, verwendet **SQLDriverConnect** die Standardsprache oder Datenbank für die angegebene Benutzer-ID und gibt SQL_SUCCESS_WITH_INFO zurück.  
  
 Wenn der *Parameterwert DriverCompletion* SQL_DRIVER_COMPLETE oder SQL_DRIVER_PROMPT ist und die Sprache oder Datenbank ungültig ist, zeigt **SQLDriverConnect** das Dialogfeld erneut an.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall  
 Weitere Informationen zur Verwendung von **SQLDriverConnect** zum Herstellen einer Verbindung mit einem [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] Cluster finden Sie unter SQL Server Native Client Support for High [Availability, Disaster Recovery](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>SQLDriverConnect-Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPNs)  
 SQLDDriverConnect verwendet das Dialogfeld ODBC-Anmeldung, wenn die Eingabeaufforderung aktiviert ist. Damit können SPNs sowohl für den Prinzipalserver als auch für seinen Failoverpartner eingegeben werden.  
  
 SQLDriverConnect akzeptiert die neuen Verbindungszeichenfolgenschlüsselwörter **ServerSPN** und **FailoverPartnerSPN**und erkennt die neuen Verbindungsattribute SQL_COPT_SS_SERVER_SPN und SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Wenn ein Wert für ein Verbindungsattribut mehrfach angegeben wird, hat ein programmgesteuert festgelegter Wert Vorrang vor dem Wert in einem DSN und einem Wert in einer Verbindungszeichenfolge. Ein Wert in einem DSN hat Vorrang vor einem Wert in einer Verbindungszeichenfolge.  
  
 Wenn eine Verbindung hergestellt wird, legt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client für SQL_COPT_SS_MUTUALLY_AUTHENTICATED und SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD die für das Herstellen der Verbindung zu verwendende Authentifizierungsmethode fest.  
  
 Weitere Informationen zu SPNs finden Sie unter [Dienstprinzipalnamen &#40;SPNs&#41; in Clientverbindungen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Beispiele  
 Der folgende Aufruf veranschaulicht die geringste Datenmenge, die für **SQLDriverConnect**erforderlich ist:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Die folgenden Verbindungszeichenfolgen veranschaulichen die erforderlichen Mindestdaten, wenn der *Parameterwert DriverCompletion* SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLDriverConnect-Funktion](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET ANSI_NULLS &#40;Transact-SQL-&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL-&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
