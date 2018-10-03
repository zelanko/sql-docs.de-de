---
title: SQLTransact-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b76b7a550211522c2b2100776b88f311abb2b932
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646858"
---
# <a name="sqltransact-function"></a>SQLTransact-Funktion
**Übereinstimmung mit Standards**  
 Version eingeführt: ODBC-1.0-Standards-Compliance: als veraltet markiert  
  
 **Zusammenfassung**  
 In ODBC 3. *x*, die ODBC 2.*.x* Funktion **SQLTransact** wurde ersetzt durch **SQLEndTran**. Weitere Informationen finden Sie unter [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Das Attribut SQL_ASYNC_DBC_FUNCTION_ENABLE, die in der ODBC 3.8 eingeführt wurde, wird nicht von **SQLTransact**. Anwendungen, die mithilfe eines asynchronen Vorgangs für ein Verbindungshandle müssen verwenden **SQLEndTran**.  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
