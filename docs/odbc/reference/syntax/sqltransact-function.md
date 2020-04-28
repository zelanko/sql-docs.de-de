---
title: SQLtransact-Funktion | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7a4f1da36a7c233e9a1b5832ee83e86a5c1f77d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287080"
---
# <a name="sqltransact-function"></a>SQLTransact-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: deprecated  
  
 **Zusammenfassung**  
 In ODBC *3. x*wurde die ODBC *2. x* -Funktion **SQLTransact** durch **SQLEndTran**ersetzt. Weitere Informationen finden Sie unter [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Das Attribut SQL_ASYNC_DBC_FUNCTION_ENABLE, das in ODBC 3,8 eingeführt wurde, wird von **SQLTransact**nicht unterstützt. Anwendungen, die einen asynchronen Vorgang für ein Verbindungs Handle verwenden, müssen **SQLEndTran**verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
