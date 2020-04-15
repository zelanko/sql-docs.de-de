---
title: SQLParamData | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7a2cc7bfdf35bf30a0883eecf6767e03b6805253
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81289048"
---
# <a name="sqlparamdata"></a>SQLParamData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Wenn SQLParamData den *ValuePtrPtr* zurückgibt, der einem Tabellenwertparameter zugeordnet ist, sollte die Anwendung SQLPutData mit *StrLen_Or_Ind*aufrufen. Wenn *StrLen_Or_Ind* einen Wert größer als 0 hat, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bedeutet dies, dass die Anwendung bereit ist, dass Native Client Parameterdaten für die nächste Tabellenwert-Parameterzeile sammelt. Wenn *StrLen_Or_Ind* den Wert 0 hat, bedeutet dies, dass es keine weiteren Datenzeilen für den Parameter "Tabellenwert" gibt. Weitere Informationen finden Sie unter [Bindung und Datenübertragung von Tabellenwertparametern und Spaltenwerten](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=80706)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
