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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 11c5048cd197643823bb6b0fc8e8247983666d8c
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705980"
---
# <a name="sqlgetstmtattr"></a>'SQLGetStmtAttr'
  Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber erweitert SQLGetStmtAttr, um Treiber spezifische Anweisungs Attribute verfügbar zu machen.  
  
 [SQLSetStmtAttr](sqlsetstmtattr.md) listet Anweisungsattribute auf, auf die sowohl Schreib- als auch Lesezugriff möglich ist. In diesem Thema sind die schreibgeschützten Anweisungsattribute aufgeführt.  
  
## <a name="sql_sopt_ss_current_command"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 Das SQL_SOPT_SS_CURRENT_COMMAND-Attribut macht den aktuellen Befehl eines Befehlsbatches verfügbar. Zurückgegeben wird ein ganzzahliger Wert, der die Position des Befehls im Batch angibt. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
## <a name="sql_sopt_ss_nocount_status"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 Das SQL_SOPT_SS_NOCOUNT_STATUS-Attribut zeigt die aktuelle Einstellung der NOCOUNT-Option an. Diese Option steuert, ob [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Anzahl der von einer Anweisung betroffenen Zeilen ausweist, wenn [SQLRowCount](sqlrowcount.md) aufgerufen wird. Der *ValuePtr* -Wert ist vom Typ SQLLEN.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|SQL_NC_OFF|NOCOUNT ist OFF. SQLRowCount gibt die Anzahl der betroffenen Zeilen zurück.|  
|SQL_NC_ON|NOCOUNT ist ON. Die Anzahl der betroffenen Zeilen wird von SQLRowCount nicht zurückgegeben, und der zurückgegebene Wert ist 0.|  
  
 Wenn SQLRowCount 0 zurückgibt, sollte die Anwendung SQL_SOPT_SS_NOCOUNT_STATUS testen. Wenn SQL_NC_ON zurückgegeben wird, gibt der Wert 0 von SQLRowCount lediglich an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Zeilen Anzahl zurückgegeben hat. Wird SQL_NC_OFF zurückgegeben, bedeutet dies, dass NOCOUNT deaktiviert ist, und der Wert 0 aus SQLRowCount zeigt an, dass keine Zeilen von der Anweisung betroffen waren.  
  
 Anwendungen sollten den Wert von SQLRowCount nicht anzeigen, wenn SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF ist. Große Batches oder gespeicherte Prozeduren können mehrere SET NOCOUNT-Anweisungen enthalten. Daher kann nicht davon ausgegangen werden, dass SQL_SOPT_SS_NOCOUNT_STATUS konstant bleibt. Diese Option sollte jedes Mal getestet werden, wenn SQLRowCount 0 zurückgibt.  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a>SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Das SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT-Attribut gibt den Meldungstext für die Abfragebenachrichtigungsanforderung zurück.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>'SQLGetStmtAttr' und Tabellenwertparameter  
 SQLGetStmtAttr kann aufgerufen werden, um beim Arbeiten mit Tabellenwert Parametern den Wert von SQL_SOPT_SS_PARAM_FOCUS im Anwendungsparameter Deskriptor (APD) zu erhalten. Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;ODBC-&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLSetStmtAttr-Funktion](https://go.microsoft.com/fwlink/?LinkId=59370)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
