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
ms.openlocfilehash: da50163b90d4a871c2524e1723797474386be8f6
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53356215"
---
# <a name="sqlparamdata"></a>SQLParamData
  Bei Rückgabe der SQLParamData der *ValuePtrPtr* verknüpft ist, mit einem Table-valued Parameter, der die Anwendung sollte aufrufen SQLPutData mit *StrLen_Or_Ind*. Wenn *StrLen_Or_Ind* verfügt über einen Wert größer als 0, es bedeutet, dass die Anwendung kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Parameterdaten für die nächste Zeile des Tabellenwertparameters zu erfassen. Wenn *StrLen_Or_Ind* verfügt über einen Wert von 0 (null) sind keine weiteren Zeilen mit Daten für den Tabellenwertparameter. Weitere Informationen finden Sie unter [Bindung und Data Transfer of Table-Valued-Parameter und Spaltenwerte](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
