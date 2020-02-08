---
title: Nativ kompilierte gespeicherte Prozeduren – Datenzugriffsanwendungen
ms.custom: seo-dt-2019
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 9cf6c5ff-4548-401a-b3ec-084f47ff0eb8
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: abc9aa1f61d241f3fe24196ad9d8ad4244b951f2
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "74412767"
---
# <a name="calling-natively-compiled-stored-procedures-from-data-access-applications"></a>Aufrufen von systemintern kompilierten gespeicherten Prozeduren über Datenzugriffsanwendungen

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Dieses Thema enthält Informationen zum Aufrufen systemintern kompilierter gespeicherter Prozeduren über Datenzugriffsanwendungen.

## <a name="guidance-points"></a>Anleitungspunkte

- Cursor können keine systemintern kompilierte gespeicherte Prozedur durchlaufen.

- Das Aufrufen von nativ kompilierten gespeicherten Prozeduren über CLR-Module mithilfe der Kontextverbindung wird nicht unterstützt.

### <a name="sqlclient"></a>SqlClient

- Bei SqlClient wird nicht zwischen *vorbereiteter* und *direkter* Ausführung unterschieden. Führen Sie gespeicherte Prozeduren mit SqlCommand mit CommandType = CommandType.StoredProcedure aus.

- SqlClient unterstützt keine vorbereiteten RPC-Prozeduraufrufe.

- Das Abrufen von Informationen vom Typ „Nur Schema“ (Metadatenermittlung) zu den Resultsets, die durch eine nativ kompilierte gespeicherte Prozedur (CommandType.SchemaOnly) zurückgegeben werden, wird von SqlClient nicht unterstützt.
  - Verwenden Sie stattdessen [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).

### <a name="includessnoversionincludesssnoversion-mdmd-native-client"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client

- Das Abrufen von Informationen vom Typ „Nur Schema“ (Metadatenermittlung) zu den Resultsets, die durch eine nativ kompilierte gespeicherte Prozedur zurückgegeben werden, wird von Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client vor [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] nicht unterstützt.
  - Verwenden Sie stattdessen [sp_describe_first_result_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md).

### <a name="odbc"></a>ODBC

Die folgenden Empfehlungen gelten für Aufrufe der systemintern kompilierten gespeicherten Prozedur mithilfe des ODBC-Treibers in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.

*Einmaliger Aufruf:* Die effizienteste Methode, eine gespeicherte Prozedur einmal aufzurufen ist, einen direkten RPC-Aufruf mithilfe von **SQLExecDirect** und ODBC CALL-Klauseln auszugeben. Verwenden Sie nicht die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung **EXECUTE**. Wenn eine gespeicherte Prozedur mehrmals aufgerufen wird, ist die vorbereitete Ausführung effizienter.

*Mehrmaliger Aufruf:* Das effizienteste Verfahren, um eine gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Prozedur mehrmals aufrufen ist, vorbereitete RPC-Prozeduraufrufe zu verwenden. Vorbereitete RPC-Aufrufe werden mithilfe des ODBC-Treibers von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client folgendermaßen ausgeführt:

1. Herstellen einer Verbindung mit der Datenbank
2. Binden der Parameter mithilfe von **SQLBindParameter**
3. Vorbereiten des Prozeduraufrufs mit **SQLPrepare**
4. Mehrmaliges Ausführen der gespeicherte Prozedur mit **SQLExecute**

#### <a name="c-code-for-odbc"></a>C-Code für ODBC

Das folgende C-Codefragment veranschaulicht die vorbereitete Ausführung einer gespeicherten Prozedur zum Hinzufügen von Einzelposten zu einer Bestellung. **SQLPrepare** wird nur einmal aufgerufen. **SQLExecute** wird mehrmals aufgerufen, nämlich einmal pro Prozedurausführung.

