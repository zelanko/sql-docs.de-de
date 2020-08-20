---
description: SQLSetScrollOptions-Funktion
title: SQLSetScrollOptions-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0197c3756b76b480cd5370b5edff9d6fc88b201c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491207"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions-Funktion
**Konformitäts**  
 Eingeführte Version: ODBC 1,0 Standards Compliance: deprecated  
  
 **Zusammenfassung**  
 In ODBC *3. x*wurde die ODBC 2,0-Funktion **SQLSetScrollOptions** durch Aufrufe von **SQLGetInfo** und **SQLSetStmtAttr**ersetzt.  
  
> [!NOTE]
>  Weitere Informationen dazu, was der Treiber-Manager diese Funktion zuordnet, wenn eine ODBC *2. x* -Anwendung mit einem ODBC *3. x* -Treiber arbeitet, finden Sie unter [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Anhang G: Driver Guidelines for abwärts Compatibility.  
> 
> [!NOTE]
>  Wenn der Treiber-Manager **SQLSetScrollOptions** für eine Anwendung zuordnet, die mit einem ODBC *3. x* -Treiber arbeitet, der **SQLSetScrollOptions**nicht unterstützt, legt der Treiber-Manager die SQL_ROWSET_SIZE Anweisungs Option, nicht das SQL_ATTR_ROW_ARRAY_SIZE Statement-Attribut, auf das *rowsetsize* -Argument in **sqlsetscrolloption**fest. Daher kann **SQLSetScrollOptions** nicht von einer Anwendung verwendet werden, wenn mehrere Zeilen durch einen-Befehl von **SQLFetch** oder **SQLFetchScroll**abgerufen werden. Diese Option kann nur verwendet werden, wenn mehrere Zeilen durch einen **sqlextendebug**-Befehl abgerufen werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Ihre Anwendung unter einem 64-Bit-Betriebssystem ausgeführt wird, finden Sie weitere [Informationen unter ODBC 64-Bit-Informationen](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
