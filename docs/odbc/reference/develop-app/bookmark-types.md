---
title: Lesezeichen-Typen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 26d0297cd9dc57e9f30945a9248b235ae469da3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306331"
---
# <a name="bookmark-types"></a>Textmarkentypen
Alle Lesezeichen in ODBC *3.x* sind Lesezeichen variabler Länge. Dadurch kann ein Primärschlüssel oder ein eindeutiger Index, der einer Tabelle zugeordnet ist, als Lesezeichen verwendet werden. Die Textmarke kann auch ein 32-Bit-Wert sein, wie in ODBC *2.x*verwendet wurde. Um anzugeben, dass eine Textmarke mit einem Cursor verwendet wird, legt eine ODBC *3.x-Anwendung* das attribut SQL_ATTR_USE_BOOKMARK-Anweisung auf SQL_UB_VARIABLE. Ein Lesezeichen variabler Länge wird automatisch verwendet.  
  
 Eine Anwendung kann **SQLColAttribute** aufrufen, wobei das *FieldIdentifier-Argument* auf SQL_DESC_OCTET_LENGTH festgelegt ist, um die Länge der Textmarke abzurufen. Da eine Textmarke variabler Länge ein langer Wert sein kann, sollte eine Anwendung nicht an Spalte 0 gebunden werden, es sei denn, sie verwendet die Textmarke für viele Zeilen im Rowset.  
  
 Lesezeichen mit fester Länge werden nur aus Gründen der Abwärtskompatibilität unterstützt. Wenn eine ODBC *2.x-Anwendung,* die mit einem ODBC *3.x-Treiber* arbeitet, **SQLSetStmtOption** aufruft, um SQL_USE_BOOKMARKS auf SQL_UB_ON festzulegen, wird sie im Treiber-Manager SQL_UB_VARIABLE zugeordnet. Es wird ein Lesezeichen variabler Länge verwendet, auch wenn nur 32 Bit davon aufgefüllt werden. Wenn ein Treiber Lesezeichen mit fester Länge unterstützt, unterstützt er Lesezeichen variabler Länge. Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, **SQLSetStmtAttr** aufruft, um SQL_ATTR_USE_BOOKMARKS auf SQL_UB_VARIABLE festzulegen, wird sie im Treiber-Manager SQL_UB_ON zugeordnet, und es wird ein 32-Bit-Lesezeichen mit fester Länge verwendet. Das SQL_ATTR_FETCH_BOOKMARK_PTR Anweisungsattribut muss dann auf ein 32-Bit-Lesezeichen verweisen. Wenn die verwendeten Lesezeichen länger als 32 Bit sind, z. B. wenn Primärschlüssel als Lesezeichen verwendet werden, muss der Cursor die tatsächlichen Werte 32-Bit-Werten zuordnen. Es könnte z. B. eine Hashtabelle von ihnen erstellen. Wenn eine ODBC *3.x-Anwendung,* die mit einem ODBC *2.x-Treiber* arbeitet, eine Textmarke bindet, muss die Pufferlänge 4 betragen.
