---
title: SQLParamData | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 79285523ec83d3f10ad6f23010a7f9a6398e5980
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68890108"
---
# <a name="sqlparamdata"></a>SQLParamData
  Wenn SQLParamData den einem Tabellenwert Parameter zugeordneten *ValuePtrPtr* -Wert zurückgibt, sollte die Anwendung SQLPutData mit *StrLen_Or_Ind*aufrufen. Wenn *StrLen_Or_Ind* einen Wert größer als 0 (null) aufweist, bedeutet dies, dass die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Anwendung bereit ist, dass der Native Client Parameterdaten für die nächste Tabellenwert Parameter-Zeile sammelt. Wenn *StrLen_Or_Ind* den Wert 0 hat, bedeutet dies, dass es keine weiteren Daten Zeilen für den Tabellenwert Parameter gibt. Weitere Informationen finden Sie unter [binden und Datenübertragung von Tabellenwert Parametern und Spaltenwerten](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Weitere Informationen zu Tabellenwert Parametern finden Sie unter [Tabellenwert Parameter &#40;(ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
