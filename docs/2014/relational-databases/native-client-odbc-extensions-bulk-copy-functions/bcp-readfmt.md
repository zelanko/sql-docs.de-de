---
title: Bcp_readfmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_readfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_readfmt function
ms.assetid: 654001c8-ae9f-425c-b820-f0191bf89367
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76ccc4271877b81ae103a89b5df727b74017d9ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62688668"
---
# <a name="bcpreadfmt"></a>bcp_readfmt
  Liest eine Datendatei-Formatdefinition aus der angegebenen Formatdatei.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_readfmt (  
HDBC   
hdbc  
,  
LPCTSTR   
szFormatFile  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *szFormatFile*  
 Pfad und Dateiname der Datei, die die Formatwerte für die Datendatei enthält.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Nach dem `bcp_readfmt` die Formatwerte gelesen, nimmt Sie geeignete Aufrufe an [Bcp_columns](bcp-columns.md) und [Bcp_colfmt](bcp-colfmt.md). Sie brauchen keine Formatdatei zu analysieren, um diese Aufrufe zu tätigen.  
  
 Um eine Formatdatei beizubehalten, rufen [Bcp_writefmt](bcp-writefmt.md). Aufrufe von `bcp_readfmt` können auf gespeicherte Formate verweisen. Weitere Informationen finden Sie unter [bcp_init](bcp-init.md).  
  
 Alternativ können Sie das Hilfsprogramm zum Massenkopieren (**Bcp**) können Sie die benutzerdefinierte Datenformate in Dateien, die auf Sie verweisen können speichern `bcp_readfmt`. Weitere Informationen zu den **Bcp** -Hilfsprogramm und die Struktur der **Bcp** -datenformatdateien finden Sie unter [Massenimport und-Export von Daten &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Die `BCPDELAYREADFMT` Wert, der die *eOption* Parameter [Bcp_control](bcp-control.md) ändert das Verhalten von Bcp_readfmt.  
  
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
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
