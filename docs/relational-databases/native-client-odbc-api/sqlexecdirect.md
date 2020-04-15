---
title: SQLExecDirect | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52d5e1bffc49b13289c063154affd517cb8866f6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298471"
---
# <a name="sqlexecdirect"></a>SQLExecDirect
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Wenn das Anweisungsattribut SQL_SOPT_SS_PARAM_FOCUS nicht 0 ist, gibt SQLExecDirect SQL_ERROR zurück und generiert einen Diagnosedatensatz mit SQLSTATE=HY024 und der Meldung "Ungültiger Attributwert, SQL_SOPT_SS_PARAM_FOCUS (muss zur Ausführungszeit Null sein)". Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Tabellenwertparameter &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sqlexecdirect](https://go.microsoft.com/fwlink/?LinkId=80709)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
