---
title: SQLSetConnectOption-Funktion | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b429e499cccaad553236b4ebee78374c69c7c4dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093014"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: deprecated  
  
 **Zusammenfassung**  
 In ODBC 3 *. x*wurde die ODBC 2,0-Funktion **SQLSetConnectOption** durch **SQLSetConnectAttr**ersetzt. Weitere Informationen finden Sie unter [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]
>  Weitere Informationen dazu, wie der Treiber-Manager diese Funktion zuordnet, wenn eine ODBC 2 *. x* -Anwendung mit einem ODBC 3 *. x* -Treiber arbeitet, finden Sie unter [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Bemerkungen  
 Weitere Informationen finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung unter einem 64-Bit-Betriebssystem ausgeführt wird.  
  
> [!NOTE]  
>  Das in ODBC 3,8 eingeführte Attribut SQL_ASYNC_DBC_FUNCTION_ENABLE wird von **SQLSetConnectOption**nicht unterstützt. Anwendungen, die den asynchronen Vorgang für das Verbindungs Handle verwenden, müssen **SQLSetConnectAttr**verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
