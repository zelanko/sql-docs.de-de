---
title: SQLAllocStmt-Zuordnung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLAllocStmt
- SQLAllocStmt function [ODBC], mapping
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 447233a3ba014a5ef92f2f49840ad302f8aeccf0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305483"
---
# <a name="sqlallocstmt-mapping"></a>SQLAllocStmt-Zuordnung
Wenn eine Anwendung **SQLAllocStmt** über einen ODBC *3.x-Treiber* aufruft, ruft der Aufruf von:  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 wird **SQLAllocHandle** vom Treiber-Manager im Treiber wie folgt zugeordnet:  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 mit *InputHandle* auf *hdbc* und *OutputHandlePtr* auf *phstmt*gesetzt.
