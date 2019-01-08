---
title: SQLGetStmtAttr | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5604aafbbc8a6d77081e829269955c8b7600f4ee
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53359923"
---
# <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'
  Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber erweitert SQLGetStmtAttr um treiberspezifische Anweisungsattribute verfügbar zu machen.  
  
 [SQLSetStmtAttr](sqlsetstmtattr.md) listet Anweisungsattribute auf, auf die sowohl Schreib- als auch Lesezugriff möglich ist. In diesem Thema sind die schreibgeschützten Anweisungsattribute aufgeführt.  
  
## <a name="sqlsoptsscurrentcommand"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 Das SQL_SOPT_SS_CURRENT_COMMAND-Attribut macht den aktuellen Befehl eines Befehlsbatches verfügbar. Zurückgegeben wird ein ganzzahliger Wert, der die Position des Befehls im Batch angibt. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
## <a name="sqlsoptssnocountstatus"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 Das SQL_SOPT_SS_NOCOUNT_STATUS-Attribut zeigt die aktuelle Einstellung der NOCOUNT-Option an. Diese Option steuert, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Anzahl der von einer Anweisung betroffenen Zeilen ausweist, wenn [SQLRowCount](sqlrowcount.md) aufgerufen wird. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|Wert|Description|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT ist OFF. SQLRowCount gibt die Anzahl der betroffenen Zeilen zurück.|  
|SQL_NC_ON|NOCOUNT ist ON. Die Anzahl der betroffenen Zeilen nicht durch SQLRowCount zurückgegeben, und der zurückgegebene Wert ist 0.|  
  
 Wenn SQLRowCount 0 zurückgibt, sollte die Anwendung SQL_SOPT_SS_NOCOUNT_STATUS testen. Wenn SQL_NC_ON zurückgegeben wird, der Wert 0 aus SQLRowCount nur gibt an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurden keine Zeilenanzahl zurückgegeben. Wird SQL_NC_OFF zurückgegeben, bedeutet dies, dass NOCOUNT deaktiviert und der Wert 0 aus SQLRowCount gibt an, dass alle Zeilen nicht in die Anweisung ausgewirkt hat.  
  
 Anwendungen sollten den Wert der SQLRowCount nicht angezeigt, wenn SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF ist. Große Batches oder gespeicherte Prozeduren können mehrere SET NOCOUNT-Anweisungen enthalten. Daher kann nicht davon ausgegangen werden, dass SQL_SOPT_SS_NOCOUNT_STATUS konstant bleibt. Diese Option sollte jedes Mal getestet werden, die SQLRowCount 0 zurück.  
  
## <a name="sqlsoptssquerynotificationmsgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Das SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT-Attribut gibt den Meldungstext für die Abfragebenachrichtigungsanforderung zurück.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>'SQLGetStmtAttr' und Tabellenwertparameter  
 SQLGetStmtAttr kann aufgerufen werden, um den Wert von SQL_SOPT_SS_PARAM_FOCUS im anwendungsparameterdeskriptor (APD) abzurufen, bei der Arbeit mit Tabellenwertparametern. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLSetStmtAttr-Funktion](https://go.microsoft.com/fwlink/?LinkId=59370)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
