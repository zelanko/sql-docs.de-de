---
title: Metadatenermittlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 50455f67760c920881f9f8daaf42d7abe4037c45
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707281"
---
# <a name="metadata-discovery"></a>Metadatenermittlung
  Aufgrund der verbesserten Metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Anwendungen sicherstellen, dass Spalten- oder Parametermetadaten, die von der Ausführung einer Abfrage zurückgegeben werden, mit dem Metadatenformat identisch oder kompatibel sind, das Sie vor dem Ausführen der Abfrage angegeben haben. Wenn die nach der Ausführung der Abfrage zurückgegebenen Metadaten nicht mit dem Metadatenformat identisch sind, das Sie vor der Ausführung der Abfrage angegeben haben, wird ein Fehler ausgegeben.  
  
 Sie können jetzt in bcp- und ODBC-Funktionen sowie in IBCPSession- und IBCPSession2-Schnittstellen verzögertes Lesen (verzögerte Metadatenerkennung) angeben, um Metadatenermittlung für Abfrageausgabevorgänge zu verhindern. Dies verbessert die Leistung und schließt Metadatenermittlungsfehler aus.  
  
 Wenn Sie eine Anwendung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] entwickeln, jedoch eine Verbindung mit einer früheren Serverversion als [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]herstellen, entspricht die Funktionalität der Metadatenermittlung der Version des Servers.  
  
## <a name="remarks"></a>Bemerkungen  
 Die folgenden bcp-Funktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 Das Angeben des Metadatenformats mit [bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)führt ebenfalls zu einer Leistungsverbesserung.  
  
 [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) verfügt über eine neue *eOption* zum Steuern des Verhaltens von bcp_readfmt: `BCPDELAYREADFMT` .  
  
 Die folgenden ODBC-Funktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)  
  
 Die folgenden OLE DB-Elementfunktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (Weitere Informationen finden Sie unter [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md).)  
  
 Das Angeben des Metadatenformats mit IBCPSession::BCPSetBulkMode führt ebenfalls zu einer Leistungsverbesserung.  
  
 Die verbesserte Metadatenermittlung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wurde durch das Hinzufügen von zwei gespeicherten Prozeduren in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]ermöglicht:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](sql-server-native-client-features.md)  
  
  
