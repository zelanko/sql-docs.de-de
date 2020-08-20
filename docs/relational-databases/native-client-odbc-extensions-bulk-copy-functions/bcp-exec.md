---
description: bcp_exec
title: bcp_exec | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_exec
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 41b4fca44f8dab8d4cb2eac1211387d27004b7c4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494140"
---
# <a name="bcp_exec"></a>bcp_exec
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Führt ein vollständiges Massenkopieren der Daten zwischen einer Datenbanktabelle und einer Benutzerdatei aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_exec (  
        HDBC hdbc,  
        LPDBINT pnRowsProcessed);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *pnRowsProcessed*  
 Ein Zeiger auf DBINT. Die **bcp_exec** -Funktion füllt DBINT mit der Anzahl der erfolgreich kopierten Zeilen. Wenn *pnRowsProcessed* auf NULL festgelegt ist, wird es von **bcp_exec**ignoriert.  
  
## <a name="returns"></a>Rückgabe  
 SUCCEED, SUCCEED_ASYNC oder FAIL. Die **bcp_exec** -Funktion gibt SUCCEED zurück, wenn alle Zeilen kopiert wurden. **bcp_exec** gibt SUCCEED_ASYNC zurück, falls ein asynchroner Massenkopiervorgang aussteht. **bcp_exec** gibt FAIL zurück, wenn ein vollständiger Fehler auftritt oder wenn die Anzahl der Zeilen, die Fehler generieren, den in BCPMAXERRS mithilfe von [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)angegebenen Wert erreicht. BCPMAXERRS ist standardmäßig auf 10 festgelegt. Die BCPMAXERRS-Option wirkt sich nur auf die Syntaxfehler aus, die vom Anbieter während des Lesens der Zeilen aus der Datendatei (und nicht der Zeilen, die an den Server gesendet werden) erkannt werden. Der Server bricht den Batch ab, wenn er einen Fehler in einer Zeile erkennt. Überprüfen Sie den *pnRowsProcessed* -Parameter auf die Anzahl an erfolgreich kopierten Zeilen.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion kopiert Daten aus einer Datendatei in eine Datenbanktabelle oder umgekehrt, abhängig vom Wert des *eDirection* -Parameters in [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md).  
  
 Vor dem Aufrufen von **bcp_exec**rufen Sie **bcp_init** mit einem gültigen Benutzerdateinamen auf. Andernfalls wird ein Fehler ausgelöst.  
  
 **bcp_exec** ist die einzige Massenkopierfunktion, die im Allgemeinen für eine beliebige Zeitlänge aussteht. Es ist deshalb die einzige Massenkopierfunktion, die den asynchronen Modus unterstützt. Um den asynchronen Modus festzulegen, verwenden Sie [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) , um SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_ON festzulegen, bevor Sie **bcp_exec**aufrufen. Rufen Sie **bcp_exec** mit denselben Parametern auf, um den Vorgang auf Vollständigkeit zu überprüfen. Wenn das Massenkopieren noch nicht abgeschlossen wurde, gibt **bcp_exec** SUCCEED_ASYNC zurück. Außerdem wird in *pnRowsProcessed* eine Statuszahl der Anzahl der Zeilen zurückgegeben, die an den Server gesendet wurden. Für die zum Server gesendeten Zeilen wird erst ein Commit ausgeführt, wenn das Ende eines Batches erreicht wurde.  
  
 Informationen zu einem Breaking Change beim Massen kopieren ab finden Sie unter [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [Durchführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Verwendung von **bcp_exec**veranschaulicht:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
