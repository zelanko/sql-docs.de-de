---
title: SQLSetConnectOption-Funktion | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 263b15cb75fb5c0c7c1d7aa630a8da171b9765a7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301595"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Standards-Konformität: Veraltet  
  
 **Zusammenfassung**  
 In ODBC 3 *.x*wurde die ODBC 2.0-Funktion **SQLSetConnectOption** durch **SQLSetConnectAttr**ersetzt. Weitere Informationen finden Sie unter [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]
>  Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn eine ODBC 2 *.x-Anwendung* mit einem ODBC 3 *.x-Treiber* arbeitet, finden Sie unter [Zuordnen veralteter Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)..  
  
## <a name="remarks"></a>Bemerkungen  
 Siehe [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
> [!NOTE]  
>  Das in ODBC 3.8 eingeführte Attribut SQL_ASYNC_DBC_FUNCTION_ENABLE wird von **SQLSetConnectOption**nicht unterstützt. Anwendungen, die den asynchronen Vorgang für das Verbindungshandle verwenden, müssen **SQLSetConnectAttr**verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
