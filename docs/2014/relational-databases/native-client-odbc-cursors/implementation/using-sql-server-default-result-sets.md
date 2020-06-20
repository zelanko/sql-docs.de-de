---
title: Verwenden SQL Server Standard Resultsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 18cd10dd95329f68a42497d2bea5ce63f345ceff
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85020851"
---
# <a name="using-sql-server-default-result-sets"></a>Verwenden von SQL Server-Standardresultsets
  Die standardmäßigen ODBC-Cursorattribute sind:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 Wenn diese Attribute auf ihre Standardwerte festgelegt sind, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwendet der Native Client-ODBC-Treiber ein [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Standardresultset. Standardresultsets können für beliebige, von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützte SQL-Anweisungen verwendet werden und stellen die effizienteste Methode für die Übertragung des gesamten Resultsets an den Client dar.  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]Einführung in die Unterstützung von Mars (Multiple Active Result Sets); Anwendungen können nun über mehr als ein aktives Standard Resultset pro Verbindung verfügen. MARS ist standardmäßig nicht aktiviert.  
  
 Vor [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] unterstützten Standardresultsets nicht mehrere aktive Anweisungen über die gleiche Verbindung. Nach der Ausführung einer SQL-Anweisung über eine Verbindung akzeptiert der Server keine Befehle vom Client für diese Verbindung (außer der Anforderung zum Abbrechen des restlichen Resultsets), bis alle Zeilen im Resultset verarbeitet wurden. Um den Rest eines teilweise verarbeiteten Resultsets abzubrechen, rufen Sie [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) oder [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) auf, wobei der *fOption* -Parameter auf SQL_CLOSE festgelegt ist. Um ein teilweise verarbeitetes Resultset abzuschließen und auf das vorhanden sein eines anderen Resultsets zu testen, müssen Sie [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)aufzurufen. Wenn eine ODBC-Anwendung versucht, einen Befehl für ein Verbindungs Handle durchzuführen, bevor ein Standardresultset vollständig verarbeitet wurde, generiert der-Befehl SQL_ERROR, und ein **SQLGetDiagRec** -Befehl gibt Folgendes zurück:  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Cursorn](how-cursors-are-implemented.md)  
  
  
