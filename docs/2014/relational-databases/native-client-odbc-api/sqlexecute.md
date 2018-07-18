---
title: SQLExecute | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 017eb7f8c7df6064b0808a2d8d6406e0b9df6ffd
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408246"
---
# <a name="sqlexecute"></a>SQLExecute
  Wenn das Anweisungsattribut SQL_SOPT_SS_PARAM_FOCUS auf 0 (null) SQLExecute nicht festgelegt ist, wird SQL_ERROR zurück und einen Diagnosedatensatz mit SQLSTATE generiert = HY024 und der Meldung "Ungültiger Attributwert, SQL_SOPT_SS_PARAM_FOCUS (muss bei Ausführungszeit NULL sein)". Weitere Informationen zu SQL_SOPT_SS_PARAM_FOCUS finden Sie unter [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Tabellenwertparametern finden Sie unter [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=80708)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
