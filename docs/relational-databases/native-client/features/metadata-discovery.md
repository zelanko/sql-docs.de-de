---
title: Metadatenermittlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5d822362e9f9f7e70e4421056383aae8ddef03dc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303351"
---
# <a name="metadata-discovery"></a>Metadatenermittlung
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Aufgrund der verbesserten Metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] können [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Anwendungen sicherstellen, dass Spalten- oder Parametermetadaten, die von der Ausführung einer Abfrage zurückgegeben werden, mit dem Metadatenformat identisch oder kompatibel sind, das Sie vor dem Ausführen der Abfrage angegeben haben. Wenn die nach der Ausführung der Abfrage zurückgegebenen Metadaten nicht mit dem Metadatenformat identisch sind, das Sie vor der Ausführung der Abfrage angegeben haben, wird ein Fehler ausgegeben.  
  
 Sie können jetzt in bcp- und ODBC-Funktionen sowie in IBCPSession- und IBCPSession2-Schnittstellen verzögertes Lesen (verzögerte Metadatenerkennung) angeben, um Metadatenermittlung für Abfrageausgabevorgänge zu verhindern. Dies verbessert die Leistung und schließt Metadatenermittlungsfehler aus.  
  
 Wenn Sie eine Anwendung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] entwickeln, jedoch eine Verbindung mit einer früheren Serverversion als [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]herstellen, entspricht die Funktionalität der Metadatenermittlung der Version des Servers.  
  
## <a name="remarks"></a>Bemerkungen  
 Die folgenden bcp-Funktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   [bcp_columns](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 Das Angeben des Metadatenformats mit [bcp_setbulkmode](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md)führt ebenfalls zu einer Leistungsverbesserung.  
  
 [bcp_control](../../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) hat eine neue *eOption,* um das Verhalten von bcp_readfmt zu steuern: **BCPDELAYREADFMT**.  
  
 Die folgenden ODBC-Funktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   [SQLNumResultCols](../../../relational-databases/native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../../relational-databases/native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)  
  
 Die folgenden OLE DB-Elementfunktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters::GetParameterInfo (Weitere Informationen finden Sie unter [ICommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).)  
  
 Das Angeben des Metadatenformats mit IBCPSession::BCPSetBulkMode führt ebenfalls zu einer Leistungsverbesserung.  
  
 Die verbesserte Metadatenermittlung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wurde durch das Hinzufügen von zwei gespeicherten Prozeduren in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]ermöglicht:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client-Funktionen](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
