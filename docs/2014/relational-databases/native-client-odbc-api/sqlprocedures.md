---
title: SQLProcedures | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: rothja
ms.author: jroth
ms.openlocfilehash: e37f15841a36eb95c1e9263d137ba2734d622367
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85021801"
---
# <a name="sqlprocedures"></a>'SQLProcedures'
  Alle gespeicherten Prozeduren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geben einen Wert zurück. **SQLProcedures** gibt SQL_PT_FUNCTION für die Resultsetspalte PROCEDURE_TYPE aus.  
  
 **SQLProcedures** gibt SQL_SUCCESS zurück, unabhängig davon, ob Werte für die Parameter *CatalogName, SchemaName* oder *ProcName* vorhanden sind. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLProcedures** kann in einem statischen Servercursor ausgeführt werden. Wenn versucht wird, **SQLProcedures** in einem aktualisierbaren (dynamischen oder Keyset-)Cursor auszuführen, gibt der Cursor SQL_SUCCESS_WITH_INFO zurück. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 **SQLProcedures** gibt Informationen zu allen Prozeduren zurück, deren Name *ProcName* entspricht und die vom aktuellen Benutzer ausgeführt werden können bzw. für die der Benutzer die VIEW DEFINITION-Berechtigung erhalten hat.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLProcedures-Funktion](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
