---
title: SQLParamOptions-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLParamOptions
- SQLParamOptions function [ODBC], mapping
ms.assetid: 57ed65f6-9620-4738-b331-19d2a2b5cae4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 821af40a9550cc6e5fc038bb8e9a24f9e4323441
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792816"
---
# <a name="sqlparamoptions-mapping"></a>SQLParamOptions-Zuordnung
Wenn eine Anwendung ruft **SQLParamOptions** über einen ODBC *3.x* Treiber, den Aufruf  
  
```  
SQLParamOptions(hstmt, crow, piRow);  
```  
  
 wird an zwei Aufrufe zugeordnet **SQLSetStmtAttr** wie folgt:  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMSET_SIZE, crow, 0);  
SQLSetStmtAttr(hstmt, SQL_ATTR_PARAMS_PROCESSED_PTR, piRow, 0);  
```
