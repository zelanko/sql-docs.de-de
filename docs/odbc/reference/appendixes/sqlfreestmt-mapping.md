---
title: SQLFreeStmt-Zuordnung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1872806265470327f3e7bff468be2ba6d9011421
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199425"
---
# <a name="sqlfreestmt-mapping"></a>SQLFreeStmt-Zuordnung
Wenn eine Anwendung ruft **SQLFreeStmt** mit einer *Option* Argument SQL_DROP über einen ODBC 3.*.x* Treiber, den Aufruf von  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 wird zugeordnet  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 mit der *behandeln* Argument festgelegt wird, mit dem Wert im *Befehls beschäftigt*.
