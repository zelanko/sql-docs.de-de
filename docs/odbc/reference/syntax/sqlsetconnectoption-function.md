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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093014"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption-Funktion
**Übereinstimmung mit Standards**  
 Eingeführt in Version: ODBC-1.0-Standards-Compliance: Als veraltet markiert  
  
 **Zusammenfassung**  
 In ODBC 3. *.x*, die ODBC 2.0-Funktion **SQLSetConnectOption** wurde ersetzt durch **SQLSetConnectAttr**. Weitere Informationen finden Sie unter [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]
>  Weitere Informationen dazu, was der Treiber-Manager diese Funktion auf, wenn einer ODBC 2. zuordnet *.x* Anwendung arbeitet mit einer ODBC 3. *.x* -Treiber verwenden, finden Sie unter [veraltet Zuordnungsfunktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Hinweise  
 Finden Sie unter [ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md), wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird.  
  
> [!NOTE]  
>  Das Attribut SQL_ASYNC_DBC_FUNCTION_ENABLE in ODBC 3.8 eingeführt wird nicht von **SQLSetConnectOption**. Anwendungen, die den asynchronen Vorgang für Verbindungshandle verwenden müssen verwenden **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>Siehe auch  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
