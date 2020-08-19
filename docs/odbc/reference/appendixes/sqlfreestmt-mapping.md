---
description: SQLFreeStmt-Zuordnung
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
ms.openlocfilehash: 1f5066593e900fc60eea0ce5a5fc183eb2e83137
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421484"
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
