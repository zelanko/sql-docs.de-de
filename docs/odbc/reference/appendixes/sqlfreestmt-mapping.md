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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9d187db4d40132385b9ae4564fddbf89987e3e97
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302011"
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
