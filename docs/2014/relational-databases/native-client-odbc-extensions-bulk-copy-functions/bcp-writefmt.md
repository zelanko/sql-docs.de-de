---
title: Bcp_writefmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_writefmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_writefmt function
ms.assetid: cb4c1d37-667d-4bcd-b13c-eb638bcc9b69
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d4a5067598b475ed8fe103606088d0e4d6d0554
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689406"
---
# <a name="bcpwritefmt"></a>bcp_writefmt
  Erstellt eine Formatdatei, die eine Beschreibung des Formats der aktuellen Datendatei für das Massenkopieren enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_writefmt (  
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
 Pfad und Dateiname der Benutzerdatei zum Abrufen der Formatwerte für die Datendatei.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Die Formatdatei gibt das Datenformat einer durch Massenkopieren erstellten Datendatei an. Durch Aufrufen von [bcp_columns](bcp-columns.md) und [bcp_colfmt](bcp-colfmt.md) wird das Format der Datendatei definiert. **bcp_writefmt** speichert diese Definition in der Datei, auf die von *szFormatFile*verwiesen wird. Weitere Informationen finden Sie unter [bcp_init](bcp-init.md).  
  
 Weitere Informationen zur Struktur von **Bcp** -datenformatdateien finden Sie unter [importieren und Exportieren von Massendaten mithilfe des Hilfsprogramms Bcp &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).  
  
 Verwenden Sie [bcp_readfmt](bcp-readfmt.md), um eine gespeicherte Formatdatei zu laden.  
  
> [!NOTE]  
>  Die von **bcp_writefmt** erstellte Formatdatei wird nur von Versionen des in Version **7.0 und höher enthaltenen Hilfsprogramms** bcp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt.  
  
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
   _T("myErrors"),    DB_OUT) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_columns(hdbc, 3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
bcp_colfmt(hdbc, 1, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 1);  
bcp_colfmt(hdbc, 2, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 2);  
bcp_colfmt(hdbc, 3, SQLCHARACTER, 0, SQL_VARLEN_DATA, '\t', 1, 3);  
  
if (bcp_writefmt(hdbc, _T("myFmtFile.fmt")) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_exec(hdbc, &nRowsProcessed) == SUCCEED)  
   {  
   printf_s("%ld rows copied from SQL Server\n", nRowsProcessed);  
   }  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
