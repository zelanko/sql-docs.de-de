---
title: Lesezeichen Typen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fb8f5848ef9fdffab8592215fdcc5406b24319c3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68118780"
---
# <a name="bookmark-types"></a>Textmarkentypen
Alle Lesezeichen in ODBC *3. x* sind Lesezeichen mit variabler Länge. Dadurch kann ein Primärschlüssel oder ein eindeutiger Index, der einer Tabelle zugeordnet ist, als Lesezeichen verwendet werden. Bei dem Lesezeichen kann es sich auch um einen 32-Bit-Wert handeln, der in ODBC *2. x*verwendet wurde. Um anzugeben, dass ein Lesezeichen mit einem Cursor verwendet wird, legt eine ODBC *3. x* -Anwendung das SQL_ATTR_USE_BOOKMARK Statement-Attribut auf SQL_UB_VARIABLE fest. Ein Lesezeichen variabler Länge wird automatisch verwendet.  
  
 Eine Anwendung kann **SQLColAttribute** aufrufen, wobei das *fieldidentifier* -Argument auf SQL_DESC_OCTET_LENGTH festgelegt ist, um die Länge des Lesezeichens zu erhalten. Da ein Lesezeichen variabler Länge einen Long-Wert aufweisen kann, sollte eine Anwendung nicht an Spalte 0 gebunden werden, es sei denn, Sie verwendet das Lesezeichen für viele der Zeilen im Rowset.  
  
 Lesezeichen mit fester Länge werden nur aus Gründen der Abwärtskompatibilität unterstützt. Wenn eine ODBC *2. x* -Anwendung, die mit einem ODBC *3. x* -Treiber arbeitet, **SQLSetStmtOption** aufruft, um SQL_USE_BOOKMARKS auf SQL_UB_ON festzulegen, wird Sie im Treiber-Manager zum SQL_UB_VARIABLE zugeordnet. Ein Lesezeichen variabler Länge wird verwendet, auch wenn nur 32 Bits davon aufgefüllt werden. Wenn ein Treiber Lesezeichen mit fester Länge unterstützt, werden Lesezeichen mit variabler Länge unterstützt. Wenn eine ODBC *3. x* -Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, **SQLSetStmtAttr** aufruft, um SQL_ATTR_USE_BOOKMARKS auf SQL_UB_VARIABLE festzulegen, wird Sie im Treiber-Manager SQL_UB_ON zugeordnet, und es wird ein 32-Bit-Lesezeichen mit fester Länge verwendet. Das Attribut der SQL_ATTR_FETCH_BOOKMARK_PTR Anweisung muss dann auf ein 32-Bit-Lesezeichen zeigen. Wenn die verwendeten Lesezeichen länger als 32 Bits sind, z. b. wenn Primärschlüssel als Lesezeichen verwendet werden, muss der Cursor die tatsächlichen Werte 32-Bit-Werten zuordnen. Es könnte z. b. eine Hash Tabelle erstellen. Wenn eine ODBC *3. x* -Anwendung, die mit einem ODBC *2. x* -Treiber arbeitet, ein Lesezeichen bindet, muss die Pufferlänge 4 lauten.
