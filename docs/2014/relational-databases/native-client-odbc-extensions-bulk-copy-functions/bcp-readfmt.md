---
title: bcp_readfmt | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 55800012b84cf33908d9feddfdac63d85536e97d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019395"
---
# <a name="bcp_readfmt"></a>bcp_readfmt
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
  
## <a name="returns"></a>Gibt zurück  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Nachdem `bcp_readfmt` die Format Werte gelesen hat, werden die entsprechenden Aufrufe an [bcp_columns](bcp-columns.md) und [bcp_colfmt](bcp-colfmt.md)durchführt. Sie brauchen keine Formatdatei zu analysieren, um diese Aufrufe zu tätigen.  
  
 Um eine Format Datei beizubehalten, wenden Sie [bcp_writefmt](bcp-writefmt.md)an. Aufrufe von `bcp_readfmt` können auf gespeicherte Formate verweisen. Weitere Informationen finden Sie unter [bcp_init](bcp-init.md).  
  
 Alternativ kann das Hilfsprogramm zum Massen kopieren (**bcp**) benutzerdefinierte Datenformate in Dateien speichern, auf die von verwiesen werden kann `bcp_readfmt` . Weitere Informationen zum **bcp** -Hilfsprogramm und zur Struktur von **bcp** -Datenformat Dateien finden Sie unter [Massen Import und-Export von Daten &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md).  
  
 Der `BCPDELAYREADFMT` Wert des *eOption* -Parameters von [bcp_control](bcp-control.md) ändert das Verhalten von bcp_readfmt.  
  
> [!NOTE]  
>  Die Format Datei muss von Version 4,2 oder höher des **bcp** -Hilfsprogramms erstellt worden sein.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
