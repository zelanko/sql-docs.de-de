---
title: Bcp_readfmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- bcp_readfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 108485cf0ce8385701520396a70b25d3026b60f2
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2018
ms.locfileid: "39559176"
---
# <a name="bcpreadfmt"></a>bcp_readfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Liest eine Datendatei-Formatdefinition aus der angegebenen Formatdatei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_readfmt (  
        HDBC hdbc,  
        LPCTSTR szFormatFile);  
```  
  
## <a name="arguments"></a>Argumente  
 *HDBC*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *szFormatFile*  
 Pfad und Dateiname der Datei, die die Formatwerte für die Datendatei enthält.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Nach dem **Bcp_readfmt** die Formatwerte gelesen, nimmt Sie geeignete Aufrufe an [Bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) und [Bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md). Sie brauchen keine Formatdatei zu analysieren, um diese Aufrufe zu tätigen.  
  
 Um eine Formatdatei beizubehalten, rufen [Bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md). Aufrufe von **Bcp_readfmt** können auf gespeicherte Formate verweisen. Weitere Informationen finden Sie unter [Bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md).  
  
 Alternativ können Sie das Hilfsprogramm zum Massenkopieren (**Bcp**) können Sie die benutzerdefinierte Datenformate in Dateien, die auf Sie verweisen können speichern **Bcp_readfmt**. Weitere Informationen zu den **Bcp** -Hilfsprogramm und die Struktur der **Bcp** -datenformatdateien finden Sie unter [Massenimport und-Export von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Die **BCPDELAYREADFMT** Wert, der die *eOption* Parameter [Bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) ändert das Verhalten von Bcp_readfmt.  
  
> [!NOTE]  
>  Die Formatdatei muss Version 4.2 oder höher erstellt wurden die **Bcp** Hilfsprogramm.  
  
## <a name="example"></a>Beispiel  
  
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
if (bcp_init(hdbc, _T("myTable"), _T("myData.csv"),  
   _T("myErrors"),    DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_readfmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   cout << nRowsProcessed << " rows copied to SQL Server\n";  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
