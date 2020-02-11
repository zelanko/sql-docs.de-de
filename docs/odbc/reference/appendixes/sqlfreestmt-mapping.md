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
ms.openlocfilehash: a92af35d8a1b1e98a484c69d7d2e66bf5bef3196
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086077"
---
# <a name="sqlfreestmt-mapping"></a>SQLFreeStmt-Zuordnung
Wenn eine Anwendung **SQLFreeStmt** mit einem *options* Argument von SQL_DROP über einen ODBC *3. x* -Treiber aufruft, wird der Aufruf von  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 ist zugeordnet  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 Wenn das *handle* -Argument auf den Wert in *hstmt*festgelegt ist.
