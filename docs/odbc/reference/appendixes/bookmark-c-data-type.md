---
title: Bookmark-C-Datentyp | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: b81acf6c60bd11e03a598e349e145dbf72e174b4
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53205289"
---
# <a name="bookmark-c-data-type"></a>Textmarke, C-Datentyp
Das Lesezeichen C-Datentyp kann es sich um eine Anwendung ein Lesezeichen abrufen. Die Lesezeichen-C-Typen werden verwendet, nur für die Lesezeichenwerte abzurufen, die variabler Länge werden kann. Sie sollten nicht in andere Datentypen konvertiert werden. Eine Anwendung ruft ein Lesezeichen, legen Sie entweder von Spalte 0 des Ergebnisses mit **SQLBulkOperations** (mit einem Vorgang des SQL_ADD), **SQLFetch**, **SQLFetchScroll**, oder **SQLGetData**. Weitere Informationen finden Sie unter [Lesezeichen](../../../odbc/reference/develop-app/bookmarks-odbc.md).  
  
 Die folgende Tabelle enthält den Wert der *CType* für den Lesezeichen C-Datentyp, geben Sie der ODBC-C-Datentyp, der die Lesezeichen C-Datentyp und die Definition dieser Daten implementiert von SQL. H.  
  
> [!NOTE]
>  Der Datentyp SQL_C_BOOKMARK wurde als veraltet markiert. ODBC 3.*.x* Anwendungen sollten keine SQL_C_BOOKMARK verwenden. ODBC 3.*.x* Treiber müssen SQL_C_BOOKMARK unterstützen nur, wenn sie mit ODBC 2. arbeiten möchten. *X* Anwendungen, die sie verwenden. Der Treiber-Manager ordnet SQL_C_VARBOOKMARK SQL_C_BOOKMARK, wenn es sich bei eine Anwendung mit einer ODBC 2. funktioniert. *x* Treiber.  
  
|C-Typ-ID|ODBC-C-Typdefinition|C-Typ|  
|-----------------------|--------------------|------------|  
|SQL_C_BOOKMARK<br />(Veraltet)|LESEZEICHEN|lange ganze Zahl ohne Vorzeichen|  
|SQL_C_VARBOOKMARK|SQLCHAR *|unsigned char *|
