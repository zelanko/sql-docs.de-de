---
title: SQLParamData | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bd3fefeaa05f806650b58d1778658fda0ed63fa2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060499"
---
# <a name="sqlparamdata"></a>SQLParamData
  Wenn SQLParamData gibt die *ValuePtrPtr* mit einem Tabellenwertparameter verknüpft ist, sollte die Anwendung mit SQLPutData Aufrufen *StrLen_Or_Ind*. Wenn *StrLen_Or_Ind* verfügt über einen Wert größer als 0 (null) bedeutet, dass die Anwendung bereit für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Parameterdaten für die nächste Zeile für den Tabellenwertparameter zu sammeln. Wenn *StrLen_Or_Ind* verfügt über einen Wert von 0 bedeutet keine weiteren Zeilen von Daten für den Tabellenwertparameter vorhanden sind. Weitere Informationen finden Sie unter [Bindung und Data Transfer of Table-Valued-Parametern und Spaltenwerte](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  