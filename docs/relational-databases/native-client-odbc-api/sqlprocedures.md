---
title: SQLProcedures | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b5fe3b032491371eb53a5f1663e8e6778ce60871
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73785836"
---
# <a name="sqlprocedures"></a>'SQLProcedures'
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Alle gespeicherten Prozeduren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geben einen Wert zurück. **SQLProcedures** meldet SQL_PT_FUNCTION für die Resultsetspalte PROCEDURE_TYPE.  
  
 **SQLProcedures** gibt SQL_SUCCESS zurück, ob Werte für die Parameter *CatalogName,* Schema Name oder *procname* vorhanden sind. **SQLFetch** gibt SQL_NO_DATA zurück, wenn in diesen Parametern ungültige Werte verwendet werden.  
  
 **SQLProcedures** kann in einem statischen Server Cursor ausgeführt werden. Wenn versucht wird, **SQLProcedures** in einem aktualisierbaren (dynamischen oder Keyset-)Cursor auszuführen, gibt der Cursor SQL_SUCCESS_WITH_INFO zurück. Das bedeutet, dass der Cursortyp geändert wurde.  
  
 **SQLProcedures** gibt Informationen zu allen Prozeduren zurück, deren Namen *procname* entsprechen und die vom aktuellen Benutzer ausgeführt werden können oder für die dem aktuellen Benutzer die View Definition-Berechtigung erteilt wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLProcedures-Funktion](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
