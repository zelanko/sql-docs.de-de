---
title: SQLParamData | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 57b45032038f81fe6e2e15202db7b8c790ca4716
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47856918"
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Bei Rückgabe der SQLParamData der *ValuePtrPtr* verknüpft ist, mit einem Table-valued Parameter, der die Anwendung sollte aufrufen SQLPutData mit *StrLen_Or_Ind*. Wenn *StrLen_Or_Ind* verfügt über einen Wert größer als 0, es bedeutet, dass die Anwendung kann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client Parameterdaten für die nächste Zeile des Tabellenwertparameters zu erfassen. Wenn *StrLen_Or_Ind* verfügt über einen Wert von 0 (null) sind keine weiteren Zeilen mit Daten für den Tabellenwertparameter. Weitere Informationen finden Sie unter [Bindung und Data Transfer of Table-Valued-Parameter und Spaltenwerte](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLParamData](http://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
