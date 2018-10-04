---
title: DiagnoseDatensätze und-Felder | Microsoft-Dokumentation
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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ac31a6f55e365a208bd2a4d3d8f6690693775a0d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47780240"
---
# <a name="diagnostic-records-and-fields"></a>Diagnosedatensätze und -felder
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Diagnosedatensätze sind ODBC-Umgebungs-, Verbindungs-, Anweisungs- oder Deskriptorhandles zugeordnet. Wenn eine ODBC-Funktion einen anderen Rückgabecode als SQL_SUCCESS oder SQL_INVALID_HANDLE auslöst, verfügt das von der Funktion aufgerufene Handle über zugeordnete Diagnosedatensätze mit Informations- oder Fehlermeldungen. Diese Datensätze werden so lange beibehalten, bis eine andere Funktion mit diesem Handle aufgerufen wird. Anschließend werden sie verworfen. Die Zahl der Diagnosedatensätze, die einem Handle zugeordnet sein können, ist unbegrenzt.  
  
 Es gibt zwei Arten von Diagnosedatensätzen: Header und Status. Der Headerdatensatz ist Datensatz 0; wenn es Statusdatensätze gibt, sind dies die Datensätze 1 und höher. Diagnosedatensätze enthalten andere Felder für den Headerdatensatz und die Statusdatensätze. ODBC-Komponenten können auch eigene Diagnosedatensatzfelder definieren.  
  
 Felder im Headerdatensatz enthalten allgemeine Informationen über die Ausführung einer Funktion, einschließlich Rückgabecode, Zeilenanzahl, Anzahl der Statusdatensätze und Typ der ausgeführten Anweisung. Der Headerdatensatz wird immer erstellt, es sei denn, eine ODBC-Funktion gibt SQL_INVALID_HANDLE zurück. Eine vollständige Liste der Felder im Headerdatensatz, finden Sie unter [SQLGetDiagField](../../relational-databases/native-client-odbc-api/sqlgetdiagfield.md).  
  
 Felder in den Statusdatensätzen enthalten Informationen über bestimmte Fehler oder Warnungen, die vom ODBC-Treiber-Manager, vom Treiber oder von der Datenquelle zurückgegeben werden, einschließlich SQLSTATE, systemeigener Fehlernummer, Diagnosemeldung, Spaltennummer und Zeilennummer. Statusdatensätze werden nur erstellt, wenn die Funktion SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA oder SQL_STILL_EXECUTING zurückgibt. Eine vollständige Liste der Felder in den statusdatensätzen, finden Sie unter **SQLGetDiagField**.  
  
 **SQLGetDiagRec** einen einzelnen Diagnosedatensatz zusammen mit der ODBC SQLSTATE, systemeigener Fehlernummer und diagnosemeldungsfeldern abgerufen. Diese Funktion ist ähnlich wie die ODBC 2. *X *** SQLError** Funktion. Die einfachste Fehlerbehandlungsfunktion in ODBC 3. *x* besteht darin, wiederholt aufrufen **SQLGetDiagRec** beginnend mit der *RecNumber* Parameter auf 1 festgelegt und besitzt eine Schrittweite *RecNumber* von 1 bis zum **SQLGetDiagRec** SQL_NO_DATA zurückgibt. Dies ist gleichbedeutend mit einer ODBC 2. *x* Aufruf durch eine Anwendung **SQLError** bis SQL_NO_DATA_FOUND zurückgegeben.  
  
 ODBC 3. *x* unterstützt weitaus mehr Diagnoseinformationen als ODBC 2. *X*. Diese Informationen werden gespeichert, in weiteren Feldern in Diagnosedatensätzen abgerufen, indem **SQLGetDiagField**.  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber verfügt über treiberspezifische Diagnosefelder, die mit abgerufen werden können **SQLGetDiagField**. Bezeichnungen für diese treiberspezifischen Felder werden in sqlncli.h definiert. Mit diesen Bezeichnungen rufen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Status, den Schweregrad, den Servernamen, den Prozedurnamen und die jedem Diagnosedatensatz zugeordnete Zeilennummer ab. Außerdem enthält sqlncli.h Definitionen der Codes, die der Treiber verwendet, um Transact-SQL-Anweisungen zu identifizieren, wenn eine Anwendung ruft **SQLGetDiagField** mit *DiagIdentifier* SQL_DIAG_DYNAMIC_ festgelegt FUNCTION_CODE.  
  
 **SQLGetDiagField** vom ODBC-Treiber-Manager mit Fehlerinformationen aus dem zugrunde liegenden Treiber zwischenspeichert verarbeitet wird. Der ODBC-Treiber-Manager zwischenspeichert keine treiberspezifische Diagnosefelder erst, nachdem erfolgreiche eine Verbindung hergestellt wurde. **SQLGetDiagField** gibt SQL_ERROR zurück, wenn sie aufgerufen wird, um treiberspezifische Diagnosefelder abzurufen, bevor eine erfolgreiche Verbindung abgeschlossen wurde. Wenn eine ODBC-Verbindungsfunktion SQL_SUCCESS_WITH_INFO zurückgibt, sind noch keine treiberspezifischen Diagnosefelder für die Verbindungsfunktion verfügbar. Sie können beginnen, Aufrufen von **SQLGetDiagField** für treiberspezifische Diagnosefelder erst nach der Sie einen weiteren ODBC vorgenommen haben Funktionsaufruf nach der Verbindungsfunktion.  
  
 Die meisten Fehler gemeldet werden, indem die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber kann effektiv verwenden nur die Informationen, die vom diagnostiziert werden **SQLGetDiagRec**. In einigen Fällen sind jedoch die von den treiberspezifischen Diagnosefeldern zurückgegebenen Informationen für die Fehlerdiagnose wichtig. Beim Codieren eines ODBC-fehlerhandlers für Anwendungen mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber, es ist eine gute Idee, die auch **SQLGetDiagField** abzurufenden, dass mindestens die SQL_DIAG_SS_MSGSTATE und SQL_DIAG_SS_SEVERITY treiberspezifische Felder. Wenn ein bestimmter Fehler an mehreren Orten im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Code ausgelöst werden kann, erkennt der Microsoft Software Service anhand von SQL_DIAG_SS_MSGSTATE, wo genau ein Fehler ausgelöst wurde, was mitunter für die Problemdiagnose hilfreich ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Behandlung von Fehlern und Meldungen](../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
