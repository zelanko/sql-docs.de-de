---
title: Metadatenermittlung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ec3c0f4f-f838-43ce-85f2-cf2761e2aac5
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5bb0c1c7b0ff489e5addff5bb84649984b97f527
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37416259"
---
# <a name="metadata-discovery"></a>Metadatenermittlung
  Metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ermöglicht [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Formatieren von Native Client-Anwendungen, um sicherzustellen, dass diese Spalten- oder Parametermetadaten, die von der Ausführung einer Abfrage zurückgegeben wird, identisch oder kompatibel mit den Metadaten vor dem angegebenen Sie können die Abfrage ausgeführt. Wenn die nach der Ausführung der Abfrage zurückgegebenen Metadaten nicht mit dem Metadatenformat identisch sind, das Sie vor der Ausführung der Abfrage angegeben haben, wird ein Fehler ausgegeben.  
  
 Sie können jetzt in bcp- und ODBC-Funktionen sowie in IBCPSession- und IBCPSession2-Schnittstellen verzögertes Lesen (verzögerte Metadatenerkennung) angeben, um Metadatenermittlung für Abfrageausgabevorgänge zu verhindern. Dies verbessert die Leistung und schließt Metadatenermittlungsfehler aus.  
  
 Wenn Sie entwickeln eine Anwendung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] jedoch eine Verbindung herstellen, um eine Server-Version älter als [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], metadatenermittlung Funktionalität auf die Version des Servers.  
  
## <a name="remarks"></a>Hinweise  
 Die folgenden Bcp-Funktionen wurden verbessert [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] um verbesserte metadatenermittlung bereitzustellen:  
  
-   [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)  
  
-   [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)  
  
-   [bcp_getcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-getcolfmt.md)  
  
-   [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)  
  
-   [bcp_setcolfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md)  
  
 Sie sehen auch eine leistungsverbesserung beim Angeben von Metadatenformats mit [Bcp_setbulkmode](../../native-client-odbc-extensions-bulk-copy-functions/bcp-setbulkmode.md).  
  
 [Bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) verfügt über ein neues *eOption* zur Steuerung des Verhaltens von Bcp_readfmt: `BCPDELAYREADFMT`.  
  
 Die folgenden ODBC-Funktionen wurden verbessert [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] um verbesserte metadatenermittlung bereitzustellen:  
  
-   [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md)  
  
-   [SQLDescribeCol](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [SQLNumParams](../../native-client-odbc-api/sqlnumparams.md)  
  
-   [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)  
  
 Die folgenden OLE DB-Elementfunktionen wurden in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] verbessert, um verbesserte Metadatenermittlung bereitzustellen:  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   ICommandWithParameters:: GetParameterInfo (finden Sie unter [ICommandWithParameters](../../native-client-ole-db-interfaces/icommandwithparameters.md) Informationen)  
  
 Sehen Sie auch eine leistungsverbesserung beim Angeben von Metadaten-Format mit IBCPSession::BCPSetBulkMode  
  
 Die verbesserte Metadatenermittlung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wurde durch das Hinzufügen von zwei gespeicherten Prozeduren in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ermöglicht:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Native Client-Features](sql-server-native-client-features.md)  
  
  
