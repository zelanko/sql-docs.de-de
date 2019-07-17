---
title: Lesezeichentypen | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118780"
---
# <a name="bookmark-types"></a>Textmarkentypen
Alle Lesezeichen in ODBC *3.x* variabler Länge, die Lesezeichen. Dadurch wird eine primary key- oder eines eindeutigen Indexes einer Tabelle, die als Lesezeichen verwendet werden zugeordnet. Das Lesezeichen auch kann ein 32-Bit-Wert, wie in ODBC verwendet wurde *2.x*. Um anzugeben, dass ein Lesezeichen mit einem Cursor einen ODBC verwendet wird *3.x* Anwendung verwendet wird, legt das SQL_ATTR_USE_BOOKMARK-Anweisungsattribut auf SQL_UB_VARIABLE fest. Ein Lesezeichen variabler Länge wird automatisch verwendet.  
  
 Kann eine Anwendung aufrufen **SQLColAttribute** mit der *FieldIdentifier* Argument, die auf SQL_DESC_OCTET_LENGTH festgelegt ist, um die Länge des Lesezeichens abzurufen. Da ein Lesezeichen variabler Länge, die einen long-Wert sein kann, sollten eine Anwendung, wenn das Lesezeichen für viele der Zeilen im Rowset können nicht auf die Spalte 0 binden.  
  
 Lesezeichen mit fester Länge sind nur für Abwärtskompatibilität unterstützt. Wenn eine ODBC *2.x* arbeiten mit einer ODBC-Anwendung *3.x* Treiber ruft **SQLSetStmtOption** zugeordnet, um SQL_USE_BOOKMARKS SQL_UB_ON festzulegen, in der Treiber-Manager, um SQL_ UB_VARIABLE. Ein Lesezeichen variabler Länge wird verwendet, auch wenn nur 32 Bit des Zertifikats aufgefüllt werden. Wenn ein Treiber Lesezeichen mit fester Länge unterstützt, wird es variabler Länge, die Lesezeichen unterstützen. Wenn eine ODBC *3.x* arbeiten mit einer ODBC-Anwendung *2.x* Treiber ruft **SQLSetStmtAttr** um SQL_ATTR_USE_BOOKMARKS SQL_UB_VARIABLE festzulegen, klicken Sie auf den Treiber zugeordnet Manager SQL_UB_ON und ein 32-Bit-Lesezeichen fester Länge wird verwendet. Das SQL_ATTR_FETCH_BOOKMARK_PTR-Anweisungsattribut muss klicken Sie dann auf einem 32-Bit-Lesezeichen verweisen. Wenn die Lesezeichen verwendet mehr als 32 Bit, sind z. B. Primärschlüssel als Lesezeichen verwendet werden, der Cursor die tatsächlichen Werte auf 32-Bit-Werte zuordnen muss. Es könnte z. B. eine Hashtabelle erstellt werden. Wenn eine ODBC *3.x* arbeiten mit einer ODBC-Anwendung *2.x* Treiber bindet ein Lesezeichen, das die Pufferlänge muss 4 sein.
