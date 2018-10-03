---
title: Verarbeiten von Ergebnissen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], about result sets
- SQLRowCount function
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- COMPUTE clause
- result sets [ODBC]
- COMPUTE BY clause
ms.assetid: 61a8db19-6571-47dd-84e8-fcc97cb60b45
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 80700d67ddf4a6976e9212370cb6edf3f72c6e6c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764498"
---
# <a name="processing-results-odbc"></a>Verarbeiten von Ergebnissen (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Wenn eine Anwendung eine SQL-Anweisung übermittelt, gibt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] alle resultierenden Daten als ein oder mehrere Resultsets zurück. Ein Resultset ist ein Satz von Zeilen und Spalten, die den Kriterien der Abfrage entsprechen. SELECT-Anweisungen, Katalogfunktionen sowie einige gespeicherte Prozeduren erzeugen Resultsets, die für eine Anwendung in der Form von tabellarischen Daten verfügbar gemacht werden. Wenn es sich bei der ausgeführten SQL-Anweisung um eine gespeicherte Prozedur, einen Batch mit mehreren Befehlen oder eine SELECT-Anweisung mit Schlüsselwörtern handelt, ergeben sich daraus mehrere zu verarbeitende Resultsets.  
  
 Auch ODBC-Katalogfunktionen können Daten abrufen. Z. B. [SQLColumns](../../relational-databases/native-client-odbc-api/sqlcolumns.md) Ruft Daten über Spalten in der Datenquelle ab. Diese Resultsets können 0 (null) oder mehr Zeilen enthalten.  
  
 Andere SQL-Anweisungen, z. B. GRANT oder REVOKE, geben keine Resultsets zurück. Bei diesen Anweisungen der Rückgabecode von **SQLExecute** oder **SQLExecDirect** ist in der Regel der einzige Hinweis darauf der Anweisung war erfolgreich.  
  
 Jede INSERT-, UPDATE- und DELETE-Anweisung gibt ein Resultset zurück, das nur die Anzahl der von der Änderung betroffenen Zeilen enthält. Diese Anzahl wird verfügbar, wenn die Anwendung ruft versucht [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md). ODBC 3. *x* -Anwendungen müssen entweder Aufruf **SQLRowCount** legen Sie zum Abrufen des Ergebnisses oder [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md) , ihn abzubrechen. Wenn eine Anwendung einen Batch oder die gespeicherte Prozedur, die mit mehreren INSERT-, Update- oder DELETE-Anweisungen ausführt, das Resultset jeder änderungsanweisung verarbeitet werden muss mit **SQLRowCount** oder abgebrochen wird, verwenden **SQLMoreResults**. Die Anzahlangaben können durch eine SET NOCOUNT ON-Anweisung im Batch oder in der gespeicherten Prozedur annulliert werden.  
  
 Transact-SQL enthält die SET NOCOUNT-Anweisung. Wenn die NOCOUNT-Option auf festgelegt ist, gibt SQL Server nicht die Anzahl der von einer Anweisung betroffenen Zeilen zurück und **SQLRowCount** gibt 0 zurück. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiberversion führt eine treiberspezifische [SQLGetStmtAttr](../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) option, SQL_SOPT_SS_NOCOUNT_STATUS, um zu melden, ob die NOCOUNT-Option aktiviert oder deaktiviert ist. Jederzeit **SQLRowCount** 0 zurückgibt, ist die Anwendung sollte SQL_SOPT_SS_NOCOUNT_STATUS testen. Wenn SQL_NC_ON zurückgegeben wird, wird den Wert 0 aus **SQLRowCount** gibt nur an, dass SQL Server keine Zeilenanzahl zurückgegeben hat. Wenn SQL_NC_OFF zurückgegeben wird, bedeutet dies, dass NOCOUNT deaktiviert ist und der Wert 0 aus **SQLRowCount** gibt an, dass alle Zeilen nicht in die Anweisung ausgewirkt hat. Anwendungen sollten keine zeigt den Wert der **SQLRowCount** Wenn SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF ist. Große Batches oder gespeicherte Prozeduren können mehrere SET NOCOUNT-Anweisungen enthalten. Daher kann der Programmierer nicht davon ausgehen, dass SQL_SOPT_SS_NOCOUNT_STATUS konstant bleibt. Die Option sollte jedes Mal getestet werden **SQLRowCount** gibt 0 zurück.  
  
 Mehrere andere Transact-SQL-Anweisungen geben ihre Daten in Meldungen statt in Resultsets zurück. Wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber diese Meldungen empfängt, die er SQL_SUCCESS_WITH_INFO zurückgegeben. Damit können die Anwendung wissen, dass informationsmeldungen verfügbar sind. Die Anwendung kann dann aufrufen **SQLGetDiagRec** um diese Meldungen abzurufen. Die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen, die auf diese Weise funktionieren, sind folgende:  
  
-   DBCC  
  
-   SET SHOWPLAN (mit früheren Versionen von SQL Server verfügbar)  
  
-   SET STATISTICS  
  
-   PRINT  
  
-   RAISERROR  
  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber gibt SQL_ERROR nach einem RAISERROR mit einem Schweregrad von 11 oder höher. Ist der Schweregrad von RAISERROR 19 oder mehr, wird auch die Verbindung unterbrochen.  
  
 Zum Verarbeiten der Resultsets aus einer SQL-Anweisung geht die Anwendung folgendermaßen vor:  
  
-   Sie bestimmt die Charakteristika des Resultsets.  
  
-   Sie bindet die Spalten an Programmvariable.  
  
-   Sie ruft einen einzelnen Wert, eine ganze Zeile mit Werten oder mehrere Zeilen mit Werten ab.  
  
-   Sie überprüft, ob weitere Resultsets vorhanden sind, und wenn dies der Fall ist, ermittelt sie die Charakteristika des neuen Resultsets.  
  
 Der Prozess des Abrufens von Zeilen aus der Datenquelle und deren Rückgabe an die Anwendung wird "Fetching" (Abrufen) genannt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Bestimmen der Eigenschaften eines Resultsets &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
-   [Zuweisen von Speicher](../../relational-databases/native-client-odbc-results/assigning-storage.md)  
  
-   [Abrufen von Ergebnisdaten](../../relational-databases/native-client-odbc-results/fetching-result-data.md)  
  
-   [Zuordnen von Datentypen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/mapping-data-types-odbc.md)  
  
-   [Datentypverwendung](../../relational-databases/native-client-odbc-results/data-type-usage.md)  
  
-   [Automatische Übersetzung der Zeichendaten](../../relational-databases/native-client-odbc-results/autotranslation-of-character-data.md)  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [Verarbeiten von Ergebnissen: Themen zur Vorgehensweise &#40;ODBC&#41;](http://msdn.microsoft.com/library/772d9064-c91d-4cac-8b60-fcc16bf76e10)  
  
  
