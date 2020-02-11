---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86488da93470a61a54638e9c60e6e1795a9da4dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125745"
---
# <a name="bookmark-c-data-type"></a>Textmarke, C-Datentyp
Der Datentyp Bookmark C ermöglicht einer Anwendung das Abrufen eines Lesezeichens. Die Lesezeichen-C-Typen werden nur zum Abrufen von Lesezeichen Werten verwendet, die eine Variable Länge aufweisen können. Sie sollten nicht in andere Datentypen konvertiert werden. Eine Anwendung ruft ein Lesezeichen entweder aus der Spalte 0 des Resultsets mit **SQLBulkOperations** (mit dem Vorgang SQL_ADD), **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**ab. Weitere Informationen finden Sie unter [Lesezeichen](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 In der folgenden Tabelle sind der Wert von *CType* für den Datentyp Bookmark c, der ODBC-c-Datentyp, der den Datentyp Bookmark c implementiert, und die Definition dieses Datentyps aus SQL aufgeführt. Micha.  
  
> [!NOTE]
>  Der SQL_C_BOOKMARK-Datentyp ist veraltet. ODBC *3. x* -Anwendungen sollten SQL_C_BOOKMARK nicht verwenden. ODBC *3. x* -Treiber müssen SQL_C_BOOKMARK nur unterstützen, wenn Sie mit ODBC *2. x* -Anwendungen arbeiten möchten, die Sie verwenden. Der Treiber-Manager ordnet SQL_C_VARBOOKMARK SQL_C_BOOKMARK zu, wenn eine Anwendung mit einem ODBC *2. x* -Treiber arbeitet.  
  
|C-Typbezeichner|ODBC C-Typedef|C-Typ|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Veraltet)|Lesezeichen|Ganzzahl ohne Vorzeichen long int|  
|SQL_C_VARBOOKMARK|SQLCHAR|unsigned char *|
