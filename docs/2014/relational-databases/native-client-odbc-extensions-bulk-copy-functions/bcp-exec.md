---
title: bcp_exec | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_exec
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d5ce458ea8f5874620ea0561eeea5c6ff8e56bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62689033"
---
# <a name="bcp_exec"></a>bcp_exec
  Führt ein vollständiges Massenkopieren der Daten zwischen einer Datenbanktabelle und einer Benutzerdatei aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_exec (  
HDBC   
hdbc  
,  
LPDBINT   
pnRowsProcessed  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *pnRowsProcessed*  
 Ein Zeiger auf DBINT. Die **bcp_exec** -Funktion füllt DBINT mit der Anzahl der erfolgreich kopierten Zeilen. Wenn *pnRowsProcessed* auf NULL festgelegt ist, wird es von **bcp_exec**ignoriert.  
  
## <a name="returns"></a>Rückgabe  
 SUCCEED, SUCCEED_ASYNC oder FAIL. Die **bcp_exec** -Funktion gibt SUCCEED zurück, wenn alle Zeilen kopiert wurden. **bcp_exec** gibt SUCCEED_ASYNC zurück, wenn ein asynchroner Massen Kopiervorgang noch aussteht. **bcp_exec** gibt einen Fehler zurück, wenn ein kompletter Fehler auftritt, oder wenn die Anzahl der Zeilen, die Fehler generieren, den für BCPMAXERRS mithilfe von [bcp_control](bcp-control.md)angegebenen Wert erreicht. BCPMAXERRS ist standardmäßig auf 10 festgelegt. Die BCPMAXERRS-Option wirkt sich nur auf die Syntaxfehler aus, die vom Anbieter während des Lesens der Zeilen aus der Datendatei (und nicht der Zeilen, die an den Server gesendet werden) erkannt werden. Der Server bricht den Batch ab, wenn er einen Fehler in einer Zeile erkennt. Überprüfen Sie den *pnRowsProcessed* -Parameter auf die Anzahl an erfolgreich kopierten Zeilen.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Funktion kopiert Daten aus einer Datendatei in eine Datenbanktabelle oder umgekehrt, abhängig vom Wert des *eDirection* -Parameters in [bcp_init](bcp-init.md).  
  
 Vor dem Aufrufen von **bcp_exec**rufen Sie **bcp_init** mit einem gültigen Benutzerdateinamen auf. Andernfalls wird ein Fehler ausgelöst.  
  
 **bcp_exec** ist die einzige Massen Kopierfunktion, die für eine beliebige Zeitspanne wahrscheinlich aussteht. Es ist deshalb die einzige Massenkopierfunktion, die den asynchronen Modus unterstützt. Um den asynchronen Modus festzulegen, verwenden Sie [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) , um SQL_ATTR_ASYNC_ENABLE auf SQL_ASYNC_ENABLE_ON festzulegen, bevor Sie **bcp_exec**aufrufen. Rufen Sie **bcp_exec** mit denselben Parametern auf, um den Vorgang auf Vollständigkeit zu überprüfen. Wenn das Massenkopieren noch nicht abgeschlossen wurde, gibt **bcp_exec** SUCCEED_ASYNC zurück. Außerdem wird in *pnRowsProcessed* eine Statuszahl der Anzahl der Zeilen zurückgegeben, die an den Server gesendet wurden. Für die zum Server gesendeten Zeilen wird erst ein Commit ausgeführt, wenn das Ende eines Batches erreicht wurde.  
  
 Informationen zu einem Breaking Change beim Massen kopieren ab [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]finden Sie unter [Durchführen von Massen Kopier Vorgängen &#40;ODBC-&#41;](../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
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
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