```cpp
// Bind parameters
// 1 - OrdNo
SQLRETURN returnCode = SQLBindParameter(
                     hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0,
                     &order.OrdNo, sizeof(SQLINTEGER), NULL);
if (returnCode != SQL_SUCCESS && returnCode != SQL_SUCCESS_WITH_INFO) {
   ODBCError(henv, hdbc, hstmt, NULL, true);
   exit(-1);
}

// 2, 3, 4 - ItemNo, ProdCode, Qty
...

// Prepare stored procedure
returnCode = SQLPrepare(hstmt, (SQLTCHAR *) _T("{call ItemInsert(?, ?, ?, ?)}"),
                        SQL_NTS);

for (unsigned int i = 0; i < order.ItemCount; i++) {
   ItemNo = order.ItemNo[i];
   ProdCode = order.ProdCode[i];
   Qty = order.Qty[i];

   // Execute stored procedure
   returnCode = SQLExecute(hstmt);
   if (returnCode != SQL_SUCCESS && returnCode != SQL_SUCCESS_WITH_INFO) {
      ODBCError(henv, hdbc, hstmt, NULL, true);
      exit(-1);
   }
}
```

## <a name="using-odbc-to-execute-a-natively-compiled-stored-procedure"></a>Ausführen einer nativ kompilierten gespeicherten Prozedur mithilfe von ODBC

In diesem Beispiel wird veranschaulicht, wie mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treibers Parameter gebunden und gespeicherte Prozeduren ausgeführt werden. Das Beispiel wird zu einer Konsolenanwendung kompiliert, die mithilfe der direkten Ausführung einen einzelnen Auftrag einfügt und mithilfe der vorbereiteten Ausführung die Auftragsdetails einfügt.

So führen Sie dieses Beispiel aus:

1. Erstellen Sie eine Beispieldatenbank mit einer speicheroptimierten Datendateigruppe. Informationen zum Erstellen einer Datenbank mithilfe einer speicheroptimierten Datendateigruppe finden Sie unter [Erstellen einer speicheroptimierten Tabelle und einer nativ kompilierten gespeicherten Prozedur](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md).

