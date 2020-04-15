---
title: SQLSetScrollOptions-Funktion | Microsoft Docs
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
ms.openlocfilehash: 056fc203581e1d5d8323b09ac62d692093d8c0f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287266"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions-Funktion
**Konformität**  
 Eingeführte Version: ODBC 1.0-Standards-Konformität: Veraltet  
  
 **Zusammenfassung**  
 In ODBC *3.x*wurde die ODBC 2.0-Funktion **SQLSetScrollOptions** durch Aufrufe von **SQLGetInfo** und **SQLSetStmtAttr**ersetzt.  
  
> [!NOTE]
>  Weitere Informationen darüber, was der Treiber-Manager dieser Funktion zuordnet, wenn eine ODBC *2.x-Anwendung* mit einem ODBC *3.x-Treiber* arbeitet, finden Sie unter [Zuordnen veralteter Funktionen](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
> 
> [!NOTE]
>  Wenn der Treiber-Manager **SQLSetScrollOptions** für eine Anwendung zuordnet, die mit einem ODBC *3.x-Treiber* arbeitet, der **SQLSetScrollOptions**nicht unterstützt, legt der Treiber-Manager die SQL_ROWSET_SIZE-Anweisungsoption und nicht das SQL_ATTR_ROW_ARRAY_SIZE-Anweisungsattribut auf das *RowsetSize-Argument* in **SQLSetScrollOption**fest. Daher kann **SQLSetScrollOptions** nicht von einer Anwendung verwendet werden, wenn mehrere Zeilen durch einen Aufruf von **SQLFetch** oder **SQLFetchScroll**abgerufen werden. Sie kann nur verwendet werden, wenn mehrere Zeilen durch einen Aufruf von **SQLExtendedFetch**abgerufen werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Ihre Anwendung auf einem 64-Bit-Betriebssystem ausgeführt wird, finden Sie weitere Informationen unter [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ODBC-API-Referenz](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC-Headerdateien](../../../odbc/reference/install/odbc-header-files.md)
