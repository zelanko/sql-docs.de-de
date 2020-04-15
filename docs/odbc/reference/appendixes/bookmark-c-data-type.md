---
title: Lesezeichen C Datentyp | Microsoft Docs
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
ms.openlocfilehash: 566f1065d30a47b2db234ba1f11f877725189fb7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292290"
---
# <a name="bookmark-c-data-type"></a>Textmarke, C-Datentyp
Der Datentyp "Lesezeichen C" ermöglicht es einer Anwendung, eine Textmarke abzurufen. Die Lesezeichen-C-Typen werden nur zum Abrufen von Lesezeichenwerten verwendet, die variabel sein können. sie sollten nicht in andere Datentypen konvertiert werden. Eine Anwendung ruft eine Textmarke entweder aus Spalte 0 des Resultsets mit **SQLBulkOperations** (mit einer Operation von SQL_ADD), **SQLFetch**, **SQLFetchScroll**oder **SQLGetData**ab. Weitere Informationen finden Sie unter [Lesezeichen](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 In der folgenden Tabelle sind der Wert von *CType* für den Datentyp Lesezeichen C, der ODBC C-Datentyp, der den Datentyp "Lesezeichen C" implementiert, und die Definition dieses Datentyps aus SQL aufgeführt. H.  
  
> [!NOTE]
>  Der SQL_C_BOOKMARK Datentyp smuss veraltet. ODBC *3.x-Anwendungen* sollten keine SQL_C_BOOKMARK verwenden. ODBC *3.x-Treiber* müssen SQL_C_BOOKMARK nur unterstützen, wenn sie mit ODBC *2.x-Anwendungen* arbeiten möchten, die sie verwenden. Der Treiber-Manager ordnet SQL_C_VARBOOKMARK SQL_C_BOOKMARK zu, wenn eine Anwendung mit einem ODBC *2.x-Treiber* arbeitet.  
  
|C-Typ-Idonid|ODBC C typdef|C-Typ|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Veraltet)|Lesezeichen|unsigned long int|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