2. Erstellen Sie eine ODBC-Datenquelle mit dem Namen PrepExecSample, die auf die Datenbank zeigt. Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Treiber. Sie können das Beispiel auch ändern und den [Microsoft ODBC-Treiber für SQL Server](https://msdn.microsoft.com/library/jj730314.aspx)verwenden.

3. Führen Sie das [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skript (unten) in der Beispieldatenbank aus.

4. Kompilieren Sie das Beispiel, und führen Sie es aus.

5. Vergewissern Sie sich, dass das Programm erfolgreich ausgeführt wurde, indem Sie den Inhalt der Tabellen abfragen:

    ```sql
    SELECT * FROM dbo.Ord
    ```

    ```sql
    SELECT * FROM dbo.Item
    ```

## <a name="preliminary-transact-sql"></a>Vorläufige Transact-SQL

Der folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Code erstellt die speicheroptimierten Datenbankobjekte.

```sql
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.OrderInsert'))
  DROP PROCEDURE dbo.OrderInsert  
GO
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.ItemInsert'))
  DROP PROCEDURE dbo.ItemInsert  
GO  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.Ord'))
  DROP TABLE dbo.Ord  
GO  
IF EXISTS (SELECT * FROM SYS.OBJECTS WHERE OBJECT_ID=OBJECT_ID('dbo.Item'))
  DROP TABLE dbo.Item  
GO

CREATE TABLE dbo.Ord  
(  
   OrdNo INTEGER NOT NULL PRIMARY KEY NONCLUSTERED,  
   OrdDate DATETIME NOT NULL,   
   CustCode VARCHAR(5) NOT NULL)   
 WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE TABLE dbo.Item  
(  
   OrdNo INTEGER NOT NULL,   
   ItemNo INTEGER NOT NULL,   
   ProdCode INTEGER NOT NULL,   
   Qty INTEGER NOT NULL,  
   CONSTRAINT PK_Item PRIMARY KEY NONCLUSTERED (OrdNo,ItemNo))  
   WITH (MEMORY_OPTIMIZED=ON)  
GO  
  
CREATE PROCEDURE dbo.OrderInsert(
    @OrdNo INTEGER, @CustCode VARCHAR(5))  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(   TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
   LANGUAGE = 'english')  
  
  DECLARE @OrdDate datetime = GETDATE();  
  INSERT INTO dbo.Ord (OrdNo, CustCode, OrdDate)
      VALUES (@OrdNo, @CustCode, @OrdDate);
END  
GO  
  
CREATE PROCEDURE dbo.ItemInsert(
    @OrdNo INTEGER, @ItemNo INTEGER, @ProdCode INTEGER, @Qty INTEGER)
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH  
(   TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
   LANGUAGE = N'us_english')  
  
  INSERT INTO dbo.Item (OrdNo, ItemNo, ProdCode, Qty)
      VALUES (@OrdNo, @ItemNo, @ProdCode, @Qty)
END  
GO  
```

## <a name="c-code"></a>C-Code

Im Folgenden das C-Codelisting.

```cpp
// compile with: user32.lib odbc32.lib
#pragma once  
#define WIN32_LEAN_AND_MEAN  // Exclude rarely-used stuff from Windows headers.
#include <stdio.h>  
#include <stdlib.h>  
#include <tchar.h>  
#include <windows.h>  
#include "sql.h"  
#include "sqlext.h"  
#include "sqlncli.h"  
  
// cardinality of order item related array variables
#define ITEM_ARRAY_SIZE 20  
  
// struct to pass order entry data  
typedef struct OrdEntry_struct {  
   SQLINTEGER OrdNo;  
   SQLTCHAR CustCode[6];  
   SQLUINTEGER ItemCount;  
   SQLINTEGER ItemNo[ITEM_ARRAY_SIZE];  
   SQLINTEGER ProdCode[ITEM_ARRAY_SIZE];  
   SQLINTEGER Qty[ITEM_ARRAY_SIZE];  
} OrdEntryData;  
  
SQLHANDLE henv, hdbc, hstmt;  
  
void ODBCError(
      SQLHANDLE henv, SQLHANDLE hdbc,
      SQLHANDLE hstmt, SQLHANDLE hdesc,
      bool ShowError)
{  
   SQLRETURN r = 0;  
   SQLTCHAR szSqlState[6] = {0};  
   SQLINTEGER fNativeError = 0;  
   SQLTCHAR szErrorMsg[256] = {0};  
   SQLSMALLINT cbErrorMsgMax = sizeof(szErrorMsg) - 1;
   SQLSMALLINT cbErrorMsg = 0;  
   TCHAR text[1024] = {0}, title[256] = {0};  
  
   if (hdesc != NULL)  
      r = SQLGetDiagRec(SQL_HANDLE_DESC, hdesc, 1, szSqlState,
              &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);
   else {  
      if (hstmt != NULL)  
         r = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, 1, szSqlState,
                 &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);
      else {  
         if (hdbc != NULL)  
            r = SQLGetDiagRec(SQL_HANDLE_DBC, hdbc, 1, szSqlState,
                    &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);
         else  
            r = SQLGetDiagRec(SQL_HANDLE_ENV, henv, 1, szSqlState,
                    &fNativeError, szErrorMsg, cbErrorMsgMax, &cbErrorMsg);
      }  
   }  
  
   if (ShowError) {  
      _sntprintf_s(title, _countof(title), _TRUNCATE, _T("ODBC Error %i"),
                      fNativeError);  
      _sntprintf_s(text, _countof(text), _TRUNCATE, _T("[%s] - %s"),
                      szSqlState, szErrorMsg);  
  
      MessageBox(NULL, (LPCTSTR) text, (LPCTSTR) _T("ODBC Error"), MB_OK);
   }  
}  
  
void connect() {  
   SQLRETURN r;  
  
   r = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &henv);  
  
   // This is an ODBC v3 application  
   r = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, 0);
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, NULL, NULL, NULL, true);  
      exit(-1);  
   }  
  
   r = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Run in ANSI/implicit transaction mode  
   r = SQLSetConnectAttr(hdbc, SQL_ATTR_AUTOCOMMIT,
                          (SQLPOINTER) SQL_AUTOCOMMIT_OFF, SQL_IS_INTEGER);
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, NULL, NULL, NULL, true);  
      exit(-1);  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=PrepExecSample");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS,
                          NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, NULL, NULL, true);  
      exit(-1);  
   }  
}  
  
void setup_ODBC_basics() {  
   SQLRETURN r;  
  
   r = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);  
      exit(-1);  
   }  
}  
  
void OrdEntry(OrdEntryData& order) {  
   // Simple order entry  
   SQLRETURN r;  
  
   SQLINTEGER ItemNo, ProdCode, Qty;  
  
   // Bind parameters for the Order  
   // 1 - OrdNo input  
   r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER,
                          0, 0, &order.OrdNo, sizeof(SQLINTEGER), NULL);
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 2 - Custcode input  
   r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT,SQL_C_TCHAR, SQL_VARCHAR, 5, 0,
                          &order.CustCode, sizeof(order.CustCode), NULL);
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Insert the order  
   r = SQLExecDirect(hstmt, (SQLTCHAR *) _T("{call OrderInsert(?, ?)}"),SQL_NTS);
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Flush results & reset hstmt  
   r = SQLMoreResults(hstmt);  
   if (r != SQL_NO_DATA) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   r = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Bind parameters for the Items  
   // 1 - OrdNo   
   r = SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0,
                          &order.OrdNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 2 - ItemNo   
   r = SQLBindParameter(hstmt, 2, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0,
                          &ItemNo, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 3 - ProdCode  
   r = SQLBindParameter(hstmt, 3, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0,
                          &ProdCode, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // 4 - Qty  
   r = SQLBindParameter(hstmt, 4, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 10, 0,
                          &Qty, sizeof(SQLINTEGER), NULL);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Prepare to insert items one at a time  
   r = SQLPrepare(hstmt, (SQLTCHAR *) _T("{call ItemInsert(?, ?, ?, ?)}"),SQL_NTS);
  
   for (unsigned int i = 0; i < order.ItemCount; i++) {  
  ItemNo = order.ItemNo[i];  
      ProdCode = order.ProdCode[i];  
      Qty = order.Qty[i];  
      r = SQLExecute(hstmt);  
      if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
         ODBCError(henv, hdbc, hstmt, NULL, true);   
         exit(-1);  
      }  
   }  
  
   // Flush results & reset hstmt  
   r = SQLMoreResults(hstmt);  
   if (r != SQL_NO_DATA) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   r = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
  
   // Commit the transaction  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO) {  
      ODBCError(henv, hdbc, hstmt, NULL, true);   
      exit(-1);  
   }  
}  
  
void testOrderEntry() {  
  
   OrdEntryData order;  
  
   order.OrdNo = 1;  
   _tcscpy_s((TCHAR *) order.CustCode, _countof(order.CustCode), _T("CUST1"));
   order.ItemNo[0] = 1;  
   order.ProdCode[0] = 10;  
   order.Qty[0] = 1;  
   order.ItemNo[1] = 2;  
   order.ProdCode[1] = 20;  
   order.Qty[1] = 2;  
   order.ItemNo[2] = 3;  
   order.ProdCode[2] = 30;  
   order.Qty[2] = 3;  
   order.ItemNo[3] = 4;  
   order.ProdCode[3] = 40;  
   order.Qty[3] = 4;  
   order.ItemCount = 4;  
  
   OrdEntry(order);  
}  
int _tmain() {  
   connect();  
   setup_ODBC_basics();  
  
   testOrderEntry();  
}  
```

## <a name="see-also"></a>Weitere Informationen

[Nativ kompilierte gespeicherte Prozeduren](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)
