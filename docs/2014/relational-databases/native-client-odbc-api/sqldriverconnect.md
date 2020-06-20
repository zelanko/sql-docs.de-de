---
title: SQLDriverConnect | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 40691dfb381883b59155607fb56f4933820e3e44
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022644"
---
# <a name="sqldriverconnect"></a>SQLDriverConnect
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber definiert Verbindungsattribute, die entweder Schlüsselwörter für Verbindungszeichenfolgen ersetzen oder verbessern. Mehrere Schlüsselwörter für Verbindungszeichenfolgen verfügen über vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber angegebene Standardwerte.  
  
 Eine Liste der Schlüsselwörter, die im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verfügbar sind, finden [Sie unter Verwenden von Verbindungs Zeichenfolgen-Schlüsselwörtern mit SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Weitere Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verbindungs Attributen und Standardverhalten von Treibern finden Sie unter [SQLSetConnectAttr](sqlsetconnectattr.md).  
  
 Eine Erläuterung der Schlüsselwörter für Verbindungs Zeichenfolgen, die für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client gültig sind, finden [Sie unter Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Wenn der `SQLDriverConnect` Wert für den *DriverCompletion* -Parameter SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE oder SQL_DRIVER_COMPLETE_REQUIRED ist, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ruft der Native Client-ODBC-Treiber Schlüsselwort Werte aus dem angezeigten Dialogfeld ab. Wenn der Schlüsselwortwert in der Verbindungszeichenfolge übergeben wird und der Benutzer den Schlüsselwortwert nicht im Dialogfeld ändert, verwendet der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber den Wert aus der Verbindungszeichenfolge. Wenn der Wert in der Verbindungszeichenfolge nicht festgelegt wird und der Benutzer keine Zuweisung im Dialogfeld vornimmt, verwendet der Treiber den Standardwert.  
  
 `SQLDriverConnect`muss ein gültiges *WindowHandle* erhalten, wenn ein *DriverCompletion* -Wert die Anzeige des Dialog Felds Verbindung des Treibers erfordert (oder möglicherweise erfordert). Ein ungültiges Handle gibt SQL_ERROR zurück.  
  
 Geben Sie entweder das Schlüsselwort DRIVER oder DSN an. ODBC gibt an, dass ein Treiber das äußere linke dieser beiden Schlüsselwörter verwendet und das andere ignoriert, wenn beide Schlüsselwörter angegeben sind. Wenn der Treiber angegeben ist oder der äußteste der beiden ist und der Wert des `SQLDriverConnect` *DriverCompletion* -Parameters SQL_DRIVER_NOPROMPT ist, sind das Server Schlüsselwort und ein entsprechender Wert erforderlich.  
  
 Wenn SQL_DRIVER_NOPROMPT angegeben wird, müssen Schlüsselwörter für die Benutzerauthentifizierung mit Werten vorhanden sein. Der Treiber stellt sicher, dass entweder die Zeichenfolge "Trusted_Connection=yes" oder sowohl das UID- als auch das PWD-Schlüsselwort vorhanden sind.  
  
 Wenn der Wert für den *DriverCompletion* -Parameter SQL_DRIVER_NOPROMPT oder SQL_DRIVER_COMPLETE_REQUIRED ist und die Sprache oder Datenbank aus der Verbindungs Zeichenfolge stammt und ungültig ist, wird `SQLDriverConnect` SQL_ERROR zurückgegeben.  
  
 Wenn der Wert für den *DriverCompletion* -Parameter SQL_DRIVER_NOPROMPT oder SQL_DRIVER_COMPLETE_REQUIRED ist und die Sprache oder Datenbank aus den ODBC-Datenquellen Definitionen stammt und entweder ungültig ist, `SQLDriverConnect` verwendet die Standardsprache oder-Datenbank für die angegebene Benutzer-ID und gibt SQL_SUCCESS_WITH_INFO zurück.  
  
 Wenn der Wert für den *DriverCompletion* -Parameter SQL_DRIVER_COMPLETE oder SQL_DRIVER_PROMPT ist und die Sprache oder Datenbank ungültig ist, wird `SQLDriverConnect` das Dialogfeld erneut angezeigt.  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a>SQLDriverConnect-Unterstützung für hohe Verfügbarkeit, Wiederherstellung im Notfall  
 Weitere Informationen zum `SQLDriverConnect` Herstellen einer Verbindung mit einem Cluster mithilfe von [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] finden Sie [unter SQL Server Native Client-Unterstützung für hohe Verfügbarkeit und Notfall Wiederherstellung](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a>SQLDriverConnect-Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPNs)  
 SQLDDriverConnect verwendet das ODBC-Anmelde Dialogfeld, wenn die Eingabeaufforderung aktiviert ist. Damit können SPNs sowohl für den Prinzipalserver als auch für seinen Failoverpartner eingegeben werden.  
  
 SQLDriverConnect akzeptiert die neuen Verbindungs Zeichenfolgen `ServerSPN` -Schlüsselwörter und und `FailoverPartnerSPN` erkennt die neuen Verbindungs Attribute SQL_COPT_SS_SERVER_SPN und SQL_COPT_SS_FAILOVER_PARTNER_SPN.  
  
 Wenn ein Wert für ein Verbindungsattribut mehrfach angegeben wird, hat ein programmgesteuert festgelegter Wert Vorrang vor dem Wert in einem DSN und einem Wert in einer Verbindungszeichenfolge. Ein Wert in einem DSN hat Vorrang vor einem Wert in einer Verbindungszeichenfolge.  
  
 Wenn eine Verbindung hergestellt wird, legt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client für SQL_COPT_SS_MUTUALLY_AUTHENTICATED und SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD die für das Herstellen der Verbindung zu verwendende Authentifizierungsmethode fest.  
  
 Weitere Informationen zu SPNs finden Sie unter [Dienst Prinzipal Namen &#40;SPNs&#41; in Client Verbindungen &#40;ODBC-&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="examples"></a>Beispiele  
 Der folgende-Befehl veranschaulicht die geringste Menge an Daten, die für erforderlich ist `SQLDriverConnect` :  
  
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
 [Details zur ODBC-API-Implementierung](odbc-api-implementation-details.md)   
 [Festlegen ANSI_NULLS &#40;Transact-SQL-&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql)   
 [Festlegen ANSI_PADDING &#40;Transact-SQL-&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)   
 [SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
