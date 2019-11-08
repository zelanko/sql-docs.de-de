---
title: bcp_moretext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_moretext
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 05d7a6ca9f90439f803032087f4032765cba2f88
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73782625"
---
# <a name="bcp_moretext"></a>bcp_moretext
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Sendet einen Teil eines langen Datentypwerts variabler Länge an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_moretext (  
        HDBC hdbc,  
        DBINT cbData,  
        LPCBYTE pData);  
```  
  
## <a name="arguments"></a>Argumente  
 *hdbc*  
 Das für den Massenkopiervorgang aktivierte ODBC-Verbindungshandle.  
  
 *cbData*  
 Entspricht der Anzahl der Datenbytes, die aus den Daten, auf die *pData*verweist, auf den SQL Server kopiert werden. Der Wert SQL_NULL_DATA gibt NULL an.  
  
 *pData*  
 Ist ein Zeiger auf den unterstützten, langen Datenausschnitt variabler Länge, der an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gesendet werden soll.  
  
## <a name="returns"></a>Rückgabewert  
 SUCCEED oder FAIL.  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion kann zusammen mit [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) und [bcp_sendrow](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) verwendet werden, um lange Datenwerte mit variabler Länge in mehreren kleineren Blöcken nach SQL Server zu kopieren. **bcp_moretext** kann mit Spalten verwendet werden, die die folgenden SQL Server-Datentypen aufweisen: **text**, **ntext**, **image**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , benutzerdefinierter Typ (UDT) und XML. **bcp_moretext** unterstützt keine Datenkonvertierungen. Die angegebenen Daten müssen mit dem Datentyp der Zielspalte übereinstimmen.  
  
 Wenn **bcp_bind** mit einem *pData* -Parameter ungleich NULL für Datentypen aufgerufen wird, die von **bcp_moretext**unterstützt werden, sendet **bcp_sendrow** unabhängig von der Länge den gesamten Datenwert. Verfügt **bcp_bind** hingegen über einen *pData* -NULL-Parameter für unterstützte Datentypen, kann **bcp_moretext** verwendet werden, um Daten unmittelbar nach einer erfolgreichen Rückgabe von **bcp_sendrow** zu kopieren. Dadurch wird angegeben, dass alle gebundenen Spalten mit vorhandenen Daten verarbeitet wurden.  
  
 Wenn Sie **bcp_moretext** verwenden, um eine unterstützte Datentypspalte in einer Zeile zu senden, müssen Sie alle anderen unterstützten Datentypspalten in der Zeile ebenfalls mit diesem Parameter senden. Es dürfen keine Spalten übersprungen werden. Unterstützte Datentypen sind SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT und SQLXML. SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY und SQLVARBINARY gehören auch zu dieser Kategorie, wenn die Spalte den Datentyp varchar(max), nvarchar(max) bzw. varbinary(max) aufweist.  
  
 Durch Aufrufen von **bcp_bind** oder [bcp_collen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) wird festgelegt, dass die gesamte Länge aller Datenausschnitte in die SQL Server-Spalte kopiert wird. Wenn Sie versuchen, mehr Bytes an den SQL Server zu senden, als im Aufruf für **bcp_bind** oder **bcp_collen** angegeben, wird ein Fehler ausgegeben. Dieser Fehler tritt beispielsweise in einer Anwendung auf, die mit **bcp_collen** die Länge der verfügbaren Daten für eine **text** -Spalte von SQL Server auf 4500 festgelegt und anschließend fünf Mal **bcp_moretext** aufgerufen hat, wobei bei jedem Aufruf angegeben wurde, dass die Länge des Datenpuffers 1000 Byte beträgt.  
  
 Wenn eine kopierte Zeile mehr als eine lange Spalte variabler Länge enthält, sendet **bcp_moretext** die Daten zunächst an die Spalte mit der niedrigsten Ordnungszahl, dann an die Spalte mit der zweitniedrigsten Ordnungszahl usw. Die richtige Einstellung der gesamten Länge der erwarteten Daten ist wichtig. Es gibt außer der Längeneinstellung keine Möglichkeit zu signalisieren, dass alle Daten für eine Spalte durch Massenkopieren empfangen wurden.  
  
 Wenn **var (max)** -Werte mithilfe von bcp_sendrow und bcp_moretext an den Server gesendet werden, ist es nicht erforderlich, bcp_collen aufzurufen, um die Spaltenlänge festzulegen. Stattdessen wird der Wert nur für diese Typen beendet, indem bcp_sendrow mit der Länge 0 (null) aufgerufen wird.  
  
 Eine Anwendung ruft normalerweise **bcp_sendrow** und **bcp_moretext** innerhalb der Schleifen auf, um mehrere Datenzeilen zu senden. Im Folgenden wird die Vorgehensweise für eine Tabelle mit zwei **text** -Spalten umrissen:  
  
```  
while (there are still rows to send)  
{  
bcp_sendrow(...);  
  
for (all the data in the first varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
for (all the data in the second varbinary(max) column)  
bcp_moretext(...);  
bcp_moretext(hdbc, 0, NULL);  
  
}  
  
```  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie **bcp_moretext** mit **bcp_bind** und **bcp_sendrow**verwendet wird:  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      idRow = 5;  
char*      pPart1 = "This text value isn't very long,";  
char*      pPart2 = " but it's broken into three parts";  
char*      pPart3 = " anyhow.";  
DBINT      cbAllParts;  
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
if (bcp_init(hdbc, "comdb..articles", NULL, NULL, DB_IN) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Bind program variables to table columns.   
if (bcp_bind(hdbc, (LPCBYTE) &idRow, 0, SQL_VARLEN_DATA, NULL, 0,  
   SQLINT4, 1)    == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
cbAllParts = (DBINT) (strnlen(pPart1, sizeof(pPart1) + 1) + strnlen(pPart2, sizeof(pPart2) + 1) + strnlen(pPart3, sizeof(pPart3) + 1));  
if (bcp_bind(hdbc, NULL, 0, cbAllParts, NULL, 0, SQLTEXT, 2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Send this row, with the text value broken into three chunks.   
if (bcp_sendrow(hdbc) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart1, sizeof(pPart1) + 1), pPart1) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart2, sizeof(pPart2) + 1), pPart2) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
if (bcp_moretext(hdbc, (DBINT) strnlen(pPart3, sizeof(pPart3) + 1), pPart3) == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// All done. Get the number of rows processed (should be one).  
nRowsProcessed = bcp_done(hdbc);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Massenkopierfunktionen](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
