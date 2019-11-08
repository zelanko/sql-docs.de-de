---
title: Diagnosedaten Sätze und Felder | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- header records [ODBC]
- SQL Server Native Client ODBC driver, errors
- messages [ODBC], diagnostic records
- ODBC error handling, diagnostic records
- SQLGetDiagField function
- diagnostic records [ODBC]
- errors [ODBC], diagnostic records
- fields [ODBC]
- status information [ODBC]
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5bffbd7ce22bf3e1e906e68e880fb76bee36c4b3
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783658"
---
# <a name="diagnostic-records-and-fields"></a>Diagnosedatensätze und -felder
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Diagnosedatensätze sind ODBC-Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptorhandles zugeordnet. Wenn eine ODBC-Funktion einen anderen Rückgabecode als SQL_SUCCESS oder SQL_INVALID_HANDLE auslöst, verfügt das von der Funktion aufgerufene Handle über zugeordnete Diagnosedatensätze mit Informations- oder Fehlermeldungen. Diese Datensätze werden so lange beibehalten, bis eine andere Funktion mit diesem Handle aufgerufen wird. Anschließend werden sie verworfen. Die Zahl der Diagnosedatensätze, die einem Handle zugeordnet sein können, ist unbegrenzt.  
  
 Es gibt zwei Arten von Diagnosedatensätzen: Header und Status. Der Headerdatensatz ist Datensatz 0; wenn es Statusdatensätze gibt, sind dies die Datensätze 1 und höher. Diagnosedatensätze enthalten andere Felder für den Headerdatensatz und die Statusdatensätze. ODBC-Komponenten können auch eigene Diagnosedatensatzfelder definieren.  
  
 Felder im Headerdatensatz enthalten allgemeine Informationen über die Ausführung einer Funktion, einschließlich Rückgabecode, Zeilenanzahl, Anzahl der Statusdatensätze und Typ der ausgeführten Anweisung. Der Headerdatensatz wird immer erstellt, es sei denn, eine ODBC-Funktion gibt SQL_INVALID_HANDLE zurück. Eine komplette Liste der Felder im Header Daten Satz finden Sie unter [SQLGetDiagField](../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md).  
  
 Felder in den Statusdatensätzen enthalten Informationen über bestimmte Fehler oder Warnungen, die vom ODBC-Treiber-Manager, vom Treiber oder von der Datenquelle zurückgegeben werden, einschließlich SQLSTATE, systemeigener Fehlernummer, Diagnosemeldung, Spaltennummer und Zeilennummer. Statusdatensätze werden nur erstellt, wenn die Funktion SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA oder SQL_STILL_EXECUTING zurückgibt. Eine umfassende Liste der Felder in den Statusdaten Sätzen finden Sie unter **SQLGetDiagField**.  
  
 **SQLGetDiagRec** Ruft einen einzelnen Diagnosedaten Satz zusammen mit den Feldern "ODBC SQLSTATE", "Native Error Number" und "Diagnostic-Message" ab. Diese Funktion ähnelt dem ODBC 2. _x_**SQLError** -Funktion. Die einfachste Fehler Behandlungs Funktion in ODBC 3. *x* dient zum wiederholten Aufrufen von **SQLGetDiagRec** , beginnend mit dem auf 1 festgelegten Parameter " *RecNumber* " und dem erhöhen der *RecNumber* um 1, bis **SQLGetDiagRec** SQL_NO_DATA zurückgibt. Dies entspricht einem ODBC 2. *x* -Anwendung, die **SQLError** aufrufen, bis SQL_NO_DATA_FOUND zurückgegeben wird.  
  
 ODBC 3. *x* unterstützt wesentlich mehr Diagnoseinformationen als ODBC 2. *x*. Diese Informationen werden in weiteren Feldern in Diagnosedaten Sätzen gespeichert, die mit **SQLGetDiagField**abgerufen werden.  
  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verfügt über Treiber spezifische Diagnose Felder, die mit **SQLGetDiagField**abgerufen werden können. Bezeichnungen für diese treiberspezifischen Felder werden in sqlncli.h definiert. Mit diesen Bezeichnungen rufen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Status, den Schweregrad, den Servernamen, den Prozedurnamen und die jedem Diagnosedatensatz zugeordnete Zeilennummer ab. Sqlncli. h enthält außerdem Definitionen der Codes, die der Treiber zum Identifizieren von Transact-SQL-Anweisungen verwendet, wenn eine Anwendung **SQLGetDiagField** aufruft, wobei *DiagIdentifier* auf SQL_DIAG_DYNAMIC_FUNCTION_CODE festgelegt ist.  
  
 **SQLGetDiagField** wird vom ODBC-Treiber-Manager mithilfe von Fehlerinformationen verarbeitet, die er vom zugrunde liegenden Treiber zwischenspeichert. Der ODBC-Treiber-Manager speichert Treiber spezifische Diagnose Felder erst zwischen, wenn eine erfolgreiche Verbindung hergestellt wurde. **SQLGetDiagField** gibt SQL_ERROR zurück, wenn es aufgerufen wird, um Treiber spezifische Diagnose Felder zu erhalten, bevor eine erfolgreiche Verbindung hergestellt wurde. Wenn eine ODBC-Verbindungsfunktion SQL_SUCCESS_WITH_INFO zurückgibt, sind noch keine treiberspezifischen Diagnosefelder für die Verbindungsfunktion verfügbar. Sie können **SQLGetDiagField** für Treiber spezifische Diagnose Felder erst aufrufen, nachdem Sie einen weiteren ODBC-Funktionsaufruf nach der Connect-Funktion durchgeführt haben.  
  
 Die meisten Fehler, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber gemeldet werden, können nur mit den von **SQLGetDiagRec**zurückgegebenen Informationen diagnostiziert werden. In einigen Fällen sind jedoch die von den treiberspezifischen Diagnosefeldern zurückgegebenen Informationen für die Fehlerdiagnose wichtig. Beim Codieren eines ODBC-Fehler Handlers für Anwendungen, die den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber verwenden, empfiehlt es sich, auch **SQLGetDiagField** zu verwenden, um mindestens die SQL_DIAG_SS_MSGSTATE-und SQL_DIAG_SS_SEVERITY treiberspezifischen Felder abzurufen. Wenn ein bestimmter Fehler an mehreren Orten im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Code ausgelöst werden kann, erkennt der Microsoft Software Service anhand von SQL_DIAG_SS_MSGSTATE, wo genau ein Fehler ausgelöst wurde, was mitunter für die Problemdiagnose hilfreich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
