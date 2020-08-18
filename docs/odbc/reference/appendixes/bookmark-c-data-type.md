---
description: Textmarke, C-Datentyp
title: Bookmark C-Datentyp | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- C data types [ODBC], bookmark C data type
- pseudo-type identifiers [ODBC], bookmark C data type
- data types [ODBC], pseudo-type identifiers
- bookmarks [ODBC]
- bookmark C data type [ODBC]
ms.assetid: add88e48-ada3-4c0c-a5ac-e78903d3ff41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4647002d5e57ea20656a4fa2dec03aa8092b9b36
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411256"
---
# <a name="bookmark-c-data-type"></a>Textmarke, C-Datentyp
Der Datentyp Bookmark C ermöglicht einer Anwendung das Abrufen eines Lesezeichens. Die Lesezeichen-C-Typen werden nur zum Abrufen von Lesezeichen Werten verwendet, die eine Variable Länge aufweisen können. Sie sollten nicht in andere Datentypen konvertiert werden. Eine Anwendung ruft ein Lesezeichen entweder aus der Spalte 0 des Resultsets mit **SQLBulkOperations** (mit dem Vorgang SQL_ADD), **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**ab. Weitere Informationen finden Sie unter [Lesezeichen](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 In der folgenden Tabelle sind der Wert von *CType* für den Datentyp Bookmark c, der ODBC-c-Datentyp, der den Datentyp Bookmark c implementiert, und die Definition dieses Datentyps aus SQL aufgeführt. Micha.  
  
> [!NOTE]
>  Der SQL_C_BOOKMARK-Datentyp ist veraltet. ODBC *3. x* -Anwendungen sollten SQL_C_BOOKMARK nicht verwenden. ODBC *3. x* -Treiber müssen SQL_C_BOOKMARK nur unterstützen, wenn Sie mit ODBC *2. x* -Anwendungen arbeiten möchten, die Sie verwenden. Der Treiber-Manager ordnet SQL_C_VARBOOKMARK SQL_C_BOOKMARK zu, wenn eine Anwendung mit einem ODBC *2. x* -Treiber arbeitet.  
  
|C-Typbezeichner|ODBC C-Typedef|C-Typ|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Veraltet)|Lesezeichen|unsigned long int|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|
