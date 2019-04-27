---
title: Bcp_moretext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_moretext
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_moretext function
ms.assetid: 23e98015-a8e4-4434-9b3f-9c7350cf965f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 83142e83ba04328ddf025e0a2f16ff18ad947075
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62688844"
---
# <a name="bcpmoretext"></a>bcp_moretext
  Sendet einen Teil eines langen Datentypwerts variabler Länge an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
  
RETCODE bcp_moretext (  
HDBC   
hdbc  
,  
DBINT   
cbData  
,  
LPCBYTE   
pData  
);  
  
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
 Diese Funktion kann zusammen mit [bcp_bind](bcp-bind.md) und [bcp_sendrow](bcp-sendrow.md) verwendet werden, um lange Datenwerte mit variabler Länge in mehreren kleineren Blöcken nach SQL Server zu kopieren. **Bcp_moretext** kann mit Spalten, die die folgenden SQL Server-Datentypen verwendet werden: `text`, `ntext`, `image`, `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, den benutzerdefinierten Typ (UDT) und XML. **bcp_moretext** unterstützt keine Datenkonvertierungen. Die angegebenen Daten müssen mit dem Datentyp der Zielspalte übereinstimmen.  
  
 Wenn **Bcp_bind** aufgerufen wird und einen *pData* -Parameter für Datentypen, die von Microsoft Intune **Bcp_moretext**, `bcp_sendrow` sendet den gesamten Datenwert unabhängig der Länge. IF, allerdings **Bcp_bind** enthält eine NULL *pData* -Parameter für unterstützte Datentypen, **Bcp_moretext** kann verwendet werden, um Daten unmittelbar nach einer erfolgreichen Rückgabe von zukopieren.`bcp_sendrow` , der angibt, dass alle gebundenen Spalten mit vorhandenen Daten verarbeitet wurden.  
  
 Wenn Sie **bcp_moretext** verwenden, um eine unterstützte Datentypspalte in einer Zeile zu senden, müssen Sie alle anderen unterstützten Datentypspalten in der Zeile ebenfalls mit diesem Parameter senden. Es dürfen keine Spalten übersprungen werden. Unterstützte Datentypen sind SQLTEXT, SQLNTEXT, SQLIMAGE, SQLUDT und SQLXML. SQLCHARACTER, SQLVARCHAR, SQNCHAR, SQLBINARY und SQLVARBINARY gehören auch zu dieser Kategorie, wenn die Spalte den Datentyp varchar(max), nvarchar(max) bzw. varbinary(max) aufweist.  
  
 Durch Aufrufen von **bcp_bind** oder [bcp_collen](bcp-collen.md) wird festgelegt, dass die gesamte Länge aller Datenausschnitte in die SQL Server-Spalte kopiert wird. Ein Versuch zum Senden von SQL Server mehr als im Aufruf angegebenen Bytes **Bcp_bind** oder `bcp_collen` wird ein Fehler generiert. Dieser Fehler wird z. B. auftreten, in einer Anwendung verwendet `bcp_collen` , legen Sie die Länge der verfügbaren Daten für eine SQL Server `text` Spalte 4500, dann aufgerufen, **Bcp_moretext** fünf Mal beim bei jedem Aufruf wurde, dass die Länge des Datenpuffers 1000 Byte beträgt.  
  
 Wenn eine kopierte Zeile mehr als eine lange Spalte variabler Länge enthält, sendet **bcp_moretext** die Daten zunächst an die Spalte mit der niedrigsten Ordnungszahl, dann an die Spalte mit der zweitniedrigsten Ordnungszahl usw. Die richtige Einstellung der gesamten Länge der erwarteten Daten ist wichtig. Es gibt außer der Längeneinstellung keine Möglichkeit zu signalisieren, dass alle Daten für eine Spalte durch Massenkopieren empfangen wurden.  
  
 Wenn `var(max)` Werte werden gesendet, an den Server mit Bcp_sendrow und Bcp_moretext es ist nicht notwendig, Bcp_collen, um die Spaltenlänge festzulegen. Stattdessen wird der Wert nur für diese Typen, von der aufrufenden Bcp_sendrow mit einer Länge von 0 (null) beendet.  
  
 Eine Anwendung ruft normalerweise `bcp_sendrow` und **Bcp_moretext** innerhalb der Schleifen auf, um mehrere Datenzeilen zu senden. Hier ist ein Überblick über die Vorgehensweise für eine Tabelle mit zwei `text` Spalten:  
  
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
 Dieses Beispiel zeigt, wie Sie mit **Bcp_moretext** mit **Bcp_bind** und `bcp_sendrow`:  
  
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
 [Massenkopierfunktionen](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
