---
title: SQLDriverConnect | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1e8b52f4940a60e464f9ea4405ddd421bb9b48d4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68035638"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber definiert Verbindungsattribute, die entweder Schlüsselwörter für Verbindungszeichenfolgen ersetzen oder verbessern. Mehrere Schlüsselwörter für Verbindungszeichenfolgen verfügen über vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber angegebene Standardwerte.  
  
 Eine Liste der verfügbaren in Schlüsselwörter der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verbindungsattributen und Standardverhalten von Treibern finden Sie unter [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
 Eine Erläuterung der Schlüsselwörter für Verbindungszeichenfolgen, die für die gültig sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Wenn die **SQLDriverConnect**_DriverCompletion_ Parameterwert ist, SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE oder sql_driver_complete_required lautet, den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber Ruft Werte aus dem angezeigten Dialogfeld ab. Wenn der Schlüsselwortwert in der Verbindungszeichenfolge übergeben wird und der Benutzer den Schlüsselwortwert nicht im Dialogfeld ändert, verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber den Wert aus der Verbindungszeichenfolge. Wenn der Wert in der Verbindungszeichenfolge nicht festgelegt wird und der Benutzer keine Zuweisung im Dialogfeld vornimmt, verwendet der Treiber den Standardwert.  
  
 **SQLDriverConnect** zugewiesen werden, der einen gültigen *WindowHandle* Wenn ein *DriverCompletion* Wert die Anzeige des Verbindungsdialogfelds des Treibers erfordert (oder erfordern könnte). Ein ungültiges Handle gibt SQL_ERROR zurück.  
  
 Geben Sie entweder das Schlüsselwort DRIVER oder DSN an. ODBC gibt an, dass ein Treiber das äußere linke dieser beiden Schlüsselwörter verwendet und das andere ignoriert, wenn beide Schlüsselwörter angegeben sind. Wenn DRIVER angegeben ist, oder das äußere linke der beiden Komponenten, und die **SQLDriverConnect**_DriverCompletion_ -Parameterwert SQL_DRIVER_NOPROMPT, das SERVER-Schlüsselwort und ein entsprechenden Wert sind erforderlich.  
  
 Wenn SQL_DRIVER_NOPROMPT angegeben wird, müssen Schlüsselwörter für die Benutzerauthentifizierung mit Werten vorhanden sein. Der Treiber stellt sicher, dass entweder die Zeichenfolge "Trusted_Connection=yes" oder sowohl das UID- als auch das PWD-Schlüsselwort vorhanden sind.  
  
 Wenn die *DriverCompletion* -Parameterwert SQL_DRIVER_NOPROMPT oder sql_driver_complete_required lautet und die Sprache oder Datenbank die Verbindungszeichenfolge stammt und ungültig ist, **SQLDriverConnect**gibt SQL_ERROR zurück.  
  
 Wenn die *DriverCompletion* -Parameterwert SQL_DRIVER_NOPROMPT oder sql_driver_complete_required lautet und die Sprache oder Datenbank die ODBC-Datenquellendefinitionen stammt und ungültig ist, **SQLDriverConnect**  verwendet die standardmäßige Sprache oder Datenbank für die angegebenen Benutzer-ID und gibt SQL_SUCCESS_WITH_INFO zurück.  
  
 Wenn die *DriverCompletion* Parameterwert ist, SQL_DRIVER_COMPLETE oder sql_driver_prompt lautet und die Sprache oder Datenbank ungültig ist, wird **SQLDriverConnect** das Dialogfeld erneut an.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall  
 Weitere Informationen zur Verwendung von **SQLDriverConnect** zum Herstellen einer Verbindung mit einer [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, finden Sie unter [SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>SQLDriverConnect-Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPNs)  
 SQLDDriverConnect verwendet den Anmeldenamen für die ODBC-Anmeldungsdialogfeld, wenn aufforderungen aktiviert ist. Damit können SPNs sowohl für den Prinzipalserver als auch für seinen Failoverpartner eingegeben werden.  
  
 SQLDriverConnect akzeptiert die neuen Schlüsselwörter für Verbindungszeichenfolgen **"serverspn"** und **FailoverPartnerSPN**, und erkennt die neuen Verbindungsattribute SQL_COPT_SS_SERVER_SPN und SQL_COPT_SS_ FAILOVER_PARTNER_SPN.  
  
 Wenn ein Wert für ein Verbindungsattribut mehrfach angegeben wird, hat ein programmgesteuert festgelegter Wert Vorrang vor dem Wert in einem DSN und einem Wert in einer Verbindungszeichenfolge. Ein Wert in einem DSN hat Vorrang vor einem Wert in einer Verbindungszeichenfolge.  
  
 Wenn eine Verbindung hergestellt wird, legt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client für SQL_COPT_SS_MUTUALLY_AUTHENTICATED und SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD die für das Herstellen der Verbindung zu verwendende Authentifizierungsmethode fest.  
  
 Weitere Informationen zu SPNs finden Sie unter [Service Principal Names &#40;SPNs&#41; in Clientverbindungen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Beispiele  
 Der folgende Aufruf illustriert die Mindestdatenmenge für **SQLDriverConnect**:  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 Die folgenden Verbindungszeichenfolgen illustrieren die Mindestdatenmenge bei der *DriverCompletion* -Parameterwert SQL_DRIVER_NOPROMPT:  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [SQLDriverConnect-Funktion](https://go.microsoft.com/fwlink/?LinkId=59340)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SET ANSI_NULLS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-nulls-transact-sql.md)   
 [SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-warnings-transact-sql.md)  
  
  
